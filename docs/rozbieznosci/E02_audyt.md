# ZERO — E02 „EWA" — krytyczny audyt rozbieżności

Data: 2026-11-27. Źródło: `R/ZERO_mini_serial_E02_EWA_rev.md` (2108 linii, przeczytane w całości),
R = `/tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/zero-unrar/Zero/`.
Do porównań: `R/ZERO_mini_serial_E01_ADAM_rev.md`, `R/ZERO_mini_serial_E03_ARES_rev.md`, `R/ZERO_HANDOFF_2026-10-11.md` (sekcje 2–5),
notatki `docs/przeglad-2026-11-27/E02_scenariusz.md` i `decyzje_i_konsultacje.md`.
Tryb: wyłącznie odczyt. Nic w R nie zmieniono. Wszystkie propozycje są do decyzji autora — dialogów nie zmieniano.
Numery linii dotyczą pliku E02, chyba że zaznaczono „E01 l." lub „E03 l.".

Wagi: **KRYTYCZNA** (łamie logikę lub kanon), **WYSOKA**, **ŚREDNIA**, **NISKA**.

---

## 0. Podsumowanie liczbowe

| Waga | Punkty główne (E02-xx) | Miejsca łamiące zasadę „bez mężczyzn" (E02-Mxx) |
|---|---|---|
| KRYTYCZNA | 3 | 0 |
| WYSOKA | 10 | 2 |
| ŚREDNIA | 23 | 6 |
| NISKA | 20 | 6 |
| **Razem** | **56** | **14** |

Weryfikacja wcześniejszych ustaleń: §9 (A1, A2, A3, B7, B9, B10, C11, D15, D16 i uwagi z notatek).
Docelowa numeracja scen: §10. Skutki zbiorcze: §11. Rekomendowana kolejność poprawek: §12.

---

## 1. Chronologia — tabela (kolejność w pliku)

