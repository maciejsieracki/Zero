# ZERO-PROCES-003-komenda-usuwania-plikow

WYZWALACZ:  decyzja wlasciciela ECHO-013 (2026-11-27): przygotowac konkretna komende PowerShell do wklejenia, usuwajaca nieaktywne pliki zasad AutoBot z dysku OneDrive. Zalezy od zamkniecia ZERO-PROCES-002 (ECHO-011): lista kasacji (inwentarz, sekcja 7) i hashe (sekcja 8.5) musza byc zatwierdzone przez Final Control.
GOAL:       Istnieje zweryfikowany skrypt PowerShell, ktory po wklejeniu przez wlasciciela usuwa ze wskazanego folderu wylacznie pliki zasad AutoBot o nazwie i hashu SHA-256 zgodnych z zatwierdzona lista kasacji, domyslnie w trybie podgladu, z instrukcja uzycia.
KONIEC:     PRAWDA gdy scenariusze S-P7..S-P10 przechodza. Zadna zmiana poza allowlista.

ZADANIE: przygotuj dwa pliki w katalogu tematu: `usun_pliki_autobot.ps1` (skrypt) i `README.md` (5 krokow uzycia oraz ten sam skrypt w bloku kodu do wklejenia w czacie).
Skrypt, po uruchomieniu przez wlasciciela w Windows PowerShell 5.1 lub PowerShell 7:
1. Zmienna `$dir` ma wartosc domyslna dokladnie: `C:\Users\Maciej Sieracki\OneDrive - NASTER S.A\_NOWA_STRUKTURA\Caude` (zapis "Caude" zachowany; wlasciciel moze ja zmienic na poczatku skryptu).
2. Przeszukuje `$dir` rekurencyjnie plikow o DOKLADNYCH nazwach z listy kasacji z inwentarza (sekcja 7 pliku `docs/proces/ZERO-PROCES-002-inwentarz-zasad-autobot/inwentarz.md`): `autobotSKILL.md`, `civautobotSKILL.md`, `AutoBot-Orkiestrator-SKILL.md`, `AutoBot-Orkiestrator-v1.1.0-SKILL.md`, `skasujzmergowanegalezieautobot.sh`, `autobot-skills.zip`. Liczy SHA-256 (`Get-FileHash`) i kwalifikuje do usuniecia tylko pliki, ktorych nazwa I pelny hash zgadzaja sie z hashami z sekcji 8.5 inwentarza (hashe wpisz do skryptu; Evaluator porowna je z archiwum).
3. Domyslnie tryb podgladu (zmienna `$Usun = $false`): wypisuje tabele (sciezka, rozmiar, hash, decyzja) i niczego nie usuwa. Po zmianie na `$true` przenosi pliki do Kosza (`Microsoft.VisualBasic.FileIO.FileSystem.DeleteFile` z `SendToRecycleBin`), pojedynczo, przez sciezke dokladna; bez `-Recurse`, bez symboli wieloznacznych, bez usuwania katalogow.
4. Plik o zgodnej nazwie, ale innym hashu: nie usuwa, wypisuje "NAZWA ZGODNA, HASH INNY — pomijam".
5. `autobot-skills.zip` kwalifikuje tylko wtedy, gdy w tym samym folderze lub wyzej w `$dir` istnieje katalog `autobot-skills` (zip jest duplikatem folderu, ktory zostaje); w przeciwnym razie ostrzega i pomija.
6. Nie dotyka: folderu `autobot-skills`, pakietu `autobot/` (Python), paczki v2 ani niczego spoza listy. Konczy podsumowaniem (ile znaleziono, ile zakwalifikowano, ile usunieto/pominieto).
7. Obsluguje sciezki ze spacjami (`-LiteralPath`, cudzyslowy), nie wymaga uprawnien administratora, nie laczy sie z siecia.

REGULA PRZECIW SAMOOSZUKIWANIU:
- Zakaz uznania skryptu za poprawny bez porownania wpisanych hashy z hashami z inwentarza (sekcja 8.5) i z faktycznych plikow archiwum.
- Zakaz uruchamiania skryptu w kontenerze (to Windows/OneDrive) oraz uruchamiania jakichkolwiek plikow z archiwum.
- Zakaz usuwania po samej nazwie pliku; zakaz domyslnego trybu usuwania; zakaz symboli wieloznacznych w poleceniach usuwania.
- Jesli `pwsh` jest dostepny w kontenerze, sprawdz skladnie parserem; jesli nie jest, wpisz jawnie NIE URUCHOMIONO, zrob przeglad skladni linia po linii i wypisz ryzyka (nie udawaj testu).
- Zakaz edycji plikow poza allowlista; zakaz rozszerzania listy kasacji ponad zatwierdzona.

PROCEDURA NAPRAWCZA PRZY FAIL: Evaluator numeruje zarzuty (plik, linia skryptu, punkt listy, reprodukcja); Operator (w obronie) odpowiada na kazdy numer; po werdykcie NAPRAW poprawia tylko wskazane linie skryptu.

ALLOWLISTA:
  - `docs/proces/ZERO-PROCES-003-komenda-usuwania-plikow/usun_pliki_autobot.ps1`
  - `docs/proces/ZERO-PROCES-003-komenda-usuwania-plikow/README.md`
ZAKAZANE BEZWZGLEDNIE: wszystko inne w repozytorium (w tym `autobot/`, `scenariusze/`, `docs/analiza/`, `docs/research/`, inwentarz — tylko odczyt), uploads, wykonywanie skryptow z archiwum i wlasnego skryptu, usuwanie jakichkolwiek plikow, sekrety.

MIEJSCE PRACY: `docs/proces/ZERO-PROCES-003-komenda-usuwania-plikow/`
BAZA:          HEAD galezi roboczej; zrodlo hashy: archiwum `/root/.claude/uploads/3337db06-529b-5b00-81d6-a0a7013a451d/a4edf6ca-Autobot.rar` (tylko odczyt, swieza ekstrakcja do nowego pustego katalogu w scratchpadzie)
OBIEG:         Operator -> Evaluator (10 punktow) -> Obrona przy zarzutach -> Final Control (per zarzut) -> Integration

RUNDA: 0 z 3
