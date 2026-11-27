# E03 ARES: notatki z przeglądu scenariusza i czytanki PDF

Źródła (tylko odczyt, nic nie zmieniano w R):
- `/tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/zero-unrar/Zero/ZERO_mini_serial_E03_ARES_rev.md` (1932 linie, cały plik przeczytany)
- `/tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/zero-unrar/Zero/ZERO_HANDOFF_2026-10-11.md` (sekcje 2-5, sekcja 3 = struktura E03)
- Kontrola E01/E02 tylko dla faktów powoływanych przez E03.
- Wyciągi z PDF (tekst): `.../scratchpad/notes/E01_ADAM_Czytanie.txt`, `E02_EWA_Czytanie.txt`, `E03_ARES_Czytanie.txt`

Narzędzia: `pdftotext`, `pdfinfo`, Python 3 w trybie `-I` (skrypty porównujące w `.../scratchpad/notes/tools/`).

---

## 1. Struktura E03 (scena po scenie)

| # | Blok | Miejsce / czas (wg rev) | Linie rev | Czas wg rev | Treść w jednym zdaniu |
|---|---|---|---|---|---|
| CO | COLD OPEN | Habitat, Mars, SOL 287 | 41-92 | ok. 3 min | Piotr słucha sygnałów, Elena mówi o zebraniu Forda; napis "SOL 287" |
| T | Napis tytułowy | | 96 | | "ZERO -- ARES" |
| K | KLAMRA, obrona farmy | Łowicz, T+13 | 104-281 | ok. 6 min | 10 ujęć: alarm, napad (Marta strzela), Zofia ranna i żywa, warty, Aga dzwoni, śmigłowiec, "nie obronimy wszystkich", Vera spuszcza głowę |
| 1 | Gabinet rządowy | Warszawa, T+47 | 285-409 | ok. 5 min | Sowa: pożary; woda; prąd; LNG "zniszczony"; szpitale na agregatach; banki spermy zniszczone, "2-3 pokolenia" |
| 2 | Farma Zofii | Łowicz, T+47 | 413-461 | ok. 3 min | Wolska zleca Marcie uruchomienie ESA Darmstadt |
| 3 | Laboratorium | Warszawa, T+47 | 465-565 | ok. 4 min | Aga przyłapuje Verę: sekwencja wirusa nie jest naturalna; "Nad czym naprawdę pracowałaś?" |
| 4 | Granica | Słubice, T+48 | 569-650 | ok. 3 min | Reif odbiera Martę; plan "wyspy" (odcięcie od martwej sieci) |
| 5 | GPZ / stacja ESA | Bensheim, T+48-49 | 654-722 | ok. 5 min | Marta przeprogramowuje GPZ; rozruch stacji, "Stacja żyje" |
| 6 | Vera na ulicy | Warszawa, T+47 | 727-750 | ok. 2 min | Vera przy witrynie, plakat "RAZEM ODBUDOWUJEMY", dziewczynki rysują kredą |
| - | PUNKT ZWROTNY | | 754 | | |
| 7 | UJAWNIENIE, Ares IV | Mars, SOL 287 | 758-846 | ok. 5 min | Ford mówi załodze, że ludzkość zginęła w 100% mężczyzn; "Tata." (Piotr, l. 827, do sprawdzenia) |
| 8 | Stacja ESA, pierwszy sygnał | Darmstadt, T+49 | 854-902 | ok. 3 min | Łącze z Marsem; Kamila (Warszawa); opóźnienie 8:40 |
| 9 | Centrum Łączności | Warszawa, T+49 | 906-1014 | ok. 4 min | Wolska i Ford: banki, powrót za 8 miesięcy, warunek ochotnika i orbity Księżyca |
| 10 | Kanał prywatny | Darmstadt, T+49 | 1016-1113 | ok. 5 min | Marta-Piotr: "Karolina jest cała"; "Czy ty uruchomiłaś tę stację?"; próbka dla Karoliny |
| 11 | Ares IV, równolegle | Mars, SOL 287 | 1115-1231 | ok. 4 min | Piotr zgłasza się na ochotnika ("komandorem tej misji"); list Marcusa; James i Elena nagrywają |
| 12 | Laboratorium Very | Warszawa, T+50 | 1235-1266 | ok. 3 min | Wiadomości; Vera zagląda do szafy: pojemnik termiczny; pisze "ANTIDOTUM" |
| 13 | Ujęcia równoległe | T+49 / SOL 287 | 1274-1294 | ok. 2 min | Piotr, Marta, Aga przy zdjęciu, Karolina z żółtą teczką, Basia |
| 14 | Wyznanie | Warszawa, T+50 | 1296-1474 | ok. 5 min | Vera przyznaje się Adze; "Tata umarł na wirusa..."; "Pomogę ci. Ze względu na nich" |
| 15 | Lądowanie | Polska, T+295 | 1477-1555 | ok. 3 min | Kapsuła, tunel, dłonie na szybach Piotr-Karolina; Vera odprowadzona przez oficerów |
| 15A | Pokój kwarantanny | T+313 | 1557-1669 | ok. 5 min | Piotr i Marta; próbka marsjańska dla Karoliny; Korańczyk w progu |
| 16 | Epilog, Ziemia | T+400 | 1671-1793 | ok. 6 min | Montaż 7 krótkich ujęć: fabryka robotów, wiatraki, szpital, James, Aga, Wolska szkoli; "LATA PÓŹNIEJ" (placeholder do przebudowy) |
| 17 | Farma Zofii | Łowicz, T+430 | 1789-1863 | ok. 3 min | Piotr i Marta naprawiają traktor; Zofia na ganku |
| OK | Ostatnie ujęcie + napisy | Mars, świt | 1867-1890 | ok. 0,5 min | 5 napisów końcowych (patrz pkt 2) |