| Poz. | Scena | Nagłówek / T+ / pora | Linia | Uwagi chronologiczne |
|---|---|---|---|---|
| 0 | PROLOG | T+9, świt | 52 | Flash-forward; klamra z E01 sc. 15 (T+8). |
| 1 | 1 | Montaż T+1 → T+8; napis „T PLUS 8 DNI" | 98 (napis 154) | Kończy się na T+8, a następna scena wraca do T+3 (E02-03). |
| 2 | 1A | T+3, „godzina czternasta" | 158 | Treść decyzji = treść komunikatu z sc. 1 (T+2) (E02-03). |
| 3 | 2 | T+3 | 309 | OK. |
| 4 | 3 | T+5 | 357 | OK. |
| 5 | 3B | T+6 (Oslo T+6) | 443 | Stoi PRZED sc. 4 (T+5) (E02-06). |
| 6 | 4 | T+5, wieczór | 476 | Cofnięcie T+6 → T+5. |
| 7 | 4A | T+6 | 521 | OK. |
| 8 | 5A | T+7 południe → T+8 świt | 592 | Numer 5A przed 5 (D15). |
| 9 | 5 | T+9, ranek/świt | 652 | OK. |
| 10 | 5B | T+9, wieczór | 685 | Wieczór przed sc. 6, która dzieje się w dzień (E02-07). |
| 11 | 6 | T+9 (dzień: „Do wieczora") | 754 | Cofnięcie wieczór → dzień. |
| 12 | 6A | T+10, NOC | 804 | „Noc" niezdefiniowana; czyta się jako noc PO 19:15 (E02-09). |
| 13 | 7 | Montaż T+9 wieczór → T+11 ranek | 863 | Obejmuje i wyprzedza 7A, 6B, 6C; koniec = duplikat 6C (E02-08). |
| 14 | 7A | T+10 („Ciemno za szybą" → wieczór) | 937 | Po montażu, który doszedł do T+11. |
| 15 | 6B | T+10, 19:15 | 1048 | Numer 6B po 7A (D15). |
| 16 | 6C | T+11, 05:43 (+3 h na wyłączenie) | 1113 | OK. |
| 17 | 8 | T+10 | 1241 | T+10 po T+11 (E02-10). |
| 18 | 9 | T+11, popołudnie | 1270 | OK. |
| 19 | 10 | T+11 (po komunikacie z 14:00) | 1298 | OK. |
| — | (brak 11) | — | — | Scena 11 usunięta, numer nie zamknięty (D15). |
| 20 | 12A | T+12, 06:20 | 1341 | Numer 12A przed 12 (D15). |
| 21 | 12 | T+12, dzień | 1453 | OK. |
| 22 | 13 | T+12, dzień | 1528 | OK. |
| 23 | 14 | T+12, popołudnie | 1571 | OK. |
| 24 | 16 | T+13, rano | 1613 | Numer 16 przed 15 (D15). |
| 25 | 15 | T+13, wieczór („Następny dzień" — liczone od sc. 14) | 1725 | Kolejność poprawna, numer i podpis „Następny dzień" mylące. |
| 26 | 17 | T+13, noc | 1808 | OK. |
| 27 | 18 | T+13, późna noc | 1957 | OK; po niej napis „E W A" (2005). |
| 28 | 19 KLAMRA | T+13, głęboka noc | 2012 | Po napisie tytułowym (E02-47). |

Wniosek: odcinek ma **6 miejsc, w których czas się cofa** (1→1A, 3B→4, 5B→6, 7→7A, 6C→8, plus wewnętrzne nakładanie montażu 7) i **5 par z odwróconą numeracją** (5A/5, 7/7A/6B/6C, 12A/12, 16/15, brak 11).

---

## 2. Punkty KRYTYCZNE

### E02-01 — Aga nie rozpoznaje ani matki, ani ojca (A1) — **KRYTYCZNA**
- **Lokalizacja:** sc. 3, l.399–410.
- **Cytat:** „Autor: prof. Marek Dąbrowski, Uniwersytet Warszawski." (l.399); „Małym drukiem: "Dane wstępne: V. Strand (materiały niepublikowane)."" (l.406); „Pisze w notatniku: "V. Strand. Kim jest?"" (l.409–410).
- **Sprzeczność:** obsada E02 l.37 „Dr Aga Bryk z d. Strand" i l.40 „Córka Very Strand". E01 obsada (E01 l.45–46): Dąbrowski to „Były mąż Very, ojciec Agi". E01 sc. P3 (E01 l.640–656) pokazuje Agę-studentkę mieszkającą z Verą: „Mamo, jest coś do jedzenia?", „Tata dzwonił. Pyta, czy przyjdę w sobotę na obiad." Aga czyta więc publikację **własnego ojca** z przypisem o danych **własnej matki** i nie reaguje na żadne z tych nazwisk. Handoff opisywał tylko połowę problemu (matkę). Ojciec w tej scenie pogłębia zgrzyt.
- **Warianty:**
  1. Rozpoznanie: notatka „V. Strand. Mama." + krótka reakcja na nazwisko ojca (np. zatrzymanie na „Dąbrowski"). Tajemnicę przed widzem przenieść na pytanie „co mama wiedziała?" (zgodne z „Wiesz co robisz?" w sc. 17).
  2. Aga rozpoznaje oboje, ale notuje pytanie o winę: „Tata i mama. Co oni zrobili?" — mocniejsze podłoże pod wyznanie w E03 sc. 14.
  3. Zastąpić przypis czymś anonimowym (np. „dane: kod OSL-07") — słabsze, gubi rymy z E01 sc. 8 i P4.
- **Rekomendacja:** wariant 1. To zmienia też wydźwięk sc. 17 (Aga świadomie zabiera matkę „do analizy wirusa") i sc. 15.
- **Skutki:** E01 bez zmian (P4 l.889 i sc. 8 l.819 to te same przypisy — rym zostaje). E03 sc. 14 (wyznanie) — sprawdzić, czy Aga „dowiaduje się", czy „potwierdza". Pliki produkcyjne: insert ekranu z przypisem (grafika w post), czytanka E02 do regeneracji.

### E02-02 — Nota i obsada zakładają, że widz nie wie, kim jest Vera; treść i E01 mówią co innego — **KRYTYCZNA**
- **Lokalizacja:** obsada l.44–45; nota l.26–30; sc. 15 l.1745–1747; sc. 17 l.1866; tabela l.2074; sc. 3B l.454–473; sc. 12A l.1413, 1428–1430.
- **Cytaty:** „Przybywa na farmę jako nieznajoma. Matka Agi. / Widz jeszcze tego nie wie." (l.44–45); „Widz zaczyna to czuć w scenie 17 (ognisko) -- ale nie ma pewności. / Pewność przychodzi w E03." (l.29–30); „Jestem Vera Strand. / Matka Agnieszki." (l.1746–1747); „AGA ... Dotarłaś." (l.1777–1778); „Widz nie rozumie jeszcze dlaczego." (l.1866); tabela: „Scena 15 Vera przybywa jako nieznajoma" (l.2074).
- **Sprzeczność:** widz wie, że Vera to matka Agi, już z E01 (P3: „Mamo"; sc. 8: kontakt „Aga" ze zdjęciem wnuczek, E01 l.822–823) i z E02 sc. 3B („Mamo. Żyjesz?") oraz 12A („Moja mama"). W sc. 15 Vera przedstawia się Zofii z nazwiska i jako matka, a Aga ją wita. Nie jest „nieznajomą" ani dla widza, ani dla farmy. Wiedza o tym, że Vera stworzyła wirusa, też jest w E01 (obsada E01 l.37–38 „Twórczyni wirusa Y. Tylko ona wie."; P4 l.909–919: „Adam"). „Pewność w E03" dotyczy więc co najwyżej tego, co wie **Aga**, a nie widz.
- **Warianty:**
  1. Przepisać notę, obsadę i tabelę: „Vera przybywa jako matka Agi; dla farmy obca. Widz wie, kim jest i co zrobiła. Aga nie wie." Ironia dramatyczna = widz wie więcej niż Aga.
  2. Jeśli „nieznajoma" ma zostać: Vera nie przedstawia się jako matka (np. „Jestem Vera. Szukam Agi Bryk."), a Aga wita ją dopiero w sc. 17. Wiedzy widza i tak to nie cofnie (E01).
- **Rekomendacja:** wariant 1 (zgodny z E01 i E03). Usunąć „Widz nie rozumie jeszcze dlaczego" (l.1866) albo zamienić na „Aga nie rozumie".
- **Skutki:** nota E03 (jeśli też zakłada niewiedzę widza) — sprawdzić. Pliki produkcyjne: charakterystyki postaci dla E02 (jeszcze nie powstały) muszą przyjąć model wiedzy z wariantu 1.

### E02-03 — Scena 1 wyprzedza całą akcję i ogłasza decyzje, które zapadają dopiero w sc. 1A — **KRYTYCZNA**
- **Lokalizacja:** sc. 1 l.100, 111–128, 145–154; sc. 1A l.159, 286–302.
- **Cytaty:** sc. 1 (T+2): „Zabezpieczcie źródła wody na kilka dni. / Możliwe są przerwy w dostawach energii -- / jeśli macie dostęp do agregatu, przygotujcie go." (l.124–126); „Napis biały na czarnym: T PLUS 8 DNI" (l.154). Sc. 1A (T+3): „Mówimy im żeby zabezpieczyli wodę. Mówimy / że mogą być przerwy w zasilaniu. Mówimy żeby / postarały się o agregat jeśli mogą." (l.287–290); „Za godzinę jestem na antenie." (l.302).
- **Sprzeczność:** (a) komunikat z T+2 zawiera dokładnie to, co rząd ustala dzień później na naradzie, która kończy się zapowiedzią wystąpienia. (b) Montaż kończy się napisem „T+8", a sc. 1A, 2, 3, 3B, 4, 4A wracają do T+3–T+6. Widz dostaje informację, że jesteśmy w dniu 8, i natychmiast cofa się o 5 dni, bez sygnału. (c) Montaż zawiera beat T+6 „Karolina ... Marta z PSE. Krótka rozmowa." (l.145–147), który koliduje z sc. 4 (T+5, Marta nie odbiera) i z wyrzutem w sc. 12 (l.1496).
- **Warianty:**
  1. Skrócić montaż do T+1–T+2 (bez Wolskiej albo z Wolską tylko „Ogłaszam…/Przejmuję…", bez wody i agregatów) i zakończyć napisem „T PLUS 3 DNI". Beaty T+3–T+8 (sklep, kartki, szpital, balkon) przenieść do montażu 5A.
  2. Przesunąć Wolską z sc. 1 na T+3 i postawić ją PO sc. 1A jako realizację „Za godzinę jestem na antenie" (wtedy to „Briefing 1").
  3. Zostawić sc. 1 bez zmian, ale usunąć z 1A ustalenia „co mówimy" i zostawić tylko „Prawda / Część" — najsłabsze, bo l.302 dalej zapowiada wystąpienie.
- **Rekomendacja:** 1 + 2 łącznie: montaż T+1–T+2 bez komunikatu, komunikat jako krótki beat po 1A. Napis „T+8" usunąć (albo przenieść na koniec 5A).
- **Skutki:** numeracja briefingów („BRIEFING 3" l.895, „BRIEFING 4" l.1242) i nota „cztery razy" (l.2085) — przeliczyć. Czas sc. 1 maleje o ok. 0,5–1 min.

---

## 3. Punkty WYSOKIE

### E02-04 — Prolog łamie ciągłość z E01 sc. 15 (kurs, czas, ruch statku) — **WYSOKA**
- **Lokalizacja:** prolog l.53–57, 69–72; E01 l.1226–1263.
- **Cytaty:** E02: „ciągłość z ostatnim kadrem odcinka pierwszego" (l.56); „Dryfuje bokiem do / wiatru, powoli, nieuchronnie." (l.70–71); „T PLUS 9" (l.54). E01 sc. 15 (T+8, świt): „Płynie. Powoli, równo, prosto." (E01 l.1238); „kurs ustawiony, prędkość stała, autopilot trzyma linię" (E01 l.1250–1251); „dziób wycelowany w cienką kreskę lądu na horyzoncie. Tam, daleko, majaczą światła terminalu." (E01 l.1256–1257).
- **Sprzeczność:** (a) w E01 statek idzie prosto na autopilocie, w E02 dryfuje bokiem. (b) W E01 o świcie T+8 terminal jest już na horyzoncie (kilkanaście–kilkadziesiąt km), a w E02 uderzenie następuje o świcie T+9, czyli doba później. Przy stałej prędkości statek byłby w porcie po kilku godzinach. (c) „Ciągłość z ostatnim kadrem" sugeruje ten sam moment, a nie następny dzień.
- **Warianty:** 1) Zmienić E02 prolog na „T PLUS 8" (ten sam świt, kilka godzin później) i „idzie prosto, autopilot" zamiast „dryfuje". 2) Zostawić T+9, a w E01 sc. 15 usunąć „majaczą światła terminalu" (statek dalej od brzegu). 3) Wyjaśnić dryf: autopilot się wyłączył w nocy i statek zszedł z kursu (jedno zdanie didaskaliów w E02).
- **Rekomendacja:** wariant 1, jeśli oś czasu (handoff §3: „T+9 uderzenie") może się zmienić. W przeciwnym razie wariant 2 + „dryfuje" zamienić na „idzie kursem".
- **Skutki:** handoff §3, oś czasu; sc. 7 (l.886 „T PLUS 10 ... dzień po uderzeniu") i 7A — przeliczyć. Pliki Flow: prompt prologu musi wziąć model statku z E01 (cztery kopuły Moss, E01 l.1235–1236).

### E02-05 — Żółta teczka: w E01 schowana w szafie w PSE, w E02 Marta zabiera ją z szafy w domu; plecak i torba podwójnie — **WYSOKA**
- **Lokalizacja:** sc. 12A l.1345, 1439; sc. 12 l.1461, 1477–1478; sc. 18 l.1965; E01 l.154–158, 582–583.
- **Cytaty:** E01: „Marta odkłada teczkę do szafy. Zamyka." (E01 l.158; scena w „CENTRUM DYSPOZYTORSKIE PSE, WARSZAWA", E01 l.127); „patrzy na szafę / gdzie leży żółta teczka." (E01 l.582–583). E02: „Marta wychodzi z PSE z plecakiem i torbą." (l.1345); „Marta pakuje. Nie dużo -- plecak i jedna torba." (l.1461); „Marta przy szafie. Otwiera. Żółta teczka -- bierze. / Wkłada do plecaka między ubraniami." (l.1477–1478).
- **Sprzeczność:** rekwizyt założony w E01 w szafie w PSE pojawia się w E02 w domu. Do tego Marta wychodzi z PSE z plecakiem i torbą, a w domu pakuje „plecak i jedną torbę" — nie wiadomo, czy to te same.
- **Warianty:** 1) W 12A Marta przed wyjściem otwiera szafę w PSE i zabiera teczkę (spłata ziarna z E01). W sc. 12 usunąć teczkę i zostawić pakowanie ubrań. 2) Dodać w E02 wcześniej jeden beat (np. sc. 4 lub 6C), w którym Marta zabiera teczkę z szafy w PSE, a w sc. 12 przekłada ją do plecaka. 3) Zostawić E02 i w E01 zmienić „szafę" na teczkę zabieraną do domu (wymaga zmiany E01 l.158 i 583).
- **Rekomendacja:** wariant 1 — najmocniejszy obraz („Jedenaście dni" + teczka z szafy). Rozwiązuje też problem toreb: wychodzi z PSE z plecakiem (teczka w środku), w domu dopakowuje torbę.
- **Skutki:** E03 l.1291, 1501, 1567, 1599 — teczka u Karoliny; bez kolizji. Lista rekwizytów i ciągłość: plecak Marty (E01 l.133 „z kawą i plecakiem") — ten sam plecak.

### E02-08 — Montaż 7: zakres T+9–T+11 nakłada się na 6A, 7A, 6B i 6C; zakończenie dubluje 6C i ma zły czas — **WYSOKA**
- **Lokalizacja:** sc. 7 l.865, 870–933; sc. 6C l.1228–1238.
- **Cytaty:** „T PLUS 9 DO T PLUS 11" (l.865); „T PLUS 11, ŚWIT: / Lotnisko Chopina." (l.913–914); „Centrum PSE -- za oknem świt. / Beata i Ania zbierają się do wyjścia. / Marta zostaje sama przy wygasłej konsoli." (l.931–933). Sc. 6C: decyzja o 05:43 (l.1115), „Trzy godziny od teraz" (l.1176), „Wychodzą. Marta zostaje sama." (l.1238).
- **Sprzeczność:** (a) montaż pokazuje koniec sieci (wygasła konsola, wyjście Beaty i Ani) przed sceną, w której sieć jest wyłączana. (b) Wyłączenie zaczyna się o 05:43 i trwa ok. 3 h, więc „świt" i „wygasła konsola" w jednym ujęciu są niemożliwe (sieć gaśnie ok. 09:00). (c) Ten sam beat wyjścia Beaty i Ani pojawia się dwa razy. (d) „Latarnie ... nie paliły się w nocy" (l.921) — w nocy T+10/11 Warszawa była ostatnim zasilanym punktem (l.1087, 1119).
- **Warianty:** 1) Uciąć montaż na T+10 popołudnie (briefing 3), beaty T+10 wieczór (rafineria) i T+11 (lotnisko, ulice, śmieci) przenieść za 6C jako mini-montaż „po wyłączeniu". Usunąć l.931–933. 2) Zostawić montaż w całości, ale postawić go PO 6C, usunąć z niego beaty T+9–T+10 i ostatni beat PSE. 3) Zostawić, usunąć tylko l.931–933 — usuwa duplikat, ale nakładanie czasu zostaje.
- **Rekomendacja:** wariant 1.
- **Skutki:** czas sc. 7 (2,5 vs 4,0 — E02-12). Muzyka: kontrabas w sc. 7 to pierwsza muzyka (l.867–868) — po podziale ustalić, w której części startuje.

### E02-10 — Briefing 4 (T+10) stoi po wyłączeniu sieci (T+11) — **WYSOKA**
- **Lokalizacja:** sc. 8 l.1241–1267.
- **Cytat:** „INT. STUDIO TELEWIZYJNE -- BRIEFING 4 / T PLUS 10" (l.1242–1243); „Obraz gaśnie. Czarny ekran." (l.1259).
- **Sprzeczność:** w pliku sc. 8 jest po 6C (T+11). Widz zobaczy „ostatnie wystąpienie" po tym, jak na mapie zgasła Warszawa, ale z nagłówkiem T+10. Dodatkowo w T+10 obraz gaśnie, a w sc. 10 (T+11) telewizja jeszcze nadaje — trzeba to jasno rozdzielić (awaria studia vs koniec sieci).
- **Warianty:** 1) Zmienić nagłówek na T+11 ok. 09:00 — Wolska ogłasza wyłączenie, obraz gaśnie, bo sieć właśnie padła („Ktoś poza kadrem" = informacja o odcięciu). 2) Zostawić T+10 i przenieść sc. 8 przed 6B/6C.
- **Rekomendacja:** wariant 1 (najmocniejszy dramaturgicznie; spina 6C z 8 i 9).
- **Skutki:** w wariancie 1 Wolska występuje po rozmowie z Martą o 05:43 — zgodne. Tabela (l.2067) do korekty.

### E02-11 — Numeracja scen (D15) — **WYSOKA**
- **Lokalizacja:** cały plik; tabela l.2051–2078.
- **Cytaty:** kolejność nagłówków w pliku: PROLOG, 1, 1A, 2, 3, 3B, 4, 4A, 5A, 5, 5B, 6, 6A, 7, 7A, 6B, 6C, 8, 9, 10, 12A, 12, 13, 14, 16, 15, 17, 18, 19. Brak „SCENA 11". Tabela: „Scena 15 ... / Scena 16 ..." (l.2074–2075) — odwrotnie niż w pliku; brak 3B w tabeli.
- **Sprzeczność:** numeracja nie odpowiada ani kolejności, ani chronologii. Handoff (§4 D15) pominął scenę 7 między 6A a 7A.
- **Warianty:** 1) Pełne przenumerowanie 1–28 wg §10. 2) Zachowawczo: zostawić numery, ale ustawić sceny chronologicznie i dodać w tabeli kolumnę „nr produkcyjny".
- **Rekomendacja:** wariant 1 — przed planem zdjęciowym i przed rozpiską Flow (pliki clip-po-clipie będą miały nazwy od numerów scen).
- **Skutki:** czytanka PDF, przyszłe pliki `ZERO_E02_S*_Clip*.md`, odniesienia w nocie (l.29 „scenie 17", l.2106 „SCENA 19"), handoff §3 („SCENA 19 — KLAMRA") i E03 („ciągłość bezpośrednio po finale odcinka drugiego").

