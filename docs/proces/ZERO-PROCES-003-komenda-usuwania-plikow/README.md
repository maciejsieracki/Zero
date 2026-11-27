# ZERO-PROCES-003 — komenda usuwania nieaktywnych plikow zasad AutoBot

Skrypt `usun_pliki_autobot.ps1` (ten sam tekst jest w bloku kodu nizej, do wklejenia) przeszukuje folder `$dir` i przenosi do Kosza **wylacznie** pliki z zatwierdzonej listy kasacji (inwentarz ZERO-PROCES-002, sekcja 7), i to tylko wtedy, gdy zgadza sie **dokladna nazwa i pelny SHA-256** (sekcja 8.5). Domyslnie pracuje w **trybie podgladu** (`$Usun = $false`) i niczego nie usuwa. Plikow nie usuwa zaden agent — robi to wylacznie wlasciciel (ECHO-013).

Domyslny folder: `C:\Users\Maciej Sieracki\OneDrive - NASTER S.A\_NOWA_STRUKTURA\Caude`

## Uzycie w 5 krokach

1. **Wklej.** Otworz Windows PowerShell (5.1) albo PowerShell 7 — zwykle, bez "Uruchom jako administrator". Jesli pliki leza w innym folderze, popraw tylko linie `$dir = '...'` na poczatku skryptu. Wklej caly blok kodu ponizej i nacisnij Enter.
2. **Sprawdz tabele podgladu.** Skrypt wypisze tabele: Sciezka, Rozmiar, SHA256, Decyzja oraz podsumowanie. W tym trybie nic nie jest usuwane. Do usuniecia ida tylko wiersze z decyzja `ZAKWALIFIKOWANY (nazwa i hash zgodne)`. Wiersz `NAZWA ZGODNA, HASH INNY — pomijam` oznacza plik o tej samej nazwie, ale innej tresci — zostaje.
3. **Zmien flage.** Gdy tabela jest zgodna z oczekiwaniem, w skrypcie zmien `$Usun = $false` na `$Usun = $true` (tylko ta jedna zmiana).
4. **Uruchom.** Wklej skrypt ponownie i nacisnij Enter. Kazdy zakwalifikowany plik jest tuz przed usunieciem hashowany jeszcze raz i przenoszony do Kosza pojedynczo (`PRZENIESIONO DO KOSZA: "..."`). Na koncu podsumowanie: ile znaleziono, zakwalifikowano, przeniesiono, pominieto.
5. **Sprawdz Kosz.** Otworz Kosz Windows (a dla plikow OneDrive takze Kosz w OneDrive w przegladarce): powinny tam byc wylacznie pliki z tabeli oznaczone jako zakwalifikowane. Kazdy mozna przywrocic ("Przywroc"). Folder `autobot-skills` musi pozostac na miejscu.

## Skrypt do wklejenia

