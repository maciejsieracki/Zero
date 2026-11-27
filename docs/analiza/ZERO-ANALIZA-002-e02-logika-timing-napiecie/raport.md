# ZERO-ANALIZA-002 — E02 EWA: logika, timing, budowanie napięcia

**ID tematu:** ZERO-ANALIZA-002-e02-logika-timing-napiecie. **GOAL:** Dla odcinka E02 istnieje zweryfikowany raport z analizy logiki, timingu i budowania napiecia: z doslownymi cytatami, numerami linii, waga, wariantami naprawy (PROPOZYCJE) i kolejnoscia poprawek.

Data: 2026-11-27. Rola: Operator, runda 1 z 3. Tryb: tylko odczyt scenariusza; żaden plik w `scenariusze/` nie został zmieniony.

**Źródło rozstrzygające (rząd 1):** `scenariusze/ZERO_mini_serial_E02_EWA_rev.md`, 2108 linii, przeczytane w całości (L1–L2108, Read partiami: L1–400, L400–849, L850–1299, L1300–1749, L1750–2108). SHA-256 przed analizą: `1166c23dd0652dc76607167d9452263f036777a3ec0dbe1f35035c5610b4b093` (zgodny z `scenariusze/MANIFEST.sha256`).

**Materiał wejściowy (rząd 4, weryfikowany, nie przepisywany):** `docs/rozbieznosci/E02_audyt.md` (dalej: audyt; 545 linii, przeczytany w całości), `docs/przeglad-2026-11-27/E02_scenariusz.md` (dalej: notatki), `docs/przeglad-2026-11-27/decyzje_i_konsultacje.md` (dalej: decyzje, część o E02), handoff `ZERO_HANDOFF_2026-10-11.md` sekcje 2–5 (dalej: handoff, H). Wzór struktury: raport ZERO-ANALIZA-001 (E01).

**Konwencja cytatów.** `L123 \`tekst\`` = dosłowny fragment jednej linii pliku E02 (skopiowany z wyniku Read/grep, bez wcięcia z lewej). `H74 \`tekst\`` = linia handoffu. `E01:L1237` / `E03:L238` = linia sąsiedniego odcinka; te odwołania pochodzą z punktowego `sed -n`/`grep -n` i są oznaczone **na podstawie fragmentu** (E01 i E03 nie były w tym temacie czytane w całości; E03 nie jest przedmiotem analizy, służy wyłącznie do wskazania skutków).

**Konwencja propozycji.** Każdy wariant naprawy, rekomendacja i nowe brzmienie kwestii to **PROPOZYCJA** do decyzji właściciela (ECHO-003, G2, G3). Propozycje brzmienia są pisane kursywą jako zwykły tekst, nigdy w formacie cytatu. Nic z tego nie trafia do plików scenariuszy.

**Oznaczenie NIEPOTWIERDZONE.** Każde twierdzenie naukowe, techniczne, branżowe (energetyka, sieć, gaz, paliwa, telekomunikacja) lub o realnych instytucjach i obiektach, którego nie da się sprawdzić w tekście scenariusza, jest oznaczone NIEPOTWIERDZONE (w tym temacie nie weryfikowano go w źródle zewnętrznym).

Skala wag: **KRYTYCZNA** = łamie logikę odcinka albo kanon zapisany w samym pliku; **WYSOKA** = widoczna dla widza sprzeczność, istotna utrata napięcia albo sprzeczność kanonu między odcinkami; **ŚREDNIA** = sprzeczność drugoplanowa, wiarygodność, ciągłość, etykiety; **NISKA** = kosmetyka, dokumentacja, język.

---

## (a) Podsumowanie

### Stan odcinka w trzech wymiarach

- **LOGIKA:** świat jest opisany konsekwentnie w wielu drobnych punktach (np. wsie odcięte od prądu w T+3 L233–L234 i agregat na farmie, który L1623 `Mamy zapasowy agregat -- pali się od dziesięciu dni.` w T+13 — zgadza się co do dnia; duże miasta zostają do końca L235 i L814). Sypie się jednak trzy razy na poziomie kanonu i struktury: (1) Aga czyta publikację własnego ojca z przypisem własnej matki i pisze L410 `"V. Strand. Kim jest?"`; (2) nota i obsada twierdzą, że widz nie wie, kim jest Vera (L45), choć odcinek sam to mówi (L454, L1413, L1747); (3) montaż otwarcia dochodzi do T+8 i ogłasza decyzje, które rząd podejmuje dopiero w T+3 (L124–L126 vs L287–L290). Do tego sześć cofnięć osi czasu w kolejności pliku i numeracja scen niezgodna ani z kolejnością, ani z chronologią.
- **TIMING:** pięć różnych długości odcinka: nagłówek L3 `Format: ok. 65 minut`; tabela L2080 `RAZEM:                                                     ok. 69,0 min`; suma 28 pozycji tabeli = **70,5 min**; suma 29 etykiet CZAS = **73,5 min**; handoff ~67 i decyzje ~66–67. Cztery sceny mają różny czas w etykiecie i w tabeli (3, 7, 18) albo brak ich w tabeli (3B). Infrastruktura i państwo zajmują 24,5 min (33,3%), wydarzenia osobiste 38,5 min (52,4%), montaże i prolog 10,5 min (14,3%).
- **NAPIĘCIE:** dwa szczyty (6C wyłączenie sieci 9/10 i klamra 19 9/10) i mocny start (prolog 8/10). Środek odcinka (16:30–50:00) jest prowadzony prawie wyłącznie przez PSE, narady i mapy: wątek Agi znika na 33,5 min, wątek Very na 46,5 min. Najgłębsza dolina to przyjazd na farmę i biogazownia (13 → 14 → 16: 3, 3, 2) tuż przed sceną Very. Zakończenie sceny 7 ujawnia wynik sceny 6C, zanim 6C nastąpi.

### 10 najważniejszych punktów

1. **E02-01 (KRYTYCZNA, POTWIERDZONE):** Aga nie rozpoznaje ani ojca (L399 autor publikacji), ani matki (L406 przypis), a obsada mówi L37 `Dr Aga Bryk z d. Strand` i L40 `Córka Very Strand.`
2. **E02-02 (KRYTYCZNA, POTWIERDZONE):** L45 `Widz jeszcze tego nie wie.` przeczy L454, L1413, L1747 `Matka Agnieszki. Ona mi powiedziała żeby tu przyjechać.`
3. **E02-03 (KRYTYCZNA, POTWIERDZONE z zawężeniem):** komunikat T+2 (L124–L126) wyprzedza naradę T+3 (L287–L290, L302), a napis L154 `Napis biały na czarnym: T PLUS 8 DNI` cofa widza o pięć dni bez sygnału.
4. **E02-08 (WYSOKA, POTWIERDZONE):** montaż 7 kończy się L933 `Marta zostaje sama przy wygasłej konsoli.` przed sceną 6C, w której sieć dopiero jest wyłączana — zbyt wczesne ujawnienie i duplikat L1238.
5. **N-01 (WYSOKA, nowe):** między L476 a L1341 (33,5 min) Aga ma jeden beat w montażu (L873), Vera nie ma żadnego przez 46,5 min; osobiste stawki odcinka giną w sekwencji PSE.
6. **E02-12 (WYSOKA, POTWIERDZONE):** 65 / 69,0 / 70,5 / 73,5 min; rozbieżności etykieta–tabela w sc. 3, 7, 18 i brak 3B.
7. **E02-04 (WYSOKA, POTWIERDZONE):** prolog L70 `Dryfuje bokiem do` / L71 `wiatru, powoli, nieuchronnie.` i L54 `T PLUS 9` vs E01:L1237 `Płynie. Powoli, równo, prosto.` w T+8 (na podstawie fragmentu).
8. **E02-21 + E02-22 (WYSOKIE):** Aga ma telefon satelitarny znikąd (L1869) i przyjmuje wezwanie w E02 (L1872–L1875), które E03 pokazuje drugi raz (E03:L238, na podstawie fragmentu).
9. **E02-14, E02-15 (WYSOKIE, kanon):** L400 `Data: osiemnaście lat temu.` vs E01 P4 (~12 lat); Wolska L42 `Katarzyna` vs E03:L13 `ANNA WOLSKA` przy gen. Annie Sowie (L165).
10. **M01 i M10 (WYSOKIE, zasada „bez mężczyzn”):** martwa załoga w prologu (L71–L72) i nocne sylwetki z kilofem w klamrze (L2022–L2026), które widz odczyta jako mężczyzn.

### Decyzje kanoniczne wymagane od właściciela (skrót; pełna lista w sekcji f2)

D-01 model wiedzy widza o Verze; D-02 co Aga wie w sc. 3 (rozpoznanie matki i ojca); D-03 imię i wiek Wolskiej; D-04 data publikacji Dąbrowskiego; D-05 prolog T+8 czy T+9 i ruch statku (razem z E01 sc. 15); D-06 zasada „bez mężczyzn” i wyjątki; D-07 docelowy metraż; D-08 struktura montaży 1 i 7; D-09 nazwisko Zofii, jej mąż i los; D-10 kiedy Aga przyjmuje wezwanie i skąd ma telefon; D-11 teczka i list; D-12 tytuł „Pani Premier”; D-13 Ania czy Ela; D-14 plansza „E W A” przed czy po sc. 19; D-15 wariant numeracji; D-16 konsultacja branżowa KSE; D-17 obecność wątku Piotra w E02.

---

## (b) LOGIKA — zweryfikowana, zdeduplikowana lista rozbieżności

Numeracja E02-xx i E02-Mxx zachowana z audytu. Nowe punkty: N-xx. Przy każdym punkcie jest status weryfikacji audytu (sekcja c to zbiorcza tabela). Deduplikacja: E02-M11 = E02-20 (opisane tylko przy E02-20); E02-56 = handoff B9; E02-37 = handoff B7; E02-38 = handoff C11 (łączone z E02-01); E02-13 jest skutkiem E02-11 i E02-12; E02-40 obejmuje zarzut (c) z E02-03; część E02-49 (podróż Very) rozwinięta jako N-05.

### KRYTYCZNE

#### E02-01 — Aga nie rozpoznaje ani ojca, ani matki w publikacji (handoff A1)
- **Waga:** KRYTYCZNA. **Status audytu:** POTWIERDZONE (rozszerzenie audytu o ojca potwierdzone).
- **Lokalizacja i cytaty:**
  - obsada: L37 `Dr Aga Bryk z d. Strand    34 lata. Doktor chorób zakaźnych, Szpital Bielański.`; L40 `Córka Very Strand.`
  - sc. 3: L399 `Autor: prof. Marek Dąbrowski, Uniwersytet Warszawski.`; L406 `Małym drukiem: "Dane wstępne: V. Strand (materiały niepublikowane)."`; L410 `"V. Strand. Kim jest?"`
  - E01 (na podstawie fragmentu): E01:L45 `Prof. Marek Dąbrowski      70 lat. Polski wirusolog, UW. Były mąż Very,`; E01:L46 `ojciec Agi. Pojawia się tylko w scenach przeszłości`; E01:L654 `Tata dzwonił. Pyta, czy przyjdę w sobotę na obiad.`
- **Na czym polega sprzeczność:** córka z domu Strand czyta publikację ojca z przypisem o niepublikowanych danych matki i pyta, kim jest „V. Strand”. Nie reaguje też na nazwisko ojca. Skutek wewnątrz E02: w sc. 17 ta sama Aga prosi matkę L1885 `Potrzebują kogoś do analizy wirusa.` — czyli wie, że matka jest wirusolożką (obsada L43). Sc. 3 i sc. 17 nie mogą być prawdziwe jednocześnie bez rozpoznania w sc. 3.
- **Warianty naprawy (PROPOZYCJA):**
  1. Rozpoznanie matki i ojca; pytanie przeniesione na „co wiedziała”. PROPOZYCJA brzmienia notatki L410: *V. Strand. Mama. Tata to opublikował?* Tajemnica dla widza przechodzi z „kim jest” na „co zrobiła”.
  2. Rozpoznanie + pytanie o winę. PROPOZYCJA: *Tata i mama. Co oni zrobili?* — mocniejsze podłoże pod finał E03 (na podstawie fragmentu handoffu H133).
  3. Przypis anonimowy (kod próbki zamiast nazwiska). Usuwa sprzeczność, ale gubi rym z E01 i osłabia sc. 17.
- **Rekomendacja (PROPOZYCJA):** wariant 1, połączony z beatem śmierci ojca (E02-38) i datą (E02-14) w jednej poprawce sc. 3.
- **Skutki:** sc. 3B (SMS nabiera sensu: Aga pisze do matki zaraz po odkryciu), sc. 15 (powitanie L1778 `Dotarłaś.`), sc. 17 (L1890 `Wiesz co robisz?` zyskuje podwójne dno), nota L26–L30. E03: finał „wyznanie Very” (H133, na podstawie fragmentu) — Aga „potwierdza”, a nie „dowiaduje się”. Pliki produkcyjne: insert ekranu z przypisem (grafika w post), czytanka E02.

#### E02-02 — Nota i obsada zakładają, że widz nie wie, kim jest Vera; odcinek mówi to cztery razy
- **Waga:** KRYTYCZNA. **Status audytu:** POTWIERDZONE (część o wiedzy z E01 — na podstawie fragmentu).
- **Lokalizacja i cytaty:**
  - obsada: L44 `Przybywa na farmę jako nieznajoma. Matka Agi.`; L45 `Widz jeszcze tego nie wie.`
  - nota: L29 `Widz zaczyna to czuć w scenie 17 (ognisko) -- ale nie ma pewności.`; L30 `Pewność przychodzi w E03.`
  - sc. 3B: L454 `"Mamo. Żyjesz? Jedź do Polski.`; L465 `Vera przy biurku w pustym gabinecie.`; L473 `Wstaje. Zaczyna się pakować.`
  - sc. 12A: L1413 `Moja mama -- wysłałam do niej SMS żeby jechała do Polski.`; L1428 `Pisze SMS do Very:`; L1429 `"Mamo. Farma pod Łowiczem. Zofia Kowalska.`
  - sc. 15: L1746 `Dzień dobry. Jestem Vera Strand.`; L1747 `Matka Agnieszki. Ona mi powiedziała żeby tu przyjechać.`; L1778 `Dotarłaś.`
  - sc. 17: L1866 `Widz nie rozumie jeszcze dlaczego.`; tabela: L2074 `Scena 15   Vera przybywa jako nieznajoma                    ok. 2,0 min`
- **Na czym polega sprzeczność:** już w 15. minucie (sc. 3B) widz widzi SMS „Mamo” i jego odbiór w Oslo. W sc. 15 Vera przedstawia się Zofii jako matka. Nie jest „nieznajomą” ani dla widza, ani dla farmy. Z E01 (na podstawie fragmentu: E01:L37–L38 obsada oraz wnioski raportu ZERO-ANALIZA-001 o P2/P3/sc. 8) widz wie też, że Vera stworzyła wirusa. „Pewność w E03” może więc dotyczyć tylko wiedzy **Agi**. Zdanie L1866 jest nieprawdziwe dla widza, który zna E01 (rozumie, dlaczego Vera zamyka oczy na głos córki).
- **Warianty naprawy (PROPOZYCJA):**
  1. Przepisać notę, obsadę i tabelę na model „widz wie, Aga nie”. PROPOZYCJA brzmienia L45: *Widz wie, kim jest i co zrobiła. Aga nie wie.* PROPOZYCJA L1866: *Aga nie rozumie. Widz — tak.*
  2. Zachować „nieznajomą” tylko wobec farmy: Vera nie mówi, że jest matką. PROPOZYCJA L1746–L1747: *Dzień dobry. Jestem Vera. Szukam Agi Bryk.* Wiedzy widza to nie cofa (sc. 3B, 12A).
- **Rekomendacja (PROPOZYCJA):** wariant 1 (zgodny z E01 i z ironią dramatyczną z L26–L28).
- **Skutki:** nota L26–L30, obsada L44–L45, tabela L2074, sc. 17 L1866. E03: noty zakładające niewiedzę widza (sprawdzić w osobnym temacie). Pliki produkcyjne: charakterystyki postaci.

#### E02-03 — Montaż 1 wyprzedza akcję: komunikat T+2 = decyzja T+3; napis „T+8” przed powrotem do T+3
- **Waga:** KRYTYCZNA. **Status audytu:** POTWIERDZONE w częściach (a) i (b); **ZAWĘŻONE** w części (c).
- **Lokalizacja i cytaty:**
  - sc. 1: L100 `T PLUS 1 DO T PLUS 8`; L111 `T PLUS 2: Sala konferencyjna. Wicepremier KATARZYNA WOLSKA`; L124 `Zabezpieczcie źródła wody na kilka dni.`; L125 `Możliwe są przerwy w dostawach energii --`; L126 `jeśli macie dostęp do agregatu, przygotujcie go.`; L154 `Napis biały na czarnym: T PLUS 8 DNI`
  - sc. 1A: L159 `INT. SALA KONFERENCYJNA, KANCELARIA PREMIERA -- T PLUS 3`; L270 `Co mówimy społeczeństwu?`; L287 `Mówimy im żeby zabezpieczyli wodę. Mówimy`; L288 `że mogą być przerwy w zasilaniu. Mówimy żeby`; L289 `postarały się o agregat jeśli mogą. Mówimy`; L302 `Za godzinę jestem na antenie.`
- **Na czym polega sprzeczność:** (a) narada w T+3 decyduje, co powiedzieć społeczeństwu, a widz już w T+2 słyszał dokładnie te słowa; pytanie L270 traci stawkę. (b) Jedyny napis ekranowy z dniem w pierwszej połowie (L154) mówi „dzień 8”, a kolejne sceny (1A, 2, 3, 3B, 4, 4A) dzieją się w T+3–T+6. Nagłówki T+ scen nie są napisami ekranowymi, więc widz nie dostaje sygnału cofnięcia. (c) **Zawężenie:** audyt uznał beat L145–L147 (T+6, `Marta z PSE. Krótka rozmowa.`) za kolizję z sc. 4 (T+5, L506 `Nie odbiera.`). To różne dni, więc kolizji nie ma; zostaje tylko napięcie wobec L1496 (opisane w E02-40).
- **Warianty naprawy (PROPOZYCJA):**
  1. Montaż 1 skrócony do T+1–T+2, bez komunikatu o wodzie i agregatach (zostaje L116–L117), napis końcowy PROPOZYCJA: *T PLUS 3 DNI*. Beaty T+3–T+8 (sklep, kartki, szpital, balkon) przenieść do montażu 5A.
  2. Komunikat Wolskiej przenieść za 1A jako realizację L302 (krótki beat po naradzie).
  3. Zostawić sc. 1, a z 1A usunąć L286–L292 (decyzję „co mówimy”). Najsłabsze: L302 dalej zapowiada wystąpienie, które widz już widział.
- **Rekomendacja (PROPOZYCJA):** 1 + 2 łącznie.
- **Skutki:** numeracja wystąpień (L895 `Wicepremier Wolska -- BRIEFING 3.`, L1242 `INT. STUDIO TELEWIZYJNE -- BRIEFING 4`), nota L2085, tabela L2052. Czas sc. 1 maleje o ok. 1 min (sekcja d4).

### WYSOKIE

