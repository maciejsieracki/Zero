# ZERO — E01 Scena 1: przegląd promptów Flow (tylko odczyt)

Data przeglądu: 2026-11-27
Źródło: `/tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/zero-unrar/Zero` (dalej R)
Zakres: pliki wskazane w zadaniu + pliki, do których odsyłają (ZERO_instrukcje_dla_agenta_Flow.md, ZERO_Scena1_beaty_7s_ENG.md, ZERO_E01_S1_Clip00–11.md, ZERO_INSTRUKCJA_Flow_scena1_ciaglosc.md, ZERO_VEO3_TEST_Scena1_Epilog_ENG.md, ZERO_VEO3_INTRO_czolowka_ENG.md, ZERO_czolowka.md, scenariusz ZERO_mini_serial_E01_ADAM_rev.md sc. 1).
Nic w R nie zmodyfikowano. Nie uruchamiano skryptów z archiwum.

Uwaga o datach: znaczniki czasu (mtime) pochodzą z rozpakowania. FULL i FULL_edited mają identyczny znacznik (2026-06-09 18:18:18), więc nie rozstrzygają, która wersja jest nowsza.

---

## 1. Mapa wersji

| Plik (względem R) | mtime | Struktura | Czas klipu | Status / uwagi |
|---|---|---|---|---|
| `ZERO_VEO3_E01_Scena1_ENG_v4.md` | 2026-06-07 | 7 klipów (0–6), pełne prompty EN, bridge przez zrzut klatki (Image to video) | max 9 s | Handoff §9 nazywa go AKTYWNYM. Nie ma poprawki Karoliny ani tła. Zawiera 4 błędy (sekcja 4). |
| `_archiwum/ZERO_VEO3_E01_Scena1_ENG_v3.md` | 2026-06-06 | Ta sama lista 7 klipów (nagłówki linii 24–340), nagłówek identyczny, „max 9 seconds" | 9 s | Historia. Przed v4. |
| `ZERO_produkcja_flow/ZERO_VEO3_E01_Scena1_FULL_ENG.md` | 2026-06-09 | 7 klipów (0–6), bardzo szczegółowe bloki (15 sekcji), nagłówek „Veo 3" | 10 s („do not exceed 10 s") | Brak 6 kwestii z sc. 1 (patrz sekcja 5). Tytuł ZERO generowany w Veo. |
| `ZERO_produkcja_flow/ZERO_VEO3_E01_Scena1_FULL_ENG_edited.md` | 2026-06-09 | = FULL + poprawka Karoliny i tła (diff 104 linie) | 10 s | Jedyna wersja z poprawką. Dialogi i czasy bez zmian. |
| `ZERO_produkcja_flow/ZERO_VEO3_TEST_Scena1_Epilog_ENG.md` | 2026-06-09 | Format testowy „sekunda po sekundzie": 7 klipów sc. 1 (CLIP 0–6) + EPILOG (E1–E4) | 8 s („Klip ≤ 8 s (Veo)", linia 4) | Trzecia odrębna wersja sc. 1. Sc. 1: „Answer it" Michała zamienione na gest (linia 181). Epilog poza zakresem. |
| `ZERO_produkcja_flow/ZERO_Scena1_beaty_7s_ENG.md` | 2026-06-09 | 12 beatów (BEAT 0–11), jeden mówiący na beat | ~7 s | BEAT 0 oznaczony „GOTOWE" (linia 11). Najpełniejsze kwestie sc. 1. |
| `ZERO_produkcja_flow/ZERO_E01_S1_Clip00.md` … `Clip11.md` | 2026-06-09 | 12 plików, 1:1 z BEAT 0–11, action-only (reguły w pliku reguł) | ~7 s (Clip00 „~10 s") | Brak statusów. Odsyłają do „Instrukcje dla agenta". |
| `ZERO_produkcja_flow/ZERO_INSTRUKCJA_Flow_scena1_ciaglosc.md` | 2026-06-09 | Procedura krok po kroku: wklej CAŁY blok CLIP z FULL przy każdym ujęciu | 10 s, model „Veo" (linia 22) | Odsyła do FULL (7 klipów), nie do Clip00–11. |
| `ZERO_produkcja_flow/ZERO_instrukcje_dla_agenta_Flow.md` | 2026-06-09 | Stałe reguły do panelu „Instrukcje dla agenta" w Flow | — | Zawiera już poprawkę Karoliny (linie 25–26) i tła (linie 36–38). |

### Odpowiedź na (a): która wersja jest aktualna

Nie ma jednej aktualnej wersji. Dokumenty sobie przeczą:
- Handoff (11.10.2026, nadrzędny) mówi, że aktywne są prompty v4 (§9: „aktywne prompty Sceny 1 (7 klipów EN)").
- Ten sam handoff w §7 (linia 275) planuje generowanie „klipy 0→11 metodą B" (czyli Clip00–11).
- Pliki z 9.06 (beaty + Clip00–11) są najnowsze i najpełniejsze pod względem dialogów (sekcja 5).
- Poprawka Karoliny i tła istnieje tylko w FULL_edited i w pliku reguł.

Wniosek: najbardziej prawdopodobna wersja wykonawcza to Clip00–11 + ZERO_instrukcje_dla_agenta_Flow.md. v4 wygląda na przestarzałą (7 czerwca) i ma błędy. FULL_edited to najlepszy opis referencyjny, ale brakuje w nim kwestii. Ostateczną decyzję powinien podjąć Maciej, bo handoff wskazuje v4.

---

## 2. Handoff vs pliki (b): 7 czy 12 klipów

- Handoff §9 (linia 310) mówi o 7 klipach — to v4. Handoff §7 (linia 275) mówi o klipach 0→11 — to Clip00–11. Handoff jest więc sprzeczny sam ze sobą.
- Clip00–11 to NIE jest ten sam podział co Clip 0–6. Clip00–11 = BEAT 0–11 (12 ujęć po ~7 s, jeden mówiący na ujęcie). Clip 0–6 (v4/FULL/TEST) = 7 ujęć po 8–10 s, często z dwoma mówiącymi (np. v4 klip 2: K i M). Nie ma mapowania klip→klip.
- Nazewnictwo się myli: „CLIP 0–6" (FULL, v4) i „Clip00–11" (pliki) to dwa różne projekty tych samych ujęć, a nie jeden projekt w dwóch formatach.

---

## 3. Co zmienia FULL_edited (c)

Diff FULL → FULL_edited (`diff -u`, 6 bloków):
1. Sekcja 4 (wygląd), klipy 0, 1, 2, 3, 4, 5, 6 — dopisano: Karolina ma TYLKO zieloną kurtkę nad jasnym/kremowym topem; NIE nosi żółtego swetra i nie ma dinozaura; żółty sweter z JEDNYM dinozaurem tylko Michał.
2. Sekcja 5 (tło), klipy 0–6 — dopisano: tło pixel-stable, bez dryfu i bez nowych budynków od pierwszej do ostatniej sekundy.
3. Negatywy — dopisano 2 punkty w klipach 1–6: Karolina w żółtym swetrze / dinozaur; zmiana tła.

Nie zmieniono: dialogów, czasów klipów, kolejności, pozycji L/P, długości (nadal 10 s), tytułu ZERO. Edited NIE usuwa: „distant cafe music" (FULL linia 199), ZERO generowanego w Veo (linie 188–190), braków kwestii (sekcja 5).

Poprawka dotyczy tylko FULL. v4 i Clip00–11 jej nie mają. Clip00–11 nie opisują ubrań Karoliny wcale i polegają na panelu reguł (ZERO_instrukcje_dla_agenta_Flow.md, linie 25–26), który działa tylko, jeśli został wklejony do Flow.

---

## 4. Naruszenia reguł w promptach (d)

Reguły źródłowe: handoff §7 (linie 255–259), ZERO_instrukcje_dla_agenta_Flow.md, ZERO_Scena1_beaty_7s_ENG.md (UWAGI, linie 82–84).

| # | Plik | Linia / klip | Problem | Reguła / dowód |
|---|---|---|---|---|
| 1 | v4 | linia 74, klip 0 | Michał „speaks quietly" 6–9 s, a w klipie 0 ma nie być dialogu. Bridge-out klipu 0 też mówi „mid-sentence" (linia 84). | Beat 0 „Bez dialogu"; FULL kl.0 §14 „NO human speech anywhere" |
| 2 | v4 | linia 301, klip 4 | Karolina „CENTER or slightly RIGHT" | Stała pozycja PRAWA (handoff §7; reguły linie 17–18) |
| 3 | v4 | linie 378–379 (klip 5, bridge-out) i 419 (klip 6) | Dinozaur „on back-center of sweater" i „visible" na plecach | „EXACTLY ONE dinosaur, centered on chest". FULL kl.6 §4 (linie 1198–1211) to wprost koryguje: plecy są gładkie. v4 nie został poprawiony. |
| 4 | FULL | linia 199, kl.0 | „distant cafe music barely audible" | „Bez muzyki (tylko ambient ulicy)" (handoff §7, reguły linia 50). Diegetyczna muzyka nadal narusza zasadę. |
| 5 | FULL (linie 188–190, 221), v4 (kl.0, „ZERO"), Clip00 (linia 4), BEAT 0 | Tytuł „ZERO" generowany w Veo | Czołówka i notka INTRO: tytuły w CapCut, nie w Veo. Reguły: „never burn any text into the video" (ZERO_instrukcje linia 45–46). Dodatkowo: ZERO pojawia się w czołówce (50–55 s) i w Scenie 1 (kl.0, ~6–10 s) — podwójny tytuł w minucie. |
| 6 | v4 klipy 1, 2, 3, 5; FULL kl.5 | Więcej niż jeden mówiący w klipie | Reguły Flow (linie 47–48) mówią „jedna osoba naraz", co jest spełnione. Instrukcja (ZERO_INSTRUKCJA linia 11) mówi „w jednym klipie mówi tylko jedna osoba", co jest łamane. Konflikt dokumentów. |
| 7 | FULL (10 s), ZERO_INSTRUKCJA (linie 22, 24: „Model: Veo", „10 s") | Długość vs model | Veo 3.1 bazowo ~8 s (ZERO_instrukcje linia 8; handoff §7 linia 246). Omni Flash do ~9–10 s bez Extend (handoff §7 linia 245). Prompt 10 s jest tylko w Omni i na granicy limitu. Instrukcja (linia 79–84) używa Extend, który działa tylko na Veo — sprzeczność z handoffem. v4 (9 s) też nie mieści się w bazowych 8 s Veo. |
| 8 | v4 (kl.4, linia 317; kl.5, linia 356) vs FULL (kl.4 kończy siedząc, linie 939–941; kl.5 zaczyna stojąco, linia 984) | Ciągłość: wstawanie | Brak przejścia siedzenie → stanie w FULL i w BEAT 8→9 (Clip09 „Both now standing" bez ujęcia wstawania). |
| 9 | INTRO (linia 429) vs FULL (linia 106) | Światło na tym samym murku | Czołówka CLIP_03A: słońce z PRAWEJ, murek 80–90 cm. Scena 1: słońce z LEWEJ, murek „knee-height". Dwa różne światła na jednym miejscu. |
| 10 | Clip00 ~10 s; reszta ~7 s; FULL 10 s; v4 7 s | Czas tytułu ZERO | Clip00: ~6 s; FULL: 9–10 s; v4: 7 s; BEAT 0: 6–7 s. Drobne, ale do ujednolicenia. |
| 11 | Scenariusz (linia 73); INTRO (linia 534); czołówka (linia 70) | Okulary dinozaura | „dinozaur w okularach" w scenariuszu i czołówce; żaden prompt Sceny 1 nie ma okularów. Rozbieżność kanonu. |
| 12 | Karolina, v4 i FULL | Kurtka + „light/pale top" | Nie ma wprost zakazu swetra w v4, a „pale top" bywa czytany jako sweter. Ryzyko niskie; poprawka tylko w edited i w regułach. |

Zgodne z regułami: pozycje L/P w większości klipów; jeden dinozaur na przedzie w FULL i Clip00–11; dialogi EN; brak napisów PL w wideo (poza ZERO); brak naprawdę wielu mówiących naraz (klipy FULL 1–6 i BEAT-y mają jednego mówiącego lub naprzemienność).

---

## 5. Rozbieżności dialogów (e)

Scenariusz: `ZERO_mini_serial_E01_ADAM_rev.md`, SCENA 1, linie 62–124. Kwestie w tabeli wg kolejności scenariusza. Oznaczenia: + = jest, − = brak, ~ = jest częściowo.

| # | Scenariusz (PL), linia | EN w v4 | EN w BEAT/Clip00–11 | EN w FULL/edited | EN w TEST (epilog) | Uwaga |
|---|---|---|---|---|---|---|
| 1 | K „Skąd ty w ogóle masz takie rzeczy." (76) | + „Where do you even get things like this." (linia 148) | + | + (kl.1) | + | Tłumaczenie swobodne, zgodne. |
| 2 | M „Mama kupiła na świętego Mikołaja. Powiedziałem, że ładny." (79) | + „Mom bought it for Saint Nicholas Day. I said it was nice." | + (BEAT 2) | + (kl.2, linie 578–582) | + (E2 cl.2) | Scenariusz: „bez wstydu"; FULL: „bashful". Kosmetyka. |
| 3 | K „Mikołaj przynosi dzieciom do szóstego roku życia." (82) | + | + (BEAT 3) | + (kl.3) | + | FULL dodaje „gifts" (EN) i w napisach „prezenty" (linia 778) — nie ma tego w scenariuszu. |
| 4 | M „A mi przynosi do teraz, bo mama mówi, że jestem grzeczny." (85) | + (linia 206) | + (BEAT 4, Clip04) | **− BRAK** (kl.3 linia 763 i 788: „no lines from Michal") | − | **Krytyczne: brak w FULL/edited.** |
| 5 | „Karolina śmieje się głośno. Michał też." (87) | — | ~ (BEAT 3 „real, gentle laugh") | ~ (linia 716–717: „not loud") | ~ | Scenariusz: głośno; prompty: cicho. Decyzja. |
| 6 | K „Moja mama." (93) | + | + (BEAT 5, Clip05) | + (kl.4, linia 937) | + | — |
| 7 | M „Odbierz, odbierz." (96) | + (linia 263) | + (BEAT 6, Clip06) | **− BRAK** (kl.4: tylko gest) | − (gest, cisza, linia 181) | Krytyczne w FULL. |
| 8 | K „Mamo — tak, już wychodziłam, wiem, że —" (99) | + (linia 270) | + (BEAT 7, Clip07) | **− BRAK** | − | Krytyczne w FULL. |
| 9 | MARTA „Karolina, czy wzięłaś klucze od piwnicy, bo —" (102) | + (linia 307, jako „MOTHER'S VOICE") | − (BEAT 8: tylko „faint mother's voice", bez tekstu) | − | − | Kwestia Marty tylko w v4. Decyzja: słyszalna czy tylko szum. |
| 10 | K „Mamo, mam zajęcia za osiem minut." (105) | + (linia 310) | + (BEAT 8, Clip08) | **− BRAK** | − | Krytyczne w FULL. |
| 11 | MARTA „Tak, tak, dobrze, to do wieczora." (108) | + (linia 312) | − (tylko „faint") | − | − | Jak #9. |
| 12 | M „No to co, kawa po wykładzie?" (114) | + | + (BEAT 9, Clip09) | + (kl.5, linia 1114) | + | — |
| 13 | K „Kawa po wykładzie." (117) | + | + (BEAT 10, Clip10) | + (kl.5, linia 1120) | + | — |

Podsumowanie: FULL/edited nie ma 6 kwestii sc. 1 (#4, #7, #8, #9, #10, #11; #9 i #11 to Marta). TEST nie ma #4 i #8 i zamienia #7 na gest. Beaty/Clip00–11 pokrywają wszystkie kwestie Michała i Karoliny; brakuje im tylko 2 kwestii Marty (sł. „faint"). v4 jest najpełniejsza, ale ma błędy w klipie 0 i w pozycji Karoliny.

Inne rozbieżności:
- Muzyka: scenariusz linia 65 „Muzyka: ciepła, ambientowa, miejska" vs reguła „bez muzyki w klipach Flow" (decyzja: muzyka w CapCut, czyli zgodnie z regułą, ale scenariusz trzeba uzgodnić).
- Murek: scenariusz linia 72 „murek przed budynkiem uczelni" vs prompty „murek na Nowym Świecie". Do uzgodnienia z opisem lokacji.
- Okulary dinozaura: linia 73 scenariusza (patrz tabela naruszeń #11).
- Wstawanie: scenariusz linia 110–111 („Michał wstaje, podaje jej rękę") — v4 ma to przejście, FULL i beaty nie (naruszenie #8).

---

## 6. Status generowania (f)

- Jedyny znacznik statusu w R: `ZERO_Scena1_beaty_7s_ENG.md`, linia 11: „BEAT 0 — establishing (GOTOWE)". Odpowiada Clip00.
- Clip01–11: brak jakichkolwiek znaczników (ani „wygenerowany", ani „zaakceptowany").
- Archiwum nie zawiera żadnych plików wideo ani zrzutów klatek (tylko .md i .pdf), więc status Clip00 nie da się zweryfikować.
- Handoff §10 pkt 5 (11.10.2026) nadal wymienia „generowanie E01 Sceny 1 w Flow (metoda B)" jako następny krok, a §7 wymaga najpierw „utwardzić: Karolina NIE w swetrze + blokada tła". Nie ma dowodu, że poprawka została wdrożona w Flow.
- Wniosek: wg dokumentów zrobiony jest co najwyżej Clip00 (BEAT 0). Pozostałe 11 klipów Clip01–11 (albo 6 z FULL/v4) to stan „do zrobienia". Jeśli Clip00 był generowany, to w wersji z beatów, a nie z v4 kl.0 (który ma mówiącego).

---

## 7. Dodatkowe konflikty w dokumentach (poza zakresem, ale blisko)

- Model: handoff §7 mówi Omni Flash (bez Extend), instrukcja i FULL mówią Veo (z Extend), beaty mówią Extend (+7 s, linia 82). Te trzy nie mogą być prawdziwe jednocześnie.
- Procedura: ZERO_INSTRUKCJA każe wklejać CAŁY blok CLIP z FULL przy każdym klipie. Clip00–11 + reguły w panelu to inny sposób (action-only). Oba jednocześnie dublują reguły i mogą się rozjechać.
- INTRO (nagłówek, linia 23) pisze „Ujęcia murku i pustej ulicy (CLIP_04 i CLIP_08)" — poprawne numery to CLIP_03 i CLIP_07. INTRO (linie 403, 429) generuje murek i ulicę w Veo, a `ZERO_czolowka.md` (linie 179–180) wymaga nakręcenia ich w terenie.
- INTRO twierdzi, że Veo 3 generuje max 8 s (linia 12), co zgadza się z TEST i ZERO_instrukcje, ale nie z FULL (10 s) i v4 (9 s).
- Epilog TEST (E4, linia 365): „NO music (or one very faint warm note)" — sprzeczne z zasadą „bez muzyki", choć poza sc. 1.

---

## 8. Rekomendacje (pełna lista)

1. Ustalić wersję wykonawczą (Clip00–11 + reguły w panelu) i oznaczyć v4 oraz FULL jako historię/referencję. Zaktualizować handoff §9, który nadal wskazuje v4 jako aktywny.
2. Ustalić model: Omni Flash (handoff) czy Veo 3.1 (instrukcja/FULL). Ujednolicić długość klipów do ≤8 s (bezpiecznie dla obu), bo 10 s to granica Omni.
3. Uzupełnić kwestie: w FULL brakuje 4 kwestii Michała/Karoliny (#4, #7, #8, #10). Zdecydować o kwestiach Marty (#9, #11): słyszalne czy szum. Dopiero potem używać FULL jako źródła.
4. Usunąć błędy z v4 (klip 0 mówiący, Karolina centrum, dinozaur na plecach) lub nie używać v4 wcale. Usunąć „distant cafe music" z FULL.
5. Zdecydować o trzech rzeczach kanonu przed generowaniem: (a) okulary dinozaura (scenariusz i czołówka tak, prompty nie); (b) muzyka w scenie (scenariusz tak, reguły nie); (c) tytuł ZERO w Clip00 — Veo czy CapCut (czołówka już pokazuje ZERO na początku odcinka, więc podwójny tytuł). Dodatkowo wyrównać światło murka (czołówka: prawa; Scena 1: lewa) i dopisać ujęcie wstawania (BEAT 8→9).
