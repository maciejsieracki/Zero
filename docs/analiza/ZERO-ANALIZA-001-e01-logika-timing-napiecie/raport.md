# ZERO-ANALIZA-001 — E01 ADAM: logika, timing, budowanie napięcia

Data: 2026-11-27. Rola: Operator, runda 1 z 3. Tryb: tylko odczyt scenariusza; żaden plik w `scenariusze/` nie został zmieniony.

**Źródło rozstrzygające (rząd 1):** `scenariusze/ZERO_mini_serial_E01_ADAM_rev.md`, 1263 linie, przeczytane w całości (L1–L1263). SHA-256 przed analizą: `b0264c950cbafe7181234554136f6cb65a826c12c88a96730917f9c0825f4340`.

**Materiał wejściowy (rząd 4, weryfikowany, nie przepisywany):** `docs/rozbieznosci/E01_audyt.md` (dalej: audyt), `docs/przeglad-2026-11-27/E01_scenariusz.md` (dalej: notatki), `docs/przeglad-2026-11-27/E01_beaty_i_rozpiska.md` (dalej: beaty), `docs/przeglad-2026-11-27/decyzje_i_konsultacje.md` (dalej: decyzje), handoff `ZERO_HANDOFF_2026-10-11.md` sekcje 2–5 (dalej: handoff).

**Konwencja cytatów.** `L123 \`tekst\`` = dosłowny fragment jednej linii pliku E01 (skopiowany z wyniku Read/grep, bez wcięcia z lewej). `H82 \`tekst\`` = linia handoffu. `E02:L410` / `E03:L833` = linia sąsiedniego odcinka; te odwołania pochodzą z punktowego `sed -n` i są oznaczone **na podstawie fragmentu** (E02 i E03 nie były czytane w całości; E03 nie jest przedmiotem analizy).

**Konwencja propozycji.** Każdy wariant naprawy, rekomendacja i nowe brzmienie kwestii to **PROPOZYCJA** do decyzji właściciela (ECHO-003, G2, G3). Nic z tego nie trafia do plików scenariuszy.

**Oznaczenie NIEPOTWIERDZONE.** Każde twierdzenie naukowe, techniczne, prawne lub branżowe, którego nie da się sprawdzić w tekście scenariusza, jest oznaczone NIEPOTWIERDZONE (nie było weryfikowane w źródle zewnętrznym w tym temacie).

Skala wag: **KRYTYCZNA** = łamie logikę odcinka albo kanon zapisany w samym pliku; **WYSOKA** = widoczna dla widza sprzeczność lub istotna utrata napięcia; **ŚREDNIA** = sprzeczność drugoplanowa, wiarygodność, ciągłość; **NISKA** = kosmetyka, dokumentacja, język.

---

## (a) Podsumowanie

### Stan odcinka w trzech wymiarach

- **LOGIKA:** szkielet jest spójny (wiek Very 24 → 35 → 49 → 52 → 64 i Agi 5 → 19 → 34 zgadza się z napisami P1–P4), ale nota reżyserska i obsada obiecują co innego niż sceny: reveal Agi (L16, L41), zakończenie (L26–L28), język Very (L52, L56). Dwie sprzeczności są twarde i krzyżują się z innymi odcinkami: oś milczenia Ares IV (sc. 6 vs sc. 14) i wiedza widza o tym, że Aga jest córką Very. Do tego trzy cofnięcia osi T w kolejności scen i odwrócona krzywa liczb śmiertelności.
- **TIMING:** suma etykiet CZAS = **60,5 min** przy nagłówku „ok. 60 minut” (L3). Plik **nie zawiera tabeli czasów**. Teraźniejszość 40,5 min (66,9%), przeszłość 16,5 min (27,3%), wstawki 3,5 min (5,8%). Pierwsze zagrożenie pojawia się dopiero w 9. minucie (sc. 3). Druga połowa (od 32:15) jest prawie bez dialogu.
- **NAPIĘCIE:** krzywa rośnie od 1 do 10 z dwiema głębokimi dziurami (P3 po wstawce T-7 i P4 po wstawce T-5) i długą doliną między 11:30 a 21:15. Bloki przeszłości lokalnie obniżają napięcie, ale „ładują” ironię dramatyczną: widz wie, że Vera stworzyła wirusa (sc. 3) i że jest matką Agi (P2/P3/sc. 8), więc sc. 7, 12, 13 i 14 grają podwójnie. Najmocniejszy hak na koniec to sc. 15 (statek na gazoport), osłabiony fałszywym zakończeniem w montażu (L1211).

### 10 najważniejszych punktów

1. **E01-01 (KRYTYCZNA, POTWIERDZONE):** nota mówi, że widz nie wie o Adze (L16, L41), a P2, P3 i sc. 8 mu to mówią (L514, L640, L824).
2. **E01-02 (KRYTYCZNA, POTWIERDZONE):** Ares IV milczy od T-11 (L533 + L569), a na T0 pada „SIGNAL INTERRUPTED” (L1188).
3. **E01-06 (WYSOKA):** „100%” pada już na T-7/T-6 (L594, L932), więc ogłoszenie WHO na T0 (L1196) nie jest kulminacją informacji.
4. **E01-08 (WYSOKA, ZAWĘŻONE):** trzy cofnięcia osi T (T-9 → T-10, T-7 → T-8, T-5 → T-6). Tylko T-14 ma jawny napis ekranowy (L289), ale dwa cofnięcia są wyczuwalne w treści.
5. **E01-07 (WYSOKA):** SMS Michała z 09:47 (L853–L854) i „Po wczoraj: nic.” (L986) w tym samym dniu T-5.
6. **N-05 (WYSOKA, nowe):** 9 minut bez zagrożenia na otwarcie (sc. 1 + sc. 2 + P1), P1 nie ma wyzwalacza.
7. **E01-11 (WYSOKA):** imię Piotra nie pada w żadnej scenie (grep: tylko L27, L34, L35). Widz nie wie, że mąż Marty jest na Ares IV.
8. **E01-04 (WYSOKA):** cliffhanger z noty (L26–L28) nie istnieje w montażu, a odcinek kończy się sc. 15 (T+8), nie Zero Day.
9. **E01-03 (WYSOKA, ZAWĘŻONE z KRYTYCZNEJ):** P2 gra niespełnione napięcie (L480–L481) między ludźmi, którzy chwilę później mają wspólny dom i dziecko (L497–L514).
10. **N-03 / N-06 (ŚREDNIA, nowe):** fałszywe zakończenie w montażu Zero Day (L1211 `Czarny ekran.` przed ujęciem Agi) i najgłębszy spadek napięcia w odcinku: 5-minutowy P3 zaraz po wstawce T-7.

### Decyzje kanoniczne wymagane od właściciela (skrót; pełna lista w sekcji f)

D-01 reveal Agi w E01 (tak/nie); D-02 oś milczenia Ares IV razem z E03; D-03 mechanizm uwolnienia i pacjent zero; D-04 kiedy Vera i Marek zostali parą; D-05 dzień śmierci Pawła (T-1 czy T0); D-06 czy śmierć Dąbrowskiego ma ujęcie; D-07 obecność Piotra w E01; D-08 los Michała w E01; D-09 docelowy metraż; D-10 reguła językowa Very.

---

## (b) LOGIKA — zweryfikowana, zdeduplikowana lista rozbieżności

Numeracja E01-xx zachowana z audytu. Nowe punkty: N-xx. Przy każdym punkcie jest status weryfikacji audytu (sekcja c to zbiorcza tabela).

Deduplikacja: E01-14 = handoff A5; E01-10 = handoff A6; wpisy E01-45 dla L164–L165, L1079, L1194 są zdublowane z E01-10, E01-14, E01-33 i są opisane tylko tam.

### KRYTYCZNE

#### E01-01 — Widz dowiaduje się w E01, że Aga jest córką Very (wbrew nocie i obsadzie)
- **Waga:** KRYTYCZNA. **Status audytu:** POTWIERDZONE, z doprecyzowaniem: w P2 związek wynika tylko z imienia i języka, pewność daje sc. 8.
- **Lokalizacja i cytaty:**
  - nota: L16 `Widz nie wie jeszcze, że Aga jest córką Very.`
  - obsada: L41 `Widz tego jeszcze nie wie.`
  - P2: L511 `Z pokoju: AGA (mała, może 4-5 lat) wybiega do kuchni.`; L514 `Mamma! Pappa powiedział, że możemy jutro do parku!`
  - P3: L636 `Vera siedzi przy stole. Aga (19 lat) właśnie wróciła --`; L640 `Mamo, jest coś do jedzenia? Byłam na wykładzie do ósmej.`; L750 `Wrócisz?`
  - sc. 8: L824 `Kontakt: "Aga". Zdjęcie profilowe -- Aga z dwiema małymi`; L825 `dziewczynkami, wszyscy w parku, słońce.`
  - sc. 12: L1079 `Dziewczynki są u twojej mamy sąsiadki?`
- **Na czym polega sprzeczność:** nota i obsada deklarują tajemnicę. Sceny robią co innego. P2 i P3 pokazują Agę mówiącą do Very „Mamma”/„Mamo”. Sc. 8 pokazuje w telefonie Very kontakt „Aga” ze zdjęciem kobiety z dwiema dziewczynkami, a obsada mówi o Adze `Żona Pawła. Matka dwóch córek. Córka Very.` (L40). Najpóźniej w sc. 8 (32. minuta) widz ma pewność. Handoff zakłada, że widz „długo tego nie wie”: H69 `**Vera Strand** — norweska wirusolog, **64 l.**, twórczyni wirusa, **matka Agi** (widz długo`.
- **Warianty (PROPOZYCJE):**
  1. Przyjąć reveal w E01 jako ironię dramatyczną (widz wie, Aga nie wie, co zrobiła matka). Poprawić notę L16 i obsadę L41. W E02 zmienić scenę z „V. Strand. Kim jest?” (E02:L410, na podstawie fragmentu) na rozpoznanie.
  2. Zachować tajemnicę do E02/E03: w P2 i P3 nie nazywać dziecka (np. „DZIEWCZYNKA”), usunąć „Mamma”/„Mamo”, w sc. 8 kontakt bez imienia i bez twarzy dorosłej.
  3. Hybryda: P2 i P3 bez zmian (widz podejrzewa), w sc. 8 zamiast zdjęcia Agi z córkami samo „A.”. Pewność dopiero w E02.
- **Rekomendacja (PROPOZYCJA):** wariant 1. Analiza napięcia (sekcja e) pokazuje, że cała wartość bloków P2–P3 i scen 7, 12, 13, 14 opiera się na tej wiedzy widza. Wariant 2 zabiera blokom przeszłości funkcję, a teraźniejszości ironię.
- **Skutki:** nota L16 i obsada L41; E02 sc. 3 (na podstawie fragmentu: E02:L410 `"V. Strand. Kim jest?"`); handoff §2; beaty BlokP2, BlokP3 i Sceny 8 przy wariancie 2/3; prompt zdjęcia profilowego; PDF czytanki E01. Od tej decyzji zależą E01-32 i E01-14.

#### E01-02 — Milczenie Ares IV: od T-11 w sc. 6, a na T0 „SIGNAL INTERRUPTED”
- **Waga:** KRYTYCZNA. **Status audytu:** POTWIERDZONE w części E01. Część o E03 (Ford: „trzy tygodnie”) potwierdzona tylko na podstawie fragmentu.
- **Lokalizacja i cytaty:**
  - sc. 6: L533 `T MINUS 9 DNI`; L569 `Ares IV milczy od czterdziestu ośmiu godzin.`; L570 `ESA nie ma kontaktu.`; L575 `Pewnie zakłócenia. Zdarzało się.`
  - sc. 14: L1188 `Miga ekran: "ARES IV -- SIGNAL INTERRUPTED."`
  - E03:L833 `Milczeliśmy przez trzy tygodnie, bo potrzebowałam` (na podstawie fragmentu)
- **Na czym polega sprzeczność:** 48 godzin przed T-9 to T-11. Jeśli od T-11 nie ma kontaktu, to na T0 nie ma czego „przerywać”. Scenariusz nie pokazuje odzyskania łączności między T-9 a T0. Między odcinkami: od T-11 do sceny ujawnienia w E03 mija znacznie więcej niż „trzy tygodnie”. Długości tego okresu nie liczę, bo nagłówków E03 nie czytałem w całości.
- **Warianty (PROPOZYCJE):**
  1. Przenieść telefon z sc. 6 na T-1 albo T0 i połączyć go z ujęciem ESA w Zero Day. Milczenie zaczyna się wtedy w T0.
  2. Zostawić T-11 jako chwilową awarię („zakłócenia”, L575). W sc. 11 (T-4) dodać jedną linię, że łączność wróciła, a na T0 zostawić „SIGNAL INTERRUPTED” jako właściwe zerwanie. Kwestię w E03 uzgodnić z osią.
  3. Zmienić ekran w sc. 14 na „ARES IV -- NO CONTACT: DAY 11” (L1188). Milczenie trwa ciągle od T-11, a E03 tłumaczy je jako „najpierw awaria, potem nasza decyzja”.
- **Rekomendacja (PROPOZYCJA):** wariant 2. Zostawia niepokój Marty od 21. minuty (jedyny wątek Piotra w odcinku) i wymaga jednej linii w E01. Wariant 1 przesuwa jedyne zdarzenie Ares IV na sam koniec i osłabia wątek Marty w środku odcinka.
- **Skutki:** sc. 6, sc. 11 (przy wariancie 2), sc. 14; E03 sc. 7 (na podstawie fragmentu); beaty Sceny 6 i Zero Day; rozpiska; handoff §2 („pierwszy kontakt z Marsem”). Zależność: E01-11 (bez imienia Piotra cały wątek jest dla widza nieczytelny).

### WYSOKIE

#### E01-03 — P2: niespełnione napięcie między ludźmi, którzy są już parą z dzieckiem
- **Waga:** WYSOKA (audyt: KRYTYCZNA). **Status audytu:** ZAWĘŻONE.
- **Lokalizacja i cytaty:** L431 `Napis: "WARSZAWA. OK. 11 LAT PO PRZYJEŹDZIE."`; L435 `On pisze, ona poprawia, on kiwa głową. Para, która przez kilkanaście`; L457 `Vera siada. Marek siada obok. Blisko -- ale to jest normalne,`; L480 `Coś jest w tej ciszy -- nie po raz pierwszy, widz to czuje.`; L481 `Ale ani jedno, ani drugie nie robi nic.`; L491 `Wychodzi. On patrzy za nią przez chwilę.`; L495 `Cięcie. Mieszkanie. Inny dzień.`; L498 `Przy ścianie -- krzesełko dziecięce. Puste -- dziecko gdzieś`; L514 `Mamma! Pappa powiedział, że możemy jutro do parku!`
- **Na czym polega sprzeczność:** pierwsza część P2 gra relację przed związkiem (bliskość, nic się nie dzieje, ona wychodzi, on patrzy za nią). Druga część, opisana jako „inny dzień”, pokazuje wspólny dom i pięcioletnią córkę, czyli związek trwający co najmniej kilka lat. **Dlaczego zawężam:** tekst nigdzie nie mówi, że nie są jeszcze parą. Słowo „Para” (L435) i „to jest normalne” (L457) da się czytać jako długoletnie małżeństwo, a „nie po raz pierwszy” (L480) jako powracającą iskrę. Sprzeczność dotyczy więc inscenizacji i odbioru, a nie twardej osi czasu. Dlatego waga WYSOKA, nie KRYTYCZNA. Zostaje problem widza: nie wie, kiedy zostali parą, a scena przy tablicy sugeruje, że jeszcze nie są.
- **Warianty (PROPOZYCJE):**
  1. Dodać napis przed kuchnią („Kilka lat później.” albo bez napisu, z inną charakteryzacją). Tablicę zostawić „ok. 5 lat po przyjeździe” (Vera ok. 29, przed narodzinami Agi), a napis L431 przenieść na kuchnię.
  2. Zmienić didaskalia L478–L491 tak, żeby grały bliskość pary: on zostaje przy tablicy, ona wychodzi do domu, bo „ktoś musi odebrać małą”. To łączy obie połowy.
  3. Przenieść scenę przy tablicy na koniec P1 (ten sam blok, „kilka lat później”), a w P2 zostawić tylko kuchnię.
- **Rekomendacja (PROPOZYCJA):** wariant 2, bo nie dodaje napisu ani nowego wieku Very do charakteryzacji. Jeśli właściciel chce zachować „pierwszy raz”, to wariant 1.
- **Skutki:** napis L431; beaty BlokP2; charakteryzacja Very (przy wariancie 1 dodatkowy wizerunek); rozpiska; PDF. Decyzja kanoniczna D-04.