#### E02-04 — Prolog łamie ciągłość z E01 sc. 15 (kurs, czas, ruch statku)
- **Waga:** WYSOKA. **Status audytu:** POTWIERDZONE (numery linii E01 w audycie przesunięte o 1; argument o czasie dopłynięcia — NIEPOTWIERDZONE).
- **Lokalizacja i cytaty:** L54 `T PLUS 9`; L56 `Reżysersko: ciągłość z ostatnim kadrem odcinka pierwszego. Statek`; L71 `wiatru, powoli, nieuchronnie. Na pokładzie nieruchome cienie martwej` (poprzedzone L70 `Dryfuje bokiem do`). E01 (na podstawie fragmentu): E01:L1228 `T PLUS 8`; E01:L1237 `kopuły zbiorników jak katedry. Płynie. Powoli, równo, prosto. Za rufą`; E01:L1249 `kurs ustawiony, prędkość stała, autopilot trzyma linię. Na monitorze`; E01:L1255 `horyzoncie. Tam, daleko, majaczą światła terminalu. Statek widmo idzie`.
- **Na czym polega sprzeczność:** (a) w E01 statek idzie prosto na autopilocie, w E02 dryfuje bokiem; (b) w E01 o świcie T+8 światła terminalu są już widoczne, a uderzenie następuje o świcie T+9 — doba później (że statek przy stałej prędkości dopłynąłby w kilka godzin, to ocena NIEPOTWIERDZONE, zależna od niepodanej odległości i prędkości); (c) „ciągłość z ostatnim kadrem” sugeruje ten sam poranek. Wewnątrz E02 T+9 jest spójne: L886 `Świnoujście. Terminal LNG -- dzień po uderzeniu.` (T+10).
- **Warianty naprawy (PROPOZYCJA):** 1) prolog na T+8 (ten sam świt, kilka godzin później) i „idzie kursem” zamiast „dryfuje”; wtedy L886 zmienić na „dwa dni po uderzeniu”; 2) zostawić T+9, a w E01 sc. 15 usunąć „majaczą światła terminalu”; 3) zostawić T+9 i dryf, dopisać w didaskaliach prologu jedno zdanie: autopilot zgubił kurs w nocy.
- **Rekomendacja (PROPOZYCJA):** wariant 3 (zmienia tylko E02, nie rusza osi czasu z handoffu H140 i zachowuje L886).
- **Skutki:** handoff §3 oś czasu (H140), E01 sc. 15 (w wariancie 1 i 2), sc. 7 L886, sc. 7A L953. Prompt prologu musi przejąć model statku z E01 (E01:L1236 cztery kopuły, na podstawie fragmentu).

#### E02-05 — Żółta teczka: w E01 schowana w szafie PSE, w E02 Marta bierze ją z szafy w domu
- **Waga:** WYSOKA (główny rekwizyt łuku Marta–Piotr przez trzy odcinki). **Status audytu:** POTWIERDZONE (teczka, na podstawie fragmentu E01); **ZAWĘŻONE** (plecak i torba — samo w sobie nie jest sprzeczne).
- **Lokalizacja i cytaty:** E01 (na podstawie fragmentu): E01:L127 `INT. CENTRUM DYSPOZYTORSKIE PSE, WARSZAWA -- TO SAMO RANO`; E01:L158 `Marta odkłada teczkę do szafy. Zamyka. Bierze raport od Tomka.` E02: L1345 `Marta wychodzi z PSE z plecakiem i torbą.`; L1461 `Marta pakuje. Nie dużo -- plecak i jedna torba.`; L1477 `Marta przy szafie. Otwiera. Żółta teczka -- bierze.`; L1478 `Wkłada do plecaka między ubraniami.`; L1965 `Marta wyjmuje z plecaka żółtą teczkę.`
- **Na czym polega sprzeczność:** rekwizyt założony w szafie w PSE wraca z szafy w mieszkaniu. Wyjście z PSE „z plecakiem i torbą” i pakowanie „plecaka i jednej torby” w domu da się pogodzić (dopakowanie), więc to tylko niejasność.
- **Warianty naprawy (PROPOZYCJA):** 1) w 12A, przed wyjściem z PSE, Marta otwiera szafę i zabiera teczkę; w sc. 12 zostaje samo pakowanie ubrań; 2) beat zabrania teczki z PSE wcześniej (np. koniec 6C), w sc. 12 tylko przełożenie do plecaka; 3) zmienić E01 (teczka zabrana do domu).
- **Rekomendacja (PROPOZYCJA):** wariant 1 — obraz „Jedenaście dni” (L1449) z teczką z szafy spłaca ziarno z E01 i rozwiązuje kwestię toreb.
- **Skutki:** E01 bez zmian w wariancie 1; E03 (teczka u Karoliny, na podstawie fragmentu audytu) bez kolizji; lista rekwizytów.

#### E02-08 — Montaż 7 nakłada się na 6A, 7A, 6B, 6C; jego koniec ujawnia i dubluje 6C
- **Waga:** WYSOKA. **Status audytu:** POTWIERDZONE (części a, c); **ZAWĘŻONE** (b: konflikt „świt” zależy od tego, jak czytać trzy godziny; d: latarnie mogły być wyłączone oszczędnościowo).
- **Lokalizacja i cytaty:** L865 `T PLUS 9 DO T PLUS 11`; L913 `T PLUS 11, ŚWIT:`; L931 `Centrum PSE -- za oknem świt.`; L932 `Beata i Ania zbierają się do wyjścia.`; L933 `Marta zostaje sama przy wygasłej konsoli.`; L921 `Latarnie uliczne nie gasną rano -- nie paliły się w nocy.` Sc. 6C: L1115 `T PLUS 11, GODZINA 05:43`; L1176 `Zgoda. Trzy godziny od teraz.`; L1219 `Zielony punkt gaśnie.`; L1238 `Wychodzą. Marta zostaje sama.`
- **Na czym polega sprzeczność:** (a) w kolejności pliku widz widzi wygasłą konsolę i odejście Beaty i Ani (34:00–36:30), a cztery minuty po końcu montażu scenę, w której sieć dopiero jest wyłączana (40:30–44:30) — **zbyt wczesne ujawnienie** wyniku najmocniejszej sceny środka; (b) jeśli okno L1176 jest czasem na przejście szpitali na generatory, sieć gaśnie nie wcześniej niż ok. 08:43, a nie o świcie; jeśli przełączanie zaczyna się od razu (L1204 `Trzy kobiety przy mapie. Pierwsze przełączniki.`), świt jest możliwy — tekst nie rozstrzyga; (c) ten sam beat wyjścia pojawia się dwa razy (L932–L933 i L1238); (d) L921 przy L1087 `Prawie cała czerwona. Jeden zielony punkt -- Warszawa.` (T+10 19:15) — Warszawa miała prąd w nocy, ale tekst nie mówi, że latarnie musiały świecić.
- **Warianty naprawy (PROPOZYCJA):** 1) uciąć montaż na T+10 popołudnie (L894–L904, briefing 3); beaty T+10 wieczór i T+11 (rafineria, lotnisko, ulice, śmieci) przenieść za 6C jako krótki montaż „po wyłączeniu”; usunąć L931–L933; 2) cały montaż po 6C, bez beatów T+9–T+10 i bez beatu PSE; 3) tylko usunąć L931–L933 (usuwa duplikat i spoiler, nakładanie osi zostaje).
- **Rekomendacja (PROPOZYCJA):** wariant 1.
- **Skutki:** czas sc. 7 (etykieta 2,5 vs tabela 4,0 — E02-12); pierwsza muzyka (L867) — po podziale ustalić, w której części startuje; tabela L2063.

#### E02-11 — Numeracja scen niezgodna z kolejnością i chronologią (handoff D15)
- **Waga:** WYSOKA (produkcja: nazwy plików klip-po-klipie i plan zdjęciowy; ukrywa też cofnięcia osi). **Status audytu:** POTWIERDZONE; handoff D15 **ZAWĘŻONY** (pominął sc. 7 w ciągu 6A → 7A).
- **Lokalizacja i cytaty:** kolejność nagłówków w pliku (grep `^SCENA|^PROLOG`): L52 PROLOG, L98 1, L158 1A, L309 2, L357 3, L443 3B, L476 4, L521 4A, L592 5A, L652 5, L685 5B, L754 6, L804 6A, L863 7, L937 7A, L1048 6B, L1113 6C, L1241 8, L1270 9, L1298 10, L1341 12A, L1453 12, L1528 13, L1571 14, L1613 16, L1725 15, L1808 17, L1957 18, L2012 19. Brak `SCENA 11` (grep pusty). Tabela: L2074 `Scena 15   Vera przybywa jako nieznajoma                    ok. 2,0 min` przed L2075 `Scena 16   Biogazownia -- Marta i Karolina naprawiają (T+13) ok. 3,0 min` (odwrotnie niż w pliku); 3B w tabeli brak. Dodatkowo L1729 `Następny dzień. Wieczór. Prawie ciemno.` liczy „następny dzień” od sc. 14, a nie od poprzedzającej sc. 16.
- **Warianty naprawy (PROPOZYCJA):** 1) pełne przenumerowanie 1–28 po ustawieniu kolejności (sekcja f1, krok 4); 2) zachowawczo: zostawić numery, dodać w tabeli kolumnę „nr produkcyjny” i „kolejność T+”.
- **Rekomendacja (PROPOZYCJA):** wariant 1, ale dopiero po decyzjach struktury (E02-03, E02-08) — inaczej trzeba będzie numerować dwa razy.
- **Skutki:** nota L29 (`scenie 17`) i L2106 (`SCENA 19 (KLAMRA)`), tabela L2051–L2078, handoff §3, E03 (odwołania do sceny klamry, na podstawie fragmentu), czytanka.

#### E02-12 — Długość odcinka: pięć różnych liczb
- **Waga:** WYSOKA. **Status audytu:** POTWIERDZONE (przeliczone od zera, sekcja d1).
- **Lokalizacja i cytaty:** L3 `Format: ok. 65 minut`; L2080 `RAZEM:                                                     ok. 69,0 min`; L357 `SCENA 3  [CZAS: ok. 5 min]` vs L2055 `Scena 3    Szpital, Aga, wezwanie rządowe (T+5)             ok. 3,0 min`; L863 `SCENA 7  [CZAS: ok. 2,5 min]` vs L2063 `Scena 7    Kaskada montaż + katastrofy (T+9-11)             ok. 4,0 min`; L1957 `SCENA 18  [CZAS: ok. 3 min]` vs L2077 `Scena 18   Ognisko dogasa -- Marta i Karolina, teczka       ok. 2,0 min`; L443 `SCENA 3B  [CZAS: ok. 1,5 min]` (brak w tabeli).
- **Ustalenia:** suma 28 pozycji tabeli = 70,5 (nie 69,0); suma 29 etykiet = 73,5; handoff H43 i decyzje: ~67 i ~66–67. Składniki w sekcji d1.
- **Warianty naprawy (PROPOZYCJA):** 1) etykiety jako metraż roboczy (73,5) i cięcie do celu (sekcja d4); 2) tabela jako metraż i poprawa etykiet 3, 7, 18 + dopisanie 3B (= 72,0).
- **Rekomendacja (PROPOZYCJA):** po przebudowie z E02-03 i E02-08 policzyć od nowa; jedna liczba w L3, w tabeli i w handoffie (decyzja D-07).
- **Skutki:** budżet generacji, handoff §1, czytanka.

#### E02-14 — Data publikacji Dąbrowskiego (handoff A3)
- **Waga:** WYSOKA (kanon międzyodcinkowy). **Status audytu:** POTWIERDZONE (na podstawie fragmentu E01).
- **Lokalizacja i cytaty:** L400 `Data: osiemnaście lat temu.`; L43 `Prof. Vera Strand           64 lata. Norweska wirusolog. Mówi po polsku z akcentem.` E01 (na podstawie fragmentu): E01:L867 `(VERA MA OKOŁO 52 LATA)`; E01:L869 `Napis: "OSLO. DWA LATA PO WYJEŹDZIE Z WARSZAWY."`; E01:L885 `To są jej wyniki. Jej metodologia. Jej pięć lat pracy`; E01:L886 `przed wyjazdem i trzynaście lat przed tym.`
- **Na czym polega sprzeczność:** Vera widzi skradzioną publikację w wieku ok. 52 lat, dziś ma 64 → publikacja ok. 12 lat temu (najpóźniej). 18 lat temu Vera miała ok. 46 lat i według E01 była jeszcze w Warszawie, co psuje „ukradł po jej wyjeździe”. Prawdopodobne źródło liczby 18: 5 + 13 lat pracy (E01:L885–L886).
- **Warianty naprawy (PROPOZYCJA):** 1) PROPOZYCJA brzmienia L400: *Data: dwanaście lat temu.*; 2) zmienić wiek Very w E01 P4 (psuje E01).
- **Rekomendacja (PROPOZYCJA):** wariant 1 (zgodny z handoffem H160).
- **Skutki:** E03 (ewentualne odwołania do daty — sprawdzić w osobnym temacie).

#### E02-15 — Wolska: imię i wiek (handoff A2); „Anna” jest już w E02 przy jej stole
- **Waga:** WYSOKA (kanon). **Status audytu:** POTWIERDZONE; notatki **OBALONE** w części („Anna nie pojawia się przy Wolskiej w E02”).
- **Lokalizacja i cytaty:** L42 `Wicepremier Katarzyna Wolska  ~58 lat. Dawna minister finansów. Twarda.`; L111 `T PLUS 2: Sala konferencyjna. Wicepremier KATARZYNA WOLSKA`; L165 `GENERAŁ ANNA SOWA (szefowa sztabu, pięćdziesiąt lat, rzeczowa)`; L945 `GENERAŁ SOWA stoi. Nie siada tym razem.`; L321 `Trzecia kobieta -- ANIA, administracja, nie inżynier -- przy monitorach`. E03 (na podstawie fragmentu): E03:L13 `**ANNA WOLSKA** — wicepremier, 51 lat. Prowadzi odbudowę kraju.`; E03:L915 `Commander Ford. Tu Anna Wolska, pełniąca obowiązki`.
- **Na czym polega sprzeczność:** E02 jest wewnętrznie spójny (Katarzyna, ~58), E03 mówi Anna, 51. Przy „Annie Wolskiej” w sc. 1A i 7A przy jednym stole siedzą dwie Anny, a w PSE pracuje Ania.
- **Warianty naprawy (PROPOZYCJA):** 1) Katarzyna ~58 i poprawka E03 (obsada i kwestia L915); 2) Anna 51 i zmiana imienia gen. Sowy w E02 (L165).
- **Rekomendacja (PROPOZYCJA):** wariant 1 (rekomendacja handoffu H157).
- **Skutki:** E03 obsada i sc. 9 (na podstawie fragmentu); casting/Entity w Flow (wiek).

#### E02-21 — Łączność po wyłączeniu sieci: telefon satelitarny Agi znikąd; adres farmy dla Very tylko z SMS-a T+12
- **Waga:** WYSOKA. **Status audytu:** POTWIERDZONE (telefon Agi); **ZAWĘŻONE** (SMS-y w T+12 nie są w tekście niemożliwe — L1312 dopuszcza sygnał; ocena działania sieci komórkowej po blackoucie NIEPOTWIERDZONE).
- **Lokalizacja i cytaty:** L1278 `Karolina z telefonem w ręce. Ekran ciemny.`; L1280 `Próbuje hotspot, WiFi, wszystko.`; L1312 `jeżeli macie jeszcze sygnał.`; L1398 `AGA (odbiera od razu)`; L1431 `Wysyła.`; L1433 `Pisze drugi SMS -- do Bożeny, mamki dziewczynek:`; L1869 `Telefon satelitarny Agi dzwoni. Bierze go.`; telefony satelitarne w pliku (grep `atelit`): tylko L560, L563, L1359, L1362 (Marta) i L1869 (Aga); L454–L455 SMS T+6 bez adresu (`"Mamo. Żyjesz? Jedź do Polski.` / `Czekam na ciebie."`).
- **Na czym polega sprzeczność:** Aga używa telefonu satelitarnego, którego nigdzie nie dostała (Marta dostaje swój w 4A L563 i 12A L1359). Vera zna adres farmy tylko z SMS-a z T+12 (L1429–L1430), więc fabuła sc. 15 wisi na jednym SMS-ie wysłanym dzień po wyłączeniu sieci; tekst dopuszcza sygnał (L1312), ale tego nie pokazuje.
- **Warianty naprawy (PROPOZYCJA):** 1) w sc. 3 głos z Gabinetu zapowiada telefon: PROPOZYCJA brzmienia po L433: *Prześlemy pani telefon satelitarny. Proszę go nie wyłączać.* — spłaca L1869 i L1398; 2) w 12A jedno zdanie, że sieć komórkowa działa jeszcze na zasilaniu awaryjnym stacji (twierdzenie techniczne NIEPOTWIERDZONE — wymaga konsultacji); 3) Vera dostaje adres inną drogą (np. Aga dzwoni z satelity).
- **Rekomendacja (PROPOZYCJA):** 1 + 3 (jeden rekwizyt rozwiązuje oba problemy).
- **Skutki:** E03 klamra (Aga dzwoni „z telefonem przy uchu -- jedna kreska” E03:L233, na podstawie fragmentu) — zdecydować, czy to komórka czy satelita (E02-22).

#### E02-22 — Wezwanie Agi przyjęte w E02 sc. 17 i drugi raz w E03
- **Waga:** WYSOKA. **Status audytu:** POTWIERDZONE (na podstawie fragmentu E03; numery linii E03 w audycie przesunięte).
- **Lokalizacja i cytaty:** L1872 `AGA (cicho przez telefon)`; L1873 `Tak.`; L1875 `Jutro rano.`; L1883 `Jutro rano jadę do Warszawy.`; L1884 `Chcę żebyś pojechała ze mną.`; L1902 `Zofia. Jutro rano muszę wyjechać.`; L2099 `AGA: Odchodzi. Wie gdzie. Nie mówi. Najkrótsze pożegnanie`. E03 (na podstawie fragmentu): E03:L238 `Doktor Aga Bryk. Choroby zakaźne, Bielański. Jestem gotowa. Dołączam.`; E03:L242 `Tak. Ale mam warunek. Przyślijcie dwoje ludzi z wojska na tę farmę.`
- **Na czym polega sprzeczność:** w E02 Aga zgadza się, ustala wyjazd z Verą, Zofią i Martą; w E03 następnego ranka przedstawia się i „dołącza” jak po raz pierwszy, stawia warunek. Środek transportu: „jadę” (L1883) vs śmigłowiec (E03:L252, na podstawie fragmentu).
- **Warianty naprawy (PROPOZYCJA):** 1) E03 jako drugi telefon (potwierdzenie z warunkiem); 2) w E02 bez zgody — PROPOZYCJA brzmienia L1873–L1875: *Tak. / Rozumiem. / Oddzwonię rano.*; decyzja zapada w E03 pod wpływem napadu; 3) usunąć telefon z sc. 17, prośbę do Very zostawić jako zamiar.
- **Rekomendacja (PROPOZYCJA):** wariant 2 — napad z sc. 19 staje się przyczyną warunku w E03, a sc. 17 zachowuje napięcie (decyzja otwarta).
- **Skutki:** nota L2099–L2100; rozmowy z Zofią (L1902–L1919) i Martą (L1929–L1938) — w wariancie 2 przeformułować na „może będę musiała”.

#### E02-M01 — Prolog: martwa męska załoga w kadrze (zasada „bez mężczyzn”)
- **Waga:** WYSOKA (zasada produkcyjna). **Status audytu:** POTWIERDZONE.
- **Lokalizacja i cytaty:** L71 `wiatru, powoli, nieuchronnie. Na pokładzie nieruchome cienie martwej`; L72 `załogi. Nikt nie stoi przy sterownicy.`; L249 `Marynarze to byli mężczyźni. Gazowce i tankowce`. E01 (na podstawie fragmentu): E01:L1242 `Na pokładzie, pod nadbudówką, leżą postacie. Mężczyźni. Nieruchomi.`
- **Na czym polega sprzeczność:** zasada E02 (handoff §7, rząd 2) zakłada brak mężczyzn w kadrze; prolog świadomie pokazuje ciała z E01.
- **Warianty naprawy (PROPOZYCJA):** 1) formalny wyjątek „zmarli z E01” zapisany w zasadzie; 2) pokład bez ciał — tylko kaski i kombinezony (rym z E01:L1243, na podstawie fragmentu); 3) dystans: „cienie” bez rozpoznawalnej płci, ujęcie z daleka.
- **Rekomendacja (PROPOZYCJA):** 1 + 3 (decyzja D-06).

#### E02-M10 — Klamra: nocne sylwetki z narzędziami czytane jako mężczyźni
- **Waga:** WYSOKA (fałszywy trop w cliffhangerze). **Status audytu:** POTWIERDZONE.
- **Lokalizacja i cytaty:** L2023 `w rytm kroków. Idą. Nie widać twarzy, tylko ciemne kształty. Kobiety,`; L2025 `Łopata. Ostrze sztyletu. Kilof zarzucony na ramię. Trzonek kopaczki.`; L2026 `Dziewięć sylwetek. Idą w stronę farmy. Nie biegną. Idą równo, spokojnie,`; L2017 `Jedyne światło to lampy naftowe. Twarzy nie widać. Całą scenę czytamy`.
- **Na czym polega sprzeczność:** didaskalia mówią „Kobiety”, ale reżyseria każe nie pokazywać twarzy; widz z E01/E02 (świat bez mężczyzn) odczyta uzbrojone sylwetki jako pytanie „przeżyli?”, które E03 rozstrzyga przeciwnie (handoff H118 `nocny najazd 9 uzbrojonych kobiet na farmę;`).
- **Warianty naprawy (PROPOZYCJA):** 1) jedna lampa wyłuskuje kobiecą dłoń lub warkocz — widz wie, że to kobiety (napięcie: przemoc między kobietami, zgodnie z notą L2106–L2108); 2) świadomie zostawić dwuznaczność jako hak, ale wtedy E03 musi to wygrać (decyzja autora).
- **Rekomendacja (PROPOZYCJA):** wariant 1 (zgodny z notą i z tematem „nowy świat”).

