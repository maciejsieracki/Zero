# ZERO — A01 Biblia serialu (pakiet produkcyjny E01, narzędzie docelowe Kling 4.0)

**ID tematu:** ZERO-PAKIET-001-biblia-serialu (pozycja A01 pakietu; fala 1; ECHO-040, ECHO-041, ECHO-042)
**Data:** 2026-11-28
**Rola i runda:** Operator (Sonnet 5.5), runda 3 z 3 — poprawki po werdykcie NAPRAW (runda 2): E-2-1 (Q2 B i C: twierdzenia o Klingu oznaczone BRAK DANYCH/NIEPOTWIERDZONE), E-2-2 (KB-02, KB-19 i zasada 4 w 7.1: PROPOZYCJA REZYSERSKA), E-2-3 (TE-25, napis „Adam” z `SC L273`), E-2-4 (ls w 0.5, stany i ścieżka w 8.2), E-2-5 (legenda prefiksów, `TN-nn` zamiast `T-nn`); P-2-1 dotyczy orkiestratora (poza allowlistą). Poprawki rundy 2: E-1-1 (rozdzielone ID: motywy `MO-nn`, miejsca `LK-nn`), E-1-2 (wiersz ARS w 0.3/0.4, ujednolicone opisy rozpiski), E-1-3 (legenda toru M, status PROPOZYCJA/ROZBIEŻNOŚĆ w 3.2), P-1 (odświeżone hashe i stan decyzji po ECHO-043..045 w 0.2/0.4/0.5)
**Zakres:** odcinek E01 „ADAM” (szczegółowo tylko na poziomie biblii serialu; sceny nie są rozpisywane ujęcie po ujęciu — Scena 1 ma osobny plik ZERO-PROD-002); odcinek E02 „EWA” tylko jako informacja o serialu; E03 — jedna linia (sekcja 3.5, ECHO-005).
**Narzędzie docelowe:** Kling 4.0 (ECHO-037). Plik **nie wybiera narzędzia ani wariantu** (ECHO-027) — wariant 4.0 / 4.0 Flash i droga uruchomienia (MCP / API) zostają przy właścicielu.
**Status:** wytwór Operatora do kontroli. Niczego nie wygenerowano (obrazy, głosy, wideo), nie wywołano sieci, API ani MCP, nie założono kont ani kluczy.

> **Zasada pliku.** Ten plik jest jedną „mapą serialu” dla modelu, reżysera i montażysty. **Nie dopisuje faktów kanonu.** Wszystko, co jest „od reżysera”, ma etykietę **PROPOZYCJA REZYSERSKA**. Wszystko, co zależy od decyzji właściciela, jest pytaniem ABC (sekcja 9). Tam, gdzie źródła się różnią, zapisane są **obie wersje z cytatami** i nie ma rozstrzygnięcia (G3).

---

## 0. Legenda, hierarchia źródeł, źródła z SHA-256

### 0.1 Legenda oznaczeń

| Oznaczenie | Znaczenie |
|---|---|
| **PROPOZYCJA REZYSERSKA** | element „od reżysera” (kadr, przejście, rytm, sformułowanie, wersja EN) spoza scenariusza E01; nie jest kanonem (G2, G3, ECHO-041) |
| **BRAK DANYCH** | źródła milczą; obok podane, gdzie szukano i jak sprawdzić |
| **ROZBIEŻNOŚĆ ŹRÓDEŁ** | dwa źródła mówią co innego; zapisane są dwa cytaty i status; brak rozstrzygnięcia |
| **NIEPOTWIERDZONE** | twierdzenie naukowe, branżowe lub relacja rzędu 4, której nie sprawdzono w źródle rzędu 1 |
| **[KANON]** / **[PRODUKT]** / **[TECH]** | typ decyzji wg ANALIZA-003: kanoniczna właściciela / produktowa-kosztowa właściciela / porządkowa bez zmiany treści |
| **kanon SC** | fakt wprost z tekstu scenariusza E01 (rząd 1) |
| **materiał rz.4** | dokument produkcyjny, raport lub notatka (rząd 4) — poszlaka, nie rozstrzyga |
| **zał.** | założenie robocze, nie fakt (np. 24 fps) |
| **Tor: A / B / M** (kolumna w 3.1) | **A** = sceny toru A (`SC L12`); **B** = bloki przeszłości P1–P4 (`SC L19`); **M** = wstawka medialna T-10, T-7, T-5, T-1 — wartość **M** jest klasyfikacją redakcyjną tego pliku (**PROPOZYCJA REZYSERSKA**), nie kategorią SC: SC zalicza media do wątków toru A (3.2) |
| **Prefiksy ID** (runda 3, zarzut E-2-5: legenda uzupełniona) | **ID własne tego pliku:** `MO-nn` motywy (1.3); `TN-nn` ton (1.4); `ZS-nn` zasady stałe i `GM-nn` granice modelu (2); `O-nn` osoby (5.1); `RL-nn` relacje (5.2); `LK-nn` miejsca (5.4); `F-nn` fakty o świecie (5.5); `TE-nn` teksty ekranowe (5.6); `RK-nn` rozbieżności kanoniczne i produkcyjne istotne dla pakietu (6.1); `RP-nn` rozbieżności produkcyjne wpływające na zasady stałe (6.2); `KB-nn` kadry bez postaci z SC i materiałów (7.3); `KP-nn` kadry spoza SC (7.4); `PR-nn` przejścia (7.5); `ZERO-PAKIET-001-Qn` pytania ABC (9). **Segmenty odcinka** (3.1): `S1`–`S15` sceny, `P1`–`P4` bloki przeszłości, `W-10`, `W-7`, `W-5`, `W-1` wstawki medialne (liczba po `W-` = dzień T minus). **Oś czasu:** zapis `T-14`, `T-10`, `T-9`, `T-7`, `T-5`, `T-1`, `T0`, `T+8` (bez zera wiodącego, z jedną lub dwiema cyframi) = dzień osi, nie identyfikator; prefiks tonu to `TN-`, a nie `T-` — rozdzielone w rundzie 3 (dawne `T-01`..`T-09`; zarzut E-2-5). **ID cudze:** `R-nn`, `Q-nn`, `L-nn`, `E01-nn`, `N-nn`, `D-nn` (raporty AN1, AN3), `Dnn` (`PLAN`), `ECHO-nnn` (`DECYZJE`), `Kn` i `Un` (klipy i ujęcia `P002`) — odnoszą się do plików wejściowych. Dawne `M-nn` (motywy i miejsca jednocześnie) zastąpione w rundzie 2 (zarzut E-1-1) |

### 0.2 Hierarchia przy sprzeczności (zlecenie)

1. scenariusz E01 `scenariusze/ZERO_mini_serial_E01_ADAM_rev.md` (rząd 1, rozstrzyga treść scenariusza);
2. decyzje właściciela `autobot/DECYZJE.md` (ECHO);
3. raport ANALIZA-003 i dokumenty produkcyjne (rząd 4).

Gdy decyzja właściciela (ECHO) jest nowsza od tekstu scenariusza i go nie zmienia (np. ECHO-020), plik zapisuje obie wersje, oznacza status i **nie wybiera** — decyzja o zapisie w scenariuszu należy do właściciela i osobnego tematu poprawek.

**Stan decyzji na rundę 2.** `DECYZJE L51` `Tresc pierwszego i drugiego serialu jest zaakceptowana.` (ECHO-045): scenariusze E01 i E02 (`_rev`) są podstawą produkcji, ale `DECYZJE L51` `akceptacja tresci NIE rozstrzyga konkretnych decyzji kanonicznych` — akceptacja treści nie rozstrzyga decyzji kanonicznych ANALIZA-001 i ANALIZA-002 ani sprzeczności wewnątrz scenariuszy (te czekają na jednoznaczną odpowiedź właściciela) — rejestr rozbieżności (sekcja 6) i pytania ABC (sekcja 9) pozostają otwarte. ECHO-043 (pula 4 tematów) i ECHO-044 (podział sekwencji E01 na ujęcia, tematy ZERO-UJECIA) nie zmieniają faktów ani zasad tego pliku.

### 0.3 Konwencja cytatów i skróty

Cytat ma postać: `SKRÓT Lnn` + fragment w odwrotnych apostrofach = dosłowny fragment jednej linii pliku (numer linii pliku, nie sceny). `SKRÓT Lnn–mm` = zakres linii. „AN3 R-14” = pozycja R-14 raportu ANALIZA-003 (ID, nie linia).

**Uwaga o kolizji oznaczeń.** W raporcie ANALIZA-003 skróty `A01`, `A02`, `A08` oznaczają pliki **archiwum** (nota reżyserska, charakterystyki postaci, noty techniczne). W pakiecie produkcyjnym `A01`–`A09` oznaczają pliki **pakietu** (A01 = ten plik). Dlatego w tym pliku pliki archiwum mają prefiks **ARCH-** (np. ARCH-01 = `01_nota_rezyserska.md`), a pliki pakietu zawsze pełne nazwy (np. `A02_przewodnik_wizualny.md`). Podobnie plik kategorii E `E01_rejestr_decyzji_kanonicznych.md` nie jest odcinkiem E01.

Skróty `ARS`, `AHO`, `ADR`, `KS` itd. odsyłają do wierszy tabeli 0.4; `ARS` = rozpiska sekundowa E01 (`ZERO_E01_rozpiska_sekundowa.md`, archiwum), cytowana tylko jako `ARS Lnn` (obecnie RK-15, `ARS L1554`).

Bazy ścieżek: `A/` = `/tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/zero-extract/Zero/ZERO_DO_PRZENIESIENIA/`; `U/` = `/root/.claude/uploads/3337db06-529b-5b00-81d6-a0a7013a451d/` (pliki wgrane przez właściciela; prefiks hash w nazwie pliku pominięty w skrótach).

### 0.4 Źródła (pliki wejściowe, tylko odczyt) z SHA-256

SHA-256 policzone `sha256sum` 2026-11-28 przed pisaniem pliku i ponownie po zakończeniu (sekcja 0.5). „Czytano” = ile pliku faktycznie przeczytano w tym temacie.

| Skrót | Plik | SHA-256 | Rząd | Czytano / użycie |
|---|---|---|---|---|
| SC | `scenariusze/ZERO_mini_serial_E01_ADAM_rev.md` (1263 linie) | `b0264c950cbafe7181234554136f6cb65a826c12c88a96730917f9c0825f4340` | 1 | w całości; hash zgodny z `scenariusze/MANIFEST.sha256` |
| MF | `scenariusze/MANIFEST.sha256` | `ae826cc3989822ace0030574c09e60d4a235d63d8ae5f23e3a143d2f3221b205` | — | w całości (kontrola hasha SC) |
| SC2 | `scenariusze/ZERO_mini_serial_E02_EWA_rev.md` | `1166c23dd0652dc76607167d9452263f036777a3ec0dbe1f35035c5610b4b093` | 1 (dla E02) | tylko nagłówek, nota, obsada, prolog, lista nagłówków scen — wyłącznie informacja o serialu (sekcja 3.4) |
| DECYZJE | `autobot/DECYZJE.md` | `2fcf6e47cc3f0cb1aa7d8b8345cae4a860616e2c0cc7ad32ad8d2e3f969d3866` (stan przy czytaniu w rundzie 1: ECHO-001..042); stan na rundę 2 (2026-11-28) `598d7a438b537ac1dc316fe2ee341a83a6125afc2c0a9c4da03598b700d43aab` (commity orkiestratora dopisały ECHO-043 na L49, ECHO-044 na L50 i ECHO-045 na L51; linie L1–L48 bez zmian: `sha256(L1–L48)` = `5d7bf2dfa30598fa9d737cd3128aad92e38688de5f216f2fd9255355adcd885c` przed i po) | 2 | w całości (ECHO-001..042 w rundzie 1; w rundzie 2 dodatkowo ECHO-043..045 — patrz 0.2: nie zmieniają treści pliku) |
| WYBORY | `autobot/WYBORY_TRWALE.md` | `ee45294c95ca493afaa6ef61a6ba2c4edf0dc53699fbf46d0adff0aa05e97f7b` | — | granice G1–G7 |
| SCEN | `autobot/SCENARIUSZE.md` | `d4da9697e1428b700f627daaee5a7ce01efdb41499ab4ab1961499738b9aa833` (stan przy czytaniu w rundzie 1, L1–L171); stan na rundę 2 `0b53bd1801882cdd9bcc065df7a095d330dae6626a7834f659fcd648a6ff1e13` (orkiestrator dopisał na końcu sekcję `ZERO-UJECIA-001..023`, S-J1..S-J6; `sha256(L1–L171)` = `d4da9697…a833`, czyli bez zmian względem stanu z rundy 1) | — | scenariusze S-D1..S-D7 (bez zmian) |
| REJ | `autobot/REJESTR_TEMATOW.md` | `d553bab00ab694b232876498369ac5e35eb3bc91de1bb1c3430d95b2cf7770cb` | — | tylko status tematów pakietu w 8.2 (odczyt, runda 3) |
| ZLEC | `autobot/zlecenia/ZERO-PAKIET-001-biblia-serialu.md` | `fadcb16ac9284431265db1bea8f7bc192ea7f58f534da826571d6cee288818ed` | — | zlecenie tego tematu |
| ZPL2 | `autobot/zlecenia/ZERO-PLAN-002-pakiet-produkcyjny.md` | `5328d1b703f20abb5ce221db5abee9e434ca68edc5f831986e4e801b62284233` | — | struktura pakietu A–E, zasada wsadu dla modelu |
| ZPK | `autobot/zlecenia/ZERO-PAKIET-002-przewodnik-wizualny.md`, `ZERO-PAKIET-011-rejestr-decyzji.md`, `ZERO-PAKIET-023-katalog-ujec-uzupelniajacych.md`, `ZERO-PROD-002-scena1-kling.md`, `ZERO-PROD-003-scena1-kling-tekst.md` | `6b9e2303db7c77f38e91f0384c60e6acb882dcbc61b7a48b5c3de3e69bcb7654`; `e01a3e97c7474cfab8cd9327b5d37ba54c2e4a2b13967d18c0de386d24ffd306`; `4b98677096d9829c2b954f9a27b44b46df65c930a85e0c8e4ee2926d724c11f7`; `dfd7a7cb622d41e1e5ca3903abc14b784afb5e32e611cc19bdb288f21a853ea7`; `1692058a70d3d5243866d2e504204e96bb3d83780cf486b72e186733de045495` | — | zlecenia pokrewne: nazwy plików pakietu, zakres sąsiednich pozycji (odczyt wycinków) |
| PLAN | `PLAN_WDROZENIA_ZERO.md` | `8aec58877dbcf25ddda090cfd3bd021a7f0884b7001ca1fee4191f3567062171` | 4 | L1–112 w całości, reszta wyszukiwaniem (D1–D16) |
| AN1 | `docs/analiza/ZERO-ANALIZA-001-e01-logika-timing-napiecie/raport.md` | `69157791ed43dc12b50ff71fe979b39ab2ade93d88fe0461faa6ec44a12c4839` | 4 | sekcje (a) i (f) w całości, reszta wyszukiwaniem |
| AN1T | `docs/analiza/ZERO-ANALIZA-001-e01-logika-timing-napiecie/tabela_scen.md` | `f07ab61e727e715b755f9adcc05714ce72e1cb096699a039a7e73a988b775d65` | 4 | w całości |
| AN2 | `docs/analiza/ZERO-ANALIZA-002-e02-logika-timing-napiecie/raport.md` | `8bc020602acf7676af78f7c4baace96ee0054a08cf710962383c2b6aca596fcd` | 4 | fragmenty o zasadzie „bez mężczyzn” (informacja o serialu) |
| AN3 | `docs/analiza/ZERO-ANALIZA-003-produkcja-e01-spojnosc/raport.md` | `f5a9a43c127a00d64f3a1889ce390a4808cbc87c864141cef6cf61a7b153dbe1` | 4 | w całości (po kontroli Evaluatora, bez formalnego zamknięcia, niezacommitowany — wejście rzędu 4) |
| AN3T | `docs/analiza/ZERO-ANALIZA-003-produkcja-e01-spojnosc/tabela_rozbieznosci.md` | `34cf3a787b4a69ce4d9f0422cac8648596f25b955d0723bb18a37a2cbe47bd66` | 4 | nagłówek i próbka wierszy (R-01..R-04) |
| E02A | `docs/rozbieznosci/E02_audyt.md` | `20253d0561fe09c7a10a13dbe1f946af52094cbc12bd8a88eb62db67688934e4` | 4 | nagłówek (informacja o E02) |
| R001 | `docs/research/ZERO-RESEARCH-001-porownanie-generatorow-wideo/kling.md` | `acfa1275f3c927908d6946a81309f452072584132df7e948fbf01ba9d3d019f0` | badanie zatw. | w całości |
| R002 | `docs/research/ZERO-RESEARCH-002-audio-i-jezyk-polski/kling.md` | `a6742ebf2a36c0dab9eea06cadfe5cf6cc31a5ff0e0f843cf3eba3e509ca2671` | badanie zatw. | L1–60 (tabele audio i język) |
| R003 | `docs/research/ZERO-RESEARCH-003-api-i-mcp-sterowanie/kling.md` | `7f0058f7e38511cad68e53d2f349c00cac4f726bc8773c7e27d0e170a69ca670` | badanie zatw. | L44–60, L100–116 (parametry API, MCP) |
| R005 | `docs/research/ZERO-RESEARCH-005-zestawienie-zbiorcze/zestawienie_zbiorcze.md` | `a83887cee35b637973197bad62f1025420419fd378e06c2a1acb2969ae902df2` | badanie zatw. | sekcja 1.1 i wiersze Kling |
| R008 | `docs/research/ZERO-RESEARCH-008-omni-vs-kling-jakosc/omni_vs_kling.md` | `d5f4a5b558c94a9e1d3b5860fd7700b913fa5650c1160679509b5dd1940afbc3` | badanie zatw. (wpisy rz.4 = NIEPOTWIERDZONE) | L1–30, L90–102, L136–165 |
| P002 | `docs/produkcja/ZERO-PROD-002-scena1-kling/scena1_kling.md` | `9f1cc804ecbfcdba3ad58236a0d789012d899c184b00b4e723880fc8c932dda2` | produkt | tabela klipów (sek. 4.1), prompty K01, K03, K08, sek. 7–8 |
| ARCH-01 | `A/ZERO_E01_produkcja/01_nota_rezyserska.md` | `a8d02ff0952ed38ea0ca6cdc95e557179f46a9b2e13b6abfad2914b69ec4f774` | 4 | w całości |
| ARCH-02 | `A/ZERO_E01_produkcja/02_charakterystyki_postaci.md` | `96db68af07fc1c25ada7bf4032b4bf57f315e7d3369b4c3974a28ef377434f12` | 4 | w całości |
| ARCH-08 | `A/ZERO_E01_produkcja/08_noty_techniczne.md` | `8f173fc023b33fa15b0eddf1f878c1f7444888f784b93100827b9b8bce8293fa` | 4 | w całości |
| ADR | `A/ZERO_produkcja_flow/ZERO_decyzje_rewizja.md` | `97e2508fd3298463ffd8056977514e5ec454e5590a9ff9552e6bab4663f08b33` | 4 | w całości |
| AHO | `A/ZERO_HANDOFF_przekazanie.md` (stan na 8.06.2026) | `0d9740dd31f397275576f4acc1b0f5a0659ae1baa727716745fc6f1d5a3040a8` | 4 | L1–135 |
| KS | `A/ZERO_kontekst_sesji.md` | `1a1167e888ee2e0fccd12132808b81ea64249054f871dcb18a512d946925117f` | 4 | wyszukiwanie (L247) |
| U03 | `U/4582ead6-03_opisy_wizualne_scen.md` | `36b4c783dec70dfa7889f3fc9db1d137bf9bb361fc4830fb0da1c92cc6431492` | 4 | w całości |
| U04 | `U/8d6c4388-04_dzwiek_i_muzyka.md` | `411551dfe53cc8be238ee20c1741e951d027aee1799baff820d2a8dd6ec6b0f3` | 4 | w całości |
| U05 | `U/d029e8a1-05_inserty_closeup.md` | `e0f4b32d1639b72bf4eedab1bf95dda2fe7134b2d9eac903cb6dd93027e84949` | 4 | w całości |
| U06 | `U/4f2b6ba0-06_przejscia_scen.md` | `bfcf4f77c2bce33a4224e4a2af977b9bed76975d24d4a2568381b377c14670b2` | 4 (nieaktualny w kolejności i napisach, AN3 R-01..R-04) | w całości |
| U07 | `U/758ebb13-07_podtekst_dialogowy.md` | `29f0bd62cd358af71d881cab31674bb76afe5c9d26a7f5207b30ef9839156ba7` | 4 | L1–30 |
| UAF | `U/ee92a910-ZERO_instrukcje_dla_agenta_Flow.md` | `ccd9f2ee35ebe96881502882c1ebaa330201d334dcd4b78f5f36fcaa35427022` | 4 (narzędziowo Flow) | w całości |
| UKS | `U/85b2d98d-ZERO_konsultacja_scenariuszowa.md` | `147a2ac66f5d212b2672840b6266b483e2ac4d85af1a06bf7de44550de89ab22` | 4 (nieaktualny dla E01, AN3 R-63) | L55–80 |
| BS2 | `A/ZERO_produkcja_flow/ZERO_E01_Scena2_beaty_7s_ENG.md` | `a8250b53ecb882f52b26575af8ec4ed32b5d08a936bbcc410a3f88dbe3439c87` | 4 | tylko jedna linia (L10), cytowana w rozbieżności RK-12 |
| BP3 | `A/ZERO_produkcja_flow/ZERO_E01_BlokP3_beaty_7s_ENG.md` | `56546b754f9e23c22623501196cc8363f095b0605a3a516ba68592190f1fa8e6` | 4 | tylko jedna linia (L21), cytowana w rozbieżności RK-18 |
| ARS | `A/ZERO_produkcja_flow/ZERO_E01_rozpiska_sekundowa.md` (1581 linii) | `27a985315822cba2c5387ab9fffa17f5346374d626308476e516dc9dc610c4d0` | 4 (błąd rachunkowy sumy: `AN3 R-14`) | bezpośrednio tylko linia L1554 (suma „ŁĄCZNIE”) i skrót pliku do hasha; ujęcia Sceny 1 przez `P002` (rozpiska nie była czytana linia po linii poza L1554) |

**Pliki z listy wejść zlecenia, z których ten plik nie czerpie faktów:** `docs/przeglad-2026-11-27/*` (ich ustalenia są zweryfikowane w AN1 i AN3, więc cytowane przez te raporty), pozostałe beaty, klipy, `ZERO_INSTRUKCJA_Flow_scena1_ciaglosc.md`, metoda A/B, porównanie Veo vs Kling (wszystkie opisane i zhashowane w AN3 sekcja 1; tu odwołania idą przez ID rozbieżności AN3; wyjątek: rozpiska sekundowa `ARS` — zhashowana w tabeli 0.4, czytana bezpośrednio tylko w linii sumy L1554). **Pliki pakietu zatwierdzone wcześniej:** w chwili rozpoczęcia pisania w `docs/produkcja/pakiet/` nie było żadnego pliku (katalog pusty) — ten plik jest pierwszy (w trakcie pracy w katalogu pojawił się roboczy, niezatwierdzony plik `E01_rejestr_decyzji_kanonicznych.md`, a do rundy 3 także `A02_przewodnik_wizualny.md` i `A03_biblia_postaci.md` — tematy „w toku”, żaden nie został użyty); spójność z pozostałymi pozycjami pakietu opisano jako powiązania (sekcja 10) i do sprawdzenia po ich zatwierdzeniu.

### 0.5 Kontrola zakresu i niezmienności
- **Stan katalogu `docs/produkcja/pakiet/` (runda 3, zarzut E-2-4)** — wynik `ls -la --time-style=long-iso docs/produkcja/pakiet/` z 2026-11-28, godz. 15:11 (kopia; inne tematy zapisują równolegle, więc rozmiary i godziny mogą się już różnić; rozmiar i godzina tego pliku to stan sprzed końcowego zapisu rundy 3):

```
-rw-r--r-- 1 root root 151780 2026-11-28 15:11 A01_biblia_serialu.md
-rw-r--r-- 1 root root 153182 2026-11-28 15:09 A02_przewodnik_wizualny.md
-rw-r--r-- 1 root root 250739 2026-11-28 15:10 A03_biblia_postaci.md
-rw-r--r-- 1 root root 259428 2026-11-28 15:10 E01_rejestr_decyzji_kanonicznych.md
```

  Poza tym `docs/produkcja/ZERO-PROD-002-scena1-kling/` zawiera tylko `scena1_kling.md` (pliku `scena1_kling_tekst.txt` nie ma). Tabela 8.2 opiera się na tym wyniku.
- **Zmieniony plik:** wyłącznie `docs/produkcja/pakiet/A01_biblia_serialu.md` (nowy). Pomocnicze skrypty (kontrola cytatów, kontrola tabel, listy hashy) leżą w scratchpadzie sesji, poza repozytorium.
- **Hashe wejść** (sekcja 0.4): policzone `sha256sum` przed pisaniem i po zakończeniu; **wszystkie zgodne** (wejścia: repozytorium, archiwum, pliki wgrane przez właściciela, zlecenia pokrewne) **z dwoma wyjątkami z działań orkiestratora (poza tym tematem)**: `autobot/DECYZJE.md` (dopisane ECHO-043, -044, -045; L1–L48 bez zmian) i `autobot/SCENARIUSZE.md` (dopisana sekcja ZERO-UJECIA, L1–L171 bez zmian); aktualne hashe w 0.4. **Runda 2:** hashe wszystkich pozostałych wejść z 0.4 przeliczono ponownie 2026-11-28 (zgodne), dodano wiersz ARS (E-1-2); kontrola cytatów po poprawkach — patrz raport terminalny rundy 2.
- **Sieć, konta, klucze, API, MCP, generowanie obrazów, głosów i wideo:** brak.
- **Skrypty z archiwum:** żaden nie był uruchamiany.
- **Git:** brak poleceń zmieniających stan (commit, push, add, checkout).
- **Ranking i wybór narzędzia (ECHO-027):** brak; Q10 zawiera zestawienie parametrów, nie rekomendację.
- **Kanon:** żadne imię, data, zdarzenie ani kwestia nie zostały dopisane; elementy „od reżysera” mają etykietę PROPOZYCJA REZYSERSKA (opisy EN w 7.3 i 7.4, rytm w 7.1, typy przejść oznaczone w 7.5, logline w 1.1, funkcje w 7.1).
- **E03:** poza zakresem (3.5).