#### E01-04 — Cliffhanger z noty nie istnieje w montażu; odcinek nie kończy się Zero Day
- **Waga:** WYSOKA. **Status audytu:** POTWIERDZONE.
- **Lokalizacja i cytaty:** L26 `Odcinek kończy się Zero Day. Cliffhanger: Marta z żółtą`; L27 `teczką i zdjęciem Piotra. Aga przy zwłokach Pawła.`; L28 `Vera w hotelu patrzy na mapę świata.`; L1200 `Powrót do Marty. Siedzi sama przy głównej konsoli.`; L1175 `Szpital. Aga biegnie korytarzem.`; L1214 `Na ekranie dwie sekwencje genetyczne, ułożone obok siebie.`; L1228 `T PLUS 8`; L1263 `KONIEC ODCINKA 1`
- **Na czym polega sprzeczność:** w montażu Marta jest przy konsoli bez teczki. Zdjęcia Piotra nie ma w żadnej scenie: grep „Piotr” daje tylko L27, L34 i L35. Aga biegnie i porównuje sekwencje, a ciała Pawła nie ma. Paweł umarł na T-1 (L1108, L1119). Z noty spełniony jest tylko obraz Very przy mapie (L1183). Odcinek kończy się sc. 15 (T+8). Według audytu beat z teczką jest w E02 (E02:L1972 `Zapieczętowana koperta -- list, którego Marta jeszcze nie otworzyła.`, na podstawie fragmentu).
- **Warianty (PROPOZYCJE):**
  1. Poprawić notę do faktycznego montażu (Aga w laboratorium, sc. 15 jako ostatni obraz).
  2. Dodać do montażu jedno mikroujęcie: Marta otwiera szafę, patrzy na teczkę i nie otwiera jej. To spłaca zasiew z L158 i L582–L583 i nie zużywa beatu z E02.
  3. Dodać pełne otwarcie teczki ze zdjęciem Piotra. Wtedy w E02 trzeba usunąć powtórzenie.
- **Rekomendacja (PROPOZYCJA):** 1 + 2.
- **Skutki:** nota L26–L28; montaż sc. 14 (+1 ujęcie, ok. 5 s); beaty Zero Day; inserty; PDF; E02 sc. 18 tylko przy wariancie 3 (na podstawie fragmentu).

#### E01-05 — P3: „Tata dzwonił… obiad w sobotę”, a tej samej nocy Marek jest w kuchni
- **Waga:** WYSOKA. **Status audytu:** POTWIERDZONE.
- **Lokalizacja i cytaty:** L654 `Tata dzwonił. Pyta, czy przyjdę w sobotę na obiad.`; L672 `Vera i Marek w kuchni. Aga śpi. Cisza między nimi`; L678 `Marek stoi przy zlewie. Nie odwraca się od razu.`; L735 `On powinien wyjść.`
- **Na czym polega sprzeczność:** zaproszenie od ojca przez telefon na sobotni obiad zakłada, że ojciec mieszka osobno. Tej samej nocy Marek jest w kuchni wspólnego mieszkania, a kilka tygodni później Aga mówi, że to „on powinien wyjść”, czyli nadal mieszkają razem.
- **Warianty (PROPOZYCJE):**
  1. PROPOZYCJA brzmienia L654: `Tata dzwonił. Że znowu wróci późno.` Podtekst kłamstwa zostaje, a kwestia pasuje do zdrady.
  2. Marek już się wyprowadził: wtedy rozmowa w kuchni (L672–L701) dzieje się przy drzwiach, kiedy przychodzi po rzeczy, a L735 trzeba zmienić.
  3. Obiad u rodziny Marka (np. `Babcia pyta, czy przyjdę w sobotę na obiad.`).
- **Rekomendacja (PROPOZYCJA):** wariant 1, jedna kwestia.
- **Skutki:** beaty BlokP3, rozpiska, PDF.

#### E01-06 — Eskalacja „100%” jest odwrócona; T0 nie dokłada informacji
- **Waga:** WYSOKA. **Status audytu:** POTWIERDZONE.
- **Lokalizacja i cytaty:** W2 (T-7): L593 `Pasek TVN: "WIRUS Y (HYV-1): ŚMIERTELNOŚĆ U MĘŻCZYZN WYSOKA -- WHO POTWIERDZA"`, L594 `Pasek TVN24: "WIRUS Y -- ŚMIERTELNOŚĆ BLISKA 100% U HOSPITALIZOWANYCH MĘŻCZYZN"`; sc. 7 (T-7): L772 `Śmiertelność wynosi już kilkadziesiąt procent wśród`; sc. 9 (T-6): L932 `Na pasku: "WIRUS Y (HYV-1): WHO POTWIERDZA -- ŚMIERTELNOŚĆ 100% U MĘŻCZYZN."`; W3 (T-5): L845 `udokumentowanych przypadkach -- jest bliska`, L846 `stuprocentowej. Wirus rozpoznaje sekwencję`; sc. 14 (T0): L1195 `Wirus Y. Klinicznie HYV-1. Śmiertelność u mężczyzn:`, L1196 `sto procent. Nie odnotowano żadnego przypadku przeżycia.`
- **Na czym polega sprzeczność:** na T-7 telewizja podaje „bliska 100%”, a lekarz na zamkniętej konferencji tego samego dnia mówi o „kilkudziesięciu procentach”. Na T-6 pasek WHO „potwierdza 100%”, na T-5 epidemiolog cofa się do „bliska”, a na T0 rzecznik ogłasza jako szok to, co pasek podał 6 dni wcześniej. Krzywa informacji idzie w górę, w dół i znowu w górę.
- **Warianty (PROPOZYCJE):**
  1. Ułożyć rosnącą krzywą zmianą samych pasków. PROPOZYCJA: L594 `Pasek TVN24: "WIRUS Y -- ŚMIERTELNOŚĆ ROŚNIE, SZPITALE W EUROPIE ALARMUJĄ"`; L932 `Na pasku: "WIRUS Y (HYV-1): WHO -- ŚMIERTELNOŚĆ U MĘŻCZYZN PONAD 90%."`. Wtedy T-5 „bliska stuprocentowej” i T0 „sto procent, brak przeżyć” rosną.
  2. Zostawić liczby, ale w T0 przenieść akcent z procentu na „żadnego przypadku przeżycia” i skalę globalną.
  3. Ujednolicić kwestię lekarza z Berlina z paskiem.
- **Rekomendacja (PROPOZYCJA):** wariant 1 (tylko paski, bez dialogów).
- **Skutki:** beaty Wstawki T-7, Sceny 9 i Zero Day; noty techniczne (paski TV); PDF. Nie dotyka E02/E03.

#### E01-07 — Michał: SMS 09:47 „Jestem w szpitalu” i „Po wczoraj: nic.” w tym samym dniu T-5
- **Waga:** WYSOKA. **Status audytu:** POTWIERDZONE.
- **Lokalizacja i cytaty:** W3 (T-5): L853 `Wiadomość od Michała, godzina 09:47:`, L854 `"Jestem w szpitalu, to pewnie nic. Przyjdź dzisiaj?"`; sc. 10 (T-5, popołudnie): L977 `T MINUS 5 DNI`, L984 `Ostatnia wiadomość od Michała: "Gorączka trochę spada.`, L985 `Nie martw się." Godzina: wczoraj, wieczór.`, L986 `Po wczoraj: nic.`
- **Na czym polega sprzeczność:** po południu T-5 „ostatnia” wiadomość jest z wczoraj, chociaż rano tego dnia przyszła wiadomość z 09:47. Do tego łuk emocjonalny jest pomieszany: „gorączka spada” (wczoraj), „jestem w szpitalu” (rano), cisza.
- **Warianty (PROPOZYCJE):**
  1. SMS z 09:47 przenieść na T-6, a „Gorączka trochę spada” ustawić na wieczór T-6. T-5 to cisza. Wymaga przestawienia W3 i sc. 9 (zob. E01-08).
  2. PROPOZYCJA brzmienia L985–L986: `Godzina: dziś, 09:47.` / `Potem: nic.`, a wiadomość „Gorączka trochę spada” przenieść do sc. 9.
  3. Przesunąć sc. 10 na T-4.
- **Rekomendacja (PROPOZYCJA):** wariant 1 razem z przestawieniem z E01-08. Daje czysty łuk „nadzieja, potem cisza”.
- **Skutki:** inserty ekranu telefonu; beaty Wstawki T-5 i Sceny 10; rozpiska; PDF.

#### E01-08 — Kolejność scen cofa się na osi T (3 miejsca)
- **Waga:** WYSOKA. **Status audytu:** ZAWĘŻONE. Jawny napis ekranowy ma tylko T-14 (L289 `Napis: T MINUS 14 DNI`). Pozostałe T są w nagłówkach, więc widz nie widzi samych liczb. Dwa z trzech cofnięć są jednak wyczuwalne w treści.
- **Lokalizacja i cytaty:** L294 `T MINUS 9 DNI` (sc. 4), potem L351 `WSTAWKA MEDIALNA -- T MINUS 10 DNI`; L767 `T MINUS 7 DNI` (sc. 7), potem L808 `T MINUS 8 DNI` (sc. 8); L837 `WSTAWKA MEDIALNA -- T MINUS 5 DNI`, potem L928 `T MINUS 6 DNI` (sc. 9).
- **Wyczuwalność w treści:** (1) sc. 8 podaje nagłówek `"TAJEMNICZA CHOROBA MĘŻCZYZN -- TRZECI PRZYPADEK W BERLINIE."` (L813) po tym, jak w sc. 7 lekarz z Berlina mówi o śmiertelności „kilkudziesięciu procent” (L772). Świat cofa się do wcześniejszego etapu. (2) Sc. 9: Karolina mówi L958 `On jest zdrowy. Ma gorączkę, ale powiedzieli, że to nie...`, a widz minutę wcześniej przeczytał w W3, że Michał jest w szpitalu (L854). (3) W1 po sc. 4 jest niewyczuwalne (WHO wspomina o Europie, nie o Warszawie).
- **Warianty (PROPOZYCJE):**
  1. Przestawić segmenty: W1 przed sc. 4; sc. 8 przed sc. 7 (albo przed W2); sc. 9 przed W3.
  2. Zmienić etykiety: W1 → T-9, sc. 8 → T-7, sc. 9 → T-5 rano.
  3. Mieszanka: przestawić W1 i sc. 9, przetykietować sc. 8.
- **Rekomendacja (PROPOZYCJA):** wariant 1. Nie zmienia treści, a P4 trafia wtedy bezpośrednio po wydruku z sc. 8 (zob. E01-18).
- **Skutki:** rozpiska (kolejność), przejścia scen, PDF. Zależności: E01-07, E01-18, N-04.

#### E01-09 — Arytmetyka P4: „pięć + trzynaście lat”
- **Waga:** WYSOKA. **Status audytu:** POTWIERDZONE.
- **Lokalizacja i cytaty:** L885 `To są jej wyniki. Jej metodologia. Jej pięć lat pracy`; L886 `przed wyjazdem i trzynaście lat przed tym.`; L183 `(VERA MA 24 LATA)`; L225 `Twój projekt doktorski -- chromosom Y, mechanizmy`; L867 `(VERA MA OKOŁO 52 LATA)`; L869 `Napis: "OSLO. DWA LATA PO WYJEŹDZIE Z WARSZAWY."`
- **Na czym polega sprzeczność:** 5 + 13 = 18 lat pracy. Vera zaczyna projekt w wieku 24 lat (L183, L225), a wyjeżdża w wieku ok. 50 (52 − 2, L867, L869), czyli po ok. 26 latach. Liczba 18 pokrywa się z „osiemnaście lat temu” w E02 (E02:L400 `Data: osiemnaście lat temu.`, na podstawie fragmentu), a E01 daje publikację ok. 12 lat temu (64 − 52).
- **Warianty (PROPOZYCJE):**
  1. PROPOZYCJA brzmienia L885–L886: `To są jej wyniki. Jej metodologia. Ćwierć wieku jej pracy.`
  2. Bez liczby: `To są jej wyniki. Jej metodologia. Całe jej życie zawodowe.`
  3. Zostawić podział, ale zgodny z osią: `…dwadzieścia pięć lat pracy w Warszawie.`
- **Rekomendacja (PROPOZYCJA):** wariant 1 albo 2, razem z E02:L400 → „około dwanaście lat temu” (rekomendacja handoffu A3).
- **Skutki:** E02 sc. 3 (na podstawie fragmentu); beaty BlokP4; PDF.

#### E01-10 — Zasiew przyjaźni Marta–Aga jest nieczytelny (handoff A6)
- **Waga:** WYSOKA. **Status audytu:** POTWIERDZONE (audyt sam zawęża A6, i to zawężenie potwierdzam).
- **Lokalizacja i cytaty:** L164 `Słuchaj -- ta koleżanka Agi Bryk ze studiów, Marta`; L165 `ma na imię jak ja, dzwoniła ostatnio?`; L167 `TOMEK (nie rozumiejąc pytania)`; L417 `"Aga, jutro możesz pogadać? Przepraszam, że znowu`; L418 `o złej porze. M."`
- **Na czym polega sprzeczność:** gramatycznie Marta pyta o trzecią osobę, inną Martę. Handoff mówi, że to ona sama jest przyjaciółką Agi: H74 `Przyjaciółka Marty ze studiów. To ona ściąga Verę na farmę SMS-em (ironia dramatyczna).` Pytanie jest skierowane do podwładnego z PSE, który nie ma powodu tego wiedzieć, i scenariusz zaznacza, że Tomek nie rozumie (L167). W sc. 5 Marta pisze do Agi bezpośrednio, więc pośredniczka nie jest potrzebna. Grep „studi” w E02 nie daje wyników (na podstawie grep), więc wątek nie jest spłacany.
- **Warianty (PROPOZYCJE):**
  1. Usunąć wymianę L161–L171. Przyjaźń oprzeć na SMS-ie z sc. 5 i dać mu podpis kontaktu (insert: „Aga ❤ akademik”, bez dialogu).
  2. PROPOZYCJA brzmienia L164–L165: `Słuchaj -- jakby dzwoniła Aga Bryk ze szpitala, to daj mi znać. Od razu.` (zasiew relacji i niepokoju, bez zabawy imieniem).
  3. Zostawić zagadkę „drugiej Marty” i spłacić ją w E02.
- **Rekomendacja (PROPOZYCJA):** wariant 2. Zostawia scenę i Tomka, zasiewa Agę w 4. minucie i daje widzowi pytanie: dlaczego Marta czeka na telefon od lekarki chorób zakaźnych?
- **Skutki:** beaty Sceny 2; rozpiska (która tej wymiany nie ma); PDF; handoff §2 („przyjaciółka ze studiów”, zob. E01-40).

#### E01-11 — Piotr nie istnieje w scenach; wiadomość o Ares IV przychodzi jak sprawa służbowa
- **Waga:** WYSOKA. **Status audytu:** POTWIERDZONE.
- **Lokalizacja i cytaty:** L34 `Żona Piotra Kowalskiego -- astronauty Ares IV.`; L542 `Marta -- masz pilny na wewnętrznym. Numer trzy.`; L559 `Rozumiem. Przekażę dalej.`; L569 `Ares IV milczy od czterdziestu ośmiu godzin.`; L396 `i Michał powiedział, że mu przypomina tatę.`
- **Na czym polega sprzeczność:** imię Piotra pada tylko w nocie i obsadzie (grep: L27, L34, L35). Widz nie wie, że mąż Marty jest na Ares IV. Najbliżej są „przypomina tatę” (L396) i spojrzenie na szafę z teczką (L582–L583). Wiadomość przychodzi na wewnętrzną linię operatora sieci, a Marta odpowiada jak urzędniczka („Przekażę dalej”). Tomek reaguje tak, jakby znał sytuację (L575), a widz jej nie zna. Centralny wątek serii (mężczyźni na Marsie) nie jest w E01 ustawiony.
- **Warianty (PROPOZYCJE):**
  1. PROPOZYCJA brzmienia L559: `Rozumiem. Sama powiem córce.` oraz po L570 nowa kwestia TOMKA: `Piotr?` i odpowiedź MARTY: `Cała załoga.`
  2. Zostawić dialog i dodać insert: zdjęcie Piotra w kombinezonie misji jako tapeta prywatnego telefonu Marty (sc. 5, L415–L419).
  3. W sc. 9 PROPOZYCJA nowej kwestii KAROLINY: `A tata? Jest coś z ESA?` i odpowiedzi MARTY: `Nie wiem jeszcze.` (powtórzenie L952 nabiera drugiego znaczenia).
- **Rekomendacja (PROPOZYCJA):** 1 + 2. Dwie krótkie zmiany ustawiają cały wątek Ares dla E02/E03 i nadają sens spojrzeniu na teczkę.
- **Skutki:** sc. 5, 6, 9; inserty; beaty Sceny 6 i 9; E03 (pierwszy kontakt Marta–Piotr zyskuje podbudowę; na podstawie handoffu §3). Zależność: E01-02.

#### E01-12 — Śmierć Dąbrowskiego zapowiedziana w obsadzie, nieobecna na ekranie (handoff C11)
- **Waga:** WYSOKA. **Status audytu:** POTWIERDZONE.
- **Lokalizacja i cytaty:** L46 `ojciec Agi. Pojawia się tylko w scenach przeszłości`; L47 `i umiera poza kadrem w Zero Day.`; montaż L1157–L1224 (grep „Dąbrowsk” daje w teraźniejszości tylko wydruki: L818 `Nazwisko autora: prof. Marek Dąbrowski.` i L879).
- **Na czym polega sprzeczność:** w montażu nie ma ani ujęcia, ani informacji. Widz E01 nie wie nawet, czy Dąbrowski żyje w teraźniejszości.
- **Warianty (PROPOZYCJE):**
  1. Ujęcie w montażu: Vera w hotelu widzi na ekranie listę zmarłych naukowców albo nekrolog z nazwiskiem (bez słów), po czym patrzy na dłonie (L1222). To spina dwa jej ujęcia.
  2. Aga w laboratorium dostaje telefon (bez dźwięku) i na sekundę przerywa porównywanie sekwencji.
  3. W sc. 8 dać sygnał, że Marek żyje (świeży wywiad z nim w portalu, L812–L813), a śmierć zostawić na E02/E03.