Numeracja scen 1-17 jest ciągła (15A to wstawka). Liczba bloków numerowanych: 18 (w tym 15A).

Oś czasu: T+13 (klamra) → T+47/49 (Ziemia i Mars) → T+50 → T+295 (lądowanie) → T+313 → T+400 → T+430.

---

## 2. Status punktów audytu w E03

**A2 (Wolska: Anna 51 vs Katarzyna ~58): OTWARTE.**
- E03 l. 13: `ANNA WOLSKA — wicepremier, 51 lat`.
- E03 l. 915: `Tu Anna Wolska, pełniąca obowiązki premiera` (sc. 9).
- E03 l. 896 i 17 oraz 1139: Ford to też Anna (`Tu Anna Ford`, `COMMANDER ANNA FORD`).
- Kanon w E02: `Wicepremier Katarzyna Wolska ~58` (E02 l. 42, 111), `GENERAŁ ANNA SOWA` (E02 l. 165).
- Efekt: w E03 są dwie Anny w różnych rolach (Wolska, Ford), a Sowa z E02 też jest Anną. Problem jest realny, jeśli zostaje Anna.
- Rekomendacja z handoffu (Katarzyna) jest zgodna z E02. Wymaga zmiany w E03 l. 13 i 915, a także tytułu "wicepremier"/"pełniąca obowiązki premiera" (patrz pkt 3).

**A4 (napis 78,3 mln km vs opóźnienie 8:40): OTWARTE.**
- E03 l. 765: napis `ODLEGŁOŚĆ OD ZIEMI: 78,3 MLN KM` (sc. 7).
- 8:40 w jedną stronę odpowiada ok. 156 mln km. Opóźnienie 8:40 jest użyte konsekwentnie w l. 895, 902, 920, 958, 968, 998, 1030, 1049, 1085.
- Plus osobna sprawa: rozmowy traktowane są jak 8:40 w obie strony (patrz pkt 3, fizyka).

**B8 (termiczny pojemnik Very): OTWARTE.**
- Jedyne wystąpienie: l. 1247 (`za odczynnikami: zamknięty pojemnik termiczny`). Vera patrzy i zamyka szafę.
- Brak dalszego wątku w scenach 13-17 i w napisach. Wątek nie jest domknięty ani wycięty.