```powershell
# ZERO-PROCES-003-komenda-usuwania-plikow
# usun_pliki_autobot.ps1 -- usuwa (do Kosza) WYLACZNIE nieaktywne pliki zasad AutoBot
# z zatwierdzonej listy kasacji (inwentarz ZERO-PROCES-002, sekcja 7; hashe z sekcji 8.5).
# Plik jest celowo w czystym ASCII (bez polskich znakow), aby Windows PowerShell 5.1
# odczytal go poprawnie takze bez BOM. Dziala w Windows PowerShell 5.1 i PowerShell 7.
# Nie wymaga administratora. Nie laczy sie z siecia. Nie usuwa katalogow.
#
# ===== USTAWIENIA (wolno zmienic tylko te dwie linie) =====
$dir  = 'C:\Users\Maciej Sieracki\OneDrive - NASTER S.A\_NOWA_STRUKTURA\Caude'
$Usun = $false    # $false = TYLKO PODGLAD (nic nie usuwa); $true = przenies zakwalifikowane pliki do Kosza
# ==========================================================

& {
    # --- Zatwierdzona lista kasacji: DOKLADNA nazwa -> pelny SHA-256 (inwentarz, sekcja 7 i 8.5) ---
    $Lista = [ordered]@{
        'autobotSKILL.md'                      = 'b7ce490ca518104265a7670a68e9c68a5f6978bfca22cf3a4f3a00144b3d6812'
        'civautobotSKILL.md'                   = 'fd1f90877fab5dd83ca488e554fe54cf0abd85f17da53519fae6d1fb1177372b'
        'AutoBot-Orkiestrator-SKILL.md'        = '8f3efd7f7f027af556a5a723163e752fbc3e952b1547e5f4f2873535a1d37829'
        'AutoBot-Orkiestrator-v1.1.0-SKILL.md' = '626eeb5308a843abc1e3b44801feb9b7cf0b637271e21dc4f3fb3a9486a29788'
        'skasujzmergowanegalezieautobot.sh'    = '9df2c59f72658b045d1fdaeb69be8f899aa097809d4688f3dea8e219ad6aa265'
        'autobot-skills.zip'                   = '44f63cfb3389aef2f3d587cd47041d395a79b5b5660dbaa9b1a1e30e37a6a242'
    }
    # Folder, ktory ZOSTAJE (jedyna kopia zestawu f); zip jest jego duplikatem.
    $FolderZostaje  = 'autobot-skills'
    # Plik-swiadek w zachowanym folderze (inwentarz 8.5): potwierdza, ze folder jest pelna kopia zestawu f.
    $SwiadekRel     = 'skills\autobot-orchestrator\SKILL.md'
    $SwiadekHash    = '6e8e071694bd1a51abda87cea0f758bd5b29492693d613323a85777b2b0a72b9'
    $Myslnik        = [string][char]0x2014   # myslnik U+2014 budowany z kodu, aby plik pozostal ASCII

    $tryb = 'PODGLAD (nic nie jest usuwane)'
    if (($Usun -is [bool]) -and $Usun) { $tryb = 'USUWANIE DO KOSZA' }
    Write-Host ''
    Write-Host ('Folder: "' + $dir + '"')
    Write-Host ('Tryb:   ' + $tryb)
    Write-Host ''

    if (-not (Test-Path -LiteralPath $dir -PathType Container)) {
        Write-Host ('BLAD: folder nie istnieje: "' + $dir + '". Nic nie zrobiono.') -ForegroundColor Red
        return
    }
    $root = (Get-Item -LiteralPath $dir -Force).FullName.TrimEnd('\')

    function Get-Sha256([string]$sciezka) {
        try {
            return (Get-FileHash -LiteralPath $sciezka -Algorithm SHA256 -ErrorAction Stop).Hash.ToLowerInvariant()
        } catch {
            return $null
        }
    }

    # Czy plik lezy w obszarze chronionym (miedzy plikiem a $dir, bez samego $dir):
    #  - folder autobot-skills (zestaw f, zostaje),
    #  - pakiet Pythona autobot/ (katalog z __init__.py albo z podkatalogiem autobot\__init__.py),
    #  - paczka v2 (katalog z AUTOBOT-POLICY.md).
    function Test-Chroniony([System.IO.DirectoryInfo]$katalog) {
        $p = $katalog
        while ($p -ne $null -and ($p.FullName.TrimEnd('\') -ne $root)) {
            if ($p.Name -eq $FolderZostaje) { return $true }
            if (Test-Path -LiteralPath (Join-Path $p.FullName '__init__.py') -PathType Leaf) { return $true }
            if (Test-Path -LiteralPath (Join-Path $p.FullName 'autobot\__init__.py') -PathType Leaf) { return $true }
            if (Test-Path -LiteralPath (Join-Path $p.FullName 'AUTOBOT-POLICY.md') -PathType Leaf) { return $true }
            $p = $p.Parent
        }
        return $false
    }

    # Warunek dla zip: w tym samym folderze lub wyzej (az do $dir wlacznie) istnieje katalog
    # autobot-skills z plikiem-swiadkiem o zgodnym hashu.
    function Test-FolderZostajeObok([System.IO.DirectoryInfo]$katalog) {
        $p = $katalog
        while ($p -ne $null) {
            $kandydat = Join-Path $p.FullName $FolderZostaje
            if (Test-Path -LiteralPath $kandydat -PathType Container) {
                $swiadek = Join-Path $kandydat $SwiadekRel
                if ((Test-Path -LiteralPath $swiadek -PathType Leaf) -and ((Get-Sha256 $swiadek) -eq $SwiadekHash)) {
                    return $true
                }
            }
            if ($p.FullName.TrimEnd('\') -eq $root) { break }
            $p = $p.Parent
        }
        return $false
    }

    # --- Wyszukiwanie: rekurencyjne przegladanie $dir (tylko odczyt), filtr po DOKLADNEJ nazwie ---
    # (-Recurse dotyczy wylacznie wyszukiwania; polecenie usuwania ponizej go nie uzywa)
    $bledyOdczytu = $null
    $wszystkie = @(Get-ChildItem -LiteralPath $dir -Recurse -File -Force -ErrorAction SilentlyContinue -ErrorVariable bledyOdczytu)

    $wiersze = New-Object System.Collections.ArrayList
    $doUsuniecia = New-Object System.Collections.ArrayList
    $znaleziono = 0

    foreach ($f in $wszystkie) {
        $nazwa = $null
        $wielkoscLiter = $false
        foreach ($k in $Lista.Keys) {
            if ($f.Name -ceq $k) { $nazwa = $k; break }
            if ($f.Name -ieq $k) { $wielkoscLiter = $true }
        }
        if ($nazwa -eq $null -and -not $wielkoscLiter) { continue }   # spoza listy: nie dotykamy

        $znaleziono++
        $wDir = $f.FullName.StartsWith($root + '\', [System.StringComparison]::OrdinalIgnoreCase)
        $hash = Get-Sha256 $f.FullName
        $hashPokaz = $hash
        if ($hash -eq $null) { $hashPokaz = '(nie odczytano)' }

        if (-not $wDir) {
            $decyzja = 'POZA FOLDEREM (link lub skrot) ' + $Myslnik + ' pomijam'
        } elseif ($nazwa -eq $null) {
            $decyzja = 'NAZWA ROZNI SIE WIELKOSCIA LITER ' + $Myslnik + ' pomijam'
        } elseif (Test-Chroniony $f.Directory) {
            $decyzja = 'FOLDER CHRONIONY (autobot-skills / autobot / v2) ' + $Myslnik + ' pomijam'
        } elseif ($hash -eq $null) {
            $decyzja = 'BLAD ODCZYTU HASHA ' + $Myslnik + ' pomijam'
        } elseif ($hash -ne $Lista[$nazwa]) {
            $decyzja = 'NAZWA ZGODNA, HASH INNY ' + $Myslnik + ' pomijam'
        } elseif (($nazwa -eq 'autobot-skills.zip') -and -not (Test-FolderZostajeObok $f.Directory)) {
            $decyzja = 'OSTRZEZENIE: brak folderu autobot-skills obok/wyzej ' + $Myslnik + ' pomijam'
        } else {
            $decyzja = 'ZAKWALIFIKOWANY (nazwa i hash zgodne)'
            [void]$doUsuniecia.Add([pscustomobject]@{ Plik = $f; Nazwa = $nazwa })
        }

        [void]$wiersze.Add([pscustomobject][ordered]@{
            Sciezka = $f.FullName
            Rozmiar = $f.Length
            SHA256  = $hashPokaz
            Decyzja = $decyzja
        })
    }

    if ($wiersze.Count -gt 0) {
        $wiersze | Format-Table -Property Sciezka, Rozmiar, SHA256, Decyzja -AutoSize -Wrap | Out-String -Width 4096 | Write-Host
    } else {
        Write-Host 'Nie znaleziono zadnego pliku o nazwie z listy kasacji.'
    }
    if ($bledyOdczytu -and $bledyOdczytu.Count -gt 0) {
        Write-Host ('Uwaga: ' + $bledyOdczytu.Count + ' elementow nie dalo sie przejrzec (brak dostepu). Te miejsca pominieto.') -ForegroundColor Yellow
    }

    # --- Usuwanie: tylko w trybie $true, pojedynczo, przez dokladna sciezke, do Kosza ---
    $usunieto = 0
    $pominieto = $znaleziono - $doUsuniecia.Count
    $bledyUsuwania = 0

    if (($Usun -is [bool]) -and $Usun) {
        if ($doUsuniecia.Count -gt 0) { Add-Type -AssemblyName Microsoft.VisualBasic }
        foreach ($d in $doUsuniecia) {
            $sciezka = $d.Plik.FullName
            # Ponowne sprawdzenie hashu tuz przed usunieciem (plik mogl sie zmienic).
            if ((Get-Sha256 $sciezka) -ne $Lista[$d.Nazwa]) {
                Write-Host ('POMINIETO (hash zmienil sie przed usunieciem): "' + $sciezka + '"') -ForegroundColor Yellow
                $pominieto++
                continue
            }
            try {
                [Microsoft.VisualBasic.FileIO.FileSystem]::DeleteFile(
                    $sciezka,
                    [Microsoft.VisualBasic.FileIO.UIOption]::OnlyErrorDialogs,
                    [Microsoft.VisualBasic.FileIO.RecycleOption]::SendToRecycleBin)
                if (Test-Path -LiteralPath $sciezka) {
                    Write-Host ('BLAD: plik nadal istnieje: "' + $sciezka + '"') -ForegroundColor Red
                    $bledyUsuwania++
                } else {
                    Write-Host ('PRZENIESIONO DO KOSZA: "' + $sciezka + '"') -ForegroundColor Green
                    $usunieto++
                }
            } catch {
                Write-Host ('BLAD usuwania "' + $sciezka + '": ' + $_.Exception.Message) -ForegroundColor Red
                $bledyUsuwania++
            }
        }
    }

    Write-Host ''
    Write-Host '===== PODSUMOWANIE ====='
    Write-Host ('Znaleziono plikow o nazwie z listy: ' + $znaleziono)
    Write-Host ('Zakwalifikowano (nazwa i hash):     ' + $doUsuniecia.Count)
    if (($Usun -is [bool]) -and $Usun) {
        Write-Host ('Przeniesiono do Kosza:              ' + $usunieto)
        Write-Host ('Pominieto:                          ' + $pominieto)
        Write-Host ('Bledy usuwania:                     ' + $bledyUsuwania)
    } else {
        Write-Host  'Usunieto:                           0 (tryb podgladu)'
        Write-Host ('Pominieto:                          ' + $pominieto)
        Write-Host  'Aby usunac: zmien $Usun = $false na $Usun = $true i wklej skrypt ponownie.'
    }
}
```