### E02-12 — Czas odcinka: pięć różnych liczb — **WYSOKA**
- **Lokalizacja:** l.3; tabela l.2051–2080; nagłówki scen.
- **Cytaty:** „Format: ok. 65 minut" (l.3); „RAZEM: ok. 69,0 min" (l.2080).
- **Ustalenia (przeliczone):** suma 28 pozycji tabeli = **70,5 min** (nie 69,0). Suma 29 nagłówków `[CZAS]` (z 3B) = **73,5 min**. Rozbieżności nagłówek ↔ tabela: sc. 3 „ok. 5 min" (l.357) vs 3,0; sc. 7 „ok. 2,5 min" (l.863) vs 4,0; sc. 18 „ok. 3 min" (l.1957) vs 2,0; sc. 3B „ok. 1,5 min" (l.443) — brak w tabeli. Pozostałe 25 pozycji zgodne. Handoff: „E02 — EWA (~67 min)"; decyzje: „~66–67".
- **Warianty:** 1) Przyjąć nagłówki scen (73,5) jako roboczy metraż i ciąć do ok. 67 (kandydaci: 1A, 7A — dwie narady o podobnej funkcji; montaże 1/5A/7; 6C 4 min). 2) Przyjąć tabelę i poprawić nagłówki 3, 7, 18 + dodać 3B (= 72,0 min).
- **Rekomendacja:** po przebudowie z E02-03 i E02-08 policzyć od nowa; docelowo jedna liczba w nagłówku, tabeli i handoffie.
- **Skutki:** budżet generacji (produkcja_i_budzet), handoff §1.

### E02-14 — Data publikacji Dąbrowskiego (A3) — **WYSOKA**
- **Lokalizacja:** sc. 3 l.400.
- **Cytat:** „Data: osiemnaście lat temu."
- **Sprzeczność:** E01 P4: „OSLO. DWA LATA PO WYJEŹDZIE Z WARSZAWY." (E01 l.870) i „(VERA MA OKOŁO 52 LATA)" (E01 l.867); Vera ma dziś 64 → publikacja ok. **12 lat temu**. 18 lat temu Vera miałaby 46 i byłaby jeszcze w Warszawie, co psuje „ukradł po jej wyjeździe". Prawdopodobne źródło pomyłki: E01 l.882–883 „Jej pięć lat pracy przed wyjazdem i trzynaście lat przed tym" (5 + 13 = 18 lat pracy, a nie lat od publikacji).
- **Warianty:** 1) „około dwanaście lat temu" (handoff). 2) Zmienić wiek Very w P4 na ~46 — psuje E01.
- **Rekomendacja:** wariant 1.
- **Skutki:** brak w E03 (sprawdzić ewentualne wzmianki w sc. 14).

### E02-15 — Wolska: imię i wiek (A2) oraz kolizja imion „Anna" już w E02 — **WYSOKA**
- **Lokalizacja:** l.42, 111, 165; E03 l.13, 915.
- **Cytaty:** „Wicepremier Katarzyna Wolska ~58 lat." (l.42); „Wicepremier KATARZYNA WOLSKA" (l.111); „GENERAŁ ANNA SOWA (szefowa sztabu, pięćdziesiąt lat, rzeczowa)" (l.165); E03: „**ANNA WOLSKA** — wicepremier, 51 lat." (E03 l.13); „Tu Anna Wolska, pełniąca obowiązki / premiera" (E03 l.915–916).
- **Sprzeczność:** E02 jest wewnętrznie spójny (Katarzyna, ~58). Notatka z przeglądu twierdzi jednak, że „Anna nie pojawia się przy Wolskiej w E02" — to nieprawda: gen. **Anna** Sowa stoi przy niej w sc. 1A i 7A. Jeśli wybrać „Anna Wolska", w jednym pokoju w E02 siedzą dwie Anny, a w PSE pracuje „Ania" (l.321).
- **Warianty:** 1) Katarzyna ~58 (zgodnie z handoffem) + poprawka E03 l.13 i l.915. 2) Anna 51 + zmiana imienia gen. Sowy w E02 (l.165).
- **Rekomendacja:** wariant 1.
- **Skutki:** E03 obsada i sc. 9; wiek 51 vs 58 wpływa na casting/Entity w Flow.

### E02-21 — Łączność po blackoucie: telefon satelitarny Agi znikąd, SMS-y w martwej sieci — **WYSOKA**
- **Lokalizacja:** sc. 9 l.1278–1281; sc. 12A l.1398, 1428–1437; sc. 17 l.1869.
- **Cytaty:** „Karolina z telefonem w ręce. Ekran ciemny. ... Próbuje hotspot, WiFi, wszystko." (l.1278–1280, T+11); „AGA (odbiera od razu)" (l.1398, T+12); „Pisze SMS do Very: ... Wysyła." (l.1428–1431); „Pisze drugi SMS -- do Bożeny" (l.1433); „Telefon satelitarny Agi dzwoni." (l.1869).
- **Sprzeczność:** od T+11 rano nie ma sieci (6C) i — wg sc. 9 i 10 („jeżeli macie jeszcze sygnał", l.1312) — komórki praktycznie nie działają. Marta dzwoni z telefonu satelitarnego, ale Aga musi mieć odbiornik, który działa; SMS-y do Very (w drodze przez Skandynawię) i do Bożeny muszą dojść. W sc. 17 Aga ma telefon satelitarny, którego nigdzie nie dostała (Marta dostała swój w 4A/12A). Vera dociera na farmę dzięki SMS-owi z T+12 — bez niego nie zna adresu (SMS z T+6, l.454–455, mówi tylko „Jedź do Polski").
- **Warianty:** 1) W sc. 3 rząd (połączenie z Gabinetu, l.420–433) wysyła Adze telefon satelitarny („Prześlemy pani telefon, żeby był kontakt") — jedno zdanie spłaca 12A i 17. 2) W 12A zaznaczyć, że sieć komórkowa w Warszawie działa jeszcze na zasilaniu awaryjnym stacji bazowych (kilka godzin) — wtedy przesunąć 12A przed sc. 9 lub osłabić sc. 9. 3) Vera zna adres z innego źródła (Aga podała go w T+6 — zmiana SMS-a w 3B).
- **Rekomendacja:** 1 + 3 (SMS z T+6 już z adresem farmy jest niemożliwy, bo w T+6 nikt nie planuje farmy — więc realnie 1 + opcja 2 dla SMS-ów).
- **Skutki:** E03 klamra ujęcie 8: Aga dzwoni „z telefonem przy uchu -- jedna kreska zasięgu" (E03 l.235–236) — trzeba zdecydować, czy to komórka czy satelita (E02-22).

### E02-22 — E02 sc. 17 vs E03 klamra: Aga dwa razy przyjmuje wezwanie — **WYSOKA**
- **Lokalizacja:** sc. 17 l.1869–1885, 1928–1938; E03 l.234–247, 252–256.
- **Cytaty:** E02: „AGA (cicho przez telefon) / Tak. / Rozumiem. / Jutro rano." (l.1872–1875); „Jutro rano jadę do Warszawy. / Chcę żebyś pojechała ze mną." (l.1883–1884). E03 (rano po napadzie): „Doktor Aga Bryk. Choroby zakaźne, Bielański. Jestem gotowa. Dołączam. ... mam warunek. Przyślijcie dwoje ludzi z wojska ... Bez tego nigdzie nie lecę." (E03 l.240–244).
- **Sprzeczność:** w E02 Aga już zgodziła się wyjechać rano i ustaliła to z Zofią i Martą; w E03 przedstawia się i „dołącza" po raz pierwszy, telefonem komórkowym, i stawia warunek. Środek transportu: „jadę" (E02) vs śmigłowiec (E03).
- **Warianty:** 1) E03 ujęcie 8 przepisać jako drugi telefon: „Potwierdzam na rano. Ale po tej nocy mam warunek…" 2) W E02 rozmowa w sc. 17 bez zgody („Oddzwonię rano") — wtedy decyzja zapada w E03 pod wpływem napadu (mocniejsze). 3) Usunąć telefon z sc. 17, zostawić prośbę do Very jako zamiar.
- **Rekomendacja:** wariant 2 — napad w 19 staje się powodem warunku w E03.
- **Skutki:** nota E02 l.2099–2100 („AGA: Odchodzi. Wie gdzie."), sc. 17 rozmowy z Zofią i Martą.

---

## 4. Punkty ŚREDNIE

### E02-06 — Sc. 3B (T+6) przed sc. 4 (T+5 wieczór) — **ŚREDNIA**
- **Lokalizacja:** l.443–444, 476–478.
- **Cytaty:** „INT. LABORATORIUM WIRUSOLOGII -- T PLUS 6" (l.444); „INT. CENTRUM PSE -- POKÓJ SOCJALNY -- WIECZÓR / T PLUS 5" (l.477–478).
- **Warianty:** 1) Zamienić kolejność (4 → 3B). 2) Zmienić 3B na „T PLUS 5, NOC".
- **Rekomendacja:** 2 (Aga dzwoni do Norwegii tej samej nocy po odkryciu przypisu — logiczne następstwo sc. 3, szczególnie po naprawie E02-01). Przy okazji ujednolicić nazwę miejsca: „SZPITAL BIELAŃSKI, LABORATORIUM" (l.358) vs „LABORATORIUM WIRUSOLOGII" (l.444).

### E02-07 — Sc. 5B (T+9 wieczór) przed sc. 6 (T+9 dzień); wiszący telefon w sc. 5 — **ŚREDNIA**
- **Lokalizacja:** l.682, 686–687, 755–770.
- **Cytaty:** sc. 5: „Wybiera numer. Czeka." (l.682); 5B: „INT. CENTRUM PSE -- WIECZÓR / T PLUS 9" (l.686–687); sc. 6: „Do wieczora. Może do północy jeżeli się uda." (l.770).
- **Sprzeczność:** sc. 6 musi dziać się przed wieczorem, a stoi po wieczornym 5B. Telefon z końca sc. 5 to najpewniej telefon do elektrowni (sc. 6), więc 5 i 6 powinny sąsiadować.
- **Warianty:** 1) Kolejność 5 → 6 → 5B. 2) Połączyć 5 i 6 w jedną scenę (sc. 5 kończy się wybraniem numeru, sc. 6 jest odpowiedzią).
- **Rekomendacja:** 1 (+ w sc. 6 podać porę „T PLUS 9, POŁUDNIE"). Tytuł sc. 6 „TELEFON DO ELEKTROWNI" zgadza się z wariantem 1.

### E02-09 — Sc. 6A „T+10, NOC": niejasna noc; stan mapy wymaga dookreślenia (ZAWĘŻONE) — **ŚREDNIA**
- **Lokalizacja:** l.806–815; sc. 7 l.880–882; 6B l.1086–1087; 6C l.1117–1119.
- **Cytaty:** 6A: „Mapa za nią: ponad połowa punktów czerwona." (l.808); „Trzymamy Warszawę, Kraków i Wrocław." (l.814). Sc. 7 T+10 rano: „czerwona na około połowie punktów" (l.882). 6B (19:15): „Prawie cała czerwona. Jeden zielony punkt -- Warszawa." (l.1087).
- **Ocena:** jeśli 6A to noc z T+9 na T+10 (przed świtem), stan mapy rośnie logicznie: ponad połowa → połowa (rano, drobna niekonsekwencja) → prawie cała (19:15) → wyłączenie (T+11). Sprzeczność jest wtedy tylko w etykiecie. Jeśli 6A ma być nocą PO 19:15, mapa się cofa (z jednego zielonego punktu do trzech miast).
- **Warianty:** 1) Nagłówek „NOC Z T+9 NA T+10, ok. 02:00" + w 7 „ponad połowa". 2) Przenieść 6A za 6B i zmienić tekst Marty na „Trzymamy tylko Warszawę".
- **Rekomendacja:** 1.