- **Rekomendacja (PROPOZYCJA):** wariant 1. Jedno ujęcie bez dialogu daje ironię „jej krzywdziciel ginie od jej wirusa” (rekomendacja handoffu C11).
- **Skutki:** montaż sc. 14 (+1 ujęcie); beaty Zero Day; E03 sc. 14 (na podstawie handoffu §3, wyznanie „Tata umarł…”). Decyzja D-06.

#### E01-13 — Mechanizm uwolnienia niejasny; droga Oslo → Warszawa bez pomostu
- **Waga:** WYSOKA. **Status audytu:** POTWIERDZONE w części tekstowej (niejasność fiolki, brak pomostu). Ocena epidemiologiczna („nierealne w 4 dni”) jest NIEPOTWIERDZONE.
- **Lokalizacja i cytaty:** L282 `Już po wszystkim.`; L284 `Otwiera fiolkę. Praca trwa krótko. Zamknięta. Skończone.`; L287 `Fiolka jest pusta.`; L360 `zachorowania wśród mężczyzn w Niemczech, Francji`; L318 `Aga wchodzi do sali. Przy łóżku -- mężczyzna, około 45 lat.`; E02:L364 `jednej z tablic: "Tomasz Kamiński, W-wa, 14.03 -- pacjent zero".` (na podstawie fragmentu)
- **Na czym polega sprzeczność:** (1) Vera mówi „Już po wszystkim” *przed* otwarciem fiolki (L282, potem L284). Nie wiadomo, czy uwalnia wirusa, czy niszczy ostatnią próbkę. (2) Z jednej sceny w Oslo na T-14 w ciągu 4 dni powstają ogniska w trzech krajach, a po 5 dniach są trzy przypadki na jednym oddziale w Warszawie. Tekst nie daje drogi zakażenia. Czy taka dynamika jest możliwa: NIEPOTWIERDZONE (nie badano). (3) Pacjent zero w E02 jest z Warszawy.
- **Warianty (PROPOZYCJE):**
  1. Sc. 3 to zniszczenie ostatniej próbki, a uwolnienie było wcześniej i wieloogniskowe. Wtedy T-14 nie jest dniem zero zakażeń.
  2. Vera rozsyła wirusa: jedno ujęcie w sc. 3 albo sc. 8 (bilety lotnicze, lista adresów, pudełka kurierskie).
  3. Zostawić tajemnicę i dać w E02/E03 linię o długim okresie bezobjawowym. Twierdzenie o okresie utajenia byłoby wtedy faktem fikcji, nie nauki.
- **Rekomendacja (PROPOZYCJA):** decyzja właściciela (D-03), bo dotyka sedna fabuły. Przy każdym wariancie przestawić L282 za L284, żeby „Już po wszystkim” padło po czynności.
- **Skutki:** sc. 3, ewentualnie sc. 8; E02 (pacjent zero, na podstawie fragmentu); E03 (śledztwo, wyznanie; na podstawie handoffu); noty techniczne; beaty Sceny 3.

#### N-05 — Otwarcie: 9 minut bez zagrożenia, P1 bez wyzwalacza (nowe)
- **Waga:** WYSOKA (napięcie, ryzyko odpływu widza).
- **Lokalizacja i cytaty:** L88 `Zwykła, młoda, prosta chwila. Nic się nie zapowiada.`; L150 `Nic pilnego. Normalna środa.`; L251 `W takim razie -- zaczynamy.`; L261 `Pierwsze zimne ujęcie w całym odcinku.`; L21 `Cztery bloki przeszłości rozmieszczone przez cały odcinek,`; L22 `każdy wyzwolony przez coś w teraźniejszości.`
- **Na czym polega problem:** sc. 1 (3,5 min), sc. 2 (1,5 min) i P1 (4 min) dają 9:00 normalności, zanim pojawi się pierwszy niepokój (sc. 3 zaczyna się w 9:00, wyliczenie w sekcji d). Jedynymi sygnałami są żółta teczka (L156) i niezrozumiałe pytanie o „koleżankę Agi” (L164–L165). P1 nie ma wyzwalacza w teraźniejszości: poprzedza go rozmowa Marty z Tomkiem, a Vera nie została jeszcze pokazana. To łamie regułę z L21–L22.
- **Warianty (PROPOZYCJE):**
  1. Przestawić P1 za sc. 3: krzywa „Adam” i fiolka (L273, L287) stają się wyzwalaczem młodej Very. Sc. 3 zaczyna się wtedy w 5:00.
  2. Krótki teaser na otwarcie (10–15 s z sc. 3: ręka w rękawicy, żółta karteczka na obiektywie), potem sc. 1 bez zmian.
  3. Skrócić sc. 1 z 3,5 do 2,5 min (sekcja d).
- **Rekomendacja (PROPOZYCJA):** 1 + 3. Bez nowych treści; pierwszy hak w 4:00–5:00.
- **Skutki:** rozpiska (kolejność), przejścia scen, PDF; zależność z E01-18.

### ŚREDNIE

#### E01-14 — „u twojej mamy sąsiadki” (handoff A5)
- **Status audytu:** POTWIERDZONE. **Cytaty:** L1079 `Dziewczynki są u twojej mamy sąsiadki?`; L1082 `Tak. U Bożeny. Śpią już pewnie.`; L807 `INT. MIESZKANIE VERY, OSLO -- WIECZÓR`
- **Problem:** matka Agi mieszka w Oslo, a składnia („mamy sąsiadki”) jest niejasna. Kwestia jest dodatkowo trzecim sygnałem, że Aga ma żyjącą matkę (E01-01).
- **Warianty (PROPOZYCJE):** (1) PROPOZYCJA L1079: `Dziewczynki są u Bożeny?` i L1082: `Tak. Śpią już pewnie.`; (2) handoff: „u Bożeny, u sąsiadki?”; (3) zostawić jako ślad, że Vera ma mieszkanie w Warszawie (decyzja kanoniczna).
- **Rekomendacja (PROPOZYCJA):** wariant 1. **Skutki:** beaty Sceny 12, rozpiska, PDF.

#### E01-15 — Nota językowa sprzeczna ze scenami
- **Status audytu:** POTWIERDZONE. **Cytaty:** L52 `Vera mówi po polsku przez cały E01 -- z wyraźnym norweskim akcentem.`; L56 `Z Agą rozmawiały po norwesku -- ale w E01 nie ma ich wspólnej sceny.`; L432 `Vera swobodniejsza, pewniejsza. Polski prawie bez akcentu.`; L639 `AGA (po polsku, naturalnie)`; L711 `AGA (po norwesku -- napisy polskie)`; L900 `VERA (do siebie, bardzo cicho, po norwesku -- napisy)`
- **Problem:** teraźniejsza Vera wypowiada w E01 tylko kwestię z L282, po norwesku. P2 i P3 to wspólne sceny Very z Agą (wbrew L56). W P3 kuchnia jest po polsku, a pakowanie po norwesku, bez reguły.
- **Warianty (PROPOZYCJE):** (1) nowa reguła w nocie: „po norwesku sama ze sobą i z Agą w chwilach intymnych; po polsku w pracy i przy ludziach”; (2) ujednolicić P3; (3) dopisać, że akcent wrócił po latach w Oslo.
- **Rekomendacja (PROPOZYCJA):** 1 + 3, bez zmian dialogów. **Skutki:** nota, lektor, napisy, instrukcje Flow. Decyzja D-10.

#### E01-16 — Paweł umiera na T-1; nota każe Adze stać „przy zwłokach” na T0
- **Status audytu:** POTWIERDZONE w E01; E03 na podstawie fragmentu. **Cytaty:** L1108 `T MINUS 1 DZIEŃ`; L1119 `O czwartej czternaście.`; L27 `teczką i zdjęciem Piotra. Aga przy zwłokach Pawła.`; E03:L1401 `Mój mąż. Umarł o czwartej rano. W pierwszym dniu.` (na podstawie fragmentu)
- **Warianty (PROPOZYCJE):** (1) zmienić kwestię w E03; (2) przesunąć sc. 12–13 tak, by śmierć wypadła o 04:14 w T0 (sc. 13 = świt T0, montaż zaczyna się od Agi); (3) uznać „w pierwszym dniu” za subiektywny skrót Agi.
- **Rekomendacja (PROPOZYCJA):** wariant 2. Synchronizuje notę i E03 i podnosi T0 (osobista strata w dniu globalnej). **Skutki:** nagłówki sc. 12–13, beaty, rozpiska. Decyzja D-05.

#### E01-17 — Nota: „TOR B -- Warszawa”, „T-14 do T=0”, trzy wątki
- **Status audytu:** POTWIERDZONE. **Cytaty:** L18 `TOR B -- PRZESZŁOŚĆ: Warszawa, lata wcześniej.`; L869 `Napis: "OSLO. DWA LATA PO WYJEŹDZIE Z WARSZAWY."`; L12 `TOR A -- TERAŹNIEJSZOŚĆ: Warszawa i Oslo, T-14 do T=0.`; L1228 `T PLUS 8`
- **Warianty (PROPOZYCJE):** (1) poprawić notę (Warszawa i Oslo; T-14 do T+8; cztery wątki, z Verą); (2) oznaczyć sc. 15 jako epilog. **Rekomendacja:** 1 (tylko nota).

#### E01-18 — Wyzwalacze bloków przeszłości spełnione częściowo
- **Status audytu:** POTWIERDZONE. **Cytaty:** L22 `każdy wyzwolony przez coś w teraźniejszości.`; P2 po L417 `"Aga, jutro możesz pogadać? Przepraszam, że znowu`; P3 po L602 `Mam trochę gardło ale pewnie z klimy. Jutro normalnie tak?"`; P4 po L856 `Sygnał. Sygnał. Poczta głosowa.`
- **Problem:** P1 nie ma wyzwalacza (N-05). P2 ma dobry wyzwalacz (SMS „Aga” → mała Aga). P3 następuje po SMS-ie Michała, który nie ma związku z Verą (teczka była dwa segmenty wcześniej). P4 jest oddzielony od swojego wyzwalacza (wydruk w sc. 8, L817–L819) wstawką W3.
- **Warianty (PROPOZYCJE):** (1) P1 za sc. 3; (2) W3 przed sc. 8, żeby P4 szedł bezpośrednio po wydruku; (3) przed P3 dać 2-sekundowy most: Vera w Oslo wyłącza telewizor z paskiem W2. **Rekomendacja:** 1 + 2 (+3 opcjonalnie).

#### E01-19 — Obsada niepełna
- **Status audytu:** POTWIERDZONE. **Cytaty:** L1151 `Za plecami premiera -- kobieta. Wicepremier Wolska.`; L676 `Wiem o Kaśce.`; L1082 `Tak. U Bożeny. Śpią już pewnie.`
- **Problem:** obsada (L31–L47) ma 8 pozycji. Brak w niej Joanny, Beaty, Marcina, lekarza z Berlina, rzeczniczki WHO, Wolskiej (postaci kanonicznej), doktorantki „Kaśki” oraz małej Agi i Agi w wieku 19 lat.
- **Warianty (PROPOZYCJE):** dopisać role mówiące i sekcję „Epizody”. **Rekomendacja:** tak.

#### E01-20 — Sc. 11: „dwa miejsca puste” przy trzech nieobecnych; drugi „Marek”
- **Status audytu:** POTWIERDZONE. **Cytaty:** L1009 `Sala normalnie wyglądająca -- ale dwa miejsca są puste.`; L1015 `Dzwoniła jego żona. Ma gorączkę od przedwczoraj.`; L1016 `I Marek też nie będzie. I Kacper powiedział, że...`
- **Warianty (PROPOZYCJE):** (1) `Sala normalnie wyglądająca -- ale trzy miejsca są puste.`; (2) PROPOZYCJA L1016: `I Jacek też nie będzie. I Kacper powiedział, że...` **Rekomendacja:** 1 + 2.

#### E01-21 — Sc. 5: „byliśmy na wystawie” i „Idź oglądać wystawę. Dobranoc” po południu
- **Status audytu:** POTWIERDZONE. **Cytaty:** L370 `INT. CENTRUM PSE -- POPOŁUDNIE`; L389 `Mamo, byliśmy z Michałem na tej wystawie o której mówiłam.`; L408 `Tak. Idź oglądać wystawę. Dobranoc kochanie.`; L108 `Tak, tak, dobrze, to do wieczora.`
- **Warianty (PROPOZYCJE):** (1) PROPOZYCJA L389: `Mamo, jesteśmy z Michałem na tej wystawie, o której mówiłam.` i L388 „jakby z galerii”; (2) PROPOZYCJA L408: `Tak. Wracajcie ostrożnie. Do wieczora, kochanie.` **Rekomendacja:** 2 (zachowuje „knajpę” i domyka „do wieczora” z L108).

#### E01-22 — Wiedza świata: „trzeci przypadek w Berlinie” (T-8) po kryzysowym WHO (T-10); „wirus Y” w TV przed wykładem o mechanizmie
- **Status audytu:** POTWIERDZONE. **Cytaty:** L813 `"TAJEMNICZA CHOROBA MĘŻCZYZN -- TRZECI PRZYPADEK W BERLINIE."`; L358 `Światowa Organizacja Zdrowia zwołała dziś nadzwyczajne`; L593 `Pasek TVN: "WIRUS Y (HYV-1): ŚMIERTELNOŚĆ U MĘŻCZYZN WYSOKA -- WHO POTWIERDZA"`; L779 `Chromosom Y. Wirus rozpoznaje specyficzną sekwencję`
- **Warianty (PROPOZYCJE):** (1) PROPOZYCJA L813: `"TAJEMNICZA CHOROBA MĘŻCZYZN -- SETKI PRZYPADKÓW W NIEMCZECH."`; (2) w W2 „nowy wirus (HYV-1)”, a „wirus Y” dopiero w W3; (3) sc. 7 przed W2. **Rekomendacja:** 1 + 2.

#### E01-23 — Sc. 3: laboratorium BSL-4, kombinezon „P3”, karteczka z kieszeni
- **Status audytu:** ZAWĘŻONE. Niespójność oznaczeń w tekście jest potwierdzona. Wszystkie twierdzenia techniczne audytu (co oznacza „P3”, budowa kombinezonów, istnienie lub brak laboratorium BSL-4 w Norwegii) są **NIEPOTWIERDZONE**. Audyt podawał je z pamięci; w tym temacie nie były weryfikowane.
- **Cytaty:** L258 `INT. LABORATORIUM BIOSAFETY LEVEL 4, OSLO -- TERAŹNIEJSZOŚĆ`; L266 `w kombinezonie P3. Przed nią na blacie: fiolka z bezbarwnym płynem.`; L276 `z kieszeni żółtą karteczkę samoprzylepną. Zasłania obiektyw.`
- **Problem w tekście:** nagłówek podaje poziom 4, a opis kostiumu „P3”. Czy to ta sama klasa, NIEPOTWIERDZONE. Wystarczy, że dwa oznaczenia poziomu w jednej scenie się różnią.
- **Warianty (PROPOZYCJE):** (1) zostawić „BSL-4” i usunąć „P3” z opisu kostiumu („w pełnym kombinezonie ochronnym”); (2) fikcyjny instytut z nazwą; (3) konsultacja merytoryczna przed zdjęciami. **Rekomendacja:** 1 + 3.

#### E01-24 — Ślad prowadzi wprost do Very
- **Status audytu:** POTWIERDZONE (tekst); wniosek o skuteczności śledztwa to interpretacja dramaturgiczna. **Cytaty:** L791 `WHO i Interpol prowadzą śledztwo.`; L877 `Tytuł: "Selektywna kaskada odpornościowa przy sekwencji`; L889 `"Dane wstępne: V. Strand (materiały niepublikowane)."`
- **Warianty (PROPOZYCJE):** (1) w E02/E03 jedna linia o rozpadzie śledztwa; (2) mniej jednoznaczny tytuł artykułu; (3) usunąć „Interpol”. **Rekomendacja:** 1.

#### E01-25 — „rs1799945” w P2
- **Status audytu:** ZAWĘŻONE. Cytat jest potwierdzony. Twierdzenia audytu o tym, czego dotyczy ten identyfikator, i o dacie powstania bazy identyfikatorów są **NIEPOTWIERDZONE**. Zarzut anachronizmu zależy od roku teraźniejszości, którego E01 nie podaje (grep lat 19xx/20xx: brak wyników).
- **Cytat:** L447 `Masz rację. Diabeł tkwi w wariancie rs1799945.`
- **Warianty (PROPOZYCJE):** (1) PROPOZYCJA L447: `Masz rację. Diabeł tkwi w tym jednym wariancie.`; (2) fikcyjny opis lokalizacji bez identyfikatora. **Rekomendacja:** 1 (usuwa ryzyko i ułatwia TTS).