SHA-256 pliku `usun_pliki_autobot.ps1` (identyczny z blokiem powyzej): `72d84a069ff70cfbf7df288d81da8b92b8057dd640f83519275a964c889d9afe`

## Co skrypt usuwa (zatwierdzona lista kasacji — nic ponad nia)

| Nazwa (dokladna, wielkosc liter ma znaczenie) | SHA-256 (inwentarz 8.5) | Rozmiar w archiwum [B] |
|---|---|---|
| `autobotSKILL.md` | `b7ce490ca518104265a7670a68e9c68a5f6978bfca22cf3a4f3a00144b3d6812` | 18368 |
| `civautobotSKILL.md` | `fd1f90877fab5dd83ca488e554fe54cf0abd85f17da53519fae6d1fb1177372b` | 22224 |
| `AutoBot-Orkiestrator-SKILL.md` | `8f3efd7f7f027af556a5a723163e752fbc3e952b1547e5f4f2873535a1d37829` | 7799 |
| `AutoBot-Orkiestrator-v1.1.0-SKILL.md` | `626eeb5308a843abc1e3b44801feb9b7cf0b637271e21dc4f3fb3a9486a29788` | 24917 |
| `skasujzmergowanegalezieautobot.sh` | `9df2c59f72658b045d1fdaeb69be8f899aa097809d4688f3dea8e219ad6aa265` | 2487 |
| `autobot-skills.zip` | `44f63cfb3389aef2f3d587cd47041d395a79b5b5660dbaa9b1a1e30e37a6a242` | 49563 |

