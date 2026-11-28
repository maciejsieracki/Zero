# ZERO-UJECIA-009-wstawka-t7

WYZWALACZ:  decyzja wlasciciela ECHO-044 (2026-11-28): dorobic podzial wszystkich scen na ujecia; ta pozycja = WSTAWKA MEDIALNA 2 (T-7) (Przebitka ekranow, kolejki, telefon Karoliny).
GOAL:       Istnieje zweryfikowany plik `docs/produkcja/ujecia/UJ10_wstawka_t7.md`: pelny podzial sekwencji "WSTAWKA MEDIALNA 2 (T-7)" odcinka E01 serialu ZERO na ujecia (kazde zdarzenie i kazda kwestia scenariusza w ujeciu, komplet pol ujecia, czasy w sekundach z sumami, przejscia i kadry bez postaci), z jawnymi rozbieznosciami zrodel i czasu, luki i propozycje reżyserskie oznaczone PROPOZYCJA, pytania ABC do wlasciciela, bez nowych faktow kanonu.
KONIEC:     PRAWDA gdy scenariusze S-J1..S-J5 przechodza (opisy w `autobot/SCENARIUSZE.md`, sekcja "Tematy ZERO-UJECIA-001..023"). Zadna zmiana poza allowlista.

WEJSCIA (tylko odczyt; hierarchia: scenariusz E01 rank 1 > decyzje wlasciciela ECHO > dokumenty produkcyjne i raport ANALIZA-003 rank 4; sprzecznosci zapisuj jawnie z dwoma cytatami, nie rozstrzygaj):
 - `scenariusze/ZERO_mini_serial_E01_ADAM_rev.md` (znajdz sekwencje po naglowku i etykiecie CZAS) oraz `MANIFEST.sha256`; `docs/analiza/ZERO-ANALIZA-001-e01-logika-timing-napiecie/` (raport.md, tabela_scen.md); `docs/analiza/ZERO-ANALIZA-003-produkcja-e01-spojnosc/` (raport.md — niezacommitowany, po kontroli Evaluatora, uzyj jako wejscia rzedu 4);
 - rozpiska sekundowa E01 w archiwum: /tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/zero-extract/Zero/ZERO_DO_PRZENIESIENIA/ZERO_produkcja_flow/ZERO_E01_rozpiska_sekundowa.md (sekcja tej sekwencji: ujecia i czasy), beaty 7 s tej sekwencji w /tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/zero-extract/Zero/ZERO_DO_PRZENIESIENIA/ZERO_produkcja_flow/, dokumenty /tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/zero-extract/Zero/ZERO_DO_PRZENIESIENIA/ZERO_E01_produkcja/ (03_opisy_wizualne_scen, 04_dzwiek_i_muzyka, 05_inserty_closeup, 06_przejscia_scen, 07_podtekst_dialogowy, 02_charakterystyki_postaci) oraz pliki wgrane przez wlasciciela w /root/.claude/uploads/3337db06-529b-5b00-81d6-a0a7013a451d/; plik handoff /tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/zero-extract/Zero/ZERO_DO_PRZENIESIENIA/ZERO_HANDOFF_przekazanie.md;
 - `autobot/DECYZJE.md` (ECHO-020, 027, 036, 037, 040, 041, 044), `docs/produkcja/ZERO-PROD-002-scena1-kling/scena1_kling.md` (wzor formatu ujec i osi czasu Sceny 1), `docs/research/ZERO-RESEARCH-001-*/kling.md` i `-003-*/kling.md` (granice Klinga).
 - tej sekwencji dotycza: beaty: ZERO_E01_Wstawka_T-7_beaty_7s_ENG.md; deklarowany czas wg tabeli rozpiski: odczytaj z tabeli rozpiski (sekcja "LACZNY CZAS"/tabela sekwencji).

