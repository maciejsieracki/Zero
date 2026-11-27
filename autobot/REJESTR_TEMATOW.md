# ZERO — rejestr tematow

Stan na 2026-11-27 (aktualizowany przez orkiestratora po kazdym zdarzeniu terminalnym).

## Aktywne

| ID | GOAL | Runda | Stan |
|---|---|---|---|
| ZERO-RESEARCH-001-porownanie-generatorow-wideo | Istnieje zweryfikowane zestawienie generatorow wideo AI (Kling, Seedance, Veo, Sora 2, MiniMax API): maks. dlugosc klipu, maks. rozdzielczosc, koszt 1 min Full HD w rozliczeniu kredytowym/API, od najtanszego | 1 z 3 | w toku (workflow, wezly -a..-e) |
| ZERO-ANALIZA-001-e01-logika-timing-napiecie | Dla E01 istnieje zweryfikowany raport: logika, timing i napiecie z cytatami i wariantami naprawy | 1 z 3 | w toku (workflow) |
| ZERO-ANALIZA-002-e02-logika-timing-napiecie | Dla E02 istnieje zweryfikowany raport: logika, timing i napiecie z cytatami i wariantami naprawy | 0 z 3 | oczekuje na wolny slot (pula 2); start po zakonczeniu ANALIZA-001 |
| ZERO-RESEARCH-002-audio-i-jezyk-polski | Istnieje zweryfikowane zestawienie, ktore generatory (Kling, Seedance, Veo, Sora 2, MiniMax API) tworza dzwiek razem z obrazem, jak obsluguja jezyk polski i czy audio powstaje jednoczesnie z wideo, z ocena pewnosci zrodel | 0 z 3 | oczekuje na wolny slot (pula 2); start po zakonczeniu RESEARCH-001 (zalezy od jego wyniku) |
| ZERO-RESEARCH-003-api-i-mcp-sterowanie | Istnieje zweryfikowane zestawienie, ktorzy dostawcy wideo (Kling, Seedance, Veo, Sora 2, MiniMax) maja API, SDK i serwer MCP umozliwiajace sterowanie generowaniem z Claude Code, z punktowa ocena gotowosci | 0 z 3 | oczekuje na wolny slot (pula 2); start po RESEARCH-001; kolejnosc kolejki: PROCES-002 (pierwszenstwo), RESEARCH-002, RESEARCH-003, ANALIZA-002 (do zmiany na polecenie wlasciciela) |
| ZERO-PROCES-002-inwentarz-zasad-autobot | Istnieje zweryfikowany inwentarz zestawow zasad AutoBot (Autobot.rar, paczka v2, wersja sesji): data, zakres, czy definiuja obrone i osobna role Integration, status, rekomendacja usuniecia lub zachowania, wskazanie najnowszego zestawu z obrona i roznic wzgledem v2 | 0 z 3 | oczekuje na pierwszy wolny slot (pierwszenstwo, ECHO-010); pierwszy temat w nowym obiegu z obrona |

## Zablokowane / do rozpoczecia

- Temat miedzyodcinkowy E01<->E02 (spojnosc, wiedza widza) — po raportach ANALIZA-001 i -002.
- Tematy poprawek scenariuszy — po decyzjach kanonicznych wlasciciela.

## Zamkniete

| ID | GOAL | Wynik | Najslabszy wezel |
|---|---|---|---|
| ZERO-BAZA-001-import-scenariuszy | Trzy aktualne scenariusze (`_rev`) w `scenariusze/` bajt w bajt zgodne z archiwum zrodlowym | PASS, runda 1 z 3; **READY_FOR_DEPLOY** po wlaczeniu do galezi roboczej (commit "Wlacz baze scenariuszy (ZERO-BAZA-001)...") | Operator (w raporcie skrocone hashe i zrodlo ekstrakcji tylko slownie; Evaluator i Final Control powtorzyly dowody niezaleznie) |

## Liczby obowiazujace

| Wielkosc | Wartosc | Status |
|---|---|---|
| Limit rund | 3 | obowiazuje |
| Pula rownolegla | 2 | ECHO-002 |
| Limit raportu terminalnego | 400 slow | obowiazuje |
| Baza scenariuszy SHA-256 (poczatek) | E01 b0264c95…, E02 1166c23d…, E03 24315de7… (pelne w `scenariusze/MANIFEST.sha256`) | potwierdzone przez Evaluatora i Final Control |
| Czas E01 (suma etykiet CZAS) | 60,5 min | niepotwierdzone przez Evaluatora — do weryfikacji w ANALIZA-001 |
| Czas E02 | 5 roznych wartosci (65 / 69 / 70,5 / 73,5 / ~67) | do rozstrzygniecia w ANALIZA-002 |

## Slad procesu — dlug niespelniony

Przed wprowadzeniem zasad AutoBot (2026-11-27) uruchomiono bez zapisu zlecenia: siedmiu agentow przegladu archiwum, dwa audyty Opus (E01, E02), dwa audyty zatrzymane (E03, miedzyodcinkowy) oraz plan (`PLAN_WDROZENIA_ZERO.md`) i notatki w `docs/`. **Traktowane wylacznie jako material wejsciowy (rzad 4), nie jako wynik procesu.** Zapisow nie uzupelniamy wstecz.