Pozycja 6 listy kasacji ("jedna z dwoch kopii zestawu f") jest zrealizowana jako usuniecie `autobot-skills.zip` i zachowanie folderu `autobot-skills/` (inwentarz: "Zachowac: `autobot-skills/` (jedna kopia)"). Zip jest kwalifikowany tylko gdy w jego folderze lub wyzej (do `$dir` wlacznie) istnieje katalog `autobot-skills`, a w nim `skills\autobot-orchestrator\SKILL.md` o SHA-256 `6e8e071694bd1a51abda87cea0f758bd5b29492693d613323a85777b2b0a72b9` (inwentarz 8.5) — to dodatkowy, zaostrzajacy warunek: zip nie zniknie, jesli folder-kopia jest pusty lub inny. W przeciwnym razie: `OSTRZEZENIE: brak folderu autobot-skills obok/wyzej — pomijam`.

## Zabezpieczenia (S-P8)

- Domyslnie podglad; usuwanie tylko gdy `$Usun` jest dokladnie wartoscia logiczna `$true` (tekst `'true'` nie wystarczy).
- Kwalifikacja = dokladna nazwa (`-ceq`) **i** pelny SHA-256 (`Get-FileHash -Algorithm SHA256`); hash liczony ponownie tuz przed usunieciem.
- Usuwanie: `[Microsoft.VisualBasic.FileIO.FileSystem]::DeleteFile(<pelna sciezka>, OnlyErrorDialogs, SendToRecycleBin)` — do Kosza, pojedynczo, jedna dokladna sciezka na wywolanie; brak `Remove-Item`, brak `-Recurse` w usuwaniu, brak symboli wieloznacznych, brak usuwania katalogow. `-Recurse` wystepuje wylacznie w `Get-ChildItem` (wyszukiwanie, tylko odczyt).
- Pomija i raportuje: `NAZWA ZGODNA, HASH INNY — pomijam`; `NAZWA ROZNI SIE WIELKOSCIA LITER — pomijam`; `BLAD ODCZYTU HASHA — pomijam`; `FOLDER CHRONIONY (autobot-skills / autobot / v2) — pomijam` (plik pod katalogiem `autobot-skills`, pod pakietem Pythona `autobot/` rozpoznanym po `__init__.py`, albo pod paczka v2 rozpoznana po `AUTOBOT-POLICY.md`); `POZA FOLDEREM (link lub skrot) — pomijam`.
- Pliki spoza listy nie sa nawet hashowane ani wypisywane.
- Myslnik "—" w komunikatach jest budowany z kodu (`[char]0x2014`), a plik .ps1 jest czystym ASCII — Windows PowerShell 5.1 czyta pliki bez BOM w kodowaniu ANSI, a bajty UTF-8 myslnika zawieraja bajt 0x94, ktory 5.1 traktuje jak cudzyslow i ktory zepsulby parsowanie.

