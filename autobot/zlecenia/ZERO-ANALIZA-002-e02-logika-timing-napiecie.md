# ZERO-ANALIZA-002-e02-logika-timing-napiecie

WYZWALACZ:  decyzja wlasciciela ECHO-005 (zakres E01 i E02), ECHO-002 (rownolegle), ECHO-003 (propozycje brzmienia w raporcie); odblokowanie zaleznosci po ZERO-BAZA-001; slot zwolniony po zakonczeniu ZERO-ANALIZA-001. Data 2026-11-27.
GOAL:       Dla odcinka E02 istnieje zweryfikowany raport z analizy logiki, timingu i budowania napiecia: z doslownymi cytatami, numerami linii, waga, wariantami naprawy (PROPOZYCJE) i kolejnoscia poprawek.
KONIEC:     PRAWDA gdy scenariusze S-A1..S-A9 przechodza. Zadna zmiana poza allowlista.

ZADANIE: przeprowadz pelna analize odcinka E02 w trzech wymiarach: LOGIKA, TIMING, BUDOWANIE NAPIECIA.
1. Przeczytaj w calosci plik zrodlowy `scenariusze/ZERO_mini_serial_E02_EWA_rev.md` (Read partiami do konca; nic nie pomijaj).
2. MATERIAL WEJSCIOWY (rzad 4 — poszlaka, do zweryfikowania w pliku scenariusza, NIE do przepisywania): `docs/rozbieznosci/E02_audyt.md`; `docs/przeglad-2026-11-27/E02_scenariusz.md`; `docs/przeglad-2026-11-27/decyzje_i_konsultacje.md`; handoff `/tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/zero-unrar/Zero/ZERO_HANDOFF_2026-10-11.md` (sekcje 2-5). Wzor wykonania i formatu: raport E01 `docs/analiza/ZERO-ANALIZA-001-e01-logika-timing-napiecie/raport.md` i `tabela_scen.md` (zatwierdzony przez Final Control; mozna uzyc jako wzoru struktury, nie tresci).
3. Napisz `docs/analiza/ZERO-ANALIZA-002-e02-logika-timing-napiecie/raport.md` z sekcjami: (a) Podsumowanie: stan odcinka w 3 wymiarach, 10 najwazniejszych punktow, decyzje kanoniczne wymagane od wlasciciela; (b) LOGIKA: zweryfikowana, zdeduplikowana lista rozbieznosci — ID (zachowaj numeracje z audytu wejsciowego tam, gdzie dotyczy; nowe: N-xx), waga (KRYTYCZNA/WYSOKA/SREDNIA/NISKA), lokalizacja z numerem linii, dosowny cytat, na czym polega sprzecznosc, 1-3 warianty naprawy jako PROPOZYCJE, rekomendacja, skutki dla innych odcinkow i plikow produkcyjnych; (c) WERYFIKACJA USTALEN WEJSCIOWYCH: tabela ID -> POTWIERDZONE/OBALONE/ZAWEZONE/NIEZBADANE -> cytat i linia; (d) TIMING: tabela czasow scen (etykieta CZAS, naglowek, tabela czasow, suma policzona z wypisanymi skladnikami), analiza rytmu (proporcje blokow, dlugie odcinki statyczne, przyspieszenia i zwolnienia), wnioski i PROPOZYCJA metrazu per scena; (e) NAPIECIE: opisz kotwice skali 0/5/10, krzywa napiecia scena po scenie (ocena 0-10 z uzasadnieniem: cytat i linia), mapa informacji (co wie widz, co wiedza postacie, w kluczowych punktach), miejsca spadku napiecia, zbyt wczesne ujawnienia, kandydaci na cliffhangery, otwarcie i zakonczenie odcinka; propozycje (takze PROPOZYCJA nowego brzmienia kwestii tam, gdzie to ma sens — ECHO-003, granica G2); (f) kolejnosc rekomendowanych poprawek (zaleznosci) i lista decyzji kanonicznych dla wlasciciela. Na poczatku raportu wpisz jawna linie z ID i GOAL tematu.
4. Napisz `docs/analiza/ZERO-ANALIZA-002-e02-logika-timing-napiecie/tabela_scen.md`: kazda scena i blok odcinka (wg numeracji w pliku): numer | T lub godzina | czas z etykiety | czas wg tabeli czasow (jesli jest) | napiecie 0-10 | co wie widz | uwagi.
WSKAZOWKI DLA E02: numeracja scen jest pokrecona (PROLOG, 1, 1A, 2, 3, 3B, 4, 4A, 5A, 5, 5B, 6, 6A, 7, 7A, 6B, 6C, 8, 9, 10, 12A, 12, 13, 14, 16, 15, 17, 18, 19; brak 11) — w tabela_scen.md zachowaj numeracje z pliku i dodaj kolumne kolejnosci chronologicznej T+. Odcinek ma zasade produkcyjna "bez mezczyzn w kadrze" — uwzglednij liste miejsc lamiacych ja z audytu wejsciowego. Przy analizie napiecia zwroc uwage na dlugie sekwencje infrastrukturalne (PSE, mapy, narady) vs wydarzenia osobiste. PROPOZYCJE zapisuj jako zwykly tekst z etykieta PROPOZYCJA, nie w formacie doslownego cytatu (aby kontrola cytatow nie dawala falszywych alarmow).