**B10 (los Zofii): ROZWIĄZANE w tekście, decyzja Macieja nadal otwarta.**
- Klamra, l. 202-204: `Żyje. Rozcięta głowa, krew na skroni, oszołomiona, ale przytomna`.
- Sc. 17, l. 1820 i 1850: Zofia na ganku z herbatą, "śmieje się cicho". Brak jakiejkolwiek wzmianki o urazie.
- Tekst spójny z wariantem "żyje". Jeśli Maciej wybierze inny wariant, zmieniają się l. 202-204 (klamra) i l. 1820-1850 (sc. 17).

**C13 (antidotum vs szczepionka): OTWARTE, nazewnictwo mieszane.**
- "antidotum": l. 475, 487, 512, 1254, 1260, 1430, 1884 (napis końcowy: "ANTIDOTUM VERY STRAND ZOSTAŁO ZATWIERDZONE PRZEZ WHO"), także tabela l. 1910.
- "szczepionka": l. 974, 984, 987, 993, 1127, 1145, 1444, 1445.
- Mechanizm w scenach 9-11 to szczepionka (podanie plus kontrolowana ekspozycja). Napis końcowy i lab mówią "antidotum". Zalecenie: ujednolicić.

**Scena "LATA PÓŹNIEJ": do przebudowy, wciąż placeholder.**
- l. 1776-1785: napis `LATA PÓŹNIEJ`, Nowy Świat, mężczyzna z gazetą, "Nikt na niego nie patrzy". Placeholder `[do pełnej przebudowy... osobne zadanie]` w l. 1785.
- Sekwencja jest mocno nieczytelna: nie wiadomo, kim jest mężczyzna i dlaczego jest to jedyne ujęcie z mężczyzną w finale Ziemi.

**COLD OPEN (Mars, SOL 287):** l. 41-92. Zgodne z handoffem. Napis "SOL 287" w l. 92.

**Napis tytułowy:** l. 96, "ZERO -- ARES". Zgodne.

**Klamra (T+13):** l. 104-281. Zgodne z handoffem: Marta strzela z dubeltówki, napastniczki uciekają, Zofia żywa, warty, śmigłowiec zabiera Agę i Verę, dwie żołnierki zostają, "nie obronimy wszystkich", Vera spuszcza głowę.

**Finał T+295 / T+313 / T+400 / T+430 i napisy końcowe:**
- T+295 lądowanie: l. 1477 (`FLASH-FORWARD: T+295 DNI`). Zgodne z handoffem.
- T+313 pokój kwarantanny: l. 1557. Zgodne.
- T+400 epilog: l. 1671. Zgodne.
- T+430 farma: l. 1789. Zgodne.
- Napisy końcowe, handoff wymienia cztery. Plik zawiera pięć, z czego napis "POWIEDZIAŁA: WIEM" jest ostatni (l. 1890). Zgodne z handoffem co do treści (wirus aktywny / antidotum zatwierdzone dnia lądowania / Vera aresztowana / Aga świadkiem koronnym / "POWIEDZIAŁA: WIEM").

**Liczba scen i czas:**
- Liczba bloków: 21 (cold open, klamra, 1-17 z 15A, ostatnie ujęcie). Numeracja 1-17 ciągła.
- Tabela czasu (l. 1894-1918): suma pozycji to 73,5 min, a tabela podaje ŁĄCZNIE 74,5 min (błąd arytmetyczny o 1 min).
- Nagłówki części: "CZĘŚĆ PIERWSZA: ZIEMIA ok. 22 min" (l. 100), ale klamra 6 + sc. 1-6 (22) = 28 min. "FINAŁ ok. 9 min" (l. 1270), ale sc. 13-17 + ostatnie = 24,5 min.
- Nota reżyserska (l. 31): "pierwsze dwadzieścia minut to wyłącznie Ziemia", "UJAWNIENIE po ok. 25 minutach". Tabela daje ok. 31 min (cold open 3 + klamra 6 + sc. 1-6 22). Niespójne.
- Uwaga produkcyjna l. 1920: "cel ok. 67 min". Rzeczywista suma to ok. 73,5 min (80,6 wg nagłówków części).

---

## 3. Inne niespójności i błędy (z lokalizacją, bez poprawiania)

