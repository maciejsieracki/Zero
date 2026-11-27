# E01 ADAM: beaty 7 s i rozpiska sekundowa (notatki z przeglądu, tylko odczyt)

Data przeglądu: 2026-11-27. Źródła (wszystkie w R, nic nie zmieniano):
- R/ZERO_mini_serial_E01_ADAM_rev.md (scenariusz, 14 scen + Zero Day + sc. 15)
- R/ZERO_produkcja_flow/ZERO_E01_Scena{2..12}_beaty_7s_ENG.md, ZERO_E01_BlokP{1..4}_..., ZERO_E01_Wstawka_T-{10,7,5,1}_..., ZERO_E01_ZeroDay_...
- R/ZERO_produkcja_flow/ZERO_E01_rozpiska_sekundowa.md (1581 linii)
- R/ZERO_HANDOFF_2026-10-11.md (§1 długość, §2 kanon, §4 audyt, §7 reguły Flow)
- Scena 1 (ZERO_Scena1_beaty_7s_ENG.md) tylko odnotowana, bez oceny (pokryta przez Clip00-11 / v4).

## A. Mapa pokrycia (scena -> plik beatów -> beaty -> czas)

Czas deklarowany = scenariusz (nagłówek sceny). Czas beatów = liczba beatów x 7 s.

| Pozycja | Czas deklarowany | Plik beatów | Beaty | Czas beatów | Pokrycie | Status |
|---|---|---|---|---|---|---|
| Sc 1 | 3,5 min (210 s) | ZERO_Scena1_beaty_7s_ENG.md | 12 (0-11) | 84 s | 40% | poza oceną (Clip00-11) |
| Sc 2 | 1,5 min (90 s) | Scena2 | 12 | 84 s | 93% | OK |
| P1 | 4 min (240 s) | BlokP1 | 17 | 119 s | 50% | OK, 1 utrata setupu (patrz D) |
| Sc 3 | 2,5 min (150 s) | Scena3 | 9 | 63 s | 42% | OK |
| Sc 4 | 3 min (180 s) | Scena4 | 14 | 98 s | 54% | OK |
| WT T-10 | 0,75 min (45 s) | Wstawka_T-10 | 4 (0-3) | 28 s | 62% | błędna notka o miejscu |
| Sc 5 | 2 min (120 s) | Scena5 | 14 | 98 s | 82% | OK |
| P2 | 4 min (240 s) | BlokP2 | 25 | 175 s | 73% | niespójne (język Aga) |
| Sc 6 | 2 min (120 s) | Scena6 | 14 | 98 s | 82% | OK |
| WT T-7 | 1 min (60 s) | Wstawka_T-7 | 6 | 42 s | 70% | duplikat T-10 (beaty 2-4) |
| P3 | 5 min (300 s) | BlokP3 | 30 | 210 s | 70% | niespójne (brakujące linie, b11) |
| Sc 7 | 3 min (180 s) | Scena7 | 11 | 77 s | 43% | OK |
| Sc 8 | 1,5 min (90 s) | Scena8 | 6 | 42 s | 47% | niespójne (język, dodana kwestia) |
| WT T-5 | 1 min (60 s) | Wstawka_T-5 | 5 | 35 s | 58% | kolizja z Sc 10 |
| P4 | 3,5 min (210 s) | BlokP4 | 11 | 77 s | 37% | OK |
| Sc 9 | 3 min (180 s) | Scena9 | 12 | 84 s | 47% | niespójne (kanon Karoliny) |
| Sc 10 | 2,5 min (150 s) | Scena10 | 9 | 63 s | 42% | niespójne (kanon, kolizja z T-5) |
| Sc 11 | 3,5 min (210 s) | Scena11 | 10 | 70 s | 33% | OK |
| Sc 12 | 5 min (300 s) | Scena12 | 17 | 119 s | 40% | OK (A5 audytu nieusunięte) |
| Sc 13 | 2 min (120 s) | BRAK PLIKU | 0 | 0 s | 0% | LUKA |
| WT T-1 | 0,75 min (45 s) | Wstawka_T-1 | 3 | 21 s | 47% | niespójne (wiek Wolskiej) |
| Sc 14 Zero Day | 4 min (240 s) | ZeroDay | 16 | 112 s | 47% | naruszenie (muzyka w Flow) |
| Sc 15 statek | 1,5 min (90 s) | BRAK PLIKU | 0 | 0 s | 0% | LUKA (także brak w rozpisce) |

