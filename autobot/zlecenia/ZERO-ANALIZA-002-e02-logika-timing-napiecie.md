# ZERO-ANALIZA-002-e02-logika-timing-napiecie

WYZWALACZ:  decyzja wlasciciela ECHO-005 (zakres E01 i E02), ECHO-002 (rownolegle), ECHO-003 (propozycje brzmienia w raporcie); odblokowanie zaleznosci po ZERO-BAZA-001. Data 2026-11-27.
GOAL:       Dla odcinka E02 istnieje zweryfikowany raport z analizy logiki, timingu i budowania napiecia: z doslownymi cytatami, numerami linii, waga, wariantami naprawy (PROPOZYCJE) i kolejnoscia poprawek.
KONIEC:     PRAWDA gdy scenariusze S-A1..S-A9 przechodza. Zadna zmiana poza allowlista.

ALLOWLISTA:
  - `docs/analiza/ZERO-ANALIZA-002-e02-logika-timing-napiecie/raport.md`
  - `docs/analiza/ZERO-ANALIZA-002-e02-logika-timing-napiecie/tabela_scen.md`
ZAKAZANE BEZWZGLEDNIE: `scenariusze/` (G1), `autobot/`, `docs/przeglad-2026-11-27/`, `docs/rozbieznosci/`, katalog tematu E01, E03 i Planify jako przedmiot analizy, polecenia git zmieniajace stan, sekrety.

ZRODLO ROZSTRZYGAJACE: `scenariusze/ZERO_mini_serial_E02_EWA_rev.md` (po imporcie ZERO-BAZA-001). MATERIAL WEJSCIOWY (rzad 4, do weryfikacji, nie do przepisywania): `docs/rozbieznosci/E02_audyt.md`, `docs/przeglad-2026-11-27/E02_*.md`, `ZERO_HANDOFF_2026-10-11.md` (w scratchpadzie archiwum).

MIEJSCE PRACY: `docs/analiza/ZERO-ANALIZA-002-e02-logika-timing-napiecie/`
BAZA:          HEAD po imporcie bazy

PLAN SPRAWDZENIA:
  1. S-A1 cytaty — proba i wszystkie KRYTYCZNE/WYSOKIE sprawdzone `grep -n` / `sed -n` w pliku scenariusza
  2. S-A2 timing — przeliczenie od zera
  3. S-A3 napiecie — pokrycie 100% scen (z numeracja pokrecona: 3B, 5A, 6A..), uzasadnienia z tekstu
  4. S-A4 statusy ustalen wejsciowych (w tym lista 14 miejsc "bez mezczyzn")
  5. S-A5 allowlista i hash `scenariusze/`; S-A6 propozycje; S-A7 kompletnosc; S-A8 raport; S-A9 zrodla

RUNDA: 0 z 3
