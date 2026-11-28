# ZERO-PLAN-002-pakiet-produkcyjny

WYZWALACZ:  decyzja wlasciciela ECHO-039 (2026-11-28): rozpisac wszystko, co potrzebne do stworzenia filmu — wszystkie pliki, jak reżyser — i co dostarczyc modelowi (Kling 4.0), zeby wiedzial, jak stworzyc sceny.
GOAL:       Istnieje zweryfikowany dokument "Pakiet produkcyjny ZERO": pelny katalog plikow i materialow potrzebnych do wygenerowania i zmontowania odcinkow (fundament serialu, pliki sceny, zarzadzanie produkcja, postprodukcja, zarzadzanie decyzjami i wersjami), dla kazdego pliku nazwa, cel, zawartosc, format, kto tworzy, zrodla, zaleznosci, stan (istnieje / czesciowy / brak) i priorytet, z kolejnoscia prac i lista decyzji wlasciciela — oparty na rzeczywistym stanie repozytorium i archiwum oraz zatwierdzonych badaniach.
KONIEC:     PRAWDA gdy scenariusze S-L1..S-L5 przechodza. Zadna zmiana poza allowlista.

WEJSCIA (tylko odczyt): repozytorium (`scenariusze/`, `docs/`, `autobot/`, `PLAN_WDROZENIA_ZERO.md`); kopia archiwum w /tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/zero-extract/Zero/ZERO_DO_PRZENIESIENIA/ (m.in. ZERO_E01_produkcja/ — 8 dokumentow, ZERO_produkcja_flow/ — beaty, rozpiska sekundowa, instrukcje, metoda A/B); pliki wgrane przez wlasciciela w /root/.claude/uploads/3337db06-529b-5b00-81d6-a0a7013a451d/; raport `docs/analiza/ZERO-ANALIZA-003-produkcja-e01-spojnosc/raport.md` (luki i rozbieznosci; jesli jeszcze go nie ma w repozytorium, temat nie startuje); plik Sceny 1 `docs/produkcja/ZERO-PROD-002-scena1-kling/scena1_kling.md` (wzor formatu pliku sceny); badania RESEARCH-001..008 (Kling: parametry, Elements, glosy, MCP/API, polski, jakosc).

ZADANIE: utworz `docs/produkcja/ZERO-PLAN-002-pakiet-produkcyjny/pakiet_produkcyjny.md` (po polsku; nazwy techniczne bez znakow diakrytycznych), podejscie rezysera: co model musi dostac, zeby wiedziec jak zrobic sceny. Struktura:
 1. Cel i zasada pakietu (jedno zrodlo prawdy; wsad dla modelu = male, scisle pliki; kanon dialogow bez zmian; polski glos w montazu; granice precyzji ms).
 2. Katalog plikow w pieciu kategoriach: A fundament serialu; B pliki sceny; C zarzadzanie produkcja; D postprodukcja; E zarzadzanie (decyzje, wersje, testy). Dla kazdego pliku tabela: ID (np. A-03), nazwa i sciezka docelowa, cel, zawartosc (pola), format (md/txt/docx/obrazy/audio), kto tworzy (workflow / wlasciciel / zewnetrzne narzedzie), zrodla wejsciowe, zaleznosci, stan i dowod (sciezka w repozytorium lub archiwum, albo "brak"), priorytet (P0 pilot, P1 scena 1, P2 E01, P3 E02), orientacyjna pracochlonnosc.
 3. Reżyserskie arkusze wzorcowe: pelny szablon pliku sceny (pola: cel, beaty, wejscie/wyjscie, przejscia, lista ujec z oska czasu w ms, dialog PL/EN, sygnaly dzwiekowe, ciaglosc, paczka promptow, referencje) oparty na formacie z `scena1_kling.md`.
 4. Co dostarczyc modelowi (Kling 4.0): minimalny zestaw na klip (prompt, Elements, pierwsza klatka, ustawienia, negatywy) i co zostaje poza modelem (muzyka, polski glos, napisy, przejscia).
 5. Graf zaleznosci i kolejnosc prac: pilot (19 s rozmowa o swetrze) -> Scena 1 -> reszta E01 -> E02; punkty kontrolne; kryteria akceptacji klipu.
 6. Luki z ANALIZA-003 i ich wplyw na pakiet; lista decyzji wlasciciela jako pytania ABC (m.in. styl film/manga, wyglad Karoliny, czas scen i luka 126 s w Scenie 1, narzedzie do polskiego glosu, muzyka, rzeczywiste marki, prawa i filtry tresci).
 7. Szacunek skali (liczba scen, ujec, klipow, kosztu probnego z RESEARCH-001/-005) z oznaczeniem niepewnosci.
 Bez rankingu i rekomendacji wyboru narzedzia (ECHO-027); elementy "od rezysera" oznacz jako PROPOZYCJA REZYSERSKA, kanon scenariusza bez zmian.

REGULA PRZECIW SAMOOSZUKIWANIU:
 - Zakaz twierdzen o stanie plikow bez sprawdzenia sciezki; status "istnieje" wymaga sciezki i krotkiego dowodu, status "brak" wymaga wyszukania w repozytorium i archiwum.
 - Zakaz dopisywania faktow kanonu (postaci, zdarzen, dialogow); decyzje kanoniczne i produktowe tylko jako pytania ABC (G2, G3).
 - Zakaz twierdzen o mozliwosciach Klinga z pamieci; tylko z zatwierdzonych badan z odnosnikiem albo BRAK DANYCH.
 - Zakaz rankingu i wyboru narzedzia (ECHO-027); zakaz nowych odczytow sieci, kont, kluczy, wywolan API i generowania wideo; zakaz edycji plikow wejsciowych i poza allowlista; pisz plik etapami.

PROCEDURA NAPRAWCZA PRZY FAIL: Evaluator numeruje zarzuty; Operator odpowiada PRZYJMUJE/ODRZUCAM z dowodem; po werdykcie NAPRAW poprawia tylko wskazane miejsca.

ALLOWLISTA:
  - `docs/produkcja/ZERO-PLAN-002-pakiet-produkcyjny/pakiet_produkcyjny.md` (nowy plik)
ZAKAZANE BEZWZGLEDNIE: `scenariusze/`, `autobot/`, `docs/analiza/`, `docs/research/*`, `docs/produkcja/ZERO-PROD-*` (tylko odczyt), pliki wejsciowe (uploads, archiwum), polecenia git zmieniajace stan (poza rola Integration), sekrety, siec.

MIEJSCE PRACY: `docs/produkcja/ZERO-PLAN-002-pakiet-produkcyjny/`
BAZA:          HEAD galezi roboczej (po integracji ANALIZA-003 i PROD-002)
OBIEG:         Operator -> Evaluator (10 punktow) -> Obrona przy zarzutach -> Final Control (per zarzut) -> Integration

RUNDA: w kolejce (po ANALIZA-003); rundy 1-3 z 3; licznik w rejestrze aktualizuje orkiestrator po zakonczeniu workflow