#### E01-26 — Epoka bloków przeszłości
- **Status audytu:** ZAWĘŻONE. E01 nie podaje roku teraźniejszości (grep: brak lat), więc „P1 = ok. 1986 = PRL” to założenie, nie fakt z tekstu. Uwaga o „Zakładzie” i „Departamencie” na UW jest NIEPOTWIERDZONE.
- **Cytaty:** L186 `Napis dyskretny w rogu: "WARSZAWA. 40 LAT WCZEŚNIEJ."`; L213 `Departament wirusologii. Pan profesor... pan jest`
- **Warianty (PROPOZYCJE):** (1) właściciel ustala rok teraźniejszości i w notach technicznych epokę każdego bloku; (2) zostawić bez roku i unikać w kadrze techniki datującej. **Rekomendacja:** 1.

#### E01-27 — Dwie wersje przypisu
- **Status audytu:** POTWIERDZONE. **Cytaty:** L817 `Obok laptopa: wydruki. Na wierzchu strona tytułowa publikacji.`; L819 `W przypisach, drobnym drukiem: "V. Strand (dane własne, niepublikowane)."`; L888 `W przypisach, drobnym drukiem, na stronie czternastej:`; L889 `"Dane wstępne: V. Strand (materiały niepublikowane)."`
- **Warianty (PROPOZYCJE):** (1) w sc. 8 przyjąć brzmienie z P4 i „wydruk otwarty na stronie czternastej”; (2) świadomie dwa dokumenty. **Rekomendacja:** 1.

#### E01-28 — „Ogłaszam stan wyjątkowy” w ustach premiera
- **Status audytu:** ZAWĘŻONE. Cytat jest potwierdzony. Twierdzenie o tym, kto według Konstytucji RP wprowadza który stan nadzwyczajny, jest **NIEPOTWIERDZONE** (nie sprawdzano w tym temacie).
- **Cytat:** L1148 `Ogłaszam stan wyjątkowy na terenie całego kraju.`
- **Warianty (PROPOZYCJE):** (1) PROPOZYCJA L1148: `Zwróciłem się do Prezydenta o wprowadzenie stanu wyjątkowego na terenie całego kraju.` (przy okazji sygnał rozpadu władzy pod Wolską); (2) zostawić jako licencję. **Rekomendacja:** przed decyzją zweryfikować podstawę prawną.

#### E01-29 — Sc. 15: statek na autopilocie 8 dni po T0
- **Status audytu:** ZAWĘŻONE. Cytaty są potwierdzone. Wyliczenia nawigacyjne audytu (węzły, mile, zachowanie autopilota) są **NIEPOTWIERDZONE**. Sprzeczność tekstowa to: martwi od co najmniej 8 dni, a opis „jakby przysnął”.
- **Cytaty:** L1228 `T PLUS 8`; L1244 `relingu, jakby przysnął. Mewa siada mu na ramieniu, po chwili odlatuje.`; L1249 `kurs ustawiony, prędkość stała, autopilot trzyma linię. Na monitorze`; L1251 `GAZOPORT. Nikt tego nie czyta. Statek sam pamięta, dokąd miał płynąć.`
- **Warianty (PROPOZYCJE):** (1) ostatnie zgony na pokładzie niedawno (wymaga dopuszczenia zgonów po T0 i doprecyzowania L1196); (2) statek stał na kotwicy i ruszył (np. zerwał się); (3) zmienić T+8 na T+1/T+2 i przesunąć prolog E02. Format „T PLUS 8 DNI”. **Rekomendacja:** 1 + format.

#### E01-30 — Metraż: 60 / 60,5 / 65 / ~52 / 54–55
- **Status audytu:** POTWIERDZONE. **Cytat:** L3 `Format: ok. 60 minut`; H42 `- **E01 — ADAM** (~65 min)`
- **Problem:** scenariusz jest wewnętrznie prawie spójny (60 vs 60,5; sekcja d). Pozostałe liczby pochodzą z dokumentów rzędu 2 i 4.
- **Warianty (PROPOZYCJE):** (1) cel 60 min; (2) ~65 min; (3) ~52–55 min. **Rekomendacja:** 1 z redystrybucją metrażu (sekcja d). Decyzja D-09.

#### E01-31 — Wątki zasiane i nieopłacone w E01
- **Status audytu:** POTWIERDZONE dla E01. Spłaty w E02 są NIEZBADANE (nie czytano E02 L711, L734).
- **Cytaty:** L102 `Karolina, czy wzięłaś klucze od piwnicy, bo --`; L417 `"Aga, jutro możesz pogadać? Przepraszam, że znowu`; L377 `Izolacja wygląda na R-17 jak myśleliśmy. Mogę naprawić`
- **Warianty (PROPOZYCJE):** (1) w sc. 11 insert: odpowiedź „Aga: nie mogę, pacjenci. Jutro.” na prywatnym telefonie Marty (L1044); (2) usunąć „znowu o złej porze”. **Rekomendacja:** 1.

#### E01-32 — „Dwie sekwencje / To niemożliwe” (handoff B9)
- **Status audytu:** POTWIERDZONE. **Cytaty:** L1214 `Na ekranie dwie sekwencje genetyczne, ułożone obok siebie.`; L1219 `To niemożliwe.`; L787 `Ktoś to zaprojektował.`
- **Problem:** w E01 nie wiadomo, co jest porównywane. Wniosek „zaprojektowany” padł już w sc. 7 (L787), więc „To niemożliwe” na T0 niczego nie dodaje, chyba że druga sekwencja jest osobista.
- **Warianty (PROPOZYCJE):** (1) druga sekwencja to stare dane z domowego archiwum matki (np. dyskietka, wydruk „V. Strand”), a „To niemożliwe” znaczy rozpoznanie; (2) dwie próbki od różnych pacjentów, identyczne; (3) wątek ocalałego (wymaga zmiany L1196). **Rekomendacja:** 1, zależnie od D-01. Najmocniejszy kandydat na cliffhanger osobisty (sekcja e).

#### N-03 — Montaż Zero Day: fałszywe zakończenie i zdublowane ujęcie Karoliny (nowe)
- **Waga:** ŚREDNIA (rytm, napięcie końca).
- **Cytaty:** L1207 `Karolina. Siedzi na podłodze pod oknem.`; L1208 `Sweter Michała leży na fotelu.`; L1180 `Sweter Michała leży na fotelu.`; L1211 `Czarny ekran.`; L1219 `To niemożliwe.`; L1224 `Czarny ekran.`; L1260 `Czarny ekran.`
- **Problem:** ujęcie Karoliny pod oknem ze swetrem pojawia się w montażu dwa razy prawie słowo w słowo (L1178–L1181 i L1207–L1209). Po drugim pada `Czarny ekran.` (L1211), który widz odczyta jako koniec odcinka. Potem wracają jeszcze Aga (najważniejsza informacja montażu) i Vera, po nich drugi czarny ekran (L1224), a po sc. 15 trzeci (L1260). Najmocniejsza kwestia montażu („To niemożliwe”) trafia za fałszywe zakończenie.
- **Warianty (PROPOZYCJE):** (1) usunąć czarny ekran L1211 i drugie ujęcie Karoliny; (2) zostawić refren Karoliny, ale L1211 zastąpić twardym cięciem na Agę; (3) przenieść Agę i Verę (L1213–L1222) przed drugie ujęcie Karoliny, a czarny ekran zostawić po Karolinie.
- **Rekomendacja (PROPOZYCJA):** wariant 1.
- **Skutki:** beaty Zero Day, rozpiska.

#### N-04 — Kolejność W3 → sc. 9 odwraca wiedzę widza (nowe, skutek E01-08 dla napięcia)
- **Waga:** ŚREDNIA. **Cytaty:** L854 `"Jestem w szpitalu, to pewnie nic. Przyjdź dzisiaj?"`; L958 `On jest zdrowy. Ma gorączkę, ale powiedzieli, że to nie...`; L938 `Michał mówi, że jego tata jest w szpitalu od wczoraj.`
- **Problem:** widz wie z W3, że Michał jest w szpitalu. W sc. 9 (dzień wcześniej, pokazany później) Karolina mówi, że jest zdrowy. Ironia działa wstecz i scena traci napięcie, bo widz nie ma już pytania „co z Michałem”. Dodatkowo „on” w L958 jest dwuznaczne (E01-43).
- **Warianty (PROPOZYCJE):** jak E01-08 wariant 1 (sc. 9 przed W3). **Rekomendacja:** razem z E01-08.

#### N-06 — P3 po W2: najgłębszy spadek napięcia w odcinku (nowe)
- **Waga:** ŚREDNIA. **Cytaty:** L602 `Mam trochę gardło ale pewnie z klimy. Jutro normalnie tak?"`; L615 `Napis: "WARSZAWA. OK. 25 LAT PO PRZYJEŹDZIE."`; L704 `Cięcie. Kilka tygodni później.`
- **Problem:** pierwsze osobiste zagrożenie (objaw u Michała, napięcie 6) jest przerwane najdłuższym blokiem przeszłości (5 min, trzy lokacje, dwa skoki czasu) o zdradzie, bez związku z teraźniejszym zagrożeniem (napięcie 3). Pytanie „co z Michałem” wisi 5 minut bez podbicia.
- **Warianty (PROPOZYCJE):** (1) skrócić P3 do ok. 4 min (scena kuchni nocą L670–L701 jest najmocniejsza, korytarz L619–L631 można skrócić do jednego spojrzenia); (2) podzielić P3: zdrada (korytarz + kuchnia) po W2, wyjazd (L704–L760) po sc. 8, czyli tuż przed P4; (3) dać przed P3 most z teraźniejszością (E01-18 wariant 3).
- **Rekomendacja (PROPOZYCJA):** 1 + 3.

#### N-08 — Los Michała nierozstrzygnięty w E01 (nowe)
- **Waga:** ŚREDNIA (decyzja kanoniczna D-08). **Cytaty:** L989 `Automat: "Numer jest chwilowo niedostępny."`; L1179 `Telefon w ręce. Czarny ekran.`; L1180 `Sweter Michała leży na fotelu.`
- **Problem:** obsada (L36) nie mówi, że Michał umiera, w przeciwieństwie do Pawła (L43). W scenach jego śmierć jest tylko sugerowana. Handoff: H79 `W E01 z **Michałem** (chłopak w żółtym swetrze z dinozaurem — ginie w pandemii).` Jeśli to celowa niedopowiedziana żałoba, warto to zapisać. Jeśli nie, Karolina nie ma swojego punktu kulminacyjnego.
- **Warianty (PROPOZYCJE):** (1) zostawić niedopowiedzenie i zapisać to w nocie; (2) w montażu jedno ujęcie ekranu telefonu Karoliny: nieodebrane połączenie „Mama Michała”; (3) potwierdzenie w E02. **Rekomendacja:** 2 (najtańsze domknięcie, bez dialogu).

#### N-02 — Sc. 5 i sc. 6: ten sam dzień, ta sama pora, ten sam opis otwarcia (nowe)
- **Waga:** NISKA (rytm). **Cytaty:** L370 `INT. CENTRUM PSE -- POPOŁUDNIE`; L373 `Marta przy konsolach. Telebimy spokojne. Rozmawia`; L533 `T MINUS 9 DNI`; L537 `Marta przy konsolach. Telebimy spokojne. Oblicza coś,`
- **Problem:** dwie sceny w tym samym miejscu, dniu i porze, rozdzielone 4-minutowym P2, zaczynają się prawie identycznym zdaniem. Widz może uznać sc. 6 za powtórzenie.
- **Warianty (PROPOZYCJE):** (1) sc. 6 na wieczór T-9 (zmiana światła) i inny opis otwarcia; (2) połączyć sc. 5 i 6 w jedną scenę z P2 przeniesionym gdzie indziej. **Rekomendacja:** 1 (zgodne też z E01-21 „Dobranoc”).

### NISKIE

| ID | Status audytu | Cytat i linia | Problem | Propozycja |
|---|---|---|---|---|
| E01-33 | POTWIERDZONE | L1191 `Genewa. Konferencja prasowa WHO. Ta sama kobieta, co wcześniej` / L1194 `RZECZNIK WHO (po angielsku -- napisy polskie)` | rodzaj etykiety | PROPOZYCJA: `RZECZNICZKA WHO` |
| E01-34 | POTWIERDZONE | L396 `i Michał powiedział, że mu przypomina tatę.` | gramatycznie tata Michała, a reakcja Marty (L400–L402) wskazuje Piotra | PROPOZYCJA: `i Michał powiedział, że przypomina mu tatę. Mojego.` |
| E01-35 | POTWIERDZONE | L161 `Przy wyjściu z sali Marta mija Tomka. Zatrzymuje się na sekundę.` / L171 `Nieważne, za dużo na głowie. Idę do sali.` | przestrzeń: wychodzi z sali i idzie do sali | PROPOZYCJA: „Przy automacie z kawą” + `Wracam do sali.` |
| E01-36 | POTWIERDZONE | L1042 `Mapa za nią -- więcej pomarańczowych punktów niż tydzień temu.` / L1162 `Mapa świata. Pomarańczowa -- od brzegów ku środkowi.` | mapa sieci czy epidemii | PROPOZYCJA: w notach: pomarańczowy = stacje bez obsady |
| E01-37 | POTWIERDZONE | L993 `Na krześle w kącie pokoju -- zostawiony sweter.` / L1180 `Sweter Michała leży na fotelu.` / L1178 `Mieszkanie Karoliny. Karolina siedzi na podłodze pod oknem.` | krzesło/fotel; „mieszkanie” vs „pokój” (L976). Kolor dinozaura z kanonu Flow: NIEZBADANE (plik produkcyjny) | PROPOZYCJA: wszędzie „fotel” i „pokój Karoliny” |
| E01-38 | POTWIERDZONE | L1183 `Vera w anonimowym hotelu w Oslo. Telewizor. Mapa świata.` / L807 `INT. MIESZKANIE VERY, OSLO -- WIECZÓR` | brak powodu hotelu | PROPOZYCJA: walizka i bilet w kadrze (ucieczka) albo mieszkanie |
| E01-39 | POTWIERDZONE | L45 `Były mąż Very,` vs H82 `- **Prof. Marek Dąbrowski** — **70 l.**, polski wirusolog (UW), były partner Very, **ojciec Agi**.` | mąż vs partner; nazwisko Agi „z d. Strand” | decyzja D-11 |
| E01-40 | ZAWĘŻONE | L33 `Dr Marta Kowalska          38 lat. Analityczka sieci PSE. Skupiona, pragmatyczna.` (fragment `38 lat. Analityczka sieci PSE.`) / L35 `19 lat. Córka Marty i Piotra. Studentka informatyki.` | Marta rodzi w wieku 19 lat; „ze studiów” przy 4 latach różnicy i innych kierunkach. Wieku Piotra E01 nie podaje (grep) | PROPOZYCJA: „z akademika” zamiast „ze studiów” |
| E01-41 | POTWIERDZONE (błąd handoffu) | L1157 `SCENA 14 -- ZERO DAY` vs H111 `14 scen + montaż „Zero Day" + **SCENA 15 — STATEK WIDMO** (T+8, gazowiec LNG dryfuje na gazoport` | 13 scen + Zero Day (sc. 14) + sc. 15 | poprawić handoff |
| E01-42 | POTWIERDZONE (interpretacja, nie sprzeczność) | L901 `Moje.` | motyw prywatny vs czyn globalny | zostawić (decyzja kanoniczna) |
| E01-43 | POTWIERDZONE | L938 `Michał mówi, że jego tata jest w szpitalu od wczoraj.` / L958 `On jest zdrowy. Ma gorączkę, ale powiedzieli, że to nie...` | zaimek | PROPOZYCJA: didaskalia „(o Michale)” |
| E01-44 | POTWIERDZONE | L1152 `Obserwuje go. Wie, co będzie. Czeka.` | możliwa lektura spisku; wiek Wolskiej z beatów: NIEZBADANE | PROPOZYCJA: `Obserwuje go. Wie, że za chwilę zostanie sama. Czeka.` |
| E01-45 | POTWIERDZONE (próba: L327, L377, L389, L601, L782, L1055, L1111, L1228, L1250, L593) | np. L327 `Wczoraj wieczór. Doktor Bryk -- mamy podobny przypadek`; L782 `Nikt nie ewoluuje z taką precyzją.`; L1111 `Za zmęczona na płacz.`; L1250 `pełzną współrzędne i jedna nazwa portu docelowego: SWINOUJSCIE --` | język (lista w audycie). Uwaga audytu, że „TVN nie emituje pasków”: NIEPOTWIERDZONE | korekta językowa osobnym tematem, bez zmiany treści dialogów |
| N-01 | nowe (błąd handoffu) | L1237 `kopuły zbiorników jak katedry. Płynie. Powoli, równo, prosto. Za rufą` / L1249 `kurs ustawiony, prędkość stała, autopilot trzyma linię. Na monitorze` | handoff §3 mówi „dryfuje” (H111), a scenariusz pokazuje statek płynący kursem na autopilocie | poprawić handoff |
| N-07 | nowe | L225 `Twój projekt doktorski -- chromosom Y, mechanizmy` / L442 `wystarczająco selektywny -- zadziała na XY, ale też` / L779 `Chromosom Y. Wirus rozpoznaje specyficzną sekwencję` | widz zna mechanizm z P1 i P2, zanim lekarz z Berlina ogłosi go jako odkrycie w sc. 7. To nie błąd (ironia), ale sc. 7 nie jest odkryciem dla widza | zostawić; akcent sc. 7 na reakcji Agi (już jest: L803) |
| N-09 | nowe | L186 `Napis dyskretny w rogu: "WARSZAWA. 40 LAT WCZEŚNIEJ."` / L431 `Napis: "WARSZAWA. OK. 11 LAT PO PRZYJEŹDZIE."` / L869 `Napis: "OSLO. DWA LATA PO WYJEŹDZIE Z WARSZAWY."` | trzy różne systemy napisów (absolutny, względem przyjazdu, względem wyjazdu); widz musi liczyć | PROPOZYCJA: jeden system „X LAT WCZEŚNIEJ”: P1 40, P2 29, P3 15, P4 12 (24→64, 35→64, 49→64, 52→64) |
| N-10 | nowe | L127 `INT. CENTRUM DYSPOZYTORSKIE PSE, WARSZAWA -- TO SAMO RANO` / L12 `TOR A -- TERAŹNIEJSZOŚĆ: Warszawa i Oslo, T-14 do T=0.` | sc. 1 i 2 nie mają oznaczenia T; nie wiadomo, czy są przed T-14 (sc. 3), czy tego samego dnia | PROPOZYCJA: nagłówek „T MINUS 14 DNI” w sc. 1–2 albo „T MINUS 15 DNI” |