## B. Sumy i długość

- Beaty E01 bez Sc 1: 245 = Sc 2-12 (128) + bloki (83) + wstawki (18) + Zero Day (16). 245 x 7 s = 1715 s = 28:35.
- Z Sc 1 (12 beatów): 257 beatów = 1799 s = 29:59.
- Deklarowany czas (scenariusz, Sc 1-15 + bloki + wstawki): 3630 s = 60:30. Nagłówek scenariusza: "ok. 60 minut". Handoff §1: "E01 ~65 min". Rozbieżność celu: 60 vs 65.
- Pokrycie beatami: 1799/3630 = ~50%.
- Do 60:30 przy 7-s beatach potrzeba ~519 beatów (przy 65 min ~557), czyli ~260-300 beatów więcej niż jest.
- Metoda B (Save frame -> Start Image) tworzy łańcuch: beat n zależy od ostatniej klatki beatu n-1. Generowanie w obrębie sceny jest szeregowe; sceny można robić równolegle.
- Koszt (szacunek, brak danych o przepustowości Flow): 257 klipów w pierwszym przebiegu; każdy retake to kolejna generacja. Przy 2 generacjach na klip ok. 500 generacji. Założenie, nie pomiar.
- Do dopisania: Sc 13 (~17 beatów, 120 s) i Sc 15 (~13 beatów, 90 s). Razem ~30 beatów.

## C. Ciągłość (c)

1. Karolina, wygląd: beaty Sc 9 i Sc 10 mają "jasne włosy, bluza" (Sc 9 l.12-13; Sc 10 l.12). Kanon Flow (handoff §7 l.241, l.256): "ciemne włosy, zielona kurtka, BEZ swetra, gołe dłonie". Sc 14 (Zero Day) ma tylko "bluza". Zielona kurtka nie pojawia się w żadnym pliku beatów E01 (Sc 2-14).
2. Michał: jednodinozaurowy sweter zgodny (Sc 10 l.13, l.994 scen.; ZD l.181). Pozycja L/P nie jest zapisana w plikach Sc 2-14, więc nie da się jej tu zweryfikować.
3. Tło: beaty Sc 2-14 nie zawierają deklaracji "tło statyczne". Plik Sc 1 odsyła do "Instrukcji dla agenta" i tego nie robi. Sc 2-14 nie mają tego odesłania.
4. Muzyka: jedyny cue muzyczny w beatach to Zero Day (nagłówek l.19, l.21; beat 1 l.32; beat 16 l.136). Handoff §7 l.266: "muzyka jako osobna warstwa (NIE w klipach Flow)". Sprzeczność z regułą "Bez muzyki (tylko ambient ulicy)" (§7 l.260). Scenariusz Sc 14 wymaga muzyki.
5. Scenariusz Sc 1 (l.65) i rozpiska Sc 1 (l.12) mówią "Muzyka: ciepła, ambientowa". Konflikt z regułą "bez muzyki". Poza zakresem, odnotowuję.
6. Chronologia: WT T-5 (scen. l.849-854; beat 4): Michał 09:47 "Jestem w szpitalu... Przyjdź dzisiaj?" (dzień T-5). Sc 10 (T-5, popołudnie; beat 1 l.31-34; rozpiska l.1117): "Ostatnia wiadomość: wczoraj wieczór. Po wczoraj: nic." Sprzeczność w tym samym dniu. Dodatkowo WT T-5 jest w montażu przed P4/Sc 9 (T-6), więc montaż cofa się w czasie.
7. Wolska: WT T-1 constants l.14 "ok. 48 lat". Kanon: E02 "Katarzyna ~58", E03 "Anna 51" (handoff §2 l.85; §4 A2 l.151-157). Trzy różne wersje.
8. Pozycja WT T-10: notka beatów l.48 mówi "między Sceną 3 a Sceną 4". Scenariusz (l.351) i rozpiska (l.401) dają: po Sc 4, przed Sc 5.
9. Język Very/Aga (konwencja niespójna):
   - Sc 3 beaty: "po norwesku (angielski voice-over)".
   - Sc 8 beaty l.12 constants: "po angielsku z norweskim akcentem"; scenariusz nota (l.54-55): "w scenach teraźniejszości (Oslo) mówi do siebie po norwesku, napisy polskie".
   - P3 beaty: constants l.12 "Vera mówi po polsku bez akcentu", ale dialog EN z akcentem; reguła l.21: "sceny z norweskim (Aga/Vera) mówione po angielsku z akcentem", scenariusz: po norwesku z napisami PL.
   - P2 beaty: Aga do Very po norwesku (zgodne ze scen.); Aga do taty: constants l.12 "po polsku", reguła l.26 "po angielsku", beat 22 "po angielsku". Rozpiska l.566: "po norwesku". Scenariusz: "Pappaaaaa. Jutro park?" (bez wskazania języka).