**Hash tego pliku:** podaje raport terminalny Operatora (plik nie może zawierać własnego SHA-256). Kontrole pomocnicze (poza repozytorium): każdy cytat w formie `SKRÓT Lnn` + fragment sprawdzony skryptem względem pliku źródłowego; wszystkie tabele mają równą liczbę kolumn i brak pustych komórek.

---

## 1. Logline, premisa, motywy, ton

### 1.1 Logline

| Poziom | Sformułowanie | Podstawa |
|---|---|---|
| E01 (**PROPOZYCJA REZYSERSKA** — sformułowanie; fakty z SC) | „Czternaście dni przed Zero Day zwykły świat — Warszawa, szpital, centrum sieci energetycznej — jeszcze nie wie, że wirus Y zabija mężczyzn. Jego twórczyni, norweska wirusolog Vera Strand (nota obsady: „Tylko ona wie.”), patrzy na to z Oslo; w czterech blokach przeszłości widzimy, jak do tej chwili doszła.” | `SC L12` `TOR A -- TERAŹNIEJSZOŚĆ: Warszawa i Oslo, T-14 do T=0.`; `SC L38` `Twórczyni wirusa Y. Tylko ona wie.`; `SC L21` `Cztery bloki przeszłości rozmieszczone przez cały odcinek,` |
| Serial (informacja; materiał rz.4) | „Polski mini-serial sci-fi / dramat społeczny, 3 odcinki: wirus Y zabija prawie wszystkich mężczyzn, świat staje się światem kobiet; wątek główny to odbudowa i wina Very Strand; drugi plan to misja Ares IV.” | `PLAN L12` `Premisa:`; `AHO L38` `**Premisa:** wirus zabija praktycznie wszystkich mężczyzn (śmiertelność u mężczyzn ~100%).` |

Logline celowo **nie rozstrzyga** wiedzy widza o relacji Vera–Aga (ROZBIEŻNOŚĆ RK-01 w sekcji 6).

### 1.2 Premisa odcinka E01 (kanon SC)

- Format i gatunek: `SC L3` `Format: ok. 60 minut`; `SC L4` `Gatunek: Sci-Fi / Dramat społeczny`.
- Dwa tory: `SC L10` `Odcinek działa na dwóch torach narracyjnych.` — **Tor A (teraźniejszość)**: Warszawa i Oslo, T-14 do T=0 (`SC L12`), trzy wątki równoległe: `SC L14` `Trzy wątki równoległe: Marta i Karolina (PSE, dom),` / `SC L15` `Aga Bryk (szpital, pierwsze przypadki), media (eskalacja).`; **Tor B (przeszłość)**: `SC L19` `Pełne sceny z historii Very i Dąbrowskiego -- nie przebitki,` — cztery bloki.
- Odcinek kończy się Zero Day (nota), a w pliku scenariusza po montażu Zero Day następuje jeszcze Scena 15 (T+8): `SC L26` `Odcinek kończy się Zero Day. Cliffhanger: Marta z żółtą` oraz `SC L1226` `SCENA 15 -- STATEK WIDMO  [CZAS: ok. 1,5 min]`. To jest **ROZBIEŻNOŚĆ wewnątrz rzędu 1** (RK-03, RK-04).
- Mechanizm wirusa, jak go podaje scenariusz (naukowo NIEPOTWIERDZONE, AN1 konwencja): `SC L779` `Chromosom Y. Wirus rozpoznaje specyficzną sekwencję` / `SC L782` `Nikt nie ewoluuje z taką precyzją.` / `SC L787` `Ktoś to zaprojektował.`

### 1.3 Motywy (tabela)

| ID | Motyw | Gdzie w E01 (kanon SC) | Podstawa motywu | Status |
|---|---|---|---|---|
| MO-01 | Normalność tuż przed końcem („Normalna środa”) | `SC L150` `Nic pilnego. Normalna środa.`; `SC L152` `Marta kiwa głową. Normalna środa.`; `SC L173` `Normalna środa. Marta wraca do swoich monitorów.` | tekst SC | kanon SC |
| MO-02 | Cisza zamiast muzyki; im gorzej, tym mniej muzyki | `SC L979` `Cisza. Bez muzyki.`; `SC L1258` `Cisza trzyma się dłużej, niż jest wygodnie.` | `U04 L8` `Muzyka w E01 jest obecna tylko wtedy, gdy życie jest normalne. Gdy życie się kończy — cisza.` | kanon SC + materiał rz.4 |
| MO-03 | Żółty jako kotwica (sweter, teczka, karteczka) | `SC L73` `On ma sweter -- jasnożółty, z nadrukiem dinozaura w okularach.`; `SC L154` `Na biurku Marty, między raportami i kubkiem: żółta teczka`; `SC L276` `z kieszeni żółtą karteczkę samoprzylepną. Zasłania obiektyw.` | `U05 L16` `Żółty kolor łączy Karolinę (żółta teczka), Michała (żółty sweter) i Martę (teczka Piotra).` | kanon SC (kolor w trzech miejscach) + materiał rz.4 (interpretacja „łączy”) |
| MO-04 | Nieobecność zamiast pokazanej śmierci (pusty murek, pusty boks, sweter, puste miejsca) | `SC L122` `Kamera zostaje na pustym murku przez chwilę.`; `SC L286` `Wychodzi. Kamera zostaje przy pustym boksie.`; `SC L1009` `Sala normalnie wyglądająca -- ale dwa miejsca są puste.`; `SC L1180` `Sweter Michała leży na fotelu.` | `U05 L28` `Sweter to Michał. Kiedy widzimy sweter zamiast Michała — wiemy.`; `ARCH-08 L75` `**Śmierć Pawła:** NIE pokazujemy śmierci on-screen.` | kanon SC + materiał rz.4 |
| MO-05 | Praca, wina i „Adam” (krzywa wzrostu, tablica, kradzież badań) | `SC L273` `naukowych -- krzywa wzrostu. Napis pod nią: "Adam".`; `SC L901` `Moje.`; `SC L919` `Jedno słowo: "Adam."` | `ADR L16` `(a) tajny kryptonim projektu Very (tablica, notatki),` | kanon SC + materiał rz.4 |
| MO-06 | Ludzie, którzy jeszcze nie wiedzą (ironia dramatyczna) | `SC L13` `Ciepłe barwy. Żyjące miasto. Ludzie, którzy jeszcze nie wiedzą.` | `U07` (Tomek „nie wie”, grać bez wiedzy) — tu tylko wskazanie | kanon SC |
| MO-07 | Komunikaty bez odpowiedzi (telefon, poczta głosowa, „numer niedostępny”) | `SC L856` `Sygnał. Sygnał. Poczta głosowa.`; `SC L989` `Automat: "Numer jest chwilowo niedostępny."` | rym z serialem: `SC2 L20` `Skończył się powoli, w kolejkach i w ciszy, w telefonach` | kanon SC (E01, E02) |
| MO-08 | Kobiety przejmują stanowiska (zapowiedź świata kobiet) | `SC L1023` `Dobrze. Przejmujemy ich stanowiska.`; `SC L1037` `Agnieszka -- bierz R-dziewiętnaście. Ela -- R-dwadzieścia dwa.` | `PLAN L12` `świat staje się światem kobiet` | kanon SC + materiał rz.4 |
| MO-09 | Kliniczne skupienie zamiast paniki (Aga) | `SC L338` `Nie strach. Rozpoznawanie anomalii.` | — | kanon SC |
| MO-10 | Rodzice i dzieci / kolejne pokolenia (Marta–Karolina–„tata”, Vera–Aga) | `SC L396` `i Michał powiedział, że mu przypomina tatę.`; `SC L514` `Mamma! Pappa powiedział, że możemy jutro do parku!`; `SC L754` `Zadzwonię, kiedy dojadę.` (odpowiedź na „Wrócisz?”) | tekst SC | kanon SC |

*Uwaga:* MO-10, jako motyw „pokoleń”, jest **PROPOZYCJĄ REZYSERSKĄ** w warstwie interpretacji (zestawienie scen); same cytaty są kanonem SC.

### 1.4 Ton

| ID | Ton / zasada tonu | Źródło | Status |
|---|---|---|---|
| TN-01 | powściągliwy; „świat nie kończy się w ogniu, tylko powoli — w kolejkach i ciszy” | `PLAN L13` `**Ton:** powściągliwy`; `SC2 L20` `Skończył się powoli, w kolejkach i w ciszy, w telefonach` | materiał rz.4 (serial) + kanon SC2 (E02) |
| TN-02 | Tor A: ciepło, żyjące miasto | `SC L13` `Ciepłe barwy. Żyjące miasto. Ludzie, którzy jeszcze nie wiedzą.` | kanon SC |
| TN-03 | Tor B: barwa pośrednia | `SC L23` `Barwa: pośrednia -- cieplejsza niż Oslo Very, chłodniejsza` | kanon SC |
| TN-04 | Oslo (BSL-4): zimno, cisza, wentylacja | `SC L261` `Pierwsze zimne ujęcie w całym odcinku.`; `SC L263` `Cisza zamiast miejskiego hałasu. Szum wentylacji.` | kanon SC |
| TN-05 | wstawki medialne: eskalacja od „zarządzanego niepokoju” do „już nie” | `SC L353` `Kadr telewizyjny. Ton: profesjonalny. Zarządzany niepokój.`; `SC L839` `To już nie jest zarządzany niepokój.` | kanon SC |
| TN-06 | Zero Day: muzyka narasta od zera, syreny przy punktach mapy | `SC L1160` `Muzyka: narasta od zera. Smyczki, cisza, smyczki.`; `SC L1163` `Pierwsze czerwone punkty. Przy każdym z nich -- sygnał syreny alarmowej.` | kanon SC |
| TN-07 | Scena 15: bez muzyki, pokazujemy mało i powoli | `SC L1230` `Reżysersko: bez muzyki. Tylko morze, wiatr i metal. Pokazujemy mało` | kanon SC |
| TN-08 | język wizualny zmienia się powoli w trakcie odcinka (bliskość → dystans → chłodna stabilność) | `ARCH-01 L8` `Dlatego język wizualny zmienia się w trakcie odcinka, bardzo powoli, prawie niezauważalnie.` | materiał rz.4 (szczegóły: `A02_przewodnik_wizualny.md`) |
| TN-09 | E02: „bez muzyki dramatycznej przez pierwsze dziesięć minut po prologu” | `SC2 L17` `Nie ma muzyki dramatycznej przez pierwsze dziesięć minut po prologu.` | kanon SC2 (informacja o serialu) |

---

## 2. Zasady stałe serialu

Zasady są trzech rodzajów: (a) wynikają z tekstu scenariusza (kanon SC), (b) są decyzją właściciela (ECHO) albo regułą produkcyjną z materiałów rzędu 4, (c) są granicami narzędzia (tylko z zatwierdzonych badań). Kolumna „Status” mówi, czym zasada jest **teraz**; kolumna „Rozbieżność / otwarte” wskazuje, co jest nierozstrzygnięte.

### 2.1 Zasady stałe (tabela)

| ID | Zasada | Zakres | Źródło (plik i linia, cytat) | Status | Rozbieżność / otwarte |
|---|---|---|---|---|---|
| ZS-01 | **Bez muzyki w klipach.** Klip niesie dialog, ambient i efekty; muzyka jest osobną warstwą w montażu | cały serial (reguła produkcyjna) | `UAF L50` `birds). NO music, NO score.`; `AHO L215` `auto-napisy (EN) podmienić na polskie → muzyka jako osobna warstwa (NIE w klipach Flow).`; `DECYZJE L14` `nie uchyla zasady` (ECHO-008: wymóg dźwięku z modelu nie uchyla zasady „bez muzyki w klipach”; ostateczna reguła audio zostaje do decyzji właściciela) | reguła z handoffu; **ostateczna reguła audio otwarta** (ECHO-008) | ROZBIEŻNOŚĆ RK-16, RK-17 (scenariusz opisuje muzykę: `SC L65` `Muzyka: ciepła, ambientowa, miejska. Żadnego niepokoju.`; `SC L1160` `Muzyka: narasta od zera. Smyczki, cisza, smyczki.`); pytanie Q2 |
| ZS-02 | **Cisza jako narzędzie.** Im gorzej, tym mniej muzyki; sound design zastępuje muzykę; ciszę po kluczowej kwestii zostawiamy | cały serial | `U04 L8` `Muzyka w E01 jest obecna tylko wtedy, gdy życie jest normalne. Gdy życie się kończy — cisza.`; `SC L979` `Cisza. Bez muzyki.`; `SC L1198` `Sala bez pytań. Cisza zamiast pytań.`; `U04 L62` `Po tej kwestii — cisza przez 3 sekundy zanim kamera przejdzie do szafy.` | kanon SC + materiał rz.4 (długości ciszy w ms: pliki sceny B, nie ta biblia) | czasy ciszy w ms **BRAK DANYCH** w SC (szukano: SC L1–1263); zapisane tylko „3 sekundy” w `U04` |
| ZS-03 | **Dwa tory E01.** Tor A (teraźniejszość, T-14..T=0) i tor B (cztery pełne sceny przeszłości, nie przebitki); każdy blok przeszłości wyzwolony przez coś w teraźniejszości | E01 | `SC L10` `Odcinek działa na dwóch torach narracyjnych.`; `SC L22` `każdy wyzwolony przez coś w teraźniejszości.`; `ARCH-01 L36` `**Tor B (przeszłość):** cztery bloki, każdy wywołany przez konkretny bodziec w teraźniejszości:` | kanon SC | wyzwalacze w SC spełnione częściowo (AN1 E01-18, N-05); kolejność P1 — RK-05; „T=0” w nocie vs sc. 15 w T+8 — RK-29 |
| ZS-04 | **Trzy palety barwne** (Warszawa dziś ciepła; przeszłość pośrednia; Oslo zimne) — szczegóły w `A02_przewodnik_wizualny.md` | cały serial | `SC L13` `Ciepłe barwy. Żyjące miasto. Ludzie, którzy jeszcze nie wiedzą.`; `SC L23` `Barwa: pośrednia -- cieplejsza niż Oslo Very, chłodniejsza`; `SC L262` `Barwa spada natychmiast: fluorescencja, czerń, biel.`; `ARCH-01 L26` `Zimna, fluorescencyjna, niemal beżowo-szara. Zero sentymentu w kadrze.` | kanon SC (trzy światy) + materiał rz.4 (nazwy kolorów) | wartości kolorów i obiektywów = PROPOZYCJA REZYSERSKA w `A02_przewodnik_wizualny.md` |
| ZS-05 | **Język Very i Agi.** Vera mówi po polsku z norweskim akcentem; w Oslo do siebie po norwesku (napisy polskie); Aga z Verą w przeszłości po norwesku (napisy polskie) | E01 | `SC L52` `Vera mówi po polsku przez cały E01 -- z wyraźnym norweskim akcentem.`; `SC L55` `(Oslo) mówi do siebie po norwesku -- napisy polskie.`; `SC L513` `AGA (po norwesku -- napisy polskie)` | kanon SC | ROZBIEŻNOŚĆ RK-19 (nota vs sceny), RK-18 (reguła językowa w beatach); [KANON] Q8 |
| ZS-06 | **Dialogi: kanon polski bez zmian.** Brzmienia EN do promptów to PROPOZYCJA (G2); polski głos i napisy w montażu | cały serial | `DECYZJE L9` `Analiza podaje propozycje nowego brzmienia kwestii`; `DECYZJE L42` `dialogi: kanon polski bez zmian`; `UAF L45` `- All dialogue in ENGLISH (Polish subtitles are added later in post — never burn` | decyzja właściciela (ECHO-003, ECHO-036 pkt 4) + reguła produkcyjna rz.4 | **strategia dialogów otwarta** (PLAN D3, AN3 Q5): EN + polski głos / polski wprost / bez ruchu ust |
| ZS-07 | **Teksty ekranowe (napisy T i P, paski TV, SMS-y, ekrany) w montażu, nie w klipie** | cały serial | `UAF L46` `any text into the video).`; `R002 L26` `subtitles` (model może dodać napisy i muzykę domyślnie; zakaz wpisuje się do promptu) | reguła produkcyjna rz.4 + granica narzędzia | **otwarte** — AN3 R-45, L-10, Q14; plik z listą tekstów: `A06_biblia_rekwizytow_i_ciaglosci.md` |
| ZS-08 | **Jedna osoba mówi naraz**; pozostałe z zamkniętymi ustami | cały serial | `UAF L47` `- Only ONE person speaks at a time; the other listens with mouth closed, lips not`; `R002 L25` `One speaker at a time` | reguła produkcyjna rz.4 + zgodna z przykładem producenta narzędzia | reguła „jedna osoba na klip” vs „kilku mówców kolejno w klipie”: AN3 R-35, Q7 |
| ZS-09 | **Strony kadru w Scenie 1:** Michał zawsze po lewej, Karolina zawsze po prawej; bez odbicia lustrzanego | tylko Scena 1 | `UAF L17` `- MICHAL (the man) is ALWAYS on the LEFT side of the frame.`; `UAF L18` `- KAROLINA (the woman) is ALWAYS on the RIGHT side of the frame.` | reguła produkcyjna rz.4 (dla jednej sceny) | szczegóły: `B05_arkusz_ciaglosci_s1.md`, `B01_karta_sceny1.md` |
| ZS-10 | **Śmierci Pawła nie pokazujemy** (przejście „do po”; monitor milknie jako most dźwiękowy) | E01, scena 12→13 | `ARCH-08 L75` `**Śmierć Pawła:** NIE pokazujemy śmierci on-screen. Ostatni kadr Pawła to splecione dłonie z Agą. Cięcie do korytarza po. Monitor milknie jako sound bridge między scenami.`; `SC L1119` `O czwartej czternaście.` | reguła produkcyjna rz.4; nie zmienia kanonu (SC nie pokazuje zgonu) | dotyczy wyłącznie śmierci Pawła; sc. 15 pokazuje martwych mężczyzn (`SC L1242` `Na pokładzie, pod nadbudówką, leżą postacie. Mężczyźni. Nieruchomi.`) |
| ZS-11 | **Ares IV w E01 tylko jako nieobecność** (teczka ze zdjęciem Piotra, rozmowa, informacja „milczy”, ekran ESA); statku i kosmosu nie pokazujemy | E01 | `ARCH-08 L125` `**Nie pokazujemy statku ani przestrzeni kosmicznej w E01.** To jest celowe — Ares IV istnieje tylko jako nieobecność, jako coś czego nie ma. Widzimy Piotra po raz pierwszy dopiero w E03.`; `SC L569` `Ares IV milczy od czterdziestu ośmiu godzin.` | reguła produkcyjna rz.4; zgodna z SC | obecność Piotra w E01 (imię, zdjęcie) — AN1 D-07, E01-11; oś milczenia — RK-02 |
| ZS-12 | **Ciągłość teczki:** żółta teczka Marty chowana do tej samej szafy w każdej scenie; szafa widoczna w tle | E01 (sc. 2, 6, 14) | `ARCH-08 L39` `**Uwaga ciągłości:** Żółta teczka Marty musi być schowana do tej samej szafy w każdej scenie. Szafa powinna być widoczna w tle.`; `SC L158` `Marta odkłada teczkę do szafy. Zamyka. Bierze raport od Tomka.` | kanon SC + reguła produkcyjna rz.4 | czy teczka/zdjęcie Piotra wraca w sc. 14 — RK-03; szczegóły `A06_biblia_rekwizytow_i_ciaglosci.md` |
| ZS-13 | **Zasada E02 „bez mężczyzn w kadrze”** — tylko informacja o serialu (nie dotyczy E01) | E02 | `KS L247` `- [ ] E02 — prompty (bez mężczyzn w tle)`; `AN2 L173` `- **Na czym polega sprzeczność:** zasada E02 (handoff §7, rząd 2) zakłada brak mężczyzn w kadrze; prolog świadomie pokazuje ciała z E01.` | zasada produkcyjna rz.4; **zakres i wyjątki nierozstrzygnięte** (AN2 D-06) | `AN2 L879` `A: żaden żywy mężczyzna w kadrze i dźwięku; wyjątki: zmarli z E01, zdjęcia Pawła i Piotra` to wariant z analizy, nie decyzja; pytanie Q3 |
| ZS-14 | **E01 pokazuje świat mieszany** (kobiety i mężczyźni razem) — w E02 mężczyzn już nie ma w kadrze | E01 sc. 1 i dalej | `SC L69` `na wynos, rowery, psy na smyczach, mężczyźni i kobiety razem,`; `ARCH-08 L111` `**Kluczowa uwaga:** W scenie 1 widać mężczyzn i kobiety razem w naturalnym środowisku miejskim.` | kanon SC (sc. 1) + materiał rz.4 | zdanie „jedyne miejsce w serialu” w `ARCH-08 L111` pomija sc. 2–13 (mężczyźni: Tomek, Paweł, pacjenci) — claim rz.4, **nie przenosimy** |
| ZS-15 | **Precyzja do milisekundy to plan i kryterium kontroli, nie gwarancja generatora** | pliki sceny B, tracker, kontrola jakości | `DECYZJE L42` `zadne dzis dostepne narzedzie wideo nie gwarantuje trafienia w milisekunde`; `R003 L56` `seed` (brak parametru czasu zdarzenia i seed w dokumentacji API); `R008 L100` `more opportunities for missed actions` (relacja rz.4, NIEPOTWIERDZONE) | decyzja właściciela (ECHO-036 pkt 3) + granica narzędzia | tolerancja i tempo mowy — [PRODUKT] AN3 Q18, `P002` pytanie P-10 |
| ZS-16 | **Narzędzie: Kling 4.0; bez rankingu i bez wyboru za właściciela** | pakiet | `DECYZJE L43` `Nie dla Seedance, tylko dla Kling mowilem.`; `DECYZJE L33` `Porownania dostawcow wideo: zbieramy charakterystyke, wybor nalezy do wlasciciela.` | decyzje właściciela (ECHO-027, ECHO-037) | wariant 4.0 / 4.0 Flash, rozdzielczość, droga MCP/API — [PRODUKT] Q10 |
| ZS-17 | **Kanon rozstrzyga wyłącznie właściciel.** Elementy „od reżysera” (kadry spoza SC, przejścia, rytm, nowe brzmienia EN) = PROPOZYCJA REZYSERSKA | cały pakiet | `WYBORY L25` `**G3** Kanon (postacie, fakty, os czasu) rozstrzyga wylacznie wlasciciel`; `WYBORY L24` `**G2** Tresci dialogow nie zmieniamy samowolnie` | granice G2, G3 (potwierdzone ECHO-022) | — |
| ZS-18 | **Realne marki i instytucje w fikcyjnych rolach** (TVN, TVN24, CNN, WHO, ESA, PSE, Szpital Bielański, UW, gazoport) — dopuszczalne „fikcyjne odpowiedniki jeśli wymaga clearance” | cały serial | `ARCH-08 L49` `- Logo stacji: TVN, TVN24, CNN — lub fikcyjne odpowiedniki jeśli wymaga clearance`; `PLAN L131` `**Realne marki → fikcyjne**` | otwarte (PLAN D15; temat praw `C04_prawa_i_licencje.md`) | Q9 |

### 2.2 Granice narzędzia (Kling 4.0) istotne dla zasad stałych — tylko z zatwierdzonych badań

Każde twierdzenie ma odnośnik (plik i linia tabeli badania) albo jest oznaczone BRAK DANYCH. Nic nie jest z pamięci. Granice dotyczą wyłącznie najnowszej generacji Klinga (4.0 i jej wariantu 4.0 Flash; ECHO-030, ECHO-031) — starsze generacje nie są używane. Ten blok **nie jest rankingiem ani rekomendacją** (ECHO-027); opisuje, czego biblia nie może obiecywać modelowi.

