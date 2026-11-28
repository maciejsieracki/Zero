# ZERO-PAKIET-011-rejestr-decyzji

WYZWALACZ:  decyzja wlasciciela ECHO-040 (2026-11-28): rozpisac pakiet produkcyjny; ta pozycja = punkt 22 ("Rejestr decyzji kanonicznych"); fala 1.
GOAL:       Istnieje zweryfikowany plik `docs/produkcja/pakiet/E01_rejestr_decyzji_kanonicznych.md`: Rejestr decyzji kanonicznych dla odcinka E01 serialu ZERO (narzedzie docelowe Kling 4.0), kompletny wg specyfikacji zlecenia, oparty na scenariuszu E01 i zatwierdzonych materialach, z propozycjami reżyserskimi oznaczonymi jako PROPOZYCJA, jawnymi rozbieznosciami zrodel i pytaniami ABC do wlasciciela, bez nowych faktow kanonu.
KONIEC:     PRAWDA gdy scenariusze S-D1..S-D5 (oraz S-D6 dla pozycji sceny 1) przechodza; opisy w `autobot/SCENARIUSZE.md`, sekcja "Tematy ZERO-PAKIET-001..022". Zadna zmiana poza allowlista.

WEJSCIA (tylko odczyt; hierarchia przy sprzecznosci: scenariusz E01 rank 1 > decyzje wlasciciela ECHO > raport ANALIZA-003 i dokumenty produkcyjne rank 4; sprzecznosci zapisuj jawnie z dwoma cytatami, nie rozstrzygaj):
 - `scenariusze/ZERO_mini_serial_E01_ADAM_rev.md` i `MANIFEST.sha256`; `docs/analiza/ZERO-ANALIZA-001-e01-logika-timing-napiecie/` (raport.md, tabela_scen.md); `docs/analiza/ZERO-ANALIZA-003-produkcja-e01-spojnosc/` (raport.md, tabela_rozbieznosci.md — luki i rozbieznosci materialow produkcyjnych);
 - `autobot/DECYZJE.md` (ECHO-020, 027, 030, 031, 036, 037, 039, 040), `PLAN_WDROZENIA_ZERO.md`, `docs/przeglad-2026-11-27/`;
 - materialy produkcyjne: kopia archiwum /tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/zero-extract/Zero/ZERO_DO_PRZENIESIENIA/ (ZERO_E01_produkcja/ 8 dokumentow; ZERO_produkcja_flow/ — beaty, rozpiska sekundowa, instrukcje, metoda A/B, decyzje, repercusje, handoff) oraz pliki wgrane przez wlasciciela w /root/.claude/uploads/3337db06-529b-5b00-81d6-a0a7013a451d/;
 - badania Klinga: `docs/research/ZERO-RESEARCH-001-*/kling.md`, `-002-*/kling.md`, `-003-*/kling.md`, `-005-*/zestawienie_zbiorcze.md`, `-008-*/omni_vs_kling.md`;
 - zrodlo formatu pliku sceny: `docs/produkcja/ZERO-PROD-002-scena1-kling/scena1_kling.md` (jesli zamkniety).
 - pliki pakietu zatwierdzone wczesniej (jesli istnieja w `docs/produkcja/pakiet/`): odczytaj i zachowaj spojnosc; dla fali 1 sa to tylko pliki fundamentu zatwierdzone przed Toba.