### E02-13 — Opisy w tabeli czasów niezgodne z treścią — **ŚREDNIA**
- **Cytaty i rozbieżności:**
  - „Scena 4 Salon Marty, Briefing 2, Karolina pyta (T+5)" (l.2056) — scena dzieje się w „POKÓJ SOCJALNY" PSE (l.477); Karolina nie pyta, tylko dzwoni i pisze SMS „Mamo. Jak u ciebie." (l.514).
  - „Scena 5 PSE Dzień 9 -- pierwsza awaria GPZ" (l.2059) — awarie są od T+3 (l.170–172, 318).
  - „Scena 5B Marta dzwoni do Karoliny 1" (l.2060) — wcześniej jest rozmowa w sc. 1 (l.145–147).
  - „Scena 15 Vera przybywa jako nieznajoma" (l.2074) — patrz E02-02.
  - Kolejność 15/16 odwrotna niż w pliku; brak 3B (l.443).
  - „Scena 2 PSE Dzień 3 -- mapa i trzy kobiety" — zgodne.
- **Rekomendacja:** przebudować tabelę dopiero po zatwierdzeniu nowej numeracji (§10).

### E02-16 — „Ania" w PSE zamiast osób z E01 (Agnieszka, Ela) — **ŚREDNIA**
- **Lokalizacja:** l.321–322; E01 l.1036–1037, 1171.
- **Cytaty:** E02: „Trzecia kobieta -- ANIA, administracja, nie inżynier" (l.321). E01 (T-4): „Agnieszka -- bierz R-dziewiętnaście. Ela -- R-dwadzieścia dwa." (E01 l.1037); Zero Day: „Marta i dwie kobiety przy konsolach." (E01 l.1171).
- **Sprzeczność:** w E01 w PSE zostają z Martą Beata oraz Agnieszka i Ela; w E02 trzecią osobą jest nowa „Ania" (administracja). Nikt nie wyjaśnia, co stało się z Agnieszką i Elą. „Ania" koliduje z gen. Anną Sową, a „Agnieszka" z Agą (l.1747 „Matka Agnieszki").
- **Warianty:** 1) Zmienić „Ania" → „Ela" (z E01): spójność z E01 i usunięcie kolizji z Anną. 2) Zostawić „Ania" i dodać w sc. 2 pół zdania („Ela nie przyszła od wczoraj"). 3) Zostawić, ale w E01 zmienić Elę na Anię.
- **Rekomendacja:** 1. Uwaga: „administracja, nie inżynier" (l.321) kłóci się z E01, gdzie Agnieszka/Ela obsługują konsole — przy wariancie 1 usunąć „nie inżynier" albo zostawić jako świadomą zmianę postaci.

### E02-17 — „Pani Premier" vs „Wicepremier" (ZAWĘŻONE) — **ŚREDNIA**
- **Lokalizacja:** „Pani Premier": l.811, 1128, 1136, 1144, 1356, 1366, **1376** (7 razy; notatka podawała 6). „Wicepremier": l.42, 111, 115, 120, 421 („Gabinetu Wicepremiera", T+5), 895 („Wicepremier Wolska -- BRIEFING 3", T+10), 1319 („komunikat wicepremier Wolskiej", T+11).
- **Ocena:** w E01 premier jest mężczyzną (E01 l.1146–1151: „PREMIER ... Za plecami premiera -- kobieta. Wicepremier Wolska."), w E02 Wolska mówi „Przejmuję pełnię władzy wykonawczej" (l.117), a w E03 jest „pełniąca obowiązki premiera" (E03 l.915–916). Forma „Pani Premier" jest więc fabularnie uzasadniona. Niespójne jest to, że didaskalia i komunikaty państwowe po T+2 dalej mówią „wicepremier".
- **Warianty:** 1) Od T+2 w didaskaliach i komunikatach: „p.o. Premiera" / „premier Wolska"; w obsadzie: „Wicepremier, od T+2 p.o. Premiera". 2) Wszędzie „Pani Wicepremier" (sztywne, ale formalnie poprawne).
- **Rekomendacja:** 1 (zgodne z E03).

### E02-18 — Wolska ogłasza stan wyjątkowy, który premier ogłosił już w E01 — **ŚREDNIA**
- **Lokalizacja:** l.116; E01 l.1146–1147.
- **Cytaty:** E02 (T+2): „Ogłaszam stan wyjątkowy na terenie całego kraju." E01 (T-1): „PREMIER / Ogłaszam stan wyjątkowy na terenie całego kraju."
- **Warianty:** 1) Świadome echo — zaznaczyć w didaskaliach („te same słowa co premier"). 2) Zmienić na „Stan wyjątkowy pozostaje w mocy. Przejmuję…".
- **Rekomendacja:** 1 albo 2 — byle świadomie; obecnie czyta się jak pomyłka.

### E02-19 — „Zofia Kowalska" (D16) — **ŚREDNIA**
- **Lokalizacja:** l.1416, 1429, 1435.
- **Cytaty:** „Farma pod Łowiczem. Zofia Kowalska." (l.1416); „Mamo. Farma pod Łowiczem. Zofia Kowalska." (l.1429); „do Zofii Kowalskiej" (l.1435).
- **Ocena:** potwierdzone. Zawężenie wniosku z notatki: nie musi to być nazwisko panieńskie Marty. E03 mówi o „wuju" (E03 l.180 „tam, gdzie wuj trzymał starą dubeltówkę"); „wuj" to tradycyjnie brat matki, więc Zofia może być żoną brata matki Marty i nosić nazwisko panieńskie **matki** Marty. Jedyne wykluczone rozwiązanie to „Kowalska" (nazwisko Piotra), bo Karolina w ogóle nie znała ciotki (l.1552).
- **Warianty:** 1) Inne nazwisko (dowolne, różne od Kowalska/Bryk/Strand/Wolska). 2) Bez nazwiska: „Zofia, farma pod Łowiczem, za kościołem" (adres opisowy).
- **Rekomendacja:** 1. Przy okazji zdecydować, czy Zofia jest wdową (wuj zmarł na wirusa) — patrz E02-48.

### E02-20 — „MINISTER" vs „MINISTRA", „ministrowie" — **ŚREDNIA**
- **Lokalizacja:** l.161, 177, 188–190, 272, 278, 1001.
- **Cytaty:** „Osiem kobiet -- ministrowie, szefowe służb, / ekspertki." (l.161); „MINISTER INFRASTRUKTURY" (l.177, 1001); „MINISTRA ENERGETYKI" (l.188, 190); „MINISTER KOMUNIKACJI" (l.272, 278).
- **Sprzeczność:** w świecie bez mężczyzn każda osoba przy stole jest kobietą; formy mieszane sugerują mężczyzn i w generatorze (prompty EN „minister") dadzą mężczyznę. „Ministrowie" to forma męskoosobowa.
- **Warianty:** 1) Ujednolicić „MINISTRA …" (konsekwentnie z l.188). 2) „MINISTER" jako tytuł nieodmienny + w didaskaliach „(kobieta, ok. 50)".
- **Rekomendacja:** 1 + w l.161 „ministry". W promptach EN zawsze „female minister".

### E02-23 — Pozycje postaci między E02 sc. 18/19 a E03 klamrą — **ŚREDNIA**
- **Lokalizacja:** sc. 18 l.1961–1962, 1998; sc. 19 l.2030; E03 l.107–125, 159.
- **Cytaty:** E02: „Inne kobiety odeszły. Zostały Marta i Karolina." (l.1961); „Siedzą razem przy prawie wygasłym ogniu." (l.1998). E03 („ciągłość bezpośrednio po finale"): Marta „Przy zlewie ... z kubkiem herbaty" (E03 l.122), Aga i Vera przy stole (E03 l.116), „Schodzą KAROLINA (19) i HELENA (~50), zaspane" (E03 l.159).
- **Sprzeczność:** jeszcze chwilę wcześniej Karolina siedziała z Martą przy ognisku, a w E03 jest zaspana na górze. Aga, która „jutro rano" wyjeżdża, siedzi z Verą przy stole — co jest możliwe, ale w E02 nie zostało pokazane.
- **Warianty:** 1) W E02 sc. 18 dodać zejście do domu („Wchodzą. Karolina idzie spać.") i przesunąć 19 o „godzinę później". 2) W E03 zmienić „zaspane" na „wystraszone", Karolina w kuchni.
- **Rekomendacja:** 1 (jedno zdanie w E02).

### E02-24 — Bożena: wątek urwany — **ŚREDNIA**
- **Lokalizacja:** l.1433–1437; sc. 15 l.1787; sc. 17 l.1909–1913.
- **Cytaty:** „Pisze drugi SMS -- do Bożeny, mamki dziewczynek: ... jedź / z nimi na farmę" (l.1433–1435); „Dziewczynki są w środku. Śpią już." (l.1787); „Zostają tu. Marta jest. Karolina jest." (l.1912).
- **Sprzeczność:** nie wiadomo, czy Bożena dotarła z dziewczynkami i czy jest na farmie. Jeśli jest, Zofia nie musiałaby „zajmować się" dziećmi; jeśli nie — kto przywiózł dziewczynki? Słowo „mamka" oznacza kobietę karmiącą piersią — przy dzieciach 4 i 2 lata to błąd; w E01 Bożena to sąsiadka/niania (E01 l.1082).
- **Warianty:** 1) Jedno zdanie w sc. 15 lub 17: „Bożena przywiozła je wczoraj. Wróciła do swoich." 2) Bożena na farmie (w ognisku, bez kwestii).
- **Rekomendacja:** 1 + „mamki" → „niani".