| ID | Granica | Odnośnik | Skutek dla zasad stałych |
|---|---|---|---|
| GM-01 | `duration` 3–30 s, liczby całkowite, domyślnie 10 s (4.0); 3–20 s (4.0 Flash) | `R003 L54` `3-30 s (liczby calkowite; bez parametru i bez dlugosci w prompcie domyslnie 10 s)` | ujęcie krótsze niż 3 s nie istnieje jako osobny klip; plan klipów w `A08_przewodnik_promptow_kling.md` i plikach B |
| GM-02 | rozdzielczość: 720p / 1080p (domyślnie) / 4k (4.0); 4.0 Flash tylko 720p | `R003 L53` `4.0 Flash: tylko` (wartości: 720p, 1080p domyślnie, 4k — w tej samej linii tabeli) | rozdzielczość docelowa = [PRODUKT] (Q10); nie rozstrzygamy |
| GM-03 | proporcje: 16:9 domyślne w T2V | `R003 L55` `16:9` (domyślnie) | ZS-04, wstawki TV jako pełny kadr 16:9 — decyzja AN3 R-67 |
| GM-04 | klatki: `first_frame`, `middle_frame`, `last_frame` w I2V 4.0; Flash tylko pierwsza klatka | `R003 L49` `contents[].type` = `prompt`, `first_frame`, `middle_frame`, `last_frame`; `R003 L49` `Only first-frame-to-video generation is supported` | ciągłość klatek między ujęciami i kadry bez postaci z klatki startowej (sekcja 7) |
| GM-05 | Elements (referencje postaci i obiektów): do 7 elementów, do 15 zasobów na zadanie | `R003 L50` `do 7 elementow` | spójność postaci przez Elements — `A03_biblia_postaci.md`; kadry bez postaci nie potrzebują Elements postaci |
| GM-06 | głosy: do 3 profili głosu na zadanie (próbka 5–30 s); 4.0 Flash: brak klonowania głosu | `R002 L27` `maks. 3 glosy`; `R008 L153` `"Voice Cloning — Not supported"` | `A04_arkusze_glosow.md`, `D02_plan_polskiego_glosu.md` |
| GM-07 | języki mowy: 9 (zh, en, ja, ko, es, pt, de, fr, hi); **polski: BRAK DANYCH oficjalnie**; norweskiego na liście nie ma | `R002 L21` `chinski, angielski, japonski, koreanski, hiszpanski`; `R002 L22` `polski nie wymieniony`; `R008 L139` `BRAK DANYCH: polski nie jest wymieniony` | ZS-05, ZS-06; jedyna relacja o polskiej mowie w 4.0 to test autorski rz.4 (`R008 L142`, NIEPOTWIERDZONE) |
| GM-08 | dialog pisze się w cudzysłowie w języku, w którym ma paść | `R008 L140` `write the dialogue in that language directly inside quotation marks` | prompty EN w plikach B; kanon PL pozostaje w arkuszu dialogów |
| GM-09 | wielu mówców w klipie: dopuszczalne, „One speaker at a time”; limit liczbowy BRAK DANYCH | `R002 L25` `limit liczbowy BRAK DANYCH` | ZS-08, test zerowy |
| GM-10 | muzykę i napisy model może dodać domyślnie; zakaz wpisuje się do promptu; całego audio nie da się wyłączyć | `R002 L26` `the model may add subtitles and background music by default`; `R008 L97` `Niechciana muzyka i efekty` (relacje rz.4, NIEPOTWIERDZONE) | ZS-01, ZS-07: zakaz w każdym prompcie + kontrola pliku |
| GM-11 | przedłużanie klipu w 4.0: brak („Coming Soon”); brak narzędzia extend w oficjalnym MCP | `R003 L51` `Video Extension (Coming Soon)` | dłuższe ujęcie = jeden klip do 30 s albo cięcia z `first_frame`; metoda Extend z Flow się nie przenosi (AN3 R-30) |
| GM-12 | `seed`: brak w tabelach parametrów | `R003 L56` `seed` | brak powtarzalności prób; dziennik prób w `C01_tracker_produkcji.md` |
| GM-13 | liczba klatek na sekundę: **BRAK DANYCH** (szukano: R001–R008) | `AN3 L650` `Liczby klatek na sekundę w zatwierdzonych badaniach brak`; `P002 L81` `BRAK DANYCH. ZALOZENIE: 24 fps` | ms jest wartością nadrzędną, klatki dopiero po pomiarze (zał. 24 fps w `P002`) |
| GM-14 | limit długości pola promptu: **BRAK DANYCH** | `DECYZJE L44` `limit dlugosci pola promptu Klinga nie jest znany z zatwierdzonych badan (BRAK DANYCH)` | sprawdzić w aplikacji przy pierwszym teście |
| GM-15 | czytelność tekstu wygenerowanego w obrazie (np. „Adam”): **BRAK DANYCH** | `AN3 L694` `czytelność tekstu w obrazie Kling 4.0 — BRAK DANYCH w badaniach` | teksty ekranowe w montażu (ZS-07) |
| GM-16 | filtry treści (wysypka, ciała w sc. 15, laboratorium BSL-4, realne marki): **BRAK DANYCH**; temat ECHO-023 niewykonany | `AN3 L724` `Badania RESEARCH-001..008 tego nie opisują`; `DECYZJE L29` `Temat warunkow komercyjnych i filtrow tresci = A.` | test przed pełnym wsadem (AN3 Q20) |
| GM-17 | MCP oficjalny korzysta z konta aplikacji (kredyty aplikacji), nie z pakietów Units API; droga uruchomienia = wybór właściciela | `R003 L58` `oficjalny MCP/CLI **nie jest** opakowaniem API Open Platform`; `DECYZJE L43` `droga uruchomienia Klinga (MCP z konta aplikacji albo API z kluczem) pozostaje wyborem wlasciciela` | `A08_przewodnik_promptow_kling.md` opisuje obie drogi |

---

## 3. Struktura odcinków E01–E02

### 3.1 E01 — 23 segmenty w kolejności scenariusza

Lista obejmuje **wszystkie 23 segmenty z etykietą CZAS** w `SC`: sceny 1–15 (15), bloki przeszłości P1–P4 (4) i wstawki medialne (4). Kolejność = kolejność w pliku (nie chronologia T — por. 4.1). Kolumna „Tor”: A / B / M wg legendy 0.1 (M = wstawka medialna, klasyfikacja redakcyjna — **PROPOZYCJA REZYSERSKA**; SC wymienia media jako wątek toru A, patrz 3.2). Raport AN3 podaje 23 segmenty (sekcja 1.6); rozpiska sekundowa ma 22 sekwencje, bo nie zawiera sc. 15 (`AN3 R-01`).

| Nr | Segment | Nagłówek SC (linia) | CZAS wg SC (min) | T / epoka (SC) | Lokalizacja (nagłówek SC) | Tor | Postacie z obsady w segmencie (z SC) |
|---|---|---|---|---|---|---|---|
| 1 | Sc. 1 | L62 | 3,5 | brak T; „RANEK, ZWYKŁY DZIEŃ” | EXT./INT. WARSZAWA | A | Karolina, Michał; głos Marty (telefon) |
| 2 | Sc. 2 | L126 | 1,5 | brak T; „TO SAMO RANO” | INT. CENTRUM DYSPOZYTORSKIE PSE, WARSZAWA | A | Marta, Tomek |
| 3 | Blok P1 / sc. P1 | L177 / L181 | 4 | przeszłość; Vera 24 lata | INT. KORYTARZ WYDZIAŁU BIOLOGII UW / GABINET DĄBROWSKIEGO | B | Vera, Dąbrowski (30 lat), studentka |
| 4 | Sc. 3 | L257 | 2,5 | T MINUS 14 DNI | INT. LABORATORIUM BIOSAFETY LEVEL 4, OSLO | A | Vera |
| 5 | Sc. 4 | L292 | 3 | T MINUS 9 DNI, rano | INT. SZPITAL BIELAŃSKI, ODDZIAŁ CHORÓB ZAKAŹNYCH | A | Aga, Paweł, Joanna, pacjent |
| 6 | Wstawka T-10 | L351 | 0,75 | T MINUS 10 DNI | studio informacyjne (SC nie podaje nagłówka lokacji) | M | prezenterka |
| 7 | Sc. 5 | L369 | 2 | T MINUS 9 DNI, popołudnie | INT. CENTRUM PSE | A | Marta, Marcin (radio), Karolina (telefon) |
| 8 | Blok P2 / sc. P2 | L423 / L427 | 4 | przeszłość; Vera ok. 35 lat | INT. LABORATORIUM UW / MIESZKANIE | B | Vera, Dąbrowski, Aga (4–5 lat) |
| 9 | Sc. 6 | L531 | 2 | T MINUS 9 DNI, popołudnie | INT. CENTRUM PSE | A | Marta, Tomek, dyżurna |
| 10 | Wstawka T-7 | L588 | 1 | T MINUS 7 DNI | ekrany TV, kolejki, telefon Karoliny (SC nie podaje nagłówka lokacji) | M | brak postaci z obsady poza telefonem Karoliny |
| 11 | Blok P3 / sc. P3 | L607 / L611 | 5 | przeszłość; Vera ok. 49 lat | INT. KORYTARZ WYDZIAŁU / GABINET / MIESZKANIE | B | Vera, Dąbrowski, doktorantka, Aga (19 lat) |
| 12 | Sc. 7 | L765 | 3 | T MINUS 7 DNI, wieczór | INT. SZPITAL BIELAŃSKI, ODDZIAŁ CHORÓB ZAKAŹNYCH | A | Aga, lekarz z Berlina (ekran), Paweł |
| 13 | Sc. 8 | L806 | 1,5 | T MINUS 8 DNI, wieczór | INT. MIESZKANIE VERY, OSLO | A | Vera |
| 14 | Wstawka T-5 | L837 | 1 | T MINUS 5 DNI | studio, telefon Karoliny (SC nie podaje nagłówka lokacji) | M | epidemiolog, Karolina |
| 15 | Blok P4 / sc. P4 | L861 / L865 | 3,5 | przeszłość; Vera ok. 52 lata | INT. GABINET W OSLO / MIESZKANIE W OSLO | B | Vera |
| 16 | Sc. 9 | L926 | 3 | T MINUS 6 DNI, wieczór | INT. SALON MARTY | A | Marta, Karolina |
| 17 | Sc. 10 | L975 | 2,5 | T MINUS 5 DNI, popołudnie | INT. POKÓJ KAROLINY | A | Karolina |
| 18 | Sc. 11 | L1005 | 3,5 | T MINUS 4 DNI, ranek | INT. CENTRUM PSE | A | Marta, Beata, Agnieszka, Ela |
| 19 | Sc. 12 | L1048 | 5 | T MINUS 2 DNI, noc | INT. SZPITAL BIELAŃSKI, OIT | A | Aga, Paweł |
| 20 | Sc. 13 | L1106 | 2 | T MINUS 1 DZIEŃ, świt | INT. SZPITAL BIELAŃSKI, KORYTARZ | A | Aga, Joanna |
| 21 | Wstawka T-1 | L1140 | 0,75 | T MINUS 1 DZIEŃ | studio (SC nie podaje nagłówka lokacji) | M | prezenterka, premier, Wolska |
| 22 | Sc. 14 Zero Day | L1157 | 4 | MONTAŻ — T ZERO | montaż wielu miejsc (sekcja 5.4) | A (montaż) | Marta, Karolina, Aga, Vera, rzecznik WHO, kobieta w centrum ESA |
| 23 | Sc. 15 Statek widmo | L1226 | 1,5 | T PLUS 8, świt | EXT. BAŁTYK / POKŁAD GAZOWCA LNG | A | brak postaci z obsady (martwa załoga) |
| — | **Suma** | — | **60,5** | — | — | — | — |

Kontrola sumy (liczona od zera): 3,5 + 1,5 + 4 + 2,5 + 3 + 0,75 + 2 + 4 + 2 + 1 + 5 + 3 + 1,5 + 1 + 3,5 + 3 + 2,5 + 3,5 + 5 + 2 + 0,75 + 4 + 1,5 = **60,5 min** (zgodnie z `AN1T`: 60,5). Nagłówek mówi `SC L3` `Format: ok. 60 minut` — RK-15 (metraż).

Nagłówki lokacji i etykiety CZAS: `SC L62` `SCENA 1  [CZAS: ok. 3,5 min]`; `SC L126` `SCENA 2  [CZAS: ok. 1,5 min]`; `SC L181` `SCENA P1  [CZAS: ok. 4 min]`; `SC L257` `SCENA 3  [CZAS: ok. 2,5 min]`; `SC L351` `WSTAWKA MEDIALNA -- T MINUS 10 DNI  [CZAS: ok. 0,75 min]`; `SC L1157` `SCENA 14 -- ZERO DAY  [CZAS: ok. 4 min]`; `SC L1226` `SCENA 15 -- STATEK WIDMO  [CZAS: ok. 1,5 min]`.

### 3.2 Podział na tory i wstawki (z sumami)

**Status podziału: PROPOZYCJA REZYSERSKA (klasyfikacja redakcyjna) + ROZBIEŻNOŚĆ z SC.** Czasy segmentów i ich sumy są kanonem SC (etykiety CZAS); sam **podział na trzy kategorie** (tor A bez mediów / tor B / wstawki M) i udziały procentowe to klasyfikacja tego pliku, nie fakt scenariusza. Dwa teksty SC:
- `SC L14` `Trzy wątki równoległe: Marta i Karolina (PSE, dom),` / `SC L15` `Aga Bryk (szpital, pierwsze przypadki), media (eskalacja).` — wg SC media (wstawki) są **jednym z trzech wątków toru A**, a nie osobną kategorią;
- tabela poniżej wydziela wstawki jako osobny wiersz (kategoria M), więc „tor A” w tabeli (40,5 min) jest węższy niż tor A wg SC. **Wariant zgodny z SC** (tor A razem z wstawkami M): 40,5 + 3,5 = **44,0 min = 72,7%** (przeszłość bez zmian: 16,5 min = 27,3%). Plik **nie rozstrzyga**, który podział jest właściwy dla montażu (nie jest to decyzja kanoniczna; wpływa tylko na raportowanie proporcji).
- Sc. 15 (T+8) jest w tabeli zaliczona do toru A, mimo że nota SC L12 ogranicza tor A do `T-14 do T=0`; **ROZBIEŻNOŚĆ wewnątrz rzędu 1** zapisana w RK-29 (`SC L12` `TOR A -- TERAŹNIEJSZOŚĆ: Warszawa i Oslo, T-14 do T=0.` wobec `SC L1228` `T PLUS 8`); bez sc. 15 tor A (sc. 1–14) = 39,0 min.

| Kategoria | Segmenty (numery z 3.1) | Liczba | Czas (min) | Udział |
|---|---|---|---|---|
| Teraźniejszość (tor A w ujęciu tabeli: sc. 1–15, bez wstawek M) | 1, 2, 4, 5, 7, 9, 12, 13, 16, 17, 18, 19, 20, 22, 23 | 15 | 40,5 | 66,9% |
| Przeszłość (tor B: P1–P4) | 3, 8, 11, 15 | 4 | 16,5 | 27,3% |
| Wstawki medialne (M: W T-10, T-7, T-5, T-1; wg SC L15 część toru A) | 6, 10, 14, 21 | 4 | 3,5 | 5,8% |
| **Razem** | — | **23** | **60,5** | 100% |

Rachunek: teraźniejszość 3,5 + 1,5 + 2,5 + 3 + 2 + 2 + 3 + 1,5 + 3 + 2,5 + 3,5 + 5 + 2 + 4 + 1,5 = 40,5; przeszłość 4 + 4 + 5 + 3,5 = 16,5; wstawki 0,75 + 1 + 1 + 0,75 = 3,5 (zgodne z `AN1T` i `AN1`). Udziały: 40,5 / 60,5 = 66,9%; 16,5 / 60,5 = 27,3%; 3,5 / 60,5 = 5,8%.

*Uwaga o P4.* `SC L865`–`L866` umieszcza P4 w Oslo (`INT. GABINET W OSLO / MIESZKANIE W OSLO -- PRZESZŁOŚĆ`), a nota mówi `SC L18` `TOR B -- PRZESZŁOŚĆ: Warszawa, lata wcześniej.` — **ROZBIEŻNOŚĆ wewnątrz rzędu 1** (AN1 E01-17); tu P4 jest zaliczony do toru B (blok przeszłości), a nie do „Warszawy”.

### 3.3 Cztery bloki przeszłości (skrót; szczegóły osi — sekcja 4.2)

| Blok | Tytuł bloku (SC) | Napis ekranowy (SC) | Wiek Very (SC) | Czas (min) |
|---|---|---|---|---|
| P1 | `SC L177` `BLOK PRZESZŁOŚCI (1) -- WARSZAWA, LATA WCZEŚNIEJ` | `SC L186` `Napis dyskretny w rogu: "WARSZAWA. 40 LAT WCZEŚNIEJ."` | `SC L183` `(VERA MA 24 LATA)` | 4 |
| P2 | `SC L423` `BLOK PRZESZŁOŚCI (2) -- WARSZAWA, KILKA LAT PO PRZYJEŹDZIE` | `SC L431` `Napis: "WARSZAWA. OK. 11 LAT PO PRZYJEŹDZIE."` | `SC L429` `(VERA MA OKOŁO 35 LAT)` | 4 |
| P3 | `SC L607` `BLOK PRZESZŁOŚCI (3) -- WARSZAWA, ZDRADA` | `SC L615` `Napis: "WARSZAWA. OK. 25 LAT PO PRZYJEŹDZIE."` | `SC L613` `(VERA MA OKOŁO 49 LAT)` | 5 |
| P4 | `SC L861` `BLOK PRZESZŁOŚCI (4) -- KRADZIEŻ BADAŃ` | `SC L869` `Napis: "OSLO. DWA LATA PO WYJEŹDZIE Z WARSZAWY."` | `SC L867` `(VERA MA OKOŁO 52 LATA)` | 3,5 |

### 3.4 E02 „EWA” — informacja o serialu (bez rozpisywania scen)

| Cecha | Wartość | Źródło | Uwaga |
|---|---|---|---|
| Tytuł i format | „ODCINEK 2: EWA”; `Format: ok. 65 minut` | `SC2 L2` `ODCINEK 2: EWA`; `SC2 L3` `Format: ok. 65 minut` | suma 29 etykiet CZAS = 73,5 min wg `AN2` (metraż E02 — decyzja AN2 D-07; nie dotyczy tego pliku) |
| Struktura (nagłówki scen w pliku) | PROLOG + 28 oznaczeń scen (1, 1A, 2, 3, 3B, 4, 4A, 5A, 5, 5B, 6, 6A, 7, 7A, 6B, 6C, 8, 9, 10, 12A, 12, 13, 14, 16, 15, 17, 18, 19 — brak numeru 11) | `SC2 L52` `PROLOG -- UDERZENIE  [CZAS: ok. 2 min]`; `SC2 L98` `SCENA 1  [CZAS: ok. 3 min]` | numeracja nie jest chronologią (AN2, E02A) — nie rozpisujemy |
| Zakres czasu | od `T PLUS 1` do `T PLUS 13` | `SC2 L100` `T PLUS 1 DO T PLUS 8`; `SC2 L54` `T PLUS 9` | prolog T+9; montaż aftermath T+1..T+8 |
| Prolog | gazowiec-widmo z końca E01 uderza w gazoport; „ostatni wielki huk tego świata”; chłodno, z dystansu | `SC2 L10` `Wyjątkiem jest prolog. Jedno jedyne uderzenie -- ostatni wielki huk`; `SC2 L12` `brzegu i uderza w gazoport. Pokazujemy to chłodno, z dystansu, bez` | most do E01 sc. 15 — RK-35 |
| Muzyka | brak muzyki dramatycznej przez pierwsze dziesięć minut po prologu; montaż aftermath bez muzyki | `SC2 L17` `Nie ma muzyki dramatycznej przez pierwsze dziesięć minut po prologu.`; `SC2 L102` `Bez muzyki. Odgłosy rzeczywistości: kroki, wiatr, odległe syreny.` | zasada tonu TN-09 |
| Barwa | temperatura barwna spada o pół stopnia względem E01 | `SC2 L103` `Temperatura barwna spada o pół stopnia względem E01. Świat jest` | rym z tą bibliią: E01 = pełne ciepło → E02 = chłodniej |
| Obsada E02 (skrót) | Marta (38), Karolina (19), Aga (34; córki Hania 4 l. i Zosia 2 l.), wicepremier Katarzyna Wolska (~58), Vera (64), Zofia (~55), Helena (~50), Basia (~45), kobieta z elektrowni | `SC2 L35`–`L49` (lista OBSADA — ODCINEK 2) | `SC2 L39` `Matka dwóch córek: Hania (4 l.) i Zosia (2 l.).`; E01 podaje tylko „dwóch córek” (`SC L40`) |
| Wiedza widza | `SC2 L45` `Widz jeszcze tego nie wie.` (o tym, że Vera jest matką Agi) | `SC2 L43`–`L45` | ROZBIEŻNOŚĆ z ECHO-020 — RK-01 |
| Zasada „bez mężczyzn w kadrze” | informacja o serialu: patrz ZS-13 | `KS L247`, `AN2 L173`, `AN2 L879` | zakres otwarty (AN2 D-06); wyjątki nierozstrzygnięte |

### 3.5 E03 „ARES”

E03 jest poza zakresem tego pliku i tego etapu (ECHO-005, do odwołania): `DECYZJE L11` `E03 wymaga przebudowy przez wlasciciela i jest poza zakresem do odwolania.` Żaden fakt z E03 nie jest tu użyty.

---

## 4. Oś świata i czasu

**Skróty segmentów** (numeracja 3.1): sceny **S1–S15**, bloki przeszłości **P1–P4**, wstawki medialne **W-10, W-7, W-5, W-1** (od ich napisów T MINUS).

### 4.1 Tor A — oś T (chronologicznie) z odnośnikami

W kolumnie „Kolejność w pliku” podano numer segmentu z 3.1; różnica względem chronologii jest widoczna wprost. Sceny 1 i 2 nie mają znacznika T (SC nie podaje dnia), poza `środą`.

| T (SC) | Segment (nr w pliku) | Pora dnia (SC) | Nagłówek / znacznik (SC, dosłownie) | Zdarzenie osi (kanon SC) |
|---|---|---|---|---|
| brak T („środa”) | S1 (1), S2 (2) | ranek | `SC L63` `EXT./INT. WARSZAWA -- RANEK, ZWYKŁY DZIEŃ`; `SC L127` `INT. CENTRUM DYSPOZYTORSKIE PSE, WARSZAWA -- TO SAMO RANO`; `SC L152` `Marta kiwa głową. Normalna środa.` | zwykły ranek, nic się nie zapowiada; materiały rz.4 dopisują T-14 pośrednio — `AN3 R-62` (dzień sc. 1–2 do potwierdzenia, [KANON, lekki]) |
| T-14 | S3 (4) | brak (laboratorium) | `SC L259` `T MINUS 14 DNI`; `SC L289` `Napis: T MINUS 14 DNI` | Vera zasłania kamerę, otwiera fiolkę: `SC L282` `Już po wszystkim.` |
| T-10 | W-10 (6) | brak | `SC L351` `WSTAWKA MEDIALNA -- T MINUS 10 DNI  [CZAS: ok. 0,75 min]` | posiedzenie WHO w Genewie: `SC L358` `Światowa Organizacja Zdrowia zwołała dziś nadzwyczajne` |
| T-9 | S4 (5) | rano | `SC L293` `INT. SZPITAL BIELAŃSKI, ODDZIAŁ CHORÓB ZAKAŹNYCH -- RANEK`; `SC L294` `T MINUS 9 DNI` | pierwsze przypadki w Warszawie: `SC L319` `Gorączka. Dziwna symetryczna wysypka wzdłuż szyi.` |
| T-9 | S5 (7) | popołudnie | `SC L371` `T MINUS 9 DNI` | Marta w PSE; rozmowa z Karoliną; SMS do Agi (`SC L417` `"Aga, jutro możesz pogadać? Przepraszam, że znowu`) |
| T-9 | S6 (9) | popołudnie | `SC L533` `T MINUS 9 DNI` (nagłówek sceny 6) | `SC L569` `Ares IV milczy od czterdziestu ośmiu godzin.` |
| T-8 | S8 (13) | wieczór | `SC L808` `T MINUS 8 DNI` | Vera czyta nagłówek: `SC L813` `"TAJEMNICZA CHOROBA MĘŻCZYZN -- TRZECI PRZYPADEK W BERLINIE."` |
| T-7 | W-7 (10) | brak | `SC L588` `WSTAWKA MEDIALNA -- T MINUS 7 DNI  [CZAS: ok. 1 min]` | paski: `SC L593` `Pasek TVN: "WIRUS Y (HYV-1): ŚMIERTELNOŚĆ U MĘŻCZYZN WYSOKA -- WHO POTWIERDZA"`; `SC L594` `Pasek TVN24: "WIRUS Y -- ŚMIERTELNOŚĆ BLISKA 100% U HOSPITALIZOWANYCH MĘŻCZYZN"`; SMS 18:23 (`SC L600`) |
| T-7 | S7 (12) | wieczór | `SC L767` `T MINUS 7 DNI` | wideokonferencja: `SC L772` `Śmiertelność wynosi już kilkadziesiąt procent wśród` |
| T-6 | S9 (16) | wieczór | `SC L928` `T MINUS 6 DNI` | pasek: `SC L932` `Na pasku: "WIRUS Y (HYV-1): WHO POTWIERDZA -- ŚMIERTELNOŚĆ 100% U MĘŻCZYZN."` |
| T-5 | W-5 (14) | brak | `SC L837` `WSTAWKA MEDIALNA -- T MINUS 5 DNI  [CZAS: ok. 1 min]` | epidemiolog; SMS 09:47: `SC L853` `Wiadomość od Michała, godzina 09:47:` |
| T-5 | S10 (17) | popołudnie | `SC L977` `T MINUS 5 DNI` | numer Michała niedostępny: `SC L989` `Automat: "Numer jest chwilowo niedostępny."` |
| T-4 | S11 (18) | ranek | `SC L1007` `T MINUS 4 DNI` | PSE: `SC L1023` `Dobrze. Przejmujemy ich stanowiska.` |
| T-2 | S12 (19) | noc | `SC L1050` `T MINUS 2 DNI` | Paweł na OIT |
| T-1 | S13 (20) | świt | `SC L1108` `T MINUS 1 DZIEŃ` | zgon Pawła: `SC L1119` `O czwartej czternaście.` |
| T-1 | W-1 (21) | brak | `SC L1140` `WSTAWKA MEDIALNA -- T MINUS 1 DZIEŃ  [CZAS: ok. 0,75 min]` | `SC L1148` `Ogłaszam stan wyjątkowy na terenie całego kraju.` |
| T0 | S14 (22) | brak (montaż) | `SC L1158` `MONTAŻ -- T ZERO` | Zero Day; `SC L1196` `sto procent. Nie odnotowano żadnego przypadku przeżycia.` |
| T+8 | S15 (23) | świt | `SC L1228` `T PLUS 8` | statek widmo; `SC L1251` `GAZOPORT. Nikt tego nie czyta. Statek sam pamięta, dokąd miał płynąć.` |

**Cofnięcia osi T w kolejności pliku (ROZBIEŻNOŚĆ, rząd 1 wewnątrz SC; AN1 E01-08, N-04):** (1) po S4 (T-9, `SC L294`) następuje W-10 (T-10, `SC L351`); (2) po S7 (T-7, `SC L767`) następuje S8 (T-8, `SC L808`); (3) po W-5 (T-5, `SC L837`) następuje S9 (T-6, `SC L928`). Tylko T-14 ma jawny napis ekranowy w SC (`SC L289` `Napis: T MINUS 14 DNI`) — decyzja o napisach T w montażu: Q4. Nota twierdzi inaczej: `ARCH-01 L34` `**Tor A (teraźniejszość):** ciągły, chronologiczny, bez wyjątków.` — **ROZBIEŻNOŚĆ RK-21**.

### 4.2 Tor B — bloki przeszłości (wiek, napisy, wyzwalacze)