---

## (c) WERYFIKACJA USTALEŃ WEJŚCIOWYCH

Statusy: POTWIERDZONE (cytat z pliku E01 zgodny), OBALONE (tekst przeczy), ZAWĘŻONE (prawdziwe w części lub z poprawką), NIEZBADANE (poza zakresem; dopuszczalne tylko dla pozycji bez wagi KRYT/WYS).

### c1. Audyt `E01_audyt.md`, rejestr E01-01 … E01-45

| ID | Waga audytu | Status | Cytat i linia (E01) | Uwagi |
|---|---|---|---|---|
| E01-01 | KRYT | POTWIERDZONE | L16 `Widz nie wie jeszcze, że Aga jest córką Very.`; L514 `Mamma! Pappa powiedział, że możemy jutro do parku!`; L824 `Kontakt: "Aga". Zdjęcie profilowe -- Aga z dwiema małymi` | pewność w sc. 8; w P2 tylko poszlaka (imię) |
| E01-02 | KRYT | POTWIERDZONE (E01); E03 na podstawie fragmentu | L569 `Ares IV milczy od czterdziestu ośmiu godzin.`; L1188 `Miga ekran: "ARES IV -- SIGNAL INTERRUPTED."` | E03:L833 potwierdzone sed -n |
| E01-03 | KRYT | ZAWĘŻONE → WYSOKA | L480 `Coś jest w tej ciszy -- nie po raz pierwszy, widz to czuje.`; L497 `Mała kuchnia. Vera przy kuchence, Marek czyta przy stole.` | tekst nie wyklucza lektury „stare małżeństwo” (L435, L457) |
| E01-04 | WYS | POTWIERDZONE | L27 `teczką i zdjęciem Piotra. Aga przy zwłokach Pawła.` | grep „Piotr”: tylko L27, L34, L35 |
| E01-05 | WYS | POTWIERDZONE | L654 `Tata dzwonił. Pyta, czy przyjdę w sobotę na obiad.`; L672 `Vera i Marek w kuchni. Aga śpi. Cisza między nimi` | — |
| E01-06 | WYS | POTWIERDZONE | L594 `Pasek TVN24: "WIRUS Y -- ŚMIERTELNOŚĆ BLISKA 100% U HOSPITALIZOWANYCH MĘŻCZYZN"`; L772 `Śmiertelność wynosi już kilkadziesiąt procent wśród` | — |
| E01-07 | WYS | POTWIERDZONE | L854 `"Jestem w szpitalu, to pewnie nic. Przyjdź dzisiaj?"`; L986 `Po wczoraj: nic.` | — |
| E01-08 | WYS | ZAWĘŻONE | L351 `WSTAWKA MEDIALNA -- T MINUS 10 DNI`; L808 `T MINUS 8 DNI`; L928 `T MINUS 6 DNI`; L289 `Napis: T MINUS 14 DNI` | jawny napis tylko dla T-14; 2 z 3 cofnięć wyczuwalne w treści |
| E01-09 | WYS | POTWIERDZONE | L886 `przed wyjazdem i trzynaście lat przed tym.` | E02:L400 potwierdzone sed -n |
| E01-10 | WYS | POTWIERDZONE | L164 `Słuchaj -- ta koleżanka Agi Bryk ze studiów, Marta` | grep „studi” w E02: brak |
| E01-11 | WYS | POTWIERDZONE | L559 `Rozumiem. Przekażę dalej.` | — |
| E01-12 | WYS | POTWIERDZONE | L47 `i umiera poza kadrem w Zero Day.` | — |
| E01-13 | WYS | POTWIERDZONE (tekst); ocena epidemiologiczna NIEPOTWIERDZONE | L282 `Już po wszystkim.`; L287 `Fiolka jest pusta.` | — |
| E01-14 | ŚR | POTWIERDZONE | L1079 `Dziewczynki są u twojej mamy sąsiadki?` | = handoff A5 |
| E01-15 | ŚR | POTWIERDZONE | L56 `Z Agą rozmawiały po norwesku -- ale w E01 nie ma ich wspólnej sceny.` | — |
| E01-16 | ŚR | POTWIERDZONE (E01); E03 na podstawie fragmentu | L1119 `O czwartej czternaście.` | E03:L1401 potwierdzone sed -n |
| E01-17 | ŚR | POTWIERDZONE | L18 `TOR B -- PRZESZŁOŚĆ: Warszawa, lata wcześniej.` | — |
| E01-18 | ŚR | POTWIERDZONE | L22 `każdy wyzwolony przez coś w teraźniejszości.` | — |
| E01-19 | ŚR | POTWIERDZONE | L1151 `Za plecami premiera -- kobieta. Wicepremier Wolska.` | Wolskiej brak w obsadzie L31–L47 |
| E01-20 | ŚR | POTWIERDZONE | L1009 `Sala normalnie wyglądająca -- ale dwa miejsca są puste.` | — |
| E01-21 | ŚR | POTWIERDZONE | L408 `Tak. Idź oglądać wystawę. Dobranoc kochanie.` | — |
| E01-22 | ŚR | POTWIERDZONE | L813 `"TAJEMNICZA CHOROBA MĘŻCZYZN -- TRZECI PRZYPADEK W BERLINIE."` | — |
| E01-23 | ŚR | ZAWĘŻONE; twierdzenia techniczne NIEPOTWIERDZONE | L266 `w kombinezonie P3. Przed nią na blacie: fiolka z bezbarwnym płynem.` | twierdzenie o BSL-4 w Norwegii NIEPOTWIERDZONE |
| E01-24 | ŚR | POTWIERDZONE | L791 `WHO i Interpol prowadzą śledztwo.` | — |
| E01-25 | ŚR | ZAWĘŻONE; fakty genetyczne NIEPOTWIERDZONE | L447 `Masz rację. Diabeł tkwi w wariancie rs1799945.` | roku teraźniejszości brak w E01 |
| E01-26 | ŚR | ZAWĘŻONE | L186 `Napis dyskretny w rogu: "WARSZAWA. 40 LAT WCZEŚNIEJ."` | „PRL” to założenie roku, nie tekst |
| E01-27 | ŚR | POTWIERDZONE | L819 `W przypisach, drobnym drukiem: "V. Strand (dane własne, niepublikowane)."` | — |
| E01-28 | ŚR | ZAWĘŻONE; prawo NIEPOTWIERDZONE | L1148 `Ogłaszam stan wyjątkowy na terenie całego kraju.` | — |
| E01-29 | ŚR | ZAWĘŻONE; nawigacja NIEPOTWIERDZONE | L1228 `T PLUS 8` | — |
| E01-30 | ŚR | POTWIERDZONE | L3 `Format: ok. 60 minut` | suma 60,5 przeliczona w sekcji d |
| E01-31 | ŚR | POTWIERDZONE (E01); spłaty w E02 NIEZBADANE | L102 `Karolina, czy wzięłaś klucze od piwnicy, bo --` | — |
| E01-32 | ŚR | POTWIERDZONE | L1219 `To niemożliwe.` | — |
| E01-33 | NIS | POTWIERDZONE | L1194 `RZECZNIK WHO (po angielsku -- napisy polskie)` | — |
| E01-34 | NIS | POTWIERDZONE | L396 `i Michał powiedział, że mu przypomina tatę.` | — |
| E01-35 | NIS | POTWIERDZONE | L171 `Nieważne, za dużo na głowie. Idę do sali.` | — |
| E01-36 | NIS | POTWIERDZONE | L1203 `Od brzegów ku środkowi. Jeszcze nie wszystko. Ale już wiadomo.` | — |
| E01-37 | NIS | POTWIERDZONE (tekst); kanon Flow NIEZBADANE | L993 `Na krześle w kącie pokoju -- zostawiony sweter.` | — |
| E01-38 | NIS | POTWIERDZONE | L1183 `Vera w anonimowym hotelu w Oslo. Telewizor. Mapa świata.` | — |
| E01-39 | NIS | POTWIERDZONE | L45 `Były mąż Very,` | H82 „były partner” |
| E01-40 | NIS | ZAWĘŻONE | L35 `19 lat. Córka Marty i Piotra. Studentka informatyki.` | wieku Piotra (37) nie ma w E01 |
| E01-41 | NIS | POTWIERDZONE | L1157 `SCENA 14 -- ZERO DAY` | — |
| E01-42 | NIS | POTWIERDZONE (interpretacja) | L901 `Moje.` | — |
| E01-43 | NIS | POTWIERDZONE | L958 `On jest zdrowy. Ma gorączkę, ale powiedzieli, że to nie...` | — |
| E01-44 | NIS | POTWIERDZONE | L1152 `Obserwuje go. Wie, co będzie. Czeka.` | — |
| E01-45 | NIS | POTWIERDZONE (próba 10 pozycji) | L1111 `Za zmęczona na płacz.` | uwaga o TVN: NIEPOTWIERDZONE |

Audyt, sekcja 3 (czasy: suma 60,5, teraźniejszość 40,5, przeszłość 16,5, wstawki 3,5): **POTWIERDZONE** przeliczeniem od zera (sekcja d). Audyt, sekcja 4 (oś T w kolejności pliku i wieki postaci): **POTWIERDZONE** (L183, L204, L431, L511, L613, L636, L867).

### c2. Handoff (sekcje 2–5) — punkty dotyczące E01

| Punkt | Status | Cytat i linia | Uwagi |
|---|---|---|---|
| §4 A1 (Aga „V. Strand. Kim jest?”) | POTWIERDZONE (E02, na podstawie fragmentu); w E01 pogłębione | E02:L410 `"V. Strand. Kim jest?"`; L514 `Mamma! Pappa powiedział, że możemy jutro do parku!` | → E01-01 |
| §4 A2 (Wolska: imię) | ZAWĘŻONE (E01 neutralny) | L1151 `Za plecami premiera -- kobieta. Wicepremier Wolska.` | E01 nie podaje imienia ani wieku |
| §4 A3 (publikacja 18 vs 12 lat) | POTWIERDZONE, ZAWĘŻONE co do źródła | L867 `(VERA MA OKOŁO 52 LATA)`; L886 `przed wyjazdem i trzynaście lat przed tym.` | E01 daje ok. 12 lat; liczba 18 pasuje do arytmetyki L885–L886 → E01-09 |
| §4 A4 (Mars: dystans) | ZAWĘŻONE (nie dotyczy E01) | grep „km” w E01: brak wyników; L1188 `Miga ekran: "ARES IV -- SIGNAL INTERRUPTED."` | w E01 nie ma dystansu ani opóźnienia. Według notatek decyzji (sekcja 10, K1) punkt A4 handoffu jest błędny; nie badałem tego, bo dotyczy E03 |
| §4 A5 („u twojej mamy sąsiadki”) | POTWIERDZONE | L1079 `Dziewczynki są u twojej mamy sąsiadki?` | → E01-14 |
| §4 A6 (Marta „jak ja”) | ZAWĘŻONE | L165 `ma na imię jak ja, dzwoniła ostatnio?` | gramatycznie to pytanie o inną Martę, nie o siebie w 3. osobie → E01-10 |
| §4 B7 (list w teczce) | ZAWĘŻONE (E01 zasiewa tylko teczkę) | L158 `Marta odkłada teczkę do szafy. Zamyka. Bierze raport od Tomka.`; L583 `gdzie leży żółta teczka.` | E02:L1972 (na podstawie fragmentu) → E01-04 |
| §4 B8 (pojemnik Very) | ZAWĘŻONE (nie dotyczy E01) | grep „pojemnik” w E01: brak | — |
| §4 B9 (dwie sekwencje) | ZAWĘŻONE | L1214 `Na ekranie dwie sekwencje genetyczne, ułożone obok siebie.`; L787 `Ktoś to zaprojektował.` | inżynieria wiadoma od sc. 7; L1196 wyklucza ocalałych → E01-32 |
| §4 B10 (Zofia) | ZAWĘŻONE (nie dotyczy E01) | grep „Zofi” w E01: brak | — |
| §4 C11 (śmierć Dąbrowskiego) | POTWIERDZONE | L47 `i umiera poza kadrem w Zero Day.` | → E01-12 |
| §4 C12 (czterdziestu mężczyzn) | ZAWĘŻONE (nie dotyczy E01) | L1196 `sto procent. Nie odnotowano żadnego przypadku przeżycia.` | E01 nie mówi o załodze Ares IV |
| §4 C13 (antidotum/szczepionka) | ZAWĘŻONE (E01 neutralny) | L847 `chromosomu Y. Nie mamy leczenia przyczynowego.` | grep „antidot”, „szczepion”: brak |
| §4 C14 (Karolina–Korańczyk) | ZAWĘŻONE (nie dotyczy E01) | grep „Korańczyk”: brak | — |
| §4 D15, D16 | ZAWĘŻONE (nie dotyczy E01) | grep „Zofi”, „Kamiński” w E01: brak | dotyczą E02 |
| §4 „Co jest spójne”: bloki 24→52 grają z 64 | POTWIERDZONE | L183 `(VERA MA 24 LATA)`; L867 `(VERA MA OKOŁO 52 LATA)` | wiek Very i Agi spójny |
| §4 „Co jest spójne”: pacjent zero Kamiński | ZAWĘŻONE | grep „Kamiński” w E01: brak | spójne tylko dlatego, że E01 milczy → E01-13 |
| §4 „Co jest spójne”: ESA Darmstadt spłaca ziarno z E01 | ZAWĘŻONE | L570 `ESA nie ma kontaktu.`; L1188 `Miga ekran: "ARES IV -- SIGNAL INTERRUPTED."` | ziarno jest, ale ma sprzeczną oś → E01-02 |
| §4 „Co jest spójne”: statek jako klamra E01→E02 | POTWIERDZONE | L1251 `GAZOPORT. Nikt tego nie czyta. Statek sam pamięta, dokąd miał płynąć.` | — |
| §3 „14 scen + montaż Zero Day + SCENA 15” | OBALONE | L1157 `SCENA 14 -- ZERO DAY` | → E01-41 |
| §3 „gazowiec LNG dryfuje” | OBALONE | L1237 `kopuły zbiorników jak katedry. Płynie. Powoli, równo, prosto. Za rufą` | → N-01 |
| §3 „T-14→T0” | ZAWĘŻONE | L1228 `T PLUS 8` | odcinek wychodzi do T+8 |
| §1 „E01 ~65 min” | OBALONE jako opis pliku | L3 `Format: ok. 60 minut` | → E01-30 |
| §2 Vera „matka Agi (widz długo tego nie wie)” | OBALONE dla E01 | L514 `Mamma! Pappa powiedział, że możemy jutro do parku!`; L824 `Kontakt: "Aga". Zdjęcie profilowe -- Aga z dwiema małymi` | → E01-01 |
| §2 Vera „mówi po polsku z akcentem” | ZAWĘŻONE | L37 `Prof. Vera Strand          64 lata. Norweska wirusolog. Mówi po polsku z akcentem.` (fragment `Mówi po polsku z akcentem.`); L282 `Już po wszystkim.` (po norwesku) | w teraźniejszości E01 Vera nie mówi po polsku → E01-15 |
| §2 Aga „matka Hani (4 l.) i Zosi (2 l.)” | ZAWĘŻONE | L825 `dziewczynkami, wszyscy w parku, słońce.` | imion i wieku córek w E01 brak |
| §2 Aga „Przyjaciółka Marty ze studiów” | ZAWĘŻONE | L164 `Słuchaj -- ta koleżanka Agi Bryk ze studiów, Marta` | nieczytelne → E01-10 |
| §2 Paweł „zm. w E01, 04:14” | POTWIERDZONE | L1119 `O czwartej czternaście.` | dzień T-1 (L1108) |
| §2 Marta „prawa ręka Wolskiej” | ZAWĘŻONE (nie w E01) | L1151 `Za plecami premiera -- kobieta. Wicepremier Wolska.` | brak związku Marta–Wolska w E01 |
| §2 Dąbrowski „były partner” | OBALONE dla E01 | L45 `Były mąż Very,` | → E01-39 |
| §2 Michał „ginie w pandemii” | ZAWĘŻONE | L989 `Automat: "Numer jest chwilowo niedostępny."` | w E01 tylko sugerowane → N-08 |
| §2 „Adam” = kryptonim | POTWIERDZONE | L273 `naukowych -- krzywa wzrostu. Napis pod nią: "Adam".`; L919 `Jedno słowo: "Adam."` | — |
| §2 wirus Y / HYV-1 | POTWIERDZONE | L1195 `Wirus Y. Klinicznie HYV-1. Śmiertelność u mężczyzn:` | — |
| §2 Bożena = niania | ZAWĘŻONE | L1082 `Tak. U Bożeny. Śpią już pewnie.` | E01 nie mówi, kim jest Bożena |
| §5 decyzje otwarte (Wolska, Zofia, publikacja, Mars, A1, pojemnik/list, odporność) | ZAWĘŻONE | jak wyżej (A2, A3, B7–B10) | dla E01 ważne: publikacja (E01-09), A1 (E01-01), dwie sekwencje (E01-32) |