### E02-25 — Mapa sieci: kolory bez legendy, sprzeczne liczby — **ŚREDNIA**
- **Lokalizacja:** l.162–163, 316–318, 340–342, 745, 795, 808, 882, 1087, 1119; E01 l.1191–1193, 1045.
- **Cytaty:** „Czerwone: trzy. Nowych względem poprzedniego dnia." (l.318) i zaraz „Wczoraj były dwa. Pojutrze będzie pięć." (l.341); „GPZ Grodzisk -- znowu żółty?" (l.745); „Blok B na mapie -- żółty jeszcze." (l.795); „Jeden zielony punkt -- Warszawa." (l.1087). E01 Zero Day: „Mapa za nią prawie cała pomarańczowa. / Kilkanaście czerwonych punktów" (E01 l.1191–1192).
- **Sprzeczność:** (a) „trzy nowe" i „wczoraj były dwa" się wykluczają. (b) W E01 przy T0 czerwonych punktów jest kilkanaście, w E02 przy T+3 — trzy. (c) Cztery kolory (zielony/żółty/pomarańczowy/czerwony) bez definicji. Punkty raz oznaczają GPZ, raz bloki elektrowni („Blok B"), raz miasta („zielony — Warszawa"). (d) Przy 80–85% stacji w trybie awaryjnym Warszawa „zielona".
- **Warianty:** 1) Legenda w didaskaliach sc. 2: zielony = norma, żółty = ostrzeżenie, pomarańczowy = tryb awaryjny, czerwony = wyłączony; punkty = stacje; miasta = obszary zasilania. W l.318 usunąć „Nowych względem poprzedniego dnia." 2) W E01 Zero Day zmienić „czerwone" na „żółte".
- **Rekomendacja:** 1 (+ grafika mapy robiona w post, nie w Veo — ta sama legenda w E01/E02/E03).

### E02-26 — Prognozy „ile mamy czasu" nie układają się w ciąg — **ŚREDNIA**
- **Cytaty:** T+3: „Dziewięć. ... Tyle mamy. Zanim sieć zacznie sama siebie odcinać." (l.345–351) → koniec ok. T+12; T+6: „Mamy jeszcze osiem, może dziesięć dni / zanim sieć zacznie się odcinać kaskadowo." (l.542–543) → T+14–16; T+10 noc: „dwadzieścia cztery, / góra trzydzieści sześć godzin" (l.821–822); T+11 05:43: „Sieć padnie za osiem do dwunastu godzin" (l.1149).
- **Sprzeczność:** prognoza z T+6 jest późniejsza niż z T+3, a sieć pada w T+11. „Dziewięć" nie ma jednostki.
- **Warianty:** 1) T+3: „Dziewięć dni." T+6: „Pięć, może sześć dni." 2) T+6 zostawić, a w T+3 zmienić na „Dwanaście".
- **Rekomendacja:** 1.

### E02-29 — Terminologia sieci: GPZ w PSE, „bocznik", „Rogów" zamiast „Rogowca" z E01 — **ŚREDNIA**
- **Lokalizacja:** l.170, 540, 660–665, 745, 968, 1107; E01 l.137.
- **Cytaty:** „osiemdziesiąt procent GPZ-ów" (l.170); „GPZ Rogów, cztery kilometry od bocznika / wysokiego napięcia" (l.660–661); E01: „Rogowiec znowu dał znać o sobie." (E01 l.137).
- **Sprzeczność faktograficzna:** PSE (operator przesyłowy) prowadzi stacje najwyższych napięć (220/400 kV); GPZ (110 kV/SN) należą do operatorów dystrybucyjnych. Analityczka PSE mówiąca o „80% GPZ-ów" brzmi dla branży nieprecyzyjnie. „Bocznik" to element pomiarowy, nie obiekt sieci. „Rogowiec" (E01) to prawdziwa stacja przy Bełchatowie; E02 „Rogów" wygląda na zgubione ziarno z E01.
- **Warianty:** 1) „stacje" / „stacje NN" zamiast GPZ w ustach Marty; GPZ zostawić przy OSD (Bydgoszcz pyta o zgodę). 2) „Stacja Rogowiec — przy Bełchatowie" (spłata E01) zamiast „GPZ Rogów, ... bocznika".
- **Rekomendacja:** 1 + 2. Krzyżanów (l.665) to prawdziwa stacja 400 kV koło Kutna — może zostać.

### E02-30 — Fizyka sieci: kierunek awarii i uzasadnienia decyzji — **ŚREDNIA**
- **Lokalizacja:** l.233–240, 812–813, 775–776, 1151–1155.
- **Cytaty:** „Drastyczny spadek napięcia. Do końca dnia / musimy odciąć zasilanie na wsie" (l.233–234); „Sieć przesyłowa / na dwudziestu dwóch procentach przepustowości." (l.812–813); „Możecie przyjąć na sieć przy kontrolowanym / odstawieniu dwóch bloków?" (l.775–776); „albo poczekać aż padnie chaotycznie i uszkodzi / transformatory" (l.1153–1154).
- **Ocena:** gdy umiera połowa ludzi i staje przemysł, zapotrzebowanie gwałtownie spada; typowym problemem jest wtedy nadmiar mocy, wzrost napięcia i częstotliwości oraz brak obsady do regulacji i usuwania awarii — a nie „spadek napięcia". Odcinanie wsi ma sens jako „nie mamy komu naprawiać sieci dystrybucyjnej", a nie jako oszczędzanie mocy. „Przepustowość" sieci przesyłowej nie jest tu ograniczeniem (trafniej: „generacja na 22% normalnego poziomu"). „Przyjąć na sieć" — niejasne (moc? obciążenie?). Kontrolowane wyłączenie chroniące przed niekontrolowanym blackoutem jest wiarygodne, ale argument „uszkodzi transformatory" lepiej zastąpić „stracimy możliwość ponownego uruchomienia (black start)".
- **Warianty:** 1) Krótka konsultacja z dyspozytorem/inżynierem KSE i korekta 4–5 kwestii. 2) Zostawić jako licencję dramatyczną.
- **Rekomendacja:** 1 — Marta jest „głosem kompetencji"; branżowy widz wyłapie te zdania.

### E02-31 — Paliwo, gaz, LNG — liczby i logika — **ŚREDNIA**
- **Lokalizacja:** l.191, 213–216, 248–251, 960–962.
- **Cytaty:** „Rafinerie mają paliwo na tydzień -- może dziesięć dni." (l.191); „Terminal LNG w Świnoujściu: marynarze byli mężczyznami." (l.215); „Gdańsk i Gdynia -- personel zszedł na ląd." (l.248); „Rezerwy / w krajowych magazynach -- na dwa, może trzy tygodnie." (l.960–961).
- **Ocena:** Polska utrzymuje zapasy obowiązkowe paliw na ok. 90 dni (problemem jest dystrybucja i obsługa, nie ilość). Krajowe magazyny gazu to kilka miliardów m³ — przy zapotrzebowaniu spadłym o połowę starczą na miesiące, nie tygodnie; brak też Baltic Pipe (gaz z Norwegii — ironiczny związek z Verą). Terminal LNG to obiekt lądowy; „marynarze" dotyczą gazowców, nie terminalu. „Personel zszedł na ląd" — załogi nie żyją, nie „zeszły".
- **Warianty:** 1) Przenieść akcent z ilości na obsługę: „Paliwa jest na miesiące. Nie ma komu go rozwieźć." / „Gaz jest. Nie ma komu obsługiwać tłoczni." 2) Zostawić liczby, ale dodać „przy obecnym tempie i bez obsługi".
- **Rekomendacja:** 1 — podnosi wiarygodność i wzmacnia temat „brak ludzi, nie brak zasobów".

### E02-32 — „Trzy nazwiska w całej Polsce" — **ŚREDNIA**
- **Lokalizacja:** l.828–838.
- **Cytat:** „Trzy nazwiska w całej Polsce -- wszystkie zajęte." (l.838); „Inżynier sieci bez mężczyzn..." (l.834).
- **Ocena:** inżynierek elektroenergetyków w Polsce są setki (w samym PSE, OSD, elektrowniach). Trzy to liczba niewiarygodna; kłóci się też z sc. 1A („Kobiety z zakładów petro -- mamy listę ... jedenaście osób", l.193–194). Kwestia Wolskiej (l.834) jest niegramatyczna.
- **Warianty:** 1) „Dwieście nazwisk w całej Polsce. Każda ma już trzy stanowiska." 2) „Trzy w zasięgu dojazdu".
- **Rekomendacja:** 1.

### E02-33 — Biogazownia: „transformator w gazowni" i praca wyspowa — **ŚREDNIA**
- **Lokalizacja:** l.1622–1633, 1701–1709.
- **Cytaty:** „Transformator strzelił przy wejściu." (l.1622); „Mamy zapasowy agregat -- pali się od dziesięciu dni." (l.1623); „To musimy jeszcze zrobić jedno połączenie do transformatora w gazowni." (l.1708).
- **Sprzeczność:** transformator jest uszkodzony, a Marta chce się do niego podłączyć; „gazownia" nie istnieje na farmie (jest biogazownia). Kluczowa trudność techniczna — praca agregatu kogeneracyjnego bez sieci (tryb wyspowy, synchronizacja) — jest pominięta, a to dokładnie specjalność Marty. „Pali się" o agregacie czyta się jak „płonie".
- **Warianty:** 1) Marta: „Bez sieci ten silnik nie ma się do czego zsynchronizować. Przestawię go na wyspę." 2) „połączenie z rozdzielnicą domu, z pominięciem spalonego transformatora".
- **Rekomendacja:** 1 + 2 („Ale to na jutro" może zostać).

### E02-34 — Nota „żadnych eksplozji" vs sc. 7 — **ŚREDNIA**
- **Lokalizacja:** nota l.18–19; sc. 7 l.886–892, 907–911, 916–918.
- **Cytaty:** „Poza tym jednym uderzeniem -- żadnych eksplozji, żadnych katastrof / filmowych." (l.18–19) vs „Pożar na jednym z bloków ... Niski wybuch, nie kataklizm." (l.908–909); „Potem daleki grzmot. Nie burza." (l.918, katastrofa samolotu); pożar lasu (l.890–892).
- **Warianty:** 1) Nota: „żadnych eksplozji na ekranie z bliska; reszta — z daleka, w dźwięku". 2) Usunąć „Niski wybuch" z sc. 7 (zostawić dym i alarm).
- **Rekomendacja:** 1 (montaż katastrof jest potrzebny dramaturgicznie).

### E02-35 — Nota o wodzie dotyczy nieistniejącej sceny — **ŚREDNIA**
- **Lokalizacja:** l.2094–2097.
- **Cytat:** „VERA NA FARMIE: Wchodzi przez bramę i zaraz zaczyna robić / rzeczy użyteczne. ... Woda będzie ciekła po raz pierwszy w następnej scenie." (l.2094–2097).
- **Sprzeczność:** po sc. 15 następuje ognisko (17); żadna scena farmy nie pokazuje uruchomienia wody. Woda leje się wcześniej w Warszawie (l.728–731). Vera w sc. 17 siedzi „trochę poza kręgiem" i nie robi nic użytecznego. Nota jest pozostałością starszej wersji.
- **Warianty:** 1) Usunąć zdanie o wodzie. 2) Dodać w sc. 16 lub 15 beat: Vera naprawia pompę/studnię (spłata noty, „przetrwanie przez użyteczność").
- **Rekomendacja:** 1 (albo 2, jeśli metraż pozwoli).

### E02-37 — Zapieczętowany list w teczce (B7) — **ŚREDNIA**
- **Lokalizacja:** l.1972.
- **Cytat:** „Zapieczętowana koperta -- list, którego Marta jeszcze nie otworzyła."
- **Ocena:** POTWIERDZONE. W E03 teczka wraca (E03 l.1291, 1501, 1567, 1599), list — nie. W E03 l.1201 Piotr „zaczyna pisać list" — możliwy, ale niezaplanowany rym.
- **Warianty:** 1) List od Piotra „otworzyć, gdyby…" — Marta otwiera go w E03 po pierwszym kontakcie (sc. 10) albo Karolina w kwarantannie (15A). 2) Usunąć zdanie z E02.
- **Rekomendacja:** 1, z rymem do E03 l.1201 (Piotr pisze drugi list).