## Weryfikacja wykonana przez Operatora (runda 1)

- **Hashe:** swieza ekstrakcja `Autobot.rar` (`unrar x`, tylko odczyt) do nowego pustego katalogu `scratchpad/p003-rar-op/`; `sha256sum` 6 plikow z listy = hashe w skrypcie = hashe z inwentarza 8.5: **6/6 zgodnych**. Plik-swiadek `autobot-skills/skills/autobot-orchestrator/SKILL.md` = `6e8e071694bd1a51abda87cea0f758bd5b29492693d613323a85777b2b0a72b9`, zgodny z `$SwiadekHash` w skrypcie i z inwentarzem 8.5 (poprawka rundy 2: wczesniejszy skrot `…aa964` byl bledny — ta koncowka nalezy do `MAIN-AGENT-ORCHESTRATOR-FAILURE-PATTERNS.md`; ponownie sprawdzone `sha256sum` na swiezej ekstrakcji `scratchpad/p003-r2-op/`). Zadnego pliku z archiwum nie uruchomiono.
- **Skladnia: NIE URUCHOMIONO.** `pwsh` nie jest dostepny w kontenerze (`which pwsh powershell` = brak), wiec parser PowerShell nie zostal uzyty, a skrypt nie byl uruchamiany. Wykonano: przeglad linia po linii (ponizej), kontrola ASCII (`grep -P '[^\x00-\x7F]'` = 0 trafien), bilans nawiasow poza literalami i komentarzami: `( )` 73/73, `{ }` 46/46, `[ ]` 20/20.