| Blok | Vera (SC) | Dąbrowski (SC / wyliczenie) | Aga (SC) | Napis (SC) | Zdarzenia kanoniczne (SC) | Co poprzedza blok w pliku SC | Wyzwalacz wg noty produkcyjnej (rz.4) |
|---|---|---|---|---|---|---|---|
| P1 | `SC L183` `(VERA MA 24 LATA)` | `SC L204` `Otwiera MAREK DĄBROWSKI -- 30 lat, nieogolony, w za dużej bluzie,` | nie występuje (BRAK DANYCH w SC) | `SC L186` `Napis dyskretny w rogu: "WARSZAWA. 40 LAT WCZEŚNIEJ."` | przyjazd na stypendium doktoranckie (`SC L212`); `SC L218` `Doktorem. Jeszcze nie profesorem. Wejdź.`; projekt: `SC L225` `Twój projekt doktorski -- chromosom Y, mechanizmy` | S2 (po `SC L173` `Normalna środa. Marta wraca do swoich monitorów.`) | `ARCH-01 L37` `- P1 (Vera 24 lata) — wywołany przez scenę 3: widzimy Oslo Verę w laboratorium → cofamy się do początku` — kolejność inna niż w SC (RK-05) |
| P2 | `SC L429` `(VERA MA OKOŁO 35 LAT)` | wiek: BRAK DANYCH w SC (z różnicy 40 lat ok. 41 wg beatów — `AN3 R-06`, materiał rz.4) | `SC L511` `Z pokoju: AGA (mała, może 4-5 lat) wybiega do kuchni.` | `SC L431` `Napis: "WARSZAWA. OK. 11 LAT PO PRZYJEŹDZIE."` | wspólna praca przy tablicy; `SC L447` `Masz rację. Diabeł tkwi w wariancie rs1799945.`; kuchnia, dziecko: `SC L514` `Mamma! Pappa powiedział, że możemy jutro do parku!` | S5 | `ARCH-01 L38` `- P2 (Vera 28 lat) — wywołany przez scenę 5: Marta mówi o Piotrze → scena o Verze i Marku razem` (stary wiek; SC: ok. 35) |
| P3 | `SC L613` `(VERA MA OKOŁO 49 LAT)` | wiek: BRAK DANYCH w SC (ok. 55 wg beatów — `AN3 R-06`) | `SC L636` `Vera siedzi przy stole. Aga (19 lat) właśnie wróciła --` | `SC L615` `Napis: "WARSZAWA. OK. 25 LAT PO PRZYJEŹDZIE."` | Vera widzi Marka z doktorantką (`SC L622`); `SC L676` `Wiem o Kaśce.`; wyjazd: `SC L721` `Jest projekt w Oslo. Dostałam finansowanie.` | W-7 | `ARCH-01 L39` `- P3 (Vera 46 lat) — wywołany przez scenę 8: Vera patrzy na publikację Marka → cofamy się do odkrycia zdrady` (stary wiek; wyzwalacz S8 leży **po** P3 w SC — `AN3 R-58`) |
| P4 | `SC L867` `(VERA MA OKOŁO 52 LATA)` | w kadrze nie występuje; autor artykułu: `SC L879` `Autor: prof. Marek Dąbrowski, Uniwersytet Warszawski.` | nie występuje (BRAK DANYCH w SC) | `SC L869` `Napis: "OSLO. DWA LATA PO WYJEŹDZIE Z WARSZAWY."` | przypis: `SC L889` `"Dane wstępne: V. Strand (materiały niepublikowane)."`; `SC L901` `Moje.`; tablica: `SC L919` `Jedno słowo: "Adam."` | W-5 | `ARCH-01 L40` `- P4 (Vera 52 lata) — wywołany przez scenę 8: Vera chowa wydruk → cofamy się do momentu kradzieży i narodzin "Adama"` |

**Arytmetyka osi życia (wyliczenie z SC; fakty podane w SC oznaczone cytatem, reszta = rachunek, nie kanon):**

| Pozycja | Wartość | Skąd |
|---|---|---|
| Vera dziś (T-14) | 64 lata | `SC L37` `64 lata. Norweska wirusolog. Mówi po polsku z akcentem.` |
| Vera w P1 | 24 lata = 64 − 40 | `SC L186` `40 LAT WCZEŚNIEJ` (zgodne) |
| Vera w P2 | ok. 35 lat = 24 + 11 | `SC L431` `OK. 11 LAT PO PRZYJEŹDZIE` (zgodne) |
| Vera w P3 | ok. 49 lat = 24 + 25 | `SC L615` `OK. 25 LAT PO PRZYJEŹDZIE` (zgodne) |
| Vera w P4 | ok. 52 lata; 2 lata po wyjeździe z Warszawy | `SC L869` (zgodne z wyjazdem ok. 49–50 lat: `SC L704` `Cięcie. Kilka tygodni później.` w P3) |
| Dąbrowski dziś / w P1 | 70 / 30 lat → różnica 40 lat | `SC L45` `70 lat.` i `SC L204` (zgodne) |
| Aga dziś | 34 lata | `SC L39` `34 lata.` |
| Aga w P2 / P3 | 4–5 lat / 19 lat | `SC L511`; `SC L636` |
| Wiek Very przy urodzeniu Agi | 30 lat (wyliczenie 64 − 34; zgodne z P2: 35 − 5 i P3: 49 − 19) | `ADR L25` `Vera urodziła Agę w wieku 30 lat.` (rz.4; zgodne z rachunkiem) |

*Rozbieżność arytmetyczna wewnątrz SC (RK-30):* `SC L885` `To są jej wyniki. Jej metodologia. Jej pięć lat pracy` i `SC L886` `przed wyjazdem i trzynaście lat przed tym.` (5 + 13 = 18 lat) wobec `SC L615` `OK. 25 LAT PO PRZYJEŹDZIE` (25 lat w Warszawie).

### 4.3 Odnośniki osi

Szczegóły napisów T i P i ich realizacji: `A02_przewodnik_wizualny.md` (rytm i wygląd), `D01_plan_montazu.md` (miejsce w montażu), `A06_biblia_rekwizytow_i_ciaglosci.md` (lista tekstów ekranowych). Stany mapy PSE na osi T (4 stany): `AN3 R-50`, `R-51` — nie rozstrzygamy tu.

---

## 5. Rejestr faktów kanonicznych (osoby, relacje, wiek, miejsca)

Źródłem faktu jest **SC** (cytat). Kolumna „Uwagi” wskazuje, gdzie wiek, imię lub rola są BRAK DANYCH w SC albo spory. Wymyślonych imion, wieku, dat i zdarzeń w tym rejestrze nie ma.

### 5.1 Osoby

| ID | Postać | Wiek w E01 | Rola / opis (SC) | Segmenty (3.1 i 4) | Źródło (cytat) | Uwagi / rozbieżność |
|---|---|---|---|---|---|---|
| O-01 | Dr Marta Kowalska | 38 lat | analityczka sieci PSE; żona Piotra Kowalskiego, astronauty Ares IV | S1 (głos), S2, S5, S6, S9, S11, S14 | `SC L33` `38 lat. Analityczka sieci PSE. Skupiona, pragmatyczna.`; `SC L34` `Żona Piotra Kowalskiego -- astronauty Ares IV.` | strój i wygląd: AN3 R-11 [KANON, lekki]; Piotr bez imienia w scenach (AN1 E01-11) |
| O-02 | Karolina Kowalska | 19 lat | córka Marty i Piotra; studentka informatyki | S1, S5 (głos), W-7 (telefon), W-5 (telefon), S9, S10, S14 | `SC L35` `19 lat. Córka Marty i Piotra. Studentka informatyki.` | kolor włosów: SC nie opisuje; materiały sprzeczne (AN3 R-07 KRYTYCZNA) — RK-09; [KANON] Q1 |
| O-03 | Michał Zawadzki | 22 lata | chłopak Karoliny | S1; w S10 i S14 tylko sweter; wiadomości w W-7, W-5, S10 | `SC L36` `22 lata. Chłopak Karoliny. Zwykły, ciepły, żywy.` | nazwisko: RK-11; nadruk swetra: RK-10 |
| O-04 | Prof. Vera Strand | 64 lata (dziś); 24 / ok. 35 / ok. 49 / ok. 52 (bloki) | norweska wirusolog; twórczyni wirusa Y; mówi po polsku z akcentem | S3, S8, S14; P1, P2, P3, P4 | `SC L37` `64 lata. Norweska wirusolog. Mówi po polsku z akcentem.`; `SC L38` `Twórczyni wirusa Y. Tylko ona wie.` | wygląd w pięciu epokach: AN3 R-12; język: RK-18, RK-19 |
| O-05 | Dr Aga Bryk z d. Strand | 34 lata (dziś); 4–5 lat (P2); 19 lat (P3) | doktor chorób zakaźnych, Szpital Bielański; żona Pawła; matka dwóch córek; córka Very | S4, S5 (adresatka SMS), S7, S12, S13, S14; P2, P3 | `SC L39` `34 lata. Doktor chorób zakaźnych, Szpital Bielański.`; `SC L40` `Żona Pawła. Matka dwóch córek. Córka Very.`; `SC L41` `Widz tego jeszcze nie wie.` | wiedza widza: RK-01 (ECHO-020) |
| O-06 | Dr Paweł Bryk | 38 lat | chirurg, Szpital Bielański; mąż Agi; umiera w E01 | S4, S7 (za szybą), S12; zgon w S13 (poza kadrem) | `SC L42` `38 lat. Chirurg, Szpital Bielański. Mąż Agi.`; `SC L43` `Umrze w tym odcinku.` | dzień zgonu: RK-26 |
| O-07 | Tomek Wiśniewski | 35 lat | podwładny Marty w PSE | S2, S6; nieobecny w S11 | `SC L44` `35 lat. Podwładny Marty w PSE.`; `SC L1012` `Gdzie jest Tomek?` | w S11 nie ma go (żona: `SC L1015` `Dzwoniła jego żona. Ma gorączkę od przedwczoraj.`) |
| O-08 | Prof. Marek Dąbrowski | 70 lat (dziś); 30 lat (P1) | polski wirusolog, UW; były mąż Very; ojciec Agi; umiera poza kadrem w Zero Day | P1, P2, P3 (w kadrze); w S8 i P4 tylko jako autor publikacji | `SC L45` `70 lat. Polski wirusolog, UW. Były mąż Very,`; `SC L46` `ojciec Agi. Pojawia się tylko w scenach przeszłości`; `SC L47` `i umiera poza kadrem w Zero Day.` | śmierć bez ujęcia — AN1 D-06 (RK-25); wiek w P2/P3 BRAK DANYCH w SC (RK-08) |
| O-09 | Joanna | BRAK DANYCH (SC nie podaje) | pielęgniarka na oddziale chorób zakaźnych | S4, S13 | `SC L321` `PIELĘGNIARKA JOANNA czeka.` | — |
| O-10 | Marcin | BRAK DANYCH | pracownik w terenie (głos przez radio; naprawa izolacji wymaga zgody Marty); „na miejscu od siódmej” | S2 (wzmianka), S5 (głos) | `SC L141` `Wiem. Widziałam wieczorem. Mamy Marcina na miejscu?`; `SC L374` `przez słuchawki z Marcinem w terenie.` | nie występuje w kadrze |
| O-11 | Beata | BRAK DANYCH | współpracownica Marty w PSE | S11 | `SC L1011` `MARTA (do Beaty)`; `SC L1027` `Dawałam radę na szkoleniu trzy lata temu.` | — |
| O-12 | Agnieszka i Ela | BRAK DANYCH | dwie kobiety wchodzące do sali PSE z laptopami; Marta przydziela im stanowiska R-19 i R-22 (że to te same osoby — wniosek z kontekstu) | S11 | `SC L1032` `Marta siada przy konsoli Tomka. Dwie inne kobiety`; `SC L1037` `Agnieszka -- bierz R-dziewiętnaście. Ela -- R-dwadzieścia dwa.` | `R-19` i `R-22` to oznaczenia stanowisk z dialogu (znaczenie w SC niezdefiniowane) |
| O-13 | Kacper i drugi „Marek” | BRAK DANYCH | nieobecni koledzy z PSE (tylko w kwestii Beaty) | S11 (wzmianka) | `SC L1016` `I Marek też nie będzie. I Kacper powiedział, że...` | drugi „Marek” obok Dąbrowskiego — RK-27 |
| O-14 | Dyżurna | BRAK DANYCH | dyżurna w PSE | S6 | `SC L542` `DYŻURNA` | — |
| O-15 | Wicepremier Wolska | BRAK DANYCH w E01 (imię i wiek) | wicepremier; stoi za premierem, bez zbliżenia | W-1 | `SC L1151` `Za plecami premiera -- kobieta. Wicepremier Wolska.` | `SC2 L42` `Wicepremier Katarzyna Wolska  ~58 lat.` (E02); spór o imię i wiek: `PLAN L62` — decyzja PLAN D4 otwarta |
| O-16 | Premier | BRAK DANYCH | ogłasza stan wyjątkowy | W-1 | `SC L1147` `PREMIER`; `SC L1148` `Ogłaszam stan wyjątkowy na terenie całego kraju.` | podstawa prawna NIEPOTWIERDZONE (AN1 E01-28) |
| O-17 | Prezenterka | BRAK DANYCH | prezenterka studia; ta sama w W-10 i W-1 | W-10, W-1 | `SC L357` `PREZENTERKA`; `SC L1144` `Prezenterka -- ta sama bluzka drugi dzień z rzędu.` | jeden wizerunek w dwóch wstawkach — AN3 L-01, L-13 |
| O-18 | Epidemiolog | BRAK DANYCH | kobieta, „zmęczona, bez owijania w bawełnę” | W-5 | `SC L841` `Studio. Epidemiolog -- zmęczona, bez owijania w bawełnę:` | — |
| O-19 | Lekarz z Berlina | BRAK DANYCH | uczestnik wideokonferencji | S7 | `SC L771` `LEKARZ Z BERLINA` | — |
| O-20 | Rzecznik WHO / kobieta na podium | BRAK DANYCH | czyta z kartki; w Genewie podaje dane o wirusie | S14 | `SC L1167` `Nie może skończyć. Ktoś jej podaje szklankę wody.`; `SC L1194` `RZECZNIK WHO (po angielsku -- napisy polskie)` | etykieta kwestii w formie męskiej, a opis: `SC L1191` `Genewa. Konferencja prasowa WHO. Ta sama kobieta, co wcześniej` — **drobna ROZBIEŻNOŚĆ w SC** (forma etykiety vs opis) |
| O-21 | Kobieta w centrum ESA (Darmstadt) | BRAK DANYCH | przy konsoli; ekran „ARES IV -- SIGNAL INTERRUPTED.” | S14 | `SC L1187` `Centrum dowodzenia ESA, Darmstadt. Kobieta przy konsoli.` | — |
| O-22 | Studentka (P1) | BRAK DANYCH | wskazuje Verze drogę | P1 | `SC L196` `STUDENTKA (wskazuje)` | — |
| O-23 | Doktorantka (P3) | „może 27 lat” | doktorantka przy biurku Dąbrowskiego | P3 | `SC L622` `Przez szparę: Marek przy biurku. Obok niego -- DOKTORANTKA,`; `SC L623` `może 27 lat. Przechylona nad jego biurkiem. Zbyt blisko.` | imię „Kaśka” pada w `SC L676` `Wiem o Kaśce.`, ale SC nie łączy wprost doktorantki z „Kaśką” (wniosek z kontekstu, NIEPOTWIERDZONE) |
| O-24 | Pacjent (S4) | „około 45 lat” | mężczyzna z gorączką i wysypką | S4 | `SC L318` `Aga wchodzi do sali. Przy łóżku -- mężczyzna, około 45 lat.` | — |
| O-25 | Dwie córki Agi | BRAK DANYCH w E01 (imiona i wiek tylko w E02: Hania 4 l., Zosia 2 l.) | „dwie małe dziewczynki” na zdjęciu profilowym | S8 (zdjęcie) | `SC L824` `Kontakt: "Aga". Zdjęcie profilowe -- Aga z dwiema małymi` | `SC2 L39` `Matka dwóch córek: Hania (4 l.) i Zosia (2 l.).` (E02) |
| O-26 | Bożena | BRAK DANYCH | osoba, u której są dziewczynki | S12 | `SC L1082` `Tak. U Bożeny. Śpią już pewnie.` | dziwna fraza: `SC L1079` `Dziewczynki są u twojej mamy sąsiadki?` — RK-23 |
| O-27 | Piotr Kowalski | BRAK DANYCH w scenach | mąż Marty; astronauta Ares IV; w E01 tylko nota i obsada | (brak w segmentach) | `SC L34` `Żona Piotra Kowalskiego -- astronauty Ares IV.` | imię nie pada w żadnej scenie — AN1 E01-11, D-07 |
| O-28 | Rodzice Michała | BRAK DANYCH | mama kupiła sweter; tata w szpitalu | S1 (wzmianka), S9 (wzmianka), W-7 (wzmianka) | `SC L79` `Mama kupiła na świętego Mikołaja. Powiedziałem, że ładny.`; `SC L938` `Michał mówi, że jego tata jest w szpitalu od wczoraj.` | — |
| O-29 | „Marta” — koleżanka Agi ze studiów | BRAK DANYCH | wzmiankowana w pytaniu Marty do Tomka | S2 | `SC L164` `Słuchaj -- ta koleżanka Agi Bryk ze studiów, Marta`; `SC L165` `ma na imię jak ja, dzwoniła ostatnio?` | pytanie Marty o osobę o jej imieniu — AN1 E01-10; RK-28 |
| O-30 | Martwa załoga gazowca | BRAK DANYCH | mężczyźni na pokładzie; robocze kombinezony | S15 | `SC L1242` `Na pokładzie, pod nadbudówką, leżą postacie. Mężczyźni. Nieruchomi.` | filtry treści: BRAK DANYCH (GM-16) |


### 5.2 Relacje

| ID | Relacja | Strony | Źródło (cytat) | Status / uwagi |
|---|---|---|---|---|
| RL-01 | matka — córka | Marta — Karolina | `SC L35` `Córka Marty i Piotra.` | kanon SC |
| RL-02 | żona — mąż (Ares IV) | Marta — Piotr | `SC L34` `Żona Piotra Kowalskiego -- astronauty Ares IV.` | kanon SC (nota); w scenach brak imienia Piotra |
| RL-03 | para | Karolina — Michał | `SC L36` `Chłopak Karoliny.`; `SC L87` `Michał też. Bierze jej rękę.` | kanon SC |
| RL-04 | przełożona — podwładny | Marta — Tomek | `SC L44` `Podwładny Marty w PSE.` | kanon SC; AN3 R-60: `U07` nazywa Martę „żoną” zamiast „szefową” — rz.4 |
| RL-05 | małżeństwo | Aga — Paweł | `SC L42` `Mąż Agi.`; `SC L316` `nie kłótnia, małżeństwo po kilku latach szpitalnych dyżurów.` | kanon SC |
| RL-06 | matka — córki | Aga — dwie córki | `SC L40` `Żona Pawła. Matka dwóch córek. Córka Very.` | kanon SC; imiona córek tylko w E02 |
| RL-07 | matka — córka | Vera — Aga | `SC L40` `Córka Very.`; `SC L514` `Mamma! Pappa powiedział, że możemy jutro do parku!` | relacja = kanon SC; **wiedza widza o niej** = ROZBIEŻNOŚĆ RK-01 |
| RL-08 | byli małżonkowie / partnerzy | Vera — Dąbrowski | `SC L45` `Były mąż Very,`; `SC L676` `Wiem o Kaśce.` | kanon SC (nota); moment zostania parą nierozstrzygnięty — AN1 D-04, E01-03; D-11 (mąż czy partner) |
| RL-09 | doktorantka — opiekun naukowy | Vera — Dąbrowski (P1) | `SC L213` `Departament wirusologii. Pan profesor... pan jest`; `SC L214` `opiekunem naukowym?` | kanon SC |
| RL-10 | ojciec — córka | Dąbrowski — Aga | `SC L46` `ojciec Agi.`; `SC L520` `Pappaaaaa. Jutro park?`; `SC L654` `Tata dzwonił. Pyta, czy przyjdę w sobotę na obiad.` | kanon SC; sprzeczność „sobota” a noc w kuchni — AN1 E01-05 |
| RL-11 | znajome (Marta — Aga) | Marta — Aga | `SC L417` `"Aga, jutro możesz pogadać? Przepraszam, że znowu`; `SC2 L41` `Przyjaciółka Marty -- znajomość z czasów studenckich.` | źródło relacji w E01 niejasne (jedyny ślad: SMS i pytanie `SC L164`) — AN1 E01-10, D-13; „ze studiów” z obsady E02 |
| RL-12 | lekarka — pielęgniarka | Aga — Joanna | `SC L321` `PIELĘGNIARKA JOANNA czeka.`; `SC L345` `Już zleciłam. Doktor -- myśli pani, że to poważne?` | kanon SC |
| RL-13 | współpraca w PSE | Marta — Marcin, Beata, Agnieszka, Ela | `SC L374` `przez słuchawki z Marcinem w terenie.`; `SC L1037` `Agnieszka -- bierz R-dziewiętnaście. Ela -- R-dwadzieścia dwa.` | kanon SC |
| RL-14 | rodzice — syn | rodzice Michała — Michał | `SC L79` `Mama kupiła na świętego Mikołaja. Powiedziałem, że ładny.`; `SC L938` | kanon SC |
| RL-15 | opieka nad dziećmi | Bożena — dwie córki Agi | `SC L1082` `Tak. U Bożeny. Śpią już pewnie.` | kanon SC; RK-23 |
| RL-16 | premier — wicepremier | Premier — Wolska | `SC L1151` `Za plecami premiera -- kobieta. Wicepremier Wolska.` | kanon SC |

### 5.3 Wiek — zestawienie (wszystkie liczby z SC)

| Postać | Epoka / moment | Wiek wg SC | Linia | Uwagi |
|---|---|---|---|---|
| Marta | teraźniejszość | 38 | `SC L33` | — |
| Karolina | teraźniejszość | 19 | `SC L35` | — |
| Michał | teraźniejszość | 22 | `SC L36` | — |
| Vera | teraźniejszość / P1 / P2 / P3 / P4 | 64 / 24 / ok. 35 / ok. 49 / ok. 52 | `SC L37`; `SC L183`; `SC L429`; `SC L613`; `SC L867` | spójne z napisami (4.2) |
| Aga | teraźniejszość / P2 / P3 | 34 / 4–5 / 19 | `SC L39`; `SC L511`; `SC L636` | — |
| Paweł | teraźniejszość | 38 | `SC L42` | — |
| Tomek | teraźniejszość | 35 | `SC L44` | — |
| Dąbrowski | teraźniejszość (poza kadrem) / P1 | 70 / 30 | `SC L45`; `SC L204` | P2 i P3: BRAK DANYCH w SC |
| Pacjent (S4) | teraźniejszość | około 45 | `SC L318` | — |
| Doktorantka (P3) | P3 | może 27 | `SC L623` | — |
| Pozostałe postacie wymienione w 5.1 | — | BRAK DANYCH w SC | — | wiek wpisany w materiałach rz.4 (np. beaty) nie jest kanonem |

### 5.4 Miejsca

| ID | Miejsce | Segmenty | Nagłówek / opis (SC) | Uwagi / rozbieżność |
|---|---|---|---|---|
| LK-01 | Nowy Świat, Warszawa; murek przed budynkiem uczelni | S1 | `SC L63` `EXT./INT. WARSZAWA -- RANEK, ZWYKŁY DZIEŃ`; `SC L72` `KAROLINA i MICHAŁ siedzą na murku przed budynkiem uczelni.` | `SC L68` `Warszawa z zewnątrz. Tramwaj na Nowym Świecie. Ludzie z kawami` |
| LK-02 | Centrum Dyspozytorskie PSE, Warszawa | S2, S5, S6, S11, S14 | `SC L127` `INT. CENTRUM DYSPOZYTORSKIE PSE, WARSZAWA -- TO SAMO RANO`; `SC L131` `Ogromna sala operacyjna. Na telebimie mapa sieci energetycznej` | szafa z teczką w sali: `SC L158`; ewolucja sali: `AN3 R-52` |
| LK-03 | Wydział Biologii UW — korytarz i gabinet Dąbrowskiego | P1 | `SC L182` `INT. KORYTARZ WYDZIAŁU BIOLOGII UW / GABINET DĄBROWSKIEGO -- PRZESZŁOŚĆ` | dwie epoki wyglądu gabinetu — A05 |
| LK-04 | Laboratorium UW i mieszkanie Very i Marka (kuchnia) | P2 | `SC L428` `INT. LABORATORIUM UW / MIESZKANIE -- PRZESZŁOŚĆ`; `SC L498` `Przy ścianie -- krzesełko dziecięce. Puste -- dziecko gdzieś` | — |
| LK-05 | Korytarz wydziału / gabinet / mieszkanie (kuchnia) | P3 | `SC L612` `INT. KORYTARZ WYDZIAŁU / GABINET / MIESZKANIE -- PRZESZŁOŚĆ` | — |
| LK-06 | Laboratorium BSL-4, Oslo | S3 | `SC L258` `INT. LABORATORIUM BIOSAFETY LEVEL 4, OSLO -- TERAŹNIEJSZOŚĆ` | kombinezon „P3” — NIEPOTWIERDZONE (AN1 E01-23) |
| LK-07 | Mieszkanie Very, Oslo | S8 | `SC L807` `INT. MIESZKANIE VERY, OSLO -- WIECZÓR`; `SC L810` `Mieszkanie ascetyczne. Tu się pracuje, nie żyje.` | — |
| LK-08 | Gabinet uniwersytecki w Oslo, mieszkanie, laboratorium nocne | P4 | `SC L866` `INT. GABINET W OSLO / MIESZKANIE W OSLO -- PRZESZŁOŚĆ`; `SC L909` `Vera przy stanowisku. Nie projekt, który finansuje uczelnia.` | nota: „Warszawa” — por. 3.2 |
| LK-09 | Szpital Bielański — oddział chorób zakaźnych | S4, S7 | `SC L293`; `SC L766` `INT. SZPITAL BIELAŃSKI, ODDZIAŁ CHORÓB ZAKAŹNYCH -- WIECZÓR` | sala z oknem na korytarz (S7): `SC L795` `Wstaje. Idzie do okna. Na korytarzu za szybą -- Paweł.` |
| LK-10 | Szpital Bielański — OIT | S12 | `SC L1049` `INT. SZPITAL BIELAŃSKI, OIT -- NOC` | — |
| LK-11 | Szpital Bielański — korytarz | S13 | `SC L1107` `INT. SZPITAL BIELAŃSKI, KORYTARZ -- ŚWIT` | — |
| LK-12 | Salon Marty | S9 | `SC L927` `INT. SALON MARTY -- WIECZÓR` | — |
| LK-13 | Pokój Karoliny | S10 | `SC L976` `INT. POKÓJ KAROLINY -- POPOŁUDNIE` | „mieszkanie Karoliny” w S14 (`SC L1178` `Mieszkanie Karoliny. Karolina siedzi na podłodze pod oknem.`) — RK-14 |
| LK-14 | Studio informacyjne TV | W-10, W-7, W-5, W-1 | `SC L355` `Studio informacyjne. Prezenterka przy biurku.`; `SC L841` `Studio. Epidemiolog -- zmęczona, bez owijania w bawełnę:` | nagłówków lokacji brak (wstawki) |
| LK-15 | Kolejki przed szpitalem i apteką w Warszawie | W-7 | `SC L597` `Kolejka przed szpitalem w Warszawie -- długa, spokojna.`; `SC L598` `Kolejka przed apteką -- wykupione maseczki.` | kadr bez postaci z obsady (sekcja 7) |
| LK-16 | Mapa świata (ekran) | S14 | `SC L1162` `Mapa świata. Pomarańczowa -- od brzegów ku środkowi.` | — |
| LK-17 | WHO — podium i Genewa (konferencja prasowa) | S14 | `SC L1167`; `SC L1191` `Genewa. Konferencja prasowa WHO. Ta sama kobieta, co wcześniej` | realna instytucja — RK/Q9 |
| LK-18 | Ulice Warszawy (puste) | S14 | `SC L1169` `Ulice Warszawy. Puste. Jeden pies bez smyczy.` | — |
| LK-19 | Szpital — korytarz (Aga biegnie) | S14 | `SC L1175` `Szpital. Aga biegnie korytarzem.` | — |
| LK-20 | Mieszkanie Karoliny | S14 | `SC L1178` `Mieszkanie Karoliny. Karolina siedzi na podłodze pod oknem.` | RK-14 |
| LK-21 | Hotel w Oslo | S14 | `SC L1183` `Vera w anonimowym hotelu w Oslo. Telewizor. Mapa świata.` | — |
| LK-22 | Centrum dowodzenia ESA, Darmstadt | S14 | `SC L1187` `Centrum dowodzenia ESA, Darmstadt. Kobieta przy konsoli.` | realna instytucja |
| LK-23 | Laboratorium (Aga przy stole) | S14 | `SC L1213` `Aga -- przy stole w laboratorium.` | lokalizacja nieokreślona w SC |
| LK-24 | Bałtyk, pokład gazowca LNG | S15 | `SC L1227` `EXT. BAŁTYK / POKŁAD GAZOWCA LNG -- ŚWIT` | most do E02 prolog (RK-35) |