### E02-38 — Śmierć Dąbrowskiego bez beatu (C11) — **ŚREDNIA**
- **Lokalizacja:** sc. 3 l.399–410; E01 l.45–46 („umiera poza kadrem w Zero Day").
- **Ocena:** POTWIERDZONE. Naturalne miejsce na beat jest właśnie w sc. 3: Aga czyta publikację zmarłego ojca. Po naprawie E02-01 jedno spojrzenie lub notatka („Tata. 14 dni temu.") daje ten beat bez dodatkowej sceny.
- **Rekomendacja:** łączyć z E02-01.

### E02-52 — Obsada niepełna — **ŚREDNIA**
- **Lokalizacja:** l.33–49.
- **Ocena:** brak w obsadzie postaci mówiących lub widocznych: gen. Anna Sowa, Ministra Energetyki, Minister Infrastruktury, Minister Komunikacji, Beata, Ania, Joanna, Szeregowa Nowak, Dyżurna, Prezenterka, Policjantka, Głos w radiu, Hania i Zosia (śpią; E03 je pokazuje), Bożena (SMS). Brak też Piotra na zdjęciach.
- **Rekomendacja:** uzupełnić — to baza do Entity w Flow i do kontroli zasady „bez mężczyzn".

---

## 5. Zasada produkcyjna „w E02 nie ma mężczyzn w tle/kadrze" — każde miejsce

Źródło zasady: handoff §7 „Plan generowania": „(prompty do zrobienia — w E02 brak mężczyzn w tle)".

| ID | Waga | Scena, linia | Cytat | Problem | Propozycja |
|---|---|---|---|---|---|
| E02-M01 | WYSOKA | Prolog, l.70–72 | „Na pokładzie nieruchome cienie martwej / załogi." | Załoga = mężczyźni (E01 l.1243 „leżą postacie. Mężczyźni."). Martwi mężczyźni w kadrze. | Formalny wyjątek „martwi z E01" albo pokład bez ciał, tylko kaski i kombinezony. |
| E02-M02 | ŚREDNIA | Prolog, l.65–66, 83 | „kilka sylwetek przy konsolach"; „Sylwetki w budynku operacyjnym -- giną." | Płeć sylwetek nieokreślona (l.64 mówi tylko o „garstce kobiet"). | „kilka kobiecych sylwetek" w didaskaliach i w prompcie. |
| E02-M03 | ŚREDNIA | Sc. 3, l.368–370 | „Zdjęcie / przyklejone do krawędzi monitora: Paweł i dwie małe dziewczynki" | Mężczyzna na zdjęciu w kadrze. | Wyjątek „zdjęcia zmarłych" albo zdjęcie Agi z dziewczynkami (rym z E01 l.822–823). |
| E02-M04 | NISKA | Sc. 5A, l.620–621 | „GŁOS W RADIU / Wsparcia nie ma. Jesteście same." | Płeć głosu nieokreślona. | „GŁOS W RADIU (kobieta)". |
| E02-M05 | NISKA | Sc. 8, l.1254 | „Ktoś poza kadrem mówi coś cicho." | Głos nieokreślony. | „Asystentka poza kadrem". |
| E02-M06 | ŚREDNIA | Sc. 12, l.1521–1522 | „Inne kobiety też pakują auta. / Inni wynoszą rzeczy." | Forma męskoosobowa — sugeruje mężczyzn. | „Inne wynoszą rzeczy". |
| E02-M07 | NISKA | Sc. 13, l.1535–1536 | „Ktoś dostosował / sobie ciezarowke do prowadzenia." | Jeśli kierowca w kadrze — płeć nieokreślona. | „Jakaś kobieta…" albo bez kierowcy w kadrze. |
| E02-M08 | ŚREDNIA | Sc. 17, l.1949 | „Gdzieś z tyłu ktoś zaczyna śpiewać -- niski głos" | „Niski głos" czyta się jako męski (dźwięk). | „niski kobiecy głos" (alt). |
| E02-M09 | ŚREDNIA | Sc. 18, l.1969–1971 | „zdjęcia -- Piotrek przy rakiecie, ... Marta i Piotrek / razem" | Mężczyzna na zdjęciach. Kanon E03 wymaga tego zdjęcia (E03 l.1928). | Formalny wyjątek „Piotr na zdjęciach" — zapisać w zasadzie. |
| E02-M10 | WYSOKA | Sc. 19, l.2022–2026 | „Nie widać twarzy, tylko ciemne kształty. Kobiety, / jedna za drugą. ... Kilof zarzucony na ramię." | Sylwetki z narzędziami w nocy widz odczyta jako mężczyzn („przeżyli?") — fałszywy trop. E03 rozstrzyga: kobiety. | W prompcie i didaskaliach: kobiece sylwetki (długie włosy, chusty, spódnice/płaszcze); jedna lampa oświetla kobiecą dłoń. |
| E02-M11 | ŚREDNIA | Sc. 1A l.161, 177, 272, 278; 7A l.1001 | „ministrowie"; „MINISTER INFRASTRUKTURY"; „MINISTER KOMUNIKACJI" | Męskie formy → ryzyko mężczyzny w generacji. | Patrz E02-20. |
| E02-M12 | NISKA | Sc. 1, l.135 | „Ktokolwiek był na kasie -- zostawił ją." | Tylko tekst, poza kadrem — bez ryzyka, ale prompt nie może pokazać kasjera. | Bez zmian; uwaga w prompcie. |
| E02-M13 | NISKA | Sc. 1 l.113, 7 l.895–896, 8 l.1245–1248, 10 l.1302 | „Mówi do kamer."; „Za nią -- mniej personelu"; studio | Ekipy TV i personel nieopisane — generator doda mężczyzn. | W promptach: „all-female crew/staff". |
| E02-M14 | NISKA | Sc. 3, l.363–364 | „"Tomasz Kamiński, W-wa, 14.03 -- pacjent zero"" | Tylko napis; ryzyko, że ktoś doda zdjęcie pacjenta. | Bez zdjęcia na tablicy. |

Sceny sprawdzone i czyste: 1 (poza M12–M13), 2, 4, 4A, 5, 5B, 6, 6A, 6B, 6C, 9, 10 (poza M13), 12A, 14, 15, 16. Uwaga do notatki z przeglądu: uznała 5A i 8 za „bez problemu" — M04 i M05 to drobne, ale realne luki.

**Rekomendacja ogólna:** zapisać zasadę w dwóch zdaniach: „Żaden żywy mężczyzna w kadrze ani w dźwięku. Wyjątki: zmarli z E01 (prolog) oraz Paweł i Piotr na zdjęciach-rekwizytach." Każdy prompt E02 musi zawierać „all women, no men".

---

## 6. Punkty NISKIE

| ID | Lokalizacja | Cytat | Problem | Propozycja / rekomendacja |
|---|---|---|---|---|
| E02-27 | sc. 2 l.325; 4A l.588; 6 l.799 | „ten punkt w Bydgoszczy"; „Nic. Wracamy do Bydgoszczy."; „Napisz do Bydgoszczy, Łodzi i Krakowa." | ZAWĘŻONE: PSE to Warszawa (E01 l.127 „CENTRUM DYSPOZYTORSKIE PSE, WARSZAWA"); Bydgoszcz to węzeł/oddział regionalny (realnie jest tam regionalna dyspozycja). Sprzeczności lokalizacji nie ma; l.588 jest tylko dwuznaczne. | „Wracamy do sprawy Bydgoszczy." |
| E02-28 | 4A l.522; 6 l.758 | „(INTERCITY)"; „Intercity: Marta w PSE" | To autokorekta „INTERCUT" (montaż równoległy), nie „niejasny tag". | „INTERCUT". |
| E02-36 | nota l.2085–2086 | „Widzimy ją cztery razy -- coraz mniej otoczona ludźmi" | ZAWĘŻONE: cztery są **briefingi** (sc. 1, 4, 7 „BRIEFING 3", 8 „BRIEFING 4"); na ekranie Wolska jest 6 razy (1, 1A, 4, 7, 7A, 8), głosem 4 razy (4A, 6A, 6C, 12A). W sc. 4 brak opisu otoczenia, więc „coraz mniej" nie jest pokazane. | Nota: „Widzimy cztery jej wystąpienia…"; w sc. 4 dodać „za nią trzy kobiety". |
| E02-39 | 5A l.647; 5B l.701; 6C l.1147; 12A l.1449 | „Marta przejeżdża samochodem -- jedzie do PSE."; „Już dziewiąty dzień."; „Przez jedenaście dni pracowałyśmy bez przerwy."; „Jedenaście dni." | Marta jedzie do PSE w T+8 (skąd?), choć „bez przerwy" i nie była w domu; w T+12 to 12 dni, nie 11. | Usunąć „jedzie do PSE" (Marta jedzie po coś dla PSE) albo przyjąć „bez przerwy" jako hiperbolę; w 12A „Dwanaście dni" lub „Jedenaście dni i noc". |
| E02-40 | sc. 12 l.1496; sc. 1 l.145–147; sc. 4 l.506; 5B; 6B | „Przez te dni nie odebrałaś." | ZAWĘŻONE: Marta nie odbierała połączeń Karoliny (sc. 4), ale sama dzwoniła (5B, 6B), a w sc. 1 była „Krótka rozmowa". Zdanie jest prawdziwe częściowo. | „Przez te dni ty dzwoniłaś, kiedy chciałaś." albo usunąć beat z sc. 1. |
| E02-41 | sc. 12 l.1502; 17 l.1847–1852; 18 l.1985 | „Czy tata..."; „Mój mąż był... / Daleko."; „On żyje?" | Ten sam beat trzy razy w ciągu 2 dni; 12 i 18 niemal identyczne. | Zostawić 17 i 18; w sc. 12 zmienić temat (np. Michał). |
| E02-42 | 6B l.1062–1065 | „Idź teraz zrobić zakupy. / Ryż, konserwy, mąka. ... I gotówka -- nie karta." | W T+10 wieczorem, po szabrowaniu z T+7–8 (5A) i kolejkach o ryż, „zakupy" są mało realne. | „Idź do Basi z trzeciego…" / „weź co jest w piwnicy"; albo świadomie: Karolina wraca z niczym (beat). |
| E02-43 | sc. 9 l.1278–1280 | „Ekran ciemny. / Próbuje go odblokować -- nic. / Próbuje hotspot, WiFi, wszystko." | Przy ciemnym (rozładowanym) ekranie nie da się sprawdzić hotspotu ani WiFi. | „Ekran: brak sieci. Bateria 3%." albo usunąć „hotspot, WiFi". |
| E02-44 | sc. 7 l.921, 928–929 | „Latarnie uliczne nie gasną rano -- nie paliły się w nocy."; „Ze studzienki kanalizacyjnej wydobywa się para. / Oczyszczalnia nie pracuje." | Warszawa miała prąd do rana T+11; para ze studzienki nie wynika z postoju oczyszczalni (raczej cofka, zapach). | „Latarnie wyłączone dla oszczędności"; „Ze studzienki cofa się woda." |
| E02-45 | 14 l.1588; 15 l.1739, 1752 | „Dobrze, że dojechałyście."; „Nie ma jej tu jeszcze."; „Wiedziałam że przyjedziesz." | Zofia „wie" o przyjazdach bez łączności (wieś bez prądu od T+3). „Nie ma jej tu jeszcze" (narracja) — a Aga jest w domu. | „Nie widzi jej." zamiast „Nie ma jej tu jeszcze"; Zofii wystarczy, że Aga ją uprzedziła (jedno zdanie). |
| E02-46 | 3B l.467 | „SMS. Numer polski." | W E01 Vera ma kontakt „Aga" ze zdjęciem (E01 l.822). | „SMS. Ekran: Aga." |
| E02-47 | 18 l.2003–2009; 19; 2046 | „Cięcie na czarny ekran. / E W A"; „KONIEC ODCINKA 2." | Tytuł dwa razy (po prologu i po 18), a scena 19 po napisie końcowym. Formalnie to „tag po tytule" — wymaga decyzji montażowej. | Zdecydować: (a) 19 jako tag po planszy (obecnie), (b) plansza „E W A" dopiero po 19. Rek.: (a), ale zapisać w nocie. |
| E02-48 | brak w E02; E03 l.180 | E03: „tam, gdzie wuj trzymał starą / dubeltówkę myśliwską" | Ani wuj (mąż Zofii), ani broń nie są zasiane w E02; Zofia w ognisku (17) nie mówi o własnej stracie. | W sc. 17 jedno zdanie Zofii o mężu („Stach polował. Zostawił mi psa i strzelbę."). |
| E02-49 | 7A l.986–989, 997–999; 1A l.253–254; 6 nota l.2092; 3 l.372; 12A l.1370; podróż Very | „Kontenerowiec z Gdańska ... Może być."; „Naftoport Gdańsk -- za dwa dni"; „Widz będzie się zastanawiał co się z nią stało." | Drobne wątki bez spłaty: kontenerowiec z nawozami, Naftoport, statek pod Helem, kobieta z elektrowni (celowe), Joanna, propozycja CZK, sposób dotarcia Very z Oslo (promy = męskie załogi wg 1A). | Świadomie zostawić; ewentualnie 1 linia w E03 (Sowa w E03 sc. 1) o kontenerowcu/Naftoporcie; 1 linia Very w 15 („przez Szwecję, samochodem"). |
| E02-50 | sc. 10 l.1302–1303 | „Ta sama bluzka / co dwa dni temu." | Prezenterka nie pojawia się wcześniej w E02; w E01 (T-1) „ta sama bluzka drugi dzień z rzędu" (E01 l.1143) — to 12 dni wcześniej. | „Ta sama bluzka co w dniu zero." (rym z E01). |
| E02-51 | sc. 7 l.907–911; 7A l.994–996 | „Alarm automatyczny wyje sam dla siebie. / Nikt nie jedzie."; „Pożar opanowany. Dwie ranne." | Ten sam wieczór: „nikt nie jedzie" vs „opanowany, dwie ranne". | „Wygasł sam. Dwie ranne z obsady." |
| E02-53 | 12A l.1370; E03 l.235 | „Centrum Zarządzania Kryzysowego"; E03: „Rządowe Centrum Kryzysowe" | Dwie nazwy instytucji (realnie: Rządowe Centrum Bezpieczeństwa). | Jedna nazwa w E02 i E03. |
| E02-54 | cały plik | — | Błędy językowe — lista w §7. | Korekta językowa bez zmiany treści. |
| E02-55 | 3 l.375; 6A l.825, 847 | „Doktor Bryk. ... Prosi żebyś zadzwoniła"; „Czego potrzebujesz?" ... „Dziękuję, pani Kowalska." | Przeskok formy pani/ty w jednej kwestii. | Ujednolicić (świadomie lub nie). |
| E02-56 | 3 l.388–393 | „"Nie naturalne. Zbyt czyste. / Ktoś to projektował. Kto?"" | B9 POTWIERDZONE: E02 rozstrzyga „dwie sekwencje" jako dowód inżynierii; wątek odporności nie istnieje. | Decyzja autora (handoff §5); E02 nie wymaga zmian, jeśli wybrać „inżynieria". |