10. Sc 10: notka "Karolina mówi tylko do automatu" (l.19), ale w beatach Karolina nie mówi wcale.

## D. Naruszenia reguł i rozbieżności dialogów (d)

Naruszenia reguł:
- N1 Jedna osoba mówi naraz: P3 beat 11 (l.99-104) ma dwie kwestie w jednym beacie: "Mom." (Aga) i "Aga. Eat your soup." (Vera), "dwie kwestie, 7 s łącznie".
- N2 Długość beatu. Przyjęte 2,5-3 sł/s, czyli 7 s to ok. 17-21 słów. Linie powyżej tej granicy:
  - T-10 beat 1: 27 słów
  - T-7 beat 2: 24 słowa
  - P1 beat 11: 22 słowa
  - P2 beat 1: 23 słowa
  - P2 beat 8: 20 słów
  - P3 beat 27: 20 słów
  - Sc 7 beat 4: 19 słów
  - Zero Day beat 9: 18 słów (graniczne)
- N3 Muzyka w klipach Flow: Zero Day, patrz C4.
- N4 Stałe z kanonu (kurtka, włosy Karoliny): patrz C1.

Rozbieżności dialogów ze scenariuszem (zgodne: Sc 2, 4, 5, 6, 7, 9, 11, 12, P4, Zero Day, WT-5, WT-1 - sprawdzone linia po linii):
- D1 P3 beat 26-27: w scenariuszu jest Vera "Aga." i Aga "Co?" (l.735-741). W beatach brak obu kwestii.
- D2 P1 beat 6: scenariusz "Pan profesor... pan jest opiekunem naukowym?" (l.212-214). Beat 6 "You are... the supervisor?" usuwa "profesor". Beat 7 "Doctor. Not professor yet." traci setup.
- D3 Sc 8 beat 5: "Third case in Berlin." jako kwestia. Scenariusz: narracja (l.833-834). Dodana kwestia, do zatwierdzenia.
- D4 Sc 5 beat 9: "And? Does it remind you too?" Scenariusz: "I co? Przypomina?" (l.402). Dodane "you too".
- D5 WT-7 beaty 2-4: powtórzenie WT-10 beat 1-3 (WHO w Genewie, "nie ma podstaw do niepokoju", Gospodarka/Austria). Scenariusz WT-7 nie ma głosu prezenterki (l.588-603). Duplikat.
- D6 Sc 12 beat 9: "The girls are at your mom's neighbor's?" Błąd z audytu A5 (handoff l.164-165) przeniesiony bez poprawki. Decyzja otwarta.
- D7 Sc 8 beat 6: "Czarny ekran po 6-7 s". Czarny ekran nie jest w scenariuszu, opis niejasny.
- D8 Sc 3 beat 8: napis "T MINUS 14 DAYS" (scen.: "T MINUS 14 DNI"). Przy konwencji EN OK, ale trzeba wybrać.

## E. Rozpiska sekundowa (e)

