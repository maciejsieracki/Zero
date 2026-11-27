# ZERO — E01 produkcja i budżet: notatki z przeglądu (tylko odczyt)

Źródła (R = `/tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/zero-unrar/Zero`):
- `R/ZERO_HANDOFF_2026-10-11.md` (sekcje 2–5, 7 w całości, także 0, 1, 8–10 dla kontekstu)
- `R/ZERO_E01_produkcja/01..08*.md` (wszystkie 8 w całości)
- `R/ZERO_mini_serial_E01_ADAM_rev.md` (obsada, bloki przeszłości, napisy, sceny, czasy — przegląd celowany)
- `R/ZERO_DO_PRZENIESIENIA/ZERO_E01_produkcja/_backups/Bud` (plik bez rozszerzenia, to xlsx, 38 arkuszy)
- `R/ZERO_DO_PRZENIESIENIA/ZERO_E01_produkcja/_backups/Energomat_koszty_krytyczne_2026-2027_BACKUP_2026-06-09.xlsx`

Nie uruchamiano niczego z archiwum. Odczyt xlsx: kopia do katalogu roboczego w scratchpadzie, parser XML w Pythonie (`work/xl_extract.py`), bo openpyxl nie czyta jednego arkusza `Bud` (błędny XML w arkuszu `robocze>>>`).

---

## 1. Dokumenty produkcyjne — jedna linia każdy

