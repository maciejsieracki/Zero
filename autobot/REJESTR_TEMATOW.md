# ZERO — rejestr tematow

Stan na 2026-11-27 (aktualizowany przez orkiestratora po kazdym zdarzeniu terminalnym). Po restarcie kontenera stan odtworzony z wynikow workflow i repozytorium.

## Aktywne / wstrzymane

| ID | GOAL | Runda | Stan |
|---|---|---|---|
| ZERO-AUDIO-001-e01-audiobook | Gotowy do odczytu tekst audiobooka dla E01 (opisy ze scenariusza, dialogi bez zmian), PDF, notatka dla lektora i slad dodatkow | 4 z 4 (zgoda wlasciciela ECHO-015) | **w kolejce**: dodatkowe przejscie (Evaluator -> Final Control -> Integration, bez zmian tresci) ruszy, gdy zwolni sie miejsce w puli 2 (RESEARCH-002 i -003 w toku); Evaluator r3 = CLEAR |
| ZERO-RESEARCH-002-audio-i-jezyk-polski | Zestawienie: dzwiek razem z obrazem, jezyk polski, jednoczesnosc audio i wideo | 5 z 5 (zgoda wlasciciela ECHO-025) | **w toku (runda 5 z 5 na wezlach z zarzutami lub blokada; licznik aktualizuje orkiestrator po zakonczeniu workflow)**: dopuszczone hosty Google i OpenAI; Operator uruchamiany w kazdym wezle. Wczesniejszy stan: wezly: MiniMax PASS (r1); Kling FINDINGS (1 zarzut merytoryczny: zakres audio modelu Flash oznaczony BRAK DANYCH mimo zrodla), Seedance FINDINGS (2 zarzuty: stare twierdzenie o blokadzie hosta i naglowek rundy; oba wynikaja z mojego bledu — pominalem Operatora w tej rundzie, mimo ze wytyczne wymagaly ponownego odczytu), Veo i Sora 2 BLOCK (dokumentacja przekierowuje na hosty aistudio.google.com, docs.cloud.google.com, developers.openai.com niedopuszczone w sieci). Synteza nie uruchomiona.
| ZERO-RESEARCH-003-api-i-mcp-sterowanie | Zestawienie: API, SDK i serwery MCP do sterowania z Claude Code | 5 z 5 (zgoda wlasciciela ECHO-025) | **w toku (runda 5 z 5 na wezlach z zarzutami lub blokada; licznik aktualizuje orkiestrator po zakonczeniu workflow)**: dopuszczone hosty Google i OpenAI; Operator uruchamiany w kazdym wezle. Wczesniejszy stan: wezly: Kling PASS (r4), Sora 2 PASS (r4), Veo BLOCK (docs na hostach aistudio.google.com i docs.cloud.google.com niedopuszczonych), Seedance FINDINGS (1 zarzut: wymog konta BytePlus i progu 30 USD blednie przypisany kanalowi Volcengine), MiniMax FINDINGS (2 zarzuty i 1 procesowy; wynik mojego bledu — pominalem Operatora, wytyczne wymagaly ponownego odczytu platform.minimax.io). Synteza nie uruchomiona.

## Zablokowane / do rozpoczecia

- Temat miedzyodcinkowy E01<->E02 (spojnosc, wiedza widza) — po raporcie ANALIZA-002.
- Tematy poprawek scenariuszy — po decyzjach kanonicznych wlasciciela.
- ZERO-PROCES-004-przejecie-regul-autobot — pelny, samodzielny plik zasad AutoBot dla innych agentow (autobot/ZASADY_PROCESU.md; ECHO-015..018); zlecenie zapisane, w kolejce za RESEARCH-002/-003 (priorytet wlasciciela: najpierw porownanie systemow wideo).

## Zamkniete

