# ZERO-RESEARCH-006-zestawienie-word

WYZWALACZ:  polecenie wlasciciela ECHO-029 (2026-11-27): zapisac zestawienie zbiorcze w Word i udostepnic do pobrania. RESEARCH-005 zamkniety (READY_FOR_DEPLOY, commit fb39254).
GOAL:       Istnieje zweryfikowany plik Word (.docx) o tresci identycznej z zatwierdzonym zestawieniem zbiorczym dostawcow wideo AI (RESEARCH-005), czytelny przy szerokich tabelach, bez zadnych zmian merytorycznych, rankingu ani rekomendacji.
KONIEC:     PRAWDA gdy scenariusze S-R23..S-R26 przechodza. Zadna zmiana poza allowlista.

ZADANIE: z pliku zrodlowego `docs/research/ZERO-RESEARCH-005-zestawienie-zbiorcze/zestawienie_zbiorcze.md` (tylko odczyt) wytworz `docs/research/ZERO-RESEARCH-005-zestawienie-zbiorcze/zestawienie_zbiorcze.docx`.
Wymagania:
 - Tresc 1:1 ze zrodla: naglowki (poziomy), akapity, listy, tabele (wszystkie wiersze i kolumny), pogrubienia i oznaczenia pewnosci bez zmian; polskie znaki w tresci zachowane; nic nie dopisujesz, nie skracasz i nie przestawiasz.
 - Tytul dokumentu: pierwszy naglowek ze zrodla; metadane: autor "Claude Code", brak danych osobowych.
 - Orientacja pozioma (A4 poziomo, ewentualnie A3 poziomo, jesli A4 nie daje czytelnosci); marginesy waskie (1,5-2 cm); czcionka tabel 7-8 pt, tekstu 10 pt; tabele z obramowaniem, wiersz naglowkowy pogrubiony, z tlem, i powtarzany na kolejnych stronach; kolumny o rozsadnych szerokosciach, tekst zawijany, bez obcinania.
 - Spis tresci na poczatku (naglowki poziomu 1-3) lub, jesli niemozliwy bez pola TOC, lista sekcji z numerami.
 - Narzedzia lokalne: pandoc, python-docx i LibreOffice sa zainstalowane; skrypty i pliki tymczasowe zapisuj WYLACZNIE w katalogu roboczym sesji (scratchpad: /tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/word-006/), nie w repozytorium.
 - Samokontrola techniczna (nie ocena): otworz plik python-docx, policz naglowki, tabele i wiersze; skonwertuj do PDF (soffice --headless --convert-to pdf) i obejrzyj kilka stron jako obrazy.

REGULA PRZECIW SAMOOSZUKIWANIU:
 - Zakaz zmiany tresci zrodla; zakaz dopisywania wnioskow, opinii, rankingu, podsumowan (ECHO-027).
 - Zakaz uznania, ze tabele sie mieszcza, bez wyrenderowania i obejrzenia stron.
 - Zakaz uzycia sieci i zewnetrznych uslug; zakaz edycji zrodlowego .md i innych plikow repozytorium.
 - Zakaz skracania tabel ("itd.", "...") i gubienia kolumn.

PROCEDURA NAPRAWCZA PRZY FAIL: Evaluator numeruje zarzuty (miejsce, punkt listy, reprodukcja). Operator (w obronie) odpowiada PRZYJMUJE/ODRZUCAM z dowodem; po werdykcie NAPRAW poprawia tylko wskazane miejsca.

ALLOWLISTA:
  - `docs/research/ZERO-RESEARCH-005-zestawienie-zbiorcze/zestawienie_zbiorcze.docx` (nowy plik)
ZAKAZANE BEZWZGLEDNIE: `scenariusze/`, `autobot/`, `docs/analiza/`, `docs/audiobook/`, `docs/proces/`, `docs/przeglad-2026-11-27/`, `docs/rozbieznosci/`, `docs/research/ZERO-RESEARCH-001-*`, `-002-*`, `-003-*` oraz `zestawienie_zbiorcze.md` (tylko odczyt), polecenia git zmieniajace stan (poza rola Integration), sekrety, siec.

MIEJSCE PRACY: `docs/research/ZERO-RESEARCH-005-zestawienie-zbiorcze/` (wytwor) i scratchpad sesji (pliki pomocnicze)
BAZA:          HEAD galezi roboczej
OBIEG:         Operator -> Evaluator (10 punktow) -> Obrona przy zarzutach -> Final Control (per zarzut) -> Integration

RUNDA: w toku (rundy 1-3 z 3; licznik w rejestrze aktualizuje orkiestrator po zakonczeniu workflow)
