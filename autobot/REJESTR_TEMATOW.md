# ZERO — rejestr tematow

Stan na 2026-11-27 (aktualizowany przez orkiestratora po kazdym zdarzeniu terminalnym). Po restarcie kontenera stan odtworzony z wynikow workflow i repozytorium.

## Aktywne / wstrzymane

| ID | GOAL | Runda | Stan |
|---|---|---|---|
| ZERO-ANALIZA-002-e02-logika-timing-napiecie | Dla E02 istnieje zweryfikowany raport: logika, timing i napiecie z cytatami i wariantami naprawy | 1 z 3 | w toku (obieg z obrona), start po restarcie kontenera |
| ZERO-RESEARCH-001-porownanie-generatorow-wideo | Istnieje zweryfikowane zestawienie generatorow wideo AI (Kling, Seedance, Veo, Sora 2, MiniMax API): maks. dlugosc klipu, maks. rozdzielczosc, koszt 1 min Full HD w rozliczeniu kredytowym/API, od najtanszego | 3 z 3 (limit) | **WSTRZYMANY, czeka na decyzje wlasciciela**: wezly Kling, Veo, Sora 2, MiniMax = PASS; Seedance = INFRA we wszystkich 3 rundach (sieć sesji blokuje oficjalne strony BytePlus/Volcengine); synteza nie uruchomiona |
| ZERO-PROCES-002-inwentarz-zasad-autobot | Istnieje zweryfikowany inwentarz zestawow zasad AutoBot (Autobot.rar, paczka v2, wersja sesji) | 3 z 3 (limit) | **WSTRZYMANY**: Evaluator w rundzie 2 = CLEAR (10/10, wszystkie scenariusze); Final Control zglosil 2 zarzuty PROCESOWE dotyczace moich zapisow (stan rejestru i licznik rund w zleceniu), ktore Operator slusznie uznal za poza swoim zakresem (BLOCK w rundzie 3); wytwor nie zintegrowany (niezacommitowany) |
| ZERO-RESEARCH-002-audio-i-jezyk-polski | Zestawienie: dzwiek razem z obrazem, jezyk polski, jednoczesnosc audio i wideo | 0 z 3 | zablokowany: zalezy od wyniku RESEARCH-001 |
| ZERO-RESEARCH-003-api-i-mcp-sterowanie | Zestawienie: API, SDK i serwery MCP do sterowania z Claude Code | 0 z 3 | zablokowany: zalezy od wyniku RESEARCH-001 |

## Zablokowane / do rozpoczecia

- Temat miedzyodcinkowy E01<->E02 (spojnosc, wiedza widza) — po raporcie ANALIZA-002.
- Tematy poprawek scenariuszy — po decyzjach kanonicznych wlasciciela.
- Przejecie najnowszego zestawu zasad (R1-R13 z inwentarza) — osobny temat PROCES po zamknieciu PROCES-002 i decyzji wlasciciela.

## Zamkniete

| ID | GOAL | Wynik | Najslabszy wezel |
|---|---|---|---|
| ZERO-BAZA-001-import-scenariuszy | Trzy aktualne scenariusze (`_rev`) w `scenariusze/` bajt w bajt zgodne z archiwum zrodlowym | PASS, runda 1 z 3; **READY_FOR_DEPLOY** (commit "Wlacz baze scenariuszy (ZERO-BAZA-001)...") | Operator (skrocone hashe w raporcie; Evaluator i Final Control powtorzyly dowody) |
| ZERO-ANALIZA-001-e01-logika-timing-napiecie | Dla E01 zweryfikowany raport: logika, timing i napiecie z cytatami i wariantami naprawy | PASS, runda 1 z 3 (stary obieg bez osobnej obrony i roli Integration); **READY_FOR_DEPLOY** po wlaczeniu przez orkiestratora (commit "Wlacz wytwor ZERO-ANALIZA-001 (AutoBot, runda 1)") | Operator (PROPOZYCJE zapisane w formacie cytatu; brak jawnej linii GOAL w raporcie) |

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
- Restart kontenera przerwal sesje; trzy workflow (ANALIZA-001, PROCES-002 i wczesniej BAZA/RESEARCH-001) zakonczyly sie przed restartem, a ich wyniki odczytano z plikow wyjsciowych.