#### N-01 — Wątki Agi i Very znikają w środku odcinka (nowe)
- **Waga:** WYSOKA (napięcie). **Status:** nowe, z tekstu.
- **Lokalizacja i cytaty:** ostatni beat Agi przed przerwą: L461 `Aga chowa telefon. Wraca do mikroskopu.`; ostatni beat Very: L473 `Wstaje. Zaczyna się pakować.`; jedyny beat Agi w przerwie: L873 `Aga przy łóżku pacjentki. Nie zatrzymuje się.`; powrót Agi: L1398 `AGA (odbiera od razu)`; powrót Very: L1733 `VERA.`
- **Na czym polega problem:** według etykiet CZAS sc. 3B kończy się w 16:30, a 12A zaczyna w 50:00 — Aga ma przez 33,5 min jeden niemy beat w montażu. Vera znika od 16:30 do 63:00 (46,5 min). W tym czasie odcinek prowadzą PSE, narady i mapy (słowo „mapa” w odmianach: 23 linie). Wątek, który nota L26–L30 nazywa osią ironii dramatycznej, nie ma ciągłości, a ziarno sc. 3 (przypis, telefon z rządu) nie dostaje żadnego kroku.
- **Warianty naprawy (PROPOZYCJA):** 1) jeden beat Agi ok. T+8 (spłata L436 `Zadzwońcie za trzy dni.`): Aga odbiera telefon z rządu i odmawia drugi raz albo prosi o dane z Oslo; 2) krótka wstawka Very w drodze (T+8–T+10), bez dialogu — np. pusta granica, prom bez załogi (spłaca też N-05); 3) w montażu 7 rozbudować beat L873 o Agę, która patrzy na zdjęcie Pawła (L369–L370) — wtedy to osobista stawka w kaskadzie.
- **Rekomendacja (PROPOZYCJA):** 1 + 2 (ok. +1,5 min, kompensowane skrótami w PSE — sekcja d4).
- **Skutki:** metraż; napięcie środka (sekcja e3).

### ŚREDNIE

#### E02-06 — Sc. 3B (T+6) przed sc. 4 (T+5 wieczór)
- **Status:** POTWIERDZONE. Cytaty: L444 `INT. LABORATORIUM WIRUSOLOGII -- T PLUS 6`; L478 `T PLUS 5`. Nazwy miejsca: L358 `INT. SZPITAL BIELAŃSKI, LABORATORIUM -- T PLUS 5` vs L444.
- **PROPOZYCJA:** 3B na „T PLUS 5, NOC” (logiczne następstwo odkrycia z sc. 3, zwłaszcza po E02-01) albo zamiana kolejności 4 → 3B; ujednolicić nazwę laboratorium.

#### E02-07 — Sc. 5B (T+9 wieczór) przed sc. 6 (T+9 dzień); wiszący telefon na końcu sc. 5
- **Status:** POTWIERDZONE. Cytaty: L682 `Wybiera numer. Czeka.`; L686 `INT. CENTRUM PSE -- WIECZÓR`; L770 `Do wieczora. Może do północy jeżeli się uda.`
- **PROPOZYCJA:** kolejność 5 → 6 → 5B (sc. 6 jest odpowiedzią na telefon z L682), w sc. 6 dopisać porę „T PLUS 9, POŁUDNIE”.

#### E02-09 — Sc. 6A „T+10, NOC”: niejasna noc
- **Status:** ZAWĘŻONE (jak w audycie). Cytaty: L806 `T PLUS 10, NOC`; L808 `Marta stoi przy konsoli. Mapa za nią: ponad połowa punktów czerwona.`; L814 `Trzymamy Warszawę, Kraków i Wrocław.`; L821 `Przy obecnym tempie -- dwadzieścia cztery,`; L1087 `Prawie cała czerwona. Jeden zielony punkt -- Warszawa.`
- **Ocena:** czytana jako noc T+9/T+10 (ok. 02:00) jest spójna z mapą (połowa → prawie cała → wyłączenie) i z prognozą: 24–36 h od ok. 02:00 T+10 to T+11 02:00–14:00, a L1149 w T+11 05:43 daje „osiem do dwunastu godzin”. Czytana jako noc po 19:15 T+10 — mapa się cofa, a prognoza 24–36 h przeczy L1149.
- **PROPOZYCJA:** nagłówek „NOC Z T+9 NA T+10, OK. 02:00”.

#### E02-10 — Briefing 4 z nagłówkiem T+10 stoi po wyłączeniu sieci (T+11)
- **Waga:** ŚREDNIA (audyt: WYSOKA — **ZAWĘŻONE**: dla widza kolejność pliku jest spójna, bo obraz gaśnie po 6C; błędna jest etykieta). Cytaty: L1242 `INT. STUDIO TELEWIZYJNE -- BRIEFING 4`; L1243 `T PLUS 10`; L1259 `Obraz gaśnie. Czarny ekran.`; L895 `Wicepremier Wolska -- BRIEFING 3.` (też T+10, L894).
- **PROPOZYCJA:** nagłówek „T PLUS 11, OK. 09:00”; osoba poza kadrem (L1254) przekazuje informację o odcięciu. Spina 6C → 8 → 9. Tabela L2067 do korekty.

#### E02-13 — Opisy w tabeli czasów niezgodne z treścią
- **Status:** POTWIERDZONE w czterech punktach, ZAWĘŻONE w dwóch. Cytaty: L2056 `Scena 4    Salon Marty, Briefing 2, Karolina pyta (T+5)     ok. 2,5 min` vs L477 `INT. CENTRUM PSE -- POKÓJ SOCJALNY -- WIECZÓR` (POTWIERDZONE; Karolina dzwoni i pisze L514, nie pyta w scenie); etykiety „BRIEFING 1/2” nie istnieją w pliku (grep `BRIEFING`: tylko L895, L1242); L2059 `Scena 5    PSE Dzień 9 -- pierwsza awaria GPZ               ok. 2,5 min` vs L170–L172 (ZAWĘŻONE: sc. 5 pokazuje pierwszą zmianę na czerwono „na żywo”, opis jest nieprecyzyjny, nie fałszywy); L2060 `Scena 5B   Marta dzwoni do Karoliny 1 -- wanna (T+9)        ok. 2,0 min` vs L145–L147 (ZAWĘŻONE: w sc. 1 nie wiadomo, kto dzwonił); L2074 (E02-02); kolejność 15/16 i brak 3B (E02-11).
- **PROPOZYCJA:** przebudować tabelę po nowej numeracji.

#### E02-16 — „Ania” w PSE zamiast osób z E01 (Agnieszka, Ela)
- **Status:** POTWIERDZONE (na podstawie fragmentu E01). Cytaty: L321 `Trzecia kobieta -- ANIA, administracja, nie inżynier -- przy monitorach`; L1145 `Jestem tu z dwiema kobietami. Zarządzamy systemem`; E01:L1037 `Agnieszka -- bierz R-dziewiętnaście. Ela -- R-dwadzieścia dwa.`; E01:L1171 `Centrum PSE. Marta i dwie kobiety przy konsolach.`
- **PROPOZYCJA:** „Ania” → „Ela” (usuwa też kolizję z Anną Sową i z „Agnieszką” L1747); przy tym rozstrzygnąć „nie inżynier” (decyzja D-13).

#### E02-17 — „Pani Premier” vs „Wicepremier”
- **Status:** ZAWĘŻONE (jak w audycie). Grep `Pani Premier`: L811, L1128, L1136, L1144, L1356, L1366, L1376 (7 razy). Grep `-i wicepremier`: L42, L111, L115, L120, L421, L895, L1319. Cytat: L117 `Przejmuję pełnię władzy wykonawczej.`
- **Ocena:** „Pani Premier” jest fabularnie uzasadnione po L117; niespójne są didaskalia i komunikaty po T+2 (L421 T+5, L895 T+10, L1319 T+11).
- **PROPOZYCJA:** od T+2 w didaskaliach „p.o. premiera”; w obsadzie: *Wicepremier, od T+2 p.o. premiera* (decyzja D-12).

#### E02-18 — Wolska ogłasza stan wyjątkowy, który premier ogłosił w E01
- **Status:** POTWIERDZONE (na podstawie fragmentu E01). Cytaty: L116 `Ogłaszam stan wyjątkowy na terenie całego kraju.`; E01:L1148 `Ogłaszam stan wyjątkowy na terenie całego kraju.`
- **PROPOZYCJA:** świadome echo zaznaczone w didaskaliach albo brzmienie L116: *Stan wyjątkowy pozostaje w mocy.*

#### E02-19 — „Zofia Kowalska” (handoff D16)
- **Status:** POTWIERDZONE (trzy miejsca); wniosek notatek **ZAWĘŻONY**. Cytaty: L1416 `Farma pod Łowiczem. Zofia Kowalska.`; L1429 `"Mamo. Farma pod Łowiczem. Zofia Kowalska.`; L1435 `z nimi na farmę pod Łowiczem do Zofii Kowalskiej.`; L46 `Zofia                      ~55 lat. Ciotka Marty. Farmerka. Konkretna, niesentymentalna.`; L1552 `Nie wiedziałam że masz ciotkę na farmie.`
- **Ocena:** nazwisko panieńskie Marty w E02 nie pada (grep `z d.`: tylko L37, Aga). „Kowalska” nie jest więc logicznie wykluczona (zbieg nazwisk), ale czyta się jak rodzina męża, co przeczy L46 i L1552. Notatki twierdzą, że musi to być nazwisko panieńskie Marty — tekst tego nie przesądza.
- **PROPOZYCJA:** inne nazwisko (różne od Kowalska / Bryk / Strand / Wolska) albo adres opisowy bez nazwiska (decyzja D-09).

#### E02-20 (= E02-M11) — „MINISTER” vs „MINISTRA”, „ministrowie”
- **Status:** POTWIERDZONE. Cytaty: L161 `Okrągły stół. Osiem kobiet -- ministrowie, szefowe służb,`; L177 `MINISTER INFRASTRUKTURY`; L188 `MINISTRA ENERGETYKI zabiera głos.`; L272 `MINISTER KOMUNIKACJI`; L1001 `MINISTER INFRASTRUKTURY`.
- **PROPOZYCJA:** konsekwentnie „MINISTRA …”, L161 *Osiem kobiet -- ministry, szefowe służb,*; w promptach EN „female minister”.

#### E02-23 — Pozycje postaci między E02 sc. 18/19 a E03 klamrą
- **Status:** POTWIERDZONE (na podstawie fragmentu E03; numery linii E03 w audycie przesunięte o 4–9). Cytaty: L1961 `Inne kobiety odeszły. Zostały Marta i Karolina.`; L1998 `Siedzą razem przy prawie wygasłym ogniu.`; L2030 `ZOFIA, sama, z lampą w ręce, zamyka na noc szopę ze zwierzętami. Zasuwa`; E03:L159 `Na schodach tupot. Schodzą KAROLINA (19) i HELENA (~50), zaspane, wystraszone.`
- **PROPOZYCJA:** w sc. 18 jedno zdanie zejścia do domu (*Wchodzą. Karolina idzie na górę.*), sc. 19 „godzinę później”.

#### E02-24 — Bożena: wątek urwany; „mamka”
- **Status:** POTWIERDZONE. Cytaty: L1433 `Pisze drugi SMS -- do Bożeny, mamki dziewczynek:`; L1787 `Dziewczynki są w środku. Śpią już.`; L1912 `Zostają tu. Marta jest. Karolina jest.`; E01:L1082 `Tak. U Bożeny. Śpią już pewnie.` (na podstawie fragmentu).
- **PROPOZYCJA:** w sc. 15 jedno zdanie Agi: *Bożena przywiozła je wczoraj. Wróciła do swoich.*; „mamki” → „niani”.

#### E02-25 — Mapa sieci: kolory bez legendy, liczby niejasne
- **Status:** ZAWĘŻONE. Cytaty: L318 `Czerwone: trzy. Nowych względem poprzedniego dnia.`; L341 `Wczoraj były dwa. Pojutrze będzie pięć.`; L745 `GPZ Grodzisk -- znowu żółty?`; L795 `Blok B na mapie -- żółty jeszcze.`; L1087 `Prawie cała czerwona. Jeden zielony punkt -- Warszawa.`; E01:L1202 `Kilkanaście czerwonych punktów -- każdy z sygnałem alarmowym.` (na podstawie fragmentu).
- **Ocena:** L318 jest dwuznaczne („trzy, [są] nowe” vs „wczoraj dwa”), nie jednoznacznie sprzeczne. Cztery kolory bez definicji; punkty raz są stacjami, raz blokami, raz miastami; E01 T0 ma kilkanaście czerwonych, E02 T+3 — trzy.
- **PROPOZYCJA:** legenda w didaskaliach sc. 2 (zielony norma / żółty ostrzeżenie / pomarańczowy tryb awaryjny / czerwony wyłączony), usunąć zdanie „Nowych względem poprzedniego dnia.”; jedna grafika mapy w post dla E01–E03.

#### E02-26 — Prognozy „ile mamy czasu” nie układają się w ciąg (zegar odcinka)
- **Status:** POTWIERDZONE. Cytaty: L345 `Dziewięć.`; L351 `Tyle mamy. Zanim sieć zacznie sama siebie odcinać.`; L542 `Mamy jeszcze osiem, może dziesięć dni`; L821 `Przy obecnym tempie -- dwadzieścia cztery,`; L1149 `Sieć padnie za osiem do dwunastu godzin,`.
- **Ocena:** T+3 + 9 = T+12; T+6 + 8–10 = T+14–T+16 (prognoza późniejsza niż poprzednia); sieć gaśnie w T+11. Zegar, który ma budować napięcie, w T+6 rozluźnia się (sekcja e3). „Dziewięć” bez jednostki.
- **PROPOZYCJA brzmienia:** L345 *Dziewięć dni.*; L542 *Mamy jeszcze pięć, może sześć dni*.

#### E02-29 — Terminologia sieci: GPZ, „bocznik”, „Rogów” vs „Rogowiec” z E01
- **Status:** ZAWĘŻONE: część tekstowa POTWIERDZONE, ocena branżowa NIEPOTWIERDZONE. Cytaty: L170 `Energetyka -- osiemdziesiąt procent GPZ-ów`; L660 `Jeden punkt -- GPZ Rogów, cztery kilometry od bocznika`; L665 `Trzy minuty -- zmienia się następny. GPZ Krzyżanów.`; E01:L138 `Dobry. Rogowiec znowu dał znać o sobie.` (na podstawie fragmentu).
- **Ocena:** twierdzenia audytu, że PSE nie prowadzi GPZ, że „bocznik” to element pomiarowy oraz że Rogowiec i Krzyżanów to realne stacje — NIEPOTWIERDZONE. Z tekstu wynika tylko różnica nazw Rogów/Rogowiec (możliwe zgubione ziarno z E01).
- **PROPOZYCJA:** „Stacja Rogowiec” w L660 (spłata E01), resztę terminologii poddać konsultacji (D-16).

#### E02-30 — Fizyka sieci: kierunek awarii i uzasadnienia decyzji
- **Status:** ZAWĘŻONE: cytaty POTWIERDZONE, ocena fizyki NIEPOTWIERDZONE. Cytaty: L233 `Drastyczny spadek napięcia. Do końca dnia`; L812 `Trzy rafinerie zamknięte. Sieć przesyłowa`; L813 `na dwudziestu dwóch procentach przepustowości.`; L775 `Możecie przyjąć na sieć przy kontrolowanym`; L1153 `albo poczekać aż padnie chaotycznie i uszkodzi`.
- **Ocena:** teza audytu, że przy spadku zapotrzebowania typowym problemem jest nadmiar mocy, a nie spadek napięcia, oraz że lepszym argumentem jest utrata możliwości ponownego uruchomienia — NIEPOTWIERDZONE. Wewnątrz tekstu kwestie są spójne ze sobą.
- **PROPOZYCJA:** konsultacja z dyspozytorem KSE i korekta 4–5 kwestii albo świadoma licencja dramatyczna (D-16).

#### E02-31 — Paliwo, gaz, LNG — liczby i logika
- **Status:** ZAWĘŻONE: sprzeczność wewnętrzna L248 POTWIERDZONE; dane o zapasach (90 dni, magazyny gazu, Baltic Pipe) NIEPOTWIERDZONE. Cytaty: L191 `Rafinerie mają paliwo na tydzień -- może dziesięć dni.`; L215 `Terminal LNG w Świnoujściu: marynarze byli mężczyznami.`; L248 `Gdańsk i Gdynia -- personel zszedł na ląd.`; L249 `Marynarze to byli mężczyźni. Gazowce i tankowce`; L961 `w krajowych magazynach -- na dwa, może trzy tygodnie.`
- **Ocena tekstowa:** „zszedł na ląd” (L248) przeczy zdaniu następnemu (załogi to mężczyźni, czyli nie żyją). L215 łączy terminal (obiekt lądowy, w prologu obsadzony przez kobiety L64) z marynarzami — czyta się jak skrót myślowy.
- **PROPOZYCJA:** akcent z ilości na obsługę: *Paliwo jest. Nie ma komu go rozwieźć.*; L248 *Gdańsk i Gdynia -- załóg nie ma.*

#### E02-32 — „Trzy nazwiska w całej Polsce”
- **Status:** ZAWĘŻONE: gramatyka L834 POTWIERDZONE; ocena liczby inżynierek NIEPOTWIERDZONE. Cytaty: L834 `Szukamy. Inżynier sieci bez mężczyzn...`; L838 `Trzy nazwiska w całej Polsce -- wszystkie zajęte.`; L194 `jedenaście osób na trzy instalacje.`
- **PROPOZYCJA brzmienia:** L834 *Szukamy. Inżynierki sieci...*; L838 *Trzy w zasięgu dojazdu -- wszystkie zajęte.*

#### E02-33 — Biogazownia: podłączenie do spalonego transformatora, „gazownia”
- **Status:** POTWIERDZONE (sprzeczność wewnętrzna); kwestia pracy wyspowej NIEPOTWIERDZONE. Cytaty: L1622 `Tu. Transformator strzelił przy wejściu.`; L1631 `Ale sterowniki się zresetowały przy uszkodzeniu głównego transformatora.`; L1708 `To musimy jeszcze zrobić jedno połączenie do transformatora w gazowni.`; L1623 `Mamy zapasowy agregat -- pali się od dziesięciu dni.`
- **Ocena:** transformator jest uszkodzony, a Marta chce się do niego podłączyć; „gazowni” na farmie nie ma. Plus: L1623 (od T+3) zgadza się z L233–L234 (wsie odcięte w T+3).
- **PROPOZYCJA brzmienia L1708:** *Jutro przepniemy go na rozdzielnicę domu, z pominięciem spalonego transformatora.*

#### E02-34 — Nota „żadnych eksplozji” vs sc. 7
- **Status:** POTWIERDZONE. Cytaty: L18 `Poza tym jednym uderzeniem -- żadnych eksplozji, żadnych katastrof`; L909 `Niski wybuch, nie kataklizm. Słup dymu.`; L918 `Potem daleki grzmot. Nie burza.`; L891 `zaczyna się palić -- linia ognia pełznie w głąb, nikt jej nie`.
- **PROPOZYCJA:** nota: *żadnych eksplozji z bliska; reszta z daleka, w dźwięku*.

#### E02-35 — Nota o wodzie dotyczy nieistniejącej sceny
- **Status:** POTWIERDZONE. Cytaty: L2094 `VERA NA FARMIE: Wchodzi przez bramę i zaraz zaczyna robić`; L2097 `Woda będzie ciekła po raz pierwszy w następnej scenie.`; L1815 `kilka innych. Vera na skraju -- trochę poza kręgiem.`
- **PROPOZYCJA:** usunąć zdanie o wodzie albo dodać beat Very przy studni/pompie w sc. 15 lub 17.