*Nazwy w dialogu (znaczenie w SC niezdefiniowane):* `Rogowiec` (`SC L138` `Dobry. Rogowiec znowu dał znać o sobie.`), stanowiska `R-17`, `R-16`, `R-19`, `R-22`; wystawa w Zachęcie (`SC L392`); Berlin, Genewa, Niemcy, Francja, Skandynawia (`SC L359` `niezidentyfikowane`…).

### 5.5 Fakty o świecie potrzebne montażowi (kanon SC; naukowe NIEPOTWIERDZONE)

| ID | Fakt | Źródło (cytat) | Uwagi |
|---|---|---|---|
| F-01 | Wirus Y; klinicznie HYV-1 | `SC L593` `WIRUS Y (HYV-1)`; `SC L1195` `Wirus Y. Klinicznie HYV-1. Śmiertelność u mężczyzn:` | nazwa „ADAM-1” w materiałach produkcyjnych jest nieaktualna (`ADR L12`; AN3 R-53) |
| F-02 | Śmiertelność u mężczyzn: sto procent; brak przeżyć | `SC L1196` `sto procent. Nie odnotowano żadnego przypadku przeżycia.` | eskalacja liczb — RK-22 |
| F-03 | Mechanizm: chromosom Y, kaskada w komórkach odpornościowych, „ktoś to zaprojektował” | `SC L779` `Chromosom Y. Wirus rozpoznaje specyficzną sekwencję`; `SC L787` `Ktoś to zaprojektował.`; `SC L791` `WHO i Interpol prowadzą śledztwo.` | naukowo NIEPOTWIERDZONE (AN1) |
| F-04 | „Adam” = nazwa pracy Very (krzywa wzrostu, tablica) | `SC L273` `naukowych -- krzywa wzrostu. Napis pod nią: "Adam".`; `SC L919` `Jedno słowo: "Adam."` | rola kryptonimu: `ADR L16` (rz.4) |
| F-05 | Ares IV milczy 48 godzin (T-9); ekran „SIGNAL INTERRUPTED” (T0) | `SC L569`; `SC L1188` `Miga ekran: "ARES IV -- SIGNAL INTERRUPTED."` | oś milczenia — RK-02 |
| F-06 | Stan wyjątkowy ogłoszony na T-1 | `SC L1148` | podstawa prawna NIEPOTWIERDZONE (AN1 E01-28) |
| F-07 | Marker `rs1799945` w dialogu P2 | `SC L447` `Masz rację. Diabeł tkwi w wariancie rs1799945.` | NIEPOTWIERDZONE; marker genu HFE wg `PLAN L109` (rz.4) |
| F-08 | Gazowiec LNG płynie na autopilocie do gazoportu w Świnoujściu, załoga martwa (T+8) | `SC L1237` `Płynie. Powoli, równo, prosto. Za rufą`; `SC L1250`; `SC L1251` | logika T+8 — AN1 E01-29 NIEPOTWIERDZONE |

### 5.6 Teksty ekranowe z SC (dosłownie; realizacja w montażu — ZS-07, decyzja Q4)

| ID | Tekst (dosłownie z SC) | Segment | Typ | Źródło |
|---|---|---|---|---|
| TE-01 | `"WARSZAWA. 40 LAT WCZEŚNIEJ."` | P1 | napis w rogu | `SC L186` `Napis dyskretny w rogu: "WARSZAWA. 40 LAT WCZEŚNIEJ."` |
| TE-02 | `T MINUS 14 DNI` | S3 | napis | `SC L289` `Napis: T MINUS 14 DNI` |
| TE-03 | `"WHO -- POSIEDZENIE KRYZYSOWE."` | W-10 | pasek TV | `SC L364` `Pasek na dole: "WHO -- POSIEDZENIE KRYZYSOWE."` |
| TE-04 | `"Karolina"` | S5 | wyświetlacz telefonu | `SC L383` `Telefon na biurku. Wyświetlacz: "Karolina"` |
| TE-05 | `"Aga, jutro możesz pogadać? Przepraszam, że znowu o złej porze. M."` | S5 | SMS (drugi telefon Marty) | `SC L417` `"Aga, jutro możesz pogadać? Przepraszam, że znowu`; `SC L418` `o złej porze. M."` |
| TE-06 | `"WARSZAWA. OK. 11 LAT PO PRZYJEŹDZIE."` | P2 | napis | `SC L431` |
| TE-07 | `"WIRUS Y (HYV-1): ŚMIERTELNOŚĆ U MĘŻCZYZN WYSOKA -- WHO POTWIERDZA"` | W-7 | pasek TVN | `SC L593` |
| TE-08 | `"WIRUS Y -- ŚMIERTELNOŚĆ BLISKA 100% U HOSPITALIZOWANYCH MĘŻCZYZN"` | W-7 | pasek TVN24 | `SC L594` |
| TE-09 | `"MALE DEATHS SURGE ACROSS EUROPE"` | W-7 | pasek CNN (EN) | `SC L595` `Pasek CNN po angielsku: "MALE DEATHS SURGE ACROSS EUROPE"` |
| TE-10 | `"Cześć :) słyszałaś o tym? Tata mówi żeby się nie panikować. Mam trochę gardło ale pewnie z klimy. Jutro normalnie tak?"` (18:23) | W-7 | SMS Michała | `SC L600` `Kadr: telefon Karoliny. Wiadomość od Michała, godzina 18:23:`; `SC L601`; `SC L602` |
| TE-11 | `"WARSZAWA. OK. 25 LAT PO PRZYJEŹDZIE."` | P3 | napis | `SC L615` |
| TE-12 | `"TAJEMNICZA CHOROBA MĘŻCZYZN -- TRZECI PRZYPADEK W BERLINIE."` | S8 | nagłówek portalu | `SC L813` |
| TE-13 | `"V. Strand (dane własne, niepublikowane)."` | S8 | przypis na wydruku | `SC L819` |
| TE-14 | `Kontakt: "Aga"` | S8 | ekran telefonu Very | `SC L824` |
| TE-15 | `"Jestem w szpitalu, to pewnie nic. Przyjdź dzisiaj?"` (09:47) | W-5 | SMS Michała | `SC L853` `Wiadomość od Michała, godzina 09:47:`; `SC L854` |
| TE-16 | `"OSLO. DWA LATA PO WYJEŹDZIE Z WARSZAWY."` | P4 | napis | `SC L869` |
| TE-17 | `"Selektywna kaskada odpornościowa przy sekwencji chromosomu Y -- nowy mechanizm i implikacje kliniczne."` ; autor: prof. Marek Dąbrowski, Uniwersytet Warszawski | P4 | strona czasopisma | `SC L877` `Tytuł: "Selektywna kaskada odpornościowa przy sekwencji`; `SC L878`; `SC L879` |
| TE-18 | `"Dane wstępne: V. Strand (materiały niepublikowane)."` | P4 | przypis (str. 14) | `SC L889` |
| TE-19 | `"Adam."` | P4 | tablica | `SC L919` |
| TE-20 | `"WIRUS Y (HYV-1): WHO POTWIERDZA -- ŚMIERTELNOŚĆ 100% U MĘŻCZYZN."` | S9 | pasek | `SC L932` |
| TE-21 | `"Gorączka trochę spada. Nie martw się."` (wczoraj, wieczór) | S10 | SMS Michała | `SC L984`; `SC L985` |
| TE-22 | `"Numer jest chwilowo niedostępny."` | S10 | komunikat automatu (dźwięk) | `SC L989` |
| TE-23 | `"ARES IV -- SIGNAL INTERRUPTED."` | S14 | ekran ESA | `SC L1188` |
| TE-24 | `SWINOUJSCIE -- GAZOPORT` | S15 | ekran nawigacji | `SC L1250`; `SC L1251` |
| TE-25 | `"Adam"` (napis pod krzywą wzrostu na ścianie laboratorium) | S3 | napis w scenografii (odręczny) | `SC L272` `Na ścianie: jedyny odręcznie napisany element pośród wydruków`; `SC L273` `naukowych -- krzywa wzrostu. Napis pod nią: "Adam".` |

*Uwaga (runda 3, zarzut E-2-3):* rejestr ma **25 wierszy** (TE-01..TE-25); TE-25 (napis „Adam” w sc. 3, `SC L273`) dopisano na końcu, żeby nie zmieniać istniejących numerów TE-01..TE-24 — kolejność ID nie jest kolejnością SC. Sprawdzenie: wszystkie linie SC z napisem, paskiem, wiadomością, nagłówkiem, kontaktem, tytułem, przypisem lub ekranem (grep po `napis|pasek|wyświetlacz|ekran|wiadomość|tytuł|kontakt|przypis|nagłówek`) mają wiersz TE albo są opisem bez dosłownego tekstu; teksty cytowane także w MO-05 i F-04 (`SC L273`) są teraz w TE-25. TE-19 („Adam.” na tablicy P4, `SC L919`) to inny napis niż TE-25.

**Rozbieżność tekstów ekranowych (RK-31).** Przypis w S8: `SC L819` `V. Strand (dane własne, niepublikowane)` a w P4: `SC L889` `Dane wstępne: V. Strand (materiały niepublikowane)` — dwa różne brzmienia (AN1 E01-27; AN3 R-54).

---

## 6. Rozbieżności kanoniczne i istotne produkcyjnie (bez rozstrzygania)

**Jak czytać.** Każda pozycja ma dwa cytaty z lokalizacją (wersja A i B). Nie wybieramy wersji. „Typ” — [KANON] / [PRODUKT] / [TECH] wg ANALIZA-003. „Odnośnik do rejestru” — ID źródłowe pozycji, którą ma zebrać plik **`E01_rejestr_decyzji_kanonicznych.md`** (temat ZERO-PAKIET-011, równoległy; w chwili pisania tego pliku jego ID nie są jeszcze nadane, więc odnośniki idą do ID źródłowych: AN1 `E01-xx`/`N-xx`/`D-xx`, AN3 `R-xx`/`Q-xx`, `PLAN Dxx`, `ECHO-xxx`). Mapowanie na ID rejestru — do uzupełnienia po jego zatwierdzeniu (sekcja 11).

### 6.1 Rozbieżności kanoniczne (fakty, osoby, oś czasu, struktura)

| ID | Temat | Wersja A (cytat) | Wersja B (cytat) | Typ / status | Odnośnik do rejestru (ID źródłowe) | Wpływ na pakiet |
|---|---|---|---|---|---|---|
| RK-01 | Wiedza widza o relacji Vera–Aga | `SC L16` `Widz nie wie jeszcze, że Aga jest córką Very.` oraz `SC L41` `Widz tego jeszcze nie wie.` | `DECYZJE L26` `Widz wie od E01, ze Vera jest matka Agi; Aga jeszcze nie.` (ECHO-020) | [KANON]; **decyzja podjęta (ECHO-020); zapis w SC czeka na osobny temat poprawek**; w pakiecie obie wersje, bez wyboru | ECHO-020; AN1 E01-01, D-01, E01-32; AN3 R-48, Q8; PLAN D10 | `A03_biblia_postaci.md` (wskazówki aktorskie, np. `ARCH-02 L68` `Aga jest córką Very. Widz nie wie. Nie dajemy żadnych wskazówek.`), `A04_arkusze_glosow.md`, kadrowanie S8; Q1 |
| RK-02 | Oś milczenia Ares IV | `SC L569` `Ares IV milczy od czterdziestu ośmiu godzin.` (T-9) | `SC L1188` `Miga ekran: "ARES IV -- SIGNAL INTERRUPTED."` (T0) | [KANON]; otwarta | AN1 E01-02, D-02, E01-11 | tekst ekranu ESA (TE-23); oś T w 4.1 |
| RK-03 | Cliffhanger z noty a montaż Zero Day | `SC L26` `Odcinek kończy się Zero Day. Cliffhanger: Marta z żółtą` i `SC L27` `teczką i zdjęciem Piotra. Aga przy zwłokach Pawła.` | `SC L1200` `Powrót do Marty. Siedzi sama przy głównej konsoli.` | [KANON]; otwarta (sprzeczność wewnątrz rzędu 1) | AN1 E01-04; AN3 R-28, Q10; PLAN D9 | ZS-12; `A06_biblia_rekwizytow_i_ciaglosci.md` (czy teczka w S14) |
| RK-04 | Koniec odcinka: trzy kadry vs sekwencja SC i sc. 15 | `ARCH-01 L73` `Ostatni kadr to Vera. Jej dłonie. Cisza.` | `SC L1226` `SCENA 15 -- STATEK WIDMO  [CZAS: ok. 1,5 min]`; `SC L1213` `Aga -- przy stole w laboratorium.` | [KANON]; otwarta | AN3 R-26, R-01, Q10; AN1 N-03, E01-04 | `D01_plan_montazu.md`; sekcja 7 (przejścia 14→15) |
| RK-05 | Kolejność P1 względem sc. 3 | `SC L177` `BLOK PRZESZŁOŚCI (1) -- WARSZAWA, LATA WCZEŚNIEJ` (przed sc. 3: `SC L257` `SCENA 3  [CZAS: ok. 2,5 min]`) | `U06 L31` `**SCENA 3 → SCENA P1**` | [KANON]; zapis w SC = P1 przed sc. 3; decyzja Q5 | AN3 R-02, Q9; AN1 E01-18, N-05 | tabela przejść w sekcji 7.5 jest w kolejności SC |
| RK-06 | Napisy bloków P2 i P3 | `U06 L63` `Napis: "WARSZAWA. CZTERY LATA PÓŹNIEJ."`; `U06 L85` `Napis: "WARSZAWA. OSIEMNAŚCIE LAT PO PRZYJEŹDZIE."` | `SC L431` `Napis: "WARSZAWA. OK. 11 LAT PO PRZYJEŹDZIE."`; `SC L615` `Napis: "WARSZAWA. OK. 25 LAT PO PRZYJEŹDZIE."` | [TECH]; obowiązuje SC (zgodne z `ADR L27` `- P2: Vera ~35, Aga ~5 — napis "OK. 11 LAT PO PRZYJEŹDZIE"`) | AN3 R-03, R-04 | TE-06, TE-11 |
| RK-07 | Wiek Very w P2 i P3 | `ARCH-08 L86` `28 lat` (P2); `ARCH-08 L87` `46 lat` (P3) | `SC L429` `(VERA MA OKOŁO 35 LAT)`; `SC L613` `(VERA MA OKOŁO 49 LAT)` | [TECH]; obowiązuje SC | AN3 R-05 | `A03_biblia_postaci.md` (arkusze epok) |
| RK-08 | Wiek i obecność Dąbrowskiego w blokach | `ARCH-08 L93` `- P2 (34 lata): bardziej akademicki, ale wciąż nieformalny.`; `ARCH-02 L95` `**Wiek w przeszłości:** 30 → 52 lata (cztery bloki)` | `SC L204` `Otwiera MAREK DĄBROWSKI -- 30 lat, nieogolony, w za dużej bluzie,`; `SC L46` `ojciec Agi. Pojawia się tylko w scenach przeszłości` (w P4 w kadrze go nie ma) | [TECH]; SC podaje tylko 30 i 70 lat | AN3 R-06 | `A03_biblia_postaci.md` |
| RK-09 | Włosy Karoliny | `ARCH-02 L24` `**Wygląd:** Jasne włosy, niski kucyk lub luźno.` | `UAF L26` `sweater and has NO dinosaur anywhere on her clothing. Dark brown shoulder-length` (SC nie opisuje włosów) | [KANON]; otwarta | AN3 R-07 (KRYTYCZNA), Q1; `P002` pytanie P-5 | `A03_biblia_postaci.md`, `B06_paczka_referencji_s1.md` |
| RK-10 | Nadruk swetra Michała | `SC L73` `On ma sweter -- jasnożółty, z nadrukiem dinozaura w okularach.` | `UAF L22` `- MICHAL: a bright yellow knitted sweater with EXACTLY ONE green cartoon dinosaur` | [KANON]; otwarta (okulary, kolor) | AN3 R-09, Q2; PLAN D12 | `A06_biblia_rekwizytow_i_ciaglosci.md` |
| RK-11 | Nazwisko Michała | `SC L36` `Michał Zawadzki` | `ARCH-02 L34` `### MICHAŁ WIŚNIEWSKI` | [TECH]; obowiązuje SC | AN3 R-10 | `A03_biblia_postaci.md`; „Wiśniewski” to też Tomek (`SC L44`) |
| RK-12 | Strój Marty | `ARCH-02 L10` `ciemne spodnie, bluza firmowa PSE, plecak` | `BS2 L10` `Profesjonalny strój: ciemna marynarka, koszula.` (SC nie opisuje) | [KANON, lekki]; otwarta | AN3 R-11, Q15 | `A03_biblia_postaci.md` |
| RK-13 | Wygląd Very w pięciu epokach | `ARCH-02 L50` `**Wygląd:** Wysoka, siwa, krótko ostrzyżona.` | `ARCH-08 L87` `Ciemniejsze włosy, może pierwsze siwe.` (P3) | [KANON]; brak jednego arkusza (SC nie opisuje włosów) | AN3 R-12, Q15 | `A03_biblia_postaci.md` |
| RK-14 | Sweter po śmierci Michała: krzesło vs fotel; pokój vs mieszkanie | `SC L993` `Na krześle w kącie pokoju -- zostawiony sweter.` (S10: `SC L976` `INT. POKÓJ KAROLINY -- POPOŁUDNIE`) | `SC L1180` `Sweter Michała leży na fotelu.` (S14: `SC L1178` `Mieszkanie Karoliny. Karolina siedzi na podłodze pod oknem.`) | [KANON, lekki]; sprzeczność wewnątrz rzędu 1 | AN3 R-13, Q16; AN1 E01-37 | `A05_biblia_lokacji.md`, `A06_biblia_rekwizytow_i_ciaglosci.md` |
| RK-15 | Metraż E01 | `SC L3` `Format: ok. 60 minut` (suma etykiet 60,5 — sekcja 3.1) | `ADR L44` `- Metraż realny ~52 min + czołówka (62 s); patrz plik ZERO_czolowka.md.`; `AHO L34` `- **E01 — ADAM** (~65 min)`; `ARS L1554` `52 min 15s` (`ARS` = rozpiska sekundowa, tabela 0.4; błąd rachunkowy rozpiski, `AN3 R-14`: suma jej „przyjętych” czasów = 59:00) | [PRODUKT]; otwarta | AN1 E01-30, D-09; AN3 R-14, Q11; PLAN D1 | `C03_budzet_i_koszty.md` (minuty do wygenerowania), `D01_plan_montazu.md`; Q7 |
| RK-16 | Muzyka: „bez muzyki w klipie” a scenariusz | `UAF L50` `birds). NO music, NO score.` | `SC L65` `Muzyka: ciepła, ambientowa, miejska. Żadnego niepokoju.`; `SC L1160` `Muzyka: narasta od zera. Smyczki, cisza, smyczki.` | [PRODUKT]; reguła „dwóch warstw” (klip bez muzyki, muzyka w montażu) to PROPOZYCJA AN3 L-11; ECHO-008: ostateczna reguła audio należy do właściciela | AN3 R-21, R-43, R-57, L-11, Q4 (AN3); PLAN D14 | ZS-01; `A07_biblia_dzwieku.md`, `D03_muzyka_grade_eksport.md`; Q2 |
| RK-17 | Muzyka w sc. 12–14 i koniec muzyki sc. 14 | `ARCH-01 L14` `Montaż paralelny — ale bez muzyki która łączy.`; `U03 L113` `Każdy kadr trwa 5 sekund. Muzyka wygasa po pierwszym. Dwa ostatnie w ciszy.` | `U04 L36` `✓ Bardzo cicha — smyczki na tle` (sc. 12); `U04 L54` `**MOTYW GŁÓWNY SERIALU:** Pojawi się po raz pierwszy na końcu Sceny 14, przez może 4–5 sekund zanim czarny ekran. Zapowiedź, nie rozwinięcie.` | [PRODUKT]; otwarta | AN3 R-22, R-24, Q12 (AN3) | `A07_biblia_dzwieku.md`, `D03_muzyka_grade_eksport.md` |
| RK-18 | Reguła językowa dla kwestii norweskich | `SC L513` `AGA (po norwesku -- napisy polskie)` | `BP3 L21` `Sceny z norweskim (Aga/Vera) — mówione po angielsku z norweskim akcentem Very, napisy PL w poście.` | [KANON]+[PRODUKT]; norweski poza listą 9 języków Klinga (GM-07) | AN3 R-46, R-47, Q6; AN1 D-10; PLAN D11 | ZS-05; `A04_arkusze_glosow.md`, `D02_plan_polskiego_glosu.md`; Q8 |
| RK-19 | Nota językowa a sceny | `SC L52` `Vera mówi po polsku przez cały E01 -- z wyraźnym norweskim akcentem.`; `SC L56` `Z Agą rozmawiały po norwesku -- ale w E01 nie ma ich wspólnej sceny.` | `SC L281` `VERA (do siebie, szeptem, po norwesku -- napisy polskie)`; `SC L516` `VERA (po norwesku, automatycznie, bez zastanowienia)` (P2: wspólna scena Vera–Aga) | [KANON]; sprzeczność wewnątrz rzędu 1 | AN1 E01-15, D-10 | ZS-05 |
| RK-20 | SMS Michała z T-5 a „po wczoraj: nic” w sc. 10 (T-5) | `SC L853` `Wiadomość od Michała, godzina 09:47:` oraz `SC L854` `"Jestem w szpitalu, to pewnie nic. Przyjdź dzisiaj?"` (W-5, T-5) | `SC L984` `Ostatnia wiadomość od Michała: "Gorączka trochę spada.` i `SC L986` `Po wczoraj: nic.` (S10, T-5) | [KANON]; otwarta | AN1 E01-07; AN3 R-49 | TE-15, TE-21; `A06_biblia_rekwizytow_i_ciaglosci.md` |
| RK-21 | Tor A „chronologiczny” a cofnięcia osi T | `ARCH-01 L34` `**Tor A (teraźniejszość):** ciągły, chronologiczny, bez wyjątków.` | `SC L294` `T MINUS 9 DNI` (S4), a potem `SC L351` `WSTAWKA MEDIALNA -- T MINUS 10 DNI  [CZAS: ok. 0,75 min]` (W-10); podobnie S7→S8 i W-5→S9 (4.1) | [KANON]/[PRODUKT]; otwarta | AN1 E01-08, N-04 | 4.1; napisy T w montażu (Q4) |
| RK-22 | Eskalacja liczb śmiertelności | `SC L594` `Pasek TVN24: "WIRUS Y -- ŚMIERTELNOŚĆ BLISKA 100% U HOSPITALIZOWANYCH MĘŻCZYZN"` (T-7) | `SC L772` `Śmiertelność wynosi już kilkadziesiąt procent wśród` (T-7, wieczór); `SC L1196` `sto procent. Nie odnotowano żadnego przypadku przeżycia.` (T0) | [KANON]; otwarta | AN1 E01-06, E01-22 | TE-07, TE-08, TE-20, F-02 |
| RK-23 | „u twojej mamy sąsiadki” | `SC L1079` `Dziewczynki są u twojej mamy sąsiadki?` | `SC L1082` `Tak. U Bożeny. Śpią już pewnie.` | [KANON] (zmiana kwestii = G2); otwarta | AN1 E01-14; PLAN L72 (rz.4) | O-26 |
| RK-24 | Piotr w E01 | `SC L34` `Żona Piotra Kowalskiego -- astronauty Ares IV.` (nota) | w scenach imię `Piotr` nie pada (grep SC: tylko `L27`, `L34`, `L35`); `SC L396` `i Michał powiedział, że mu przypomina tatę.` | [KANON]; otwarta | AN1 E01-11, D-07 | ZS-11; `A03_biblia_postaci.md` |
| RK-25 | Śmierć Dąbrowskiego | `SC L47` `i umiera poza kadrem w Zero Day.` | w montażu sc. 14 (`SC L1157`–`L1224`) brak ujęcia i wzmianki (grep: brak „Dąbrowski”/„Marek”) | [KANON]; otwarta | AN1 E01-12, D-06; PLAN D9 | S14 |
| RK-26 | Dzień śmierci Pawła | `SC L27` `teczką i zdjęciem Piotra. Aga przy zwłokach Pawła.` (nota: na T0) | `SC L1108` `T MINUS 1 DZIEŃ` i `SC L1119` `O czwartej czternaście.` | [KANON]; otwarta | AN1 E01-16, D-05 | 4.1; S13 |
| RK-27 | Drugi „Marek” obok Dąbrowskiego | `SC L1016` `I Marek też nie będzie. I Kacper powiedział, że...` | `SC L45` `Prof. Marek Dąbrowski      70 lat. Polski wirusolog, UW. Były mąż Very,` | [KANON] (zmiana imienia = zmiana kwestii, G2) | AN1 E01-20; AN3 R-59, Q17 | O-13 |
| RK-28 | Źródło znajomości Marta–Aga | `SC L164` `Słuchaj -- ta koleżanka Agi Bryk ze studiów, Marta` i `SC L165` `ma na imię jak ja, dzwoniła ostatnio?` | `SC L417` `"Aga, jutro możesz pogadać? Przepraszam, że znowu` (Marta sama pisze do Agi); `SC2 L41` `Przyjaciółka Marty -- znajomość z czasów studenckich.` | [KANON]; otwarta | AN1 E01-10, D-13; PLAN L73 (rz.4) | RL-11, O-29 |
| RK-29 | Zakres toru A w nocie a sc. 15 | `SC L12` `TOR A -- TERAŹNIEJSZOŚĆ: Warszawa i Oslo, T-14 do T=0.` | `SC L1228` `T PLUS 8` (sc. 15) | [KANON]; otwarta | AN1 E01-17, E01-29, D-14 | 4.1, ZS-03 |
| RK-30 | Arytmetyka lat pracy Very w P4 | `SC L885` `To są jej wyniki. Jej metodologia. Jej pięć lat pracy` i `SC L886` `przed wyjazdem i trzynaście lat przed tym.` (18 lat) | `SC L615` `Napis: "WARSZAWA. OK. 25 LAT PO PRZYJEŹDZIE."` | [KANON, lekki]; otwarta | AN1 E01-09; AN3 R-65; PLAN D7 | 4.2 |
| RK-31 | Dwa różne przypisy | `SC L819` `W przypisach, drobnym drukiem: "V. Strand (dane własne, niepublikowane)."` (S8) | `SC L889` `"Dane wstępne: V. Strand (materiały niepublikowane)."` (P4) | [KANON, lekki] | AN1 E01-27; AN3 R-54 | TE-13, TE-18 |
| RK-32 | Tor B „Warszawa” a P4 w Oslo | `SC L18` `TOR B -- PRZESZŁOŚĆ: Warszawa, lata wcześniej.` | `SC L866` `INT. GABINET W OSLO / MIESZKANIE W OSLO -- PRZESZŁOŚĆ` | [KANON, lekki]; sprzeczność w rzędzie 1 | AN1 E01-17 | 3.2 |
| RK-33 | Nazwa wirusa w materiałach | `U05 L33` `**Co to jest:** Mała fiolka z bezbarwnym płynem — wirus ADAM-1.` | `SC L593` `Pasek TVN: "WIRUS Y (HYV-1): ŚMIERTELNOŚĆ U MĘŻCZYZN WYSOKA -- WHO POTWIERDZA"`; `ADR L12` `Klinicznie: **HYV-1**` | [TECH]; obowiązuje SC/ADR (dokumenty produkcyjne nieaktualne) | AN3 R-53 | F-01 |
| RK-34 | Rzecznik WHO: etykieta a opis | `SC L1194` `RZECZNIK WHO (po angielsku -- napisy polskie)` | `SC L1191` `Genewa. Konferencja prasowa WHO. Ta sama kobieta, co wcześniej` | [KANON, lekki] (drobna; forma gramatyczna) | (nowe w tej biblii; do włączenia do rejestru) | O-20 |
| RK-35 | Ruch statku w E01 a prolog E02; T+8 a T+9 | `SC L1237` `Płynie. Powoli, równo, prosto. Za rufą`; `SC L1228` `T PLUS 8` | `SC2 L70` `Z mgły wyłania się dziób gazowca. Ten sam statek. Dryfuje bokiem do`; `SC2 L54` `T PLUS 9` | [KANON]; otwarta (informacja o serialu: E02) | AN1 N-01, E01-29; AN2 D-05 | 3.4, S15 |
| RK-36 | Sala PSE w sc. 11: dwa miejsca czy 80% | `ARCH-08 L36` `- Scena 11: 80% stanowisk pustych. Zostawione kubki z kawą. Jedno przewrócone krzesło. Nie chaos — po prostu porzucenie` | `SC L1009` `Sala normalnie wyglądająca -- ale dwa miejsca są puste.`; `SC L1172` `Osiemdziesiąt procent stanowisk pustych.` (S14) | [TECH]; obowiązuje SC | AN3 R-52; AN1 E01-20 | `A05_biblia_lokacji.md` |
| RK-37 | Mapa PSE w sc. 5 | `U05 L68` `2. **Scena 5** — INSERT na mapę: więcej pomarańczowego. Subtelna zmiana.` | `SC L373` `Marta przy konsolach. Telebimy spokojne. Rozmawia` | [KANON, lekki] | AN3 R-50, R-51 | `A06_biblia_rekwizytow_i_ciaglosci.md` |