### c3. Notatki `E01_scenariusz.md`

| Ustalenie | Status | Cytat i linia | Uwagi |
|---|---|---|---|
| §1 23 segmenty | POTWIERDZONE | L1157 `SCENA 14 -- ZERO DAY` | 15 + 4 P + 4 W = 23 (skrypt: 23 etykiety CZAS) |
| §1 handoff „14 scen” błędny | POTWIERDZONE | L1157 `SCENA 14 -- ZERO DAY` | — |
| §2 tabela scen (miejsca, T, CZAS) | POTWIERDZONE | np. L1050 `T MINUS 2 DNI` | wszystkie T i CZAS zgodne z moją tabelą |
| §3 suma ≈ 60,5 min; 40,5 / 3,5 / 16,5 | POTWIERDZONE | L3 `Format: ok. 60 minut` | sekcja d |
| §4 cofnięcia W1, sc. 8, sc. 9 | POTWIERDZONE | L808 `T MINUS 8 DNI` | → E01-08 |
| §4 Michał 09:47 vs sc. 10 | POTWIERDZONE | L853 `Wiadomość od Michała, godzina 09:47:` | → E01-07 |
| §4 sc. 1–2 bez T | POTWIERDZONE | L127 `INT. CENTRUM DYSPOZYTORSKIE PSE, WARSZAWA -- TO SAMO RANO` | → N-10 |
| §5 „Tomasz Wiśniewski (Tomek)” | ZAWĘŻONE | L44 `Tomek Wiśniewski           35 lat. Podwładny Marty w PSE.` (fragment `35 lat. Podwładny Marty w PSE.`) | „Tomasz” nie pada |
| §5 Michał „żółty sweter… (L36, L73)” | ZAWĘŻONE | L36 `22 lata. Chłopak Karoliny. Zwykły, ciepły, żywy.`; L73 `On ma sweter -- jasnożółty, z nadrukiem dinozaura w okularach.` | sweter jest w L73, nie w L36 |
| §5 Piotr nieobecny w scenach | POTWIERDZONE | L34 `Żona Piotra Kowalskiego -- astronauty Ares IV.` | → E01-11 |
| §5 Kamiński, Hania/Zosia, Korańczyk nieobecni | POTWIERDZONE | grep: brak | — |
| §6 punkty A1–D16 | jak c2 | — | — |
| §7.1 cliffhanger | POTWIERDZONE | L26 `Odcinek kończy się Zero Day. Cliffhanger: Marta z żółtą` | → E01-04 |
| §7.2 język Very | POTWIERDZONE | L52 `Vera mówi po polsku przez cały E01 -- z wyraźnym norweskim akcentem.` | → E01-15 |
| §7.3 „brak wspólnej sceny” | POTWIERDZONE | L56 `Z Agą rozmawiały po norwesku -- ale w E01 nie ma ich wspólnej sceny.` | — |
| §7.4 reveal Agi | POTWIERDZONE | L640 `Mamo, jest coś do jedzenia? Byłam na wykładzie do ósmej.` | → E01-01 |
| §7.5 dwa przypisy | POTWIERDZONE | L889 `"Dane wstępne: V. Strand (materiały niepublikowane)."` | → E01-27 |
| §7.6 arytmetyka P4 | POTWIERDZONE | L885 `To są jej wyniki. Jej metodologia. Jej pięć lat pracy` | → E01-09 |
| §7.7 TVN24 vs Berlin | POTWIERDZONE | L773 `hospitalizowanych. Samo leczenie objawowe nie daje efektów.` | → E01-06 |
| §7.9–7.10 sc. 11, dwóch Marków | POTWIERDZONE | L1016 `I Marek też nie będzie. I Kacper powiedział, że...` | → E01-20 |
| §7.11 zaimek | POTWIERDZONE | L958 `On jest zdrowy. Ma gorączkę, ale powiedzieli, że to nie...` | → E01-43 |
| §7.12 Pappa/Tata | ZAWĘŻONE | L513 `AGA (po norwesku -- napisy polskie)`; L654 `Tata dzwonił. Pyta, czy przyjdę w sobotę na obiad.` | „Pappa” w kwestii norweskiej, „Tata” w polskiej; nie sprzeczność |
| §7.13 rzecznik WHO | POTWIERDZONE | L1194 `RZECZNIK WHO (po angielsku -- napisy polskie)` | — |
| §7.14 BSL-4 / P3 | ZAWĘŻONE | L266 `w kombinezonie P3. Przed nią na blacie: fiolka z bezbarwnym płynem.` | merytoryka NIEPOTWIERDZONE |
| §7.15 rs1799945 | ZAWĘŻONE | L447 `Masz rację. Diabeł tkwi w wariancie rs1799945.` | genetyka NIEPOTWIERDZONE |
| §7.16 hotel | POTWIERDZONE | L1183 `Vera w anonimowym hotelu w Oslo. Telewizor. Mapa świata.` | — |
| §7.17 krzesło/fotel | POTWIERDZONE | L1208 `Sweter Michała leży na fotelu.` | — |
| §7.18 sc. 15 w E01 czy E02 | ZAWĘŻONE | L1263 `KONIEC ODCINKA 1` | sc. 15 kończy E01; E02 ma prolog T+9 (E02:L54 `T PLUS 9`, na podstawie fragmentu) |
| §8 „Mamma/Pappaaaaa — ujednolicić” | ZAWĘŻONE | L520 `Pappaaaaa. Jutro park?` | przeciągnięcie to celowa mowa dziecka; poprawność pisowni norweskiej: NIEPOTWIERDZONE (audyt twierdził „poprawne”) |
| §8 pozostałe uwagi językowe | POTWIERDZONE | L377 `Izolacja wygląda na R-17 jak myśleliśmy. Mogę naprawić` | → E01-45 |
| §9 długie kwestie, TTS | NIEZBADANE (produkcja, bez wagi) | — | poza zakresem tematu |
| §10 założenia (Piotr, teczka, Paweł, Dąbrowski, Michał) | POTWIERDZONE | L1119 `O czwartej czternaście.` | → E01-04, -11, -12, N-08 |
| §10 wyzwalacze: P2 = „tata” (L396), P3 = teczka (L583) | ZAWĘŻONE | L417 `"Aga, jutro możesz pogadać? Przepraszam, że znowu`; L602 `Mam trochę gardło ale pewnie z klimy. Jutro normalnie tak?"` | bezpośrednio przed P2 jest SMS do Agi, przed P3 SMS Michała → E01-18 |
| §11 ryzyka produkcyjne, prawo | NIEZBADANE (produkcja, bez wagi) | — | instytucje realne w tekście: L593 (TVN), L1187 (ESA), L292 (Szpital Bielański); ocena prawna NIEPOTWIERDZONE |
| §12 pytania 1–7 | wchodzą do listy decyzji (sekcja f) | — | — |

### c4. Notatki `E01_beaty_i_rozpiska.md` (tylko twierdzenia o scenariuszu)

| Ustalenie | Status | Cytat i linia | Uwagi |
|---|---|---|---|
| A: czasy deklarowane scen | POTWIERDZONE | L1048 `SCENA 12  [CZAS: ok. 5 min]` (fragment `SCENA 12`) | wszystkie 23 wartości zgodne z moją tabelą |
| B: 3630 s = 60:30 | POTWIERDZONE | — | 60,5 × 60 = 3630 |
| C6: W3 09:47 vs sc. 10 | POTWIERDZONE | L986 `Po wczoraj: nic.` | → E01-07 |
| C8: WT T-10 po sc. 4 | POTWIERDZONE | L351 `WSTAWKA MEDIALNA -- T MINUS 10 DNI` | wstawka stoi po sc. 4 (L292–L350) |
| D1: P3 ma „Aga.” i „Co?” | POTWIERDZONE | L741 `Co?` | brakuje ich w beatach (pliku beatów nie badano) |
| D2: P1 „Pan profesor…” | POTWIERDZONE | L213 `Departament wirusologii. Pan profesor... pan jest` | — |
| D3: sc. 8 „trzeci przypadek” to narracja | POTWIERDZONE | L833 `Trzeci przypadek w Berlinie. Vera wie, co to znaczy.` | — |
| D4: sc. 5 „I co? Przypomina?” | POTWIERDZONE | L402 `I co? Przypomina?` | — |
| D5: W2 bez głosu prezenterki | POTWIERDZONE | L593 `Pasek TVN: "WIRUS Y (HYV-1): ŚMIERTELNOŚĆ U MĘŻCZYZN WYSOKA -- WHO POTWIERDZA"` | W2 (L588–L603) ma tylko paski i SMS |
| D7: czarnego ekranu nie ma w sc. 8 | POTWIERDZONE | grep „Czarny ekran”: L1179, L1211, L1224, L1260 | żaden w sc. 8 (L806–L836) |
| D8: „T MINUS 14 DNI” | POTWIERDZONE | L289 `Napis: T MINUS 14 DNI` | — |
| C1–C5, C7, C9–C10, N1–N4, E, F, G (pliki beatów i rozpiski) | NIEZBADANE (pliki produkcyjne poza allowlistą lektury; bez wagi KRYT/WYS) | — | — |

### c5. Notatki `decyzje_i_konsultacje.md` (w części o E01)

| Ustalenie | Status | Cytat i linia | Uwagi |
|---|---|---|---|
| 2a.5 oś Very/Agi (24/35/49/52/64) | POTWIERDZONE | L431 `Napis: "WARSZAWA. OK. 11 LAT PO PRZYJEŹDZIE."`; L615 `Napis: "WARSZAWA. OK. 25 LAT PO PRZYJEŹDZIE."` | — |
| 2b E01: „ADAM-1” → „wirus Y” | POTWIERDZONE | L593 `Pasek TVN: "WIRUS Y (HYV-1): ŚMIERTELNOŚĆ U MĘŻCZYZN WYSOKA -- WHO POTWIERDZA"` | grep „ADAM-1”: brak |
| 2b E01: kryptonim „Adam” na tablicy | POTWIERDZONE | L919 `Jedno słowo: "Adam."` | — |
| 2b E01: zasiać przyjaźń Marta–Aga | ZAWĘŻONE | L164 `Słuchaj -- ta koleżanka Agi Bryk ze studiów, Marta` | wdrożone, ale nieczytelne → E01-10 |
| 2b E01: metraż ~52 + 62 s | ZAWĘŻONE (niewdrożone) | L3 `Format: ok. 60 minut` | → E01-30 |
| §3 napisy P1–P4 wdrożone | POTWIERDZONE | L186, L431, L615, L869 (cytaty w N-09) | — |
| §4e A5, A6 otwarte | POTWIERDZONE | L1079, L164 | — |
| K3 metraż E01 | POTWIERDZONE (sprzeczność dokumentów) | L3 `Format: ok. 60 minut` | — |
| K15 kolizja „Tomasz” | ZAWĘŻONE | L44 (fragment `35 lat. Podwładny Marty w PSE.`) | w E01 tylko „Tomek”; kolizja dotyczy innych odcinków |
| Załącznik A (linie E01) | POTWIERDZONE (próba: L3, L164, L593, L932, L1079, L1195, L273, L919) | L932 `Na pasku: "WIRUS Y (HYV-1): WHO POTWIERDZA -- ŚMIERTELNOŚĆ 100% U MĘŻCZYZN."` | — |
| pozostałe (Flow, Kling, E03, E02) | NIEZBADANE (poza E01; bez wagi) | — | — |

---

## (d) TIMING

### d1. Tabela czasów scen

Źródła w pliku: (1) etykiety `[CZAS: ok. X min]` przy każdym segmencie; (2) nagłówek L3 `Format: ok. 60 minut`; (3) **tabeli czasów w pliku nie ma** (grep „tabela/suma/razem”: tylko słowo „razem” w L69, L119, L436, w innym znaczeniu). Kolumna „tabela czasów” ma więc wartość „brak”.

Start = suma etykiet poprzednich segmentów (mm:ss).

| # | Segment | Linia nagłówka | T / godzina | CZAS (etykieta) | Tabela czasów | Start | Koniec |
|---|---|---|---|---|---|---|---|
| 1 | Sc. 1 | L62 | brak T (ranek) | 3,5 | brak | 0:00 | 3:30 |
| 2 | Sc. 2 | L126 | brak T („TO SAMO RANO”, środa L150) | 1,5 | brak | 3:30 | 5:00 |
| 3 | P1 | L181 | przeszłość, „40 LAT WCZEŚNIEJ” | 4 | brak | 5:00 | 9:00 |
| 4 | Sc. 3 | L257 | T-14 | 2,5 | brak | 9:00 | 11:30 |
| 5 | Sc. 4 | L292 | T-9, ranek | 3 | brak | 11:30 | 14:30 |
| 6 | W1 | L351 | T-10 | 0,75 | brak | 14:30 | 15:15 |
| 7 | Sc. 5 | L369 | T-9, popołudnie | 2 | brak | 15:15 | 17:15 |
| 8 | P2 | L427 | przeszłość, „OK. 11 LAT PO PRZYJEŹDZIE” | 4 | brak | 17:15 | 21:15 |
| 9 | Sc. 6 | L531 | T-9, popołudnie | 2 | brak | 21:15 | 23:15 |
| 10 | W2 | L588 | T-7, SMS 18:23 | 1 | brak | 23:15 | 24:15 |
| 11 | P3 | L611 | przeszłość, „OK. 25 LAT PO PRZYJEŹDZIE” | 5 | brak | 24:15 | 29:15 |
| 12 | Sc. 7 | L765 | T-7, wieczór | 3 | brak | 29:15 | 32:15 |
| 13 | Sc. 8 | L806 | T-8, wieczór | 1,5 | brak | 32:15 | 33:45 |
| 14 | W3 | L837 | T-5, SMS 09:47 | 1 | brak | 33:45 | 34:45 |
| 15 | P4 | L865 | przeszłość, „DWA LATA PO WYJEŹDZIE” | 3,5 | brak | 34:45 | 38:15 |
| 16 | Sc. 9 | L926 | T-6, wieczór | 3 | brak | 38:15 | 41:15 |
| 17 | Sc. 10 | L975 | T-5, popołudnie | 2,5 | brak | 41:15 | 43:45 |
| 18 | Sc. 11 | L1005 | T-4, ranek | 3,5 | brak | 43:45 | 47:15 |
| 19 | Sc. 12 | L1048 | T-2, noc | 5 | brak | 47:15 | 52:15 |
| 20 | Sc. 13 | L1106 | T-1, świt, zgon 04:14 | 2 | brak | 52:15 | 54:15 |
| 21 | W4 | L1140 | T-1 | 0,75 | brak | 54:15 | 55:00 |
| 22 | Sc. 14 Zero Day | L1157 | T0 | 4 | brak | 55:00 | 59:00 |
| 23 | Sc. 15 Statek widmo | L1226 | T+8, świt | 1,5 | brak | 59:00 | 60:30 |

**Sumy (składniki wypisane):**
- Sceny teraźniejszości 1–15: 3,5 + 1,5 + 2,5 + 3 + 2 + 2 + 3 + 1,5 + 3 + 2,5 + 3,5 + 5 + 2 + 4 + 1,5 = **40,5 min**.
- Bloki przeszłości: P1 4 + P2 4 + P3 5 + P4 3,5 = **16,5 min**.
- Wstawki: W1 0,75 + W2 1 + W3 1 + W4 0,75 = **3,5 min**.
- **Razem: 40,5 + 16,5 + 3,5 = 60,5 min.**
- Kontrola: suma 23 etykiet policzona skryptem (regex na `[CZAS: ok. X min]`) = 60,5; liczba etykiet = 23.

**Rozbieżności:**
- Nagłówek L3 (60) vs suma etykiet (60,5): różnica +0,5 min. Mieści się w „ok.”, ale nagłówek warto podać jako „ok. 60,5 minut” albo docelowy.
- Tabela czasów: brak w pliku, więc nie ma z czym porównywać. Suma nagłówków scen = suma etykiet (etykiety są w nagłówkach).
- Źródła poza plikiem (rząd 2 i 4): handoff H42 „~65 min”; decyzje „~52 min + czołówka 62 s”; według notatek beatów rozpiska ma 22 pozycje (59:00) bez sc. 15. To nie są rozbieżności wewnątrz scenariusza (E01-30).

### d2. Czas ekranowy według dni T (składniki)