| Plik | Zawartość |
|---|---|
| 01_nota_rezyserska | Język wizualny odcinka (kamera „oddycha" → statyczna), 3 palety światów, dwutorowa narracja (P1–P4), Vera jako postać centralna, kadry końcowe Zero Day. |
| 02_charakterystyki_postaci | Wygląd, wiek, wskazówki dla aktorów przy pierwszym wejściu: Marta, Karolina, Michał, Vera (64/24), Aga, Paweł, Tomek, Dąbrowski. |
| 03_opisy_wizualne_scen | Kadr otwierający i język kamery dla scen 1–6, P1, P2, 12, 14 oraz wstawek TV. |
| 04_dzwiek_i_muzyka | Filozofia dźwięku, mapa muzyczna scen 1–14 i P1–P4, 3 tematy, cisza jako zasada. |
| 05_inserty_closeup | 8 obowiązkowych insertów/rekwizytów (teczka, sweter, fiolka, karteczka, ekran telefonu, mapa PSE, artykuł, dłonie) + tabela ciągłości. |
| 06_przejscia_scen | Lista ok. 30 cięć (CUT, SMASH, DISSOLVE) z napisami czasowymi. |
| 07_podtekst_dialogowy | Podtekst kwestii dla scen 1–6, 12, 13, P1–P3. |
| 08_noty_techniczne | BSL-4, sala PSE, wstawki TV, OIT, kostiumy bloków przeszłości, mapa świata, plener Sceny 1, zakres wzmianek o Ares IV. |

---

## 2. Zgodność z kanonem (handoff §2) i scenariuszem

Zgodne:
- Wiek: Marta 38, Karolina 19, Vera 64 (P1 24), Aga 34, Paweł 38, Tomek 35, Michał 22 (02, 08, scenariusz).
- Pacjent zero, kolejność śmierci Pawła 04:14 (07 l.126), Ares IV milczy 48 h (04, 07, 08).
- Brak muzyki w scenach 3, 4, 6, 7, 8, 9, 10, 11, 13 i w wstawce T-5/T-1 (04).
- Dąbrowski umiera poza kadrem w Zero Day (02, 08, scenariusz).
- Scena P4: Vera 52, „dwa lata po wyjeździe" (06 l.113, scenariusz l.869). Wiek i czas zgodne z 08 (12 lat temu).

Niezgodne lub niekompletne względem kanonu (szczegóły w sekcji 3).

---

## 3. Niespójności (z lokalizacją)

### A. Kanon / handoff (do poprawy w dokumentach produkcyjnych)
1. **Nazwisko Michała.** 02 l.34: „MICHAŁ WIŚNIEWSKI". Kanon (handoff §2 l.81) i scenariusz (obsada l.36): **Michał Zawadzki**. Nazwisko Wiśniewski występuje też u Tomka (02 l.84), czyli dwie niepowiązane postacie z tym samym nazwiskiem.
2. **Włosy Karoliny.** 02 l.24: „Jasne włosy, niski kucyk". Handoff §7 l.241: „ciemne włosy". Scenariusz nie podaje koloru. Ustalić jedno i wpisać do 02, 03 i do Flow.
3. **Nazwa wirusa.** 05 l.33: „wirus ADAM-1"; 08 l.64: „Paweł umiera na ADAM-1". Handoff §2 l.62: „ADAM-1 porzucone", kliniczna nazwa **HYV-1**; scenariusz używa HYV-1 w pasku TV. Zamienić na HYV-1 (lub „wirus Y").
4. **Kanon wizualny Flow nie trafił do 02/03.** Handoff §7 l.255–259: Michał po LEWEJ, Karolina po PRAWEJ, Michał w sweterze z **dokładnie jednym** zielonym dinozaurem, Karolina w **zielonej kurtce bez swetra**, gołe dłonie, brak muzyki w klipach. W 02/03/04 nie ma ani lewo/prawo, ani liczby dinozaurów, ani zielonej kurtki Karoliny. 04 l.18 (Scena 1: muzyka „Pełna") jest sprzeczne z zasadą „brak muzyki w klipach Flow", jeśli muzyka ma być w klipie — dokumenty nie mówią, że to warstwa CapCut.

### B. Osie czasu bloków przeszłości (najpoważniejsze, pokazane na liczbach)
Scenariusz ma własne napisy i wieki, spójne z wiekiem Agi (34):

| Blok | Scenariusz (źródło) | Produkcja: 01 / 06 / 08 / 03 |
|---|---|---|
| P1 | Vera 24, „40 LAT WCZEŚNIEJ" (l.186) | zgodne |
| P2 | Vera ~35, „OK. 11 LAT PO PRZYJEŹDZIE" (l.429–431), Aga 4–5 (l.511) | Vera **28**, napis „CZTERY LATA PÓŹNIEJ" (06 l.63), 08 l.86: „~36 lat temu" |
| P3 | Vera ~49, „OK. 25 LAT PO PRZYJEŹDZIE" (l.613–615), Aga 19 (l.636) | Vera **46**, napis „OSIEMNAŚCIE LAT PO PRZYJEŹDZIE" (06 l.85), 08 l.87: „~18 lat temu" |
| P4 | Vera ~52, „DWA LATA PO WYJEŹDZIE" (l.867–869) | zgodne (08 l.88: ~12 lat temu) |

Konsekwencje:
- **03 l.74 („mała Aga biegnie do kuchni", P2)** jest niemożliwe przy produkcyjnym wieku Very (28 lat ≈ 36 lat temu, a Aga ma 34 lata, czyli urodziła się ok. 34 lat temu). Dopiero scenariuszowe P2 (Vera 35, ok. 29 lat temu) daje małą Agę (4–5 lat).
- **Napisy w 06** (l.63 i l.85) trzeba poprawić na „11 LAT" i „25 LAT" PO PRZYJEŹDZIE (liczone od przyjazdu Very, 24 l.).
- **Dąbrowski** (Dąbrowski ma 70 l. dziś): w P2 ≈ 41, w P3 ≈ 55, w P4 ≈ 58. Produkcja: 08 l.93 „P2 34 lata", 08 l.94 „P3 48 lat", 02 l.100 „52 lata". Wszystkie trzy wartości są ze sobą niezgodne i nie zgadzają się z 70 l. dziś.
- **Czas P2** w 06 l.63 („CZTERY LATA PÓŹNIEJ") jest zapisany względem P1, a nie względem przyjazdu — ujednolicić formę napisu.

### C. Wewnętrzne sprzeczności w dokumentach
5. **03 l.106 vs l.113 (Scena 14):** „Każde ujęcie trwa 3–4 s" vs „Każdy kadr trwa 5 sekund" (ostatnia trójka). Także 04 l.39: „narasta przez 40 sekund" — przy 3 kadrach po 5 s brzmi to nieprawdopodobnie bez wyjaśnienia.
6. **Teczka Karoliny.** 02 l.24: Karolina ma żółtą teczkę w plecaku „noszoną od zawsze". 05 l.16: teczka to teczka Marty (zdjęcie Piotra), a Karolina nosi ją dopiero w E03. Wybrać jedną wersję.
7. **Zdjęcie Piotra.** 08 l.125: „Widzimy Piotra po raz pierwszy dopiero w E03". 05 l.9: w teczce jest zdjęcie Piotra, a scenariusz (podsumowanie, l.26–27) pokazuje Martę z teczką i zdjęciem w Zero Day. Drobne, ale do uzgodnienia.
8. **Postacie bez wpisu w 02:** Joanna (pielęgniarka, scenariusz l.1113; 07 l.125), Beata i Kacper (scenariusz l.1013–1016, scena 11). Dodać do obsady.
9. **Imię „Marek" w scenie 11 scenariusza** (l.1016) to inna osoba niż Dąbrowski. Przy czytaniu PDF i napisach może mylić.

### D. Pokrycie scen w dokumentach
10. **Scena 15 — STATEK WIDMO (scenariusz l.1226, ok. 1,5 min, bez muzyki):** nie występuje w żadnym z 8 dokumentów (brak kadrów, muzyki, przejść, insertów).
11. **Brak opisów wizualnych** w 03 dla scen 7–11, 13, P3, P4 (03 ma 1–6, P1, P2, 12, 14). Muzyka (04) i przejścia (06) są dla nich, ale kadry nie.
12. **Suma czasów scen w scenariuszu** (znaczniki [CZAS]) ≈ 57 min, bez wstawek TV i napisów. Handoff podaje ~65 min. Różnica do sprawdzenia przy montażu.

---

## 4. Technika AI (co dokumenty mówią)
- Dokumenty produkcyjne 01–08 nie wspominają o Flow, Veo, Omni Flash, Kling, CapCut ani lektorze. Cały kontekst AI jest w handoffie §7 (metoda A/B, zasady stałe, post w CapCut).
- Kluczowe zasady dla dźwięku: muzyka tylko jako osobna warstwa w CapCut; dialogi w Flow po angielsku, napisy PL w post; lektor PL nagrywany osobno.
- Scenariuszowy zapis „Vera mówi po polsku przez cały E01 — z norweskim akcentem" (scen. l.52) jest zgodny z fragmentami „po norwesku — napisy polskie" (l.55, 281, 513, 714, 900) i z 07 l.30. Nie traktuję tego jako sprzeczności.

---

## 5. Budżet — co jest w archiwum

### 5.1 Plik `Bud` (w folderze `_backups`, nazwa z budżetu: „Budżet_pitch_deck_akt.2026.06.02 …")
- Format: xlsx (Microsoft Excel 2007+), 38 arkuszy, 2,6 MB, wykresy, połączenia zewnętrzne.
- **To NIE jest budżet serialu ZERO.** Arkusz „Info" i arkusze „Spr.fin.*", „DCF Wycena", „ENE.B2B", „GAZ.B2B/B2C", „OZE", „ECOM" dotyczą spółki **ENERGOMAT**: energia B2B, gaz B2B/B2C, OZE i e-commerce, rozwijane z Polski na Czechy i Słowację (2027), kraje UE (2028–2030), USA/Kanada/Meksyk (2032), Koreę/Japonię (2033), Chiny (2034). Zero trafień na „ZERO", „serial", „Veo", „Flow", „Sieracki", „Naster" (jedyne „zero" to „zero przychodów" w Info Z18).
- Metadane: autor Marcin Szostak (utw. 2025-09-30), ostatnia modyfikacja Damian Maślanka **2026-06-02** (zgodne z nazwą „akt.2026.06.02"). DCF: „Dane z budżetu 28.05.2026".
- Najważniejsze kwoty (PLN, skumulowane w arkuszu „Spr.fin.sum", wszystkie kraje):
  - Przychody: 2027: 4,76 mln; 2028: 12,68 mln; 2029: 31,11 mln; 2030: 62,62 mln; 2031: 145,91 mln; 2032: 272,89 mln; 2036: 1 033 mln.
  - Marża bezpośrednia: 52% (2027) → 74,5% (2036). Wysokie jak na handel energią; wymaga uzasadnienia.
  - EBITDA: 2027: −0,95 mln; 2028: −0,18 mln; 2029: −1,15 mln; 2030: +7,36 mln; 2031: +47,98 mln.
  - Zysk netto: 2027: −0,98 mln; 2028: −0,21 mln; 2029: −2,17 mln; 2030: +4,88 mln.
  - Marketing (user acquisition): 2027: 1,01 mln; 2028: 1,59 mln; 2029: 3,96 mln.
  - Wynagrodzenia (P&L, bez ZUS): 2027: 1,99 mln (plan kosztów z ZUS: 2,39 mln; suma kosztów stałych 2,50 mln — zgodne z P&L).
  - **Środki pieniężne na koniec okresu: 2027: −1,13 mln; 2028: −1,31 mln; 2029: −3,44 mln; 2030: +1,47 mln.** Emisja udziałów = 0 i kredyt = 0 we wszystkich latach. Model nie ma finansowania — luka ~3,4 mln zł w ujęciu rocznym (miesięczny szczyt będzie głębszy; arkusz jest roczny). Info N42 wspomina „bezpieczeństwo operacyjne 2–4 mln zł" — nie wpięte.
  - Podatek dochodowy 2029: 0,99 mln przy zysku brutto −1,18 mln w tym roku. Podatek naliczony w roku straty (brak odliczenia strat).
  - **DCF Wycena** (WACC 15%, g 3%): EV na BO 1 612 mln zł; EV na koniec 2027: 1 855 mln; TV 2037: 4 947 mln. Porównanie w B31: 1 391 mln („WACC 15–19%, g=2%"), wpisane ręcznie.
  - **DCF nie jest spięte z P&L.** Tabela „Dane z budżetu" (DCF Wycena B5:L8): przychody 2029: 27,6 mln vs P&L 31,1; EBITDA 2029: −1,9 vs −1,15; EBITDA 2030: 5,9 vs 7,36; EBITDA 2031: 46,1 vs 47,98. Wycena pochodzi z wcześniejszej wersji modelu.
  - Marża EBITDA 2037 ≈ 64% (726/1137 mln) — do obrony.

### 5.2 Plik `Energomat_koszty_krytyczne_2026-2027_BACKUP_2026-06-09.xlsx`
- Arkusz „Koszty krytyczne". Autor pliku: openpyxl; ostatnio zmieniał Patryk Nabożny, 2026-06-09.
- Założenia: 5 miesięcy 2026 (sierp.–grudz.), 12 miesięcy 2027, mnożnik ZUS 1,203.
- Wynagrodzenia (brutto → koszt pracodawcy): Product Owner/Growth PM 16 000 → 19 248; Operations/BizDev 16 000 → 19 248; **Analityk 18 000 → 21 654 (brak tego stanowiska w arkuszu `wyn.pl` modelu: 0 trafień)**; Customer Support pół etatu 8 320 → 10 009 (w modelu: 8 000 brutto, 50 h); Marketing Manager 16 000 → 19 248; Zespół marketingowy 9 600 → 11 549 (60 zł/h, jeden etat).
- Miesięcznie: 100 955,76 zł. Rocznie 2026: **504 778,80 zł**; 2027: **1 211 469,12 zł**.
- Marketing (usługi wg P&L, 2027 ↔ model `Spr.fin.sum`): Energia B2B 811 620 (E48 w modelu — zgodne); Gaz B2B 108 120 (E91 — zgodne); OZE 94 200 (wiersz 146 — zgodne). Razem 2027: **1 013 940 zł** (= UA w modelu). 2026 = run-rate × 5/12: **422 475 zł** (Energia 338 175; Gaz 45 050; OZE 39 250).
- **Razem koszty krytyczne: 2026 = 927 253,80 zł; 2027 = 2 225 409,12 zł.** (Przeliczone niezależnie w Pythonie; zgodne z formułami.)
- Uwagi: plik jest podzbiorem Energomatu. Obejmuje 2026, którego model (start 2027) nie zawiera. Stanowisko Analityk nie ma odpowiednika w modelu. Zespół marketingowy: backup liczy jeden etat (11 549 zł/mies.), a model `wyn.pl` ma w styczniu 2027 już 23 098 zł/mies. (2 etaty-równoważniki). Customer Support: backup 8 320 zł pół etatu, model 8 000 zł przy 50 h. Model zmienia obsadę i etaty w czasie, backup ma stały stan.

### 5.3 Trzeci plik „Budżet_pitch_deck_w03_warC_NIEWDROŻONY.xlsx"
- **Nie istnieje w archiwum.** Przeszukano nazwy plików w całym R (także w `_archiwum`, `ZERO_produkcja_flow`, `ZERO_DO_PRZENIESIENIA`) oraz listingi obu ZIP-ów (Planify, PACZKA) — brak.
- Nazwa sugeruje: wariant C z wersji 03, „NIEWDROŻONY" = zmiany niezastosowane (nie wdrożona wersja). Nie da się tego zweryfikować.

### 5.4 Który budżet jest aktualny
- Dla Energomatu: `Bud` (2026-06-02) jest źródłem backupu z 2026-06-09. Oba są spójne w marketingu, ale DCF w `Bud` jest starszy niż P&L.
- Dla serialu ZERO: **brak budżetu** w archiwum. Handoff nie ma sekcji o kosztach, a dokumenty produkcyjne nie podają kwot.

### 5.5 Co budżet ZERO powinien objąć (żadnego z tych pozycji nie znaleziono)
- Generowanie AI: subskrypcja Google AI Pro, kredyty Flow/Omni Flash, Veo (Extend), backup Kling, ewentualne poprawki (liczba klipów z `ZERO_produkcja_flow`, 46 plików, nie liczona).
- Post: CapCut (warunki komercyjne), polski lektor (wykonawca lub TTS z licencją), miks, napisy, muzyka (kompozytor lub licencja biblioteczna z prawem do dystrybucji).
- Prawa: logotypy i nazwy TVN, TVN24, CNN (08 l.49; scenariusz „Pasek TVN"), nazwy WHO/ESA w wiadomościach. Wyjaśnić klarowanie albo fikcyjne odpowiedniki.
- Dystrybucja, napisy wielojęzyczne, ewentualne festiwale i marketing.

---

## 6. Luki produkcyjne (do wypuszczenia)
1. Prawa muzyczne: 3 tematy (04 l.43–54), jingle TV (04 l.23), motyw główny Zero Day. Brak kompozytora, licencji i cue sheet.
2. Lektor: brak decyzji (aktor, TTS, stawka, licencja NaturalReader do czytanek).
3. Licencje AI: warunki komercyjne Flow/Veo/Omni/Kling i CapCut — nie sprawdzone w dokumentach.
4. Scena 15, wizualia scen 7–11/13/P3/P4, kanon Flow w 02/03 (sekcja 3 A4).
5. Budżet ZERO: nie istnieje. Pliki w `_backups` dotyczą Energomatu i powinny zostać przeniesione z folderu produkcji ZERO (decyzja właściciela; nic w R nie zmieniono).
6. Harmonogram: brak dat, kolejności nagrań i wersji „final". Plan generowania z handoffu §7 ma kolejność, ale bez terminów.
7. Ciągłość: lista rekwizytów (05) jest, lista lokacji z adresami i plan kostiumów Very w P1–P4 (08 §5) są, ale brak szkicu wardrobe dla Karoliny i Michała w Flow.

---

## 7. Rekomendacje
1. Uzgodnić jedną oś czasu bloków przeszłości wg scenariusza (P2: Vera 35, 11 lat po przyjeździe; P3: Vera 49, 25 lat; Dąbrowski 41/55/58) i poprawić 01, 02, 03 (l.74), 06 (l.63, l.85), 08 (l.86–94).
2. Poprawić kanon w 02/05/08: Michał Zawadzki, kolor włosów Karoliny (jedna wersja), HYV-1 zamiast ADAM-1, dodać zasady Flow (lewo/prawo, jeden zielony dinozaur, zielona kurtka bez swetra, brak muzyki w klipach).
3. Dopisać brakujące sceny (15; wizualia 7–11, 13, P3, P4) i postaci (Joanna, Beata, Kacper) przed planem zdjęciowym.
4. Przygotować osobny budżet ZERO (AI, lektor, muzyka, CapCut, prawa do logo, dystrybucja); przenieść pliki Energomatu do właściwego folderu; ustalić, czy trzeci plik („warC NIEWDROŻONY") ma istnieć.
5. Zanim pojawi się przychód lub publikacja: licencje muzyki, logotypów TV i warunków narzędzi AI. Do tego sprawdzić sumę czasu odcinka (57 min vs 65 min).