| ID | GOAL | Wynik | Najslabszy wezel |
|---|---|---|---|
| ZERO-BAZA-001-import-scenariuszy | Trzy aktualne scenariusze (`_rev`) w `scenariusze/` bajt w bajt zgodne z archiwum zrodlowym | PASS, runda 1 z 3; **READY_FOR_DEPLOY** (commit "Wlacz baze scenariuszy (ZERO-BAZA-001)...") | Operator (skrocone hashe w raporcie; Evaluator i Final Control powtorzyly dowody) |
| ZERO-ANALIZA-001-e01-logika-timing-napiecie | Dla E01 zweryfikowany raport: logika, timing i napiecie z cytatami i wariantami naprawy | PASS, runda 1 z 3 (stary obieg bez osobnej obrony i roli Integration); **READY_FOR_DEPLOY** po wlaczeniu przez orkiestratora (commit "Wlacz wytwor ZERO-ANALIZA-001 (AutoBot, runda 1)") | Operator (PROPOZYCJE zapisane w formacie cytatu; brak jawnej linii GOAL w raporcie) |
| ZERO-ANALIZA-002-e02-logika-timing-napiecie | Dla E02 zweryfikowany raport: logika, timing i napiecie z cytatami i wariantami naprawy | PASS, runda 1 z 3 (obieg z obrona: Evaluator CLEAR 10/10, Final Control bez zarzutow, Integration INTEGRATED_VERIFIED); **READY_FOR_DEPLOY** (commit "Wlacz wytwor ZERO-ANALIZA-002-e02-logika-timing-napiecie (AutoBot, runda 1)") | Evaluator (pole z hashem zbiorczym nie dawalo sie odtworzyc; Final Control potwierdzil hashe niezaleznie) |
| ZERO-PROCES-002-inwentarz-zasad-autobot | Zweryfikowany inwentarz zestawow zasad AutoBot (Autobot.rar, paczka v2, wersja sesji) z lista kasacji i wskazaniem najnowszego zestawu z obrona | PASS po dodatkowym przejsciu (runda 4 z 4, zgoda wlasciciela ECHO-011: Evaluator CLEAR 10/10, Final Control bez zarzutow, Integration INTEGRATED_VERIFIED); **READY_FOR_DEPLOY** (commit "Wlacz wytwor ZERO-PROCES-002-inwentarz-zasad-autobot (AutoBot, runda 4)") | Orkiestrator (nieaktualny rejestr i licznik rund w zleceniu w rundach 2-3; zarzuty procesowe Final Control) |
| ZERO-PROCES-003-komenda-usuwania-plikow | Zweryfikowany skrypt PowerShell usuwajacy z OneDrive wylacznie pliki zasad AutoBot o zgodnej nazwie i hashu, domyslnie podglad, do Kosza | PASS, runda 2 z 3 (obieg z obrona: Evaluator CLEAR 10/10, Final Control, Integration INTEGRATED_VERIFIED); **READY_FOR_DEPLOY** (commit "Wlacz wytwor ZERO-PROCES-003..."). Test na prawdziwym srodowisku: wlasciciel uruchomil skrypt w Windows PowerShell 5.1 w trybie podgladu (2026-11-27) — 6 z 6 plikow znalezionych i zakwalifikowanych (nazwa i hash zgodne), 0 bledow, rozmiary zgodne z archiwum; usuwanie (flaga $true) jeszcze niewykonane | Operator (w rundzie 1 bledny skrot hasha swiadka w README; poprawiony po zarzucie) |
| ZERO-RESEARCH-001-porownanie-generatorow-wideo | Zestawienie generatorow wideo AI (Kling, Seedance, Veo, Sora 2, MiniMax API): dlugosc klipu, rozdzielczosc, koszt 1 min Full HD, od najtanszego | PASS po rundzie 4 z 4 (zgoda wlasciciela ECHO-012; Seedance po dopuszczeniu hostow BytePlus/Volcengine; synteza i Final Control ODDAL; Integration INTEGRATED_VERIFIED); **READY_FOR_DEPLOY** (commit "Wlacz wytwor ZERO-RESEARCH-001..."). Stary obieg bez osobnej obrony (ECHO-010 pkt 2). Wynik: Sora 2 API wylaczone od 2026-09-24 | Wezel Seedance (INFRA w rundach 1-3: blokada sieci); wczesniej Kling (zla podstawa cen pakietowych w rundzie 1) |

