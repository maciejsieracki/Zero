# ZERO — rejestr tematow

Stan na 2026-11-27 (aktualizowany przez orkiestratora po kazdym zdarzeniu terminalnym).

## Aktywne

| ID | GOAL | Runda | Stan |
|---|---|---|---|
| ZERO-BAZA-001-import-scenariuszy | Trzy aktualne scenariusze sa w repozytorium jako baza z hashami zgodnymi z archiwum zrodlowym | 1 z 3 | w toku (workflow wf_86bf9f7b-43a) |
| ZERO-ANALIZA-001-e01-logika-timing-napiecie | Dla E01 istnieje zweryfikowany raport: logika, timing i napiecie z cytatami i wariantami naprawy | 0 z 3 | zablokowany do konca ZERO-BAZA-001 |
| ZERO-ANALIZA-002-e02-logika-timing-napiecie | Dla E02 istnieje zweryfikowany raport: logika, timing i napiecie z cytatami i wariantami naprawy | 0 z 3 | zablokowany do konca ZERO-BAZA-001 |
| ZERO-RESEARCH-001-porownanie-generatorow-wideo | Istnieje zweryfikowane zestawienie generatorow wideo AI (Kling, Seedance, Veo, Sora 2, MiniMax API): maks. dlugosc klipu, maks. rozdzielczosc, koszt 1 min Full HD w rozliczeniu kredytowym/API, od najtanszego | 0 z 3 | w toku; pula 2 = BAZA + RESEARCH, analizy E01/E02 startuja po zwolnieniu slotow |

## Zablokowane / do rozpoczecia

- Temat miedzyodcinkowy E01<->E02 (spojnosc, wiedza widza) — po raportach ANALIZA-001 i -002.
- Tematy poprawek scenariuszy — po decyzjach kanonicznych wlasciciela.

## Zamkniete

Brak.

## Liczby obowiazujace

| Wielkosc | Wartosc | Status |
|---|---|---|
| Limit rund | 3 | obowiazuje |
| Pula rownolegla | 2 | ECHO-002 |
| Limit raportu terminalnego | 400 slow | obowiazuje |
| Czas E01 (suma etykiet CZAS) | 60,5 min | niepotwierdzone przez Evaluatora — do weryfikacji w ANALIZA-001 |
| Czas E02 | 5 roznych wartosci (65 / 69 / 70,5 / 73,5 / ~67) | do rozstrzygniecia w ANALIZA-002 |

## Slad procesu — dlug niespelniony

Przed wprowadzeniem zasad AutoBot (2026-11-27) uruchomiono bez zapisu zlecenia: siedmiu agentow przegladu archiwum, dwa audyty Opus (E01, E02), dwa audyty zatrzymane (E03, miedzyodcinkowy) oraz plan (`PLAN_WDROZENIA_ZERO.md`) i notatki w `docs/`. **Traktowane wylacznie jako material wejsciowy (rzad 4), nie jako wynik procesu.** Zapisow nie uzupelniamy wstecz.