### 6.2 Rozbieżności produkcyjne wpływające na zasady stałe (zbiorczo)

| ID | Temat | Wersja A (cytat) | Wersja B (cytat) | Typ / status | Odnośnik | Wpływ na pakiet |
|---|---|---|---|---|---|---|
| RP-01 | Przejścia: „cięcia” a przenikania | `ARCH-01 L28` `Przejścia między blokami przeszłości a teraźniejszością nie są płynne — są cięciami. Widz ma poczuć skok.` | `U06 L33` `Oslo (Vera 64 lata) → Korytarz UW (Vera 24 lata). Powolne przenikanie.` | [PRODUKT]; otwarta | AN3 L-08; Q12 (ten plik) | sekcja 7.5; `A09_katalog_ujec_uzupelniajacych_i_przejsc.md` |
| RP-02 | Muzyka diegetyczna (kawiarnia, jingle) a „bez muzyki w klipie” | `U04 L18` `Może być diegetic (muzyka z pobliskiej kawiarni). Trwa pod rozmową.` | `UAF L50` `birds). NO music, NO score.` | [PRODUKT]; otwarta | AN3 R-43, R-57 | ZS-01; Q2 |
| RP-03 | Tytuł „ZERO” w klipie a w montażu | `AN3 L434` `At ~6 s the white minimal title "ZERO" fades in` (Clip00 L4, cytat za AN3 R-41; scenariusz tytułu w sc. 1 nie ma) | `UAF L46` `any text into the video).` | [PRODUKT]; otwarta | AN3 R-41; `P002` P-7 | ZS-07 |
| RP-04 | Metoda Extend (Flow) a brak przedłużania w Klingu 4.0 | `UAF L8` `dłuższe ujęcie = Extend (+7 s) w SceneBuilder.` | `R003 L51` `Video Extension (Coming Soon)` | [TECH]; wynik: plan klipów 3–30 s | AN3 R-30 | GM-11 |

---

## 7. Kadry bez postaci i przejścia

*(sekcja wymagana przez ECHO-041 i scenariusz S-D7; dziedzina tego pliku = zasada wizualna serialu. Szczegółowy katalog dla całego E01: `A09_katalog_ujec_uzupelniajacych_i_przejsc.md`; warstwa Sceny 1 z osią w ms: `B07_kadry_uzupelniajace_i_przejscia_s1.md`; język kamery, paleta i słownik wizualny: `A02_przewodnik_wizualny.md`.)*

### 7.1 Zasada wizualna (filar realnego wyglądu filmu)

**Źródło zasady (decyzja właściciela, ECHO-041):** `DECYZJE L47` `kadry bez postaci, ktore moga nadac filmowi prawdziwy, realny wyglad`. Odczyt orkiestratora (do sprostowania jednym zdaniem): „kadry bez postaci” = ujęcia otwierające i ustanawiające miejsce, detale i inserty rekwizytów, ujęcia przejściowe, puste kadry po wyjściu postaci, ujęcia tła i atmosfery, przebitki; „przejścia” = rodzaje cięć i łączeń z zasadami użycia i sposobem wykonania z klipów Klinga (`DECYZJE L47`).

**Definicja robocza w tym pliku.** *Kadr bez postaci* = kadr, w którym żadna postać z obsady (sekcja 5.1) nie jest podmiotem ujęcia; anonimowe tło ludzkie (tłum, przechodnie) jest dozwolone w ujęciach ustanawiających. *Detal/insert* = zbliżenie na przedmiot lub ekran. *Przejście* = sposób połączenia dwóch segmentów lub ujęć.

**Rola (cztery funkcje; PROPOZYCJA REZYSERSKA — nazwy funkcji, treść z SC i materiałów):**

| Funkcja | Co robi | Przykład z SC |
|---|---|---|
| oddech | daje widzowi chwilę po scenie dialogowej lub emocjonalnej, bez dopowiadania | `SC L122` `Kamera zostaje na pustym murku przez chwilę.` |
| czas | pokazuje upływ dni i eskalację świata bez dialogu | `SC L597` `Kolejka przed szpitalem w Warszawie -- długa, spokojna.` |
| miejsce | ustanawia lokację (jedną z 24 pozycji z 5.4) i jej stan | `SC L131` `Ogromna sala operacyjna. Na telebimie mapa sieci energetycznej` |
| symbol | niesie znaczenie przedmiotem (żółte rekwizyty, „Adam”, sweter) | `SC L993` `Na krześle w kącie pokoju -- zostawiony sweter.` |

**Rytm (PROPOZYCJA REZYSERSKA; wartości do rozstrzygnięcia w `A09_katalog_ujec_uzupelniajacych_i_przejsc.md`, S-U8; uzasadnienie z materiału rz.4 `ARCH-01 L8`–`L14`).** Liczby poniżej są punktem wyjścia do dyskusji, nie kanonem i nie zmieniają kanonicznych kwestii ani ich czasu:

| Faza E01 | Segmenty | Zasada rytmu | Uzasadnienie |
|---|---|---|---|
| I — kamera blisko ludzi | S1–S6, W-10, P1–P2 | kadr bez postaci jako krótki detal lub insert (ok. 1–3 s w gotowym montażu), nie więcej niż jeden na segment dialogowy; ujęcie ustanawiające na otwarcie lokacji | `ARCH-01 L10` `**SCENY 1–6 (przed eskalacją):** kamera blisko ludzi. Ręczna, lekko oddychająca.` |
| II — eskalacja i dystans | S7–S11, W-7, W-5, P3–P4 | dodatkowo oddechowy kadr bez postaci (ok. 3–6 s) na części granic między scenami (orientacyjnie co druga granica), więcej planów ogólnych | `ARCH-01 L12` `**SCENY 7–11 (eskalacja):** kamera zaczyna się odsuwać. Więcej planów ogólnych. Ludzie stają się mniejsi wobec przestrzeni — korytarze szpitalne, mapa PSE, puste ulice. Ciepło barw opada o kilka stopni.` |
| III — Zero Day i po | S12–S15, W-1 | kadry bez postaci wg SC (mapa świata, puste ulice, kubki, sweter na fotelu; sc. 15 w całości bez postaci z obsady) — bez dokładania ponad SC bez decyzji Q11 | `SC L1162`–`L1181`; `SC L1234`–`L1256` |

**Zasady stosowania (PROPOZYCJA REZYSERSKA):**

1. Każdy kadr bez postaci ma wpisaną funkcję (oddech / czas / miejsce / symbol); kadr „dla ozdoby” nie wchodzi.
2. Nie przerywa kwestii i nie przesuwa kanonicznych kwestii w czasie (zgodność z S-U9 dla Sceny 1).
3. Samodzielny kadr ma co najmniej 3 s, bo klip Klinga 4.0 ma `duration` 3–30 s (GM-01); krótszy insert powstaje przez docięcie dłuższego klipu w montażu.
4. Każdy kadr, którego **treści lub formy** nie ma w tekście SC, ma etykietę **PROPOZYCJA REZYSERSKA** i wymaga akceptacji właściciela (Q11) — także gdy pochodzi z materiału rz.4 (znacznik „rz.4” mówi tylko, skąd kadr wzięto, i nie zastępuje etykiety; runda 3, zarzut E-2-2). Kadry **z SC** są kanonem (SC); w kolumnie „Znacznik” `SC + rz.4` = treść jest w SC, a rz.4 dodaje tylko długość, dźwięk lub sposób kadrowania. Wpisy 7.3 z etykietą PROPOZYCJA REZYSERSKA w kolumnie „Znacznik”: KB-02 i KB-19.
5. Teksty w kadrze (mapy, ekrany, napisy) — w montażu (ZS-07; czytelność tekstu generowanego w obrazie BRAK DANYCH, GM-15).
6. Precyzja czasu kadru = plan i kryterium kontroli (ZS-15), nie gwarancja modelu.

### 7.2 Typy kadrów bez postaci (definicja, funkcja, kiedy używać, wykonanie w Klingu, dźwięk)

Wykonanie w Klingu — kody (każdy ma odnośnik do badania; skuteczność ruchu kamery z promptu w 4.0: **BRAK DANYCH** w zatwierdzonych badaniach — sprawdzić w teście zerowym, jak w `P002`):

| Kod | Znaczenie | Odnośnik |
|---|---|---|
| [T2V] | tekst do wideo (bez Elements postaci): `POST /text-to-video/kling-4.0`, w MCP `text_to_video` | `R003 L48` `text_to_video` |
| [I2V-FF] | obraz do wideo z klatką startową `first_frame` (plansza referencyjna lokacji lub rekwizytu) | `R003 L49` `first_frame` |
| [I2V-FL] | jw. z `last_frame` (tylko 4.0; w 4.0 Flash tylko pierwsza klatka) | `R003 L49` `Only first-frame-to-video generation is supported` |
| [GRAF] | element graficzny lub napis dodany w montażu, nie z modelu | ZS-07, GM-15 |
| [MONTAŻ] | cięcie, przenikanie, most dźwiękowy, czerń — robi montaż, nie model (brak przedłużania klipu w 4.0) | `R003 L51` `Video Extension (Coming Soon)` |

| Typ | Definicja | Funkcja | Kiedy używać | Kiedy nie | Wykonanie w Klingu | Dźwięk |
|---|---|---|---|---|---|---|
| establishing (ustanawiający) | szeroki kadr miejsca na początku sceny lub bloku | miejsce, czas | początek lokacji, po zmianie toru A/B | gdy scena zaczyna się od kwestii w SC (nie dokładać ponad SC bez Q11) | [T2V] bez Elements; opis lokacji z karty `A05_biblia_lokacji.md`; ruch kamery w prompcie | ambient miejsca; bez muzyki, bez napisów (ZS-01, ZS-07) |
| detal / insert | zbliżenie na rekwizyt lub ekran | symbol, czas | gdy przedmiot niesie znaczenie (teczka, sweter, fiolka, SMS) | gdy tekst na ekranie ma być czytelny — wtedy [GRAF] | [T2V] lub [I2V-FF] z planszy rekwizytu; Elements rekwizytu tylko gdy rekwizyt ma stały wygląd w wielu scenach (`A06_biblia_rekwizytow_i_ciaglosci.md`) | dźwięk rekwizytu lub cisza |
| przejściowy | kadr łączący dwa miejsca lub czasy | czas | między blokami czasu lub miejsc | gdy cięcie z SC jest czystsze | [T2V] lub [I2V-FL] gdy ma domknąć ruch | most dźwiękowy z sąsiedniej sceny ([MONTAŻ]) |
| pusty kadr po wyjściu | to samo miejsce po wyjściu postaci | oddech, symbol | koniec sceny, gdy SC mówi, że kamera „zostaje” | gdy po scenie następuje natychmiastowe cięcie w SC | [I2V-FF] z planszy pustego miejsca (jak `P002` K08) | ambient bez kwestii |
| atmosfera / tło | tło świata: ulica, okno, pogoda, tłum bez twarzy | czas, ironia | eskalacja świata poza bohaterami | gdy anonimowy tłum wprowadza błędny sygnał (np. mężczyźni w E02) | [T2V]; statyści: zasada demografii w karcie sceny (AN3 L-12) | ambient (deszcz, miasto) |
| przebitka (cutaway) | krótkie ujęcie spoza bieżącej akcji, dopowiadające sens | symbol, kontrast | gdy SC każe „patrzeć” poza postać (`SC L798` `Aga kładzie dłoń na szybie.` — wzrok → obiekt) | gdy zmienia kolejność kwestii | [I2V-FF] z first_frame; ciągłość z klatką poprzedniego ujęcia | dźwięk sceny trwa (L/J cut w [MONTAŻ]) |

### 7.3 Inwentarz kadrów bez postaci obecnych w SC i materiałach (26 wpisów)

Wpisy dotyczą **całego E01** na poziomie biblii (bez rozpisywania ujęć). Ruch kamery w każdym wpisie to propozycja do promptu: domyślnie kamera nieruchoma albo bardzo powolny ruch; wyjątki są wpisane w opisie (KB-01 zejście, KB-19 odjazd, KB-21 przesuw po mapie); skuteczność ruchu kamery z promptu w 4.0 — BRAK DANYCH (7.2). Pierwsza i ostatnia klatka: kolumna „Wykonanie” podaje [I2V-FF] lub [I2V-FL] tam, gdzie klatka startowa pochodzi z planszy. **Zgodność z rozpiską sekundową:** dla Sceny 1 wpisy KB-01, KB-02 i KB-03 odpowiadają ujęciom rozpiski U1, U3 i U8 (`P002 L146` `Nowy Swiat z gory, zejscie kamery do ulicy`; `P002 L148` `Insert: sweter z dinozaurem`; `P002 L153` `Pusty murek`). Rozpiska sekundowa (`ARS`, tabela 0.4) była czytana bezpośrednio tylko w linii sumy (`ARS L1554`, RK-15); zgodność KB-01..KB-03 z jej ujęciami U1, U3, U8 jest przeniesiona z `P002` (który się na niej opiera), a dla pozostałych segmentów źródłem są SC, `U03`, `U05`, `U06` (bez linia-po-linii kontroli rozpiski); jej błędy rachunkowe opisano w `AN3 R-14`–`R-16`. „Znacznik”: **SC** = jest w tekście scenariusza; **rz.4** = jest w dokumencie produkcyjnym, nie w SC (sam znacznik rz.4 nie czyni kadru kanonem — kadr z samego rz.4 ma dodatkowo etykietę **PROPOZYCJA REZYSERSKA**: KB-02, KB-19); **SC + rz.4** = treść w SC, rz.4 dodaje długość, dźwięk lub sposób kadrowania; **P002** = zrealizowane w pliku Sceny 1. Opis do promptu (EN) = **PROPOZYCJA REZYSERSKA** (G2 — brzmienia EN nie są kanonem); każdy opis jest krótkim zdaniem do uzupełnienia kartą lokacji i zasadami z ZS-01/ZS-07.

| ID | Typ | Opis do promptu (EN, PROPOZYCJA) | Rola | Miejsce użycia (segment, linia) | Wykonanie w Klingu | Dźwięk | Znacznik i źródło |
|---|---|---|---|---|---|---|---|
| KB-01 | establishing | "High aerial establishing shot of Nowy Swiat, Warsaw, warm morning, a yellow tram, mixed crowd of women and men, descending to street level; no main characters" | miejsce, czas (świat działa) | S1, otwarcie; `SC L68` `Warszawa z zewnątrz. Tramwaj na Nowym Świecie. Ludzie z kawami` | [T2V], bez Elements; zejście kamery w prompcie; 9 s (`P002` K01, 0–9000 ms) | tramwaj, kroki, głosy w tle; bez muzyki | SC + rz.4 (ujęcie z góry: `U03 L8` `Ujęcie z góry — tramwaj na Nowym Świecie.`) + P002 |
| KB-02 | detal / insert | "Extreme close-up of a bright yellow knitted sweater with exactly one printed cartoon dinosaur wearing glasses" | symbol (Michał) | S1; `SC L73`; `U05 L24` `1. **Scena 1** — Michał w swetrze. INSERT na nadruk gdy Karolina patrzy z uśmiechem. 2 sekundy.` | wymaga referencji ubioru (to detal postaci bez twarzy): w `P002` K03 przez Elements Michała; 3 s (min. 3 s) | ambient ulicy | rz.4 + P002; **PROPOZYCJA REZYSERSKA** (kadr „insert na nadruk” spoza SC: SC opisuje sweter, `SC L73`, ale nie insert; źródło `U05 L24`); nadruk — RK-10 |
| KB-03 | pusty kadr po wyjściu | "Static wide shot of an empty low stone wall in front of a university building, street life continues" | oddech, symbol (nieobecność) | S1, koniec; `SC L122` `Kamera zostaje na pustym murku przez chwilę.` | [I2V-FF] z planszy pustego murka; 5 s (`P002` K08, 70000–75000 ms) | ambient; tramwaj w tle | SC + P002 |
| KB-04 | detal / insert | "Wide shot of a control-room video wall with a map of the Polish power grid, all green and calm" | miejsce, czas (stan: zielono) | S2; `SC L131` `Ogromna sala operacyjna. Na telebimie mapa sieci energetycznej` | [T2V]; legenda i opisy mapy w [GRAF] (GM-15) | hum elektroniczny, klawisze (`U04 L19`) | SC + rz.4 (`U05 L67` `1. **Scena 2** — INSERT na mapę: zielona, spokojna.`) — stan mapy na osi: RK-37 |
| KB-05 | detal / insert | "Insert: a hard yellow folder lying flat on a desk, half covered by papers; then a closed cabinet door" | symbol (Piotr, Ares IV) | S2; `SC L154` `Na biurku Marty, między raportami i kubkiem: żółta teczka`; `SC L158` `Marta odkłada teczkę do szafy. Zamyka. Bierze raport od Tomka.` | [T2V]/[I2V-FF]; ok. 2 s wg `U05 L12` — min. 3 s w Klingu, docięcie w montażu | hum PSE | SC + rz.4 (długość: `U05 L12` `2 sekundy`) |
| KB-06 | detal / insert | "Close-up of a ceiling-corner security camera whose lens is covered by a small yellow sticky note" | symbol (plan Very) | S3; `SC L276` `z kieszeni żółtą karteczkę samoprzylepną. Zasłania obiektyw.` | [T2V]; gest Very poza kadrem (kadr bez postaci) | szum wentylacji, szelest karteczki (`U04 L60`) | SC + rz.4 (`U05 L47` `1. **Scena 3** — Vera przylepia karteczkę.`) |
| KB-07 | pusty kadr po wyjściu | "Static shot of an empty laminar-flow cabinet, a vial on the bench, nobody in frame, cold fluorescent light" | oddech, symbol (czyn dokonany) | S3, koniec; `SC L286` `Wychodzi. Kamera zostaje przy pustym boksie.`; `SC L287` `Fiolka jest pusta.` | [I2V-FF] z planszy boksu; nieruchoma kamera (`U03 L38`: kilka sekund dłużej niż potrzeba) | tylko wentylacja (`SC L263`) | SC + rz.4 |
| KB-08 | atmosfera / tło | "Long calm queue outside a Warsaw hospital entrance and outside a pharmacy, people seen from a distance, no faces in focus" | czas (eskalacja bez dialogu) | W-7; `SC L597` `Kolejka przed szpitalem w Warszawie -- długa, spokojna.`; `SC L598` `Kolejka przed apteką -- wykupione maseczki.` | [T2V]; statyści: kobiety i mężczyźni (przed Zero Day) — AN3 L-12 | gwar, kroki; bez muzyki, bez napisów | SC |
| KB-09 | atmosfera / tło | "Night view of Oslo through a window, calm, rain, distant tram sound; nobody in frame" | czas, ironia („nieświadome”) | S8, koniec; `SC L831` `Podchodzi do okna. Oslo w nocy -- spokojne, nieświadome.` | [T2V]/[I2V-FF] z planszy okna | deszcz, odległy tramwaj (`U04 L80`) | SC + rz.4 |
| KB-10 | detal / insert | "Close-up of printed pages on a desk, an author title page, small footnote; a hand pushes them under other papers (hand only)" | symbol (kradzież badań) | S8; `SC L817` `Obok laptopa: wydruki. Na wierzchu strona tytułowa publikacji.`; `SC L819` | [GRAF] dla tekstu przypisu (TE-13, RK-31); tło papierów [T2V] | cisza (`U04 L30`) | SC |
| KB-11 | detal / insert | "Close-up of a blackboard with equations written in two different colours of handwriting, no people" | symbol (współpraca) | P2, otwarcie; `SC L438` `Na tablicy: wspólny schemat. Dwa kolory pisma -- jej i jego.` | [T2V]; równania jako faktura, bez czytelnego tekstu (GM-15) | delikatny temat przeszłości lub cisza (`U04 L25`) | SC + rz.4 (`U03 L72` `**Kadr otwierający:** Tablice z równaniami — DWA kolory pisma obok siebie.`) |
| KB-12 | detal / insert | "Small kitchen, a child's high chair by the wall, empty, sounds of play from another room" | symbol (rodzina) | P2, kuchnia; `SC L498` `Przy ścianie -- krzesełko dziecięce. Puste -- dziecko gdzieś` | [T2V]/[I2V-FF] z planszy kuchni (jedna kuchnia w P2 i P3 — `A05_biblia_lokacji.md`) | odgłosy zabawy za kadrem | SC |
| KB-13 | detal / insert | "Close-up of a scientific journal page on a laptop screen, title and a small footnote, nobody in frame" | symbol (przyczyna) | P4; `SC L876` `Strona czasopisma naukowego. Artykuł.`; `SC L889` | [GRAF] dla tytułu i przypisu (TE-17, TE-18) | cisza; muzyka P4 wg `U04 L32` — decyzja Q2 | SC + rz.4 (`U05 L80` `1. **Scena P4** — Vera czyta artykuł. INSERT na tytuł. INSERT na przypis z jej nazwiskiem.`) |
| KB-14 | atmosfera / tło | "Oslo in the rain seen through a window, empty frame, steady rain on glass" | czas, oddech | P4; `SC L898` `Oslo w deszczu. Jej miasto. Jej okno.` | [T2V]/[I2V-FF] | deszcz | SC |
| KB-15 | detal / insert | "Close-up of a hand-written single word on a whiteboard, camera stays on it" | symbol („Adam”) | P4, koniec; `SC L919` `Jedno słowo: "Adam."`; `SC L921` `Kamera zostaje na tym słowie.` | [GRAF] dla słowa (czytelność tekstu BRAK DANYCH, GM-15) | cisza, klawiatura (`U04 L32`) | SC |
| KB-16 | detal / insert | "A television screen showing a news programme, a lower-third bar; nobody in frame" | czas | S9, otwarcie; `SC L930` `Telewizor. Program informacyjny.`; `SC L932` | [T2V]; pasek TE-20 w [GRAF] | telewizor jako dźwięk diegetyczny (`U04 L33`) | SC |
| KB-17 | przebitka / atmosfera | "A sweater on a chair in a corner; then window and sky, quiet ordinary street sounds" | oddech, symbol | S10; `SC L993`; `SC L1002` `Sweter w ramionach. Okno. Niebo. Cisza.` | [I2V-FF] z planszy pokoju; krzesło czy fotel — RK-14 | dźwięki zewnętrzne przez okno (`U04 L64`) | SC + rz.4 |
| KB-18 | pusty kadr po wyjściu | "Wide shot of a control room with two empty workstations, abandoned coffee cups, the grid map in the background" | czas, miejsce | S11; `SC L1009` `Sala normalnie wyglądająca -- ale dwa miejsca są puste.` | [T2V]/[I2V-FF] z planszy sali; liczba pustych miejsc — RK-36 | głośniejszy hum sali bez głosów (`U04 L74`) | SC + rz.4 |
| KB-19 | detal / insert | "Close-up of a bedside heart monitor with a steady sine trace, then the camera slowly pulls back" | czas, puls | S12, otwarcie (`U03 L96` `**Kadr otwierający:** Monitor EKG — ZBLIŻENIE na sinusoidę.`); śmierć niepokazana (ZS-10) | [T2V]; linia EKG jako [GRAF], jeśli wygenerowana nieczytelnie | beep jako metronom sceny (`U04 L66`); moment milknięcia w montażu | rz.4; **PROPOZYCJA REZYSERSKA** (zbliżenie na monitor jako otwarcie sc. 12 spoza SC: `SC L1052` mówi tylko `Monitor.`; źródło `U03 L96`) |
| KB-20 | detal / insert | "Insert of two clasped hands on a hospital blanket, no faces" | symbol (jedyna czułość) | S12; `SC L1102` `Aga ściska jego rękę. Mocniej niż trzeba.` | detal postaci (dłonie, bez twarzy) — referencja dłoni/rękawa z arkusza postaci (`A03_biblia_postaci.md`) | beep | SC + rz.4 (`U05 L90` `1. **Scena 12** — gdy Paweł mówi "zostań." Aga ściska mocniej. INSERT na splecione dłonie — 4 sekundy.`) |
| KB-21 | detal / insert | "World map with orange points spreading from the edges toward the centre, the camera drifts across it" | czas (rozmiar katastrofy) | S14; `SC L1162` `Mapa świata. Pomarańczowa -- od brzegów ku środkowi.` | wybór: [GRAF] albo [T2V] — decyzja produktowa; punkty i opisy w [GRAF] (GM-15) | syreny przy punktach (`SC L1163`) | SC + rz.4 (`ARCH-08 L105` `**Czas na ekranie:** Ok. 5 sekund. Kamera przesuwa się po mapie — nie stoi w miejscu.`) |
| KB-22 | atmosfera / tło | "Empty Warsaw street in the morning, one dog without a leash" | czas, kontrast z S1 | S14; `SC L1169` `Ulice Warszawy. Puste. Jeden pies bez smyczy.` | [T2V]; powiązanie z S1 (ta sama ulica) = PROPOZYCJA, patrz KP-06 | cisza, odległe syreny | SC |
| KB-23 | detal / insert | "A yellow sweater with a dinosaur lying on an armchair, a dark room" | symbol (Michał) | S14; `SC L1180` `Sweter Michała leży na fotelu.`; `SC L1181` `Żółty. Z dinozaurem.` | [I2V-FF] z planszy swetra na fotelu; nadruk i mebel — RK-10, RK-14 | cisza | SC + rz.4 (`U05 L26` `3. **Scena 14** — Zero Day. Sweter na fotelu w tle za Karoliną. INSERT.`) |
| KB-24 | establishing | "Very wide aerial shot of a dark-hulled LNG carrier at dawn on a flat steel-grey sea, mist, four white tank domes, a wake behind; nobody visible on deck" | miejsce, groza | S15, ujęcie 1; `SC L1234` `UJĘCIE 1 -- bardzo szeroko, z góry.`; `SC L1238` `leniwy kilwater. Żadnej sylwetki na pokładzie. A jednak idzie kursem.` | [T2V]; bez Elements; filtry treści BRAK DANYCH (GM-16) | morze, wiatr, metal; bez muzyki (`SC L1230`) | SC |
| KB-25 | detal / insert | "Close-up of a ship's bridge console: a red lamp blinking, a navigation screen with course set, nobody present" | symbol (maszyna płynie dalej) | S15, ujęcie 3; `SC L1247` `UJĘCIE 3 -- detal mostka.`; `SC L1251` | [T2V]; nazwa portu w [GRAF] (TE-24, GM-15) | metal trzeszczy, lampka | SC |
| KB-26 | przebitka / pusty | "Wide shot: the carrier leaves the frame, its bow aimed at a thin line of land with distant terminal lights; gulls, water" | czas, groza | S15, ujęcie 4; `SC L1253` `UJĘCIE 4 -- powrót na szeroko.`; `SC L1256` `do portu. Mewy. Woda. Trzeszczący metal.` | [T2V]; domknięcie → `Czarny ekran.` (`SC L1260`) | mewy, woda, metal; cisza „dłuższa niż wygodnie” (`SC L1258`) | SC |

