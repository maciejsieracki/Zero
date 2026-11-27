# E01 ADAM — krytyczny audyt rozbieżności

Data: 2026-11-27. Tryb: tylko odczyt. Niczego w R ani w scenariuszach nie zmieniono, żadnego skryptu z archiwum nie uruchomiono.

- **Źródło prawdy:** `R/ZERO_mini_serial_E01_ADAM_rev.md` (1263 linie, przeczytane w całości, L1–L1263). Wszystkie numery linii bez prefiksu dotyczą tego pliku.
- **Kanon i audyt:** `R/ZERO_HANDOFF_2026-10-11.md`, sekcje 2–5 (przeczytane w całości).
- **Weryfikowane notatki:** `docs/przeglad-2026-11-27/E01_scenariusz.md`, `decyzje_i_konsultacje.md`, `produkcja_i_budzet.md`, `E01_beaty_i_rozpiska.md` (w części dotyczącej scenariusza).
- **Kontrola krzyżowa (punktowa, grep + odczyt fragmentów):** `R/ZERO_mini_serial_E02_EWA_rev.md` (L355–420, L700–736, L1960–1992), `R/ZERO_mini_serial_E03_ARES_rev.md` (L820–840, L1350–1405, nagłówki scen). E02 i E03 nie były czytane w całości.
- R = `/tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/zero-unrar/Zero/`

Wszystkie warianty naprawy to **propozycje do decyzji autora**. Nie zmieniam dialogów i nie rozstrzygam za autora.

Skala wag: **KRYTYCZNA** = łamie logikę lub kanon; **WYSOKA**; **ŚREDNIA**; **NISKA**.

---

## 1. Podsumowanie

| Waga | Liczba | ID |
|---|---|---|
| KRYTYCZNA | 3 | E01-01, E01-02, E01-03 |
| WYSOKA | 10 | E01-04 … E01-13 |
| ŚREDNIA | 19 | E01-14 … E01-32 |
| NISKA | 13 | E01-33 … E01-45 |
| **Razem** | **45** | |