#### E02-37 — Zapieczętowany list w teczce (handoff B7)
- **Status:** POTWIERDZONE. Cytat: L1972 `Zapieczętowana koperta -- list, którego Marta jeszcze nie otworzyła.`
- **PROPOZYCJA:** list jako „otworzyć, gdyby…” (spłata w E03 — osobny temat) albo usunięcie zdania (D-11). Zob. też PROPOZYCJA w e8 (sc. 18).

#### E02-38 — Śmierć Dąbrowskiego bez beatu (handoff C11)
- **Status:** POTWIERDZONE. Grep `Dąbrowsk`: tylko L399. Cytat E01 (na podstawie fragmentu): E01:L47 `i umiera poza kadrem w Zero Day.`
- **PROPOZYCJA:** łączyć z E02-01: jedna notatka Agi w sc. 3, np. *Tata. Czternaście dni temu.* (liczba dni zależy od osi T — do policzenia przy poprawce).

#### E02-52 — Obsada niepełna
- **Status:** POTWIERDZONE. Obsada L33–L49 zawiera 9 pozycji (Marta, Karolina, Aga, Wolska, Vera, Zofia, Helena, Basia, Kobieta z elektrowni). Brak m.in. L165 `GENERAŁ ANNA SOWA (szefowa sztabu, pięćdziesiąt lat, rzeczowa)`, L320 `BEATA przy sąsiednich konsolach -- robi trzy razy więcej niż zwykle.`, L372 `JOANNA wchodzi z wynikami. Zatrzymuje się przy drzwiach.`, L1347 `Przy nim: SZEREGOWA NOWAK (25 lat, mundur, spokojna).`, Prezenterki, Dyżurnej, Policjantki, ministrów.
- **PROPOZYCJA:** uzupełnić (baza Entity w Flow i kontroli zasady „bez mężczyzn”).

#### N-02 — Zasiane zapowiedzi rządu bez spłaty w E02 (nowe)
- **Status:** nowe. Cytaty: L436 `Zadzwońcie za trzy dni.` (T+5 → T+8); L574 `Proszę. I jeszcze jedno -- za jakiś czas`; L575 `będę miała prośbę służbową. Konkretną.`
- **Problem:** telefon do Agi w T+8 nie pada (następny kontakt: L1869 w T+13). „Prośba służbowa” z 4A nie zostaje nazwana; propozycja z 12A (L1370 `Mamy dla pani miejsce w Centrum Zarządzania Kryzysowego.`) nie jest oznaczona jako ta prośba.
- **PROPOZYCJA:** spłata L436 w nowym beacie Agi (N-01, wariant 1); w 12A Wolska: *To jest ta prośba, o której mówiłam.*

#### N-03 — Ten sam chwyt „obraz gaśnie w pół zdania” trzy razy w 14 minutach (nowe)
- **Status:** nowe. Cytaty: L902 `Cięcie -- nie na efekt dramatyczny.` (Marta wyłącza TV w pół zdania Wolskiej, L900 `Skoordynowane działania pozwolą utrzymać...`); L1252 `co nas czeka w ciągu najbliższych...`; L1259 `Obraz gaśnie. Czarny ekran.`; L1333 `Ekran gaśnie w połowie słowa.`
- **Problem:** trzecie użycie (sc. 10) jest przewidywalne; spada siła sc. 10 jako „ostatniej stacji”.
- **PROPOZYCJA:** w sc. 7 zostawić świadome wyłączenie (gest Marty), w sc. 8 utrzymać czarny ekran, a sc. 10 zakończyć inaczej — prezenterka kończy komunikat, wstaje, sama wyłącza generator (cisza z wyboru, nie z awarii).

#### N-04 — Marta zostaje w PSE ok. doby po wyłączeniu, gdy córka jest sama bez łączności (nowe)
- **Status:** nowe. Cytaty: L1238 `Wychodzą. Marta zostaje sama.` (T+11, rano); L1278 `Karolina z telefonem w ręce. Ekran ciemny.` (T+11, popołudnie); L1343 `T PLUS 12, GODZINA 06:20`; L1345 `Marta wychodzi z PSE z plecakiem i torbą.`; L1080 `Ładuj zawsze jak jest prąd. Mogę być przez jakiś czas`.
- **Problem:** po zgaszeniu sieci Marta nie ma czego pilnować (L1224 `Marta stoi nieruchomo przed wygasłą mapą.`), a mimo to przez ok. 21 godzin nie jedzie do córki; tekst nie podaje powodu. Spójne z charakterem (praca przed rodziną, sc. 4), ale niewyjaśnione.
- **PROPOZYCJA:** 1) jedno zdanie w 12A: Marta czekała na potwierdzenia z węzłów krytycznych (spłata L1165–L1166); 2) przesunąć 12A na T+11 przed południem i postawić sc. 12 bezpośrednio po sc. 9 (Marta wchodzi do pokoju, w którym Karolina siedzi na podłodze) — mocna spłata sc. 9; wtedy farma T+11/T+12 (przeliczyć oś).

#### N-05 — Podróż Very T+6 → T+13 bez śladu (nowe; rozwinięcie części E02-49)
- **Status:** nowe. Cytaty: L455 `Czekam na ciebie."`; L473 `Wstaje. Zaczyna się pakować.` (T+6); L1747 `Matka Agnieszki. Ona mi powiedziała żeby tu przyjechać.` (T+13); L1732 `Plecak na plecach -- mały, stary. Twarz zmęczona.`
- **Problem:** Vera wyjeżdża w T+6 na wezwanie „Czekam na ciebie” (do Warszawy), ale przez 6 dni nie dociera do Agi; skoro jedzie do Polski, dlaczego nie do Bielańskiego? W sc. 1A transport morski nie działa (L250 `z ropą nie przypłyną -- nie ma komu sterować,`), więc droga z Oslo jest sama w sobie dramatem, którego nie ma.
- **PROPOZYCJA:** jedna kwestia Very w sc. 15: *Przez Szwecję. Samochodem, potem pieszo.* albo wstawka z N-01 wariant 2.

#### E02-M02, M03, M06, M08, M09 — zasada „bez mężczyzn” (ŚREDNIE)
- **Status:** POTWIERDZONE (wszystkie). Cytaty: M02 L66 `kilka sylwetek przy konsolach. Cały terminal trzyma się na tych` i L83 `Trzy kobiety na molo giną. Sylwetki w budynku operacyjnym -- giną.`; M03 L369 `przyklejone do krawędzi monitora: Paweł i dwie małe dziewczynki,`; M06 L1522 `Inni wynoszą rzeczy. Bez pośpiechu, bez paniki.`; M08 L1949 `Gdzieś z tyłu ktoś zaczyna śpiewać -- niski głos, stara pieśń,`; M09 L1969 `Widz widzi co w środku: zdjęcia -- Piotrek przy rakiecie,`.
- **PROPOZYCJA:** M02 „kilka kobiecych sylwetek”; M03 i M09 formalny wyjątek „zdjęcia zmarłych i nieobecnych” (Piotr na zdjęciu jest potrzebny dla E03 — na podstawie fragmentu audytu); M06 *Inne wynoszą rzeczy.*; M08 *niski kobiecy głos*. Zasada w dwóch zdaniach (D-06): *Żaden żywy mężczyzna w kadrze ani w dźwięku. Wyjątki: zmarli z E01 w prologu oraz Paweł i Piotr na zdjęciach-rekwizytach.*

### NISKIE

| ID | Lokalizacja i cytat | Problem | Status | PROPOZYCJA |
|---|---|---|---|---|
| E02-27 | L325 `Marta -- ten punkt w Bydgoszczy. Pyta o pozwolenie`; L588 `Nic. Wracamy do Bydgoszczy.`; L799 `Napisz do Bydgoszczy, Łodzi i Krakowa.` | PSE jest w Warszawie (E01:L127, na podstawie fragmentu; L647 Marta jedzie do PSE przez Mokotów). Bydgoszcz to obiekt w sieci; tylko L588 jest dwuznaczne. Istnienie realnej dyspozycji w Bydgoszczy — NIEPOTWIERDZONE | POTWIERDZONE (zawężenie audytu) | *Nic. Wracamy do sprawy Bydgoszczy.* |
| E02-28 | L522 `INT. CENTRUM PSE + KANCELARIA (INTERCITY) -- T PLUS 6`; L758 `Intercity: Marta w PSE, kobieta gdzieś w elektrowni.` | Najpewniej autokorekta „INTERCUT” (interpretacja) | POTWIERDZONE | „INTERCUT” |
| E02-36 | L2085 `WOLSKA: Widzimy ją cztery razy -- coraz mniej otoczona ludźmi,` | Cztery są wystąpienia publiczne (sc. 1, 4, 7, 8); na ekranie Wolska jest 6 razy (1, 1A, 4, 7, 7A, 8), głosem 4 razy (4A, 6A, 6C, 12A). Otoczenie: L132 dwie kobiety, sc. 4 brak opisu, L896 mniej personelu, L1246 jedna kobieta | ZAWĘŻONE | *Widzimy cztery jej wystąpienia…*; w sc. 4 dopisać otoczenie |
| E02-39 | L647 `Marta przejeżdża samochodem -- jedzie do PSE.`; L1147 `Przez jedenaście dni pracowałyśmy bez przerwy.`; L1449 `Jedenaście dni.` | „Bez przerwy”, a w T+8 jedzie do PSE z miasta; „Jedenaście dni” w T+12 06:20 — liczba dni pracy T+1–T+11, do przyjęcia | ZAWĘŻONE | Usunąć „jedzie do PSE” (jedzie po coś dla PSE) albo przyjąć hiperbolę |
| E02-40 | L1496 `Przez te dni nie odebrałaś.`; L506 `Nie odbiera.`; L694 `KAROLINA (odbiera natychmiast)` | Prawdziwe tylko częściowo: Marta nie odbierała, ale sama dzwoniła (5B, 6B) | ZAWĘŻONE | *Przez te dni nie odbierałaś, kiedy ja dzwoniłam.* |
| E02-41 | L1502 `Czy tata...`; L1847 `Mój mąż był...`; L1985 `On żyje?` | Ten sam beat trzy razy w dwa dni; 12 i 18 prawie identyczne (spadek napięcia, e3) | POTWIERDZONE | Zostawić 17 i 18; w 18 zmienić pytanie (e8) |
| E02-42 | L1062 `Słuchaj. Idź teraz zrobić zakupy.`; L1065 `I gotówka -- nie karta.` | W T+10, po szabrowaniu T+7–T+8 (5A), „zakupy” mało realne | POTWIERDZONE | Świadomie: Karolina wraca z niczym (beat) albo *zejdź do piwnicy* |
| E02-43 | L1278 `Karolina z telefonem w ręce. Ekran ciemny.`; L1280 `Próbuje hotspot, WiFi, wszystko.` | Przy ciemnym ekranie nie da się sprawdzić hotspotu | POTWIERDZONE | *Ekran: brak sieci. Bateria 3%.* |
| E02-44 | L921 `Latarnie uliczne nie gasną rano -- nie paliły się w nocy.`; L928 `Ze studzienki kanalizacyjnej wydobywa się para.` | Warszawa miała prąd w nocy (L1087); czy para wynika z postoju oczyszczalni — NIEPOTWIERDZONE | ZAWĘŻONE | *Latarnie wyłączone dla oszczędności.* |
| E02-45 | L1588 `Marta. Dobrze, że dojechałyście.`; L1739 `Nie ma jej tu jeszcze.`; L1752 `Wiedziałam że przyjedziesz.` | Zofia „wie” bez łączności — wyjaśnialne (Aga dotarła wcześniej). L1739 to narracja z perspektywy Very, ale fałszywa (Aga jest w domu L1770) | ZAWĘŻONE | L1739 *Nie widzi jej.* |
| E02-46 | L467 `SMS. Numer polski.` | E01:L824 Vera ma kontakt „Aga” ze zdjęciem (na podstawie fragmentu); ukrywanie nadawcy niczego nie daje, bo widz widział L454 | POTWIERDZONE | *SMS. Ekran: Aga.* |
| E02-47 | L2003 `Cięcie na czarny ekran.`; L2005 `E W A`; L2046 `KONIEC ODCINKA 2.` | Plansza tytułowa dwa razy (L93, L2005); sc. 19 po planszy jako „tag” | POTWIERDZONE | Decyzja D-14 (sekcja e7) |
| E02-48 | brak w E02 (grep `strzelb|dubelt|broń`: pusty); E03:L180 `nie patrząc, sięga na półkę nad wejściem -- tam, gdzie wuj trzymał starą` (na podstawie fragmentu) | Broń i wuj z E03 nie są zasiane | POTWIERDZONE | W sc. 17 jedno zdanie Zofii o mężu i strzelbie (napięcie przed klamrą) |
| E02-49 | L986 `Kontenerowiec z Gdańska wszedł na mieliznę`; L997 `Naftoport Gdańsk -- za dwa dni potrzebuje`; L2092 `padnie i ona. Widz będzie się zastanawiał co się z nią stało.` | Drobne wątki bez spłaty; podróż Very — N-05 | POTWIERDZONE | Świadomie zostawić (świat się rozpada) |
| E02-50 | L1302 `Studio. Kobieta przed kamerą. Ta sama bluzka`; L1303 `co dwa dni temu. Włosy związane na szybko.` | Prezenterka nie pojawia się wcześniej w E02; E01:L1144 „ta sama bluzka drugi dzień z rzędu” (na podstawie fragmentu) | POTWIERDZONE | *Ta sama bluzka co w dniu zero.* |
| E02-51 | L910 `Alarm automatyczny wyje sam dla siebie.`; L911 `Nikt nie jedzie.`; L995 `Pożar opanowany. Dwie ranne. Instalacja` | „Nikt nie jedzie” vs „opanowany, dwie ranne” tego samego wieczoru | POTWIERDZONE | *Wygasł sam. Dwie ranne z obsady.* |
| E02-53 | L1370 `Mamy dla pani miejsce w Centrum Zarządzania Kryzysowego.` | E03 „Rządowe Centrum Kryzysowe” (E03:L234, na podstawie fragmentu); nazwa realnej instytucji — NIEPOTWIERDZONE | POTWIERDZONE | Jedna nazwa w E02 i E03 |
| E02-54 | np. L672 `Beata -- zacznij procedure izolowania sekcji P3 do P7.`; L782 `Będę przy konsoli. Dzwoncie co godzinę.`; L1251 `Chcialabym powiedzieć kilka słów o tym` | Błędy językowe (lista audytu §7, sprawdzona punktowo: L672, L760, L782, L792, L1251, L1475, L1536 — wszystkie obecne) | POTWIERDZONE | Korekta językowa na końcu (f1) |
| E02-55 | L375 `Doktor Bryk. Hania dzwoniła. Prosi żebyś zadzwoniła`; L825 `Czego potrzebujesz?`; L847 `Dziękuję, pani Kowalska.` | Przeskok pani/ty w jednej kwestii lub scenie | POTWIERDZONE | Ujednolicić świadomie |
| E02-56 | L391 `które są identyczne w obu. Zakreśliła kolorem.`; L392 `Pod spodem jej notatka: "Nie naturalne. Zbyt czyste.` | E02 rozstrzyga „dwie sekwencje” jako dowód inżynierii; wątku odporności nie ma (grep `chłop`: pusty) | POTWIERDZONE | Decyzja autora (handoff H214) |
| E02-M04 | L620 `GŁOS W RADIU` | Płeć głosu nieokreślona | POTWIERDZONE | *GŁOS W RADIU (kobieta)* |
| E02-M05 | L1254 `Ktoś poza kadrem mówi coś cicho.` | Głos nieokreślony | POTWIERDZONE | *Asystentka poza kadrem* |
| E02-M07 | L1535 `Za oknem: porzucone auto na poboczu. Ktoś dostosował` | Kierowca nieokreślony | POTWIERDZONE | Bez kierowcy w kadrze |
| E02-M12 | L135 `Ktokolwiek był na kasie -- zostawił ją. Kobieta za lada` | Tylko tekst; uwaga do promptu | POTWIERDZONE | Bez zmian; uwaga w prompcie |
| E02-M13 | L113 `że już niewidoczny. Mówi do kamer.`; L896 `Stoi przy podium. Za nią -- mniej personelu niż poprzednio.` | Ekipy TV nieopisane | POTWIERDZONE | „all-female crew” w promptach |
| E02-M14 | L364 `jednej z tablic: "Tomasz Kamiński, W-wa, 14.03 -- pacjent zero".` | Tylko napis; ryzyko zdjęcia pacjenta | POTWIERDZONE | Bez zdjęcia na tablicy |
| N-06 | L1847 `Mój mąż był...`; L1852 `Daleko.`; L1971 `razem, młodsi. Dokumenty misji -- wydruki, tabele, daty.` | Wątek Piotra i Ares IV w E02 tylko w rekwizytach (grep `Ares|Mars`: pusty). Dla widza E02 „Daleko” to tajemnica; pytanie, czy celowa | nowe | Decyzja D-17; ewentualnie jedno ujęcie zdjęcia z naszywką misji w sc. 18 |
| N-07 | L618 `Wisła -- sytuacja na Wolskiej. Prosimy o wsparcie.` | Ulica Wolska koliduje z nazwiskiem postaci (z notatek) | nowe (z notatek) | *sytuacja na Górczewskiej* lub inna ulica |
| N-08 | L1563 `Nie wiem. Napisałam do niej.` | W 12A Marta dzwoniła do Agi (L1396–L1423) (z notatek) | nowe (z notatek) | *Nie wiem. Dzwoniłam do niej.* |
| N-09 | L1617 `Rano. Zofia prowadzi Martę do szopy za stodołą.`; L2030 `ZOFIA, sama, z lampą w ręce, zamyka na noc szopę ze zwierzętami. Zasuwa` | Dwa budynki „szopa” (z notatek) | nowe (z notatek) | „obora” w L2030 |

---

## (c) WERYFIKACJA USTALEŃ WEJŚCIOWYCH

Statusy: **POTWIERDZONE** (zgodne z tekstem), **OBALONE** (tekst przeczy), **ZAWĘŻONE** (prawdziwe w części lub wymaga doprecyzowania), **NIEZBADANE** (nie sprawdzono — tylko dla punktów nie-KRYTYCZNYCH i nie-WYSOKICH), **NIE DOTYCZY E02** (ustalenie o innym odcinku; dowód: grep pusty lub lokalizacja poza E02).

### c1. Audyt `E02_audyt.md` (E02-01 … E02-56, E02-M01 … M14)