- Dwie kolumny: "CZAS SCENY" (suma ujęć) i "PRZYJĘTY CZAS" (wpisany ręcznie, równy czasowi z scenariusza). Przyjęte nie są wyliczone z ujęć.
- Ujęcia sumują się do 1291 s = 21:31. Przyjęte (22 pozycje) = 3540 s = 59:00. Pokrycie ujęciami: 36%.
- Luki (ujęcia / przyjęte, s): Sc 1 84/210; Sc 2 35/90; P1 87/240; Sc 3 40/150; Sc 4 58/180; WT-10 25/45; Sc 5 59/120; P2 93/240; Sc 6 55/120; WT-7 28/60; P3 154/300; Sc 7 66/180; Sc 8 28/90; WT-5 44/60; P4 59/210; Sc 9 48/180; Sc 10 37/150; Sc 11 55/210; Sc 12 72/300; Sc 13 41/120; WT-1 19/45; Sc 14 104/240.
- Błąd w tabeli podsumowania: wiersze tabeli dają "sceny teraźniejszości" 2100 s = 35:00 (tabela podaje 28:15). Łącznie wiersze = 59:00 (tabela 52:15). Wniosek "krótszy o 7-8 min" opiera się na błędnej sumie. Przy wartościach przyjętych brakuje ~1 min. Przy wartościach z ujęć brakuje ~38 min.
- Sc 15 (statek widmo, 90 s) nie występuje w rozpisce. Tabela ma 22 pozycje, w tym Sc 14 jako ostatnią.
- Uwaga w konkluzji "Scena 13 pominięta w indeksie blokowym" jest nieaktualna: Sc 13 jest w tabeli (wiersz 20).
- Źródła rozpiski nieaktualne: "ZERO_mini_serial_E01_ADAM.md" (bez _rev), "ZERO_VEO3_E01_Scena1_v2.md" (teraz v4), data 2026-06-07. Dialogi w rozpisce po polsku, beaty po angielsku.
- Treść nieaktualna względem rev:
  - Sc 2: brak wymiany Marta-Tomek "koleżanka Agi... Marta ma na imię jak ja" (rev l.164-171; beat 8-10 tak). Rozpiska ma tylko pierwsze 4 kwestie.
  - P2 Ujęcie 4: "Pracowałam nad tym od trzech lat" (rev: "od wielu lat"; beat 9: "many years").
  - Sc 12: "u twojej mamy sąsiadki" (A5 audytu, nadal).
  - WT-7 pasek TVN24 w rozpisce: "PIERWSZE POTWIERDZONE PRZYPADKI W POLSCE - ŚMIERTELNOŚĆ ROŚNIE" (l.658). Nie ma w scenariuszu ani w beatach (beaty: "MORTALITY NEAR 100% IN HOSPITALIZED MEN", zgodnie ze scen.).
  - P3 Ujęcie 8: "Vera: Aga." i "Aga: Co?" są w rozpisce (l.794-795), a w beatach ich brak (D1).
  - Sc 14 w rozpisce: 'Aga "To niemożliwe"' i pozostałe kwestie zgodne z rev.
- Rozpiska zakłada czołówkę/napisy 2-3 min i muzykę 1-2 min, czego nie ma w żadnym pliku beatów. Plik czołówki (INTRO) jest wymieniony w handoffie, ale go nie sprawdzałem.

## F. Liczba beatów/klipów na scenę (f)

| Pozycja | Beaty (7 s) |
|---|---|
| Sc 1 | 12 |
| Sc 2 | 12 |
| Sc 3 | 9 |
| Sc 4 | 14 |
| Sc 5 | 14 |
| Sc 6 | 14 |
| Sc 7 | 11 |
| Sc 8 | 6 |
| Sc 9 | 12 |
| Sc 10 | 9 |
| Sc 11 | 10 |
| Sc 12 | 17 |
| Sc 13 | brak (ok. 17 wg czasu) |
| Sc 14 Zero Day | 16 |
| Sc 15 | brak (ok. 13 wg czasu) |
| P1 | 17 |
| P2 | 25 |
| P3 | 30 |
| P4 | 11 |
| WT T-10 | 4 |
| WT T-7 | 6 |
| WT T-5 | 5 |
| WT T-1 | 3 |
| RAZEM (z Sc 1, bez brakujących) | 257 |

## G. Rekomendacje (robocze)

1. Przeliczyć rozpiskę z beatów (nie z czasu scenariusza), poprawić sumy tabeli, dodać Sc 15, przepisać dialogi na rev.
2. Zdecydować długość: przy obecnych beatach E01 wychodzi ~30 min z 60 (lub 65). Potrzeba decyzji, czy skracać scenariusz, czy dopisywać beaty (~260-300 więcej).
3. Przed generowaniem domknąć brakujące pliki: Sc 13 i Sc 15. Zero Day: usunąć cue muzyczne z beatów Flow, muzykę dać w CapCut.
4. Ujednolicić kanon w beatach: Karolina (ciemne włosy, zielona kurtka, bez swetra) w Sc 9, 10, 14; czas wiadomości Michała (WT T-5 vs Sc 10); wiek Wolskiej; jedna reguła językowa dla scen norweskich.
5. Poprawić beaty: P3 b11 rozbić na dwa beaty; P3 b26-27 dodać brakujące linie; linie >21 słów rozbić; WT-7 b2-4 usunąć lub zamienić (duplikat WT-10); P1 b6 przywrócić "pan profesor".