**Logika i fizyka**
- l. 1166: `Jestem komandorem tej misji`. Piotr mówi to o sobie, ale komandorką jest Ford (l. 17, 896, obsada). Błąd.
- l. 827: `Tata.` (Piotr, sc. 7, po "Elena: Piotrek"). Niezrozumiałe. Możliwe, że miało być "Marta." lub inna kwestia.
- l. 335: `Pożar sprzed trzech tygodni` (sc. 1). Terminal LNG został uderzony w T+9 (E02 prolog, E02 l. 2051 i 2103). W T+47 to ok. pięć tygodni, nie trzy.
- l. 984-988 vs l. 1145-1179 vs l. 1884: Wolska warunkuje lądowanie "potwierdzonym działaniem szczepionki na ochotniku", ale napis końcowy mówi "zatwierdzone przez WHO DNIA LĄDOWANIA". Test na Piotrze nie jest nigdzie pokazany ani zrelacjonowany. Lukę można zamknąć jednym zdaniem.
- Sc. 8-10 (l. 895-1085): 8:40 jest użyte jako czas odpowiedzi (wyślij, czekaj 8:40, dostajesz odpowiedź). Rzeczywista runda to 17:20. Handoff nazywa to kompresją, ale w scenie 10 wygląda na błąd fizyki.
- Liczba dni: l. 1076 `Dwieście czterdzieści osiem dni` (od T+49 daje ok. T+297). Ford l. 1004: `Okno startowe za siedem dni`, czyli start ok. T+56 plus 248 dni daje ok. T+304. Lądowanie to T+295 (l. 1477). Przesunięcie 2-9 dni, do uzgodnienia.
- Sc. 15 i 15A (l. 1487-1626): sterylna próbka marsjańska (`czerwonobrązowy pył`, `była w jego torbie przez całą kwarantannę`) trafia z rąk pacjenta w kwarantannie do dziecka. Sprzeczne z bezpieczeństwem biologicznym, skoro "wirus pozostaje aktywny w środowisku naturalnym" (l. 1882). Ryzyko logiczne.
- l. 1548-1549: Hania (5) i Zosia (3) przy lądowaniu, zgodne z handoffem (5/3).

**Nazewnictwo i obsada**
- Wolska: l. 13 `wicepremier`, l. 916 `pełniąca obowiązki premiera`. Do ujednolicenia.
- Postacie spoza obsady E03 (l. 7-23): JOANNA (l. 323, 30 lat), KAMILA Wiśniewska (l. 886), THOMAS REIF (l. 576, ESA), GENERAŁ SOWA (l. 297; w E02 to Anna Sowa). Dopisać do obsady lub oznaczyć jako epizodyczne.
- l. 180: `wuj trzymał starą dubeltówkę`. W E02 nie ma męża Zofii ani wuja. Ustalić kanon: czy Zofia ma męża.
- l. 1285: `ona i Vera` (zdjęcie w pokoju Agi). Dwuznaczne zaimki.
- l. 1285 i l. 1289-1291: Basia pojawia się w sc. 13 bez wprowadzenia (kanon: sąsiadka).

**Didaskalia i notatki produkcyjne w tekście sceny**
- l. 477: `Nowy wyraz twarzy w porównaniu z E02`. To uwaga reżyserska wpisana w didaskalia. Usunąć.
- l. 108-111 (Reżysersko w klamrze): to notatka reżyserska, poprawnie oznaczona.

**Stylistyka**
- l. 597: `Tak jak mogła być w takich warunkach` (niezręczne). Propozycja do rozważenia: "Na tyle, na ile w takich warunkach może być".
- l. 1121: `Zakreśla` (notatnik Piotra). Lekko nieoczywiste, akceptowalne.

**Wątki zawieszone (poza A/B/C z handoffu)**
- B7 (żółta teczka, list): teczka wraca w l. 1291, 1501, 1567, 1599, ale listu nie ma. Zwrot z listem nigdy nie pada. Nadal otwarte.
- C11 (Dąbrowski): w E03 pada tylko w spowiedzi (l. 1357-1382). Brak osobnego beatu śmierci. Otwarte, choć spowiedź częściowo to zastępuje.
- Karolina i Korańczyk: pojawia się tylko l. 1652-1664. Zasiane minimalnie, zgodnie z C14.