| ID audytu | Waga audytu | Status | Dowód (cytat, linia E02) | Uwagi |
|---|---|---|---|---|
| E02-01 | KRYT | POTWIERDZONE | L410 `"V. Strand. Kim jest?"`; L399 `Autor: prof. Marek Dąbrowski, Uniwersytet Warszawski.` | Ojciec — na podstawie fragmentu E01:L46 |
| E02-02 | KRYT | POTWIERDZONE | L45 `Widz jeszcze tego nie wie.`; L1747 `Matka Agnieszki. Ona mi powiedziała żeby tu przyjechać.` | — |
| E02-03 | KRYT | POTWIERDZONE (a, b) / ZAWĘŻONE (c) | L124 `Zabezpieczcie źródła wody na kilka dni.`; L302 `Za godzinę jestem na antenie.`; L154 `Napis biały na czarnym: T PLUS 8 DNI` | (c) T+6 vs T+5 to różne dni |
| E02-04 | WYS | POTWIERDZONE | L54 `T PLUS 9`; L56 `Reżysersko: ciągłość z ostatnim kadrem odcinka pierwszego. Statek` | E01 l. przesunięte o 1; „kilka godzin” NIEPOTWIERDZONE |
| E02-05 | WYS | POTWIERDZONE / ZAWĘŻONE (torby) | L1477 `Marta przy szafie. Otwiera. Żółta teczka -- bierze.` | E01:L158 na podstawie fragmentu |
| E02-06 | ŚR | POTWIERDZONE | L444 `INT. LABORATORIUM WIRUSOLOGII -- T PLUS 6`; L478 `T PLUS 5` | — |
| E02-07 | ŚR | POTWIERDZONE | L686 `INT. CENTRUM PSE -- WIECZÓR`; L770 `Do wieczora. Może do północy jeżeli się uda.` | — |
| E02-08 | WYS | POTWIERDZONE (a, c) / ZAWĘŻONE (b, d) | L933 `Marta zostaje sama przy wygasłej konsoli.`; L1238 `Wychodzą. Marta zostaje sama.` | (b) zależy od odczytu L1176 |
| E02-09 | ŚR | ZAWĘŻONE | L806 `T PLUS 10, NOC`; L814 `Trzymamy Warszawę, Kraków i Wrocław.` | Spójne przy odczycie T+9/T+10 |
| E02-10 | WYS | ZAWĘŻONE (waga → ŚREDNIA) | L1243 `T PLUS 10`; L1259 `Obraz gaśnie. Czarny ekran.` | Dla widza kolejność spójna |
| E02-11 | WYS | POTWIERDZONE | L1613 `SCENA 16  [CZAS: ok. 3 min]`; L1725 `SCENA 15  [CZAS: ok. 2 min]` | Brak SCENA 11 (grep pusty) |
| E02-12 | WYS | POTWIERDZONE | L3 `Format: ok. 65 minut`; L2080 `RAZEM:                                                     ok. 69,0 min` | 70,5 i 73,5 przeliczone (d1) |
| E02-13 | ŚR | POTWIERDZONE (4) / ZAWĘŻONE (2) | L2056 `Scena 4    Salon Marty, Briefing 2, Karolina pyta (T+5)     ok. 2,5 min` | Szczegóły w (b) |
| E02-14 | WYS | POTWIERDZONE | L400 `Data: osiemnaście lat temu.` | E01:L867, L869 na podstawie fragmentu |
| E02-15 | WYS | POTWIERDZONE | L42 `Wicepremier Katarzyna Wolska  ~58 lat. Dawna minister finansów. Twarda.`; L165 `GENERAŁ ANNA SOWA (szefowa sztabu, pięćdziesiąt lat, rzeczowa)` | E03:L13 na podstawie fragmentu |
| E02-16 | ŚR | POTWIERDZONE | L321 `Trzecia kobieta -- ANIA, administracja, nie inżynier -- przy monitorach` | E01:L1037 na podstawie fragmentu |
| E02-17 | ŚR | ZAWĘŻONE | L1376 `Pani Premier. Mam córkę.`; L1319 `Odczytuję komunikat wicepremier Wolskiej z godziny` | 7 × „Pani Premier” (zgodnie z audytem) |
| E02-18 | ŚR | POTWIERDZONE | L116 `Ogłaszam stan wyjątkowy na terenie całego kraju.` | E01:L1148 (audyt: 1146–1147, przesunięcie) |
| E02-19 | ŚR | POTWIERDZONE | L1416 `Farma pod Łowiczem. Zofia Kowalska.` | Wniosek o nazwisku panieńskim — tekst nie przesądza |
| E02-20 | ŚR | POTWIERDZONE | L161 `Okrągły stół. Osiem kobiet -- ministrowie, szefowe służb,`; L272 `MINISTER KOMUNIKACJI` | — |
| E02-21 | WYS | POTWIERDZONE / ZAWĘŻONE (SMS) | L1869 `Telefon satelitarny Agi dzwoni. Bierze go.`; L1312 `jeżeli macie jeszcze sygnał.` | Ocena sieci komórkowej NIEPOTWIERDZONE |
| E02-22 | WYS | POTWIERDZONE | L1875 `Jutro rano.`; L1883 `Jutro rano jadę do Warszawy.` | E03:L238 na podstawie fragmentu |
| E02-23 | ŚR | POTWIERDZONE | L1961 `Inne kobiety odeszły. Zostały Marta i Karolina.` | E03 l. w audycie przesunięte (np. 122 → 131) |
| E02-24 | ŚR | POTWIERDZONE | L1433 `Pisze drugi SMS -- do Bożeny, mamki dziewczynek:` | — |
| E02-25 | ŚR | ZAWĘŻONE | L318 `Czerwone: trzy. Nowych względem poprzedniego dnia.`; L341 `Wczoraj były dwa. Pojutrze będzie pięć.` | L318 dwuznaczne, nie sprzeczne |
| E02-26 | ŚR | POTWIERDZONE | L345 `Dziewięć.`; L542 `Mamy jeszcze osiem, może dziesięć dni` | — |
| E02-27 | NIS | POTWIERDZONE (zawężenie audytu) | L588 `Nic. Wracamy do Bydgoszczy.` | Realna dyspozycja w Bydgoszczy NIEPOTWIERDZONE |
| E02-28 | NIS | POTWIERDZONE | L758 `Intercity: Marta w PSE, kobieta gdzieś w elektrowni.` | „INTERCUT” to interpretacja |
| E02-29 | ŚR | ZAWĘŻONE | L660 `Jeden punkt -- GPZ Rogów, cztery kilometry od bocznika` | Branża NIEPOTWIERDZONE |
| E02-30 | ŚR | ZAWĘŻONE | L233 `Drastyczny spadek napięcia. Do końca dnia` | Fizyka NIEPOTWIERDZONE |
| E02-31 | ŚR | ZAWĘŻONE | L248 `Gdańsk i Gdynia -- personel zszedł na ląd.` | Dane o zapasach NIEPOTWIERDZONE |
| E02-32 | ŚR | ZAWĘŻONE | L838 `Trzy nazwiska w całej Polsce -- wszystkie zajęte.` | Liczba inżynierek NIEPOTWIERDZONE |
| E02-33 | ŚR | POTWIERDZONE | L1708 `To musimy jeszcze zrobić jedno połączenie do transformatora w gazowni.` | Praca wyspowa NIEPOTWIERDZONE |
| E02-34 | ŚR | POTWIERDZONE | L909 `Niski wybuch, nie kataklizm. Słup dymu.` | — |
| E02-35 | ŚR | POTWIERDZONE | L2097 `Woda będzie ciekła po raz pierwszy w następnej scenie.` | — |
| E02-36 | NIS | ZAWĘŻONE | L2085 `WOLSKA: Widzimy ją cztery razy -- coraz mniej otoczona ludźmi,` | 4 wystąpienia publiczne — zgodne |
| E02-37 | ŚR | POTWIERDZONE | L1972 `Zapieczętowana koperta -- list, którego Marta jeszcze nie otworzyła.` | Spłata w E03 — na podstawie fragmentu audytu, nie sprawdzano |
| E02-38 | ŚR | POTWIERDZONE | L399 `Autor: prof. Marek Dąbrowski, Uniwersytet Warszawski.` (jedyne wystąpienie) | — |
| E02-39 | NIS | ZAWĘŻONE | L1449 `Jedenaście dni.` | Do przyjęcia jako liczba dni pracy |
| E02-40 | NIS | ZAWĘŻONE | L1496 `Przez te dni nie odebrałaś.` | — |
| E02-41 | NIS | POTWIERDZONE | L1502 `Czy tata...`; L1985 `On żyje?` | — |
| E02-42 | NIS | POTWIERDZONE | L1062 `Słuchaj. Idź teraz zrobić zakupy.` | — |
| E02-43 | NIS | POTWIERDZONE | L1280 `Próbuje hotspot, WiFi, wszystko.` | — |
| E02-44 | NIS | ZAWĘŻONE | L921 `Latarnie uliczne nie gasną rano -- nie paliły się w nocy.` | Para ze studzienki NIEPOTWIERDZONE |
| E02-45 | NIS | ZAWĘŻONE | L1739 `Nie ma jej tu jeszcze.` | — |
| E02-46 | NIS | POTWIERDZONE | L467 `SMS. Numer polski.` | E01:L824 na podstawie fragmentu |
| E02-47 | NIS | POTWIERDZONE | L2005 `E W A`; L2046 `KONIEC ODCINKA 2.` | — |
| E02-48 | NIS | POTWIERDZONE | grep `strzelb|dubelt|broń` w E02: pusty | E03:L180 na podstawie fragmentu |
| E02-49 | NIS | POTWIERDZONE | L986 `Kontenerowiec z Gdańska wszedł na mieliznę` | Podróż Very → N-05 |
| E02-50 | NIS | POTWIERDZONE | L1303 `co dwa dni temu. Włosy związane na szybko.` | — |
| E02-51 | NIS | POTWIERDZONE | L995 `Pożar opanowany. Dwie ranne. Instalacja` | — |
| E02-52 | ŚR | POTWIERDZONE | L49 `Kobieta z elektrowni       imię nieznane. Jeden telefon. Jedna decyzja.` (ostatnia pozycja obsady) | — |
| E02-53 | NIS | POTWIERDZONE | L1370 `Mamy dla pani miejsce w Centrum Zarządzania Kryzysowego.` | Nazwa realna NIEPOTWIERDZONE |
| E02-54 | NIS | POTWIERDZONE | L1475 `rzeczy -- dowod osobisty, legitymacje, coś jeszcze.` | Lista sprawdzona punktowo |
| E02-55 | NIS | POTWIERDZONE | L825 `Czego potrzebujesz?`; L847 `Dziękuję, pani Kowalska.` | — |
| E02-56 | NIS | POTWIERDZONE | L392 `Pod spodem jej notatka: "Nie naturalne. Zbyt czyste.` | = B9 |
| E02-M01 | WYS | POTWIERDZONE | L71 `wiatru, powoli, nieuchronnie. Na pokładzie nieruchome cienie martwej` | Audyt podał l.70–72 |
| E02-M02 | ŚR | POTWIERDZONE | L83 `Trzy kobiety na molo giną. Sylwetki w budynku operacyjnym -- giną.` | — |
| E02-M03 | ŚR | POTWIERDZONE | L369 `przyklejone do krawędzi monitora: Paweł i dwie małe dziewczynki,` | — |
| E02-M04 | NIS | POTWIERDZONE | L620 `GŁOS W RADIU` | — |
| E02-M05 | NIS | POTWIERDZONE | L1254 `Ktoś poza kadrem mówi coś cicho.` | — |
| E02-M06 | ŚR | POTWIERDZONE | L1522 `Inni wynoszą rzeczy. Bez pośpiechu, bez paniki.` | — |
| E02-M07 | NIS | POTWIERDZONE | L1536 `sobie ciezarowke do prowadzenia. Na skrzyzowaniu --` | — |
| E02-M08 | ŚR | POTWIERDZONE | L1949 `Gdzieś z tyłu ktoś zaczyna śpiewać -- niski głos, stara pieśń,` | — |
| E02-M09 | ŚR | POTWIERDZONE | L1970 `Karolina mała przy torcie urodzinowym, Marta i Piotrek` | — |
| E02-M10 | WYS | POTWIERDZONE | L2025 `Łopata. Ostrze sztyletu. Kilof zarzucony na ramię. Trzonek kopaczki.` | — |
| E02-M11 | ŚR | POTWIERDZONE (= E02-20) | L177 `MINISTER INFRASTRUKTURY` | — |
| E02-M12 | NIS | POTWIERDZONE | L135 `Ktokolwiek był na kasie -- zostawił ją. Kobieta za lada` | — |
| E02-M13 | NIS | POTWIERDZONE | L1246 `Za nią -- tylko jedna kobieta z notatkami.` | — |
| E02-M14 | NIS | POTWIERDZONE | L364 `jednej z tablic: "Tomasz Kamiński, W-wa, 14.03 -- pacjent zero".` | — |
| Audyt §0: „6 miejsc, w których czas się cofa” | — | POTWIERDZONE | L154 → L159 (T+8 → T+3); L444 → L478; L687 → L755–L770; L913 → L938; L1115 → L1243 | 6. miejsce = wewnętrzne nakładanie montażu 7 (L865) |
| Audyt §9: „Notatka: suma tabeli 70,5; nagłówków 73,5” | — | POTWIERDZONE | przeliczone w d1 | — |

### c2. Handoff (sekcje 2–5) — punkty dotyczące E02

| Punkt | Treść handoffu (cytat H) | Status | Dowód w E02 |
|---|---|---|---|
| A1 | H151 `1. **Aga „V. Strand. Kim jest?" (E02 sc. 3).** Aga nazywa się *z d. Strand*, jej matką jest Vera` | POTWIERDZONE (rozszerzone o ojca) | L410 `"V. Strand. Kim jest?"` |
| A2 | H155 `2. **Wolska — imię/wiek + problem trzech Ann.** E02: „Katarzyna, ~58"; E03: „Anna, 51"` | POTWIERDZONE | L42 `Wicepremier Katarzyna Wolska  ~58 lat. Dawna minister finansów. Twarda.` |
| A3 | H158 `3. **Data publikacji Dąbrowskiego.** E02 sc. 3: „osiemnaście lat temu"; E01 blok P4 (Vera ~52,` | POTWIERDZONE | L400 `Data: osiemnaście lat temu.` |
| A4 | H161 (Mars: dystans vs opóźnienie, E03) | NIE DOTYCZY E02 | grep `mln km|8 min|Mars` w E02: pusty |
| A5 | H164 (E01 sc. 12, „u twojej mamy sąsiadki”) | NIE DOTYCZY E02 | grep `sąsiadki` w E02: pusty |
| A6 | H166 (E01 sc. 2, Marta o „koleżance Agi”) | NIE DOTYCZY E02 | dotyczy E01 |
| B7 | H170 `7. **Zapieczętowany list w żółtej teczce** (E02 sc. 18, „list, którego Marta jeszcze nie otworzyła").` | POTWIERDZONE | L1972 `Zapieczętowana koperta -- list, którego Marta jeszcze nie otworzyła.` |
| B8 | H172 (pojemnik termiczny Very, E03) | NIE DOTYCZY E02 | grep `pojemnik|termicz` w E02: pusty |
| B9 | H175 `9. **„Dwie sekwencje / To niemożliwe"** (E01 Zero Day → E02 sc. 3). Czyta się jako „wirus jest` | POTWIERDZONE | L392 `Pod spodem jej notatka: "Nie naturalne. Zbyt czyste.`; L393 `Ktoś to projektował. Kto?"` |
| B10 | H178 `10. **Los Zofii** — obecnie „żywa, ranna" i w sc. 17 (T+430) zdrowa, śmieje się na ganku. Scenariusz już` | ZAWĘŻONE (E02 nie przesądza) | L2039 `się pali. Zofia osuwa się na kolana, potem na ziemię. Nie rusza się.` |
| C11 | H182 `11. **Śmierć Dąbrowskiego — bez żadnego beatu.** To ojciec Agi i emocjonalny zapalnik Very, a umiera` | POTWIERDZONE | L399 (jedyne wystąpienie nazwiska) |
| C12 | H185 („Czterdziestu mężczyzn”, E03) | ZAWĘŻONE / w E02 tylko tło | L192 `Obsługa techniczna to w dziewięćdziesięciu procentach mężczyźni.`; L829 `Minimum czterdziestu. Mam tu dwie osoby.` |
| C13 | H188 (antidotum vs szczepionka, E03) | NIE DOTYCZY E02 | grep `antidot|szczepion` w E02: pusty |
| C14 | H190 (Karolina–Korańczyk, E03) | NIE DOTYCZY E02 | grep `Korańcz` w E02: pusty |
| D15 | H194 `15. **Numeracja scen w E02 jest pokręcona:** kolejność 5A→5, 6A→7A→6B→6C, 12A→12, 16 przed 15, brak sceny 11;` | POTWIERDZONE z korektą (ZAWĘŻONE: pominięta sc. 7) | L863 `SCENA 7  [CZAS: ok. 2,5 min]` między L804 (6A) a L937 (7A) |
| D16 | H196 `16. **„Zofia Kowalska" (E02 sc. 12A)** — to ciotka *Marty*, a Kowalski to nazwisko *Piotra* (męża Marty).` | POTWIERDZONE | L1416 `Farma pod Łowiczem. Zofia Kowalska.` |
| §2 Vera | H69 `- **Vera Strand** — norweska wirusolog, **64 l.**, twórczyni wirusa, **matka Agi** (widz długo` | OBALONE w części „widz długo nie wie” (E02) | L454 `"Mamo. Żyjesz? Jedź do Polski.`; L1747 |
| §2 Aga | H74 `Przyjaciółka Marty ze studiów. To ona ściąga Verę na farmę SMS-em (ironia dramatyczna).` | POTWIERDZONE | L41 `Przyjaciółka Marty -- znajomość z czasów studenckich.`; L1429 |
| §2 Marta | H75 `- **Marta Kowalska** — **38 l.**, analityczka kryzysowa PSE, prawa ręka Wolskiej.` | ZAWĘŻONE (w E02 doradza, odmawia stanowiska) | L1376 `Pani Premier. Mam córkę.`; L1442 `Dziękuję. Pojadę swoim.` |
| §2 Karolina | H78 `- **Karolina Kowalska** — **19 l.**, **córka Marty i Piotra**, studentka informatyki.` | POTWIERDZONE (rodzaj gramatyczny — E02-54) | L36 `Karolina Kowalska          19 lat. Córka Marty.`; L1669 `Ty. Jesteś informatykiem -- poradzisz sobie ze starym złomem.` |
| §2 Zofia | H86 `- **Zofia** — **~55 l.**, **ciotka Marty**, farmerka (okolice **Łowicza**). Konkretna, niesentymentalna.` | POTWIERDZONE | L46; L1382 `I ciotkę. Na farmie pod Łowiczem.` |
| §2 Helena, Basia | H87 `- **Helena** (~50 l.), **Basia** (~45 l.) — kobiety z wioski / sąsiadki.` | POTWIERDZONE | L47 `Helena                     ~50 lat. Kobieta z wioski.`; L48 |
| §2 Sowa | H88 `- **Generał Anna Sowa** — ~50 l., szefowa sztabu (E02/E03).` | POTWIERDZONE | L165 |
| §2 Bożena | H89 `- **Bożena** — niania/„mamka" córek Agi (Hani i Zosi).` | POTWIERDZONE („mamka” w E02) | L1433 |
| §2 wirus | H60 `- Nazwa potoczna: **wirus Y**; klinicznie **HYV-1**.` | POTWIERDZONE | L363 `Przy ścianie: tablice ze schematami sekwencji wirusa Y (HYV-1). Drobny napis w rogu` |
| §2 pacjent zero | H63 `- **Pacjent zero: Tomasz Kamiński** (W-wa, 14.03). NIE „Adam Kowalski".` | POTWIERDZONE | L364 |
| §2 Dąbrowski | H82 `- **Prof. Marek Dąbrowski** — **70 l.**, polski wirusolog (UW), były partner Very, **ojciec Agi**.` | POTWIERDZONE w zakresie E02 (UW) | L399 |
| §3 E02 opis | H115 `Skorygowany językowo. **PROLOG — UDERZENIE** (T+9: statek-widmo niszczy terminal LNG,` | POTWIERDZONE; „skorygowany językowo” OBALONE w części (E02-54) | L54 `T PLUS 9`; L672 `Beata -- zacznij procedure izolowania sekcji P3 do P7.` |
| §3 garstka kobiet | H116 `garstka kobiet ginie, czarny ekran „EWA"). Zapaść infrastruktury (prąd/woda/paliwo),` | POTWIERDZONE | L83; L93 `E W A` |
| §3 Vera „nieznajoma” | H117 `narady rządu Wolskiej, exodus Marty i Karoliny na farmę Zofii, przybycie Very jako „nieznajomej",` | ZAWĘŻONE (nieznajoma dla farmy najwyżej do L1747) | L1747 |
| §3 klamra | H118 `ognisko. **SCENA 19 — KLAMRA** (T+13, noc): nocny najazd 9 uzbrojonych kobiet na farmę;` | POTWIERDZONE | L2014 `T PLUS 13`; L2026 `Dziewięć sylwetek. Idą w stronę farmy. Nie biegną. Idą równo, spokojnie,` |
| §3 „w głowę” | H119 `Zofia dostaje w głowę przy szopie i upada. KONIEC E02 (rozwiązanie na początku E03).` | ZAWĘŻONE (w E02 brak „głowy”) | L2037 `Cisza. Potem, z boku kadru, z ciemności, szybki ruch, cień. Głuchy odgłos` |
| §3 oś czasu | H140 `Oś czasu całości: T-14 (E01) → T0 Zero Day → T+8 statek (E01) → T+9 uderzenie (E02) →` | POTWIERDZONE (E02); ciągłość z E01 — E02-04 | L54 |
| §3 E01 sc. 15 „dryfuje” | H111 `14 scen + montaż „Zero Day" + **SCENA 15 — STATEK WIDMO** (T+8, gazowiec LNG dryfuje na gazoport` | ZAWĘŻONE (E01 mówi „Płynie… prosto”, na podstawie fragmentu E01:L1237) | E02 L70–L71 dryf |
| §4 „spójne: wieki Hani/Zosi” | H200 `Oś czasu T-14→T+430; wieki Hani/Zosi (4/2 → 5/3 przy lądowaniu); bloki przeszłości Very` | POTWIERDZONE (E02) | L39 `Matka dwóch córek: Hania (4 l.) i Zosia (2 l.).`; L1837 |
| §4 „statek-widmo jako klamra” | H201 `(24 → ~52 l. grają z „64 dziś"); pacjent zero (Kamiński); statek-widmo jako klamra E01→E02;` | ZAWĘŻONE (E02-04) | L56 |
| §5 decyzje otwarte | H208–H214 (Wolska, los Zofii, data, Aga + „V. Strand”, list, wątek odporności) | POTWIERDZONE jako otwarte (nie wdrożone w E02) | L42, L2039, L400, L410, L1972, L393 |
| §5 pomysł „ratunek farmy” | H217 `**Pomysł „ratunek farmy" (gdyby wracać):** najmocniejszy = napastniczki nie chcą jedzenia, tylko` | NIE DOTYCZY E02 (pomysł, nie ustalenie; w E02 brak) | grep `chłop` pusty |
| §1 metraż (z notatek decyzji) | H43 `- **E02 — EWA** (~67 min)` | POTWIERDZONE jako rozbieżność | L3 `Format: ok. 65 minut` |

