# ZERO — wybory trwale i granice nienaruszalne

## Parametry procesu

| Parametr | Wartosc | Skad |
|---|---|---|
| Limit rund na temat | 3 | domyslny bezpieczny; orkiestrator decyduje i informuje |
| Limit objetosci raportu terminalnego | 400 slow (wytwor w pliku nie jest limitowany) | domyslny |
| Pula tematow rownoleglych | 2 | ECHO-002 |
| Etapy w ID tematow | BAZA, ANALIZA, RESEARCH, PROCES | orkiestrator, informacja |
| Modele | Opus 5.5 dla Operatora, Evaluatora i Final Control | ECHO-006 |
| Prog zwisu (ZWIS) | 40 min bez zadnego postepu; orkiestrator sprawdza przebieg zamiast restartowac | orkiestrator, informacja |
| Jezyk dokumentow | polski; nazwy techniczne, pola i sciezki po angielsku bez diakrytykow | orkiestrator |
| Miejsce pracy | `docs/analiza/<ID>/` (jedna przestrzen na temat); import: `scenariusze/` | orkiestrator |
| Baza | HEAD galezi `claude/friendly-franklin-mn4e88` (po imporcie: commit z hashami) | ECHO-001 |
| Integracja | commit orkiestratora + push na galaz robocza | ECHO-004 |
| Backup i odtworzenie | historia git; przed kazda zmiana scenariusza osobny commit-kopia | handoff 2026-10-11 |

## Granice nienaruszalne (naruszenie = natychmiastowy FAIL)

Zrodlo: zasady wlasciciela z handoffu 2026-10-11 i z rozmowy. **Do potwierdzenia przez wlasciciela jednym zdaniem; zmiana wymaga ECHO.**

- **G1** Zaden plik w `scenariusze/` nie zmienia sie w tematach analizy (hash przed i po).
- **G2** Tresci dialogow nie zmieniamy samowolnie; propozycje nowego brzmienia sa wylacznie w raporcie i oznaczone PROPOZYCJA (ECHO-003).
- **G3** Kanon (postacie, fakty, os czasu) rozstrzyga wylacznie wlasciciel; analiza proponuje warianty, nie rozstrzyga.
- **G4** Backup przed kazda zmiana scenariusza (w temacie poprawek).
- **G5** Zadnych wartosci sekretow w zapisach; push tylko na galaz robocza w `origin` (ECHO-004).
- **G6** Materialy zrodlowe (paczka `Zero.rar`, wewnetrzne ZIP-y) nie sa modyfikowane.
- **G7** Poza zakresem: E03, Planify, pliki spoza allowlisty tematu.

## Czego swiadomie nie robimy

Nie poprawiamy scenariuszy w analizie; nie analizujemy E03; nie generujemy wideo; nie budujemy budzetu; nie gonimy parytetu z cudzymi narzedziami. Pomysl spoza GOAL = nowy temat, nie poszerzenie allowlisty.

## Wybory otwarte

| # | Wybor | Stan |
|---|---|---|
| 1 | Decyzje kanoniczne D4-D16 (Wolska, Zofia, reveal Agi, os milczenia Ares, metraz...) | otwarte, do podjecia po raportach analizy |
| 2 | Kanal i model wydania serialu | otwarte |
| 3 | Potwierdzenie granic G1-G7 jednym zdaniem | oczekuje na wlasciciela |