ZADANIE: utworz plik `docs/produkcja/pakiet/E01_rejestr_decyzji_kanonicznych.md` (po polsku; nazwy techniczne bez znakow diakrytycznych; prompty i dialogi do wklejenia po angielsku). Zawartosc: Rejestr decyzji kanonicznych i produktowych E01: wszystkie otwarte decyzje z raportow ANALIZA-001 (D-01..D-15), ANALIZA-002 (dla E02, informacyjnie), ANALIZA-003 i PLAN_WDROZENIA (D1-D16) oraz konsultacji scenariuszowej, polaczone w jedna tabele: ID, pytanie, kontekst z cytatami, warianty A/B/C po dwa plusy i dwa minusy (propozycje), wplyw na pakiet i klipy, status (otwarta / rozstrzygnieta z numerem ECHO), kolejnosc rozstrzygania; osobno lista juz podjetych decyzji (ECHO-020 widz wie od E01 ze Vera jest matka Agi; ECHO-027 bez rankingu; ECHO-030/031 tylko najnowsze wersje; ECHO-036/037 Kling i os czasu w ms). Zadnych rozstrzygniec za wlasciciela.
 Na poczatku pliku: naglowek z ID tematu, data (2026-11-28), zakres, zrodla (lista plikow wejsciowych z hashami SHA-256) i legenda oznaczen (PROPOZYCJA REZYSERSKA, BRAK DANYCH, rozbieznosc zrodel). Na koncu: lista pytan ABC do wlasciciela, powiazania z innymi plikami pakietu i lista "Co jeszcze dolozyc".

REGULA PRZECIW SAMOOSZUKIWANIU:
 - Zakaz dopisywania faktow kanonu (imion, dat, zdarzen, dialogow); elementy "od rezysera" oznacz PROPOZYCJA REZYSERSKA; decyzje kanoniczne i produktowe tylko jako pytania ABC do wlasciciela (G2, G3); kanon dialogow bez zmian.
 - Kazda informacja kanoniczna ma zrodlo (plik i sekcja); sprzecznosci zrodel zapisuj jawnie z dwoma cytatami; obowiazuje scenariusz E01 i decyzje wlasciciela.
 - Zakaz twierdzen o mozliwosciach Klinga z pamieci; tylko z zatwierdzonych badan z odnosnikiem (plik i sekcja) albo BRAK DANYCH; precyzja do milisekundy to plan i kryterium kontroli, a nie gwarancja modelu.
 - Zakaz rankingu i wyboru narzedzia (ECHO-027); zakaz sieci, kont, kluczy, wywolan API i generowania wideo i obrazow; zakaz edycji plikow wejsciowych i poza allowlista; skrypty i pliki pomocnicze tylko w scratchpadzie sesji; pisz plik etapami (kilka dopisan).
 - Zakres: odcinek E01 (E03 poza zakresem); sceny: szczegolowo tylko Scena 1, pozostale sceny tylko na poziomie wymaganym przez dana pozycje (nie rozpisuj ich szczegolowo).

PROCEDURA NAPRAWCZA PRZY FAIL: Evaluator numeruje zarzuty (miejsce, punkt listy, reprodukcja); Operator (w obronie) odpowiada PRZYJMUJE/ODRZUCAM z dowodem; po werdykcie NAPRAW poprawia tylko wskazane miejsca.

ALLOWLISTA:
  - `docs/produkcja/pakiet/E01_rejestr_decyzji_kanonicznych.md` (nowy plik)
ZAKAZANE BEZWZGLEDNIE: `scenariusze/`, `autobot/`, `docs/analiza/`, `docs/research/*`, `docs/audiobook/`, `docs/proces/`, `docs/przeglad-2026-11-27/`, `docs/rozbieznosci/`, inne pliki `docs/produkcja/` (tylko odczyt), pliki wejsciowe (uploads, archiwum), polecenia git zmieniajace stan (poza rola Integration), sekrety, siec.

MIEJSCE PRACY: `docs/produkcja/pakiet/`
BAZA:          HEAD galezi roboczej
OBIEG:         Operator -> Evaluator (10 punktow) -> Obrona przy zarzutach -> Final Control (per zarzut); Integration zbiorczo po fali (jeden commit z hashami per plik)

RUNDA: w kolejce (fala 1); rundy 1-3 z 3; licznik w rejestrze aktualizuje orkiestrator po zakonczeniu workflow