### c3. Notatki `E02_scenariusz.md` (twierdzenia o scenariuszu)

| Twierdzenie notatek (sekcja) | Status | Dowód |
|---|---|---|
| §1 struktura: prolog l.52–93, sceny, „KONIEC ODCINKA 2.” l.2046, tabela l.2049–2080, nota l.2083–2108 | POTWIERDZONE | L2046 `KONIEC ODCINKA 2.`; L2049 `PODSUMOWANIE CZASU -- ODCINEK 2`; L2083 `NOTA DRAMATURGICZNA -- ODCINEK 2` |
| §1 plik ma 2108 linii | POTWIERDZONE | `grep -c ''` = 2108 |
| §2 28 bloków numerowanych + prolog = 29; brak 11 | POTWIERDZONE | lista nagłówków w E02-11 |
| §2 tabela 28 pozycji (bez 3B), RAZEM 69,0, suma 70,5 | POTWIERDZONE | d1 |
| §2 suma nagłówków „ok. 72–73,5” | ZAWĘŻONE (dokładnie 73,5) | d1 |
| §2 cztery niezgodności (3, 7, 18, 3B) | POTWIERDZONE — jedyne | d1 |
| §3 PROLOG: cienie martwej załogi = mężczyźni w kadrze | POTWIERDZONE | L70 (M01) |
| §3 SC 1: imię Katarzyna l.111; kartki l.139–140; napis l.154; T+6 rozmowa l.145–148 do zestawienia z sc. 4 | POTWIERDZONE; zestawienie z sc. 4 ZAWĘŻONE (różne dni) | L139 `"Pani Małgorzata -- mamy jedzenie. Prosimy dzwonić."`; L146 `Marta z PSE. Krótka rozmowa. Karolina mówi coś.` |
| §3 SC 1A: „ministrowie”, MINISTER/MINISTRA, „marynarze”, statek pod Helem l.253 | POTWIERDZONE | L253 `bez kontroli na Bałtyku. Jeden już osiadł` |
| §3 SC 2: „Dziewięć” niejasne; Bydgoszcz l.325 | POTWIERDZONE | L345; L325 |
| §3 SC 3: tablica Kamiński, zdjęcie Pawła, sekwencje, „osiemnaście”, przypis, telefon, „Na imię w notatniku” niejasne | POTWIERDZONE | L426 `Na imię w notatniku.` |
| §3 SC 3B: T+6 przed sc. 4 | POTWIERDZONE | E02-06 |
| §3 SC 4: w tabeli „Salon Marty”, w pliku PSE | POTWIERDZONE | E02-13 |
| §3 SC 4A: „Wracamy do Bydgoszczy” — PSE w Bydgoszczy? | ZAWĘŻONE (dwuznaczność, nie lokalizacja) | L588 |
| §3 SC 5A: „Wisła -- sytuacja na Wolskiej” kolizja nazw; Marta jedzie do PSE z Mokotowa | POTWIERDZONE (N-07, E02-39) | L618; L647 |
| §3 SC 5: „Nigdy tego nie robiłam sama.” | POTWIERDZONE | L676 `Nigdy tego nie robiłam sama.` |
| §3 SC 5B: „Już dziewiąty dzień”; odbiera natychmiast | POTWIERDZONE | L701 `Gdzie jesteś? Już dziewiąty dzień.`; L694 |
| §3 SC 6: „Intercity:” niejasne | ZAWĘŻONE (= INTERCUT, E02-28) | L758 |
| §3 SC 6A: „Trzymamy Warszawę, Kraków i Wrocław” sprzeczne z 6B/6C | ZAWĘŻONE (E02-09) | L814 |
| §3 SC 7: pierwsza muzyka „ok. 30 min od startu” | ZAWĘŻONE: 30:30 wg tabeli, 34:00 wg etykiet (d1) | L867 `Muzyka: zaczyna się od dołu -- tylko kontrabas,` |
| §3 SC 7: duplikat końca 6C | POTWIERDZONE | E02-08 |
| §3 SC 7A: „MINISTER INFRASTRUKTURY” przy „cztery kobiety” | POTWIERDZONE | L941 `Wolska i cztery kobiety. Generator słychać za ścianą.`; L1001 |
| §3 SC 6B: mapa prawie cała czerwona | POTWIERDZONE | L1087 |
| §3 SC 6C: „Przez jedenaście dni…”, „Napiszcie raport końcowy” | POTWIERDZONE | L1147; L1235 `Napiszcie raport końcowy i idźcie.` |
| §3 SC 8: „Chcialabym”; T+10 po T+11 | POTWIERDZONE | L1251; E02-10 |
| §3 SC 9: „Pierwsze absolutne zero elektroniki” | POTWIERDZONE | L1274 `Pierwsze absolutne zero elektroniki w całym serialu.` |
| §3 SC 10: komunikat z 14:00; miejsca zbiórek | POTWIERDZONE | L1320 `czternastej: "Jeżeli ktoś ma rodzinę na wsi --`; L1330 |
| §3 SC 12A: plecak i torba niezgodne z sc. 12 | ZAWĘŻONE (E02-05) | L1345; L1461 |
| §3 SC 12A: „Pani Premier” l.1356, 1366 | POTWIERDZONE (pełna lista 7 miejsc) | E02-17 |
| §3 SC 12: „Nie panikowany”, „Nie dużo”, „dowod”, teczka, „Przez te dni nie odebrałaś”, „Inni” | POTWIERDZONE | L1458 `Nie panikowany -- spokojny, zdecydowany.`; L1475; L1496 |
| §3 SC 13: „ciezarowke”, „skrzyzowaniu”; „Napisałam do niej” vs rozmowa | POTWIERDZONE (N-08) | L1536; L1563 |
| §3 SC 14: brak nazwiska Zofii w scenie | POTWIERDZONE | L1583 `ZOFIA wychodzi z domu. Około pięćdziesięciu pięciu lat,` |
| §3 SC 16: „Jesteś informatykiem”; „Ale to na jutro”; chronologia 16 → 15 poprawna | POTWIERDZONE | L1669; L1709 `Ale to na jutro.` |
| §3 SC 15: l.1747 jedyne „Agnieszka” w E02 | POTWIERDZONE | grep `Agnieszk`: tylko L1747 |
| §3 SC 17: „niski głos”; „Jutro rano jadę do Warszawy” | POTWIERDZONE | L1949; L1883 |
| §3 SC 18: zdjęcia Piotrka; koperta; drugie „E W A” | POTWIERDZONE | L1969; L1972; L2005 |
| §3 SC 19: miejsce uderzenia nieopisane („w głowę” brak); szopa ze zwierzętami ≠ szopa z agregatem | POTWIERDZONE (N-09) | L2037–L2038; L2030 |
| §4 kanon: wieki Vera 64, Marta 38, Aga 34, Karolina 19, Zofia ~55, Wolska ~58, Sowa ~50, Hania 4, Zosia 2 | POTWIERDZONE | L35 `Dr Marta Kowalska          38 lat. Analityczka PSE. Teraz też droga i farma.`; L43; L46; L165 |
| §4 kanon: „Czterokrotne Pani Premier (l.811, 1128, 1136, 1144, 1356, 1366)” | OBALONE (7 razy; liczba „cztery” niezgodna nawet z własną listą 6 linii) | grep: + L1376 `Pani Premier. Mam córkę.` |
| §4 kanon: „Mąż Piotr Kowalski (poza E02)” | ZAWĘŻONE (w E02 jest „Piotrek” na zdjęciach; nazwisko i Ares IV nie padają) | L1969 |
| §4 kanon: Zofia — nazwisko „Kowalska” w sc. 12A | POTWIERDZONE | L1416 |
| §5 A1, A3, B7, B9, D15, D16 | POTWIERDZONE (jak c2) | c2 |
| §5 A2: „Anna nie pojawia się przy Wolskiej w E02” | OBALONE | L165 `GENERAŁ ANNA SOWA (szefowa sztabu, pięćdziesiąt lat, rzeczowa)` (sc. 1A), L945 (sc. 7A) |
| §5 B10: E02 kończy na „Nie rusza się”, tekst nie przesądza | POTWIERDZONE | L2039 |
| §5 C11: Dąbrowski tylko w sc. 3 | POTWIERDZONE (tylko L399; notatki podały l.400–406 — nazwisko jest w L399) | L399 |
| §5 C12: temat mężczyzn tylko naświetlony | POTWIERDZONE | L205 `Kobiety stanowiły jeden procent załogi.`; L970 |
| §5 A4, A5, A6, B8, C13, C14 nie dotyczą E02 | POTWIERDZONE | c2 |
| §6a lista 6 miejsc „bez mężczyzn” | POTWIERDZONE, niepełna (audyt: 14) | c1 M01–M14 |
| §6a „Sceny bez problemu: … 5A … 8” | ZAWĘŻONE (M04 L620, M05 L1254) | L620; L1254 |
| §6b chronologia: 3B przed 4; 6A przed 6B; 8 po 6C; duplikat 7/6C; 12A vs 12; l.1496 vs 5B/6B | POTWIERDZONE (6A i 12A — ZAWĘŻONE) | E02-06, 09, 10, 08, 05, 40 |
| §6b „Sc. 4 vs sc. 1 (T+6)” | ZAWĘŻONE (różne dni, brak sprzeczności) | L145; L506 |
| §6b lokalizacja PSE Bydgoszcz vs Warszawa | ZAWĘŻONE | E02-27 |
| §6b nota o wodzie l.2097 | POTWIERDZONE | L2097 |
| §6b nota „cztery razy” — „co najmniej pięć razy” | ZAWĘŻONE (6 na ekranie; 4 wystąpienia publiczne) | E02-36 |
| §6b „Intercity” | ZAWĘŻONE | E02-28 |
| §6c „Wicepremier … l.421 … l.1370” | OBALONE dla l.1370 (tam jest „Centrum Zarządzania Kryzysowego”, nie „Wicepremier”) | L1370 `Mamy dla pani miejsce w Centrum Zarządzania Kryzysowego.` |
| §6c „Pani Premier” 6 miejsc | ZAWĘŻONE (7) | E02-17 |
| §6c „Wisła — sytuacja na Wolskiej” | POTWIERDZONE | N-07 |
| §6c Basia/Beata, Ania/Anna Sowa | POTWIERDZONE | L48 `Basia                      ~45 lat. Sąsiadka Zofii.`; L320; L321 |
| §6c szopa — dwa budynki | POTWIERDZONE | N-09 |
| §6d literówki (l.760, 792, 1251, 1458, 1461, 1475, 1536, 1669, 1860–1861, 425–426, 1563) | POTWIERDZONE | L760 `osob. To jest rozmowa systemow przez ludzkie głosy.`; L792 `I po waszej. Dziękuje.`; L1861 `coraz cisza, coraz głębia, aż do dna.` |
| §6e „Dziewięć” niejasne | POTWIERDZONE | E02-26 |
| §7 ryzyka produkcyjne 1–10 (dialogi, ekrany, napisy w kadrze, Entity, sceny nocne, montaże, dzieci, 6C, tłumaczenie) | fakty o tekście POTWIERDZONE (np. L154 napis w kadrze, L1619 tabliczka); oceny produkcyjne NIEZBADANE (poza zakresem logiki/timingu/napięcia) | L1619 `Tabliczka na ścianie: "STEROWANIE GŁÓWNE BG-01".` |
| §8 skrót: 29 bloków, brak 11, czasy, zakończenie | POTWIERDZONE | d1, L2046 |

### c4. Notatki `decyzje_i_konsultacje.md` (część o E02)

| Twierdzenie (linia notatek) | Status | Dowód w E02 |
|---|---|---|
| l.46, l.81: „Usunięta E02 Scena 11” — WDROŻONE | POTWIERDZONE | grep `SCENA 11` pusty; luka w numeracji zostaje (E02-11) |
| l.50: „E02: wirus Y w całym odcinku” | POTWIERDZONE | grep `wirus|HYV|ADAM`: L43 (wirusolog), L363 `wirusa Y (HYV-1)`, L1885; brak „ADAM-1” |
| l.50, l.92, l.196, l.244 (K4): metraż ~66–67 NIEWDROŻONE | POTWIERDZONE | L3 `Format: ok. 65 minut` |
| l.58: „E02: prolog — uderzenie, Scena 19 — klamra” | POTWIERDZONE | L52 `PROLOG -- UDERZENIE  [CZAS: ok. 2 min]`; L2012 `SCENA 19 -- KLAMRA  [CZAS: ok. 2 min]` |
| l.79: Kamiński WDROŻONE l.364 | POTWIERDZONE | L364 |
| l.81: brak „Ida” | POTWIERDZONE | grep `Ida\b` pusty |
| l.120, l.155, l.266 (K15): „Zofia Kowalska” l.1416, 1429, 1435 | POTWIERDZONE | E02-19 |
| l.140: A1 l.410 OTWARTE | POTWIERDZONE | L410 |
| l.141, l.256 (K10): Wolska Katarzyna l.42 vs Anna (E03) | POTWIERDZONE | L42 |
| l.142: A3 l.400 OTWARTE | POTWIERDZONE | L400 |
| l.146: B7 l.1972 OTWARTE | POTWIERDZONE | L1972 |
| l.154: D15 „E02 l.2052–2077: Scena 12A, Scena 18, brak 11” | POTWIERDZONE (tabela kończy się w L2078 na sc. 19) | L2070 `Scena 12A  Samochód wojskowy -- propozycja Wolskiej (T+12)  ok. 3,0 min`; L2078 `Scena 19   Klamra -- nocny napad na farmę, Zofia (T+13)     ok. 2,0 min` |
| l.16: brak edycji scenariuszy po 8.06 (mtime) | NIEZBADANE (dotyczy archiwum źródłowego, nie treści; poza zakresem) | — |
| l.312: lista linii E02 (l.3, 42, 364, 400, 406/410, 1416/1429/1435, 1972, 2052–2077) | POTWIERDZONE | jw. |

---

## (d) TIMING

### d1. Tabela czasów scen

Źródła w pliku: (1) etykiety `[CZAS: ok. X min]` w nagłówku każdego bloku (29 etykiet, regex na `CZAS: ok. X min`); (2) nagłówek L3 `Format: ok. 65 minut`; (3) tabela czasów L2049–L2080 (28 pozycji). Start/koniec = suma etykiet poprzednich bloków (kolejność pliku).

| # | Blok | Linia | T / godzina | CZAS (etykieta) | Tabela | Różnica | Start | Koniec |
|---|---|---|---|---|---|---|---|---|
| 1 | PROLOG | L52 | T+9, świt | 2 | 2,0 | 0 | 0:00 | 2:00 |
| 2 | 1 | L98 | T+1 → T+8 | 3 | 3,0 | 0 | 2:00 | 5:00 |
| 3 | 1A | L158 | T+3, 14:00 (L169) | 2,5 | 2,5 | 0 | 5:00 | 7:30 |
| 4 | 2 | L309 | T+3 | 2,5 | 2,5 | 0 | 7:30 | 10:00 |
| 5 | 3 | L357 | T+5 | 5 | 3,0 | **+2,0** | 10:00 | 15:00 |
| 6 | 3B | L443 | T+6 (Oslo T+6) | 1,5 | **brak** | +1,5 | 15:00 | 16:30 |
| 7 | 4 | L476 | T+5, wieczór | 2,5 | 2,5 | 0 | 16:30 | 19:00 |
| 8 | 4A | L521 | T+6 | 2 | 2,0 | 0 | 19:00 | 21:00 |
| 9 | 5A | L592 | T+7 południe → T+8 świt | 3 | 3,0 | 0 | 21:00 | 24:00 |
| 10 | 5 | L652 | T+9, ranek | 2,5 | 2,5 | 0 | 24:00 | 26:30 |
| 11 | 5B | L685 | T+9, wieczór | 2 | 2,0 | 0 | 26:30 | 28:30 |
| 12 | 6 | L754 | T+9 (dzień, L770) | 3 | 3,0 | 0 | 28:30 | 31:30 |
| 13 | 6A | L804 | T+10, noc | 2,5 | 2,5 | 0 | 31:30 | 34:00 |
| 14 | 7 | L863 | T+9 wieczór → T+11 ranek | 2,5 | 4,0 | **−1,5** | 34:00 | 36:30 |
| 15 | 7A | L937 | T+10 (ciemno, L1014) | 2 | 2,0 | 0 | 36:30 | 38:30 |
| 16 | 6B | L1048 | T+10, 19:15 | 2 | 2,0 | 0 | 38:30 | 40:30 |
| 17 | 6C | L1113 | T+11, 05:43 | 4 | 4,0 | 0 | 40:30 | 44:30 |
| 18 | 8 | L1241 | T+10 (nagłówek) | 2 | 2,0 | 0 | 44:30 | 46:30 |
| 19 | 9 | L1270 | T+11, popołudnie | 2 | 2,0 | 0 | 46:30 | 48:30 |
| 20 | 10 | L1298 | T+11 (po 14:00, L1319–L1320) | 1,5 | 1,5 | 0 | 48:30 | 50:00 |
| 21 | 12A | L1341 | T+12, 06:20 | 3 | 3,0 | 0 | 50:00 | 53:00 |
| 22 | 12 | L1453 | T+12, dzień | 3 | 3,0 | 0 | 53:00 | 56:00 |
| 23 | 13 | L1528 | T+12, dzień | 1,5 | 1,5 | 0 | 56:00 | 57:30 |
| 24 | 14 | L1571 | T+12, popołudnie | 2,5 | 2,5 | 0 | 57:30 | 60:00 |
| 25 | 16 | L1613 | T+13, rano | 3 | 3,0 | 0 | 60:00 | 63:00 |
| 26 | 15 | L1725 | T+13, wieczór | 2 | 2,0 | 0 | 63:00 | 65:00 |
| 27 | 17 | L1808 | T+13, noc | 3,5 | 3,5 | 0 | 65:00 | 68:30 |
| 28 | 18 | L1957 | T+13, późna noc | 3 | 2,0 | **+1,0** | 68:30 | 71:30 |
| 29 | 19 KLAMRA | L2012 | T+13, głęboka noc | 2 | 2,0 | 0 | 71:30 | 73:30 |

**Sumy (składniki wypisane):**
- **Suma 29 etykiet CZAS:** 2 + 3 + 2,5 + 2,5 + 5 + 1,5 + 2,5 + 2 + 3 + 2,5 + 2 + 3 + 2,5 + 2,5 + 2 + 2 + 4 + 2 + 2 + 1,5 + 3 + 3 + 1,5 + 2,5 + 3 + 2 + 3,5 + 3 + 2 = **73,5 min**. Kontrola skryptem (regex po etykietach): 73,5; liczba etykiet 29.
- **Suma 28 pozycji tabeli (L2051–L2078):** 2,0 + 3,0 + 2,5 + 2,5 + 3,0 + 2,5 + 2,0 + 3,0 + 2,5 + 2,0 + 3,0 + 2,5 + 4,0 + 2,0 + 2,0 + 4,0 + 2,0 + 2,0 + 1,5 + 3,0 + 3,0 + 1,5 + 2,5 + 2,0 + 3,0 + 3,5 + 2,0 + 2,0 = **70,5 min**. Kontrola skryptem: 70,5; liczba pozycji 28.
- **Kontrola różnicy:** 73,5 − 70,5 = 3,0 = (+2,0 sc. 3) + (+1,5 sc. 3B) + (−1,5 sc. 7) + (+1,0 sc. 18) = 3,0. Zgadza się.