*Wpis pominięty celowo:* ujęcie 2 sc. 15 (pokład z martwymi mężczyznami, `SC L1241`–`L1245`) ma postacie (ciała), więc nie jest „kadrem bez postaci”; filtry treści dla niego — BRAK DANYCH (GM-16, AN3 L-17).

### 7.4 Kadry spoza scenariusza — PROPOZYCJE REZYSERSKIE (8)

Wszystkie poniższe są **PROPOZYCJĄ REZYSERSKĄ**: nie ma ich w SC, nie wprowadzają nowych faktów (nazw, dat, zdarzeń), nie zmieniają kwestii ani czasu kwestii. Wchodzą do produkcji tylko po decyzji Q11 (A09 i B07 doprecyzują ilość, miejsce w osi i czas).

| ID | Typ | Opis do promptu (EN, PROPOZYCJA) | Rola | Miejsce użycia (między, linie SC) | Wykonanie w Klingu | Dźwięk | Wpływ na czas | Uzasadnienie |
|---|---|---|---|---|---|---|---|---|
| KP-01 | establishing | "Exterior of a large Warsaw hospital on an ordinary morning, ordinary traffic and people far away, no main characters" | miejsce, czas | przed S4, `SC L293`; po S3 | [T2V] | ruch uliczny, nie hałas wnętrza; bez muzyki | ok. +3 s (S4 = 3 min wg SC) | SC mówi `SC L296` `Szpital działa pełną parą. Hałas, ruch.` — kadr ustanawia ten stan |
| KP-02 | atmosfera / tło | "Warsaw street at dusk, lit windows, few people, calm" | czas (przed salonem Marty) | przed S9, `SC L927` | [T2V] | ciszej niż w S1, odległy ruch | ok. +3 s | ton: `SC L935` `To nie jest już zwykły wieczór.` (wejście w scenę po T-5→T-6) |
| KP-03 | pusty kadr po wyjściu | "Empty hospital intensive-care corridor at night, a monitor beep fading to silence; no bed, no patient visible" | oddech, most do „po” | po S12, przed S13, `SC L1103`→`SC L1107` | [T2V] lub [I2V-FF]; monitor milknie w [MONTAŻ] | beep milknie jako most (ZS-10; `U06 L148`) | ok. +2–3 s | zgodne z regułą niepokazywania śmierci Pawła (ZS-10) |
| KP-04 | atmosfera / tło | "First grey dawn light in a hospital corridor window, empty chairs along the wall" | czas | początek S13, `SC L1107` | [T2V] | kroki i cisza (`U04 L37`) | ok. +3 s | S13 dzieje się o świcie (`SC L1107` `INT. SZPITAL BIELAŃSKI, KORYTARZ -- ŚWIT`) |
| KP-05 | detal / insert | "Close-up of an empty workstation with a coffee mug and a keyboard, a dark screen" | czas, nieobecność | S11, po `SC L1012`–`L1015` (nieobecność Tomka), przed `SC L1032` | [T2V]; stanowisko z karty sali (`A05_biblia_lokacji.md`) | hum sali | ok. +2–3 s | wzmacnia `SC L1012` `Gdzie jest Tomek?` bez nowych faktów |
| KP-06 | przebitka (rym obrazu) | "The same Nowy Swiat street from the opening, now empty, morning light, no tram" | symbol (rym z S1) | S14, ujęcie „Ulice Warszawy” `SC L1169` (określa miejsce jako Nowy Świat) | [T2V] z tą samą planszą lokacji co KB-01 (`A05_biblia_lokacji.md`) | cisza, odległe syreny | 0 s (zastępuje KB-22 tym samym czasem) | SC nie wskazuje miejsca pustych ulic; rym z S1 to decyzja reżyserska |
| KP-07 | pusty kadr po wyjściu | "The low stone wall from the opening, now with no one and no street life" | symbol (rym z S1) | S14, krótki wtręt w montażu lub S15 przed ujęciem 1 | [I2V-FF] z planszy REF_MUREK_PUSTY (jak `P002` K08) | cisza | ok. +3 s (S14 ma stały rytm — decyzja AN3 Q12) | rym z `SC L122`; wymaga decyzji o rytmie Zero Day |
| KP-08 | detal / insert | "Close-up of a wall clock or a monitor clock reading a time in the early morning" | czas | S13, po `SC L1119` `O czwartej czternaście.` (nie przed — nie zdradzać odpowiedzi na `SC L1116` `O której?`) | [T2V]; godzina w [GRAF] (GM-15) | cisza | ok. +2 s | godzina jest w SC (`SC L1119`); kadr tylko ją pokazuje — ryzyko: nadmierne dopowiedzenie |

### 7.5 Przejścia — słownik i mapa użycia w kolejności SC

**Słownik typów** (opisy i użycia z `U06` rz.4; nie mamy dla E01 ani jednego typu spoza `U06` oprócz oznaczonych PROPOZYCJA):

| Typ | Definicja | Użycie w E01 (U06) | Wykonanie w Klingu | Dźwięk |
|---|---|---|---|---|
| CUT TO | twarde cięcie bez ceremonii | większość par (`U06 L42` `Cięcie twarde — bez ceremonii.`) | [MONTAŻ]: dwa osobne klipy | dźwięk ostatni klipu urywa się lub schodzi (ambient wg `U04`) |
| SMASH CUT | cięcie ze skokiem temperatury barwnej | ciepło → zimno (`U06 L26` `Bez przejścia, bez muzyki — natychmiastowe cięcie w inny świat.`) | [MONTAŻ]; kontrast palet z `A02_przewodnik_wizualny.md` | cisza lub kontrast ambientów |
| DISSOLVE | powolne przenikanie | wejścia w bloki przeszłości w `U06` (`U06 L33` `Oslo (Vera 64 lata) → Korytarz UW (Vera 24 lata). Powolne przenikanie.`) | [MONTAŻ]; ciągłość klatek niepotrzebna; opcjonalnie [I2V-FL] dla „zgodnego kształtu” | wygaszanie jednego ambientu i wejście drugiego |
| HARD CUT TO BLACK | natychmiastowe cięcie w czerń | koniec odcinka (`U06 L168` `Nie fade out. Nie dissolve. Natychmiastowe cięcie w czerń.`) | [MONTAŻ] | `U06 L169` `Cisza po cięciu: minimum 3 sekundy przed napisami.` |
| most dźwiękowy (sound bridge, L/J cut) | dźwięk następnej sceny wchodzi przed obrazem lub ostatni dźwięk poprzedniej trwa po cięciu | S11→S12, S12→S13 (`U06 L141` `Rozważyć SOUND BRIDGE`) | [MONTAŻ]; dźwięk dokładany, bo model nie gwarantuje momentu zdarzenia (ZS-15, GM-10) | beep EKG |
| match cut | cięcie łączące podobne kształty lub ruch | brak w `U06` — **PROPOZYCJA REZYSERSKA** (np. rym KP-06/KP-07 z S1) | [I2V-FL]: `last_frame` klipu A i `first_frame` klipu B dobrane do siebie (`R003 L49`) | zależnie od pary |

**Zasada ogólna (rz.4):** `U06 L8` `Przejścia w E01 są celowe i znaczące. Nie wszystkie są neutralne CUT TO. Każde przejście między teraźniejszością a przeszłością musi być odczuwalne — nie jako efekt specjalny, ale jako zmiana "temperatury" obrazu.` — **ROZBIEŻNOŚĆ RP-01**: `ARCH-01 L28` mówi, że przejścia w przeszłość „są cięciami”, a `U06` używa przenikań.

**Mapa użycia w kolejności SC (23 przejścia: 22 pary i zakończenie).** „Typ wg U06” = rząd 4, w starej kolejności (AN3 R-02); wpisy bez U06 = BRAK DANYCH w U06. Typ w kolumnie „Typ — PROPOZYCJA” jest **PROPOZYCJĄ REZYSERSKĄ**, gdy U06 nie opisuje pary albo koliduje z SC. Pełna lista z czasami w ms: `A09_katalog_ujec_uzupelniajacych_i_przejsc.md`.

| ID | Para (SC) | Typ wg U06 | Typ — PROPOZYCJA REZYSERSKA / status | Uzasadnienie (źródło) | Wykonanie w Klingu | Dźwięk |
|---|---|---|---|---|---|---|
| PR-01 | S1 → S2 | `U06 L17` `CUT TO` | CUT TO (bez zmian) | `U06 L20` `Ten sam ranek, inne życie.` | [MONTAŻ]: KB-03 (pusty murek) → pierwszy kadr sali | ambient ulicy → hum sali PSE (`U04 L19`) |
| PR-02 | S2 → P1 | BRAK DANYCH w U06 (U06 ma S2 → S3) | CUT z napisem `SC L186`; alternatywa DISSOLVE (decyzja Q5, Q12) | skok epoki: `ARCH-01 L28` `Widz ma poczuć skok.` | [MONTAŻ]; napis w montażu (TE-01) | hum PSE → delikatny temat przeszłości (`U04 L21`) |
| PR-03 | P1 → S3 | BRAK DANYCH w U06 (U06 ma P1 → S4) | SMASH CUT | `SC L261` `Pierwsze zimne ujęcie w całym odcinku.`; `SC L262` `Barwa spada natychmiast: fluorescencja, czerń, biel.` | [MONTAŻ]; kontrast palet (A02) | muzyka P1 urwana → szum wentylacji (`SC L263`) |
| PR-04 | S3 → S4 | BRAK DANYCH w U06 (U06 ma S3 → P1) | CUT TO z kontrastem dźwięku | `SC L286` `Wychodzi. Kamera zostaje przy pustym boksie.` → `SC L296` `Szpital działa pełną parą. Hałas, ruch.` | [MONTAŻ]: KB-07 → KP-01 lub pierwszy kadr korytarza | cisza wentylacji → ruch szpitala (`U04 L22`) |
| PR-05 | S4 → W-10 | `U06 L47` `CUT TO` | CUT TO (bez zmian) | `U06 L49` `Zmiana formatu obrazu sygnalizuje wstawkę.` | [MONTAŻ]; format wstawki — AN3 R-67 (decyzja produktowa) | jingle diegetyczny (`U04 L23`) |
| PR-06 | W-10 → S5 | `U06 L54` `CUT TO` | CUT TO (bez zmian) | `U06 L55` `Studio TV → PSE.` | [MONTAŻ] | jingle → hum PSE |
| PR-07 | S5 → P2 | `U06 L60` `DISSOLVE` | DISSOLVE z napisem `SC L431` (U06 podaje stary napis — RK-06) | `U06 L62` `Uzasadnienie narracyjne: Marta myśli o bliskiej osobie → cięcie do Very która też kiedyś miała bliską osobę.` | [MONTAŻ]; opcja match cut | cisza po rozmowie (3 s, `U04 L24`) → temat przeszłości (`U04 L25`) |
| PR-08 | P2 → S6 | `U06 L68` `CUT TO` | CUT TO (bez zmian) | `U06 L70` `Powrót do teraźniejszości. Twarde cięcie.` | [MONTAŻ] | zabawa dziecka → telefon wewnętrzny (`SC L540`) |
| PR-09 | S6 → W-7 | `U06 L75` `CUT TO` | CUT TO (bez zmian) | `U06 L77` `Eskalacja medialna odpowiada informacji którą właśnie dostała Marta.` | [MONTAŻ] | cisza 3 s po „Pewnie zakłócenia.” (`U04 L62`) → nakładające się kanały (`U04 L27`) |
| PR-10 | W-7 → P3 | `U06 L82` `DISSOLVE` | DISSOLVE z napisem `SC L615` (U06: stary napis — RK-06) | `U06 L84` `Uzasadnienie: Karolina czeka na wiadomość od kogoś bliskiego. Vera właśnie straciła kogoś bliskiego. Emocjonalne lustro.` | [MONTAŻ] | chaos kanałów → delikatny temat (`U04 L28`) |
| PR-11 | P3 → S7 | `U06 L90` `CUT TO` | CUT TO (bez zmian) | `U06 L92` `Powrót do teraźniejszości. Twarde cięcie.` | [MONTAŻ] | muzyka wygasa po odkryciu (`U04 L28`) → głosy wideokonferencji (`U04 L29`) |
| PR-12 | S7 → S8 | `U06 L97` `CUT TO` | CUT TO (bez zmian); cofnięcie osi T (RK-21) | `U06 L99` `Równoległy moment skupienia: obie kobiety patrzą na coś niepokojącego.` | [MONTAŻ]; przebitka wzroku (dłoń Agi na szybie, `SC L798`) | cisza (`U04 L30`) |
| PR-13 | S8 → W-5 | `U06 L104` `CUT TO` | CUT TO (bez zmian) | `U06 L105` `Vera odkłada telefon → studio epidemiolog.` | [MONTAŻ] | cisza → studio bez jingle (`U04 L31`) |
| PR-14 | W-5 → P4 | `U06 L110` `DISSOLVE` | DISSOLVE (napis w U06 zgodny z `SC L869`) | `U06 L112` `Uzasadnienie: słyszymy skutek → widzimy przyczynę.` | [MONTAŻ] | cisza studia → wejście muzyki, gdy Vera rozumie (`U04 L32`) |
| PR-15 | P4 → S9 | `U06 L118` `CUT TO` | CUT TO (bez zmian); cofnięcie osi T (RK-21) | `U06 L120` `Najtwardsze cięcie w odcinku. Dwa światy które nie wiedzą o sobie nawzajem.` | [MONTAŻ]: KB-15 → KB-16 lub salon | cisza laboratorium → telewizor (`U04 L33`) |
| PR-16 | S9 → S10 | `U06 L125` `CUT TO` | CUT TO (bez zmian); `U06 L126` ma „Karolina przy stole” — SC: `SC L934` `Marta na kanapie. Karolina na fotelu z telefonem.` | `U06 L127` `Czas mógł minąć. Lub to ta sama noc.` | [MONTAŻ] | telewizor → odgłosy zza okna (`U04 L34`) |
| PR-17 | S10 → S11 | `U06 L132` `CUT TO` | CUT TO (bez zmian) | `U06 L134` `Dwie różne konsekwencje tej samej katastrofy.` | [MONTAŻ]: KB-17 → KB-18 | cisza → hum sali (`U04 L74`) |
| PR-18 | S11 → S12 | `U06 L139` `CUT TO` | CUT TO + most dźwiękowy (beep EKG) | `U06 L141` `Rozważyć SOUND BRIDGE` | [MONTAŻ]: audio dokładane przed obrazem | beep wchodzi w S11 (`U06 L141`) |
| PR-19 | S12 → S13 | `U06 L146` `CUT TO` | CUT TO + most dźwiękowy (monitor milknie); możliwy KP-03 | `U06 L148` `Cięcie w chwilę po śmierci Pawła — nie pokazujemy śmierci. Przechodzimy do po.` | [MONTAŻ] | `U04 L66` `Nie przyspiesza przy śmierci — milknie.` |
| PR-20 | S13 → W-1 | `U06 L153` `CUT TO` | CUT TO (bez zmian) | `U06 L154` `Aga idzie korytarzem → studio TV, premier.` | [MONTAŻ] | kroki → studio bez muzyki (`U04 L38`) |
| PR-21 | W-1 → S14 | `U06 L159` `CUT TO` | CUT TO (bez zmian) | `U06 L161` `Ostatnie cięcie do Zero Day. Bez efektów. Twarde.` | [MONTAŻ] | cisza po słowach premiera (`U04 L38`) → start smyczków przy mapie (`U04 L39`) |
| PR-22 | S14 → S15 | BRAK DANYCH w U06 (U06 kończy odcinek po S14) | HARD CUT TO BLACK → cięcie na ujęcie 1 sc. 15 (KB-24); typ i czas czerni — decyzja [PRODUKT] (AN3 R-27) | `SC L1224` `Czarny ekran.` kończy S14; `SC L1230` `Reżysersko: bez muzyki. Tylko morze, wiatr i metal. Pokazujemy mało` | [MONTAŻ] | muzyka S14 wygasła → morze, wiatr (`SC L1230`) |
| PR-23 | S15 → koniec | `U06 L166` `HARD CUT TO BLACK` (przypisane do końca S14) | HARD CUT TO BLACK po ujęciu 4 (`SC L1260` `Czarny ekran.`); ROZBIEŻNOŚĆ: U06 nie zna sc. 15 (AN3 R-01, R-27) | `U06 L168` `Nie fade out. Nie dissolve. Natychmiastowe cięcie w czerń.` | [MONTAŻ] | `U06 L169` `Cisza po cięciu: minimum 3 sekundy przed napisami.` |

*Czarny ekran wewnątrz S14.* `SC L1211` `Czarny ekran.` stoi między ujęciem Karoliny a ujęciem Agi (fałszywe zakończenie — AN1 N-03); typ i czas tej czerni — decyzja [PRODUKT] (AN3 R-27, Q13).

### 7.6 Odnośniki dziedzinowe

- `A02_przewodnik_wizualny.md` — paleta, język kamery, słownik przejść i mapa użycia (wartości kolorów i obiektywów = PROPOZYCJA REZYSERSKA).
- `A09_katalog_ujec_uzupelniajacych_i_przejsc.md` — pełna typologia, kadry dla każdej lokacji, sekwencje przejść dla każdej pary, rytm na minutę (PROPOZYCJA).
- `B07_kadry_uzupelniajace_i_przejscia_s1.md` — warstwa kadrów uzupełniających Sceny 1 z miejscem w osi czasu (zgodność z KB-01, KB-02, KB-03 i `P002`).
- Pytanie do właściciela o zakres kadrów spoza SC: Q11; o rodzaj przejść i czerń: Q12.

---

## 8. Jak używać pakietu (mapa plików A–E)

### 8.1 Zasady użycia

1. **Źródłem treści jest scenariusz.** Pakiet go nie zastępuje; każdy plik pakietu ma cytować SC i oznaczać elementy „od reżysera” jako PROPOZYCJA REZYSERSKA. Hierarchia: SC → ECHO → raporty i dokumenty produkcyjne (0.2).
2. **Wsad dla modelu to małe, ścisłe pliki.** Do Klinga nie wklejamy plików pakietu w całości; do zadania idzie prompt (`A08_przewodnik_promptow_kling.md` plus plik sceny B), referencje i Elements (`A03_biblia_postaci.md`, `B06_paczka_referencji_s1.md`) i zasady stałe (sekcja 2). Źródło zasady: `ZPL2 L10` `wsad dla modelu = male, scisle pliki`.
3. **Poza modelem zostają:** muzyka, polski głos, napisy i przejścia (cięcia, przenikania, czerń, mosty dźwiękowe). Źródło: `ZPL2 L13` `co zostaje poza modelem (muzyka, polski glos, napisy, przejscia)`; ograniczenia narzędzia: GM-10, GM-11, ZS-01, ZS-07.
4. **Kolejność czytania:** (a) reżyser / nowy agent: `A01_biblia_serialu.md` (ten plik) → `E01_rejestr_decyzji_kanonicznych.md` → `A02_przewodnik_wizualny.md` → `A03_biblia_postaci.md` → `A05_biblia_lokacji.md`, `A06_biblia_rekwizytow_i_ciaglosci.md`, `A07_biblia_dzwieku.md` → `A08_przewodnik_promptow_kling.md` → `A09_katalog_ujec_uzupelniajacych_i_przejsc.md`; (b) operator Sceny 1: pliki B plus `P002`; (c) montażysta: `D01_plan_montazu.md`, `D02_plan_polskiego_glosu.md`, `D03_muzyka_grade_eksport.md`; (d) kontrola i koszty: `C01`–`C04`; (e) decyzje i wersje: `E01_rejestr_decyzji_kanonicznych.md`, `E02_wersje_i_plan_testow.md`.
5. **Sprzeczność pliku pakietu z SC lub ECHO** → obowiązuje SC lub ECHO wg hierarchii; sprzeczność zgłasza się w rejestrze decyzji; plików wejściowych (scenariusze, archiwum, wgrane dokumenty) nie poprawiamy (G1, G6).
6. **Oznaczenia:** legenda z 0.1 obowiązuje w całym pakiecie; „PROPOZYCJA REZYSERSKA” nigdy nie staje się kanonem bez decyzji właściciela.
7. **Odświeżanie:** plik opiera się na SC o SHA-256 `b0264c95…4340` (sekcja 0.4). Po poprawkach scenariusza (osobny temat po decyzjach kanonicznych, ECHO-020) trzeba go odświeżyć; analogiczna zasada jest zapisana dla audiobooka: `DECYZJE L20` `po decyzjach kanonicznych trzeba go odswiezyc` (ECHO-014).
8. **Precyzja:** czasy w ms w plikach B to plan i kryterium kontroli, nie gwarancja generatora (ZS-15).