Najważniejsze odkrycia, których nie było we wcześniejszych notatkach:
- **E01-02:** Ares IV milczy już od T-11 (sc 6). Kłóci się to z T0 („SIGNAL INTERRUPTED") i z E03, gdzie Ford mówi: „Milczeliśmy przez trzy tygodnie".
- **E01-03:** w P2 Vera i Marek grają niespełnione napięcie, a pół minuty później są rodzicami pięciolatki.
- **E01-05:** w P3 „Tata dzwonił, pyta o obiad w sobotę", a tej samej nocy Marek stoi w tej samej kuchni.
- **E01-06:** „100%" pada na T-7, a T0 ma być kulminacją.
- **E01-09:** arytmetyka P4 („pięć + trzynaście lat") daje 18. To prawdopodobne źródło „osiemnastu lat" w E02 (A3).
- **E01-16:** Paweł umiera na T-1, a w E03 Aga mówi: „W pierwszym dniu".

---

## 2. Weryfikacja wcześniejszych ustaleń

### 2a. Audyt handoffu 11.10 (§4) — punkty dotyczące E01

| ID źródła | Status | Dowód (cytat, linia) | Komentarz / ID tego audytu |
|---|---|---|---|
| A1 (Aga „V. Strand. Kim jest?", E02 sc 3) | **POTWIERDZONE i POGŁĘBIONE** | E02 L410 `"V. Strand. Kim jest?"`; w E01 L514 `Mamma! Pappa powiedział…`, L824–825 `Kontakt: "Aga". Zdjęcie profilowe -- Aga z dwiema małymi dziewczynkami` | Po E01 widz już wie, że Aga jest córką Very, więc zgrzyt w E02 jest jeszcze większy. → E01-01 |
| A3 (data publikacji 18 vs 12 lat) | **POTWIERDZONE, ZAWĘŻONE co do przyczyny** | L867 `(VERA MA OKOŁO 52 LATA)`, L869 `"OSLO. DWA LATA PO WYJEŹDZIE Z WARSZAWY."` → 64−52 = ok. 12 lat; E02 L400 `Data: osiemnaście lat temu.` | E01 wspiera ok. 12 lat. Ale E01 L885–886 zawiera „pięć lat… i trzynaście lat" = 18. Liczba 18 prawdopodobnie przeszła stąd do E02. → E01-09 |
| A5 („u twojej mamy sąsiadki") | **POTWIERDZONE** | L1079 `Dziewczynki są u twojej mamy sąsiadki?`, L1082 `Tak. U Bożeny.` | Mama Agi jest w Oslo (L807). Kwestia dodatkowo sygnalizuje, że Aga ma żyjącą matkę. → E01-14 |
| A6 (Marta o „koleżance Agi… Marta ma na imię jak ja") | **ZAWĘŻONE** | L164–165 `ta koleżanka Agi Bryk ze studiów, Marta / ma na imię jak ja, dzwoniła ostatnio?` | Gramatycznie to NIE jest mówienie o sobie w 3. osobie, tylko o **innej** kobiecie o imieniu Marta. Obie lektury są wadliwe: albo istnieje trzecia, niewidoczna Marta, albo zdanie jest zepsutym autoodniesieniem. Kanon (Marta = przyjaciółka Agi ze studiów) w E01 nie wybrzmiewa. → E01-10 |
| B7 (list w żółtej teczce) | **POTWIERDZONE (dotyczy E02); w E01 brak zasiewu listu** | L154–158 (teczka do szafy), L582–583 (spojrzenie na szafę). E02 L1965–1972 (zawartość, list) | E01 zasiewa tylko teczkę, nie jej zawartość. Obietnicę z noty L26–27 spełnia dopiero E02. → E01-04 |
| B9 („dwie sekwencje / To niemożliwe") | **ZAWĘŻONE** | L1213–1219; E02 L388–394 `To samo porównanie co w E01… "Nie naturalne. Zbyt czyste. Ktoś to projektował. Kto?"` | Wątek NIE jest zawieszony. E02 sc 3 spłaca go jako dowód inżynierii. W E01 nie wiadomo, czym jest druga sekwencja. Kwestia WHO L1196 („Nie odnotowano żadnego przypadku przeżycia") zamyka wariant „naturalna odporność". → E01-32 |
| C11 (śmierć Dąbrowskiego bez beatu) | **POTWIERDZONE** | L46–47 `umiera poza kadrem w Zero Day`; montaż L1157–1224 nie zawiera ani ujęcia, ani wzmianki | → E01-12 |
| C12, C13, C14, A2, A4, B8, B10, D15, D16 | Nie dotyczą E01 albo E01 jest neutralny | Wolska w E01 bez imienia (L1151); E01 mówi „leczenia przyczynowego" (L847), bez „antidotum" | — |
| §3: „14 scen + montaż Zero Day + SCENA 15" | **POTWIERDZONE jako błąd handoffu** | Sceny 1–13, potem L1157 `SCENA 14 -- ZERO DAY`, potem L1226 `SCENA 15` | Montaż Zero Day JEST sceną 14. → E01-41 |
| §1: „E01 — ADAM (~65 min)" | **POTWIERDZONE jako rozbieżność** | L3 `Format: ok. 60 minut`; suma etykiet = 60,5 min | → E01-30 |
| §2: Dąbrowski „były partner" | **ROZBIEŻNE z E01** | L45 `Były mąż Very` | → E01-39 |
| §4 „Co jest spójne": bloki 24→52 grają z 64 | **POTWIERDZONE** | L183, L429, L613, L867 | Arytmetyka wieku Very, Agi i Dąbrowskiego jest poprawna (sekcja 4) |
| §4 „Co jest spójne": pacjent zero Kamiński | **ZAWĘŻONE** | E01 nie zawiera Kamińskiego ani daty 14.03 (jest w E02 L364) | Spójne między odcinkami tylko dlatego, że E01 milczy. Pojawia się za to problem drogi zakażenia Oslo → Warszawa. → E01-13 |
| §4 „Co jest spójne": ESA Darmstadt jako spłata ziarna z E01 | **ZAWĘŻONE** | L569–570, L1187–1188 | Ziarno jest, ale jego logika czasowa koliduje z E03. → E01-02 |

### 2b. `E01_scenariusz.md` (notatki z przeglądu)

| Ustalenie | Status | Komentarz |
|---|---|---|
| §1 23 segmenty (15 numerowanych + 4 P + 4 wstawki) | POTWIERDZONE | — |
| §3 suma CZAS ≈ 60,5 min | POTWIERDZONE | Przeliczone niezależnie (sekcja 3 niżej) |
| §4 kolejność W1/sc 4, sc 7/sc 8, W3/sc 9 | POTWIERDZONE | → E01-08 |
| §4 Michał: W3 09:47 vs sc 10 | POTWIERDZONE | → E01-07 |
| §5 „Tomasz Wiśniewski (Tomek)" | ZAWĘŻONE | L44 brzmi `Tomek Wiśniewski`, a pełne imię „Tomasz" nie pada |
| §5 Piotr nienazwany w scenach | POTWIERDZONE | → E01-11 |
| §7.1 cliffhanger z noty vs montaż | POTWIERDZONE + uzupełnienie | Beat „teczka + zdjęcie Piotra" istnieje, ale w E02 (L1965–1987). → E01-04 |
| §7.2 język Very (nota vs sceny) | POTWIERDZONE, ZAWĘŻONE | L53–55 częściowo przewiduje wyjątki (Oslo, teraźniejszość). Nie obejmują P4 (przeszłość, Oslo, po norwesku, L900) ani rozmów z Agą (P2, P3). → E01-15 |
| §7.3 „w E01 nie ma ich wspólnej sceny" | POTWIERDZONE | P2 L511–520, P3 L636–760 |
| §7.4 reveal Agi | POTWIERDZONE, ROZSZERZONE | Dochodzi sc 8 (zdjęcie dorosłej Agi z córkami w telefonie Very) i sc 12. → E01-01 |
| §7.5 dwie wersje przypisu | POTWIERDZONE | → E01-27 |
| §7.6 arytmetyka P4 | POTWIERDZONE | → E01-09 |
| §7.7 TVN24 vs Berlin (T-7) | POTWIERDZONE, ROZSZERZONE | Cała krzywa eskalacji jest odwrócona. → E01-06 |
| §7.9 sc 11 trzy nazwiska, dwa miejsca | POTWIERDZONE | → E01-20 |
| §7.10 dwóch „Marków" | POTWIERDZONE | → E01-20 |
| §7.11 zaimek w sc 9 | POTWIERDZONE | → E01-43 |
| §7.12 „Pappa"/„Tata" | ZAWĘŻONE | To nie sprzeczność: „Pappa" pada w kwestii po norwesku, „Tata" w kwestii po polsku. Zostaje tylko decyzja o języku domu. → E01-15 |
| §7.13 rzecznik WHO (rodzaj) | POTWIERDZONE | → E01-33 |
| §7.14 BSL-4 / „P3" | POTWIERDZONE, ROZSZERZONE | → E01-23 |
| §7.15 rs1799945 | POTWIERDZONE, ROZSZERZONE (anachronizm) | → E01-25 |
| §7.16 hotel w Oslo | POTWIERDZONE | → E01-38 |
| §7.17 krzesło/fotel | POTWIERDZONE | → E01-37 |
| §7.18 sc 15 w E01 czy w E02 | ZAWĘŻONE | E02 ma własny prolog T+9 (E02 L54), więc nie ma ryzyka podwójnego montażu. Sc 15 to zakończenie E01, a E02 je kontynuuje. → E01-29 |
| §8 „Mamma/Pappaaaaa — ujednolicić pisownię" | **OBALONE** | „mamma" i „pappa" to poprawna pisownia norweska. Przeciągnięcie „Pappaaaaa" jest celowe (dziecko) |
| §10 wyzwalacz P3 = teczka (L583) | ZAWĘŻONE | Między sc 6 a P3 stoi wstawka W2 (L588–603). Bezpośrednim wyzwalaczem jest SMS Michała. → E01-18 |
| §10 wyzwalacz P2 = „tata" (L396) | ZAWĘŻONE | P2 następuje bezpośrednio po SMS-ie Marty do Agi (L415–418). Mocniejszym wyzwalaczem jest imię „Aga" (→ mała Aga w P2). → E01-18 |

### 2c. `produkcja_i_budzet.md` i `decyzje_i_konsultacje.md` (w części o E01)

| Ustalenie | Status | Komentarz |
|---|---|---|
| prod. §4: „Vera po polsku… nie traktuję tego jako sprzeczności" | **OBALONE** | L56 („w E01 nie ma ich wspólnej sceny") jest fałszywe. P4 (L900) to Oslo w przeszłości po norwesku, poza wyjątkiem z L54–55. Vera teraźniejsza nie mówi w E01 ani słowa po polsku. → E01-15 |
| prod. §3 D12: suma czasów ≈ 57 min | **ZAWĘŻONE** | 57 min to suma BEZ wstawek (3,5 min). Ze wstawkami 60,5 min (zgodnie z nagłówkiem). „Różnica do sprawdzenia" dotyczy tylko handoffu (65) |
| prod. §2: „Dąbrowski umiera poza kadrem w Zero Day (02, 08, scenariusz)" | **ZAWĘŻONE** | Scenariusz mówi to tylko w obsadzie (L46–47). Montaż tego nie realizuje i widz się o tym nie dowie. → E01-12 |
| prod. §3 B: wiek Dąbrowskiego P2 ≈ 41, P3 ≈ 55, P4 ≈ 58 | POTWIERDZONE | Różnica 6 lat (L183 Vera 24, L204 Marek 30) |
| prod. §3 C9: „Marek" w sc 11 | POTWIERDZONE | → E01-20 |
| decyzje §3: „Marta–Aga zasiane — WDROŻONE (l.161–165)" | **ZAWĘŻONE** | Zasiew jest nieczytelny (E01-10) i w E02 nieopłacony (grep E02: brak „studi") |
| decyzje §3: metraż E01 „~52 + 62 s" niewdrożony | POTWIERDZONE | L3 „ok. 60 minut". → E01-30 |
| beaty C6/D6 (W3 vs sc 10; A5 w beatach) | POTWIERDZONE w części scenariuszowej | Plików beatów nie weryfikowałem (poza zakresem) |

---

## 3. Czasy trwania — przeliczenie etykiet CZAS

| Segment | Linia | CZAS (min) | Segment | Linia | CZAS (min) |
|---|---|---|---|---|---|
| Sc 1 | 62 | 3,5 | P3 | 611 | 5 |
| Sc 2 | 126 | 1,5 | Sc 7 | 765 | 3 |
| P1 | 181 | 4 | Sc 8 | 806 | 1,5 |
| Sc 3 | 257 | 2,5 | W3 (T-5) | 837 | 1 |
| Sc 4 | 292 | 3 | P4 | 865 | 3,5 |
| W1 (T-10) | 351 | 0,75 | Sc 9 | 926 | 3 |
| Sc 5 | 369 | 2 | Sc 10 | 975 | 2,5 |
| P2 | 427 | 4 | Sc 11 | 1005 | 3,5 |
| Sc 6 | 531 | 2 | Sc 12 | 1048 | 5 |
| W2 (T-7) | 588 | 1 | Sc 13 | 1106 | 2 |
| | | | W4 (T-1) | 1140 | 0,75 |
| | | | Sc 14 Zero Day | 1157 | 4 |
| | | | Sc 15 | 1226 | 1,5 |

- Teraźniejszość (sc 1–15): 40,5 min. Przeszłość (P1–P4): 16,5 min (27%). Wstawki: 3,5 min. **Razem 60,5 min.**
- Nagłówek L3: „ok. 60 minut". Zgodne.
- Rozbieżne źródła zewnętrzne: handoff §1 „~65", decyzje „~52 + czołówka 62 s", rozpiska „54–55". Szczegóły w E01-30.
- Wszystkie 23 segmenty mają etykietę CZAS.

## 4. Oś czasu w kolejności pliku (oznaczenia T)

Sc 1 (brak) → Sc 2 (brak, „TO SAMO RANO") → P1 → Sc 3 **T-14** → Sc 4 **T-9** → W1 **T-10** ↩ → Sc 5 T-9 → P2 → Sc 6 T-9 → W2 T-7 → P3 → Sc 7 **T-7** → Sc 8 **T-8** ↩ → W3 **T-5** → P4 → Sc 9 **T-6** ↩ → Sc 10 T-5 → Sc 11 T-4 → Sc 12 T-2 → Sc 13 T-1 → W4 T-1 → Sc 14 T0 → Sc 15 T+8.

↩ oznacza cofnięcie w czasie.

Wiek postaci w przeszłości (wszystkie spójne): Vera 24/35/49/52/64. Aga 34 obecnie, więc urodziła się, gdy Vera miała 30 lat. W P2 Aga ma 5 lat (L511 „4-5"), w P3 19 lat (L636). Marek: 30 w P1 (L204), 70 obecnie.

---

## 5. Rejestr rozbieżności

### KRYTYCZNE

#### E01-01 — Widz dowiaduje się w E01, że Aga jest córką Very (wbrew nocie i kanonowi)
- **Waga:** KRYTYCZNA
- **Lokalizacja:** nota L16; P2 L511–520; P3 L636–664, L709–760; sc 8 L824–825; sc 12 L1079
- **Cytaty:** L16 `Widz nie wie jeszcze, że Aga jest córką Very.`; L511–514 `Z pokoju: AGA (mała, może 4-5 lat) wybiega do kuchni. / AGA (po norwesku -- napisy polskie) / Mamma! Pappa powiedział…`; L640 `Mamo, jest coś do jedzenia?`; L824–825 `Kontakt: "Aga". Zdjęcie profilowe -- Aga z dwiema małymi dziewczynkami`
- **Sprzeczność:** P2 i P3 pokazują dziecko i nastolatkę o imieniu Aga, która mówi do Very „Mamma"/„Mamo". Sc 8 pokazuje w telefonie Very zdjęcie dorosłej Agi (znanej z sc 4 i 7) z dwiema córkami (L40 „Matka dwóch córek"). Najpóźniej w sc 8 (T-8) widz łączy fakty. Handoff §2 mówi, że widz „długo tego nie wie". E02 sc 3 (L410 „V. Strand. Kim jest?") zakłada niewiedzę samej Agi.
- **Warianty:**
  1. Zaakceptować reveal w E01 jako ironię dramatyczną (widz wie, postacie nie). Poprawić notę L16 i handoff §2. Przerobić E02 L410 na rozpoznanie (jak w A1).
  2. Zachować tajemnicę: w P2/P3 nie nazywać dziecka po imieniu i usunąć „Mamma"/„Mamo". W sc 8 kontakt opisać neutralnie (np. inicjał, zdjęcie bez twarzy dorosłej).
  3. Hybryda: P2/P3 bez zmian, ale z sc 8 usunąć zdjęcie dorosłej Agi. Widz podejrzewa, ale nie ma pewności do E02.
- **Rekomendacja:** wariant 1. Struktura P1–P4 i tak opowiada rodzinę Very, a wariant 2 wymaga wycięcia najlepszych scen. Dodatkowy plus: A1 w E02 i tak musi zostać naprawione.
- **Skutki:** E02 sc 3 (L406–410) do przepisania. E03 sc 14 (wyznanie) traci walor zaskoczenia dla widza, ale nie dla Agi. Handoff §2. Beaty P2/P3/sc 8, prompty Flow (zdjęcie profilowe) i PDF czytanki E01 przy zmianie wariantu 2/3.

#### E01-02 — Milczenie Ares IV: początek T-11, T0 „SIGNAL INTERRUPTED", E03 „trzy tygodnie"
- **Waga:** KRYTYCZNA (łamie logikę między odcinkami)
- **Lokalizacja:** sc 6 L531–533, L569–570; sc 14 L1187–1188; E03 sc 7 L833 (SOL 287 ≈ T+47–49)
- **Cytaty:** L569–570 `Ares IV milczy od czterdziestu ośmiu godzin. / ESA nie ma kontaktu.` (nagłówek T MINUS 9 DNI); L1188 `Miga ekran: "ARES IV -- SIGNAL INTERRUPTED."` (T0); E03 L833 `Milczeliśmy przez trzy tygodnie, bo potrzebowałam / pewności przed rozmową z Ziemią.`
- **Sprzeczność:**
  1. Statek milczy od T-11, więc przerwanie sygnału na T0 wymagałoby niepokazanego odzyskania łączności.
  2. Od T-11 do T+49 mija ok. 60 dni, a nie „trzy tygodnie".
  3. Ford tłumaczy milczenie potrzebą pewności przed rozmową z Ziemią. Na T-11 nikt na Ziemi (oprócz Very) nie wiedział o wirusie: WHO zbiera się dopiero na T-10.
- **Warianty:**
  1. Przesunąć telefon w sc 6 na później (T-1/T0) i połączyć z ekranem ESA w Zero Day. Milczenie zaczyna się wtedy przy T0. „Trzy tygodnie" w E03 trzeba wtedy też uzgodnić (T0 → T+49 to 7 tygodni).
  2. Zostawić T-11 jako awarię techniczną („zakłócenia", L575). Na T0 pokazać „SIGNAL LOST" po krótkim przywróceniu (wymaga 1 beatu). W E03 zmienić „trzy tygodnie" na liczbę zgodną z osią i oddzielić awarię od decyzji Ford.
  3. Zostawić E01 bez zmian, a w E03 zmienić kwestię Ford na „najpierw awaria, potem nasza decyzja".
- **Rekomendacja:** wariant 2. Zachowuje napięcie Marty od T-9 i wymaga najmniejszych zmian w E01. E03 L833 trzeba poprawić przy każdym wariancie.
- **Skutki:** E03 sc 7 (L833), ewentualnie E03 sc 8–10. Beaty sc 6 i Zero Day (ekran ESA), rozpiska, PDF E01/E03. Handoff §2 („pierwszy kontakt z Marsem").

#### E01-03 — P2: niespełnione napięcie między ludźmi, którzy już są parą z dzieckiem
- **Waga:** KRYTYCZNA (łamie logikę historii Very i Marka)
- **Lokalizacja:** P2 L429–436, L478–492, L495–526
- **Cytaty:** L435–436 `Para, która przez kilkanaście / lat nauczyła się myśleć razem.`; L480–481 `Coś jest w tej ciszy -- nie po raz pierwszy, widz to czuje. / Ale ani jedno, ani drugie nie robi nic.`; L486–491 `Jest późno. Jutro o ósmej mamy radę wydziału. / Wiem. Idę. / Wychodzi. On patrzy za nią przez chwilę.`; L497–499 `Mała kuchnia. Vera przy kuchence, Marek czyta przy stole. / Przy ścianie -- krzesełko dziecięce.`; L514 `Mamma! Pappa…`
- **Sprzeczność:** pierwsza połowa P2 gra prawie-pocałunek i rozstanie na noc („Wychodzi. On patrzy za nią"), czyli relację przed związkiem. Druga połowa („Inny dzień") pokazuje wspólny dom i pięcioletnią córkę. Przy Verze 35 i Adze 5 lat są razem co najmniej ok. 6 lat. Napięcie „nie po raz pierwszy, ale nic nie robią" nie ma sensu, a widz nie wie, kiedy zostali parą.
- **Warianty:**
  1. Przenieść scenę przy tablicy do P1 albo do osobnego bloku „ok. 5 lat po przyjeździe" (Vera ok. 29, przed narodzinami Agi). P2 zostaje wtedy tylko z kuchnią.
  2. Przepisać didaskalia L478–492 tak, by grały bliskość pary (np. on zostaje, ona mówi „nie siedź długo"), bez sugestii pierwszego razu.
  3. Dodać napis „Cięcie. Kilka lat później." przed kuchnią i przesunąć napis P2 na początek kuchni. Tablica wtedy ok. 5 lat po przyjeździe.
- **Rekomendacja:** wariant 3 albo 1. Zachowują scenę, która ma najlepszą chemię, i naprawiają oś. Wariant 3 wymaga dwóch napisów.
- **Skutki:** napisy P2 (L431) i ewentualnie dodatkowy napis. Wiek Very w beatach BlokP2 i w `06_przejscia_scen` (który i tak ma błędne „CZTERY LATA PÓŹNIEJ"). Charakteryzacja Very (6. wizerunek przy wariancie 1/3). Rozpiska i PDF E01.

### WYSOKIE

#### E01-04 — Cliffhanger z noty nie jest w montażu; odcinek nie kończy się na Zero Day
- **Waga:** WYSOKA
- **Lokalizacja:** nota L26–28; sc 14 L1157–1224; sc 15 L1226–1263
- **Cytat:** L26–28 `Odcinek kończy się Zero Day. Cliffhanger: Marta z żółtą / teczką i zdjęciem Piotra. Aga przy zwłokach Pawła. / Vera w hotelu patrzy na mapę świata.`
- **Sprzeczność:** w montażu Marta siedzi przy konsoli bez teczki (L1171–1173, L1200–1205). Zdjęcie Piotra nie występuje nigdzie w E01. Aga biegnie korytarzem (L1175) i porównuje sekwencje (L1213), a zwłok Pawła nie ma. Paweł umarł na T-1, więc „przy zwłokach" na T0 wymaga osobnego wyjaśnienia. Odcinek kończy się sc 15 (T+8), nie Zero Day. Spełniona jest tylko „Vera w hotelu… mapa świata" (L1183). Beat z teczką i zdjęciami istnieje, ale w E02 (L1965–1987).
- **Warianty:**
  1. Poprawić notę do faktycznego montażu (teczka i zdjęcie przeniesione do E02; Aga w labie; sc 15 jako ostatni obraz).
  2. Dodać do montażu 2 mikroujęcia: Marta otwiera szafę i patrzy na teczkę (bez otwierania, żeby nie zużyć beatu z E02) oraz Aga w kostnicy lub przy pustym łóżku OIT.
  3. Wariant 2, ale w pełnej wersji z otwarciem teczki. Z E02 sc 18 trzeba wtedy usunąć powtórzenie „widz widzi co w środku".
- **Rekomendacja:** wariant 1 + jedno ujęcie „Marta patrzy na szafę" z wariantu 2. Spłaca zasiew z sc 2 i sc 6 i nie zjada beatu z E02.
- **Skutki:** nota reżyserska i `01_nota_rezyserska`, `05_inserty_closeup` (teczka). Beaty Zero Day, rozpiska, PDF E01. E02 sc 18 tylko przy wariancie 3.

#### E01-05 — P3: „Tata dzwonił… obiad w sobotę", a Marek mieszka w tym samym domu
- **Waga:** WYSOKA
- **Lokalizacja:** P3 L654–658 vs L670–701, L734–735
- **Cytaty:** L654 `Tata dzwonił. Pyta, czy przyjdę w sobotę na obiad.`; L672 `Vera i Marek w kuchni. Aga śpi.`; L678 `Marek stoi przy zlewie.`; L735 `On powinien wyjść.`
- **Sprzeczność:** zaproszenie od ojca przez telefon na obiad sugeruje, że ojciec mieszka osobno. Tej samej nocy Marek stoi w kuchni wspólnego mieszkania, a Aga kilka tygodni później mówi „On powinien wyjść", czyli mieszka z nimi.
- **Warianty:**
  1. Zmienić treść kwestii na coś zgodnego ze wspólnym domem, np. ojciec dzwonił, że wróci późno albo że nie będzie na kolacji. Daje to ten sam podtekst kłamstwa.
  2. Uznać, że Marek już się wyprowadził. Wtedy kuchnia „tej samej nocy" wymaga zmiany: Marek przychodzi po rzeczy albo rozmowa jest telefoniczna lub na klatce.
  3. Obiad u babci lub rodziny Marka. Wymaga dopowiedzenia, inaczej zgrzyt zostaje.
- **Rekomendacja:** wariant 1. Zmienia jedną kwestię i wzmacnia scenę: „późne powroty" pasują do zdrady.
- **Skutki:** beaty BlokP3, rozpiska (L794–795 wg notatek), `07_podtekst_dialogowy` (P3), PDF E01.

#### E01-06 — Eskalacja „100%" jest odwrócona; kulminacja T0 nic nie dodaje
- **Waga:** WYSOKA
- **Lokalizacja:** W2 L593–594 (T-7); sc 7 L772–773 (T-7); sc 9 L932 (T-6); W3 L844–846 (T-5); sc 14 L1194–1196 (T0)
- **Cytaty:** L594 `WIRUS Y -- ŚMIERTELNOŚĆ BLISKA 100% U HOSPITALIZOWANYCH MĘŻCZYZN`; L772–773 `Śmiertelność wynosi już kilkadziesiąt procent wśród / hospitalizowanych.`; L932 `WHO POTWIERDZA -- ŚMIERTELNOŚĆ 100% U MĘŻCZYZN.`; L844–846 `…jest bliska / stuprocentowej.`; L1195–1196 `Śmiertelność u mężczyzn: / sto procent. Nie odnotowano żadnego przypadku przeżycia.`
- **Sprzeczność:**
  1. Tego samego dnia (T-7) telewizja podaje „bliska 100%", a lekarz z Berlina na zamkniętej konferencji „kilkadziesiąt procent". Eksperci wiedzą mniej niż pasek TV.
  2. Na T-6 WHO już „potwierdza 100%", na T-5 epidemiolog cofa się do „bliska", a T0 powtarza jako szok to, co WHO potwierdziło 6 dni wcześniej.
  3. Ten sam pasek WHO w sc 9 i w W2 (L593 „WHO POTWIERDZA") — powtórzenie formuły.
- **Warianty:**
  1. Ułożyć rosnącą krzywą: T-10 „niezidentyfikowane", T-7 „wysoka", T-6 „kilkadziesiąt procent", T-5 „bliska 100% w udokumentowanych", T0 „100%, brak przeżyć". Zmiany tylko w paskach W2 i sc 9.
  2. Zostawić liczby, ale w T0 przenieść akcent na „brak przeżycia" i skalę (globalnie), nie na procent.
  3. Zmienić kwestię lekarza z Berlina na zgodną z paskiem i uznać, że T0 to formalne ogłoszenie.
- **Rekomendacja:** wariant 1. Zmienia tylko paski (bez dialogów), więc to najtańsza poprawka.
- **Skutki:** beaty Wstawka T-7, Scena 9 i Zero Day, rozpiska (pasek W2 już tam rozjechany, wg notatek L658), `08_noty_techniczne` (wstawki TV), PDF E01. Bez wpływu na E02/E03.

#### E01-07 — Michał: wiadomość 09:47 „Jestem w szpitalu" vs „po wczoraj: nic" (ten sam dzień T-5)
- **Waga:** WYSOKA
- **Lokalizacja:** W3 L852–857 (T-5); sc 10 L975–986 (T-5, POPOŁUDNIE)
- **Cytaty:** L853–854 `Wiadomość od Michała, godzina 09:47: / "Jestem w szpitalu, to pewnie nic. Przyjdź dzisiaj?"`; L984–986 `Ostatnia wiadomość od Michała: "Gorączka trochę spada. / Nie martw się." Godzina: wczoraj, wieczór. / Po wczoraj: nic.`
- **Sprzeczność:** po południu T-5 „ostatnia wiadomość" jest z wczoraj, choć rano tego samego dnia przyszła wiadomość 09:47. Ciąg nie gra też emocjonalnie: „gorączka spada" (wczoraj) → „jestem w szpitalu" (rano) → cisza.
- **Warianty:**
  1. Przenieść W3 (albo sam SMS) na T-6 i ustawić: T-6 rano „Jestem w szpitalu", T-6 wieczór „Gorączka trochę spada", T-5 cisza. Pasuje do sc 9 (T-6).
  2. Zmienić etykietę w sc 10 na „dziś, 09:47" i usunąć „Gorączka spada" (wtedy ostatnią wiadomością jest W3).
  3. Przesunąć sc 10 na T-4.
- **Rekomendacja:** wariant 1. Daje najczystszy łuk nadzieja → cisza i porządkuje przy okazji E01-08.
- **Skutki:** beaty Wstawka T-5 i Scena 10 (inserty ekranu telefonu), `05_inserty_closeup`, rozpiska, PDF.

#### E01-08 — Kolejność scen cofa się w czasie (3 miejsca)
- **Waga:** WYSOKA (jeśli T-oznaczenia są napisami na ekranie; L289 i `06_przejscia_scen` wskazują, że tak)
- **Lokalizacja:** sc 4 L294 (T-9) → W1 L351 (T-10); sc 7 L767 (T-7) → sc 8 L808 (T-8); W3 L837 (T-5) → sc 9 L928 (T-6)
- **Cytaty:** L294 `T MINUS 9 DNI` → L351 `WSTAWKA MEDIALNA -- T MINUS 10 DNI`; L767 `T MINUS 7 DNI` → L808 `T MINUS 8 DNI`; L837 `WSTAWKA MEDIALNA -- T MINUS 5 DNI` → L928 `T MINUS 6 DNI`
- **Sprzeczność:** tor A ma być liniowy (L12 „T-14 do T=0"). Trzy cofnięcia bez sygnału retrospekcji mylą widza, bo bloki P są oznaczane osobno.
- **Warianty:**
  1. Przestawić segmenty: W1 przed sc 4; sc 8 przed sc 7 (albo przed W2); sc 9 przed W3.
  2. Zmienić etykiety: W1 → T-9, sc 8 → T-7, sc 9 → T-5 (rano). Uwaga: sc 9 „tata w szpitalu od wczoraj" wtedy się przesuwa.
  3. Mieszanka: przestawić W1 i sc 9, przetykietować sc 8.
- **Rekomendacja:** wariant 1. Nie zmienia treści, tylko kolejność. Przy okazji P4 wypada bezpośrednio po sc 8 (wydruk = wyzwalacz).
- **Skutki:** rozpiska sekundowa (kolejność), `06_przejscia_scen`, beaty (notka WT T-10 już rozjechana z pozycją), PDF czytanki (kolejność).

#### E01-09 — Arytmetyka P4 („pięć + trzynaście lat") i źródło „osiemnastu lat" w E02 (A3)
- **Waga:** WYSOKA
- **Lokalizacja:** P4 L884–886; P1 L183; P3 L613–615, L704; E02 L400
- **Cytat:** L885–886 `To są jej wyniki. Jej metodologia. Jej pięć lat pracy / przed wyjazdem i trzynaście lat przed tym.`
- **Sprzeczność:** 5 + 13 = 18 lat. Vera zaczęła projekt jako doktorantka w wieku 24 lat (L225–226, L467) i wyjechała ok. 50, czyli po ok. 26 latach. P2 (Vera 35) mówi o „wielu latach" pracy (L473). Liczba 18 pasuje za to do błędnego E02 L400 „osiemnaście lat temu". E01 poprawnie daje publikację ok. 12 lat temu (Vera 52).
- **Warianty:**
  1. Zastąpić liczby sumą zgodną z osią (ok. 26 lat; np. „ćwierć wieku").
  2. Usunąć liczby i zostawić „całe jej życie zawodowe".
  3. Zachować podział, ale zgodny z osią (np. „pięć lat w Oslo przed wyjazdem" — wymaga wyjaśnienia, co to znaczy).
- **Rekomendacja:** wariant 1 albo 2. Równolegle E02 L400 → „ok. dwanaście lat temu" (rek. handoffu A3).
- **Skutki:** E02 sc 3 L400. Beaty BlokP4 (jeśli narracja z lektora), rozpiska, PDF E01/E02. Handoff §5 (decyzja „Data publikacji").

#### E01-10 — A6: zasiew przyjaźni Marta–Aga jest nieczytelny (i nigdzie nieopłacony)
- **Waga:** WYSOKA
- **Lokalizacja:** sc 2 L161–173; sc 5 L415–418
- **Cytaty:** L164–165 `Słuchaj -- ta koleżanka Agi Bryk ze studiów, Marta / ma na imię jak ja, dzwoniła ostatnio?`; L167 `TOMEK (nie rozumiejąc pytania) / Co?`; L417–418 `"Aga, jutro możesz pogadać? Przepraszam, że znowu / o złej porze. M."`
- **Sprzeczność:**
  1. Gramatycznie Marta pyta o trzecią osobę, inną Martę. Kanon mówi, że to ona sama jest przyjaciółką Agi ze studiów.
  2. Podwładny z PSE nie ma powodu znać koleżanek Agi, a sam scenariusz zaznacza, że Tomek nie rozumie.
  3. W sc 5 Marta pisze do Agi bezpośrednio, więc nie potrzebuje pośredniczki.
  4. Ani w E01, ani w E02 (grep: brak „studi") przyjaźń nie wybrzmiewa wprost.
  5. Różnica wieku 38/34 i różne kierunki (medycyna vs analiza sieci) słabo pasują do „przyjaciółki ze studiów" (E01-40).
- **Warianty:**
  1. Usunąć wymianę z Tomkiem. Zasiew przyjaźni oprzeć na SMS-ie z sc 5 i dodać 1 linię kontekstu (np. podpis kontaktu „Aga (akademik)" albo zdjęcie).
  2. Przepisać pytanie tak, by dotyczyło samej Agi (np. czy dzwoniła Aga Bryk ze szpitala), bez zabawy imieniem.
  3. Zostawić zagadkę, ale opłacić ją w E02 (kim jest „druga Marta").
- **Rekomendacja:** wariant 1. Najprostszy, usuwa kwestię, której intencji nie da się odczytać, i zostawia czysty zasiew.
- **Skutki:** beaty Sceny 2 (b8–10 wg notatek), rozpiska (nie ma tej wymiany — wymaga ujednolicenia w drugą stronę), `07_podtekst_dialogowy`, PDF. Handoff §2 („przyjaciółka ze studiów") do potwierdzenia.

#### E01-11 — Piotr nie istnieje w scenach; telefon o Ares IV jest nielogiczny dla PSE
- **Waga:** WYSOKA
- **Lokalizacja:** obsada L34; sc 5 L395–402; sc 6 L540–583
- **Cytaty:** L34 `Żona Piotra Kowalskiego -- astronauty Ares IV.`; L542–543 `Marta -- masz pilny na wewnętrznym. Numer trzy.`; L559 `Rozumiem. Przekażę dalej.`; L569 `Ares IV milczy od czterdziestu ośmiu godzin.`
- **Sprzeczność:**
  1. Imię Piotra nie pada w żadnej scenie. Widz nie dowiaduje się, że mąż Marty jest na Ares IV. Najbliżej jest „przypomina tatę" (L396) i spojrzenie na teczkę (L582). Centralna ironia serialu (jedyni żywi mężczyźni są na Marsie) nie jest w E01 ustawiona.
  2. Informacja o łączności ESA przychodzi na wewnętrzną linię operatora sieci energetycznej. Marta odpowiada „Przekażę dalej", jak urzędnik, nie jak żona.
  3. Tomek zna sytuację („Zdarzało się", L575), a widz nie.
- **Warianty:**
  1. Dzwonić ma ESA lub agencja kosmiczna na komórkę prywatną Marty jako najbliższej rodziny. Zamiast „Przekażę dalej" np. „Rozumiem. Powiem córce". Plus jedno zdanie z nazwą (np. Tomek: „Piotr?").
  2. Zostawić telefon służbowy, ale dodać insert zdjęcia Piotra w mundurze misji (np. na tapecie telefonu w sc 5 lub sc 11).
  3. W sc 9 Karolina pyta „A tata?". Marta odpowiada wymijająco. Spina to z E02 „On żyje?".
- **Rekomendacja:** wariant 1 + 3. Dwie kwestie, które ustawiają cały wątek Ares dla E02/E03.
- **Skutki:** E03 (pierwszy kontakt, rozmowa Marta–Piotr) zyskuje podbudowę. Beaty Sceny 6 i 9, inserty (`05`), `08_noty_techniczne` („zakres wzmianek o Ares IV"), PDF.

#### E01-12 — C11: śmierć Dąbrowskiego jest zapowiedziana w obsadzie, a nie istnieje na ekranie
- **Waga:** WYSOKA
- **Lokalizacja:** obsada L45–47; sc 14 L1157–1224
- **Cytat:** L46–47 `Pojawia się tylko w scenach przeszłości / i umiera poza kadrem w Zero Day.`
- **Sprzeczność:** w montażu nie ma ani ujęcia, ani informacji. Widz E01 nie wie, że Dąbrowski żyje w teraźniejszości ani że umarł. E03 L1357–1381 („Dąbrowski… Łącznie z moim ojcem") zakłada, że to fakt znany.
- **Warianty:**
  1. W montażu: Vera w hotelu dostaje powiadomienie lub nekrolog (bez słów), albo patrzy na nazwisko na liście zmarłych naukowców.
  2. Aga dostaje telefon (bez dźwięku) i na sekundę przerywa porównywanie sekwencji.
  3. Zostawić poza kadrem, ale w sc 8 dać sygnał, że Marek żyje (np. data na wydruku, wzmianka w portalu).
- **Rekomendacja:** wariant 1. Jedno ujęcie bez dialogu daje ironię „krzywdziciel ginie od jej wirusa" (rek. handoffu C11).
- **Skutki:** E02 (reakcja Agi na śmierć ojca?) i E03 sc 14 dostają podbudowę. Beaty Zero Day (+1–2 beaty), rozpiska, PDF.

#### E01-13 — Epidemiologia: jedno uwolnienie w Oslo na T-14 → wieloogniskowa pandemia w 4 dni; pacjent zero w Warszawie
- **Waga:** WYSOKA (wiarygodność, kanon pacjenta zero)
- **Lokalizacja:** sc 3 L257–289; W1 L357–362 (T-10); sc 4 L326–328 (T-9); sc 14; E02 L364
- **Cytaty:** L282 `Już po wszystkim.`; L284–287 `Otwiera fiolkę. Praca trwa krótko. Zamknięta. Skończone. / … Fiolka jest pusta.`; L359–361 `niezidentyfikowane / zachorowania wśród mężczyzn w Niemczech, Francji / i Skandynawii.`; E02 L364 `"Tomasz Kamiński, W-wa, 14.03 -- pacjent zero"`
- **Sprzeczność:**
  1. Mechanizm uwolnienia jest niejasny: fiolka zostaje otwarta, „zamknięta" i jest pusta. Nie wiadomo, czy Vera uwalnia wirusa, czy niszczy ostatnią próbkę („Już po wszystkim" sugeruje, że to już się stało).
  2. Z jednego punktu w Oslo w 4 dni powstają ogniska w DE/FR/Skandynawii, a w 5 dni trzy przypadki na jednym oddziale w Warszawie. Do T0 (14 dni) umierają wszyscy mężczyźni na świecie. Bez wielu ognisk lub długiej fazy utajonej jest to nierealne.
  3. Pacjent zero jest z Warszawy (E02), a uwolnienie było w Oslo. E01 nie daje żadnego pomostu.
- **Warianty:**
  1. Ustalić, że sc 3 to zniszczenie ostatniej próbki, a uwolnienie nastąpiło wcześniej i wieloogniskowo (np. przez konferencję lub lotniska). „T-14" przestaje wtedy być dniem zero zakażeń.
  2. Ustalić, że Vera rozesłała wirusa (np. paczki, aerozol na lotnisku) i dodać 1 ujęcie w sc 3 lub sc 8 (lista adresów, bilety).
  3. Zostawić jako tajemnicę, ale dać Adze w E02/E03 kwestię o długim okresie bezobjawowym lub nosicielstwie kobiet.
- **Rekomendacja:** wariant 1 lub 2. Do decyzji autora, bo dotyka sedna fabuły. Dopiero potem rozstrzygnąć, kim jest Kamiński i jaki dzień to 14.03 (E01 nie ma żadnej daty kalendarzowej).
- **Skutki:** E02 sc 3 (pacjent zero), E03 (wyznanie Very, śledztwo). `08_noty_techniczne` (BSL-4), beaty Sceny 3. Handoff §2 (wiersz „Pacjent zero").

### ŚREDNIE

#### E01-14 — A5: „u twojej mamy sąsiadki"
- **Waga:** ŚREDNIA
- **Lokalizacja:** sc 12 L1079–1082
- **Cytat:** `Dziewczynki są u twojej mamy sąsiadki?` / `Tak. U Bożeny. Śpią już pewnie.`
- **Sprzeczność:** mama Agi (Vera) mieszka w Oslo (L807), a Bożena to niania (handoff §2; E02 L1433 „mamki dziewczynek"). Kwestia jest też drugim sygnałem reveal (E01-01). Składniowo niejasna („mamy sąsiadki" = sąsiadki mamy).
- **Warianty:** (1) rek. handoffu: „u Bożeny, u sąsiadki?"; (2) „U Bożeny?" (Aga: „Tak. Śpią już pewnie."); (3) zostawić, ale jako ślad, że Vera ma mieszkanie w Warszawie (wymaga decyzji kanonicznej).
- **Rekomendacja:** wariant 2. Najkrótszy, a Bożena jest już nazwana.
- **Skutki:** beaty Sceny 12 (b9), rozpiska, PDF.

#### E01-15 — Nota językowa sprzeczna ze scenami; teraźniejsza Vera nie mówi po polsku
- **Waga:** ŚREDNIA (decyzja wpływa na lektora i Flow)
- **Lokalizacja:** nota L50–56; sc 3 L281; P2 L432, L513–523; P3 L639–642, L711–715; P4 L900
- **Cytaty:** L52 `Vera mówi po polsku przez cały E01 -- z wyraźnym norweskim akcentem.`; L56 `Z Agą rozmawiały po norwesku -- ale w E01 nie ma ich wspólnej sceny.`; L432 `Polski prawie bez akcentu.`; L639 `AGA (po polsku, naturalnie)`; L711 `AGA (po norwesku -- napisy polskie)`
- **Sprzeczność:**
  1. Vera w teraźniejszości nie wypowiada ani jednego zdania po polsku (sc 3 po norwesku, sc 8 i 14 bez słów).
  2. L56 jest fałszywe: P2 i P3 to wspólne sceny.
  3. P4 (Oslo, przeszłość, po norwesku) nie mieści się w wyjątku L54–55.
  4. W P3 matka i córka mówią po polsku w kuchni (L639–642) i po norwesku przy pakowaniu (L711–715), bez reguły.
  5. Akcent: „prawie bez akcentu" przy Verze 35 (L432), a „wyraźny" przy Verze 64 (L52). Możliwe po 14 latach w Norwegii, ale nie jest to nigdzie powiedziane.
- **Warianty:** (1) przepisać notę na regułę: „po norwesku sama ze sobą i z Agą w chwilach intymnych; po polsku w pracy i domu"; (2) ujednolicić P3 do jednego języka; (3) dopisać w nocie, że akcent wrócił po latach w Oslo.
- **Rekomendacja:** 1 + 3. Bez zmian w dialogach.
- **Skutki:** beaty (notatki wskazują 3 sprzeczne konwencje: Sc 3, Sc 8, P2, P3), instrukcje Flow (dialogi EN — trzeba zdecydować, jak oddać norweski), lektor PL, PDF czytanki (napisy vs lektor). E02/E03 obsada „mówi po polsku z akcentem" (E02 L43).

#### E01-16 — Paweł umiera na T-1, w E03 „w pierwszym dniu"
- **Waga:** ŚREDNIA
- **Lokalizacja:** sc 13 L1106–1119; E03 L1401; nota L27
- **Cytaty:** L1108 `T MINUS 1 DZIEŃ`; L1119 `O czwartej czternaście.`; E03 L1401 `Mój mąż. Umarł o czwartej rano. W pierwszym dniu.`
- **Sprzeczność:** w E01 Paweł umiera dzień przed Zero Day, a E03 sugeruje dzień T0 (albo „pierwszy dzień choroby"). Do tego nota L27 każe Adze stać „przy zwłokach" na T0.
- **Warianty:** (1) E03: „Dzień przed Zero Day" albo samo „O czwartej rano"; (2) przesunąć sc 12–13 tak, by śmierć wypadła na T0 o 04:14 (wtedy sc 13 = świt T0, a montaż Zero Day zaczyna się od Agi); (3) uznać „w pierwszym dniu" za subiektywny skrót Agi (nic nie zmieniać).
- **Rekomendacja:** wariant 2. Synchronizuje E01, notę („przy zwłokach"), E02 („umarł w E01, o 04:14") i E03.
- **Skutki:** nagłówki sc 12–13, beaty, rozpiska, E03 L1401 (przy wariancie 1), PDF E01/E03.

#### E01-17 — Nota: „TOR B — Warszawa", „T-14 do T=0", „kończy się Zero Day"
- **Waga:** ŚREDNIA
- **Lokalizacja:** nota L12, L18, L26; P4 L866–869; sc 15 L1226–1228
- **Cytaty:** L18 `TOR B -- PRZESZŁOŚĆ: Warszawa, lata wcześniej.`; L869 `"OSLO. DWA LATA PO WYJEŹDZIE Z WARSZAWY."`; L12 `T-14 do T=0`; L1228 `T PLUS 8`
- **Sprzeczność:** P4 dzieje się w Oslo. Odcinek wychodzi poza T0 (sc 15 T+8, Bałtyk). Nota L14–15 wymienia trzy wątki równoległe, a pomija teraźniejszy wątek Very (sc 3, 8, 14).
- **Warianty:** (1) poprawić notę (Warszawa/Oslo; T-14 → T+8; cztery wątki); (2) zostawić notę jako zamysł, a sc 15 oznaczyć jako epilog/teaser.
- **Rekomendacja:** wariant 1 (tylko nota, zero wpływu na sceny).
- **Skutki:** `01_nota_rezyserska`, handoff §3.

#### E01-18 — Wyzwalacze bloków przeszłości (obietnica noty) spełnione częściowo
- **Waga:** ŚREDNIA
- **Lokalizacja:** nota L21–22; P1 (po sc 2), P2 (po sc 5), P3 (po W2), P4 (po W3)
- **Cytat:** L21–22 `Cztery bloki przeszłości rozmieszczone przez cały odcinek, / każdy wyzwolony przez coś w teraźniejszości.`
- **Sprzeczność:**
  - **P1** stoi przed pierwszym pojawieniem się Very w teraźniejszości (sc 3). Nie ma wyzwalacza poza samym nazwiskiem „Agi Bryk" (L164).
  - **P2** ma dobry wyzwalacz: SMS „Aga…" (L417) → mała Aga.
  - **P3** wyzwala W2 (kolejki, SMS Michała), a nie nic związanego z Verą. Teczka jest dwa segmenty wcześniej.
  - **P4** jest oddzielony od swojego wyzwalacza (wydruk w sc 8) wstawką W3.
- **Warianty:** (1) przestawić P1 za sc 3 (krzywa „Adam" → młoda Vera); (2) W3 przed sc 8, żeby P4 szedł bezpośrednio po wydruku (zgodne z E01-08); (3) złagodzić notę („bloki rozmieszczone rytmicznie").
- **Rekomendacja:** 1 + 2. Bez nowych treści.
- **Skutki:** rozpiska, `06_przejscia_scen`, PDF.

#### E01-19 — Obsada niepełna względem scen
- **Waga:** ŚREDNIA
- **Lokalizacja:** obsada L31–47 vs sceny
- **Sprzeczność:** obsada ma 8 pozycji. W scenach mówią lub grają: Joanna (L321), Marcin (L376), dyżurna (L542), Beata (L1011), Agnieszka i Ela (L1037), Kacper i Marek z PSE (wzmianki L1016), studentka (L196), doktorantka „Kaśka" (L622, L676), prezenterka (L355), epidemiolog (L843), premier (L1147), **Wicepremier Wolska** (L1151, kanon), lekarz z Berlina (L771), rzeczniczka WHO (L1194), kobieta w ESA (L1187), mała Aga i Aga 19 l., młoda Vera (P1–P4), Bożena (wzmianka). Wolska to postać kanoniczna i nie ma jej w obsadzie.
- **Warianty:** (1) dopisać role mówiące i Wolską; (2) dodać sekcję „Epizody" z wiekiem dla AI-castingu.
- **Rekomendacja:** 1 + 2.
- **Skutki:** `02_charakterystyki_postaci` (brak Joanny, Beaty, Kacpra wg notatek), Flow Entities, PDF (role w czytance).

#### E01-20 — Sc 11: „dwa miejsca puste" przy trzech nieobecnych; drugi „Marek"
- **Waga:** ŚREDNIA
- **Lokalizacja:** sc 11 L1009–1016
- **Cytaty:** L1009 `Sala normalnie wyglądająca -- ale dwa miejsca są puste.`; L1015–1016 `Dzwoniła jego żona. Ma gorączkę od przedwczoraj. / I Marek też nie będzie. I Kacper powiedział, że...`
- **Sprzeczność:** wymienione są trzy osoby (Tomek, Marek, Kacper), a puste są dwa miejsca. Do zajęcia są trzy stanowiska (Marta przy konsoli Tomka, Agnieszka R-19, Ela R-22) i Beata na R-16, czyli 4 przydziały. Imię „Marek" koliduje z Dąbrowskim, który w P1–P3 jest tak nazywany w didaskaliach (L434, L457, L483).
- **Warianty:** (1) „trzy miejsca są puste"; (2) zmienić imię „Marek" z PSE (np. Jacek); (3) obie zmiany.
- **Rekomendacja:** wariant 3.
- **Skutki:** beaty Sceny 11, PDF (czytanka TTS: dwóch „Marków" w jednym odcinku).

#### E01-21 — Sc 5: „byliśmy na wystawie" → „Idź oglądać wystawę. Dobranoc" po południu
- **Waga:** ŚREDNIA
- **Lokalizacja:** sc 5 L370, L388–389, L408
- **Cytaty:** L370 `INT. CENTRUM PSE -- POPOŁUDNIE`; L388–389 `KAROLINA (cicho, jakby z knajpy) / Mamo, byliśmy z Michałem na tej wystawie`; L408 `Tak. Idź oglądać wystawę. Dobranoc kochanie.`
- **Sprzeczność:** Karolina jest już po wystawie, w knajpie, a Marta każe jej „iść oglądać". „Dobranoc" pada po południu, a w sc 1 Marta mówi „do wieczora", więc Karolina wraca do domu.
- **Warianty:** (1) zmienić „byliśmy" na „jesteśmy" i opis „jakby z galerii"; (2) zmienić odpowiedź Marty („Wracaj ostrożnie. Do zobaczenia wieczorem"); (3) zmienić porę sceny na wieczór (wtedy sc 6 też, a telefon o Ares przesuwa się na wieczór).
- **Rekomendacja:** wariant 1. Zmienia jedno słowo i didaskalia.
- **Skutki:** beaty Sceny 5, rozpiska, PDF.

#### E01-22 — Wiedza świata w kolejnych dniach: „Tajemnicza choroba… trzeci przypadek w Berlinie" (T-8) po wieloogniskowym WHO (T-10); „wirus Y" w TV (T-7) przed odkryciem mechanizmu przez lekarzy (T-7)
- **Waga:** ŚREDNIA
- **Lokalizacja:** W1 L357–362; sc 4 L327–328; sc 8 L812–813; W2 L593; sc 7 L779–787
- **Cytaty:** L813 `"TAJEMNICZA CHOROBA MĘŻCZYZN -- TRZECI PRZYPADEK W BERLINIE."`; L593 `WIRUS Y (HYV-1): ŚMIERTELNOŚĆ U MĘŻCZYZN WYSOKA -- WHO POTWIERDZA`; L779–787 `Chromosom Y. Wirus rozpoznaje specyficzną sekwencję… / Ktoś to zaprojektował.`
- **Sprzeczność:** po kryzysowym posiedzeniu WHO na T-10 i trzech przypadkach na jednym oddziale w Warszawie na T-9, nagłówek „trzeci przypadek w Berlinie" na T-8 brzmi jak wcześniejszy etap. Na T-7 media mają już nazwę „wirus Y", a tego samego wieczoru lekarze na zamkniętym połączeniu przedstawiają mechanizm na chromosomie Y jak nowość.
- **Warianty:** (1) nagłówek sc 8 zmienić na skalę (np. „…SETKI PRZYPADKÓW W NIEMCZECH"); (2) nazwę „wirus Y" wprowadzić dopiero w W3 (T-5), a w W2 zostawić „HYV-1"/„nowy wirus"; (3) przenieść sc 7 przed W2.
- **Rekomendacja:** 1 + 2 (tylko paski i nagłówki).
- **Skutki:** beaty Wstawka T-7 i Scena 8, inserty (`05`), PDF.

#### E01-23 — Sc 3: laboratorium BSL-4 — szczegóły nierealne
- **Waga:** ŚREDNIA (wiarygodność)
- **Lokalizacja:** sc 3 L258, L265–266, L275–277
- **Cytaty:** L258 `INT. LABORATORIUM BIOSAFETY LEVEL 4, OSLO`; L266 `w kombinezonie P3`; L275–277 `Wyjmuje / z kieszeni żółtą karteczkę samoprzylepną. Zasłania obiektyw.`
- **Sprzeczność:**
  1. „P3" to oznaczenie poziomu laboratorium (odpowiednik BSL-3), a nie kombinezonu. W BSL-4 używa się kombinezonu nadciśnieniowego z zasilaniem powietrzem lub komór rękawicowych klasy III.
  2. W takim kombinezonie nie ma dostępnej kieszeni, a karteczka samoprzylepna nie przetrwałaby dekontaminacji.
  3. Do weryfikacji przez autora: według mojej wiedzy w Norwegii nie działa laboratorium BSL-4 (w krajach nordyckich ma je Szwecja, Folkhälsomyndigheten w Solnie). Jeśli tak jest, „BSL-4 w Oslo" to fikcja, którą warto świadomie oznaczyć.
- **Warianty:** (1) „BSL-3, Oslo" + kombinezon/fartuch, maska, karteczka z kieszeni fartucha; (2) BSL-4 jako fikcyjny instytut (nazwany), kombinezon nadciśnieniowy, kamerę zasłania czymś z wyposażenia; (3) zostawić i nie pokazywać szczegółów kombinezonu.
- **Rekomendacja:** wariant 2. Zachowuje grozę BSL-4, a fikcyjna nazwa instytucji przy okazji zmniejsza ryzyko prawne.
- **Skutki:** `08_noty_techniczne` (BSL-4), beaty i prompt Sceny 3 (kostium), `05_inserty` (karteczka).

#### E01-24 — Ślad prowadzi wprost do Very (fabuła E02/E03)
- **Waga:** ŚREDNIA
- **Lokalizacja:** sc 3 L275–277; sc 7 L790–791; P4 L877–889
- **Cytaty:** L791 `WHO i Interpol prowadzą śledztwo.`; L877–879 `Tytuł: "Selektywna kaskada odpornościowa przy sekwencji / chromosomu Y…" / Autor: prof. Marek Dąbrowski`; L889 `"Dane wstępne: V. Strand (materiały niepublikowane)."`
- **Sprzeczność:** mechanizm wirusa jest identyczny z tytułem opublikowanego artykułu z przypisem „V. Strand". Do tego w BSL-4 kamera była zasłonięta w dniu T-14. Śledztwo WHO/Interpolu znalazłoby Verę w dniach, a nie dopiero przez Agę w E03 (E02 sc 3 pokazuje, że wystarczy wpisać frazę w bazę, L396–397).
- **Warianty:** (1) zaakceptować i pokazać w E02/E03, że śledztwo upadło w chaosie (zmarli śledczy — mężczyźni); (2) zmienić tytuł artykułu na mniej jednoznaczny; (3) usunąć „Interpol" z sc 7.
- **Rekomendacja:** wariant 1 (jedna linia w E02/E03; spójne z premisą).
- **Skutki:** E02 sc 3, E03 (aresztowanie dopiero „na płycie lotniska", E03 L1886).

#### E01-25 — rs1799945: realny wariant genu HFE, a do tego anachronizm
- **Waga:** ŚREDNIA (wiarygodność dla widza z wiedzą)
- **Lokalizacja:** P2 L447
- **Cytat:** `Masz rację. Diabeł tkwi w wariancie rs1799945.`
- **Sprzeczność:** rs1799945 to wariant H63D genu HFE (chromosom 6, hemochromatoza), niezwiązany z chromosomem Y. Jeśli teraźniejszość to ok. 2026, P2 (ok. 29 lat wcześniej) wypada ok. 1997. Baza dbSNP i identyfikatory „rs" ruszyły w 1998, więc identyfikator nie mógł wtedy paść.
- **Warianty:** (1) fikcyjny opis bez numeru („w tym wariancie na Yp11"); (2) fikcyjny numer rs z przesunięciem P2 po 1998 (wymaga zmiany osi); (3) opis lokalizacji (np. „region AZF") zamiast identyfikatora.
- **Rekomendacja:** wariant 1 albo 3.
- **Skutki:** beaty BlokP2, PDF (TTS czyta numer), tablica w kadrze.

#### E01-26 — Epoka bloków przeszłości: P1 to ok. 1986, czyli PRL
- **Waga:** ŚREDNIA (produkcja, scenografia, logika)
- **Lokalizacja:** P1 L186, L188–191, L212–214
- **Cytaty:** L186 `"WARSZAWA. 40 LAT WCZEŚNIEJ."`; L212–213 `Przyjechałam na -- stypendium doktoranckie. / Departament wirusologii.`
- **Sprzeczność:** przy teraźniejszości ok. 2026 P1 przypada na ok. 1986 (PRL), P2 na ok. 1997, P3 na ok. 2011, P4 na ok. 2014. Scenariusz nie sygnalizuje epoki (kostium, technika: P4 „link", laptop, P3 bez telefonów komórkowych). Norweska doktorantka na UW w PRL jest możliwa, ale wymaga świadomej scenografii. „Departament wirusologii" to kalka; na UW mówi się „Zakład".
- **Warianty:** (1) dodać w notach technicznych epokę każdego bloku; (2) nie podawać „40 lat" i zostawić „lata wcześniej" (ale wtedy kłóci się z wiekiem 24/64); (3) przesunąć teraźniejszość w przyszłość (sci-fi), co przesuwa też P1.
- **Rekomendacja:** wariant 1.
- **Skutki:** `08_noty_techniczne` (kostiumy P1–P4), prompty Flow bloków (epoka, wnętrza, technika), E03 (dziś jako ~2026?).

#### E01-27 — Dwie wersje tego samego przypisu i jego miejsca
- **Waga:** ŚREDNIA (insert, ciągłość rekwizytu)
- **Lokalizacja:** sc 8 L817–819; P4 L888–889; E02 L405–406
- **Cytaty:** L817–819 `Na wierzchu strona tytułowa publikacji. … W przypisach, drobnym drukiem: "V. Strand (dane własne, niepublikowane)."`; L888–889 `W przypisach, drobnym drukiem, na stronie czternastej: / "Dane wstępne: V. Strand (materiały niepublikowane)."`
- **Sprzeczność:** różna treść przypisu. Raz jest na stronie tytułowej, raz na str. 14. E02 powtarza wersję z P4 (str. 14).
- **Warianty:** (1) w sc 8 przyjąć brzmienie z P4 i usunąć „strona tytułowa" (np. „wydruk otwarty na stronie czternastej"); (2) świadomie dwa różne dokumenty (wtedy oznaczyć, który jest który).
- **Rekomendacja:** wariant 1.
- **Skutki:** `05_inserty_closeup` (artykuł), beaty Sceny 8, tekst w kadrze (post).

#### E01-28 — „Ogłaszam stan wyjątkowy" w ustach premiera
- **Waga:** ŚREDNIA (fakt ustrojowy)
- **Lokalizacja:** W4 L1146–1149
- **Cytat:** `Ogłaszam stan wyjątkowy na terenie całego kraju.`
- **Sprzeczność:** w Polsce stan wyjątkowy wprowadza Prezydent na wniosek Rady Ministrów (art. 230 Konstytucji). Przy epidemii właściwy jest stan klęski żywiołowej, wprowadzany przez Radę Ministrów (art. 232). Premier nie „ogłasza" stanu wyjątkowego sam.
- **Warianty:** (1) „Rada Ministrów wprowadza stan klęski żywiołowej…"; (2) „Zwróciłem się do Prezydenta o wprowadzenie stanu wyjątkowego…" (zarazem pokazuje, że prezydent jest niedostępny lub chory); (3) zostawić jako licencję.
- **Rekomendacja:** wariant 1 albo 2. Wariant 2 daje dodatkowo informację o rozpadzie władzy pod przejęcie przez Wolską.
- **Skutki:** beaty Wstawka T-1, E02 (narady rządu Wolskiej, podstawa prawna), PDF.

#### E01-29 — Sc 15: statek na autopilocie 8 dni po T0; sc 15 vs handoff
- **Waga:** ŚREDNIA
- **Lokalizacja:** sc 15 L1226–1258
- **Cytaty:** L1228 `T PLUS 8`; L1249–1251 `kurs ustawiony, prędkość stała, autopilot trzyma linię. … SWINOUJSCIE -- / GAZOPORT.`
- **Sprzeczność:**
  1. Jeśli załoga zmarła najpóźniej na T0 (WHO L1196), statek płynąłby ze stałą prędkością co najmniej 8 dni. Na Bałtyku przy ok. 15–19 węzłach to ok. 3000+ mil morskich, więc dawno uderzyłby w ląd. Autopilot kursowy nie „pamięta portu", choć system śledzenia trasy (ECDIS track control) może prowadzić po trasie.
  2. Martwe ciała na pokładzie po 8+ dniach (opis „jakby przysnął").
  3. Format „T PLUS 8" bez „DNI" (por. L289).
- **Warianty:** (1) załoga zmarła niedawno (ostatni mężczyźni umierają po T0) — wymaga korekty kwestii WHO lub dopuszczenia późnych zgonów; (2) statek dryfował i ruszył z kotwicowiska lub był wcześniej w porcie; (3) zmienić T+8 na T+1–2, a E02 prolog (T+9) przesunąć.
- **Rekomendacja:** wariant 1 (najmniej zmian: „ostatni zgon na pokładzie" w E02 lub w notach) + ujednolicić format „T PLUS 8 DNI".
- **Skutki:** E02 prolog (T+9), beaty (sc 15 nie ma pliku), filtry platform (martwe ciała).

#### E01-30 — Metraż: 60 / 60,5 / 65 / 52+1 / 54–55
- **Waga:** ŚREDNIA
- **Lokalizacja:** L3; suma etykiet (sekcja 3); handoff §1; decyzje 2b; rozpiska
- **Cytat:** L3 `Format: ok. 60 minut`
- **Sprzeczność:** pięć różnych liczb w dokumentach projektu. Scenariusz jest wewnętrznie spójny (60 vs 60,5).
- **Warianty:** (1) przyjąć 60 min jako cel i poprawić handoff i decyzje; (2) przyjąć ~65 min (handoff) i dopisać ok. 4,5 min (np. beaty z E01-04/E01-12); (3) przyjąć ~52–55 min i skrócić sc 12 (5 min przy ok. 12 kwestiach) i P3.
- **Rekomendacja:** wariant 1. Scenariusz już tyle trwa, a beaty pokrywają ok. 50%.
- **Skutki:** handoff §1, `ZERO_decyzje_rewizja`, rozpiska sekundowa (błędne sumy wg notatek), plan generowania.

#### E01-31 — Wątki zasiane i nieopłacone w E01 (oraz w serialu)
- **Waga:** ŚREDNIA
- **Lokalizacja i cytaty:**
  - L102 `czy wzięłaś klucze od piwnicy, bo --` — w E01 bez spłaty; luźno w E02 L711, L734 („wiadra z piwnicy", „do piwnicy zajrzyj"). Częściowo opłacone.
  - L415–418 SMS Marty do Agi `jutro możesz pogadać? … znowu o złej porze` — bez odpowiedzi w E01. Nie wiadomo, o czym Marta chce rozmawiać (przed wiadomością o Ares, L569).
  - L377–381 Marcin `potrzebuję zgody na odłączenie czasowe` / `Daj mi pół godziny.` — bez spłaty (drobne, może zostać jako tło).
  - L164 „ze studiów" — w serialu nieopłacone (E01-10).
  - L582–583 teczka — spłata w E02 (E01-04).
- **Warianty:** (1) dać SMS-owi odpowiedź w E01 (np. w sc 11 Marta widzi „Aga: nie mogę, pacjenci"); (2) usunąć „znowu o złej porze" albo dookreślić temat (Piotr? Karolina?); (3) zostawić i opłacić w E02 (Marta i Aga rozmawiają przed exodusem).
- **Rekomendacja:** wariant 1. Jeden insert, a zarazem ustawia przyjaźń.
- **Skutki:** beaty Sceny 5 i 11, inserty, E02.

#### E01-32 — B9: „dwie sekwencje / To niemożliwe" — co jest drugą sekwencją
- **Waga:** ŚREDNIA
- **Lokalizacja:** sc 14 L1213–1219; sc 7 L800–803; E02 L388–394
- **Cytat:** L1214–1219 `Na ekranie dwie sekwencje genetyczne, ułożone obok siebie. / Porównuje je. … To niemożliwe.`
- **Sprzeczność:** w E01 nie wiadomo, co jest porównywane. E02 mówi „pogrubiła fragmenty, które są identyczne w obu… Nie naturalne", ale nie mówi, z czym jest porównanie. Do tego „To niemożliwe" (szok) i „Ktoś to projektował. Kto?" (E02) to inny stan wiedzy niż w sc 7 (L787: „Ktoś to zaprojektował" już na T-7). Wniosek Agi na T0 niczego nie dodaje do T-7, chyba że druga sekwencja jest osobista (np. z dawnych notatek matki).
- **Warianty:** (1) drugą sekwencją są stare dane matki lub ojca (np. z rodzinnego archiwum). „To niemożliwe" = rozpoznanie, a E02 przechodzi do „V. Strand" jako potwierdzenia (spina z E01-01); (2) dwie próbki od różnych pacjentów, identyczne (brak mutacji = sztuczne). Wtedy w sc 7 nie mówić jeszcze „zaprojektował"; (3) odporność/ocalały (wymaga zmiany L1196).
- **Rekomendacja:** wariant 1 (najmocniejsza ironia; wymaga decyzji o E01-01).
- **Skutki:** E02 sc 3, E03 sc 3 (L498–528 „Skąd masz dokładną sekwencję wektora?… od trzech tygodni"), handoff §5 („ocalały chłopiec").

### NISKIE

#### E01-33 — Rodzaj: „RZECZNIK WHO" przy „ta sama kobieta"
- **Lokalizacja:** sc 14 L1166, L1191–1194. **Cytat:** `Ta sama kobieta, co wcześniej / przy podium` / `RZECZNIK WHO (po angielsku…)`.
- **Problem:** niezgodność rodzaju w etykiecie postaci.
- **Warianty:** (1) „RZECZNICZKA WHO"; (2) „RZECZNIK WHO (kobieta)".
- **Rekomendacja:** 1.
- **Skutki:** PDF (czytanka czyta rolę), beaty Zero Day.

#### E01-34 — „Michał powiedział, że mu przypomina tatę" — czyj tata
- **Lokalizacja:** sc 5 L395–396. **Cytat:** `i Michał powiedział, że mu przypomina tatę.`
- **Problem:** gramatycznie chodzi o tatę Michała, a reakcja Marty sugeruje Piotra.
- **Warianty:** (1) „że przypomina mu twojego tatę" (Karolina: „…tatę"); (2) zostawić dwuznaczność celowo.
- **Rekomendacja:** 1, jeśli to jedyny zasiew Piotra (patrz E01-11).
- **Skutki:** beaty Sceny 5 (dodane „you too" wg notatek).

#### E01-35 — Sc 2: przestrzeń — „Przy wyjściu z sali… Idę do sali… wraca do monitorów"
- **Lokalizacja:** L161, L171, L173.
- **Problem:** Marta wychodzi z sali, mówi „Idę do sali" i wraca do monitorów w tej samej sali.
- **Warianty:** (1) „Przy automacie z kawą / w korytarzu" + „Wracam do sali"; (2) usunąć „Idę do sali".
- **Rekomendacja:** 1.
- **Skutki:** beaty Sceny 2 (blocking).

#### E01-36 — Mapa w PSE: sieć czy epidemia
- **Lokalizacja:** sc 2 L131–132 („mapa sieci… zielona"); sc 11 L1042 („więcej pomarańczowych punktów"); sc 14 L1201–1203 (`Mapa za nią prawie cała pomarańczowa. / Kilkanaście czerwonych punktów -- każdy z sygnałem alarmowym. / Od brzegów ku środkowi.`).
- **Problem:** ten sam opis „od brzegów ku środkowi" dotyczy mapy świata (L1162) i mapy w PSE. Nie wiadomo, czy pomarańczowe to awarie sieci (wtedy sieć pada przed T0, a E02 L714–716 mówi o „konserwacji kilku węzłów" na T+9), czy obsada stanowisk.
- **Warianty:** (1) zdefiniować w notach technicznych: pomarańczowy = stacje bez obsady; (2) w sc 14 mapa PSE zielona z kilkoma żółtymi (kontrast ze światem).
- **Rekomendacja:** 1.
- **Skutki:** `08_noty_techniczne` (sala PSE), prompty map.

#### E01-37 — Sweter Michała: krzesło/fotel; specyfikacja vs Flow; „mieszkanie" vs „pokój"
- **Lokalizacja:** L73 (`jasnożółty, z nadrukiem dinozaura w okularach`), L993 (`Na krześle w kącie pokoju`), L1001–1002 (sweter w ramionach Karoliny), L1180, L1208 (`na fotelu`), L1178 (`Mieszkanie Karoliny`) vs L976 (`POKÓJ KAROLINY`).
- **Problem:** zmiana mebla. W sc 10 Karolina trzyma sweter w ramionach, więc jego położenie na T0 trzeba ustawić. Kanon Flow mówi „DOKŁADNIE JEDEN zielony dinozaur", a scenariusz nie podaje koloru i dodaje okulary. „Mieszkanie Karoliny" sugeruje jej własne mieszkanie, a Karolina mieszka z Martą.
- **Warianty:** (1) wszędzie „fotel", „pokój Karoliny", dopisać „zielonego dinozaura w okularach" i zgrać z Flow; (2) zostawić i spisać w tabeli ciągłości.
- **Rekomendacja:** 1.
- **Skutki:** instrukcje Flow (okulary?), `05_inserty_closeup` (tabela ciągłości), Clip00–11 Sceny 1.

#### E01-38 — Vera w „anonimowym hotelu" mimo własnego mieszkania
- **Lokalizacja:** L1183 vs sc 8 L807–810.
- **Problem:** nie ma uzasadnienia, dlaczego Vera jest w hotelu.
- **Warianty:** (1) mikrouzasadnienie (walizka, bilet — ucieczka/ukrycie); (2) zmienić na jej mieszkanie.
- **Rekomendacja:** 1, jeśli E02 ma zaczynać się jej podróżą do Polski; w przeciwnym razie 2.
- **Skutki:** E02 (przybycie Very jako „nieznajomej"), lokacje Flow (−1 lokacja przy wariancie 2).

#### E01-39 — „Były mąż" (E01) vs „były partner" (handoff); nazwisko Agi „z d. Strand"
- **Lokalizacja:** L39, L45. **Cytat:** `Były mąż Very, / ojciec Agi.`
- **Problem:** handoff mówi „partner". Przy małżeństwie polskie dziecko zwykle nosi nazwisko ojca (Dąbrowska). „Z d. Strand" jest możliwe, ale przy „mężu" wymaga uzasadnienia. Nazwisko matki ułatwia za to ukrycie związku z Dąbrowskim.
- **Warianty:** (1) „były partner" w E01; (2) zostawić „mąż" i przyjąć, że rodzice wybrali nazwisko matki.
- **Rekomendacja:** 1 (zgodne z kanonem i z nazwiskiem).
- **Skutki:** handoff §2, `02_charakterystyki`, E02/E03 obsady.

#### E01-40 — Wiek i biografia: Marta 38 / Karolina 19 / Piotr 37; „przyjaciółka ze studiów" przy różnicy 4 lat
- **Lokalizacja:** L33–35; handoff §2 (Piotr 37 l.).
- **Problem:** Marta urodziła Karolinę w wieku 19 lat, a Piotr (37) został ojcem w wieku 18 lat. To możliwe, ale nigdzie nie skomentowane, a Marta jest „Dr". Aga (34) była na studiach, gdy Marta (38) już je kończyła, i to na innym kierunku.
- **Warianty:** (1) podnieść wiek Marty i Piotra do ok. 42–44; (2) zmienić „ze studiów" na „z akademika" lub „z wolontariatu"; (3) zostawić (młodzi rodzice jako cecha postaci).
- **Rekomendacja:** 2 (bez zmiany wieku, który jest kanonem w E02/E03).
- **Skutki:** E03 (Piotr 37), `02_charakterystyki`.

#### E01-41 — Liczba scen w handoffie
- **Lokalizacja:** handoff §3 („14 scen + montaż Zero Day + SCENA 15") vs L1157 (`SCENA 14 -- ZERO DAY`).
- **Problem:** handoff liczy montaż Zero Day osobno, a w scenariuszu to scena 14. Faktycznie jest 13 scen + Zero Day (sc 14) + sc 15, plus 4 bloki P i 4 wstawki (23 segmenty).
- **Warianty:** poprawić handoff.
- **Rekomendacja:** poprawić handoff.
- **Skutki:** handoff, rozpiska (22 pozycje, brak sc 15).

#### E01-42 — Motywacja Very: skala czynu vs pokazany motyw
- **Lokalizacja:** P3 L619–760, P4 L873–919, sc 14 L1184–1185.
- **Problem:** E01 pokazuje motyw prywatny (zdrada, kradzież: „Moje", L901) przy czynie globalnym. Handoff przyjmuje „motywacja Very = Dąbrowski" jako decyzję. To nie błąd logiczny, ale luka wiarygodności, którą E03 częściowo adresuje („Nie tylko przez niego", E03 L1371).
- **Warianty:** (1) dać w P4 jedną linię uogólnienia (np. kolejne odmowy grantów, wykluczenie z publikacji jako systemowe); (2) zostawić (decyzja kanoniczna).
- **Rekomendacja:** 2, z ewentualnym 1 jako drobnym wzmocnieniem.
- **Skutki:** E03 sc 14.

#### E01-43 — Sc 9: „On jest zdrowy. Ma gorączkę" — zaimek i sprzeczność w jednym zdaniu
- **Lokalizacja:** L938, L957–958.
- **Problem:** po zdaniu o ojcu Michała „on" jest niejednoznaczne. „Zdrowy, ale ma gorączkę" to celowe wyparcie, ale lektor potrzebuje jasnego adresata.
- **Warianty:** (1) „Michał jest zdrowy…"; (2) zostawić i dać didaskalię „(o Michale)".
- **Rekomendacja:** 2 (bez zmiany dialogu).
- **Skutki:** PDF, beaty Sceny 9.

#### E01-44 — Wolska „Wie, co będzie. Czeka." — możliwa lektura spisku
- **Lokalizacja:** W4 L1151–1154.
- **Problem:** didaskalia mogą sugerować wiedzę Wolskiej o wirusie (współudział), co nie jest kanonem. Wiek Wolskiej nie jest podany (beaty mają ~48, E02 ~58, E03 51).
- **Warianty:** (1) „Wie, że może zostać sama. Czeka."; (2) zostawić jako celową dwuznaczność (wtedy rozstrzygnąć w E02).
- **Rekomendacja:** 1 + podać wiek w obsadzie E01 po decyzji A2.
- **Skutki:** beaty Wstawka T-1 (wiek), E02/E03 (A2).

#### E01-45 — Błędy językowe (wypisane, NIE poprawione)
- **Waga:** NISKA (pojedynczo). W dialogach część może być świadomą stylizacją potoczną; wtedy oznaczyć jako zamierzone.

| Linia | Fragment | Uwaga |
|---|---|---|
| L39 | `Doktor chorób zakaźnych` | kalka; „lekarka chorób zakaźnych" / „specjalistka chorób zakaźnych" (powtórzone w E02 L37, E03 L10) |
| L164–165 | `ta koleżanka Agi Bryk ze studiów, Marta / ma na imię jak ja, dzwoniła ostatnio?` | składnia (E01-10) |
| L213 | `Departament wirusologii.` | kalka (na UW: Zakład); w ustach cudzoziemki dopuszczalne jako błąd postaci |
| L241 | `Po polsku mówisz dobrze jak na pierwsze tygodnie.` | brak przecinka przed „jak" (dopuszczalne) |
| L327 | `Wczoraj wieczór.` | potocznie; normatywnie „wczoraj wieczorem" |
| L377 | `Mogę naprawić ale potrzebuję zgody` | brak przecinka przed „ale" |
| L389 | `na tej wystawie o której mówiłam` | brak przecinka przed „o której" |
| L435–436 | `Para, która przez kilkanaście / lat` | przy „ok. 11 lat po przyjeździe" granicznie poprawne; „przez lata" bezpieczniej |
| L601 | `Tata mówi żeby się nie panikować.` | „panikować" nie jest zwrotne („żeby nie panikować"), brak przecinka przed „żeby"; w SMS możliwa stylizacja |
| L782 | `Nikt nie ewoluuje z taką precyzją.` | logika: wirus to nie „nikt"; „Nic nie ewoluuje…" |
| L1024, L1037 vs L377 | `R-szesnaście`, `R-dziewiętnaście`, `R-dwadzieścia dwa` vs `R-17` | niespójny zapis oznaczeń (słownie vs cyfrą) |
| L1055 | `Lekarka i żona naraz. Obie wiedzą.` | „obie" odnosi się do ról, nie osób; stylistycznie ryzykowne dla TTS |
| L1076, L1087, L1103 | `Monitor bije.` | kalka/obrazowe; „monitor pika" (jeśli nie celowe nawiązanie do „serce bije") |
| L1079 | `u twojej mamy sąsiadki` | składnia (E01-14) |
| L1111 | `Za zmęczona na płacz.` | niezręczne; „Zbyt zmęczona, żeby płakać" |
| L1194 | `RZECZNIK WHO` | rodzaj (E01-33) |
| L1228 | `T PLUS 8` | format bez „DNI" (por. L259, L289) |
| L1250 | `SWINOUJSCIE -- GAZOPORT` | brak diakrytyków — poprawne, jeśli to ekran ECDIS/AIS (ASCII); oznaczyć jako zamierzone |
| L593 | `Pasek TVN:` | kanał TVN nie emituje pasków informacyjnych jak TVN24; do decyzji przy wymianie na fikcyjne marki |
| ogólnie | `--` vs `...` | mieszane style pauz (kosmetyka) |

---

## 6. Skutki dla plików produkcyjnych (zbiorczo)

| Plik / grupa | Punkty |
|---|---|
| Nota reżyserska (E01 L8–28) i `01_nota_rezyserska` | E01-01, -04, -15, -17, -18 |
| Obsada (L31–47), `02_charakterystyki_postaci`, Flow Entities | E01-19, -20, -39, -40, -44 |
| Beaty `ZERO_E01_*_beaty_7s_ENG.md` | E01-03 (P2), -05 (P3), -06 (W2, sc 9, ZD), -07 (W3, sc 10), -10 (sc 2), -11 (sc 6, 9), -12 (ZD), -14 (sc 12), -16 (sc 12–13), -21 (sc 5), -22 (sc 8, W2), -23 (sc 3), -25 (P2), -28 (W4), -33 (ZD) |
| Rozpiska sekundowa | E01-08 (kolejność), -18, -30 (sumy), -29/-41 (brak sc 15), plus wszystkie zmiany dialogów |
| `05_inserty_closeup` | E01-04 (teczka), -07 (ekran telefonu), -27 (przypis), -37 (sweter) |
| `06_przejscia_scen` (napisy czasowe) | E01-03, -08, -18 |
| `08_noty_techniczne` | E01-11 (Ares), -23 (BSL-4), -26 (epoka), -36 (mapa) |
| Instrukcje Flow / Scena 1 Clip00–11 | E01-15 (język), -37 (dinozaur w okularach) |
| PDF `ZERO_E01_ADAM_Czytanie.pdf` | regeneracja po każdej zmianie (szczególnie E01-14, -20, -33, -45) |
| E02 | E01-01 (L410), -09 (L400), -24, -29 (prolog), -31, -32 (sc 3) |
| E03 | E01-02 (L833), -12, -16 (L1401), -32 (sc 3), -42 |
| Handoff §1–§5 | E01-01, -02, -13, -30, -39, -41 |

## 7. Rekomendowana kolejność decyzji i poprawek

1. **Decyzje kanoniczne, od których zależy reszta:**
   - E01-01 (reveal Agi w E01: tak/nie),
   - E01-02 (oś milczenia Ares IV razem z E03),
   - E01-13 (mechanizm uwolnienia i pacjent zero).
2. **Twarde poprawki logiki w blokach przeszłości:**
   - E01-03 (P2: napis lub podział),
   - E01-05 (P3: jedna kwestia),
   - E01-09 (P4: liczby) razem z E02 L400.
3. **Oś czasu teraźniejszości (sama kolejność i paski, bez nowych treści):**
   - E01-08, -18 (przestawienia),
   - E01-06, -22 (paski TV),
   - E01-07 (SMS-y Michała),
   - E01-16 (śmierć Pawła na T0 lub korekta E03).
4. **Ustawienie wątków seryjnych (małe dopiski):**
   - E01-11 (Piotr),
   - E01-12 (Dąbrowski w Zero Day),
   - E01-04 (nota vs montaż + ujęcie szafy),
   - E01-10 i -31 (Marta–Aga),
   - E01-32 (druga sekwencja).
5. **Kwestie punktowe w dialogach:** E01-14, -20, -21, -28, -33, -34, -35.
6. **Fakty i wiarygodność:** E01-23, -25, -26, -27, -29, -24.
7. **Dokumentacja:** nota (E01-15, -17), obsada (E01-19, -39, -44), metraż (E01-30), handoff (E01-41).
8. **Na końcu, jednym przebiegiem:**
   - backup do `_backups/` → edycja → regeneracja beatów, rozpiski i czytanki PDF,
   - korekta językowa (E01-45) bez zmiany treści dialogów.