**Rozbieżności (wszystkie):**
1. Nagłówek L3 „ok. 65” vs suma etykiet 73,5: **+8,5 min**.
2. Nagłówek L3 „ok. 65” vs RAZEM tabeli L2080 „ok. 69,0”: **+4,0 min**.
3. RAZEM tabeli „69,0” vs suma pozycji tabeli 70,5: **błąd sumowania 1,5 min** w samej tabeli.
4. Suma etykiet 73,5 vs suma pozycji tabeli 70,5: **3,0 min** (składniki wyżej).
5. Etykieta vs tabela: sc. 3 (5 vs 3,0), sc. 7 (2,5 vs 4,0), sc. 18 (3 vs 2,0), sc. 3B (1,5 vs brak). Pozostałe 25 pozycji zgodne.
6. Tabela ma kolejność 15 przed 16 (L2074–L2075), plik 16 przed 15 (L1613, L1725).
7. Źródła poza plikiem: handoff H43 „~67”, decyzje „~66–67” — rozbieżność z L3 (−2 do −1,5) i z sumą etykiet (+6,5 do +7,5).

### d2. Czas ekranowy według rodzaju materiału i według dni T (składniki)

**Według rodzaju (etykiety):**
- Infrastruktura i państwo (PSE, narady, telefony rządowe, media państwowe): 1A 2,5 + 2 2,5 + 4A 2 + 5 2,5 + 6 3 + 6A 2,5 + 7A 2 + 6C 4 + 8 2 + 10 1,5 = **24,5 min (33,3%)**.
- Montaże społeczne i katastrofa: PROLOG 2 + 1 3 + 5A 3 + 7 2,5 = **10,5 min (14,3%)**.
- Wydarzenia osobiste (rodzina, przyjaźń, farma): 3 5 + 3B 1,5 + 4 2,5 + 5B 2 + 6B 2 + 9 2 + 12A 3 + 12 3 + 13 1,5 + 14 2,5 + 16 3 + 15 2 + 17 3,5 + 18 3 + 19 2 = **38,5 min (52,4%)**.
- Kontrola: 24,5 + 10,5 + 38,5 = 73,5.
- Uwaga: sc. 4, 5B, 6B dzieją się w PSE (osobiste rozmowy w pracy), a 12A łączy wątek rządowy z osobistym; zaliczone do osobistych, bo ich zdarzeniem jest relacja.

**Rozkład w czasie:** do 50:00 (bloki 1–20) infrastruktura ma 24,5 min z 50, czyli **49%**; po 50:00 (bloki 21–29) — 0 min infrastruktury, 23,5 min osobistych. Odcinek jest więc podzielony na dwie części o różnej naturze: „systemową” (0–50) i „ludzką” (50–73,5).

**Według dni T (etykiety; montaże wielodniowe liczone w dniu startu):**

| Dzień | Bloki | Minuty |
|---|---|---|
| T+1 (montaż do T+8) | 1 | 3 |
| T+3 | 1A 2,5 + 2 2,5 | 5 |
| T+5 | 3 5 + 4 2,5 | 7,5 |
| T+6 | 3B 1,5 + 4A 2 | 3,5 |
| T+7 (do T+8) | 5A | 3 |
| T+9 | PROLOG 2 + 5 2,5 + 5B 2 + 6 3 + 7 2,5 | 12 |
| T+10 | 6A 2,5 + 7A 2 + 6B 2 + 8 2 | 8,5 |
| T+11 | 6C 4 + 9 2 + 10 1,5 | 7,5 |
| T+12 | 12A 3 + 12 3 + 13 1,5 + 14 2,5 | 10 |
| T+13 | 16 3 + 15 2 + 17 3,5 + 18 3 + 19 2 | 13,5 |
| **Razem** | 3 + 5 + 7,5 + 3,5 + 3 + 12 + 8,5 + 7,5 + 10 + 13,5 | **73,5** |

Dni bez scen: T+2 i T+4 (tylko beaty montażu 1), T+8 (tylko beaty montaży 1 i 5A).

### d3. Analiza rytmu

**Proporcje bloków.** Infrastruktura 33,3%, montaże 14,3%, osobiste 52,4% (d2). Proporcja całości jest zdrowa, ale rozkład nie: pierwsze 50 minut to prawie w połowie mapy i narady, ostatnie 23,5 min — wyłącznie relacje. Brak przeplotu sprawia, że w części 1 brakuje stawki osobistej, a w części 2 — zagrożenia z zewnątrz (aż do sc. 19).

**Długie odcinki statyczne.**
1. **Ciąg PSE 24:00–34:00 (sc. 5, 5B, 6, 6A — 10 min, jedno miejsce).** Cztery bloki z rzędu w centrum dyspozytorskim; zdarzenie dramatyczne to zmiana koloru punktów (L661 `wysokiego napięcia -- zmienił kolor z pomarańczowego na czerwony.`) i rozmowy telefoniczne. Wizualnie statyczne (ekran, mapa, konsola).
2. **Narady 1A i 7A (4,5 min)** — dwie sceny raportowe o tej samej konstrukcji (Wolska pyta jednym słowem, ktoś referuje): L175 `Woda?`, L183 `Paliwo.`, L210 `Gaz?` … L957 `Gaz?`, L965 `Dobrze. Pożary?`, L992 `Rafineria?`. 7A powtarza informacje pokazane chwilę wcześniej w montażu 7 (Świnoujście, rafineria, lotnictwo).
3. **Sc. 3 (5 min, najdłuższa scena odcinka)** — w większości samotna praca przy mikroskopie i laptopie; ma ważne odkrycie, ale też czas „martwy” (L438–L440).
4. **Spokojny ciąg 53:00–63:00 (sc. 12, 13, 14, 16 — 10 min)** — pakowanie, droga, przyjazd, naprawa; brak zagrożenia z zewnątrz.
5. **Sc. 17 + 18 (6,5 min nocą przy ognisku)** — celowa cisza, ale razem z 15 to 8,5 min wieczoru T+13 bez wydarzenia zewnętrznego przed klamrą.

**Przyspieszenia i zwolnienia.**
- Start szybki: prolog (2 min) z jednym wydarzeniem, potem montaż 1 skacze przez 8 dni w 3 minuty (przyspieszenie), po czym 1A i 2 wracają do T+3 i zwalniają (narada + PSE: 5 min).
- Zwolnienie w środku: T+9 to 12 minut ekranowych (najdłuższy dzień) w pięciu blokach — najwięcej czasu dla jednego dnia, w którym zdarzenie to dwie zmiany koloru punktów i dwa telefony.
- Przyspieszenie: 6B (2) → 6C (4) → 8 (2) → 9 (2) → 10 (1,5) — od 38:30 do 50:00 bloki są krótkie, a każdy kończy się utratą (sieć, obraz, telefon, ostatnia stacja). To najlepiej zbudowany odcinek rytmu w E02.
- Zwolnienie po kulminacji: od 50:00 do 71:30 (21,5 min) tempo spada do „drogi i farmy”; sc. 16 (3 min) jest najmocniejszym hamulcem.
- Szarpnięcie końcowe: sc. 19 (2 min) po planszy „E W A”.
- Muzyka: pierwsza muzyka w sc. 7 (L867) startuje w 34:00 wg etykiet (30:30 wg tabeli); nota L17 wymaga tylko 10 minut bez muzyki — warunek spełniony z dużym zapasem.

**Wnioski.** (1) Metraż jest za ciężki w środku (T+9: 12 min; PSE 10 min w jednym miejscu; dwie narady). (2) Wątek osobisty Agi i Very ma 33,5 i 46,5 min przerwy (N-01). (3) Najlepszy rytm ma ciąg 6B–10; warto go chronić przy cięciach. (4) Po 50:00 brakuje zewnętrznego zagrożenia, które wzmocniłoby klamrę (np. zasiew z E02-48). (5) Bez skrótów nie ma miejsca na brakujące beaty (E02-01/38, N-01, E02-24, E02-48).

### d4. PROPOZYCJA metrażu per scena

Założenia (PROPOZYCJA): cel ok. 66–67 min (decyzja D-07 — decyzje mówią ~66–67, L3 mówi 65); kolejność po poprawkach E02-03, 06, 07, 08, 10 (f1, krok 4); numery scen jak w pliku.

| Blok | Obecnie (etykieta) | PROPOZYCJA | Zmiana i powód |
|---|---|---|---|
| PROLOG | 2 | 2 | bez zmian |
| 1 | 3 | 2 | −1; montaż T+1–T+2 bez komunikatu (E02-03) |
| 1A | 2,5 | 2,5 | + krótki beat komunikatu na końcu (E02-03 wariant 2), kosztem skrótu raportów |
| 2 | 2,5 | 2 | −0,5; powtarza informacje 1A |
| 3 | 5 | 4 | −1; rozpoznanie matki i beat ojca (E02-01, 38) w krótszej scenie |
| 3B | 1,5 | 1,5 | bez zmian (T+5 noc, E02-06) |
| 4 | 2,5 | 2 | −0,5 |
| 4A | 2 | 1,5 | −0,5; prognoza skrócona (E02-26) |
| 5A | 3 | 3 | + beaty T+3–T+8 z montażu 1, bez wydłużenia |
| nowy beat Agi T+8 (N-01) | 0 | 1,5 | +1,5; spłata L436 i ciągłość wątku (chronologicznie po 5A) |
| 5 | 2,5 | 2 | −0,5; scalić rytm z sc. 6 (E02-07) |
| 6 | 3 | 2 | −1; rozmowa systemów — wystarczy krócej |
| 5B | 2 | 2 | bez zmian (po sc. 6) |
| 6A | 2,5 | 2 | −0,5 |
| 7 cz. 1 (do briefingu 3) | 2,5 (łącznie) | 2 | podział montażu (E02-08); zawiera beat Agi L873 |
| 7A | 2 | 1,5 | −0,5; bez powtórzeń z montażu |
| 6B | 2 | 2 | bez zmian |
| 6C | 4 | 3,5 | −0,5; skrót sekwencji przełączników |
| 8 | 2 | 1,5 | −0,5 (T+11, E02-10) |
| 7 cz. 2 (po wyłączeniu) | — | 1,5 | z podziału montażu; bez duplikatu L931–L933 |
| 9 | 2 | 2 | bez zmian (chronić) |
| 10 | 1,5 | 1 | −0,5 (N-03) |
| 12A | 3 | 2,5 | −0,5; + teczka z szafy PSE (E02-05) |
| 12 | 3 | 2,5 | −0,5; bez powtórzenia „Czy tata” (E02-41) |
| 13 | 1,5 | 1 | −0,5 |
| 14 | 2,5 | 2 | −0,5 |
| 16 | 3 | 2,5 | −0,5 |
| 15 | 2 | 2 | + kwestia o podróży (N-05) i Bożenie (E02-24) bez wydłużenia |
| 17 | 3,5 | 4 | +0,5; zasiew strzelby i męża Zofii (E02-48) |
| 18 | 3 | 2,5 | −0,5 |
| 19 | 2 | 2,5 | +0,5; „Czerń trzyma się dłużej” wymaga czasu |

**Suma PROPOZYCJI (31 pozycji, w kolejności tabeli):** 2 + 2 + 2,5 + 2 + 4 + 1,5 + 2 + 1,5 + 3 + 1,5 + 2 + 2 + 2 + 2 + 2 + 1,5 + 2 + 3,5 + 1,5 + 1,5 + 2 + 1 + 2,5 + 2,5 + 1 + 2 + 2,5 + 2 + 4 + 2,5 + 2,5 = **66,5 min** (w granicach „~66–67” z decyzji; kontrola skryptem: 66,5, 31 pozycji). Według rodzaju: infrastruktura 1A 2,5 + 2 2 + 4A 1,5 + 5 2 + 6 2 + 6A 2 + 7A 1,5 + 6C 3,5 + 8 1,5 + 10 1 = 19,5 (29,3%); montaże PROLOG 2 + 1 2 + 5A 3 + 7 cz. 1 2 + 7 cz. 2 1,5 = 10,5 (15,8%); osobiste 3 4 + 3B 1,5 + 4 2 + beat Agi 1,5 + 5B 2 + 6B 2 + 9 2 + 12A 2,5 + 12 2,5 + 13 1 + 14 2 + 16 2,5 + 15 2 + 17 4 + 18 2,5 + 19 2,5 = 36,5 (54,9%). Kontrola: 19,5 + 10,5 + 36,5 = 66,5. Najdłuższa przerwa w wątku Agi spada z 33,5 do ok. 15 min (beat Agi po 5A, beat L873 w 7 cz. 1, potem 12A).

---

## (e) NAPIĘCIE

### e1. Kotwice skali 0–10

- **0** — świat bez zagrożenia i bez otwartego pytania.
- **2–3** — spokój z cieniem: drobny niepokój, tajemnica bez wskazanego zagrożenia, chwilowa ulga (praca, podróż, przyjazd).
- **5** — zagrożenie nazwane, dotykające bliskiej osoby bohaterki albo systemu, od którego zależy jej życie; wynik otwarty, nikt jeszcze niczego nie traci na ekranie.
- **7–8** — utrata w toku lub dokonana na ekranie (jedna postać, jeden wątek albo całe miasto), przy świadomości, że zagrożenie rośnie.
- **10** — nieodwracalna katastrofa na ekranie, dotykająca wszystkich głównych postaci naraz, bez nadziei w obrębie odcinka.

Ocena dotyczy wiedzy widza w danym miejscu kolejności pliku (nie chronologii T). Widz zna E01 (zakładamy oglądanie po kolei).

### e2. Krzywa napięcia scena po scenie (100% bloków, kolejność pliku)

| # | Blok | Ocena | Zdarzenie z tekstu (cytat, linia) i uzasadnienie |
|---|---|---|---|
| 1 | PROLOG | 8 | L83 `Trzy kobiety na molo giną. Sylwetki w budynku operacyjnym -- giną.`; L88 `potem echo, potem nic. Żadnych wozów strażackich. Nikt nie przyjedzie.` Katastrofa na ekranie, ale bez głównych postaci (stąd nie 10). |
| 2 | 1 | 4 | L108 `zatrzymywania się -- po prostu idzie i płacze.`; L123 `ale jest pod kontrolą.` Żałoba i pierwsze braki; brak zagrożenia dla bohaterek. |
| 3 | 1A | 5 | L263 `Zależy od decyzji które podejmiecie w ciągu`; L291 `Bo jeśli tego nie powiemy -- panika zabija`. Zagrożenie systemowe nazwane, zegar „sześciu godzin”. Osłabione, bo widz zna już komunikat (E02-03). |
| 4 | 2 | 4 | L345 `Dziewięć.`; L354 `Obie wiedzą co to znaczy.` Zegar bez jednostki; powtórzenie skali z 1A w mniejszym planie. |
| 5 | 3 | 6 | L393 `Ktoś to projektował. Kto?"`; L406 `Małym drukiem: "Dane wstępne: V. Strand (materiały niepublikowane)."` Widz wie z E01, kim jest V. Strand — silna ironia; L410 (Aga nie wie, kim jest matka) obniża wiarygodność, stąd 6, nie 8. |
| 6 | 3B | 6 | L454 `"Mamo. Żyjesz? Jedź do Polski.`; L473 `Wstaje. Zaczyna się pakować.` Córka wzywa sprawczynię; widz wie więcej niż Aga. |
| 7 | 4 | 4 | L506 `Nie odbiera.`; L514 `"Mamo. Jak u ciebie."` Konflikt rodzinny bez stawki życia; komunikat TV powtarza sc. 1. |
| 8 | 4A | 4 | L542 `Mamy jeszcze osiem, może dziesięć dni`; L575 `będę miała prośbę służbową. Konkretną.` Zegar się wydłuża (ulga zamiast napięcia, E02-26); mały hak. |
| 9 | 5A | 6 | L609 `Zostaje wypchana. Upada. Nikt jej nie pomaga wstać.`; L621 `Wsparcia nie ma. Jesteście same.` Rozpad porządku na ekranie; bez bohaterek (Marta tylko przejeżdża, L649). |
| 10 | 5 | 6 | L665 `Trzy minuty -- zmienia się następny. GPZ Krzyżanów.`; L676 `Nigdy tego nie robiłam sama.` Pierwsza kaskada „na żywo”. |
| 11 | 5B | 5 | L723 `Mówisz że nic, ale każesz mi napełniać wanny.`; L742 `Rozłącza się zanim Karolina odpowie.` Kłamstwo matki wobec córki; stawka osobista nazwana. |
| 12 | 6 | 5 | L770 `Do wieczora. Może do północy jeżeli się uda.`; L796 `Nie będzie żółty długo.` Zegar systemu; postać bez twarzy (celowo, L2089–L2092). |
| 13 | 6A | 6 | L821 `Przy obecnym tempie -- dwadzieścia cztery,`; L838 `Trzy nazwiska w całej Polsce -- wszystkie zajęte.` Zegar wraca do godzin; brak pomocy. |
| 14 | 7 | 7 | L878 `Kobieta odkręca i zakręca. Zakręca ostatni raz.`; L918 `Potem daleki grzmot. Nie burza.` Utraty w toku (woda, katastrofa lotnicza); koniec L933 zdradza wynik 6C (E02-08). |
| 15 | 7A | 5 | L1010 `awaryjne. Jeden -- nie lądowanie.`; L1020 `Nie wiemy. Zaczynamy liczyć.` Informacje w większości już pokazane w 7 — spadek przez redundancję. |
| 16 | 6B | 6 | L1084 `Powiedz mi prawdę.`; L1087 `Prawie cała czerwona. Jeden zielony punkt -- Warszawa.` Osobista stawka splata się z systemową. |
| 17 | 6C | 9 | L1136 `Pani Premier. Musimy wyłączyć sieć.`; L1159 `Najdłuższa cisza w tym odcinku.`; L1219 `Zielony punkt gaśnie.` Decyzja bohaterki gasi kraj; nieodwracalne. Nie 10, bo nikt z głównych postaci nie ginie. |
| 18 | 8 | 8 | L1259 `Obraz gaśnie. Czarny ekran.`; L1264 `Czterdzieści sekund.` Głos państwa urwany; widz zostaje w czerni. |
| 19 | 9 | 7 | L1279 `Próbuje go odblokować -- nic.`; L1295 `Widz siedzi z tym sam.` Córka sama, bez łączności; skutek decyzji matki dotyka rodziny. |
| 20 | 10 | 7 | L1314 `Proszę nie być sama.`; L1333 `Ekran gaśnie w połowie słowa.` Ostatnia stacja; trzecie użycie chwytu (N-03) — bez przyrostu. |
| 21 | 12A | 6 | L1376 `Pani Premier. Mam córkę.`; L1430 `Jedź tam."` Wybór rodziny zamiast państwa; ironia: Aga kieruje Verę na farmę z dziećmi. |
| 22 | 12 | 5 | L1502 `Czy tata...`; L1507 `Nie wiem.` Exodus i niepewność o Piotra. |
| 23 | 13 | 3 | L1552 `Nie wiedziałam że masz ciotkę na farmie.`; L1568 `Warszawa znikła za zakrętem.` Droga; zagrożenie oddala się. |
| 24 | 14 | 3 | L1601 `Ciepłe przyjęcie.`; L1607 `Jedna niesie drwa. Życie trwa -- innym rytmem, ale trwa.` Bezpieczna przystań. |
| 25 | 16 | 2 | L1692 `Biogazownia odpala.`; L1716 `Mamo. Właśnie naprawiłyśmy elektrownię.` Sukces i ulga; najniższy punkt krzywej. |
| 26 | 15 | 5 | L1737 `Jedną po drugiej. Czegoś szuka. Kogoś.`; L1752 `Wiedziałam że przyjedziesz.` Sprawczyni wchodzi do domu ofiar; ironia dla widza. |
| 27 | 17 | 6 | L1864 `Nie odwraca głowy. Tylko zamyka oczy na chwilę.`; L1890 `Wiesz co robisz?`; L1935 `Nie mogę powiedzieć dokąd.` Wina Very, wyjazd Agi z matką; stawka emocjonalna, bez zagrożenia fizycznego. |
| 28 | 18 | 5 | L1972 `Zapieczętowana koperta -- list, którego Marta jeszcze nie otworzyła.`; L1985 `On żyje?` Tajemnica i niepewność; pytanie powtórzone (E02-41). |
| 29 | 19 | 9 | L2039 `się pali. Zofia osuwa się na kolana, potem na ziemię. Nie rusza się.`; L2042 `za płotem, zbliżają się chwiejne światła. Coraz bliżej.` Bezpośrednie zagrożenie dla wszystkich głównych postaci (śpią w domu); wynik otwarty. |