---

## 7. Błędy językowe (tylko lista — NIE poprawiano)

Ortografia / brak znaków:
- l.672 „zacznij procedure" (procedurę); l.760 „rozmowa osob" (osób), „systemow" (systemów); l.782 „Dzwoncie" (Dzwońcie); l.792 „Dziękuje." (Dziękuję.); l.1251 „Chcialabym" (Chciałabym); l.1475 „dowod osobisty" (dowód); l.1536 „ciezarowke" (ciężarówkę), „skrzyzowaniu" (skrzyżowaniu); l.1950 „Nie ważne" (Nieważne); l.1945 „pół-śmiechem", l.1950 „pół-ludowa" (łącznie: półśmiechem, półludowa).

Fleksja / rodzaj / składnia:
- l.135 „Kobieta za lada" (za ladą).
- l.161 „Osiem kobiet -- ministrowie" (ministry).
- l.216 „porty nie mają komu przyjąć" (nie ma komu ich przyjąć).
- l.314 „bo nie było kogo obsłużyć późniejszej zmiany" (nie było kim obsadzić / komu obsłużyć).
- l.834 „Inżynier sieci bez mężczyzn..." (niegramatyczne; sens: „inżynierek sieci…").
- l.1151 „wyłączyć ją kontrolowanie" (w sposób kontrolowany).
- l.1458 „Nie panikowany" (niespanikowany / bez paniki).
- l.1461 „Nie dużo" (Niedużo).
- l.1468, 1481 „Mama --", „Mama, ty…" w wołaczu (Mamo) — niespójne z „Mamo" w innych scenach.
- l.1522 „Inni wynoszą rzeczy" (Inne).
- l.1669 „Jesteś informatykiem" (informatyczką).
- l.1860–1861 „coraz cisza, coraz głębia, aż do dna" (konstrukcja niepoprawna).
- l.192 „Obsługa techniczna to w dziewięćdziesięciu procentach mężczyźni" (czas: „to byli").
- l.248 „personel zszedł na ląd" (logika: załogi nie żyją).

Styl / sens:
- l.19 „Świat nie skończył się w ogniu -- w ogniu się nie skończył." (tautologia).
- l.425–426 „Na imię w notatniku." (to nazwisko z inicjałem: „Na nazwisko w notatniku").
- l.815 „Łódź -- od wczoraj tylko lewa strona." (niejasne: zachodnia część?).
- l.1546 „Znałaś ją?" (o własnej ciotce — dziwne; „Często u niej bywałaś?").
- l.1623 „agregat -- pali się" (dwuznaczne).
- l.1266 „te tradycyjne dwa tony" (sygnał kontrolny to jeden ton).
- l.1433 „mamki" (niani).
- l.2025 „Ostrze sztyletu" wśród narzędzi rolnych (nóż / sierp).
- Interpunkcja: masowy brak przecinków przed „że/żeby/które/kto/jak" (np. l.335 „Napisz że", l.423 „liczyć że", l.556 „Chcę żebyśmy", l.1749 „Wiedziałam że", l.1746 „powiedziała żeby").
- Formatowanie: l.134 — jedna niełamana linia, niezgodna z resztą montażu.
- Nagłówki: brak „T PLUS" w sc. 13–18 w tabeli; „Następny dzień" (l.1729) liczony od sc. 14, nie od poprzedzającej sc. 16.

---

## 8. Spójność prologu (T+9) z klamrą (sc. 19) i z końcem E01