REGULA PRZECIW SAMOOSZUKIWANIU (z faktycznie zaobserwowanych bledow tego projektu):
- Zakaz przepisywania ustalen z audytow, notatek i handoffu bez sprawdzenia w pliku scenariusza. W tym projekcie punkt A4 handoffu okazal sie bledny, a kilka ustalen audytu zostalo zawezonych. Status POTWIERDZONE wymaga cytatu skopiowanego z wyniku Read lub grep z numerem linii.
- Zakaz cytatow z pamieci i parafraz podawanych jako cytaty.
- Zakaz podawania sumy czasow bez wypisania skladnikow.
- Zakaz twierdzen naukowych, technicznych i branzowych (energetyka, siec, gaz) jako faktow bez oznaczenia NIEPOTWIERDZONE.
- Zakaz oceny napiecia bez wskazania zdarzenia z tekstu i bez opisanych kotwic skali.
- Zakaz wnioskow o innych odcinkach na podstawie fragmentow bez oznaczenia "na podstawie fragmentu". E03 nie jest przedmiotem analizy.
- Zakaz konczenia na liscie problemow: dla kazdego punktu KRYTYCZNEGO i WYSOKIEGO musza byc warianty naprawy.
- Zakaz edycji plikow poza allowlista; w szczegolnosci zakaz poprawiania scenariuszy.

PROCEDURA NAPRAWCZA PRZY FAIL: Evaluator numeruje zarzuty (miejsce i reprodukcja). Operator (w obronie) odpowiada na kazdy numer PRZYJMUJE/ODRZUCAM z dowodem; po werdykcie NAPRAW poprawia tylko wskazane miejsca raportu i zwraca raport. Nie przepisuje calosci.

ALLOWLISTA:
  - `docs/analiza/ZERO-ANALIZA-002-e02-logika-timing-napiecie/raport.md`
  - `docs/analiza/ZERO-ANALIZA-002-e02-logika-timing-napiecie/tabela_scen.md`
ZAKAZANE BEZWZGLEDNIE: `scenariusze/` (G1), `autobot/`, `docs/przeglad-2026-11-27/`, `docs/rozbieznosci/`, `docs/analiza/ZERO-ANALIZA-001-*`, `docs/research/`, `docs/proces/`, E03 i Planify jako przedmiot analizy, polecenia git zmieniajace stan (poza rola Integration), sekrety.

MIEJSCE PRACY: `docs/analiza/ZERO-ANALIZA-002-e02-logika-timing-napiecie/`
BAZA:          HEAD galezi roboczej (baza scenariuszy z MANIFEST.sha256)
OBIEG:         Operator -> Evaluator (10 punktow) -> Obrona przy zarzutach -> Final Control (per zarzut) -> Integration

RUNDA: 1 z 3