Kształt krzywej (kolejność pliku): 8, 4, 5, 4, 6, 6, 4, 4, 6, 6, 5, 5, 6, 7, 5, 6, 9, 8, 7, 7, 6, 5, 3, 3, 2, 5, 6, 5, 9. Suma ocen: 162; średnia: 162 / 29 ≈ 5,6.

### e3. Miejsca spadku napięcia

| Miejsce (start) | Spadek | Przyczyna (cytat) | PROPOZYCJA |
|---|---|---|---|
| Prolog → 1 (2:00) | 8 → 4 | zamierzona „cisza po” (L16 `Reszta odcinka zaczyna się w ciszy po.`) | zostawić — spadek celowy |
| 1A → 2 (7:30) | 5 → 4 | powtórzenie skali; L340 `Marta patrzy na mapę. Trzy czerwone punkty.` | skrócić 2 (d4), dodać jednostkę „Dziewięć dni” |
| 3B → 4 → 4A (16:30–21:00) | 6 → 4 → 4 | po ironii 3B dwie sceny PSE; zegar się wydłuża L542 | E02-26 (krótszy zegar), N-01 (beat Agi) |
| 7 → 7A (36:30) | 7 → 5 | 7A raportuje to, co widz zobaczył w 7 (L953, L995, L1009) | skrót 7A do nowych informacji (ofiary, decyzja o milczeniu L1025) |
| 12A → 13 → 14 → 16 (53:00–63:00) | 6 → 5 → 3 → 3 → 2 | 10 min bez zagrożenia; L1716 sukces | zasiać zagrożenie z zewnątrz: w 14 lub 16 ślad obcych (np. Zofia: kradną z pól), strzelba (E02-48) |
| 17 → 18 (68:30) | 6 → 5 | powtórzone pytanie L1985 po L1502 | e8: inne pytanie w 18 (o list) |

### e4. Sekwencje infrastrukturalne vs wydarzenia osobiste

- **Infrastruktura daje skalę, nie stawkę.** Średnia ocen bloków infrastrukturalnych (1A 5, 2 4, 4A 4, 5 6, 6 5, 6A 6, 7A 5, 6C 9, 8 8, 10 7): 59 / 10 = **5,9**. Bez 6C i 8 (kulminacji): 42 / 8 = **5,25**. Średnia bloków osobistych (3 6, 3B 6, 4 4, 5B 5, 6B 6, 9 7, 12A 6, 12 5, 13 3, 14 3, 16 2, 15 5, 17 6, 18 5, 19 9): 78 / 15 = **5,2**. Montaże i prolog (PROLOG 8, 1 4, 5A 6, 7 7): 25 / 4 = **6,25**. Kontrola: 59 + 78 + 25 = 162 = suma krzywej z e2; średnia całości 162 / 29 ≈ **5,6**.
- **Najmocniejsze bloki infrastrukturalne to te, w których system dotyka osoby:** 6C (Marta decyduje sama, L1157 `Wolę wyłączyć ją teraz.`), 6B (mapa + córka), 9 (skutek dla Karoliny). Najsłabsze to te, które tylko raportują (2, 4A, 7A).
- **Długie sekwencje:** PSE 24:00–34:00 (4 bloki, średnia 5,5) i narady 1A/7A. Obie mają tę samą konstrukcję „liczba → kolor mapy → telefon”; słowo „mapa” w odmianach pada w 23 liniach pliku.
- **Wydarzenia osobiste są skupione w drugiej części** (50:00–73:30), gdzie zagrożenia z zewnątrz brak do sc. 19 — stąd dolina 13–16.
- **Wniosek (PROPOZYCJA):** przeplatać — w części systemowej jeden osobisty beat Agi/Very (N-01), w części farmy jeden zewnętrzny sygnał zagrożenia przed sc. 19.

### e5. Mapa informacji w kluczowych punktach

| Punkt (blok, linia) | Co wie widz | Co wiedzą postacie | Skutek dla napięcia |
|---|---|---|---|
| Prolog (L79–L84) | Statek z E01 zniszczył terminal; zginęła ostatnia obsada | Rząd potwierdza dopiero w T+10 (L953) | Widz wyprzedza państwo o dzień — dobra ironia |
| Sc. 1 → 1A (L154, L270) | Komunikat już padł; „dzień 8” | Rząd w T+3 dopiero decyduje | Odwrócona wiedza (zła): decyzja bez stawki (E02-03) |
| Sc. 3 (L406–L410) | Z E01: Vera stworzyła wirusa i jest matką Agi (na podstawie fragmentu raportu E01) | Aga widzi „V. Strand” i (wg tekstu) nie wie, kto to | Ironia działa, ale kosztem wiarygodności Agi (E02-01) |
| Sc. 3B (L454–L473) | Aga wzywa matkę; Vera rusza | Aga nie wie, co zrobiła matka | Rdzeń ironii z noty (L26–L28) — działa |
| Sc. 5B, 6B (L717, L1090) | Sieć pada; Marta kłamie | Karolina nie wie, ale czuje (L723, L1093) | Dobra asymetria; płaci się w sc. 9 |
| Sc. 7 koniec (L933) | Sieć już zgasła, Marta sama | — (dopiero w 6C) | **Zbyt wczesne ujawnienie** wyniku 6C |
| Sc. 12A (L1413, L1429) | Aga kieruje sprawczynię na farmę, do własnych dzieci | Marta i Zofia nie wiedzą, kim jest Vera | Mocna ironia, niewykorzystana do sc. 15 |
| Sc. 15 (L1746–L1747) | Wie wszystko | Farma wie, że to matka Agi; nie wie o winie | „Nieznajoma” z noty nie istnieje (E02-02) |
| Sc. 17 (L1883–L1890) | Aga zabiera twórczynię wirusa do analizy wirusa | Aga nie wie; Vera wie | Szczyt ironii emocjonalnej; L1866 źle opisuje wiedzę widza |
| Sc. 18 (L1971–L1972) | Dokumenty misji, list | Karolina nie wie, czy ojciec żyje; Marta „Wiesz jak jest” | Tajemnica Piotra dla widza E02 (N-06) |
| Sc. 19 (L2023–L2039) | Wg tekstu: kobiety; na ekranie: sylwetki | Zofia nie wie, kto; reszta śpi | Cliffhanger; ryzyko fałszywego tropu (M10) |

### e6. Zbyt wczesne ujawnienia

1. **Montaż 7, L931–L933** — pokazuje wygasłą konsolę i odejście Beaty i Ani przed 6C. Najkosztowniejsze w odcinku: odbiera 6C pytanie „czy zdąży / czy zgaśnie” (E02-08).
2. **Montaż 1, L120–L128 i L154** — komunikat i „dzień 8” przed naradą T+3 (E02-03).
3. **Sc. 3B, L454** i **12A, L1413** — relacja matka–córka ujawniona wcześniej, niż zakłada nota (L29–L30). Przy modelu D-01 wariant 1 to nie błąd, tylko świadoma ironia; przy modelu „widz nie wie” — za wcześnie.
4. **Sc. 4A, L574–L576** — zapowiedź „prośby” bez spłaty (N-02): nie za wcześnie, tylko za długo bez odpowiedzi.

### e7. Kandydaci na cliffhangery, otwarcie i zakończenie

**Kandydaci na cliffhangery (wewnętrzne i końcowy):**
- **Sc. 19 (L2039–L2042)** — główny i najmocniejszy hak odcinka; nowy typ zagrożenia (przemoc ludzi, nie systemu).
- **Sc. 6C koniec (L1238)** + **sc. 8 (L1259–L1264)** — naturalny koniec aktu 2 (czerń 40 s); dobre miejsce na przerwę, jeśli odcinek będzie dzielony.
- **Sc. 3 koniec (L438–L440)** — po poprawce E02-01: notatka „Mama.” jako hak środka pierwszego aktu.
- **Sc. 3B koniec (L473)** — Vera pakuje się: hak, który odcinek „zapomina” na 46,5 min (N-01, N-05).
- **Sc. 17, telefon (L1872–L1875)** — w wariancie E02-22/2 („Oddzwonię rano”) zostaje otwarte pytanie na E03.
- **Sc. 18, list (L1972)** — mały hak przenoszony do E03 (D-11).

**Otwarcie.** Prolog (8/10) to znacznie mocniejszy start niż w E01 (na podstawie raportu ZERO-ANALIZA-001: E01 zaczyna od 1/10; E03 nie jest analizowane). Problem: po prologu przez 8 minut (1, 1A, 2) nie ma żadnej z głównych postaci w scenie osobistej — Marta jest tylko głosem z tabletu (L185 `Na stole tablet. Na ekranie -- MARTA, z centrum PSE.`). Pierwsza osobista stawka pojawia się w 10:00 (sc. 3). PROPOZYCJA: beat Karoliny z montażu 1 (L145–L148) rozwinąć do kilku sekund z twarzą Marty — widz od razu ma stawkę rodzinną.

**Zakończenie.** Sekwencja 18 → plansza „E W A” (L2005) → „Czerń trzyma się dłużej” (L2009) → sc. 19 → `Czarny ekran.` (L2044). Widz dostaje fałszywe zakończenie (plansza i długa czerń), po którym przychodzi hak. To może działać jak „tag” po tytule (zaskoczenie), ale osłabia sc. 18 i ryzykuje, że część widzów wyłączy przed sc. 19. PROPOZYCJA (D-14): plansza „E W A” dopiero po sc. 19; sc. 18 kończy się dogasającym ogniem (L2001 `Ogień gaśnie.`), cięcie wprost do lamp na drodze (rym ogień → lampy naftowe).

### e8. PROPOZYCJE nowego brzmienia kwestii (ECHO-003, G2; tylko w raporcie)

Wszystkie poniższe to PROPOZYCJE do decyzji właściciela; nie trafiają do `scenariusze/`.

| Miejsce | Obecnie (cytat) | PROPOZYCJA nowego brzmienia | Cel |
|---|---|---|---|
| sc. 3, L410 | L410 `"V. Strand. Kim jest?"` | PROPOZYCJA: *V. Strand. Mama. Tata to opublikował?* | E02-01 |
| sc. 3, L400 | L400 `Data: osiemnaście lat temu.` | PROPOZYCJA: *Data: dwanaście lat temu.* | E02-14 |
| sc. 3, po L433 | L433 `Już jest pilne. Ale rozumiemy.` | PROPOZYCJA (dopisek Głosu): *Prześlemy pani telefon satelitarny. Proszę go nie wyłączać.* | E02-21 |
| sc. 2, L345 | L345 `Dziewięć.` | PROPOZYCJA: *Dziewięć dni.* | E02-26 |
| sc. 4A, L542 | L542 `Mamy jeszcze osiem, może dziesięć dni` | PROPOZYCJA: *Mamy jeszcze pięć, może sześć dni* | E02-26 |
| sc. 6A, L834 | L834 `Szukamy. Inżynier sieci bez mężczyzn...` | PROPOZYCJA: *Szukamy. Inżynierki sieci...* | E02-32 |
| sc. 1, L116 | L116 `Ogłaszam stan wyjątkowy na terenie całego kraju.` | PROPOZYCJA: *Stan wyjątkowy pozostaje w mocy.* | E02-18 |
| sc. 12, L1496 | L1496 `Przez te dni nie odebrałaś.` | PROPOZYCJA: *Przez te dni nie odbierałaś, kiedy ja dzwoniłam.* | E02-40 |
| sc. 13, L1563 | L1563 `Nie wiem. Napisałam do niej.` | PROPOZYCJA: *Nie wiem. Dzwoniłam do niej.* | N-08 |
| sc. 15, L1739 | L1739 `Nie ma jej tu jeszcze.` | PROPOZYCJA: *Nie widzi jej.* | E02-45 |
| sc. 15, po L1787 | L1787 `Dziewczynki są w środku. Śpią już.` | PROPOZYCJA (Aga): *Bożena przywiozła je wczoraj. Wróciła do swoich.* | E02-24 |
| sc. 15, po L1762 | L1762 `Chciałam zostać kucharką.` | PROPOZYCJA (Vera, na pytanie Zofii o drogę): *Przez Szwecję. Samochodem, potem pieszo.* | N-05 |
| sc. 16, L1669 | L1669 `Ty. Jesteś informatykiem -- poradzisz sobie ze starym złomem.` | PROPOZYCJA: *Ty. Jesteś informatyczką -- poradzisz sobie ze starym złomem.* | E02-54 |
| sc. 16, L1708 | L1708 `To musimy jeszcze zrobić jedno połączenie do transformatora w gazowni.` | PROPOZYCJA: *Jutro przepniemy go na rozdzielnicę domu, z pominięciem spalonego transformatora.* | E02-33 |
| sc. 17, L1873–L1875 | L1875 `Jutro rano.` | PROPOZYCJA: *Tak. / Rozumiem. / Oddzwonię rano.* | E02-22 |
| sc. 17, po L1833 | L1833 `Ogień strzela iskrą.` | PROPOZYCJA (Zofia, po Basi): *Mój Stach polował. Zostawił mi psa i strzelbę. Pies zdechł.* | E02-48, napięcie przed 19 |
| sc. 17, L1866 | L1866 `Widz nie rozumie jeszcze dlaczego.` | PROPOZYCJA (didaskalia): *Aga nie rozumie. Widz — tak.* | E02-02 |
| sc. 18, L1985 | L1985 `On żyje?` | PROPOZYCJA: *Otworzysz kiedyś ten list?* — Marta: *Kiedy będę musiała.* | E02-41, E02-37 |
| sc. 12A, po L1449 | L1449 `Jedenaście dni.` | PROPOZYCJA (didaskalia): *Wraca do szafy przy konsoli. Żółta teczka. Do plecaka.* | E02-05 |
| sc. 12A, po L1371 | L1371 `Pani wiedza jest niezbędna.` | PROPOZYCJA (Wolska): *To jest ta prośba, o której mówiłam.* | N-02 |
| obsada, L45 | L45 `Widz jeszcze tego nie wie.` | PROPOZYCJA: *Widz wie, kim jest i co zrobiła. Aga nie wie.* | E02-02 |

---

## (f) Kolejność rekomendowanych poprawek (zależności) i decyzje kanoniczne

### f1. Kolejność (PROPOZYCJA)

1. **Decyzje bez pisania (blokujące):** D-01 (model wiedzy o Verze), D-02 (co Aga wie w sc. 3), D-03 (Wolska), D-06 (zasada „bez mężczyzn”), D-07 (metraż), D-08 (struktura montaży). Od D-01 i D-02 zależą sc. 3, 15, 17 i nota; od D-08 — numeracja i metraż.
2. **Sc. 3 jedną poprawką:** E02-01 + E02-38 + E02-14 (+ E02-21 wariant 1, telefon). Zależność: D-02, D-04.
3. **Nota, obsada, tabela — model wiedzy:** E02-02, E02-36, E02-35, E02-52 (po kroku 1–2).
4. **Struktura i chronologia:** E02-03 (montaż 1 i komunikat) → E02-06 (3B) → E02-07 (5/6/5B) → E02-09 (6A) → E02-08 (podział montażu 7) → E02-10 (sc. 8 na T+11) → N-04 (pobyt Marty w PSE). Dopiero potem **E02-11** (numeracja, D-15) i **E02-12/E02-13** (metraż, nowa tabela; sekcja d4 jako punkt wyjścia).
5. **Ciągłość wątków osobistych:** N-01 (beat Agi T+8), N-02 (spłata zapowiedzi), N-05 (droga Very). Po kroku 4, bo zależą od miejsca w nowej kolejności.
6. **Rekwizyty i łączność:** E02-05 (teczka z PSE), E02-21 (telefon Agi, SMS), E02-24 (Bożena), E02-37 (list, D-11).
7. **Styk z E01/E03 (osobne tematy dla E01/E03):** E02-04 (prolog, D-05), E02-22 (wezwanie Agi, D-10), E02-23 (pozycje postaci), E02-48 (strzelba, D-09), E02-15 i E02-17 (nazwy w E03).
8. **Wiarygodność branżowa (D-16):** E02-25, 26, 29, 30, 31, 32, 33, E02-44 — jedna konsultacja z inżynierem KSE; do tego czasu wszystkie oceny branżowe pozostają NIEPOTWIERDZONE.
9. **Nazwy i tytuły:** E02-16 (D-13), E02-17 (D-12), E02-18, E02-19 (D-09), E02-20, N-07, N-09, E02-53.
10. **Zasada „bez mężczyzn” w didaskaliach i promptach:** M01–M14 (po D-06).
11. **Napięcie — drobne:** N-03 (sc. 10), E02-41 (sc. 12/18), E02-47 (plansza, D-14), e8.
12. **Korekta językowa (E02-54) na końcu**, potem regeneracja tabeli czasów i czytanki.

### f2. Decyzje kanoniczne wymagane od właściciela

| Kod | Decyzja | Warianty (PROPOZYCJA) | Punkty raportu |
|---|---|---|---|
| D-01 | Co widz wie o Verze w E02 | A: widz wie (matka i sprawczyni), Aga nie — rek.; B: widz ma nie wiedzieć (wymaga zmian E01 i E02 sc. 3B, 12A, 15) | E02-02 |
| D-02 | Czy Aga w sc. 3 rozpoznaje matkę i ojca | A: rozpoznaje oboje — rek.; B: tylko matkę; C: przypis anonimowy | E02-01, E02-38 |
| D-03 | Imię i wiek Wolskiej | A: Katarzyna ~58 — rek.; B: Anna 51 (+ zmiana gen. Sowy) | E02-15 |
| D-04 | Data publikacji Dąbrowskiego | A: ok. 12 lat — rek.; B: zmiana wieku Very w E01 | E02-14 |
| D-05 | Prolog: T+8 czy T+9; dryf czy kurs | A: T+9 + zdanie o zgubionym kursie — rek.; B: T+8 kursem; C: zmiana E01 | E02-04 |
| D-06 | Zasada „bez mężczyzn” — zakres i wyjątki | A: żaden żywy mężczyzna w kadrze i dźwięku; wyjątki: zmarli z E01, zdjęcia Pawła i Piotra — rek. | M01–M14 |
| D-07 | Docelowy metraż E02 | 65 (L3) / ok. 66,5 (d4) / 67 (handoff) | E02-12 |
| D-08 | Struktura montaży 1 i 7 | A: montaż 1 do T+2 + komunikat po 1A; montaż 7 podzielony — rek.; B: tylko usunięcie duplikatu | E02-03, E02-08 |
| D-09 | Zofia: nazwisko, mąż, los | nazwisko inne niż Kowalska; mąż (wuj) z bronią zasiany w E02 tak/nie; los po napadzie (handoff B10) | E02-19, E02-48 |
| D-10 | Kiedy Aga przyjmuje wezwanie i skąd ma telefon | A: w E03, w E02 „Oddzwonię rano” — rek.; B: w E02, E03 jako drugi telefon | E02-21, E02-22 |
| D-11 | Teczka i list | teczka z PSE w 12A — rek.; list: domknąć w E03 czy usunąć | E02-05, E02-37 |
| D-12 | Tytuł Wolskiej | „p.o. premiera” od T+2 — rek.; „Pani Wicepremier” wszędzie | E02-17 |
| D-13 | Trzecia kobieta w PSE | Ela z E01 — rek.; Ania + wyjaśnienie | E02-16 |
| D-14 | Plansza „E W A” | po sc. 19 — rek.; przed sc. 19 jako tag (obecnie) | E02-47, e7 |
| D-15 | Numeracja | pełna 1–28 po przebudowie — rek.; zachowawcza z kolumną | E02-11 |
| D-16 | Konsultacja branżowa KSE | tak — rek.; licencja dramatyczna | E02-25, 26, 29–33, 44 |
| D-17 | Wątek Piotra w E02 | A: tylko rekwizyty (obecnie); B: jedno ujęcie z naszywką misji | N-06 |

Decyzje D-01 … D-17 nie zostały podjęte; raport niczego nie rozstrzyga (G3).
