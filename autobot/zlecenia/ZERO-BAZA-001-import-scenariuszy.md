# ZERO-BAZA-001-import-scenariuszy

WYZWALACZ:  decyzja wlasciciela ECHO-001 (ZERO-PROCES-001-Q1 = A), 2026-11-27. Import musi poprzedzic analize (baza wskazana przez wlasciciela).
GOAL:       Trzy aktualne scenariusze (`_rev`) znajduja sie w `scenariusze/` w repozytorium, bajt w bajt zgodne z oryginalami z archiwum zrodlowego.
KONIEC:     PRAWDA gdy: trzy pliki w `scenariusze/` maja SHA-256 rowne oryginalom z archiwum, istnieje zgodny `MANIFEST.sha256`, brak innych zmian w repozytorium. Scenariusze: S-I1, S-I2, S-I3.

ALLOWLISTA:
  - `scenariusze/ZERO_mini_serial_E01_ADAM_rev.md`
  - `scenariusze/ZERO_mini_serial_E02_EWA_rev.md`
  - `scenariusze/ZERO_mini_serial_E03_ARES_rev.md`
  - `scenariusze/MANIFEST.sha256`
ZAKAZANE BEZWZGLEDNIE: modyfikacja tresci plikow zrodlowych; jakiekolwiek inne pliki repozytorium (w tym `autobot/`, `docs/`, `PLAN_WDROZENIA_ZERO.md`); polecenia git zmieniajace stan (add, commit, push, reset, checkout, clean); zapis wartosci sekretow.

MIEJSCE PRACY: `scenariusze/` w `/home/user/Zero`; tymczasowa ekstrakcja tylko w nowym pustym katalogu w scratchpadzie sesji.
BAZA:          HEAD galezi `claude/friendly-franklin-mn4e88`; zrodlo plikow: archiwum `/root/.claude/uploads/3337db06-529b-5b00-81d6-a0a7013a451d/2b726cf2-Zero.rar` (pliki `Zero/ZERO_mini_serial_E0{1,2,3}_*_rev.md` w korzeniu archiwum, nie z `ZERO_DO_PRZENIESIENIA/`).

PLAN SPRAWDZENIA:
  1. S-I1: niezalezna swieza ekstrakcja (nowy pusty katalog) i porownanie SHA-256
  2. S-I2: `git status --porcelain` — tylko `scenariusze/`
  3. S-I3: `sha256sum -c MANIFEST.sha256` w `scenariusze/`

RUNDA: 1 z 3