| Dzień | Segmenty | Minuty |
|---|---|---|
| bez T | sc. 1 3,5 + sc. 2 1,5 | 5 |
| T-14 | sc. 3 | 2,5 |
| T-10 | W1 | 0,75 |
| T-9 | sc. 4 3 + sc. 5 2 + sc. 6 2 | 7 |
| T-8 | sc. 8 | 1,5 |
| T-7 | W2 1 + sc. 7 3 | 4 |
| T-6 | sc. 9 | 3 |
| T-5 | W3 1 + sc. 10 2,5 | 3,5 |
| T-4 | sc. 11 | 3,5 |
| T-2 | sc. 12 | 5 |
| T-1 | sc. 13 2 + W4 0,75 | 2,75 |
| T0 | sc. 14 | 4 |
| T+8 | sc. 15 | 1,5 |
| przeszłość | P1 4 + P2 4 + P3 5 + P4 3,5 | 16,5 |
| **Razem** | 5 + 2,5 + 0,75 + 7 + 1,5 + 4 + 3 + 3,5 + 3,5 + 5 + 2,75 + 4 + 1,5 + 16,5 | **60,5** |

Dni bez scen: T-13, T-12, T-11, T-3, T+1…T+7.

### d3. Analiza rytmu

**Proporcje bloków.** Teraźniejszość 40,5 / 60,5 = 66,9%; przeszłość 16,5 / 60,5 = 27,3%; wstawki 3,5 / 60,5 = 5,8%. Przeszłość zajmuje więcej niż jedną czwartą odcinka. Bloki P są rozmieszczone w 5:00, 17:15, 24:15 i 34:45. Od 38:15 do końca (22:15 min) nie ma żadnego bloku przeszłości, więc druga połowa jest jednotorowa. To dobrze służy przyspieszeniu końca.

**Gęstość dialogu (przybliżenie).** Słowa w kwestiach dialogowych liczone skryptem (linie z wcięciem pod nazwą postaci; metoda przybliżona, bez paska TV i SMS-ów): segmenty 0:00–32:15 (sc. 1 – sc. 7) ok. 704 słowa; segmenty 32:15–60:30 (sc. 8 – sc. 15) ok. 204 słowa. Segmenty bez dialogu albo prawie bez: sc. 3 (3 słowa), W2 (0), sc. 8 (0), P4 (1), sc. 10 (0), sc. 14 (16), sc. 15 (0). Druga połowa jest prawie niema. To spójne z tonem („w kolejkach i ciszy”), ale niesie ryzyko statyki i przenosi ciężar na obraz i muzykę.

**Długie odcinki statyczne.**
1. 0:00–9:00: normalność bez zagrożenia (sc. 1, sc. 2, P1). Najdłuższy fragment bez haka (N-05).
2. 11:30–21:15: dolina średniego napięcia (sc. 4 → W1 → sc. 5 → P2). Przez prawie 10 minut napięcie spada z 4 do 2 (sekcja e).
3. P3 24:15–29:15: najdłuższy segment odcinka (5 min) w miejscu pierwszego osobistego zagrożenia (N-06).
4. 32:15–43:45: pięć segmentów (sc. 8, W3, P4, sc. 9, sc. 10), z których trzy to sceny jednej postaci w samotności (Vera L806–L835, Vera L865–L923, Karolina L975–L1002). Ok. 54 słowa dialogu w 11,5 min.
5. Sc. 12 (5 min przy ok. 50 słowach): najdłuższa scena teraźniejszości, statyczna z założenia (OIT). Uzasadniona dramaturgicznie, ale przy 5 minutach to ponad 8% odcinka w jednym pokoju.

**Przyspieszenia i zwolnienia.**
- Zwolnienie: dzień T-9 trwa 7 minut ekranowych (sc. 4, 5, 6), plus 4-minutowy P2 w środku. Najwolniejszy dzień odcinka, a dzieje się w nim tylko rozpoznanie wysypki i telefon o Ares IV.
- Przyspieszenie: od sc. 11 (T-4) skoki osi robią się większe (T-4 → T-2 → T-1 → T0) przy coraz krótszych segmentach (3,5 → 5 → 2 → 0,75 → 4). Sc. 12 (5 min) hamuje to przyspieszenie, ale celowo, jako ostatnia „cisza przed”.
- Wstawki W1–W4 (0,75–1 min) działają jak metronom co ok. 9–10 minut (14:30, 23:15, 33:45, 54:15). Między W3 a W4 jest 20,5 minuty przerwy: eskalacja medialna zamiera dokładnie w strefie osobistych strat.
- Koniec: sc. 14 (4 min) + sc. 15 (1,5 min) = 5,5 min po kulminacji. Trzy czarne ekrany (L1211, L1224, L1260) dzielą to na trzy zakończenia (N-03).

**Wnioski.** (1) Metraż jest za ciężki na początku (9 min do pierwszego haka) i w środku (T-9 oraz P3). (2) Druga połowa jest dobrze przyspieszona osią T, ale prawie niema. (3) Sc. 14 jest za krótka jak na kulminację, która ma udźwignąć 6 wątków i 13 ujęć (L1162–L1222). (4) Bez skrótów brakuje miejsca na beaty z E01-04, E01-12 i N-08.

### d4. PROPOZYCJA metrażu per scena

Założenia (PROPOZYCJA): kolejność według E01-08 i E01-18 (P1 po sc. 3, W1 przed sc. 4, sc. 8 przed sc. 7, sc. 9 przed W3); cel ok. 60 min z czołówką i napisami (decyzja D-09).

| Segment | Obecnie | PROPOZYCJA | Zmiana i powód |
|---|---|---|---|
| Sc. 1 | 3,5 | 2,5 | −1; normalność czytelna szybciej (N-05) |
| Sc. 2 | 1,5 | 2 | +0,5; nowe brzmienie L164–L165 (E01-10), więcej tekstu niż czasu (ok. 51 słów + dużo akcji w 1,5 min) |
| Sc. 3 | 2,5 | 2,5 | bez zmian (pierwszy hak w 4:30) |
| P1 | 4 | 3 | −1; po sc. 3 ma wyzwalacz, wystarcza krócej |
| W1 | 0,75 | 0,75 | przed sc. 4 |
| Sc. 4 | 3 | 3 | bez zmian |
| Sc. 5 | 2 | 2 | + insert Piotra (E01-11) |
| P2 | 4 | 3,5 | −0,5; po scaleniu połówek (E01-03) |
| Sc. 6 | 2 | 2,5 | +0,5; kwestie „Piotr?” / „Cała załoga.” (E01-11) |
| W2 | 1 | 1 | bez zmian |
| P3 | 5 | 4 | −1; skrót korytarza (N-06) |
| Sc. 8 | 1,5 | 2 | +0,5; przed sc. 7, sygnał, że Dąbrowski żyje (E01-12 wariant 3, opcjonalnie) |
| Sc. 7 | 3 | 3 | bez zmian |
| P4 | 3,5 | 3 | −0,5; po sc. 7, w pobliżu wydruku |
| Sc. 9 | 3 | 2,5 | −0,5; przed W3 |
| W3 | 1 | 1 | bez zmian |
| Sc. 10 | 2,5 | 2 | −0,5 |
| Sc. 11 | 3,5 | 2,5 | −1; scena organizacyjna |
| Sc. 12 | 5 | 4 | −1 |
| Sc. 13 | 2 | 2 | bez zmian |
| W4 | 0,75 | 1 | +0,25; kwestia premiera (E01-28) |
| Sc. 14 | 4 | 5 | +1; ujęcia teczki (E01-04), Dąbrowskiego (E01-12), telefonu Karoliny (N-08) |
| Sc. 15 | 1,5 | 2 | +0,5; „cisza dłużej, niż jest wygodnie” (L1258) potrzebuje czasu |

**Suma PROPOZYCJI:** 2,5 + 2 + 2,5 + 3 + 0,75 + 3 + 2 + 3,5 + 2,5 + 1 + 4 + 2 + 3 + 3 + 2,5 + 1 + 2 + 2,5 + 4 + 2 + 1 + 5 + 2 = **56,75 min**. Teraźniejszość: 2,5 + 2 + 2,5 + 3 + 2 + 2,5 + 2 + 3 + 2,5 + 2 + 2,5 + 4 + 2 + 5 + 2 = 39,5; przeszłość: 3 + 3,5 + 4 + 3 = 13,5 (23,8%); wstawki: 0,75 + 1 + 1 + 1 = 3,75. Kontrola: 39,5 + 13,5 + 3,75 = 56,75. Zapas do 60 min (ok. 3,25 min) przeznaczony na czołówkę i napisy (ich długość to decyzja właściciela). Pierwszy hak przypada wtedy na 4:30, a nie na 9:00.

---

## (e) NAPIĘCIE

### e1. Kotwice skali 0–10

- **0** — świat bez zagrożenia i bez otwartego pytania: czysta codzienność, nic nie wiadomo i nic się nie zapowiada.
- **2–3** — tajemnica albo drobny niepokój bez wskazanego zagrożenia (rekwizyt bez wyjaśnienia, dziwne pytanie, konflikt rodzinny bez stawki życia).
- **5** — zagrożenie nazwane, które dotyka bezpośrednio bliskiej osoby bohatera; wynik otwarty, nikt jeszcze niczego nie stracił.
- **7–8** — utrata bliskiej osoby w toku albo dokonana (jedna postać lub jeden wątek), przy świadomości, że zagrożenie rośnie.
- **10** — nieodwracalna katastrofa potwierdzona na ekranie, dotykająca wszystkich głównych postaci naraz, bez nadziei w obrębie odcinka.

Ocena dotyczy wyłącznie wiedzy widza w danym miejscu kolejności pliku (nie chronologii T).

### e2. Krzywa napięcia scena po scenie (100% segmentów, kolejność pliku)

| # | Segment | Ocena | Zdarzenie z tekstu (cytat, linia) i uzasadnienie |
|---|---|---|---|
| 1 | Sc. 1 | 1 | L88 `Zwykła, młoda, prosta chwila. Nic się nie zapowiada.` Napięcie tylko z gatunku i tytułu; brak pytania w scenie. |
| 2 | Sc. 2 | 2 | L156 `Widz ją widzi przez chwilę. Nie wie jeszcze, co to.`; L167 `TOMEK (nie rozumiejąc pytania)`. Pierwsza tajemnica (teczka) i niezrozumiałe pytanie. |
| 3 | P1 | 1 | L251 `W takim razie -- zaczynamy.` Spotkanie bez konfliktu. Ziarno L225 `Twój projekt doktorski -- chromosom Y, mechanizmy` działa dopiero wstecz. |
| 4 | Sc. 3 | 6 | L276 `z kieszeni żółtą karteczkę samoprzylepną. Zasłania obiektyw.`; L287 `Fiolka jest pusta.` Celowy, ukryty czyn i nieznana substancja; pierwszy chłód (L261). |
| 5 | Sc. 4 | 4 | L331 `Wszyscy mężczyźni?`; L348 `Nie wiem jeszcze. Dlatego pytam.` Widz łączy fiolkę z chorobą mężczyzn; zagrożenie nazwane, ale anonimowe. |
| 6 | W1 | 4 | L358 `Światowa Organizacja Zdrowia zwołała dziś nadzwyczajne`; L366 `Gospodarka. Wybory lokalne w Austrii. Normalność.` Skala międzynarodowa, celowo wyciszona. |
| 7 | Sc. 5 | 3 | L396 `i Michał powiedział, że mu przypomina tatę.`; L413 `Ale ta chwila została. Widz to widział.` Ciepła scena z cieniem nieobecnego ojca; brak zagrożenia. |
| 8 | P2 | 2 | L514 `Mamma! Pappa powiedział, że możemy jutro do parku!` Duży przyrost informacji (Aga to córka Very), ale brak zagrożenia. Napięcie przenosi się w ironię (sekcja e4). |
| 9 | Sc. 6 | 5 | L569 `Ares IV milczy od czterdziestu ośmiu godzin.`; L582 `Tylko raz -- przez jedną sekundę -- patrzy na szafę`. Zagrożenie dla bliskiej osoby Marty. Bez imienia Piotra (E01-11) czyta się jako 5, nie 6. |
| 10 | W2 | 6 | L594 `Pasek TVN24: "WIRUS Y -- ŚMIERTELNOŚĆ BLISKA 100% U HOSPITALIZOWANYCH MĘŻCZYZN"`; L602 `Mam trochę gardło ale pewnie z klimy. Jutro normalnie tak?"` Pierwszy objaw u postaci, którą widz polubił w sc. 1. |
| 11 | P3 | 3 | L684 `Nie chcę wyjaśnień. Chcę wiedzieć, czy to już koniec.`; L750 `Wrócisz?` Mocny konflikt rodzinny, ale bez związku ze stawką teraźniejszości. Najgłębszy spadek (−3). |
| 12 | Sc. 7 | 7 | L787 `Ktoś to zaprojektował.`; L796 `Żywy. Rozmawia z rezydentką, gestykuluje, tłumaczy.` Aga patrzy na męża, który jest w grupie ryzyka; widz wie, kto „zaprojektował”. |
| 13 | Sc. 8 | 6 | L828 `Kciuk przy przycisku. Nie naciska.`; L834 `Tylko ona wie.` Sprawczyni waha się, czy ostrzec córkę. Lekki spadek względem sc. 7, ale wysoka ironia. |
| 14 | W3 | 7 | L846 `stuprocentowej. Wirus rozpoznaje sekwencję`; L854 `"Jestem w szpitalu, to pewnie nic. Przyjdź dzisiaj?"`; L856 `Sygnał. Sygnał. Poczta głosowa.` Michał w szpitalu, brak kontaktu. |
| 15 | P4 | 4 | L901 `Moje.`; L919 `Jedno słowo: "Adam."` Domknięcie motywu: wartość informacyjna wysoka, napięcie fabularne spada (−3) zaraz po W3. |
| 16 | Sc. 9 | 6 | L949 `Czy to jest...`; L958 `On jest zdrowy. Ma gorączkę, ale powiedzieli, że to nie...` Wyparcie Karoliny. Napięcie obniżone, bo widz wie więcej z W3 (N-04). |
| 17 | Sc. 10 | 7 | L989 `Automat: "Numer jest chwilowo niedostępny."`; L999 `Nie zakłada. Tylko trzyma.` Cisza po Michale; sweter jako zapowiedź żałoby. |
| 18 | Sc. 11 | 6 | L1018 `Beata urywa. Patrzą na siebie.`; L1020 `Nie trzeba kończyć zdania.` Zagrożenie dotyka całego zespołu Marty, ale scena jest organizacyjna. |
| 19 | Sc. 12 | 8 | L1097 `Zostań.`; L1103 `Monitor bije. Bije. Bije.` Umierający mąż głównej bohaterki; widz wie, że jego śmierć to dzieło matki Agi. |
| 20 | Sc. 13 | 8 | L1119 `O czwartej czternaście.`; L1130 `Policz. I przygotuj drugie piętro -- będziemy` Strata dokonana; Aga wraca do pracy. Napięcie utrzymane przez skalę („drugie piętro”). |
| 21 | W4 | 8 | L1142 `Kilka kanałów wyłączyło się bez wyjaśnienia. Zostały trzy.`; L1148 `Ogłaszam stan wyjątkowy na terenie całego kraju.` Rozpad infrastruktury informacji i państwa. |
| 22 | Sc. 14 | 10 | L1196 `sto procent. Nie odnotowano żadnego przypadku przeżycia.`; L1188 `Miga ekran: "ARES IV -- SIGNAL INTERRUPTED."`; L1219 `To niemożliwe.` Katastrofa globalna, dotyka wszystkich wątków naraz. |
| 23 | Sc. 15 | 8 | L1251 `GAZOPORT. Nikt tego nie czyta. Statek sam pamięta, dokąd miał płynąć.`; L1258 `Cisza trzyma się dłużej, niż jest wygodnie.` Po kulminacji nowe, konkretne zagrożenie: hak na E02. |

Kształt krzywej (kolejność pliku): 1, 2, 1, 6, 4, 4, 3, 2, 5, 6, 3, 7, 6, 7, 4, 6, 7, 6, 8, 8, 8, 10, 8.

### e3. Miejsca spadku napięcia

| Miejsce | Spadek | Przyczyna (cytat) | PROPOZYCJA |
|---|---|---|---|
| Sc. 2 → P1 (3:30–9:00) | 2 → 1 | P1 bez wyzwalacza; L251 `W takim razie -- zaczynamy.` | P1 po sc. 3 (N-05) |
| Sc. 3 → … → P2 (11:30–21:15) | 6 → 4 → 4 → 3 → 2 | dolina T-9; L366 `Gospodarka. Wybory lokalne w Austrii. Normalność.` | W1 przed sc. 4; sc. 5 krótsza o wątek wystawy (E01-21) albo z insertem Piotra |
| W2 → P3 (24:15) | 6 → 3 | najdłuższy blok po pierwszym objawie Michała (L602) | N-06: skrót P3 i most |
| W3 → P4 (34:45) | 7 → 4 | po L856 `Sygnał. Sygnał. Poczta głosowa.` przeskok do Oslo w przeszłości | E01-18 wariant 2: P4 bezpośrednio po wydruku (sc. 8); W3 tuż przed sc. 10 |
| Sc. 7 → sc. 8 | 7 → 6 | cofnięcie T-7 → T-8 i nagłówek L813 o „trzecim przypadku” | E01-08, E01-22 |
| W3 → sc. 9 | 7 → 6 | widz wie więcej niż Karolina, ale „do tyłu” (N-04) | sc. 9 przed W3 |
| montaż L1211 | fałszywy koniec | L1211 `Czarny ekran.` przed kwestią L1219 | N-03 |