**Poprawki z zakresu audytu pokryte w E03:** Karolina ma swoje 19 lat (l. 16, 159); Hania/Zosia zgodne z kanonem; Pawle 04:14 (l. 1401) zgodne z E01.

---

## 4. Kontrola czytanek PDF

### 4a. Wspólne ustalenia

- Wszystkie trzy PDF są wygenerowane przez ReportLab, mają osadzony tekst i polskie znaki poprawne (brak mojibake, U+FFFD ani `Ã`/`Ä`).
- Wszystkie trzy kończą się wierszem `Koniec odcinka.`.
- Wspólny defekt (numery linii w tym pliku dotyczą PDF, o ile nie zaznaczono inaczej): generator zamienia `:` i `--` na kropkę i zostawia małą literę po niej. Liczba wystąpień: E01 = 29, E02 = 37, E03 = 57. Przykłady:
  - E03 PDF, l. 7: `sygnałów. szum, zakłócenia` (rev: `sygnałów: szum`).
  - E03 PDF, l. 105: `Żyje. Rozcięta głowa` (błędnie: `Żyje. Rozcięta`).
  - E03 PDF, l. 459: `Śmiertelność wśród mężczyzn. praktycznie sto procent. Kobiety. odporne.`
  - E01 PDF, l. 59: `żółta teczka` (po kropce bez wielkiej litery).
- Didaskalia i opisy akcji są w tekście. Zasada z handoffu (sekcja 6) mówi "bez didaskaliów, tylko dialogi i role". Wykryte: UJĘCIE w E01 (4 razy), E02 (7 razy), E03 (11 razy; rev ma 12, w PDF nie ma tylko "OSTATNIE UJĘCIE"). Zdania typu "Piotr zapisuje coś w notatniku ołówkiem." są w E03 PDF l. 9.
- Nagłówki scen i napisy w formie zwykłego tekstu (np. E03 PDF l. 442: `Ares Iv Research Station, Sala Główna, Dzień.`; l. 1062: `Mars, Ares Iv Habitat, ...`). Błędna forma tytułowa `Iv` zamiast `IV`.
- Role są zapisane jako sama nazwa bez kropki (E03: 244 linie, E01: 161, E02: 283). Zasada z handoffu mówi "Imię.".
- Smiley w E01: rev `"Cześć :) słyszałaś..."` (l. 601), PDF `Cześć.) słyszałaś...` (l. 339). Dwukropek zamieniony na kropkę, nawias został.
- Nagłówki bloków obecne w tekście, np. E01 PDF l. 73, 229, 342, 494: `Przeszłość`.
- Pokrycie dialogów (test 5-gramów na liniach dialogowych rev): E01 87,1% (55 braków z 425, głównie nota i obsada, które słusznie wypadły), E02 89,7% (70 z 678, głównie nota i opisy prologu), E03 97,3% (16 z 598, głównie obsada i nota). Dialogi są przeniesione, problemem jest format i kolejność.

### 4b. E01 ADAM (`ZERO_E01_ADAM_Czytanie.pdf`)
- 27 stron. Ostatnie słowa: `Cisza trzyma się dłużej, niż jest wygodnie. Czarny ekran. Koniec odcinka.` Zgodne z rev.
- Fragmenty kontrolne (start / środek / koniec) zgodne z rev, poza notą techniczną pominiętą w PDF (zgodnie z zasadą).
- Błędy: smiley `Cześć.)` (PDF l. 339); 29 miejsc z małą literą po kropce; didaskalia UJĘCIE x4; nagłówki bloków.

### 4c. E02 EWA (`ZERO_E02_EWA_Czytanie.pdf`)
- 45 stron. Ostatnie słowa: `...zbliżają się chwiejne światła. Coraz bliżej. Czarny ekran. Koniec odcinka.` Zgodne z rev.
- Błędy: 37 miejsc z małą literą po kropce (np. PDF l. 8 `Gazoport. rząd srebrnych zbiorników`); UJĘCIE x7; brak mojibake.