ZADANIE: utworz plik `docs/produkcja/ujecia/UJ10_wstawka_t7.md` (po polsku; nazwy techniczne bez znakow diakrytycznych; prompty i dialogi EN do wklejenia po angielsku). Zawartosc: (1) naglowek: ID, data 2026-11-28, sekwencja, miejsce, czas wg scenariusza (etykieta CZAS), wg tabeli rozpiski i wg ANALIZA-001, zrodla z hashami SHA-256; (2) LISTA ZDARZEN I KWESTII sekwencji wyciagnieta ze scenariusza (z liniami zrodla) — podstawa kontroli pelnosci; (3) TABELA UJEC: id, typ (z postaciami / bez postaci / insert / ekran-grafika), plan i kamera, obsada i pozycje (L/P), akcja, kwestie (mowca, PL kanon doslownie, EN propozycja), dzwiek (ambient, SFX, cisza), czas od-do w s (kroki do 3 s) i dlugosc, przejscie wyjsciowe, zrodlo (linie scenariusza, ujecie rozpiski lub beat), uwagi ciaglosci; (4) sumy czasow i porownanie z czasem deklarowanym; (5) przejscia wejsciowe i wyjsciowe z 06_przejscia_scen i rozbieznosci; (6) kadry bez postaci i inserty ze zrodel oraz PROPOZYCJE dodatkowych kadrow (miejsce, czas, opis do promptu); (7) luki i rozbieznosci (czas, kolejnosc, wiek, imiona, wyglad), pytania ABC do wlasciciela; (8) powiazania z plikami pakietu.  

REGULA PRZECIW SAMOOSZUKIWANIU:
 - Najpierw z samego scenariusza wyciagnij pelna liste zdarzen i kwestii sekwencji (z liniami), potem buduj ujecia tak, by kazda pozycja listy trafila do ujecia; zakaz pomijania kwestii i zdarzen.
 - Zakaz dopisywania faktow kanonu (zdarzen, postaci, kwestii); kanon dialogow doslownie (G2); EN tylko jako PROPOZYCJA; kadry spoza scenariusza (bez postaci, przejscia, oddech) tylko jako PROPOZYCJA REZYSERSKA z oznaczeniem.
 - Zakaz wymyslania tresci, by "dociagnac" deklarowany czas sekwencji; jesli scenariusz ma mniej tresci, zapisz luke i podaj, co moze ja wypelnic (propozycje), bez wlaczania ich do kanonicznych ujec.
 - Zakaz twierdzen o mozliwosciach Klinga z pamieci; zakaz sieci, kont, kluczy, wywolan API, rankingu i wyboru narzedzia (ECHO-027); zakaz edycji plikow wejsciowych i poza allowlista; pliki pomocnicze tylko w scratchpadzie; pisz plik etapami.
 - Zakres: jedna sekwencja E01; E03 poza zakresem; ms nie sa wymagane (czasy w sekundach, w krokach do 3 s).

PROCEDURA NAPRAWCZA PRZY FAIL: Evaluator numeruje zarzuty; Operator odpowiada PRZYJMUJE/ODRZUCAM z dowodem; po werdykcie NAPRAW poprawia tylko wskazane miejsca.

ALLOWLISTA:
  - `docs/produkcja/ujecia/UJ10_wstawka_t7.md` (nowy plik)
ZAKAZANE BEZWZGLEDNIE: `scenariusze/`, `autobot/`, `docs/analiza/`, `docs/research/*`, inne pliki `docs/produkcja/` (tylko odczyt), pliki wejsciowe, polecenia git zmieniajace stan (poza rola Integration), sekrety, siec.

MIEJSCE PRACY: `docs/produkcja/ujecia/`
BAZA:          HEAD galezi roboczej
OBIEG:         Operator -> Evaluator (10 punktow) -> Obrona przy zarzutach -> Final Control (per zarzut) -> Integration (osobny commit na temat, ECHO-042)

RUNDA: w kolejce, Sonnet 5.5 (ECHO-042); rundy 1-3 z 3; licznik w rejestrze aktualizuje orkiestrator po zakonczeniu workflow
