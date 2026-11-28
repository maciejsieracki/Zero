# ZERO-UJECIA-023-tabela-zbiorcza

WYZWALACZ:  decyzja wlasciciela ECHO-044 (2026-11-28): dorobic podzial wszystkich scen na ujecia; ta pozycja = tabela zbiorcza po zamknieciu ZERO-UJECIA-001..022 (001-022 = sekwencje, 023 = zbiorcza).
GOAL:       Istnieje zweryfikowana tabela zbiorcza `docs/produkcja/ujecia/UJ00_tabela_zbiorcza_ujec.md` wszystkich 23 sekwencji E01 podzielonych na ujecia (Scena 1 wg ZERO-PROD-002 w ms, pozostale wg plikow `docs/produkcja/ujecia/UJ02..UJ23`): liczba ujec i sum sekund per sekwencje i razem, zestawienie z czasem deklarowanym, lista luk, brakow i pytan ABC; liczby przeliczone od zera.
KONIEC:     PRAWDA gdy scenariusz S-J6 oraz S-J5 przechodza (opisy w `autobot/SCENARIUSZE.md`). Zadna zmiana poza allowlista. Temat startuje dopiero po zamknieciu ZERO-UJECIA-001..022.

WEJSCIA (tylko odczyt): `docs/produkcja/ujecia/UJ02..UJ23` (zatwierdzone), `docs/produkcja/ZERO-PROD-002-scena1-kling/scena1_kling.md`, rozpiska sekundowa i tabela sekwencji w archiwum /tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/zero-extract/Zero/ZERO_DO_PRZENIESIENIA/ZERO_produkcja_flow/ZERO_E01_rozpiska_sekundowa.md, `docs/analiza/ZERO-ANALIZA-001-*/tabela_scen.md`, `autobot/DECYZJE.md`.

ZADANIE: utworz `docs/produkcja/ujecia/UJ00_tabela_zbiorcza_ujec.md`: (1) tabela 23 wierszy: lp, sekwencja, miejsce, plik zrodlowy, liczba ujec, suma sekund, czas deklarowany (rozpiska), czas wg ANALIZA-001, roznica, typy ujec (z postaciami / bez postaci / insert / ekran) liczone; (2) sumy razem i procenty pokrycia; (3) lista luk (sekwencje z mniejsza trescia niz czas), brakow (beaty Sceny 13 i 15, rozbieznosc kolejnosci P1 i sceny 3) i niezgodnosci miedzy plikami UJ; (4) pytania ABC do wlasciciela (jak traktowac deklarowane czasy; czy dopuszczamy kadry spoza scenariusza; kolejnosc sekwencji); (5) mapa zalezen do kolejnych plikow pakietu (tracker, plan montazu, beaty).

REGULA PRZECIW SAMOOSZUKIWANIU:
 - Najpierw z samego scenariusza wyciagnij pelna liste zdarzen i kwestii sekwencji (z liniami), potem buduj ujecia tak, by kazda pozycja listy trafila do ujecia; zakaz pomijania kwestii i zdarzen.
 - Zakaz dopisywania faktow kanonu (zdarzen, postaci, kwestii); kanon dialogow doslownie (G2); EN tylko jako PROPOZYCJA; kadry spoza scenariusza (bez postaci, przejscia, oddech) tylko jako PROPOZYCJA REZYSERSKA z oznaczeniem.
 - Zakaz wymyslania tresci, by "dociagnac" deklarowany czas sekwencji; jesli scenariusz ma mniej tresci, zapisz luke i podaj, co moze ja wypelnic (propozycje), bez wlaczania ich do kanonicznych ujec.
 - Zakaz twierdzen o mozliwosciach Klinga z pamieci; zakaz sieci, kont, kluczy, wywolan API, rankingu i wyboru narzedzia (ECHO-027); zakaz edycji plikow wejsciowych i poza allowlista; pliki pomocnicze tylko w scratchpadzie; pisz plik etapami.
 - Zakres: jedna sekwencja E01; E03 poza zakresem; ms nie sa wymagane (czasy w sekundach, w krokach do 3 s).

ALLOWLISTA:
  - `docs/produkcja/ujecia/UJ00_tabela_zbiorcza_ujec.md` (nowy plik)
ZAKAZANE BEZWZGLEDNIE: wszystkie inne pliki (tylko odczyt), polecenia git zmieniajace stan (poza rola Integration), sekrety, siec.

MIEJSCE PRACY: `docs/produkcja/ujecia/`
OBIEG:         Operator -> Evaluator (10 punktow) -> Obrona przy zarzutach -> Final Control (per zarzut) -> Integration (osobny commit na temat, ECHO-042)

RUNDA: w kolejce (po UJECIA-001..022), Sonnet 5.5; rundy 1-3 z 3; licznik w rejestrze aktualizuje orkiestrator po zakonczeniu workflow