### e4. Dwutorowość: czy bloki przeszłości podbijają, czy rozwadniają napięcie

- **Lokalnie rozwadniają.** Każdy blok P obniża krzywą o 1–3 punkty (P1: 1 po 2; P2: 2 po 3; P3: 3 po 6; P4: 4 po 7). Najkosztowniejsze są P3 i P4, bo przerywają dwa szczyty wątku Michała (W2, W3).
- **Globalnie podbijają przez ironię dramatyczną.** P1 i P2 dają widzowi mechanizm (L225, L442), więc sc. 7 nie jest odkryciem, tylko grozą rozpoznania. P2 i P3 dają widzowi wiedzę, że Aga jest córką Very (L514, L640). Od tej chwili sc. 7 (Aga przy szybie, L796), sc. 8 (kciuk nad kontaktem „Aga”, L828), sc. 12 i sc. 13 (śmierć Pawła) oraz sc. 14 (Aga nad sekwencjami, L1214–L1219) grają podwójnie: Aga walczy z dziełem własnej matki, a matka patrzy na zdjęcie wnuczek. P3 (L750 `Wrócisz?`; L754 `Zadzwonię, kiedy dojadę.`) jest bezpośrednim kluczem do sc. 8 (Vera nie dzwoni). P4 (L901 `Moje.`) zamienia krzywą „Adam” z sc. 3 (L273) w motyw.
- **Wniosek.** Bloki przeszłości są w tej strukturze niezbędne, ale za długie i źle wpięte w miejsca szczytów. Wiedza widza o tym, że Aga jest córką Very, jest silnikiem napięcia drugiej połowy. Dlatego rekomendacja do E01-01 to wariant 1 (ironia), a nie tajemnica. Przy wariancie 2 (tajemnica) bloki P2 i P3 tracą funkcję, a sceny 7, 8, 12, 13 i 14 spadają o 1–2 punkty (ocena ekspercka, nie pomiar).

### e5. Mapa informacji w kluczowych punktach

| Punkt (czas) | Co wie widz | Marta | Aga | Vera | Karolina |
|---|---|---|---|---|---|
| Po sc. 3 (11:30) | Kobieta w Oslo (z obsady: Vera, twórczyni wirusa) celowo opróżniła fiolkę i zasłoniła kamerę; projekt „Adam” | nic | nic | wszystko (L834 `Tylko ona wie.` pada później, ale stan wiedzy już ten) | nic |
| Po sc. 4 (14:30) | choroba dotyka tylko mężczyzn; widz łączy ją z sc. 3 | nic | „anomalia”, mężczyźni (L331) | wszystko | nic |
| Po P2 (21:15) | Aga (imię) to córka Very i Marka; Vera pracowała nad selekcją XY (L442) | nic | nic | wszystko | nic |
| Po sc. 6 (23:15) | Ares IV milczy; Marta coś ukrywa w teczce. Nie wie, że chodzi o męża (E01-11) | Ares milczy (L569) | — | — | — |
| Po sc. 7 (32:15) | wirus jest zaprojektowany, a widz wie przez kogo | — | „Ktoś to zaprojektował” (L787); coś przeczuwa (L803) | wszystko | Michał ma objawy (W2) |
| Po sc. 8 (33:45) | pewność: dorosła Aga to córka Very; Vera ma wnuczki i nie ostrzega córki (L828) | — | nie wie o matce w tym kontekście | wie i milczy | — |
| Po P4 (38:15) | motyw: kradzież badań, „Moje.”, „Adam” | — | — | — | — |
| Po sc. 13 (54:15) | Paweł nie żyje (04:14); Michał prawdopodobnie też (sugestia) | zespół choruje | mąż nie żyje | — | brak kontaktu z Michałem |
| Po sc. 14 (59:00) | 100% śmiertelności; sygnał Ares przerwany; Aga coś odkrywa w sekwencjach | Ares przerwany (ekran ESA widzi widz, nie Marta) | „To niemożliwe” (L1219), treść odkrycia nieznana | „pustka” (L1184) | — |

**Zbyt wczesne ujawnienia (wiedza widza vs postaci):**
1. **Sprawczyni w 9. minucie** (sc. 3). To celowy suspens (bomba pod stołem), nie błąd, ale pytanie „kto?” znika na cały serial. Napięcie musi więc pochodzić z pytania „czy Aga się dowie i kiedy”. Tego pytania E01 jawnie nie stawia (brak sceny, w której Aga jest blisko prawdy, poza L1219).
2. **Aga jako córka Very w 21. minucie (P2), pewność w 33. minucie (sc. 8)**: sprzeczne z notą (E01-01). Dramaturgicznie korzystne (e4).
3. **Mechanizm „chromosom Y” w 5. minucie (P1) i 18. minucie (P2)** przed ogłoszeniem w sc. 7 (N-07): sc. 7 traci wartość odkrycia, zyskuje ironię.
4. **„100%” na T-7 i T-6** (E01-06): kulminacja T0 nie dokłada informacji.
5. **Michał w szpitalu (W3) przed wyparciem Karoliny (sc. 9)** (N-04).

### e6. Kandydaci na cliffhangery

| Kandydat | Cytat i linia | Siła | Uwagi i PROPOZYCJA |
|---|---|---|---|
| Statek widmo płynie na gazoport | L1251 `GAZOPORT. Nikt tego nie czyta. Statek sam pamięta, dokąd miał płynąć.` | najwyższa (konkretne, przyszłe zagrożenie) | zostawić jako ostatni obraz; dać 2 min (d4); poprawić notę (E01-04) |
| Aga: „To niemożliwe.” | L1219 `To niemożliwe.` | wysoka, jeśli odkrycie jest osobiste (E01-32 wariant 1); niska, jeśli to tylko „zaprojektowany” (już znane z L787) | usunąć fałszywy koniec L1211 (N-03); rozstrzygnąć, co jest drugą sekwencją |
| Vera patrzy na dłonie | L1222 `Patrzy na własne dłonie.` | średnia | z ujęciem nekrologu Dąbrowskiego (E01-12) rośnie do wysokiej |
| Ares IV: „SIGNAL INTERRUPTED” | L1188 `Miga ekran: "ARES IV -- SIGNAL INTERRUPTED."` | średnia; obecnie osłabiona brakiem imienia Piotra i sprzecznością osi | E01-02 + E01-11 |
| Teczka Marty | L583 `gdzie leży żółta teczka.` | niska w E01 (nie wraca w montażu) | jedno ujęcie w montażu (E01-04 wariant 2) |
| Śródodcinkowy: Ares IV milczy | L569 `Ares IV milczy od czterdziestu ośmiu godzin.` | średnia | mocny hak w 23. minucie po dodaniu „Piotr?” |
| Śródodcinkowy: poczta głosowa Michała | L856 `Sygnał. Sygnał. Poczta głosowa.` | wysoka | nie przerywać od razu blokiem P4 (e3) |

### e7. Otwarcie i zakończenie

- **Otwarcie.** Sc. 1 dobrze ustawia stawkę (sweter z dinozaurem jako przyszły symbol żałoby, L73, wraca w L994, L1180, L1208), ale razem ze sc. 2 i P1 daje 9 minut bez zagrożenia. Ironia zaczyna działać dopiero, gdy widz wie, co nadchodzi. PROPOZYCJA: P1 po sc. 3 i skrót sc. 1 (N-05), opcjonalnie 10–15-sekundowy teaser z sc. 3.
- **Zakończenie.** Montaż Zero Day ma właściwy materiał (globalne, zawodowe i osobiste ujęcia, L1162–L1222), ale (1) trzy czarne ekrany tworzą trzy zakończenia (N-03), (2) Karolina jest pokazana dwa razy tym samym opisem, (3) kulminacja informacyjna („sto procent”) była już na T-6 (E01-06), (4) brak zapowiedzianych beatów (teczka, Dąbrowski, Paweł; E01-04, E01-12). Sc. 15 to bardzo mocny ostatni obraz i hak na E02.

### e8. PROPOZYCJE nowego brzmienia kwestii (ECHO-003, G2; tylko w raporcie)

| Miejsce | Obecnie (cytat) | PROPOZYCJA | Cel |
|---|---|---|---|
| L164–L165 | `Słuchaj -- ta koleżanka Agi Bryk ze studiów, Marta` / `ma na imię jak ja, dzwoniła ostatnio?` | `Słuchaj -- jakby dzwoniła Aga Bryk ze szpitala, to daj mi znać. Od razu.` | czytelny zasiew i pytanie dla widza (E01-10) |
| L559 | `Rozumiem. Przekażę dalej.` | `Rozumiem. Sama powiem córce.` | Piotr jako mąż, nie sprawa służbowa (E01-11) |
| po L570 | — | TOMEK: `Piotr?` / MARTA: `Cała załoga.` | imię Piotra pada w scenie (E01-11) |
| L654 | `Tata dzwonił. Pyta, czy przyjdę w sobotę na obiad.` | `Tata dzwonił. Że znowu wróci późno.` | logika wspólnego domu i podtekst zdrady (E01-05) |
| L885–L886 | `To są jej wyniki. Jej metodologia. Jej pięć lat pracy` / `przed wyjazdem i trzynaście lat przed tym.` | `To są jej wyniki. Jej metodologia. Ćwierć wieku jej pracy.` | arytmetyka (E01-09) |
| L408 | `Tak. Idź oglądać wystawę. Dobranoc kochanie.` | `Tak. Wracajcie ostrożnie. Do wieczora, kochanie.` | pora dnia (E01-21) |
| L1079 | `Dziewczynki są u twojej mamy sąsiadki?` | `Dziewczynki są u Bożeny?` | A5 (E01-14) |
| L594 (pasek) | `Pasek TVN24: "WIRUS Y -- ŚMIERTELNOŚĆ BLISKA 100% U HOSPITALIZOWANYCH MĘŻCZYZN"` | `Pasek TVN24: "WIRUS Y -- ŚMIERTELNOŚĆ ROŚNIE, SZPITALE W EUROPIE ALARMUJĄ"` | rosnąca krzywa (E01-06) |
| L932 (pasek) | `Na pasku: "WIRUS Y (HYV-1): WHO POTWIERDZA -- ŚMIERTELNOŚĆ 100% U MĘŻCZYZN."` | `Na pasku: "WIRUS Y (HYV-1): WHO -- ŚMIERTELNOŚĆ U MĘŻCZYZN PONAD 90%."` | rosnąca krzywa (E01-06) |
| L813 (nagłówek) | `"TAJEMNICZA CHOROBA MĘŻCZYZN -- TRZECI PRZYPADEK W BERLINIE."` | `"TAJEMNICZA CHOROBA MĘŻCZYZN -- SETKI PRZYPADKÓW W NIEMCZECH."` | wiedza świata (E01-22) |
| L447 | `Masz rację. Diabeł tkwi w wariancie rs1799945.` | `Masz rację. Diabeł tkwi w tym jednym wariancie.` | wiarygodność i TTS (E01-25) |
| L1148 | `Ogłaszam stan wyjątkowy na terenie całego kraju.` | `Zwróciłem się do Prezydenta o wprowadzenie stanu wyjątkowego na terenie całego kraju.` | do weryfikacji prawnej (NIEPOTWIERDZONE) (E01-28) |
| L1152 | `Obserwuje go. Wie, co będzie. Czeka.` | `Obserwuje go. Wie, że za chwilę zostanie sama. Czeka.` | bez lektury spisku (E01-44) |
| L1016 | `I Marek też nie będzie. I Kacper powiedział, że...` | `I Jacek też nie będzie. I Kacper powiedział, że...` | kolizja imion (E01-20) |
| L1194 | `RZECZNIK WHO (po angielsku -- napisy polskie)` | `RZECZNICZKA WHO (po angielsku -- napisy polskie)` | rodzaj (E01-33) |
| L282 → po L284 | `Już po wszystkim.` | ta sama kwestia przestawiona za `Otwiera fiolkę. Praca trwa krótko. Zamknięta. Skończone.` | logika czynności (E01-13) |

---

## (f) Kolejność rekomendowanych poprawek (zależności) i decyzje kanoniczne

### f1. Kolejność (PROPOZYCJA)

1. **Decyzje kanoniczne blokujące** (bez nich reszta może się zmienić): D-01 (reveal Agi: od niej zależą E01-32, E01-14, nota L16 i L41, E02 sc. 3), D-02 (oś Ares IV: od niej zależą E01-11 i ujęcie ESA), D-03 (mechanizm uwolnienia: zależy od niej E01-24), D-09 (metraż: od niego zależy d4).
2. **Struktura i kolejność segmentów** (bez nowej treści; przed zmianami dialogów, bo zmienia odwołania): E01-08, E01-18, N-05 (P1 po sc. 3), N-04, N-06 (podział lub skrót P3), N-02.
3. **Oś informacji świata** (paski i nagłówki, bez dialogów): E01-06, E01-22; potem SMS-y Michała E01-07 (zależy od kroku 2).
4. **Logika bloków przeszłości:** E01-03 (D-04), E01-05, E01-09 (razem z E02:L400 w osobnym temacie E02), N-09 (napisy).
5. **Wątki seryjne (małe dopiski):** E01-11 (po D-02), E01-02 (wykonanie wariantu), E01-12 (D-06), E01-04 (nota + ujęcie szafy), E01-10, E01-31, E01-32 (po D-01), N-08 (D-08), E01-16 (D-05).
6. **Rytm końca:** N-03 (po kroku 5, bo montaż dostaje nowe ujęcia).
7. **Kwestie punktowe:** E01-14, E01-20, E01-21, E01-28 (po weryfikacji prawnej), E01-33, E01-34, E01-35, E01-43, E01-44, E01-13 (przestawienie L282).
8. **Fakty i wiarygodność** (z weryfikacją zewnętrzną NIEPOTWIERDZONYCH): E01-23, E01-25, E01-26, E01-27, E01-29, E01-24.
9. **Dokumentacja:** nota (E01-15, E01-17, E01-04), obsada (E01-19, E01-39, E01-40), handoff (E01-41, N-01, §2), N-10.
10. **Na końcu:** backup → edycja (osobny temat poprawek, G4) → regeneracja beatów, rozpiski i PDF → korekta językowa E01-45 bez zmiany treści dialogów.

### f2. Decyzje kanoniczne wymagane od właściciela

| Kod | Pytanie | Warianty (PROPOZYCJE) | Rekomendacja analizy | Punkty |
|---|---|---|---|---|
| D-01 | Czy widz ma wiedzieć już w E01, że Aga jest córką Very? | A ironia w E01 / B tajemnica do E02–E03 / C poszlaka bez pewności | A | E01-01, -14, -32; E02 sc. 3 |
| D-02 | Kiedy zaczyna się milczenie Ares IV i jak liczy je E03? | A od T0 / B awaria T-11, odzyskanie, zerwanie T0 / C ciągłe od T-11 | B | E01-02, -11 |
| D-03 | Co robi Vera w sc. 3 i jak wirus trafia do Warszawy? | A niszczy ostatnią próbkę, uwolnienie wcześniej / B rozsyła / C tajemnica | decyzja autora | E01-13, -24 |
| D-04 | Kiedy Vera i Marek zostali parą (P2)? | A przed P2 (stare małżeństwo) / B w czasie sceny przy tablicy | A z wariantem 2 E01-03 | E01-03 |
| D-05 | Dzień śmierci Pawła | A T-1 (jak jest) / B T0, 04:14 | B | E01-16, -04 |
| D-06 | Czy śmierć Dąbrowskiego ma ujęcie w E01? | A tak, ujęcie z Verą / B tak, z Agą / C nie | A | E01-12 |
| D-07 | Czy Piotr ma imię lub twarz w E01? | A imię w dialogu / B zdjęcie / C oba / D nie | C | E01-11 |
| D-08 | Czy śmierć Michała jest w E01 potwierdzona? | A niedopowiedzenie / B ujęcie ekranu telefonu / C dopiero E02 | B | N-08 |
| D-09 | Docelowy metraż E01 | A 60 / B 65 / C 52–55 (z czołówką?) | A, metraż według d4 | E01-30 |
| D-10 | Reguła językowa Very i Agi | A norweski intymnie, polski publicznie / B wszystko po polsku / C wszystko według sceny | A | E01-15 |
| D-11 | Dąbrowski: mąż czy partner; nazwisko Agi | A partner / B mąż + nazwisko matki | A | E01-39 |
| D-12 | Rok teraźniejszości (epoka bloków P) | podać rok albo „bez roku” | podać rok | E01-26, -25 |
| D-13 | Przyjaźń Marta–Aga: „ze studiów” czy inne źródło | A studia / B akademik / C inne | B | E01-10, -40 |
| D-14 | Sc. 15: logika T+8 i stan załogi | A późne zgony / B kotwicowisko / C T+1–2 | A | E01-29 |
| D-15 | Realne instytucje (PSE, Szpital Bielański, TVN, WHO, ESA, UW) czy fikcyjne | A realne + zastrzeżenie / B fikcyjne | decyzja właściciela (ocena prawna NIEPOTWIERDZONE) | E01-23, -45, notatki §11 |

---

*Koniec raportu. Hash `scenariusze/` po analizie: zob. raport terminalny (sprawdzony `sha256sum` po zapisaniu plików).*