### 8.2 Mapa plików pakietu

Ścieżki docelowe zleceń `ZERO-PAKIET-001..024` (`autobot/zlecenia/`) leżą w `docs/produkcja/pakiet/`. Stan = wynik `ls docs/produkcja/pakiet/` z 2026-11-28 15:11, wpisany do sekcji 0.5 (runda 3, zarzut E-2-4); status „w toku” pochodzi z `autobot/REJESTR_TEMATOW.md` (odczyt) — plik w katalogu nie znaczy „zatwierdzony”. Kolumna „Kto tworzy”: workflow = Operator (Sonnet 5.5, ECHO-042); obrazy i głosy — poza tym pakietem (nic nie jest generowane, ECHO-040 pkt 6).

| Kat. | Plik (ścieżka docelowa) | Zawartość (jedno zdanie) | Zlecenie | Stan | Kto tworzy | Kiedy czytać |
|---|---|---|---|---|---|---|
| A | `A01_biblia_serialu.md` | logline, zasady stałe, struktura E01–E02, oś czasu, rejestr faktów, rozbieżności, kadry bez postaci i przejścia, mapa pakietu | ZERO-PAKIET-001 | **ten plik** (do kontroli) | workflow | na start |
| A | `A02_przewodnik_wizualny.md` | paleta, światło, język kamery, słownik przejść, zasady spójności obrazu | ZERO-PAKIET-002 | **istnieje w katalogu** (ls 2026-11-28 15:11); temat „w toku”, niezatwierdzony — w tym pliku niewykorzystany; spójność do sprawdzenia po zatwierdzeniu (sekcja 10) | workflow | przed każdym promptem obrazu |
| A | `A03_biblia_postaci.md` | arkusze postaci i epok z referencjami (opisy, nie obrazy) | ZERO-PAKIET-003 | **istnieje w katalogu** (ls 2026-11-28 15:11); temat „w toku”, niezatwierdzony — w tym pliku niewykorzystany; spójność do sprawdzenia po zatwierdzeniu (sekcja 10) | workflow; obrazy referencyjne — właściciel / zewnętrzne narzędzie | przed Elements |
| A | `A04_arkusze_glosow.md` | arkusze głosów EN i PL dla postaci mówiących | ZERO-PAKIET-004 | brak (w kolejce) | workflow | przed głosami |
| A | `A05_biblia_lokacji.md` | karty lokacji ze stałymi elementami | ZERO-PAKIET-005 | brak (w kolejce) | workflow | przed promptami lokacji |
| A | `A06_biblia_rekwizytow_i_ciaglosci.md` | rekwizyty, teksty ekranowe, stany per scena | ZERO-PAKIET-006 | brak (w kolejce) | workflow | przed insertami |
| A | `A07_biblia_dzwieku.md` | reguła audio, mapa muzyczna, sound design | ZERO-PAKIET-007 | brak (w kolejce) | workflow | przed sekcją audio promptu |
| A | `A08_przewodnik_promptow_kling.md` | szablon promptu, zasady stałe do wklejenia, drogi MCP/API | ZERO-PAKIET-008 | brak (w kolejce) | workflow | przy pisaniu promptu |
| A | `A09_katalog_ujec_uzupelniajacych_i_przejsc.md` | typologia kadrów bez postaci i przejść, rytm na minutę | ZERO-PAKIET-023 | brak (w kolejce) | workflow | przy planowaniu montażu E01 |
| B | `B01_karta_sceny1.md` | karta Sceny 1 (cel, beaty, wejście i wyjście) | ZERO-PAKIET-012 | brak (w kolejce) | workflow | start Sceny 1 |
| B | `docs/produkcja/ZERO-PROD-002-scena1-kling/scena1_kling.md` (pozycje 10 i 14 z ECHO-040 pkt 2: lista ujęć z osią ms i prompty) | plik produkcyjny Sceny 1 dla Klinga | ZERO-PROD-002 | **istnieje** (SHA-256 w 0.4) | workflow (zakończony) | operacyjnie przy Scenie 1 |
| B | `B03_arkusz_dialogow_s1.md` | kwestie PL z SC ↔ EN (PROPOZYCJA) Sceny 1 | ZERO-PAKIET-013 | brak (w kolejce) | workflow | przed dialogami |
| B | `B04_arkusz_sygnalow_dzwiekowych_s1.md` | sygnały dźwiękowe Sceny 1 (start, koniec, poziom) | ZERO-PAKIET-014 | brak (w kolejce) | workflow | przed montażem dźwięku |
| B | `B05_arkusz_ciaglosci_s1.md` | ciągłość klatek i rekwizytów Sceny 1 | ZERO-PAKIET-015 | brak (w kolejce) | workflow | przy łączeniu klipów |
| B | `B06_paczka_referencji_s1.md` | lista referencji i planszy do Elements Sceny 1 | ZERO-PAKIET-016 | brak (w kolejce) | workflow; obrazy — poza pakietem | przed generowaniem |
| B | `B07_kadry_uzupelniajace_i_przejscia_s1.md` | kadry uzupełniające i przejścia Sceny 1 z osią ms | ZERO-PAKIET-024 | brak (w kolejce) | workflow | przy montażu Sceny 1 |
| B | `docs/produkcja/ZERO-PROD-002-scena1-kling/scena1_kling_tekst.txt` (ścieżka docelowa wg zlecenia ZERO-PROD-003, zlecenie `autobot/zlecenia/ZERO-PROD-003-scena1-kling-tekst.md` (hash w 0.4), L7: „utworz `docs/produkcja/ZERO-PROD-002-scena1-kling/scena1_kling_tekst.txt`”; wersja tekstowa Sceny 1 do załączenia) | ten sam plik jako zwykły tekst | ZERO-PROD-003 | brak (ls 2026-11-28 15:11: pliku nie ma; po fali 2) | workflow | gdy narzędzie nie przyjmuje API |
| C | `C01_tracker_produkcji.md` | status klipów, prób, kosztów | ZERO-PAKIET-017 | brak (w kolejce) | workflow | w trakcie produkcji |
| C | `C02_kontrola_jakosci.md` | checklisty i procedura weryfikacji klipu | ZERO-PAKIET-018 | brak (w kolejce) | workflow | po każdym klipie |
| C | `C03_budzet_i_koszty.md` | budżet i koszty prób | ZERO-PAKIET-009 | brak (w kolejce) | workflow | przed decyzją o skali |
| C | `C04_prawa_i_licencje.md` | prawa, licencje, marki | ZERO-PAKIET-010 | brak (w kolejce) | workflow | przed publikacją |
| D | `D01_plan_montazu.md` | plan montażu E01 | ZERO-PAKIET-019 | brak (w kolejce) | workflow | przy montażu |
| D | `D02_plan_polskiego_glosu.md` | plan polskiego głosu | ZERO-PAKIET-020 | brak (w kolejce) | workflow | przy głosie |
| D | `D03_muzyka_grade_eksport.md` | muzyka, korekcja barwna, eksport | ZERO-PAKIET-021 | brak (w kolejce) | workflow | w postprodukcji |
| E | `E01_rejestr_decyzji_kanonicznych.md` (to plik kategorii E, nie odcinek E01) | zebrane decyzje kanoniczne i produktowe E01 z ID | ZERO-PAKIET-011 | **istnieje w katalogu** (ls 2026-11-28 15:11); temat „w toku”, **niezatwierdzony** — w tym pliku niewykorzystany | workflow | przy każdej decyzji |
| E | `E02_wersje_i_plan_testow.md` (to plik kategorii E, nie odcinek E02) | wersje plików i plan testów | ZERO-PAKIET-022 | brak (w kolejce) | workflow | przed pełnym wsadem |
| — | `docs/produkcja/ZERO-PLAN-002-pakiet-produkcyjny/pakiet_produkcyjny.md` | zbiorczy katalog pakietu z kolejnością prac | ZERO-PLAN-002 | brak (po fali 3) | workflow | do planowania prac |

*Uwaga o numeracji.* Zlecenia nie nadają numeru „B02” ani numeru dla promptów; ECHO-040 pkt 2 mówi, że pozycje 10 (lista ujęć z osią ms) i 14 (prompty) realizuje ZERO-PROD-002 (`DECYZJE L46`). Czy plik ZERO-PROD-002 ma w pakiecie numer B02 — **BRAK DANYCH** (szukano: `autobot/zlecenia/ZERO-PAKIET-*`, `ZERO-PLAN-002`).

### 8.3 Co dostaje model, a co zostaje poza nim (Kling 4.0)

| Warstwa | Zawartość | Plik źródłowy | Uwagi (odnośnik do granicy narzędzia) |
|---|---|---|---|
| wejście modelu | prompt EN (kadr, kamera, kto mówi i co — w cudzysłowie, ambient, efekty, zakaz muzyki i napisów) | `A08_przewodnik_promptow_kling.md` + plik sceny B | GM-08, GM-10 |
| wejście modelu | referencje postaci i obiektów (Elements), głosy | `A03_biblia_postaci.md`, `A04_arkusze_glosow.md`, `B06_paczka_referencji_s1.md` | GM-05, GM-06 |
| wejście modelu | klatka startowa (i końcowa) | `B05_arkusz_ciaglosci_s1.md` | GM-04 |
| wejście modelu | parametry: długość, rozdzielczość, proporcje | `A08_przewodnik_promptow_kling.md` | GM-01..GM-03 |
| poza modelem | muzyka | `D03_muzyka_grade_eksport.md`, `A07_biblia_dzwieku.md` | ZS-01, GM-10 |
| poza modelem | polski głos i napisy | `D02_plan_polskiego_glosu.md`, `D01_plan_montazu.md` | ZS-06, ZS-07, GM-07 |
| poza modelem | cięcia, przenikania, czerń, mosty dźwiękowe | `D01_plan_montazu.md`, `A09_katalog_ujec_uzupelniajacych_i_przejsc.md` | sekcja 7.5, GM-11 |
| poza modelem | teksty ekranowe i mapy | `A06_biblia_rekwizytow_i_ciaglosci.md` | GM-15 |

---

## 9. Pytania ABC do właściciela

Zasada: wpis decyzji w `autobot/DECYZJE.md` powstaje tylko po jednoznacznej odpowiedzi. Poniższe pytania nie rozstrzygają niczego za właściciela; warianty są opisane neutralnie (bez rekomendacji i bez rankingu narzędzi, ECHO-027). Numeracja: ZERO-PAKIET-001-Q*n*.

**ZERO-PAKIET-001-Q1 — Wiedza widza o relacji Vera–Aga w pakiecie, do czasu poprawki scenariusza (RK-01).**
A) Pakiet realizuje ECHO-020 od razu (widz wie od E01, że Vera jest matką Agi; Aga jeszcze nie); notę `SC L16` i `SC L41` traktujemy jako „do poprawki”. *Skutek:* arkusze postaci, głosów i kadrowanie S8 powstają pod ten wariant; trzeba je odświeżyć, jeśli decyzja się zmieni.
B) Pakiet trzyma wersję scenariusza (widz nie wie), ECHO-020 zapisane tylko jako uwaga. *Skutek:* pliki spójne z tekstem SC, ale sprzeczne z decyzją właściciela; do przepisania po poprawce SC.
C) Pakiet prowadzi oba warianty równolegle (kolumna „wariant”). *Skutek:* więcej pracy i dłuższe pliki; brak przepisywania po poprawce.

**ZERO-PAKIET-001-Q2 — Reguła audio (ECHO-008; RK-16, RK-17).**
A) Dwie warstwy: klip = dialog + ambient + efekty, bez muzyki (zakaz w każdym prompcie); muzyka wg jednej mapy w montażu, także muzyka „diegetyczna” (kawiarnia, jingle). *Skutek:* muzyka z SC (S1, S14) powstaje poza modelem; wymaga źródła i licencji (`C04_prawa_i_licencje.md`).
B) Jak A, ale muzyka diegetyczna (kawiarnia, jingle TV) dopuszczona w klipie. *Skutek:* trudniejsza kontrola „bez muzyki” (zakaz z promptu i kontrola pliku, GM-10); czy model stosuje się do zakazu w każdym klipie — **BRAK DANYCH** (jedyne źródło: relacja rz.4 `R008 L97` `Niechciana muzyka i efekty`, NIEPOTWIERDZONE; sprawdzić w teście zerowym, sekcja 11 poz. 9).
C) Muzyka z modelu dopuszczona tam, gdzie SC ją opisuje (S1, S14), a gdzie indziej zakaz. *Skutek:* muzyka z modelu trafia do ścieżki klipu; czy da się ją potem oddzielić od dialogu i efektów (eksport audio osobno) — **NIEPOTWIERDZONE** (`R002` wiersz 7 „Eksport audio osobno”) i **BRAK DANYCH**; plik nie twierdzi, że się nie da — do sprawdzenia w teście zerowym (sekcja 11 poz. 9). Pełne wyłączenie audio nie jest dostępne dla 4.0 (GM-10).

**ZERO-PAKIET-001-Q3 — Zasada E02 „bez mężczyzn w kadrze” w tej biblii (ZS-13).**
A) Zapisać jako informację o serialu z wyjątkami: zmarli z E01, zdjęcia Pawła i Piotra (jak wariant A analizy: `AN2 L879`). B) Zapisać bez wyjątków. C) Nie zapisywać do czasu decyzji AN2 D-06. *Skutek:* A i B zmieniają treść promptów E02 (poza zakresem tego etapu); C zostawia pole puste.

**ZERO-PAKIET-001-Q4 — Gdzie realizujemy napisy T, P1–P4, paski TV, SMS-y i ekrany (ZS-07; sekcja 5.6).**
A) W montażu, po polsku (w klipie zakaz tekstu). B) W klipie (generowane przez model), po polsku. C) Napisy T i P w montażu, teksty w scenografii (np. „Adam”) w klipie po teście czytelności (GM-15). *Skutek:* A = jedna spójna warstwa, więcej montażu; B = ryzyko zniekształceń tekstu; C = test przed decyzją.

**ZERO-PAKIET-001-Q5 — Kolejność na początku odcinka (RK-05).**
A) Jak w SC: S2 → P1 → S3. B) Jak w materiałach produkcyjnych: S2 → S3 → P1. C) Inna kolejność wskazana przez właściciela. *Skutek:* zmienia pary przejść i klatki łączące klipy (sekcja 7.5); B i C wymagają zmiany scenariusza (osobny temat).

**ZERO-PAKIET-001-Q6 — Zakończenie E01 (RK-03, RK-04).**
A) Jak w SC: Zero Day (z Agą i Verą), czarny ekran, sc. 15, czarny ekran. B) Jak w nocie reżyserskiej: trzy kadry (Marta, Karolina, Vera) i koniec; sc. 15 poza E01. C) Wariant własny wskazany przez właściciela. *Skutek:* decyduje o liczbie klipów końcówki, o przejściu PR-22, PR-23 i o tym, czy powstaje sc. 15 (filtry treści: BRAK DANYCH).

**ZERO-PAKIET-001-Q7 — Docelowy metraż E01 (RK-15).**
A) Ok. 60 min (SC: suma etykiet 60,5). B) Ok. 65 min (handoff). C) 52–55 min (rozpiska i log decyzji; z czołówką lub bez). *Skutek:* liczba klipów i koszt prób (`C03_budzet_i_koszty.md`); rozpiska 52:15 jest błędem rachunkowym (`AN3 R-14`).

**ZERO-PAKIET-001-Q8 — Reguła językowa Very i Agi (RK-18, RK-19).**
A) Kanon jak w SC: Vera po polsku z akcentem, kwestie norweskie z napisami polskimi; wykonanie w klipie ustala `A08_przewodnik_promptow_kling.md` po teście. B) Kanon zmieniony: wszystko po polsku (zmiana scenariusza, osobny temat). C) Kanon jak w SC, a w klipach kwestie norweskie jako mowa bez ruchu ust i głos w montażu. *Skutek:* norweski jest poza listą 9 języków mowy Klinga, a polski ma status BRAK DANYCH (GM-07).

**ZERO-PAKIET-001-Q9 — Realne marki i instytucje (ZS-18; PLAN D15).**
A) Zamienić marki medialne (TVN, TVN24, CNN) na fikcyjne odpowiedniki, pozostałe (WHO, ESA, PSE, UW, Szpital Bielański, gazoport) po konsultacji prawnej. B) Zostawić realne nazwy z zastrzeżeniem. C) Lista pozycja po pozycji do akceptacji. *Skutek:* teksty ekranowe (sekcja 5.6) i loga w montażu; temat praw: `C04_prawa_i_licencje.md`.

**ZERO-PAKIET-001-Q10 — Wariant narzędzia, rozdzielczość i droga uruchomienia (ZS-16; GM-01..GM-06, GM-17).**
A) Kling 4.0, 1080p, MCP z konta aplikacji. B) Kling 4.0, API Open Platform. C) Najpierw test zerowy obu wariantów (4.0 i 4.0 Flash) i dopiero decyzja. *Skutek:* 4.0 Flash ma inne ograniczenia (3–20 s — GM-01; tylko 720p — GM-02; tylko pierwsza klatka — GM-04; bez klonowania głosu — GM-06); zestawienie parametrów, nie ranking (ECHO-027).

**ZERO-PAKIET-001-Q11 — Kadry bez postaci spoza scenariusza (ECHO-041; sekcja 7.4).**
A) Tak: katalog (`A09_katalog_ujec_uzupelniajacych_i_przejsc.md`) i kadry Sceny 1 (`B07_kadry_uzupelniajace_i_przejscia_s1.md`) jako PROPOZYCJE, każdy kadr akceptuje właściciel. B) Tak, w limicie (np. określony udział metrażu) bez akceptacji per kadr. C) Nie: tylko kadry bez postaci obecne w SC i materiałach (inwentarz 7.3). *Skutek:* A = wolniej, pełna kontrola kanonu; B = szybciej, ryzyko dopisania obrazu spoza kanonu; C = film mniej „realny” wg ECHO-041.

**ZERO-PAKIET-001-Q12 — Rodzaj przejść do bloków przeszłości (RP-01; sekcja 7.5).**
A) Cięcia (zgodnie z `ARCH-01 L28`). B) Przenikania DISSOLVE dla wejść S5→P2, W-7→P3, W-5→P4 (jak w `U06`). C) Typ każdej pary ustala `A09_katalog_ujec_uzupelniajacych_i_przejsc.md` po zatwierdzeniu. *Skutek:* zmienia klipy łączące (pierwsza i ostatnia klatka) i dźwięk przejść.

### 9.2 Pytania zebrane w rejestrze (bez powielania wariantów)

Pytania o wygląd i fakty (włosy Karoliny, nadruk swetra, strój Marty, wygląd Very w epokach, sweter w S10 i S14, imię kolegi z PSE, obecność Piotra, los Michała, śmierć Dąbrowskiego, dzień śmierci Pawła, tolerancja czasu, baza Sceny 1) mają warianty w `AN3` sekcja 5 (Q1, Q2, Q3, Q5, Q7, Q10–Q20), w `AN1` sekcja (f2) (D-01..D-15) i w `PLAN` sekcja 5 (D1–D16). Pełną, ujednoliconą listę ma zebrać `E01_rejestr_decyzji_kanonicznych.md` (ZERO-PAKIET-011); w tym pliku nie powielamy wariantów.

---

## 10. Powiązania z innymi plikami pakietu

| Plik | Co ten plik (A01) dostarcza | Czego oczekuje od pliku | Do sprawdzenia po zatwierdzeniu |
|---|---|---|---|
| `A02_przewodnik_wizualny.md` | zasady ZS-03, ZS-04; sekcja 7 (kadry i przejścia) | palety, język kamery, słownik przejść; spójne z 7.2 i 7.5 | zgodność typów przejść (PR-01..PR-23) i faz rytmu (7.1) |
| `A03_biblia_postaci.md` | rejestr osób 5.1, wieki 5.3, rozbieżności wyglądu RK-09..RK-13 | arkusze epok Very, Dąbrowskiego, Agi; wygląd Karoliny i Marty | zgodność wieku i epok z 4.2 i 5.3 |
| `A04_arkusze_glosow.md` | ZS-05, ZS-06, RK-18, RK-19 | głosy EN i PL, status polskiego (GM-07) | spójność reguły językowej (Q8) |
| `A05_biblia_lokacji.md` | miejsca 5.4, RK-14, RK-36 | karty lokacji ze stałymi elementami | zgodność liczby i nazw lokacji (24 pozycje LK-01..LK-24 z 5.4) |
| `A06_biblia_rekwizytow_i_ciaglosci.md` | teksty ekranowe 5.6, RK-10, RK-31, RK-37, ZS-12 | rejestr rekwizytów, stan per scena | dosłowne brzmienia TE-01..TE-25 |
| `A07_biblia_dzwieku.md` | ZS-01, ZS-02, RK-16, RK-17, Q2 | mapa muzyczna i reguła audio | jedna reguła audio |
| `A08_przewodnik_promptow_kling.md` | zasady stałe ZS-01..ZS-09, granice GM-01..GM-17 | szablon promptu, blok zasad stałych | brak sprzeczności z GM-* |
| `A09_katalog_ujec_uzupelniajacych_i_przejsc.md` | zasada, rola i rytm (7.1), inwentarz KB-01..KB-26, przejścia PR-01..PR-23 | pełna typologia i rytm na minutę | zgodność numeracji kadrów i par |
| `B01`–`B07`, ZERO-PROD-002 | struktura E01 (3.1), oś (4.1), zasady stałe | plik Sceny 1 z osią ms | zgodność KB-01, KB-02, KB-03 z `P002` K01, K03, K08 |
| `C01`–`C04` | metraż (RK-15), granice narzędzia (GM-*) | koszty, prawa, tracker, kontrola jakości | metraż i liczba klipów |
| `D01`–`D03` | przejścia (7.5), reguła audio, teksty ekranowe | plan montażu, głos, muzyka | zgodność typów przejść i mostów dźwiękowych |
| `E01_rejestr_decyzji_kanonicznych.md` | rozbieżności RK-01..RK-37 i RP-01..RP-04 z odnośnikami do ID źródłowych | ID rejestru dla każdej pozycji | mapowanie RK → ID rejestru (uzupełnić) |
| `E02_wersje_i_plan_testow.md` | hash SC i zakres wersji (0.4) | wersje, plan testu zerowego | test zerowy dla BRAK DANYCH z GM-* |

**Sprzeczności między plikami pakietu:** w chwili pisania nie było plików pakietu zatwierdzonych wcześniej, więc nie wykryto sprzeczności. Robocze pliki `E01_rejestr_decyzji_kanonicznych.md`, `A02_przewodnik_wizualny.md` i `A03_biblia_postaci.md` (niezatwierdzone, tematy „w toku”; stan ls w 0.5) istnieją w katalogu i nie zostały użyte (nie są wejściami zatwierdzonymi przed tym tematem); zgodność z nimi (np. typy przejść z 7.5, wieki z 5.3, identyfikatory) do sprawdzenia po ich zatwierdzeniu.

---

## 11. Co jeszcze dołożyć (PROPOZYCJE; nie są częścią kanonu ani zlecenia)

| # | Co dołożyć | Uzasadnienie | Decyzja właściciela |
|---|---|---|---|
| 1 | Mapowanie RK-01..RK-37 i RP-01..RP-04 na ID rejestru `E01_rejestr_decyzji_kanonicznych.md` po jego zatwierdzeniu | rejestr nadaje własne ID; dziś odnośniki idą do ID źródłowych | nie |
| 2 | Jednostronicowe streszczenie bibli (zasady ZS, granice GM, hierarchia źródeł) do wklejenia w kontekst nowego agenta | mniej tokenów, ta sama kontrola | nie |
| 3 | Wersja bibli w języku angielskim (tylko zasady stałe i opis tonu) do bloku zasad w promptach | model dostaje zasady po angielsku; treść już jest w `A08_przewodnik_promptow_kling.md` | nie |
| 4 | Diagram wizualny osi T i toru B (SVG lub tabela graficzna) | czytelność cofnięć osi (RK-21) | nie |
| 5 | Tabela wiedzy widza po węzłach (kto, co i kiedy wie; Vera–Aga, Ares IV, Piotr) | pomaga montażowi przy ECHO-020 | TAK — po Q1 |
| 6 | Lista tekstów do czołówki (62 s) i plik `ZERO_czolowka.md` z archiwum | czołówka jest w ADR (`ADR L44`), poza zakresem tego pliku | TAK — czy czołówka wchodzi do pakietu |
| 7 | Rejestr statystów i demografii kadru per segment (AN3 L-12) | model sam dobiera statystów; zasada „kobiety i mężczyźni razem” dla S1 i T-7 | nie |
| 8 | Plan stanów mapy PSE na osi T (4 stany) | RK-37; „wykres katastrofy” | TAK — kanon lekki |
| 9 | Plan testu zerowego dla BRAK DANYCH z GM-* (fps, limit promptu, czytelność tekstu, filtry, polski, stosowanie zakazu muzyki w prompcie, eksport audio osobno) | zamienia luki w dane | TAK — zgoda na koszt testu |
| 10 | Aktualizacja plików rz.4 (`01`–`08` produkcyjne) po decyzjach, zamiast poprawiania w pakiecie | AN3 R-64; pliki mają nieaktualne wieki, napisy i nazwę wirusa | TAK — osobny temat |
| 11 | Notatka o kolizji oznaczeń A01/A02/A08 (archiwum) i A01–A09 (pakiet) w README pakietu | unika pomyłek (0.3) | nie |
| 12 | Sprawdzenie, czy sc. 15 przechodzi filtry treści (ciała na pokładzie) przed decyzją o pełnym wsadzie | GM-16 | TAK — razem z Q6 |

<!-- KONIEC-PLIKU -->