### Przeglad linia po linii (skrot)

| Linie | Konstrukcja | Ocena 5.1 / 7 |
|---|---|---|
| 9–10 | `$dir` w apostrofach (spacje, `_`, `-`, `.` bez interpretacji), `$Usun = $false` | OK / OK |
| 13 | `& { ... }` — blok, w ktorym `return` przerywa bez zamykania okna konsoli | OK / OK |
| 15–22 | `[ordered]@{}` (PS 3+) | OK / OK |
| 37–40 | `Test-Path -LiteralPath ... -PathType Container`, `return` | OK / OK |
| 43–49 | `Get-FileHash -LiteralPath -Algorithm SHA256` (PS 4+), `try/catch` | OK / OK |
| 55–65, 69–83 | funkcje w bloku; `Join-Path` bez `-Resolve` (bez rozwijania wzorcow), `Test-Path -LiteralPath` | OK / OK |
| 88 | `Get-ChildItem -LiteralPath -Recurse -File -Force -ErrorVariable` (`-File` od PS 3) | OK / OK |
| 96–101 | porownanie `-ceq` / `-ieq` po kluczach listy | OK / OK |
| 104–124 | lancuch `if/elseif`, `StartsWith(..., OrdinalIgnoreCase)` | OK / OK |
| 126–131 | `[pscustomobject][ordered]@{}` | OK / OK |
| 135 | `Format-Table -AutoSize -Wrap \| Out-String -Width 4096 \| Write-Host` | OK / OK |
| 149 | `Add-Type -AssemblyName Microsoft.VisualBasic` | OK / OK (PS 7 na Windows: Microsoft.VisualBasic.Core) |
| 159–162 | `DeleteFile(string, UIOption, RecycleOption)` — wywolanie wieloliniowe w nawiasach | OK / OK |

### Ryzyka (do oceny przez Evaluatora i wlasciciela)

1. Brak testu parserem i brak uruchomienia — skladnia oceniona tylko przegladem.
2. OneDrive "tylko online": `Get-FileHash` wymusi pobranie pliku przez klienta OneDrive (to klient OneDrive, nie skrypt, laczy sie z siecia); przy braku polaczenia wiersz dostanie `BLAD ODCZYTU HASHA — pomijam`.
3. Kosz i OneDrive: plik synchronizowany trafia do Kosza Windows i do Kosza OneDrive online; obie kopie sa przywracalne przez ograniczony czas (polityka OneDrive/organizacji).
4. `PS 7` + `SendToRecycleBin`: obslugiwane w .NET na Windows; gdyby wywolanie rzucilo wyjatek, plik zostaje, a skrypt wypisuje `BLAD usuwania`.
5. Linki symboliczne/skroty katalogow wewnatrz `$dir`: Windows PowerShell 5.1 moze w nie wchodzic przy `-Recurse`; plik i tak musi miec nazwe i hash z listy.
6. Bardzo dluga sciezka (>260 znakow) w 5.1 moze nie zostac przejrzana — zostanie zgloszona jako "elementow nie dalo sie przejrzec" i pominieta.
7. Wklejanie: wklejac caly blok naraz; jesli zasady wykonywania (ExecutionPolicy) blokuja uruchomienie pliku .ps1, wklejenie tekstu w okno konsoli dziala bez zmiany tych zasad.