- **E01 sc. 15 → prolog:** patrz E02-04 (kurs i dryf, doba przerwy, „ciągłość z ostatnim kadrem"). Zgodne: gazowiec LNG, świt, brak muzyki, port docelowy Świnoujście (E01 l.1252–1253).
- **Prolog → sc. 1A (T+3):** „Gazowce nie przypłyną -- porty nie mają komu przyjąć" (l.216) to dobra ironia wobec prologu (jeden przypłynął) — zostawić.
- **Prolog → sc. 7 (T+10) i 7A (T+10):** zgodne („dzień po uderzeniu", l.886; „Terminalu już nie ma. / Straciliśmy całą ostatnią obsadę.", l.953–954).
- **Prolog ↔ klamra 19:** rym działa (świt / głęboka noc, ogień / lampy naftowe, chłodny dystans / sylwetki, bez muzyki w obu). Prolog = katastrofa bez sprawcy, klamra = przemoc między kobietami — zgodne z notą (l.2102–2108).
- **Klamra 19 → E03:** zgodna co do Zofii (E02: „Zofia osuwa się na kolana, potem na ziemię. Nie rusza się.", l.2039; E03: „Żyje. Rozcięta / głowa", E03 l.202–203). „Dostaje w głowę" z handoffu jest tylko w E03 — E02 mówi „Głuchy odgłos uderzenia" (l.2037–2038). Liczba napastniczek: E02 „Dziewięć sylwetek" (l.2026); E03 nie podaje liczby — zgodne. Rozbieżności pozycji postaci — E02-23. Wezwanie Agi — E02-22. Broń — E02-48.

---

## 9. Weryfikacja wcześniejszych ustaleń (handoff §4 i notatki z 27.11)

| Ustalenie | Werdykt | Dowód (cytat, linia) | Komentarz |
|---|---|---|---|
| A1 Aga „V. Strand. Kim jest?" | **POTWIERDZONE, ROZSZERZONE** | l.410 „"V. Strand. Kim jest?""; l.399 „prof. Marek Dąbrowski"; E01 l.45–46 „ojciec Agi"; E01 l.654 „Tata dzwonił." | Aga nie rozpoznaje też ojca (E02-01). |
| A2 Wolska Katarzyna/Anna | **POTWIERDZONE** (międzyodcinkowo); notatka **OBALONA** w części | l.42, l.111 (Katarzyna); E03 l.13, 915 (Anna); l.165 „GENERAŁ ANNA SOWA" | Notatka: „Anna nie pojawia się przy Wolskiej w E02" — fałsz; Anna Sowa siedzi przy niej w 1A i 7A (E02-15). |
| A3 „osiemnaście lat temu" | **POTWIERDZONE** | l.400; E01 l.867, 870 | ~12 lat wg E01 (E02-14). |
| B7 list w teczce | **POTWIERDZONE, ROZSZERZONE** | l.1972; E01 l.158 (teczka w szafie PSE) | Dodatkowo teczka zmienia miejsce PSE → dom (E02-05). |
| B9 dwie sekwencje | **POTWIERDZONE** | l.388–393 | E02 rozstrzyga jako „projektowany" (E02-56). |
| B10 los Zofii | **POTWIERDZONE** (zgodne z E03) / handoff **ZAWĘŻONY** | l.2039; E03 l.202–203 | „W głowę" tylko w E03. |
| C11 śmierć Dąbrowskiego | **POTWIERDZONE** | brak beatu; l.399 | Miejsce na beat: sc. 3 (E02-38). |
| C12 „czterdziestu mężczyzn" | **POTWIERDZONE** (tylko naświetlone) | l.192, 205, 215, 249, 970–971; l.829 „Minimum czterdziestu." | „Czterdziestu" inżynierów — przypadkowy lub celowy rym z 40 mężczyznami Ares. |
| D15 numeracja | **POTWIERDZONE** | kolejność nagłówków (§1); l.2074–2075 | Handoff pominął sc. 7 w ciągu 6A→7A (E02-11). |
| D16 „Zofia Kowalska" | **POTWIERDZONE**; wniosek notatki **ZAWĘŻONY** | l.1416, 1429, 1435; E03 l.180 „wuj" | Nazwisko nie musi być panieńskim nazwiskiem Marty (E02-19). |
| Notatka: suma tabeli 70,5; nagłówków ok. 72–73,5 | **POTWIERDZONE** (dokładnie 73,5) | l.2051–2080 | E02-12. |
| Notatka: rozbieżności nagłówek/tabela (3, 7, 18, 3B) | **POTWIERDZONE** — jedyne | — | Pozostałe 25 pozycji zgodne. |
| Notatka: PSE Bydgoszcz vs Warszawa | **ZAWĘŻONE** | l.325, 588, 799; E01 l.127 | Bydgoszcz = węzeł regionalny; problem tylko w l.588 (E02-27). |
| Notatka: „Intercity" niejasny tag | **ZAWĘŻONE** | l.522, 758 | = INTERCUT (E02-28). |
| Notatka: 6A (NOC) vs 6B (19:15), sprzeczny stan mapy | **ZAWĘŻONE** | l.806–815, 882, 1087 | Spójne, jeśli 6A = noc przed T+10; problem etykiety (E02-09). |
| Notatka: duplikat końca 7 i 6C | **POTWIERDZONE, ROZSZERZONE** | l.931–933 vs 1234–1238 | Plus konflikt pory „świt" vs ok. 09:00 (E02-08). |
| Notatka: 12A plecak i torba vs 12 | **ZAWĘŻONE** | l.1345, 1461 | Samo w sobie nie jest sprzeczne; prawdziwy problem to teczka z E01 (E02-05). |
| Notatka: „Pani Premier" (6 miejsc) | **ZAWĘŻONE** | 7 miejsc (dodatkowo l.1376) | „Pani Premier" uzasadnione fabularnie (E01 l.1151, E03 l.915–916); niespójne są didaskalia „wicepremier" (E02-17). |
| Notatka: „przez te dni nie odebrałaś" sprzeczne z 5B/6B | **ZAWĘŻONE** | l.1496, 506 | Częściowo prawdziwe (E02-40). |
| Notatka: nota „cztery razy" fałszywa (≥5) | **ZAWĘŻONE** | l.2085; sc. 1, 4, 7, 8 | Cztery briefingi się zgadzają; obecności na ekranie jest 6 (E02-36). |
| Notatka: nota o wodzie | **POTWIERDZONE** | l.2097 | E02-35. |
| Notatka: lista „bez mężczyzn" (6 miejsc) | **POTWIERDZONE, ROZSZERZONE** | §5 | 14 miejsc; 5A i 8 nie są „bez problemu". |
| Notatka: 3B przed 4 | **POTWIERDZONE** | l.443, 476 | E02-06. |
| Notatka: 8 po 6C | **POTWIERDZONE** | l.1241 | E02-10. |
| Notatka: 16 przed 15, chronologia poprawna | **POTWIERDZONE** | l.1613, 1725 | Podpis „Następny dzień" mylący. |
| Notatka: „Dziewięć" niejasne | **POTWIERDZONE, ROZSZERZONE** | l.345; l.318 vs 341 | E02-25, E02-26. |
| Notatka: literówki i błędy | **POTWIERDZONE, ROZSZERZONE** | §7 | Doszły m.in. „za lada", „kontrolowanie", „procedure", „Dzwoncie", „pół-ludowa". |
| Decyzje: „Usunięta E02 Scena 11" WDROŻONE | **POTWIERDZONE** | brak „SCENA 11" | Luka w numeracji zostaje (D15). |
| Decyzje: pacjent zero Kamiński | **POTWIERDZONE** | l.364 | — |
| Decyzje: metraż ~66–67 | **POTWIERDZONE** (niewdrożone) | l.3 „ok. 65 minut" | E02-12. |

---

## 10. Docelowa numeracja i kolejność scen E02 (propozycja)

Zasada: kolejność chronologiczna (poza prologiem, który jest klamrą z E01), numeracja ciągła bez liter (pełny wariant: 1–30; wariant scalony: 1–28). Warianty z E02-03, 08, 10 przyjęte wg rekomendacji.

| Nowy nr | ← Stary | T+ / pora | Zmiana |
|---|---|---|---|
| PROLOG | PROLOG | T+9 (lub T+8, E02-04), świt | Bez zmian numeru. |
| 1 | 1 | T+1–T+2 | Montaż skrócony; bez komunikatu wodnego; napis „T PLUS 3 DNI" (E02-03). |
| 2 | 1A | T+3, 14:00 | — |
| 3 | 1 (beat Wolskiej) | T+3, wieczór | Komunikat Wolskiej = „Za godzinę jestem na antenie" (opcja; można dołączyć do 2). |
| 4 | 2 | T+3 | — |
| 5 | 3 | T+5 | — |
| 6 | 3B | T+5, noc (lub T+6) | E02-06. |
| 7 | 4 | T+5, wieczór | Jeśli 3B zostaje T+6 — zamienić 6 i 7. |
| 8 | 4A | T+6 | — |
| 9 | 5A | T+7–T+8 | (+ beaty T+4–T+8 z dawnego montażu 1). |
| 10 | 5 | T+9, świt | — |
| 11 | 6 | T+9, południe | E02-07. |
| 12 | 5B | T+9, wieczór | — |
| 13 | 6A | noc T+9/T+10 | Nagłówek doprecyzowany (E02-09). |
| 14 | 7 (część 1) | T+9 wieczór – T+10 popołudnie | Montaż kaskady do briefingu 3 (E02-08). |
| 15 | 6B | T+10, 19:15 | — |
| 16 | 7A | T+10, późny wieczór | — |
| 17 | 6C | T+11, 05:43 → ok. 09:00 | — |
| 18 | 8 | T+11, ok. 09:00 | Briefing przerwany wyłączeniem (E02-10). |
| 19 | 7 (część 2) | T+10 wieczór (rafineria) – T+11 ranek | Mini-montaż „po"; bez duplikatu Beaty/Ani. Opcjonalnie scalić z 20. |
| 20 | 9 | T+11, popołudnie | — |
| 21 | 10 | T+11, po 14:00 | — |
| 22 | 12A | T+12, 06:20 | Teczka z szafy w PSE (E02-05). |
| 23 | 12 | T+12, dzień | — |
| 24 | 13 | T+12, dzień | — |
| 25 | 14 | T+12, popołudnie | — |
| 26 | 16 | T+13, rano | — |
| 27 | 15 | T+13, wieczór | „Następny dzień" → „Tego samego dnia. Wieczór." |
| 28 | 17 | T+13, noc | — |
| 29 | 18 | T+13, późna noc | — |
| 30 | 19 KLAMRA | T+13, głęboka noc | Numer w nocie i w E03 zaktualizować. |

Uwaga: wariant z wydzielonym komunikatem (nr 3) i podziałem montażu 7 (nr 14 i 19) daje 30 numerów. Jeśli komunikat dołączyć do sc. 2, a część 2 montażu do sc. 20 — wychodzi **28 scen + prolog** (tyle, ile bloków ma dziś plik). Wariant minimalny (bez przebudowy treści): tylko przestawienie 3B/4, 5/6/5B, 8 przed 6B i przenumerowanie 1–28.

---

## 11. Skutki dla E01/E03 i plików produkcyjnych (zbiorczo)

- **E01:** E02-04 (sc. 15: kurs/światła terminalu), E02-05 (teczka w szafie PSE — wariant 1 nie wymaga zmian E01), E02-16 (Agnieszka/Ela), E02-25 (kolory mapy w Zero Day), E02-29 (Rogowiec).
- **E03:** E02-15 (Anna → Katarzyna, l.13, 915), E02-17 (tytuł „p.o. premiera" już zgodny), E02-21/22 (telefon i zgoda Agi w klamrze, l.234–247), E02-23 (pozycje postaci, l.116–159), E02-48 (wuj i dubeltówka, l.180), E02-37 (list w teczce), E02-53 (nazwa centrum).
- **Handoff:** §1 metraż, §3 oś czasu (T+8/T+9), §3 opis klamry („w głowę"), §4 D15 (dopisać sc. 7), §7 zasada „bez mężczyzn" z wyjątkami.
- **Pliki produkcyjne:** czytanka `ZERO_E02_EWA_Czytanie.pdf` do regeneracji po każdej zmianie; przyszłe pliki clip-po-clipie E02 nazywać dopiero wg nowej numeracji (§10); lista Entity do Flow z uzupełnionej obsady (E02-52); legenda mapy jako jedna grafika post dla E01–E03 (E02-25); w każdym prompcie E02 „all women, no men" + wyjątki (§5).

---

## 12. Rekomendowana kolejność poprawek

1. **Decyzje kanonu (bez pisania):** Wolska = Katarzyna (E02-15); model wiedzy widza o Verze (E02-02); zakres zasady „bez mężczyzn" z wyjątkami (§5).
2. **Logika sc. 3:** rozpoznanie matki i ojca + beat Dąbrowskiego + data ~12 lat (E02-01, E02-38, E02-14). Od tego zależą sc. 15, 17 i E03 sc. 14.
3. **Struktura i chronologia:** montaż 1 i komunikat (E02-03), 3B/4, 5/6/5B, 6A, montaż 7, sc. 8 (E02-06…10) → nowa numeracja (E02-11, §10) → przeliczenie metrażu i nowa tabela (E02-12, E02-13).
4. **Rekwizyty i łączność:** teczka z PSE (E02-05), telefon satelitarny Agi i SMS-y (E02-21), Bożena (E02-24), list (E02-37).
5. **Styk z E01/E03:** prolog vs E01 sc. 15 (E02-04), klamra vs E03 (E02-22, E02-23, E02-48).
6. **Wiarygodność branżowa:** GPZ/Rogowiec, fizyka sieci, paliwo/gaz, „trzy nazwiska", biogazownia, mapa (E02-25, 26, 29–33) — najlepiej jedna konsultacja z inżynierem KSE.
7. **Noty i obsada:** E02-34, 35, 36, 52, tytuły (E02-17, 18, 20), Zofia (E02-19), Ania (E02-16).
8. **Korekta językowa** (§7) — na końcu, po zmianach treści; potem regeneracja czytanki.