## Liczby obowiazujace

| Wielkosc | Wartosc | Status |
|---|---|---|
| Limit rund | 3 | obowiazuje |
| Pula rownolegla | 2 | ECHO-002 |
| Limit raportu terminalnego | 400 slow | obowiazuje |
| Baza scenariuszy SHA-256 (poczatek) | E01 b0264c95…, E02 1166c23d…, E03 24315de7… (pelne w `scenariusze/MANIFEST.sha256`) | potwierdzone przez Evaluatora i Final Control |
| Czas E01 (suma etykiet CZAS) | 60,5 min (suma 23 segmentow; naglowek "60 minut") | potwierdzone przez Final Control (ANALIZA-001) |
| Czas E02 | 5 roznych wartosci (65 / 69 / 70,5 / 73,5 / ~67) | do rozstrzygniecia w ANALIZA-002 |

## Slad procesu — dlug niespelniony

- Przed wprowadzeniem zasad AutoBot (2026-11-27) uruchomiono bez zapisu zlecenia: siedmiu agentow przegladu archiwum, dwa audyty Opus (E01, E02), dwa audyty zatrzymane (E03, miedzyodcinkowy) oraz plan (`PLAN_WDROZENIA_ZERO.md`) i notatki w `docs/`. Traktowane wylacznie jako material wejsciowy (rzad 4).
- Tematy BAZA-001, ANALIZA-001 i RESEARCH-001 przeszly obiegiem bez osobnej obrony (zasady z listy umiejetnosci sesji); od ECHO-010 obowiazuje obieg z obrona (skrypt `zero-autobot-v2`), a PROCES-002 i ANALIZA-002 ida juz nim.
- **Uchybienie orkiestratora:** w trakcie PROCES-002 nie zaktualizowalem w pore rejestru i licznika rund w zleceniu, przez co Final Control zglosil 2 zarzuty procesowe, a runda 3 zostala zmarnowana. Naprawione w tym zapisie.
- ANALIZA-002: pierwsze uruchomienie Operatora = INFRA (Operator odpowiedzial na wiadomosc uzytkownika z kontekstu sesji, nic nie zmienil; runda nie zuzyta); dopisano zastrzezenie o zrodle zlecenia do wszystkich rol. Integration w rundzie 1 = INTEGRATION_FAILED z powodu bledu skryptu orkiestratora (hash zbiorczy Evaluatora nie do odtworzenia); poprawiono na hashe per plik i wykonano sam krok Integration (INTEGRATED_VERIFIED).
- AUDIO-001: powtorzylem uchybienie z PROCES-002 — nie zaktualizowalem licznika rund w rejestrze w trakcie pracy workflow, wiec Final Control zglosil zarzut procesowy we wszystkich trzech rundach (w r3 jedyny). Zapobieganie: przy kolejnych tematach w rejestrze wpisuje od startu "w toku (runda 1-3 z 3; licznik aktualizuje orkiestrator po zakonczeniu workflow)" i odnotowuje to w zleceniu.
- Restart kontenera przerwal sesje; trzy workflow (ANALIZA-001, PROCES-002 i wczesniej BAZA/RESEARCH-001) zakonczyly sie przed restartem, a ich wyniki odczytano z plikow wyjsciowych.
- RESEARCH-002/-003 runda 4: **uchybienie orkiestratora** — dla wezlow z wytworem z rundy 3 ustawilem preset_op ("brak zmian"), mimo ze wytyczne rundy 4 wymagaly ponownego odczytu bezposredniego; Operator nie zostal uruchomiony, wiec Evaluator i Final Control slusznie zglosily zarzuty (Seedance R2, MiniMax R3). Runda zmarnowana; naprawa wymaga zgody wlasciciela na kolejne przejscie.