### 4d. E03 ARES (`ZERO_E03_ARES_Czytanie.pdf`)
- 39 stron. Ostatnie słowa: `Ziemia, mała, niebieska, wschodzi nad horyzontem. CZARNY EKRAN. Koniec odcinka.`
- BRAKUJĄ napisy końcowe. W PDF nie ma: "WIRUS Y POZOSTAJE AKTYWNY...", "ANTIDOTUM VERY STRAND ZOSTAŁO ZATWIERDZONE...", "VERA STRAND ZOSTAŁA ARESZTOWANA...", "AGA BRYK ZEZNAWAŁA JAKO ŚWIADEK KORONNY.", "POWIEDZIAŁA: WIEM." (w PDF tylko słowo "Wiem" w innych kontekstach).
- BRAKUJĄ też inne napisy: "ODLEGŁOŚĆ 78,3 MLN KM" (A4 znika z czytanki, ale w montażu napis zostaje), "LATA PÓŹNIEJ", "PROGRAM ODBUDOWY...", "FABRYKA ROBOTÓW, BRANDENBURGIA". Część napisów zostaje w formie zwykłego tekstu (np. "PRIORYTET. SZPITALE..." l. 978), część znika. Wynik niespójny.
- Pierwsza linia `ZERO. Odcinek trzeci. ARES.` i `T+13 dni.` (l. 34) to timecod. Zgodnie z zasadą nie powinno go być.
- Zawiera "Ares Iv" (3 wystąpienia tytułowe) zamiast "ARES IV".
- Nota reżyserska, obsada, PODSUMOWANIE CZASU i nota dramaturgiczna są poprawnie pominięte.
- Pokrycie dialogów 97,3% (najlepsze z trzech plików).

---

## 5. Ryzyka i rekomendacje (do przekazania Maciejowi)

1. Naprawić generator czytanek. Trzy błędy wspólne: zamiana `:`/`--` na kropkę z małą literą (29/37/57 miejsc), didaskalia i opisy akcji w tekście, role bez kropki. Dla E03 dodatkowo: brak napisów końcowych, `Ares Iv`, timecod `T+13 dni.`. Po poprawie zregenerować wszystkie trzy PDF (sprawdzić, że nie są otwarte w czytniku, bo to blokuje zapis).
2. Domknąć decyzje w E03 przed zdjęciami: A2 (Wolska zamiast Anny, zmiana w l. 13 i 915, plus tytuł), A4 (napis ok. 156 mln km w l. 765 albo opóźnienie ok. 4:20), C13 (jedno nazewnictwo: szczepionka, bo napis końcowy i rozmowy mówią o szczepionce; 7 wystąpień antidotum), B8 (pojemnik Very: domknąć jednym zdaniem w sc. 14 albo wyciąć).
3. Logika szczepionki: napis "zatwierdzone przez WHO dnia lądowania" (l. 1884) kłóci się z warunkiem "najpierw test na ochotniku" (l. 984-988). Dopisać zakończony test (np. w sc. 11 lub 15) albo zmienić napis. Jednocześnie usunąć błąd "komandorem tej misji" (l. 1166, Ford jest dowódczynią).
4. Czas i fizyka: tabela (l. 1918) to 73,5 min, nie 74,5. Nagłówki części (22 i 9 min) i nota (ujawnienie po 25 min) nie zgadzają się z tabelą (28, 24,5 i ok. 31 min). Opóźnienie 8:40 użyte jako runda w sc. 8-10 (rzeczywista runda 17:20). Liczby dni (248, T+295, "siedem dni") do uzgodnienia. Plus błąd "Pożar sprzed trzech tygodni" (l. 335, powinno być ok. pięciu tygodni po T+9).
5. Sprzątanie tekstu sceny: usunąć uwagę produkcyjną z didaskaliów (l. 477), ujednolicić "wicepremier"/"pełniąca obowiązki premiera", uzupełnić obsadę o Joannę, Kamilę, Reifa i Sowę (l. 7-23), zdecydować o `wuj` (l. 180) i o "Tata." (l. 827). Scena "LATA PÓŹNIEJ" (l. 1776-1785) nadal jest placeholderem.
