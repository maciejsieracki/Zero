# ZERO-PROD-003-scena1-kling-tekst

WYZWALACZ:  decyzja wlasciciela ECHO-038 (2026-11-28): wersja pliku Sceny 1 dla Klinga do zalaczenia lub wklejenia jako zwykly tekst, nie tylko dla API. Zalezy od zamknietego ZERO-PROD-002 (zweryfikowane zrodlo `docs/produkcja/ZERO-PROD-002-scena1-kling/scena1_kling.md`).
GOAL:       Istnieje zweryfikowany plik tekstowy (.txt) z cala trescia roboczego pliku Sceny 1 dla Klinga 4.0 w formie do zalaczenia lub wklejenia (bez tabel i kodu), z osia czasu w ms jako lista linii, gotowymi promptami EN w blokach, instrukcja uzycia w aplikacji i sekcja "Co jeszcze dolozyc" — o tresci identycznej ze zrodlem, bez nowych faktow.
KONIEC:     PRAWDA gdy scenariusze S-T1..S-T4 przechodza. Zadna zmiana poza allowlista.

ZADANIE: z zatwierdzonego pliku `docs/produkcja/ZERO-PROD-002-scena1-kling/scena1_kling.md` (tylko odczyt) utworz `docs/produkcja/ZERO-PROD-002-scena1-kling/scena1_kling_tekst.txt` (UTF-8, zakonczenia linii LF; znaki diakrytyczne w tekscie polskim dozwolone). Wymagania: 1) czysty tekst, bez tabel markdown i bez blokow kodu; naglowki jako linie z ===== i -----; 2) na poczatku instrukcja uzycia po polsku (co zalaczyc/wkleic i w jakiej kolejnosci; jak ustawic dlugosc 3-30 s, proporcje 16:9, Elements postaci, ostatnia klatke poprzedniego klipu jako pierwsza klatke, pobranie klipu od razu; kontrola po klipie); 3) os czasu: kazde zdarzenie jedna linia w formacie `[start ms - koniec ms | klatki | typ | mowca] opis / kwestia`; 4) prompty ujec EN w blokach `>>>> CLIP n — POCZATEK PROMPTU` ... `<<<< CLIP n — KONIEC PROMPTU` z podana liczba znakow bloku, dlugoscia klipu i wskazaniem Elements/pierwszej klatki; 5) sekcja kontroli (weryfikacja, tolerancja) i "Co jeszcze dolozyc" przepisane; 6) limit dlugosci pola promptu Klinga w aplikacji: BRAK DANYCH w zatwierdzonych badaniach — napisz, ze trzeba go sprawdzic, i dla kazdego bloku podaj liczbe znakow oraz propozycje skrotu w razie potrzeby (bez zmiany tresci faktycznej); 7) jesli plik zrodlowy zawiera opcje MCP i API, w pliku tekstowym zostaw tylko krotka sekcje "Dla zaawansowanych" z nazwami narzedzi, bez endpointow w tresci roboczej; 8) zachowaj oznaczenia propozycji i granice precyzji (model nie gwarantuje milisekundy).

REGULA PRZECIW SAMOOSZUKIWANIU:
 - Zakaz nowych faktow, kwestii, parametrow i zdarzen; tresc tylko ze zrodla; zmiana formy, nie sensu.
 - Zakaz skracania osi czasu ("itd.", "..."); liczba zdarzen, klipow, promptow i kwestii identyczna ze zrodlem.
 - Zakaz uznania, ze blok miesci sie w polu promptu aplikacji (limit nieznany).
 - Zakaz edycji zrodla, zakaz sieci, kont, kluczy i wywolan API, zakaz rankingu i rekomendacji narzedzia (ECHO-027); pliki pomocnicze i skrypty tylko w scratchpadzie sesji.

PROCEDURA NAPRAWCZA PRZY FAIL: Evaluator numeruje zarzuty; Operator odpowiada PRZYJMUJE/ODRZUCAM z dowodem; po werdykcie NAPRAW poprawia tylko wskazane miejsca.

ALLOWLISTA:
  - `docs/produkcja/ZERO-PROD-002-scena1-kling/scena1_kling_tekst.txt` (nowy plik)
ZAKAZANE BEZWZGLEDNIE: `scenariusze/`, `autobot/`, `docs/analiza/`, `docs/research/*`, `docs/produkcja/ZERO-PROD-002-scena1-kling/scena1_kling.md` (tylko odczyt), pliki wejsciowe (uploads, archiwum), polecenia git zmieniajace stan (poza rola Integration), sekrety, siec.

MIEJSCE PRACY: `docs/produkcja/ZERO-PROD-002-scena1-kling/`
BAZA:          HEAD galezi roboczej (po integracji ZERO-PROD-002)
OBIEG:         Operator -> Evaluator (10 punktow) -> Obrona przy zarzutach -> Final Control (per zarzut) -> Integration

RUNDA: w kolejce (po ZERO-PROD-002); rundy 1-3 z 3; licznik w rejestrze aktualizuje orkiestrator po zakonczeniu workflow
