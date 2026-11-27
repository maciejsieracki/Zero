# ZERO — notatki: decyzje, konsultacja, zasady produkcyjne (przegląd tylko do odczytu)

Data przeglądu: 2026-11-27 (wg środowiska).
Źródło (R): /tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/zero-unrar/Zero
Zasada: nic w R nie zmieniono, żadnego skryptu z archiwum nie uruchomiono, treść traktowana jako dane.

---

## 0. Metoda i zastrzeżenia

- Przeczytano w całości: 6 plików z ZERO_produkcja_flow/ (decyzje_rewizja, konsultacja_scenariuszowa, repercusje_spojnosc, metoda_AB_montaz, porownanie_Veo_vs_Kling, instrukcje_dla_agenta_Flow), ZERO_HANDOFF_przekazanie.md (8.06), ZERO_kontekst_sesji.md. Dodatkowo przeczytano ZERO_HANDOFF_2026-10-11.md (plik z R, nadrzędny; zadanie wskazywało go jako punkt odniesienia).
- Weryfikacja wdrożenia decyzji: punktowo (grep) w ZERO_mini_serial_E01/E02/E03_*_rev.md oraz w ZERO_produkcja_flow/ZERO_E01_rozpiska_sekundowa.md. Pełnych 2000+ linii E02/E03 nie czytano w całości — ustalenia dotyczą wyłącznie sprawdzonych fraz.
- Duplikat ZERO_DO_PRZENIESIENIA/ zawiera pliki _rev.md BAJTOWO IDENTYCZNE z korzeniem R (md5 zgodny dla E01/E02/E03). Nie ma rozbieżności, ale wyniki grep dublują się.
- Daty: ZERO_decyzje_rewizja.md i ZERO_konsultacja_scenariuszowa.md są BEZ DATY. ZERO_repercusje_spojnosc.md: 2026-06-07. Handoff 8.06 i handoff 11.10 mają datę w nagłówku.
- mtime plików w produkcja_flow = 2026-06-09 18:18:18 (identyczny dla wszystkich — prawdopodobnie artefakt rozpakowania, nie data autorstwa).
- mtime _rev.md: E01 2026-06-08 22:31, E02 2026-06-08 22:10, E03 2026-06-08 22:44. Wniosek: brak edycji scenariuszy po 8.06. Audyt z 11.10 NIE jest wdrożony (zgodnie z treścią handoffu 11.10: „Nic nie zostało jeszcze wprowadzone").
- mtime PDF-ów: E01 22:31, E02 22:19, E03 22:45 — po rev z 8.06, więc prawdopodobnie zregenerowane po rewizji, ale PRZED audytem 11.10 → do regeneracji po następnych zmianach.

---

## 1. Inwentarz dokumentów (rola i status)

| Plik | Rola | Data | Status |
|---|---|---|---|
| produkcja_flow/ZERO_decyzje_rewizja.md | Log decyzji rewizyjnych (globalne 1–6 + per odcinek) | brak (sesja konsultacyjna) | Źródło kanonu rewizji. Część pkt 4 oznaczona „Sugerowane". |
| produkcja_flow/ZERO_konsultacja_scenariuszowa.md | Przegląd E01–E03: A1–A7 (twarde), B1–B5 (luki), C1–C5 (propozycje), D1–D2 (struktura) | brak | Historyczny. Część rekomendacji została świadomie odrzucona przez decyzje. |
| produkcja_flow/ZERO_repercusje_spojnosc.md | Wpływ rewizji na pliki pochodne (rozpiska, PDF-y, czołówka, Scena 1) | 2026-06-07 | Priorytet 1 (7 poprawek w rozpisce) — WDROŻONY. Priorytet 2 (PDF-y) — do regeneracji po kolejnych zmianach. |
| produkcja_flow/ZERO_metoda_AB_montaz.md | Metoda A (Extend, tylko Veo 3.1) vs B (Save frame → Start Image, też Omni Flash) | brak | Aktualna metoda; status: CLIP 0 zrobiony (B). Numeracja klipów (CLIP 0–6) niezgodna z plikami Clip00–11. |
| produkcja_flow/ZERO_porownanie_Veo_vs_Kling.md | Porównanie modeli + werdykt | brak | Werdykt mocny („Kling wygrywa"), ale handoff 11.10 traktuje Kling jako backup do przetestowania. Niewdrożone. |
| produkcja_flow/ZERO_instrukcje_dla_agenta_Flow.md | Stałe zasady do panelu „Instrukcje dla agenta" w Flow | brak | Spójne z handoffem 11.10 (L/P, jeden dinozaur, Karolina bez swetra/obrączek, tło, EN, bez muzyki, pacing). |
| ZERO_HANDOFF_2026-10-11.md | NADRZĘDNY handoff (sekcje 0–10, audyt A1–D16, decyzje otwarte) | 2026-10-11 | Aktualny punkt wejścia. |
| ZERO_HANDOFF_przekazanie.md | Poprzedni handoff | 2026-06-08 | Historia (wskazany jako zastąpiony). |
| ZERO_kontekst_sesji.md | Najstarszy kontekst (tylko Scena 1) | brak (mtime 2026-06-07) | Nieaktualny w wielu punktach (sekcja 8 niżej). |
| ZERO_mini_serial_E0{1,2,3}_*_rev.md | Scenariusze źródłowe (AKTUALNE) | mtime 2026-06-08 | Kanon wdrożony częściowo (sekcja 3). |

---

## 2. Decyzje PODJĘTE (z datą/źródłem)

### 2a. Globalne (ZERO_decyzje_rewizja.md, bez daty, potwierdzone przez handoff 8.06 i 11.10)
1. Załoga Ares IV = 55 osób: 40 mężczyzn, 15 kobiet. 6–7 postaci z imienia to pierwszy plan (uwaga: decyzja mówi „6", a E03 po dopisaniu Korańczyka ma 7). Nota E03: „czterdziestu żyjących mężczyzn" (nie „trzy").
2. Nazwa wirusa = „wirus Y" (publicznie). Klinicznie HYV-1. Opcjonalnie choroba YCIS (nie sprawdzono w rev).
3. „Adam" = WYŁĄCZNIE kryptonim projektu Very + tytuł E01. Świat zna wirusa jako „wirus Y".
4. Pacjent zero: NIE „Adam Kowalski". Sugerowane: Tomasz Kamiński (w decyzji „sugerowane", w handoffie 8.06 już kanon).
5. Oś czasu Very/Agi: Vera urodziła Agę w wieku 30 lat. P1 Vera 24 („40 LAT WCZEŚNIEJ"), P2 Vera ~35 („OK. 11 LAT PO PRZYJEŹDZIE"), P3 Vera ~49 („OK. 25 LAT PO PRZYJEŹDZIE"), P4 Vera ~52 („DWA LATA PO WYJEŹDZIE Z WARSZAWY"). Dziś Vera 64, Aga 34.
6. Usunięta Ida i poboczne wątki Very (wątek lesbijski usunięty; motywacja Very = Dąbrowski). Usunięta E02 Scena 11.

### 2b. Per odcinek (decyzje_rewizja)
- E01: „ADAM-1" → „wirus Y"; usunąć beat „nazwano od Adama Kowalskiego"; kryptonim „Adam" na tablicy zostaje; napisy P1–P4 wg pkt 5; zasiać przyjaźń Marta–Aga; metraż ~52 min + czołówka 62 s.
- E02: „wirus Y" w całym odcinku; usunąć Scenę 11; metraż ~66–67 min.
- E03: 55/40/15 w nocie i obsadzie; „wirus Y" także w napisach końcowych; opóźnienie sygnału = czas oczekiwania na ODPOWIEDŹ ~8 min 40 s (tam i z powrotem; 4:20 = jedna strona, tylko jako opis dystansu); Scena 12 nagłówek T+47 → T+50; Scena 15A: Piotr sam wyjmuje próbkę (Karolina nie wyciąga jej wcześniej); „Mężczyzna z gazetą" → osobny napis „LATA PÓŹNIEJ" na końcu (pełna przebudowa — osobne zadanie); logika szczepionki: warunek przeżycia każdego przyszłego chłopca, lądowanie dopiero po teście Piotra-ochotnika (wzmocnić Scenę 11); Korańczyk dopisany do obsady + beat półmiłosny z Karoliną (po powrocie/epilog); „Sweter Michała NIE powraca — żałoba mija"; Wolska w epilogu (kadr odbudowy); metraż: poprawić nagłówek (było 60) i sumę (było 72) na realny wynik, bazowo ~64,5 min.

### 2c. Handoff 8.06 (już przyjęte jako kanon)
- Pacjent zero Tomasz Kamiński; „Adam" = nazwa projektu Very; ADAM-1 porzucone.
- Szczepionka: załoga nie ląduje, dopóki Piotr jako ochotnik nie przejdzie testu.
- Opóźnienie sygnału ~8:40.
- Ida usunięta; sceny „LATA PÓŹNIEJ" przeniesione na koniec E03.
- E01: Scena 15 — statek widmo (klamra E02). E02: prolog — uderzenie, Scena 19 — klamra (najazd na farmę).
- E03: nowe otwarcie (cold open Mars, napis tytułowy, obrona farmy, Ziemia T+47 ...).
- Model: Omni Flash (nie Veo 3.1 Quality — nie obsługuje character references), ~10 s; Veo 3.1 baza ~8 s + Extend +7 s.

### 2d. Handoff 11.10 — przyjęte (ustalenia kanoniczne)
- Wirus Y/HYV-1; Adam = kryptonim; pacjent zero Kamiński; szczepionka jako warunek lądowania; 8:40.
- Ares 55 (40M/15K); Korańczyk w załodze (wątek z Karoliną).
- Metoda B domyślna dla Omni; A tylko Veo.
- Standard cięcia: beaty ~7 s (pierwszy klip może być dłuższy).
- Plan E01 Scena 1: klipy Clip00–11 metodą B (Omni), potem reszta E01 i czołówka, potem E02, E03, CapCut.

---

## 3. Status wdrożenia decyzji (weryfikacja grep w _rev.md / rozpisce)

| Decyzja | Gdzie sprawdzone | Status |
|---|---|---|
| 55 / 40 M / 15 K | E03 rev l.25 (obsada), l.37 („Czterdziestu żyjących mężczyzn"), l.767 („Pięćdziesiąt pięć osób"), l.1240 (nagłówek „CZTERDZIESTU ŻYWYCH MĘŻCZYZN") | WDROŻONE |
| „sześcioro" usunięte | E03 rev: brak „sześcioro/SZEŚCIORO" | WDROŻONE |
| Wirus Y / bez ADAM-1 | grep w E0*_rev i rozpisce: brak „ADAM-1" | WDROŻONE |
| Brak „Adam Kowalski" | rozpiska l.657–658: pasek zastąpiony neutralnym („NIEZNANA…"/„WIRUS Y: PIERWSZE POTWIERDZONE PRZYPADKI…") | WDROŻONE |
| Pacjent zero Kamiński | E02 rev l.364 („Tomasz Kamiński, W-wa, 14.03 — pacjent zero") | WDROŻONE |
| Napisy P1–P4 | E01 rev l.186, 431, 615, 869; rozpiska l.176, 486, 694, 974 | WDROŻONE |
| Ida / Scena 11 E02 usunięte | E02 rev: brak „Ida", brak „SCENA 11" (tabela 2052–2077 bez 11) | WDROŻONE |
| Kadr Scena 12 E03 = T+50 | E03 rev l.1235 „SCENA 12 ... T+50 dni" | WDROŻONE (konsultacja A6 proponowała T+49 — nieaktualne) |
| Opóźnienie 8:40 | E03 rev l.895 „opóźnieniem 8 minut 40 sekund" | WDROŻONE, ALE sprzeczność z napisem 78,3 mln km (sekcja 10) |
| Piotr wyjmuje próbkę (15A) | E03 rev l.1623–1643 (próbka z torby Piotra, „Dotrzymałem") | WDROŻONE |
| „LATA PÓŹNIEJ" z gazetą na końcu | E03 rev l.1776–1783 | WDROŻONE (treść do przebudowy) |
| Szczepionka = warunek przeżycia chłopców | E03 rev l.1444–1445 | WDROŻONE |
| Lądowanie po teście Piotra | E03 rev l.986, 1177 („warunek lądowania") | WDROŻONE |
| Korańczyk w obsadzie + 15A | E03 rev l.25, 1652 (DR TOMASZ KORAŃCZYK w 15A) | CZĘŚCIOWO: wątek półmiłosny po powrocie niepotwierdzony |
| Marta–Aga zasiane | E01 rev l.161–165 („ta koleżanka Agi Bryk ze studiów…") | WDROŻONE, ale zapis budzi zastrzeżenia (audyt A6) |
| Metraż E03: header 60→~64,5; suma 72→~64,5 | E03 rev l.3 „Czas: ok. 67 min"; l.1918 „ŁĄCZNIE ok. 74,5 min" | NIEWDROŻONE / SPRZECZNE (header 67, suma 74,5, decyzja ~64,5) |
| Metraż E01 (~52 + 62 s) | E01 rev l.3 „Format: ok. 60 minut"; rozpiska l.1558–1577 (54–55 min z czołówką i napisami, „o ok. 5 min poniżej") | NIEWDROŻONE / SPRZECZNE |
| Metraż E02 (~66–67) | E02 rev l.3 „Format: ok. 65 minut" | NIEWDROŻONE (drobne) |
| Sweter Michała nie wraca w E03 | nie sprawdzono (brak wzmianki w grep) | do weryfikacji |
| Wolska w epilogu (14a) | E03 rev l.1753 (Wolska w scenie przed „LATA PÓŹNIEJ") | NIEPEWNE |

---

## 4. Konsultacja i repercussje vs audyt 11.10

### 4a. Kolizja numeracji
Trzy dokumenty używają etykiet A–D, ale z RÓŻNĄ treścią:
- Konsultacja: A1–A7 (twarde), B1–B5, C1–C5, D1–D2.
- Audyt 11.10 (handoff §4): A1–A6, B7–B10, C11–C14, D15–D16 (16 punktów, ciągła numeracja).
- Repercussje: nie używa etykiet A–D, ale sekcja 13 odnosi się do „A1–A7".
Wniosek: w rozmowie „A4" znaczy co innego, zależnie od dokumentu. Przy zmianach trzeba podawać nazwę pliku i treść, nie samą etykietę.

### 4b. Konsultacja A1–A7 → stan
| Konsultacja | Treść | Stan |
|---|---|---|
| A1 | 6 osób / 3 mężczyzn (rekomendacja) | NIEAKTUALNE — decyzja 1 = 55/40/15; konsultacja świadomie „archiwalna" (repercussje 13) |
| A2 | próbka w teczce przed powrotem Piotra | WDROŻONE (Piotr podaje próbkę) |
| A3 | mężczyzna z gazetą łamie demografię (T+400) | PRZENIESIONE pod „LATA PÓŹNIEJ" (decyzja); konflikt treści nie rozstrzygnięty |
| A4 | 4:20 (jedna strona) vs 8:40 (odpowiedź) | Rozstrzygnięte w decyzjach na 8:40 tam i z powrotem — ALE audyt 11.10 A4 (sekcja 4 handoffu) proponuje zmianę napisu 78,3 → 156 mln km. SPRZECZNE (patrz sekcja 10) |
| A5 | oś czasu Very/Agi | WDROŻONE (napisy P2–P4) |
| A6 | Scena 12: T+47 → T+49 | NIEAKTUALNE — decyzja i rev: T+50 |
| A7 | metraż E03 60 vs 72 | NIEWDROŻONE — header 67, suma 74,5 |

### 4c. Konsultacja B/C/D → stan
- B1 (ironia nazwy „Adam" — Aga zauważa w starych notatkach): NIEROZSTRZYGNIĘTE. Decyzja 3 zostawia kryptonim, ale nie wybiera tropu Agi.
- B2 (kolizja „Kowalski" pacjent zero): ROZWIĄZANE przez decyzję 4. Nowa kolizja: Zofia Kowalska (E02 l.1416, 1429, 1435) — audyt D16.
- B3 (szczepionka jako warunek przyszłych chłopców): WDROŻONE w E03 l.1444–1445. Premisa „wracają 3 mężczyzn" NIEAKTUALNA (40 żyjących).
- B4 (Marta–Aga zasiew w E01): WDROŻONE (l.164), treść wymaga poprawki (audyt A6).
- B5 (sweter Michała znika w E03): decyzja mówi „sweter NIE powraca" — celowe odrzucenie konsultacji C1.
- C1 (sweter wraca w E03): ODRZUCONE przez decyzję („żałoba mija"). Do potwierdzenia przez Macieja.
- C2 (Ida jako motywacja Very): ODRZUCONE przez decyzję 6 (Ida usunięta).
- C3 (etyka „trzech mężczyzn", jedna scena o niewygodzie): premisa zmieniona na 40; pomysł audyt C12 — NIEROZSTRZYGNIĘTE.
- C4 (cichy kadr zamrażarki zamiast linijki o bankach spermy): NIEROZSTRZYGNIĘTE (E03 l.381, 946 — częściowo obecne, nie zweryfikowano pełnego kadru).
- C5 (Wolska w epilogu — zamknięcie łuku): decyzja 14a = kadr odbudowy; częściowo.
- D1 (E03 przeładowany, ~72 min): NIEROZSTRZYGNIĘTE; metraż E03 nadal sprzeczny.
- D2 (dyscyplina dat przy montażu równoległym): zależna od A6 — T+50 zrobione.

### 4d. Repercussje (2026-06-07) → stan
- Priorytet 1, pkt 1–7 (rozpiska): WSZYSTKIE WDROŻONE (grep potwierdził: pasek WIRUS Y, usunięty pasek Adam Kowalski, napisy P2/P3, Scena 9, Zero Day WHO, tabela Sceny 3 „wirusa Y / projekt Adam").
- Pkt 1h (metraż rozpiski): repercussje wpisał „~52 min 15 s + czołówka 62 s ≈ 53:20", a sama rozpiska w sekcji WERYFIKACJA (l.1575) pisze „54–55 min z czołówką i napisami". Różne liczby.
- Priorytet 2 (PDF-y): do regeneracji — PDF-y prawdopodobnie zregenerowane po rev 8.06, ale przed audytem 11.10.
- Pkt 11 (repercussje): „ZERO_kontekst_sesji.md — NIEOBECNE" — NIEAKTUALNE (plik jest w R i w paczce 11.10).
- Pkt 12–13: ZERO_decyzje_rewizja.md „STATUS AKTUALNY" — prawda; ZERO_konsultacja „HISTORYCZNY" — prawda, ale konsultacja nadal zawiera rekomendacje sprzeczne z decyzjami (sekcja 4b/4c).

### 4e. Audyt 11.10 (A1–D16) → stan (wszystkie NIEWDROŻONE; rev zmienione ostatnio 8.06)
- A1 Aga: „V. Strand. Kim jest?" — E02 l.410 (wciąż obecne). OTWARTE, najmocniejszy zgrzyt.
- A2 Wolska Katarzyna (E02 l.42, ~58) vs Anna (E03 l.915) — OTWARTE. (Zauważ: w handoffie „trzy Anny": Wolska, Sowa, Ford.)
- A3 publikacja Dąbrowskiego: E02 l.400 „osiemnaście lat temu" — OTWARTE (E01 P4 implikuje ~12).
- A4 dystans Mars: E03 l.765 „78,3 MLN KM" — OTWARTE, PATRZ SEKCJA 10 (sprzeczność logiczna).
- A5 „u twojej mamy sąsiadki": E01 l.1079 (wciąż obecne) — OTWARTE.
- A6 Marta o „koleżance… Marta ma na imię jak ja": E01 l.164–165 (wciąż obecne) — OTWARTE.
- B7 list w żółtej teczce: E02 l.1972 („Zapieczętowana koperta — list, którego Marta jeszcze nie otworzyła") — OTWARTE.
- B8 termiczny pojemnik Very: E03 l.1247 („zamknięty pojemnik termiczny") — OTWARTE.
- B9 „dwie sekwencje / odporność": OTWARTE (pomysł „ratunek farmy" w handoffie).
- B10 los Zofii: OTWARTE (E03 sc. 17 zakłada, że żyje).
- C11 beat śmierci Dąbrowskiego: OTWARTE.
- C12 „czterdziestu mężczyzn" — scena niewygody: OTWARTE.
- C13 antidotum vs szczepionka: OTWARTE — E03 miesza: „antidotum" l.475, 487, 512, 1260, 1430; „szczepion" l.974–1445.
- C14 Karolina–Korańczyk: OTWARTE (zasiane w 15A; beat po powrocie nie potwierdzony).
- D15 numeracja scen E02 (5A, 6A, 6B, 6C, 7A, 12A, 15, 16; brak 11): OTWARTE (E02 l.2052–2077: „Scena 12A", „Scena 18", brak 11).
- D16 „Zofia Kowalska" (kolizja z Kowalskimi): E02 l.1416, 1429, 1435 — OTWARTE.

---

## 5. Veo 3.1 vs Kling — rekomendacja i wdrożenie
- Werdykt pliku: „Kling jest dobrym wyborem do tego projektu" i „Kling wygrywa kosztem i długością klipu". Veo zostaje jako zapas. To mocna rekomendacja zmiany modelu.
- Handoff 11.10 (§7, §9, §10): Kling jako BACKUP do dialogów — „do przetestowania". Produkcja nadal w Flow (Omni Flash).
- Wdrożenie: NIE. Brak plików wideo/promptów Kling w R. Brak wyniku testu.
- Wątpliwości liczbowe: „ok. 56% taniej" nie wynika z podanych stawek (Kling 0,07–0,14 $/s vs Veo 0,40–0,75 $/s; średnie ~82% taniej, zakresy ~65–90%). Wymaga sprawdzenia źródła.
- Nieaktualne w pliku: „Pierwsza klatka: tak (Frames-to-Video — tylko Veo 3.1, nie Omni Flash)" oraz „Kling: screenshot-bridge zadziała (inaczej niż Omni Flash)". Metoda A/B (korekta) potwierdza, że Omni Flash też ma Start Image / Save frame. SPRZECZNE.
- Nazwa pliku w pliku: „ZERO_E01_S1_Clip2.md" — w R jest „ZERO_E01_S1_Clip02.md" (drobne, ale przy kopiowaniu beatów może mylić).

---

## 6. Instrukcje dla agenta Flow vs handoff 11.10
Spójne z handoffem w: L/P (Michał LEWO, Karolina PRAWO), jeden zielony dinozaur na sweterze Michała, Karolina bez swetra/dinozaura/obrączek, stałe tło Nowego Światu, światło złote z lewej, dialogi EN (napisy PL w post), jedna osoba mówi naraz, bez muzyki (tylko ambient), pacing startu/końca, brak tekstu w kadrze.

Rozjazdy:
- Długość: „Uwaga: na Veo 3.1 baza klipu ~8 s" i przykład „8 seconds"; handoff: beaty ~7 s, Omni do 10 s. Drobne, ale nie ujednolicone.
- Zakres powtarzania opisu: instrukcje — „każdy prompt dodaje tylko kamerę, kto mówi + kwestię, blocking" (reszta z panelu). Metoda A/B — „W KAŻDYM prompcie trzeba DOKŁADNIE opisać każdą postać: wygląd ORAZ pełny ubiór… Powtarzać przy każdym ujęciu". SPRZECZNE w praktyce. Zalecenie: obie zasady (panel + skrót kluczowych cech w każdym prompcie).
- Model: instrukcje wspominają tylko Veo 3.1; handoff/metoda — Omni Flash dla E01 S1. Panel „Instrukcje" działa dla obu? Niezweryfikowane.
- Karolina „dark brown shoulder-length hair" (instrukcje) vs „medium-length" (kontekst 06-07). Drobne.

---

## 7. Handoff 8.06 vs handoff 11.10 — co się zmieniło
Nadpisany: ZERO_HANDOFF_przekazanie.md (8.06) — 11.10 deklaruje zastąpienie.

Zmiany w 11.10:
1. Nowy audyt spójności (§4), 16 punktów (A1–D16). Część pozycji (Wolska, Zofia, Dąbrowski, Mars) jest w decyzjach otwartych.
2. Nowa sekcja decyzji otwartych (§5) — 8 pozycji.
3. Poprawiona ścieżka: OneDrive `C:\Users\macie\OneDrive - NASTER S.A\Pulpit\01_Projekty\zero` (8.06 podawało `...\Pulpit\zero`); obejście „files on-demand" (podłączyć folder nadrzędny).
4. Nowa paczka i jej zawartość (§9), plik `ZERO_PACZKA_PRZEKAZANIE_2026-10-11.zip` (nie widziany w R — nieweryfikowane).
5. Plan generowania uporządkowany (§7 „Plan generowania", §10 „Następne kroki"): najpierw E01 Scena 1 (klipy 0→11, metoda B), potem reszta E01, E02, E03, CapCut.
6. Wzmianka o Kling jako backup (§7) — w 8.06 już była.
7. Pułapka PDF w czytniku — w obu.

Bez zmian (przeniesione): kanon postaci, zasady stałe Flow, metoda A/B, Omni vs Veo, lektor w CapCut.

Rozjazdy wewnątrz handoffu 11.10:
- Status klipów Sceny 1: §9 mówi „ZERO_VEO3_E01_Scena1_ENG_v4.md — aktywne prompty (7 klipów EN)", §7 i §10 mówią „Clip 0→11" (12 plików Clip00–11). SPRZECZNE.
- Metraż: nagłówek „E01 ~65 min, E02 ~67, E03 ~67" vs rev (60, 65, 67) vs rozpiska (54–55) vs decyzje (52, 66–67, ~64,5). SPRZECZNE.
- Wolska: §2 mówi „NIESPÓJNOŚĆ" bez rozstrzygnięcia; §5 rekomenduje Katarzyna. Zgodnie z E02 rev.
- §2 „Ares… 40 mężczyzn na pokładzie" — ok; §3 „Ares 55" — ok.
- Mars: §2 „Opóźnienie ~8:40" i §4 pkt 4 proponuje napis 156 mln km — SPRZECZNE (sekcja 10).

---

## 8. ZERO_kontekst_sesji.md (najstarszy) — co nieaktualne
Nieaktualne:
- „Model: Omni Flash… Limit klipu: 9 sekund maksimum" → Omni ~10 s; beaty ~7 s.
- „ZERO_VEO3_E01_Scena1_ENG_v4.md — AKTYWNY, 7 klipów" → v4 vs Clip00–11 (sprzeczne w handoffie 11.10).
- Workflow: „screenshot ostatniej klatki (Win+Shift+S) → Image to video → FIRST FRAME" → zastąpione metodą B (Save frame → Start Image, w Flow, bez zrzutów ekranu).
- „Następny krok: generowanie Clip 0" → zrobione (metoda_AB: CLIP 0 ✅).
- „Lokalizacja: folder outputs w Claude Cowork" → OneDrive `01_Projekty\zero`.
- „Wszystkie klipy muszą być wygenerowane od nowa" → nieaktualne (Clip 0 zrobiony wg metody_AB).
- Tabela plików „archiwum" → częściowo nieaktualna (E01 ENG_v4 aktywny; plików 6–7 wariantów).
- Problem „bridge text nie działa" — nadal aktualne (nie usunięte w 11.10, nie potwierdzone ponownie).
Nadal aktualne: postacie (Michał LEWO, sweter z jednym dinozaurem; Karolina PRAWO, zielona kurtka), zasada „EXACTLY ONE dinosaur", „NO music", dialogi EN (tabela tłumaczeń), polski lektor w CapCut, auto-napisy → PL, dźwięk ambient.

---

## 9. Zasady produkcyjne, które musi znać następna sesja
1. Modele: Omni Flash — do ~10 s, najlepsza zgodność twarzy (Entity), BEZ Extend. Veo 3.1 — baza ~8 s, Extend +7 s (tylko klipy Veo). Veo 3.1 Quality nie obsługuje character references. Veo nie przyjmuje twarzy realnych osób.
2. Metoda A = Extend (Veo 3.1, jedno ciągłe ujęcie). Metoda B = nowe ujęcie z Start Image (Save frame → Start Image + Entity + akcja; działa w Omni Flash). Domyślnie B. Agent MUSI podać A lub B przed każdym ujęciem.
3. Długość beatu: ~7 s dialogowe; pierwszy klip może być dłuższy; Kling (jeśli testowany) do 10 s.
4. Postacie: Michał zawsze LEWO (żółty sweter, DOKŁADNIE JEDEN zielony dinozaur na piersi, brązowe włosy średniej długości). Karolina zawsze PRAWO (zielona kurtka nad jasnym topem, BEZ swetra/dinozaura, gołe dłonie — bez obrączek/biżuterii, ciemne włosy). Nigdy nie zamieniać stron ani nie lustrzyć kadru.
5. Tło: stały fragment Nowego Światu, statyczny i identyczny (rusza się tylko tramwaj, przechodnie, gołębie). Światło: złote, wiosenne rano, z lewej.
6. Dialog: po angielsku; jedna osoba mówi naraz; druga z zamkniętymi ustami; bez napisów wypalonych w kadrze; bez muzyki (tylko ambient ulicy); mówiący startuje ~0,5–1 s, kończy pod koniec klipu.
7. Każde ujęcie: w osobnym pliku (Clip00 … Clip11 dla Sceny 1).
8. Post (CapCut): złożyć klipy → lektor PL nagrany osobno → nałożyć głos → auto-napisy EN podmienić na PL → muzyka jako osobna warstwa (NIE w klipach Flow).
9. Flow bywa przeciążony — generować rano (PL).
10. Workflow scenariusza: backup do `_backups/` z datą PRZED każdą zmianą → edycja → regeneracja czytanki PDF (zamknąć PDF w czytniku, inaczej nie nadpisze się) → pokazać plik. Pliki PDF: do TTS, nie TXT (polskie znaki).
11. Praca z Maciejem: zwięźle, po polsku; pytania POJEDYNCZO w treści; w korekcie językowej NIE zmieniać dialogów (propozycje tylko w trybie recenzji, do akceptacji).
12. Ścieżki: aktualne `_rev.md` w korzeniu projektu; `ZERO_DO_PRZENIESIENIA/` — identyczne kopie (md5); `_archiwum/`, `_backups/` — historia.

---

## 10. KONFLIKTY między dokumentami (z lokalizacją)

K1. Mars: napis „78,3 MLN KM" vs opóźnienie 8:40 (ODPOWIEDŹ).
   - E03 rev l.765 (napis), l.895 („opóźnieniem 8 minut 40 sekund"); decyzje (E03: 8:40 tam i z powrotem, 4:20 = jedna strona); handoff 11.10 §4 pkt A4 (sugeruje 156 mln km).
   - Fizyka: 78,3 mln km ÷ c ≈ 261 s ≈ 4 min 21 s w jedną stronę; tam i z powrotem ≈ 8 min 42 s ≈ 8:40. Napis 78,3 mln km jest ZGODNY z 8:40 jako czasem odpowiedzi. Propozycja audytu A4 (156 mln km) zepsułaby to: tam-z-powrotem wyszłoby ~17 min.
   - Wniosek: audyt A4 ma błędne założenie (traktuje 8:40 jako jedną stronę). Rekomenduję NIE zmieniać napisu; zamiast tego doprecyzować w scenie, że 8:40 to czas oczekiwania na odpowiedź.

K2. Metraż E03: header ok. 67 min (l.3) vs tabela ŁĄCZNIE ok. 74,5 min (l.1918) vs decyzja „baza ~64,5" vs handoff „~67". Plus uwaga produkcyjna (l.1920): „montaż może zredukować 5–8 min; cel ok. 67".

K3. Metraż E01: header „ok. 60 minut" (rev l.3) vs decyzja „~52 min + czołówka 62 s" vs rozpiska „54–55 min z czołówką i napisami" (l.1575) vs repercussje „≈53:20" vs handoff „~65 min". Potrzebna jedna liczba i poprawka nagłówka.

K4. Metraż E02: header „ok. 65" (rev l.3) vs decyzja „~66–67" vs handoff „~67".

K5. Scena 1 klipy: metoda_AB (CLIP 0–6, 7 klipów, v4) vs handoff 11.10 §7/§10 (Clip 0→11, 12 plików w R: ZERO_E01_S1_Clip00–11.md) vs handoff §9 (v4 „aktywny, 7 klipów").

K6. Metoda Omni Flash i pierwsza klatka: porownanie (sekcja „Tabela": Frames-to-Video tylko Veo; Kling „inaczej niż Omni") vs metoda_AB („Korekta: pierwsza klatka JEST dostępna też w Omni Flash").

K7. Kling: porownanie („Kling wygrywa"/„dobry wybór") vs handoff 11.10 §7/§10 (backup, do przetestowania).

K8. Zakres opisu postaci w prompcie: metoda_AB („w KAŻDYM prompcie… pełny ubiór… powtarzać") vs instrukcje_Flow („każdy prompt dodaje tylko akcję").

K9. Długość klipu: instrukcje („Veo baza ~8 s"; przykład „8 seconds"), handoff („beaty ~7 s", Omni ~10 s).

K10. Wolska: E02 l.42 „Katarzyna ~58" vs E03 l.915 „Anna Wolska" (handoff 11.10 A2; decyzje: nie rozstrzygnięte).

K11. Premisa „3 mężczyzn wracają" (konsultacja A1/B3/C3 — nieaktualne) vs decyzja 1 (40 żyjących). Konsultacja jest „historyczna", ale nadal zawiera premisę w B3/C3.

K12. Sweter Michała: konsultacja C1 (ma wrócić w E03) vs decyzja („NIE powraca"). Decyzja wygrywa; do potwierdzenia.

K13. Scena 12 E03: konsultacja A6 (T+49) vs decyzja/rev (T+50). Rev wygrywa.

K14. Decyzje pkt 1 mówi „6 postaci z imienia"; E03 l.25 ma 7 (dopisany Korańczyk). Drobne; zgodne z intencją.

K15. Kolizje imion/nazwisk: Anna (Wolska, Ford, Sowa — handoff); Kowalska (Marta, Zofia — E02 l.1416); Tomasz (Kamiński pacjent zero, Korańczyk, Tomek Wiśniewski w E01 — zdrobnienia). Audit D16 dotyczy tylko Zofii.

K16. Konsultacja B1 (ironia nazwy) vs decyzja 3 (świat nie wie, Vera wie). Niekonfliktowe, ale B1 sugeruje dodatkowy trop, którego decyzja nie zawiera.

K17. Repercussje (pkt 11) — „ZERO_kontekst_sesji.md NIEOBECNE" — nieaktualne.

K18. Repercussje pkt 1h: metraż E01 „53:20" vs rozpiska „54–55".

K19. Kling/Veo: „56% taniej" nie wynika z podanych stawek (sekcja 5).

K20. Pliki w porownanie: „ZERO_E01_S1_Clip2.md" vs „Clip02.md" w R.

K21. Konsultacja A7 i decyzje pkt E03 („poprawić nagłówek i sumę na ~64,5") — NIE zrobione (K2).

---

## 11. Otwarte pytania (do Macieja) — po wszystkim
1. Wolska: Katarzyna ~58 (E02) czy Anna 51 (E03)? Rek.: Katarzyna.
2. Los Zofii: żywa-ranna (teraz) / ciężko ranna / umiera. Sc. 17 E03 zakłada, że żyje.
3. Data publikacji Dąbrowskiego: ujednolicić do ~12 lat (E02 l.400 mówi 18).
4. Mars: zostawić 78,3 mln km (zgodne z 8:40 tam-z-powrotem) czy zmienić? Rek.: zostawić + doprecyzować w scenie.
5. E02 l.410: „V. Strand. Kim jest?" → rozpoznanie matki (najmocniejszy zgrzyt A1).
6. Pojemnik termiczny Very (E03 l.1247) i zapieczętowany list (E02 l.1972): domknąć czy wyciąć.
7. Wątek odporności / „ocalały chłopiec" (ratunek farmy): rozwijać czy nie.
8. Kling: adoptować jako model główny (porownanie) czy backup (handoff)? Test potrzebny.
9. Sweter Michała w E03: decyzja „nie wraca" — potwierdzić (konsultacja C1 sugeruje powrót).
10. Antidotum vs szczepionka: jedno słowo w całym E03 (audyt C13). Rek.: „szczepionka".
11. Metraż: jedna liczba dla każdego odcinka i poprawka nagłówków/sum (K2–K4).
12. Scena 1: czy aktywne są Clip00–11 (12) czy v4 (7)?
13. Ile mężczyzn z Ares IV wraca na Ziemię i jak to wybrzmiewa w E03 (premisa 40 żyjących)?
14. Beat Karolina–Korańczyk po powrocie: napisać czy zostawić jako nutę?
15. Konsultacja C4 (cichy kadr zamrażarki) i D1 (skrócenie E03): tak/nie?

---

## 12. Rekomendacje (dla następnej sesji)
1. Najpierw zamknąć 15 pytań z sekcji 11 (szczególnie 1, 4, 5, 8, 11, 12) i zapisać decyzje w ZERO_decyzje_rewizja.md z datą — obecny log nie ma dat i sprzeczne rekomendacje konsultacji nie są oznaczone jako odrzucone.
2. Wstrzymać zmianę napisu 78,3 mln km (audyt A4) — wg fizyki i decyzji 8:40 to poprawne. Zamiast tego dopisać w scenie, że 8:40 = oczekiwanie na odpowiedź.
3. Ujednolicić metraż: jedna liczba na odcinek; poprawić header E01 (60), E02 (65), E03 (67) i sumę E03 (74,5) — zgodnie z decyzją ~52 / ~66–67 / ~64,5 lub z realnym montażem.
4. Przed generowaniem Sceny 1 jednoznacznie wskazać aktywne pliki (Clip00–11 vs v4 CLIP 0–6) i zaktualizować metoda_AB oraz handoff §9.
5. Dodać do instrukcji Flow zasadę „pełny opis postaci w każdym prompcie" albo zaakceptować skrót — jedna reguła. Ujednolicić długość beatu (7 s) i zaktualizować porownanie_Veo_vs_Kling (Start Image w Omni, stawki/56%).

---

## Załącznik A — szybkie referencje (linie w _rev.md, wersja R)
- E01 rev: l.3 (Format 60), l.164–165 (Marta–Tomek, zasiew), l.186 (P1), l.431 (P2), l.593–594 (pasek WIRUS Y), l.615 (P3), l.869 (P4), l.932 (WHO pasek), l.1079 („u twojej mamy sąsiadki"), l.1195 (WHO: wirus Y, HYV-1), l.273 / 919 („Adam" kryptonim).
- E02 rev: l.3 (Format 65), l.42 (Katarzyna Wolska ~58), l.364 (Tomasz Kamiński pacjent zero), l.400 („osiemnaście lat temu"), l.406/410 („V. Strand. Kim jest?"), l.1416/1429/1435 (Zofia Kowalska), l.1972 (list), l.2052–2077 (tabela scen bez 11).
- E03 rev: l.3 (Czas 67), l.25 (obsada 55/40/15 + Korańczyk), l.37 (czterdziestu żyjących), l.381 / 946 (próg termiczny), l.475/487/512/1260/1430 („antidotum"), l.765 („78,3 MLN KM"), l.767 („Pięćdziesiąt pięć osób"), l.785–814 (populacja, „Wszyscy"), l.895 (8:40), l.915 („Anna Wolska"), l.954 („Czterdziestu z pięćdziesięciu pięciu"), l.974–1445 („szczepionka"), l.1213/1223 („Wracamy"), l.1240 („CZTERDZIESTU ŻYWYCH MĘŻCZYZN"), l.1235 (T+50), l.1247 (pojemnik termiczny), l.1444–1445 (szczepionka — warunek chłopców), l.1623–1643 (próbka Piotra), l.1652 (Korańczyk w 15A), l.1753 (Wolska), l.1776–1783 („LATA PÓŹNIEJ", gazeta), l.1882 („WIRUS Y POZOSTAJE AKTYWNY"), l.1918 (ŁĄCZNIE 74,5), l.1920 (cel 67).
- Rozpiska: l.176 (P1), l.282/1039 („Adam" kryptonim), l.486 (P2), l.657–658 (paski — zmienione), l.694 (P3), l.974 (P4), l.1065 (Scena 9 pasek), l.1444 (WHO Zero Day), l.1524 (tabela Sceny 3), l.1558–1577 (weryfikacja metrażu).

## Załącznik B — pliki Scena 1 w R
ZERO_produkcja_flow/ZERO_E01_S1_Clip00.md … Clip11.md (12 plików) — w R. ZERO_VEO3_E01_Scena1_ENG_v4.md (7 klipów, CLIP 0–6) — w korzeniu R. Inne: ZERO_VEO3_E01_Scena1_FULL_ENG(.md, _edited), ZERO_Scena1_beaty_7s_ENG.md, ZERO_VEO3_TEST_Scena1_Epilog_ENG.md, ZERO_INSTRUKCJA_Flow_scena1_ciaglosc.md (nieczytane w tej sesji).
