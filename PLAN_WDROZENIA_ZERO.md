# ZERO — przegląd projektu i plan wdrożenia

Stan na 2026-11-27. Przygotowane na podstawie pełnego przeglądu archiwum `Zero.rar` (147 plików + 2 wewnętrzne ZIP-y).

> **Jak powstał ten dokument.** Pliki czytało 7 równoległych agentów (każdy dostał listę plików do przeczytania w całości); notatki szczegółowe są w `docs/przeglad-2026-11-27/`. Ja sam przeczytałem handoff z 11.10.2026, `00_WELCOME`, `_CZYTAJ_NAJPIERW`, `ZERO_kontekst_sesji`, porównałem duplikaty i sprawdziłem w plikach `grep`-em najważniejsze twierdzenia (zaznaczone ✔). Numery linii pochodzą z raportów agentów i odnoszą się do plików `_rev.md`; te oznaczone ✔ zweryfikowałem sam.

---

## 1. Czym jest projekt

- **ZERO** — polski mini-serial sci-fi / dramat społeczny, **3 odcinki**: E01 ADAM, E02 EWA, E03 ARES. Autor koncepcji: Maciej Sieracki („Naster").
- **Premisa:** wirus Y (kliniczne HYV-1) zabija prawie wszystkich mężczyzn; świat staje się światem kobiet. Główny wątek to odbudowa i wina Very Strand (twórczyni wirusa, matka Agi). Drugi plan: misja marsjańska Ares IV (40 mężczyzn, nie mogą wrócić, dopóki nie powstanie szczepionka).
- **Ton:** powściągliwy — „świat nie kończy się w ogniu, tylko powoli, w kolejkach i ciszy".
- **Metoda produkcji:** wszystko z AI. Scenariusz, wideo w Google Flow (Veo 3.1 / Omni Flash), post-produkcja w CapCut. Zakładany głos: dialogi generowane po angielsku, polski lektor i napisy w montażu.
- **Oś czasu:** T-14 (E01) → T0 „Zero Day" → T+8 statek-widmo (E01) → T+9 uderzenie (E02) → T+13 najazd na farmę → T+47–50 (E03, Ziemia) → T+295 lądowanie → T+430 epilog.
- **Gdzie jesteśmy:** napisane są trzy scenariusze i trzy czytanki; do wideo przygotowano ok. połowy E01. **Żaden gotowy klip nie jest w archiwum.**

## 2. Co jest w archiwum

| Grupa | Pliki | Status |
|---|---|---|
| **Aktualne scenariusze** | `ZERO_mini_serial_E01/E02/E03_*_rev.md` | Źródło prawdy. Ostatnia zmiana 8.06.2026 — **audyt z 11.10 nie jest w nich wdrożony.** |
| **Handoff nadrzędny** | `ZERO_HANDOFF_2026-10-11.md` | Kanon, audyt A1–D16, decyzje otwarte. Zawiera kilka błędów (p. 4A). |
| **Czytanki** | 3 × PDF | Aktualne, ale generator ma błędy (p. 4D). |
| **Produkcja E01** | `ZERO_E01_produkcja/` (8 dokumentów), `ZERO_produkcja_flow/` (46 plików) | Aktualne, z niespójnościami (p. 4B–4C). |
| **Historia** | `_archiwum/`, `_backups/`, `ZERO_kontekst_sesji.md`, `ZERO_HANDOFF_przekazanie.md` (8.06) | Nie używać do pracy. |
| **Duplikaty** | `ZERO_DO_PRZENIESIENIA/` i `ZERO_PACZKA_PRZEKAZANIE_2026-10-11.zip` | Identyczne z plikami głównymi (jedyna różnica: `00_WELCOME.md`). Można pominąć. |
| **Nie dotyczą serialu** | `Planify-przekazanie-2026-10-11.zip`, `HANDOFF-DRAFT.md` (to handoff Planify), 2 × `Budżet_pitch_deck…xlsx`, `Energomat_koszty_krytyczne…xlsx` | Planify wskazałeś jako błąd. Oba budżety i plik kosztów to model finansowy spółki Energomat — **budżetu ZERO w archiwum nie ma.** |

Uwaga techniczna: przy rozpakowaniu `unrar` obcina nazwy z „ż" (`Bud…`) i nadpisuje jeden plik drugim; `unar` zachowuje nazwy, ale gubi 8 plików. Do importu trzeba użyć jednego i drugiego albo spakować archiwum ponownie w ZIP.

## 3. Stan faktyczny

| Obszar | Stan | Szczegóły |
|---|---|---|
| Scenariusz E01 | Gotowy, wymaga poprawek | 13 scen + montaż „Zero Day" + sc. 15; bloki przeszłości P1–P4; 4 wstawki medialne; ok. **60,5 min** |
| Scenariusz E02 | Gotowy, wymaga porządku | PROLOG + 28 bloków (w tym 3B, brak nr 11), numeracja i chronologia pomieszane; nagłówek 65 min, tabela 69–70,5, realnie **72–73,5 min** |
| Scenariusz E03 | Gotowy, wymaga poprawek | 17 scen + cold open + klamra + 15A; nagłówek 67 min, tabela 73,5/74,5; „LATA PÓŹNIEJ" nadal placeholder |
| Czytanki PDF | Działają, 3 klasy błędów | p. 4D |
| Prompty wideo E01 | ~50% pokrycia | 257 beatów ≈ 30 min; brak plików dla **sc. 13 (~17 beatów) i sc. 15 (~13 beatów)** |
| Scena 1 | Nie wygenerowana | Tylko Clip00 oznaczony „GOTOWE", w archiwum brak wideo i zrzutów; brak jednej wersji wykonawczej |
| E02, E03 prompty | Brak | |
| Postacie w Flow | 2 z ~25 | Zapisani tylko Michał i Karolina |
| Budżet ZERO | Brak | |
| Muzyka, lektor | Brak decyzji | |
| Licencje i prawa | Brak | |
| Dystrybucja | Nie określona | |

## 4. Najważniejsze ustalenia przeglądu

### A. Korekty do handoffu z 11.10 (ważne — handoff się myli)

1. **A4 (dystans Mars) — nie wdrażać.** Handoff każe zmienić napis „78,3 MLN KM" na ≈156 mln km, zakładając, że 8:40 to czas w jedną stronę. ✔ 78,3 mln km to ≈4:21 w jedną stronę, czyli **8:40 to czas tam i z powrotem**, a napis (E03 l. 765) jest poprawny. Do ustalenia tylko słownictwo: E03 l. 895 mówi „z opóźnieniem 8 min 40 s" o pojedynczej transmisji, a l. 902/1030/1085 o czekaniu na odpowiedź (to jest spójne z rundą). Zapisać w kanonie: *8:40 = czas oczekiwania na odpowiedź*.
2. **„Aktywna" wersja Sceny 1 nie jest jednoznaczna.** Handoff §9 wskazuje `v4` (7 klipów), §7 i §10 mówią o Clip 0→11 (12 klipów). `v4` ma błędy (p. 4C). Wykonawczo wygląda na parę `Clip00–11` + `ZERO_instrukcje_dla_agenta_Flow.md` — **do potwierdzenia.**
3. **E01 ma 13 scen + Zero Day + sc. 15, nie „14 scen".**
4. **Metraż niespójny wszędzie:** E01 — nagłówek 60, decyzja ~52, rozpiska 54–55, handoff ~65. Podobnie E02 i E03 (p. 3). Tabela podsumowania w rozpisce sekundowej ma błąd rachunkowy (teraźniejszość 35:00, nie 28:15; razem 59:00, nie 52:15), więc wniosek „odcinek krótszy o 7–8 min" jest fałszywy.
5. **Los Zofii** — scenariusz E03 już zakłada, że żyje (✔ pojemnik i Zofia nie mają rozstrzygnięcia, ale sc. 17 pokazuje ją zdrową).

### B. Spójność kanonu (do naprawy przed zdjęciami)

**Osoby:**
- **Wolska:** E02 „Katarzyna ~58" (✔ l. 42), E03 „Anna, 51" (✔ l. 13, 915), beat T-1 „ok. 48"; w E02 też „Pani Premier" vs „Wicepremier" i „Ania" z PSE. Rekomendacja: **Katarzyna ~58, wicepremier** (unika trzech Ann: Wolska, Sowa, Ford).
- **Zofia:** „Zofia Kowalska" (E02 sc. 12A) — Kowalski to nazwisko Piotra; E03 l. 180 „wuj" Zofii, a w E02 brak męża.
- **Michał:** `02_charakterystyki` mówi „Wiśniewski", kanon Zawadzki.
- **Karolina:** `02_charakterystyki` i beaty sc. 9/10 mają „jasne włosy, bluza"; kanon: ciemne włosy, zielona kurtka.
- **Piotr** nie występuje w scenach E01 (tylko w obsadzie i nocie), choć cliffhanger noty go zakłada.

**Czas i fabuła:**
- **Bloki przeszłości:** scenariusz P2 = Vera 35 („11 lat po przyjeździe"), P3 = Vera 49 („25 lat"); dokumenty produkcyjne 01/06/08 mają 28 / 46 i napisy „CZTERY LATA" / „OSIEMNAŚCIE LAT" — `03` l. 74 „mała Aga" w P2 jest wtedy niemożliwa. Poprawić dokumenty, nie scenariusz.
- **Data publikacji Dąbrowskiego:** ✔ E02 l. 400 „osiemnaście lat temu" vs E01 P4 (Vera 52, ~12 lat); E01 l. 886 „pięć lat + trzynaście lat przed tym" = 18. Ujednolicić do ~12.
- **A1** ✔ E02 l. 410 „V. Strand. Kim jest?" — Aga pyta o własną matkę; podkopuje reveal. A dodatkowo E01 P2 „Mamma!" (l. 514) zdradza ten reveal widzowi już w E01, wbrew nocie.
- **A5** ✔ E01 l. 1079 „u twojej mamy sąsiadki" (dzieci są u niani Bożeny); beat sc. 12 też bez poprawki.
- **A6** E01 l. 164–165 — Marta pyta o „koleżankę Agi… Martę", czyli o siebie w 3. osobie.
- **E01 cliffhanger:** nota (l. 26–27) obiecuje teczkę + zdjęcie Piotra + Agę przy zwłokach Pawła; w montażu go nie ma (l. 1157–1224). Dąbrowski nie ma beatu śmierci (C11).
- **E01 chronologia:** W1 (T-10) po sc. 4 (T-9); sc. 8 (T-8) po sc. 7 (T-7); sc. 9 (T-6) po W3 (T-5). Sc. 10 „po wczoraj nic" przeczy SMS-owi 09:47 „Jestem w szpitalu".
- **E02 chronologia:** sc. 3B (T+6) przed 4 (T+5); 6A (noc) przed 6B (19:15); 8 po 6C; mapa „trzy punkty" vs „jeden zielony"; kolejność 16 przed 15; PSE raz w Bydgoszczy, raz w Warszawie.
- **E03:** ✔ pojemnik Very (l. 1247) bez dalszego wątku; „antidotum" (7×) vs „szczepionka" (8×); test na ochotniku nigdzie nie pokazany, a napis końcowy mówi „zatwierdzone dnia lądowania"; „Jestem komandorem misji" (l. 1166, komandorem jest Ford); „trzech tygodni" (l. 335 — powinno być ok. pięciu); „248 dni" / „start za 7 dni" vs lądowanie T+295; brak w obsadzie Joanny, Kamili Wiśniewskiej, Reifa, gen. Sowy.
- **Wątki zawieszone:** list w żółtej teczce (E02 l. 1972), pojemnik Very, „dwie sekwencje / to niemożliwe" (E01 sc. 14), ocalały chłopiec / odporność. To jeden powiązany problem — patrz decyzja D8.
- **Zasada „bez mężczyzn w tle" w E02 jest łamana:** prolog „cienie martwej załogi" (l. 70–72), zdjęcie Pawła (sc. 3, l. 368–370), zdjęcia Piotra (sc. 18, l. 1969–1971), „niski głos" w śpiewie (sc. 17, l. 1949), „Inni wynoszą rzeczy" (sc. 12).
- **Język:** E01 nota mówi „Vera mówi po polsku przez cały E01", a w scenach są kwestie po norwesku zapisane po polsku (l. 281, 513–516, 711–754, 900). Rodzaj: „MINISTER" (m.) przy „osiem kobiet".
- **Literówki** (nie poprawiano): zebrane w notatkach `E01_scenariusz.md`, `E02_scenariusz.md`, `E03_scenariusz_i_PDF.md`.

### C. Produkcja wideo — co blokuje generowanie

- **Model:** handoff = Omni Flash (bez Extend, ~10 s); instrukcja i FULL = Veo (z Extend, baza ~8 s); beaty = 7 s. Metoda B (Save frame → Start Image) działa też w Omni — dokument porównujący Veo z Klingiem twierdzi inaczej (nieaktualne).
- **Dwa różne podziały Sceny 1** (Clip 0–6 vs Clip00–11) bez mapowania; dwie procedury (pełny blok promptu vs akcja + reguły w panelu).
- **Błędy w `v4`:** kl. 0 Michał mówi w ujęciu „bez dialogu"; kl. 4 Karolina „CENTER or slightly RIGHT"; kl. 5/6 dinozaur na plecach. FULL kl. 0: „distant cafe music" łamie „bez muzyki". Poprawka „Karolina nie w swetrze + blokada tła" jest tylko w `FULL_edited` i w pliku reguł.
- **Brakujące kwestie:** w FULL/edited brak 4 kwestii (m.in. „He still brings them to me…", „Answer it…", „Mom, I have class in eight minutes"); kwestii Marty-matki („basement keys", „see you tonight") brak wszędzie poza `v4`.
- **Rozjazdy kanonu sc. 1:** scenariusz „dinozaur w okularach" ✔ (E01 l. 73, 994) vs prompty „dokładnie jeden zielony dinozaur" bez okularów; scenariusz chce ciepłej muzyki ambientowej, reguły Flow zakazują muzyki; tytuł „ZERO" generowany w Veo (reguła: tekst w CapCut); **podwójny tytuł** (czołówka 50–55 s i kl. 0); światło murka z prawej w INTRO, z lewej w sc. 1.
- **Reguły łamane w beatach:** „Zero Day" ma cue muzyczne w klipach Flow; P3 b11 ma dwóch mówców; 4 linie powyżej ~21 słów (nie zmieszczą się w 7 s); beaty sc. 2–14 nie powtarzają zasad lewo/prawo i blokady tła (sc. 1 odsyła do instrukcji); „WT T-7 b2–4" duplikuje T-10; T-5 koliduje z sc. 10.
- **Postacie (Entity):** są 2 z ~25; dla E02/E03 potrzebne m.in. Marta, Aga, Zofia, Vera (w E01 w 5 wiekach), Wolska, Sowa, Ford, Piotr, Dąbrowski, dzieci.
- **Lip-sync Veo zawodny** — strategia dialogów wymaga decyzji i testu (p. 5, D3).
- **Trudne dla AI:** sc. 15 (martwi mężczyźni na statku — ryzyko filtrów), montaże z wieloma ujęciami, ekrany, mapy, paski TV i polskie napisy w kadrze (generować w post), sc. 6C w E02 (4 min o mapie).

### D. Czytanki PDF (generator do naprawy)

Kontrola 3 PDF-ów (E01 27 str., E02 45, E03 39): polskie znaki poprawne, wszystkie kończą się „Koniec odcinka.", dialogi pokryte w 87–97%. Błędy generatora:
- zamiana „:" i „--" na kropkę z małą literą (E01 29, E02 37, E03 57 miejsc: np. „sygnałów. szum");
- didaskalia i opisy akcji zostają w tekście (E01 4, E02 7, E03 11 wystąpień „UJĘCIE");
- role bez kropki (E03: 244 linie); smiley „Cześć.)" (E01); „Ares Iv" zamiast „ARES IV";
- **E03: brak wszystkich pięciu napisów końcowych oraz „LATA PÓŹNIEJ".**

### E. Prawo i licencje

- **Realne marki i instytucje** w fikcyjnych rolach: TVN, TVN24, CNN, WHO, ESA, PSE, Szpital Bielański, UW, Gazoport Świnoujście. Ryzyko wizerunkowe i prawne. Rekomendacja: marki medialne zastąpić fikcyjnymi od razu; pozostałe po konsultacji prawnej.
- **Muzyka:** trzy tematy, jingle, smyczki w „Zero Day"; brak kompozytora i licencji.
- **Narzędzia AI:** warunki użycia komercyjnego Flow/Veo/Omni, Klinga i CapCuta — do sprawdzenia przed publikacją; ewentualnie zasady platformy i przepisy o oznaczaniu treści generowanych przez AI (sprawdzić aktualne wymogi UE i platformy publikacji).
- **Głos:** lektor / aktorzy głosowi / licencjonowany TTS — prawa do głosu.
- **Rekwizyty tekstowe:** marker `rs1799945` jest markerem genu HFE, nie selekcji chromosomu Y (E01) — rozważyć zmianę dla wiarygodności.

## 5. Decyzje do podjęcia

Zgodnie z Twoimi zasadami — pojedynczo, w treści. Poniżej lista z rekomendacją; **blokery generowania** to D1–D3 i D12.

| ID | Decyzja | Rekomendacja | Blokuje |
|---|---|---|---|
| **D1** | **Metraż i format** (3 × ~65 min, ok. 207 min i ~1 770 beatów; czy skrócić) | Nie zatwierdzać dziś. Zdecydować po pilocie (F3), gdy znamy koszt i tempo. Do tego czasu pracować nad E01 i nie rozbudowywać E02/E03. | wszystko po F3 |
| **D2** | **Narzędzia** | Flow (Veo 3.1 + Omni Flash) jako baza, Kling jako backup do dialogów (test), modele open source (Wan 2.2, LTX-2, MiniMax H3) tylko jako gałąź testowa — główny powód to spójność postaci (Entity), nie sprzęt | F2 |
| **D3** | **Strategia dialogów:** (a) EN w klipie + polski lektor, (b) polski bezpośrednio, (c) wizualnie bez ruchu ust + głos w post | Test na 2 klipach (Veo, Kling, ew. LTX-2) i decyzja po wyniku; do tego czasu (a)/(c) | F3 |
| **D4** | **Wolska** — Katarzyna ~58, wicepremier | Zatwierdzić; poprawić E03 l. 13, 915, tytuł, beat T-1, „Pani Premier", „Ania" | F1 |
| **D5** | **Zofia** — żywa/ranna (stan w scenariuszu), nazwisko, „wuj" | Zatwierdzić „żywa i ranna", zmienić nazwisko, ustalić męża | F1 |
| **D6** | **8:40 = czas oczekiwania na odpowiedź**, napis 78,3 mln km zostaje | Zatwierdzić; odrzucić poprawkę A4; poprawić l. 895 | F1 |
| **D7** | **Data publikacji Dąbrowskiego** ~12 lat | Zatwierdzić; poprawić E02 l. 400 i E01 l. 886 | F1 |
| **D8** | **Odporność / „ocalały chłopiec"** → wiąże się z listem w teczce, pojemnikiem Very i „dwiema sekwencjami" | Jeśli wątek rozwijamy, te trzy elementy to jego setup i payoff; jeśli nie, wyciąć wszystkie trzy. Najpierw wybrać kierunek | F1 |
| **D9** | **Cliffhanger E01 i śmierć Dąbrowskiego** | Dopisać beat (mały koszt, duży efekt) albo poprawić notę; zacząć od wprowadzenia Piotra w sc. 6 | F1 |
| **D10** | **Reveal Agi:** usunąć „Mamma!" w P2 i przerobić E02 sc. 3 na rozpoznanie matki | Zatwierdzić | F1 |
| **D11** | **Język Very:** norweski w scenach Oslo/przeszłości (z napisami) czy polski z akcentem | Rozstrzygnąć razem z D3 | F2 |
| **D12** | **Wersja wykonawcza Sceny 1:** Clip00–11 + instrukcje agenta; archiwizacja v4 i FULL; okulary dinozaura; światło murka; tytuł w CapCut; dopisać kwestie Marty | Zatwierdzić | F3 |
| **D13** | **Szczepionka zamiast „antidotum"**; pokazać test na ochotniku przed lądowaniem lub zmienić napis | Zatwierdzić | F1 |
| **D14** | **Muzyka:** poza Flow, w CapCut; kompozytor / biblioteka z licencją komercyjną / generator z licencją | Wybrać źródło w F2 | F5 |
| **D15** | **Realne marki → fikcyjne** | Zatwierdzić dla TVN/TVN24/CNN/WHO; reszta po konsultacji | F1 |
| **D16** | **Kanał i model wydania** (np. platforma wideo, odcinki co tydzień czy całość) | Ustalić przy G1 | F7 |

## 6. Skala pracy

- Szacunek czasu: E01 ≈ 60,5 min, E02 ≈ 72–73,5 min, E03 ≈ 73,5–74,5 min → **≈ 207 min**.
- Przy standardzie 7 s na beat: **≈ 1 770 beatów**. E01 ma 257 (≈ 30 min), do pełnych 60,5 min brakuje ok. 260.
- Przy 2 próbach na klip: **≈ 3 500 generacji**. To szacunek, nie dane: nie znamy limitu kredytów na koncie Google AI Pro, tempa ani odsetka odrzutów. **Pilot (F3) ma to zmierzyć.**
- Metoda B (Save frame → Start Image) wymusza generowanie **szeregowe w obrębie sceny**; różne sceny można robić równolegle.

## 7. Plan wdrożenia

Zasady współpracy (z handoffu): zwięźle i po polsku; pytania pojedynczo, w treści; **backup przed każdą zmianą scenariusza**; po zmianie pokazać plik; korekta językowa nie zmienia dialogów (propozycje zmian — do akceptacji); przed każdym ujęciem podać metodę A lub B; pliki produkcyjne clip po clipie; czytanki w PDF, po każdej zmianie regenerować.

### F0 — Porządek (1–2 dni)
1. Zaimportować do repozytorium czysty zestaw: scenariusze `_rev`, czytanki, produkcja E01, produkcja_flow, handoff 11.10. Pominąć `ZERO_DO_PRZENIESIENIA`, ZIP-y, `_archiwum`, Planify i pliki Energomatu.
2. Proponowana struktura: `scenariusze/`, `czytanki/`, `produkcja/E01/`, `flow/`, `decyzje/DECYZJE.md`, `docs/przeglad-2026-11-27/`, `archiwum/`.
3. Utworzyć dziennik decyzji z datami (`ZERO_decyzje_rewizja.md` ma log bez dat) i wpisać D1–D16.
4. Zaktualizować handoff: usunąć A4, poprawić §9 i liczbę scen.

**Wyjście:** repo z jednym źródłem prawdy. Zrobione, gdy nie ma duplikatów ani plików obcych.

### F1 — Zamrożenie kanonu (ok. 1 tydzień)
Po decyzjach D4–D10, D13, D15. Dla każdego odcinka: backup → poprawki → regeneracja czytanki.
- **E01:** chronologia (W1, sc. 8, sc. 9, sc. 10 vs SMS), A5, A6, cliffhanger, beat Dąbrowskiego, dinozaur w okularach, język Very, reveal Agi, zamiana realnych marek, skrócenie kwestii >25 słów, rs1799945.
- **E02:** przenumerować (PROLOG, 1, 1A, 2, 3, 3B…), poprawić tabelę czasów i nagłówki, miejsce PSE, stan mapy w 6A/6B/6C, usunąć sylwetki i zdjęcia mężczyzn z kadru, Wolska, rodzaj „MINISTRA", A1, A3, Zofia.
- **E03:** Wolska, szczepionka, pojemnik/list (wg D8), test na ochotniku, „komandor", „trzech tygodni", liczby dni, obsada, „LATA PÓŹNIEJ", usunięcie uwagi produkcyjnej w didaskaliach (l. 477), metraż.
- **Czytanki:** naprawić generator (p. 4D), zregenerować 3 PDF.

**Wyjście / bramka:** „kanon 1.0" — D4–D10, D13, D15 zamknięte, zero otwartych twardych nieścisłości A/B z audytu.

### F2 — Przedprodukcja (ok. 1 tydzień, równolegle z F1)
1. **Biblia postaci i wyglądu:** referencje i Entity dla postaci wymaganych w E01 (potem E02/E03); Vera w 5 wiekach; stała reguła opisu postaci w promptach (jedna wersja).
2. **Zasady Flow:** jedna instrukcja agenta (lewo/prawo, jeden dinozaur, ciemne włosy, kurtka, tło statyczne, brak muzyki, brak tekstu w kadrze); mapowanie Clip00–11.
3. **Testy narzędzi** (D2, D3): 2 klipy dialogowe w Veo, Omni i Kling; ew. 1 klip na Wan 2.2 / LTX-2 w chmurze GPU.
4. **Budżet ZERO:** subskrypcje AI, kredyty, lektor, muzyka, narzędzia montażowe, prawo — nowy plik, nie plik Energomatu.
5. **Prawa:** warunki komercyjne narzędzi, źródło muzyki (D14), źródło głosu, lista marek do zamiany, zasady oznaczania AI.
6. **Dopisać beaty:** sc. 13, sc. 15 (bez martwych ciał — np. lina, kubki, mostek), poprawki P1 b6, P3 b11 i b26–27, WT-7, Zero Day (bez muzyki).

**Bramka:** decyzje D2, D3, D11 i D14 podjęte na podstawie testów.

### F3 — Pilot: Scena 1 + czołówka (ok. 1 tydzień) — bramka G1
1. Wygenerować Clip00–11 metodą B; po każdym klipie checklista QC.
2. Zmontować w CapCut: polski głos (wg D3), napisy, tytuł, muzyka jako osobna warstwa.
3. **Zmierzyć:** kredyty na beat, czas na beat, odsetek odrzuconych prób, odsetek klipów z poprawną spójnością twarzy/ubioru/lewo-prawo.
4. Pokazać 2–3 osobom i zebrać reakcje.

**Bramka G1 (go/no-go):** na podstawie pomiarów ustalamy D1 (metraż i format), D16 i kalendarz. Jeżeli jakość spójności postaci jest zła, wracamy do D2 (Kling / inne narzędzie) albo zmieniamy formę (np. mniej dialogów, więcej ujęć wizualnych).

**Checklista QC klipu:** Michał LEWO, Karolina PRAWO; jeden dinozaur z przodu; Karolina w zielonej kurtce bez swetra, bez biżuterii; twarze stałe; tło statyczne (rusza się tylko tramwaj, przechodnie, gołębie); brak muzyki; jeden mówiący naraz; brak tekstu w kadrze; kwestia zgodna ze scenariuszem; długość ≤ limit modelu.

### F4 — Produkcja wideo E01 (czas do ustalenia po G1)
- Kolejność: dokończyć beaty do docelowego metrażu, potem generować scena po scenie (sceny równolegle, szeregowo wewnątrz sceny), przed każdym klipem podać metodę A/B.
- Priorytet: sceny z beatami OK (2–7, 9–12, bloki P1–P4, wstawki) → sc. 13, 14 (Zero Day), 15 → sc. 8 i 10 po poprawkach.
- Śledzić postęp w tabeli: scena → beaty → wygenerowane → zaakceptowane.

### F5 — Post-produkcja E01
Głos (D3), napisy PL, muzyka i dźwięk (D14), korekcja barwna, napisy tytułowe i końcowe, kontrola całości, przegląd z 2–3 widzami. Wersja E01 v1.0.

### F6 — E02 i E03
Powtórzyć F2–F5: biblia postaci, beaty (E02: zasada bez mężczyzn w kadrze, ekrany/mapy/napisy w post), generowanie, post. E03: cold open Mars, równoległe plany Ziemia/Mars, napisy końcowe.

### F7 — Wydanie
Zależne od D16: opis, miniatury, trailer, harmonogram premier, oznaczenie treści AI, dokumentacja praw, analityka po premierze. Ewentualnie pokaz zamknięty przed publicznym.

**Orientacyjne terminy:** F0–F3 to ok. 3–4 tygodnie. Terminów F4–F7 nie podaję, bo wynikają z pomiarów w F3 (patrz p. 6).

## 8. Ryzyka

| Ryzyko | Skutek | Reakcja |
|---|---|---|
| Spójność postaci w ~1 770 beatach | Serial „skacze" wizualnie | Entity w Flow, metoda B, QC na każdym klipie, pilot w F3 |
| Skala (≈ 207 min) | Projekt nie dojdzie do końca | Decyzja o metrażu po pilocie, E01 jako pilot, możliwe skrócenie |
| Lip-sync i język dialogów | Polski głos nie pasuje do ust | Testy D3, ewentualnie (c) lub Kling |
| Limity kredytów / przeciążenie Flow | Opóźnienia i koszty | Generowanie rano (PL), pomiar w F3 |
| Filtry platformy (sc. 15, śmierć masowa) | Zablokowane klipy | Zmiana ujęć (bez ciał) |
| Realne marki i licencje | Roszczenia, zdjęcie z platformy | D14, D15, przegląd prawny |
| Duplikaty i niespójne pliki | Błędy w pracy | F0 |
| Kanon poprawiany w trakcie generowania | Przeróbki klipów | Zamrożenie kanonu (F1) przed F4 |

## 9. Open source i MiniMax (odpowiedź na pytanie o sprzęt)

- **MiniMax H3** (33 mld parametrów, wideo do 15 s, 2K, natywny dźwięk): wagi w BF16 ~134 GiB — to sprzęt serwerowy (kilka kart po 80 GB), nie domowy PC. Doniesienia o samym wydaniu wag i warunkach licencji są sprzeczne; przed użyciem sprawdzić repo `MiniMaxAI/MiniMax-H3`.
- **Wan 2.2 14B:** 24 GB VRAM wygodnie (FP8/GGUF), 16 GB z offloadingiem, 12 GB tylko przy obniżonej rozdzielczości.
- **LTX-2 (Apache 2.0, wideo + audio):** 8 GB VRAM z offloadingiem i 64 GB+ RAM tylko w niskiej rozdzielczości; 720p wymaga 16–24 GB; 1080p 24 GB+.
- **Wniosek:** największym ryzykiem jest spójność postaci (u nas Entity), nie sprzęt. Test jednego klipu w chmurze GPU w F2 rozstrzygnie. Nie planuję kupowania sprzętu przed wynikiem testu.

## 10. Najbliższe kroki

1. Potwierdzić, że Planify i pliki Energomatu mają zostać poza repozytorium.
2. Zaimportować czysty zestaw plików do repo (F0).
3. Zdecydować D4–D10 i D13 (kanon) — po kolei, jedno pytanie na raz.
4. Zdecydować D12 (wersja wykonawcza Sceny 1).
5. Naprawić generator czytanek i zregenerować 3 PDF.
6. Przenumerować E02 i poprawić chronologię E01.
7. Przygotować test dialogów (D3) na 2 klipach.
8. Założyć budżet ZERO i listę praw/licencji.
9. Dopisać beaty sc. 13 i 15.
10. Wykonać pilot Sceny 1 i zmierzyć tempo oraz koszt (G1).

## 11. Załączniki

Szczegółowe notatki agentów w `docs/przeglad-2026-11-27/`:
`E01_scenariusz.md`, `E02_scenariusz.md`, `E03_scenariusz_i_PDF.md`, `E01_beaty_i_rozpiska.md`, `scena1_flow.md`, `decyzje_i_konsultacje.md`, `produkcja_i_budzet.md`.

> Uwaga do `produkcja_i_budzet.md`: w trakcie przeglądu `unrar` nadpisał jeden plik Budżet… drugim, więc kwoty tam podane pochodzą z jednego z dwóch (oba to Energomat). Nie dotyczą ZERO.
