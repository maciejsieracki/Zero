# ZERO-RESEARCH-001 — wezel e: MiniMax (Hailuo / H3) przez API

Data odczytu: 2026-11-27. Runda 2 z 3. Operator, wezel e. Poprawki po zarzutach E-e-1-1 i E-e-1-2.

## Dostepnosc przez API

MiniMax jest dostepny przez API: MiniMax API Platform (`platform.minimax.io`), rozliczenie pay-as-you-go z salda konta (ceny w USD).
- Modele H3 (MiniMax-H3 i warianty) sa wylacznie w pay-as-you-go: strona cennika podaje, ze H3 "nie jest jeszcze obslugiwany" przez pakiety wideo (Video Packages).
- Modele Hailuo 2.3 / 02 sa w pay-as-you-go (cena za klip) i dodatkowo w pakietach "video points". Pakietow nie uzywam jako podstawy kosztu.
- Lokalny / open source H3 odpada (ECHO-007). Tego nie badano.

## UWAGA O METODZIE (ograniczenie infrastruktury)

Domena `platform.minimax.io` (a takze `minimax.io`, `web.archive.org`) **jest zablokowana w sieci tej sesji** (WebFetch: ENOTFOUND, curl: CONNECT 403). Nie moglem bezposrednio otworzyc oficjalnych stron. Wszystkie liczby ponizej pochodza z wyszukiwarki (WebSearch) ograniczonej do domeny `platform.minimax.io`. Kazda liczba jest przypisana do URL-a rzedu 1, ale odczytalem ja ze streszczenia indeksu wyszukiwarki, nie z samej strony. Dlatego pewnosc to co najwyzej **srednia**, takze tam, gdzie liczba powtarzala sie w kilku niezaleznych wyszukiwaniach. Wyszukiwarka podawala wiek stron w indeksie: ok. 113-179 dni. Ceny mogly sie zmienic. Do potwierdzenia przez Evaluatora z dostepem do domeny.

## Tabela modeli (posortowana rosnaco po koszcie 1 min)

| Model | Tryb | Maks. dlugosc 1 klipu | Maks. rozdzielczosc | 1080p? | Natywny dzwiek | Cena (zrodlo) | Cena/s | Rozdzielczosc ceny | Koszt 1 min | cost_is_1080p | Pewnosc |
|---|---|---|---|---|---|---|---|---|---|---|---|
| MiniMax-H3-Lite (najtanszy, ex aequo z H3-Max-Turbo) | T2V/I2V (v2) | 15 s (4-15) | 768P (opcje 480P/768P, bez 2K) | NIE | NIEPOTWIERDZONE dla Lite | 0,04 USD/s przy 768P | 0,040 | 768P | 2,40 USD | false | srednia |
| MiniMax-Hailuo-2.3-Fast | tylko I2V | 10 s (768P); 6 s przy 1080P | 1080P | TAK (tylko 6 s) | BRAK DANYCH (NIEPOTWIERDZONE) | 0,33 USD za klip 1080P 6 s | 0,055 | 1080P | 3,30 USD | true | srednia |
| MiniMax-Hailuo-2.3 | T2V + I2V | 10 s (768P); 6 s przy 1080P | 1080P | TAK (tylko 6 s) | BRAK DANYCH (NIEPOTWIERDZONE) | 0,49 USD za klip 1080P 6 s | 0,081667 | 1080P | 4,90 USD | true | srednia |
| MiniMax-H3 (najlepszy) | T2V/I2V/referencje (v2) | 15 s (4-15, liczby calkowite) | 2K (opcje: 480P / 768P / 2K) | NIE (brak opcji 1080P; 2K jest wyzsze) | TAK (`generate_audio`, domyslnie true) | 0,13 USD/s przy 2K | 0,13 | 2K | 7,80 USD | false | srednia |

Wymaganie ZERO to klipy ok. 7-10 s. Hailuo 2.3 / 2.3-Fast w 1080P daja tylko 6 s; 10 s jest tylko przy 768P. H3 daje 7-10 s w 768P albo w 2K.

## Rachunek kosztu krok po kroku

1. **MiniMax-H3-Lite, 768P:** 0,04 USD/s x 60 s = **2,40 USD/min**. To nie jest 1080p.
2. **MiniMax-Hailuo-2.3-Fast, 1080P:** 0,33 USD / 6 s = 0,055 USD/s; 0,055 x 60 = **3,30 USD/min**. Inaczej: 60 s / 6 s = 10 klipow x 0,33 = 3,30.
3. **MiniMax-Hailuo-2.3, 1080P:** 0,49 USD / 6 s = 0,0816667 USD/s; x 60 = **4,90 USD/min**. Inaczej: 10 klipow x 0,49 = 4,90.
4. **MiniMax-H3, 2K:** 0,13 USD/s x 60 = **7,80 USD/min**. To nie jest 1080p, tylko wyzsza rozdzielczosc. Dla porownania H3 przy 768P: 0,08 x 60 = 4,80 USD/min.

Pomocniczo (poza tabela):
- **MiniMax-H3-Max-Turbo przy 768P (T2V/I2V):** 0,04 USD/s x 60 s = **2,40 USD/min**. To ten sam koszt co H3-Lite (remis). Przy 480P: 0,025 x 60 = 1,50 USD/min. W trybie reference 768P: 0,08 x 60 = 4,80 USD/min, plus 0,12 USD/s za wejsciowe wideo.
- H3-Lite przy 480P: 0,025 x 60 = 1,50 USD/min.
- Hailuo-2.3 przy 768P 10 s: 0,56 / 10 = 0,056 USD/s, czyli 3,36 USD/min.
- Hailuo-2.3-Fast przy 768P 10 s: 0,32 / 10 = 0,032 USD/s, czyli 1,92 USD/min.
- H3-Highspeed przy 768P: 0,06 x 60 = 3,60 USD/min.

## Uwagi do modeli

- **MiniMax-H3:**
  - Strona API reference `video-generation-v2-create` podaje rozdzielczosci 480P / 768P / 2K. 480P obsluguje partner RunningHub, a wyszukiwarka podala dla niego 0,038 USD/s. Starsze strony przewodnika wymieniaja tylko 768P / 2K.
  - Dlugosc klipu: 4-15 s, 24 fps. Endpoint `/v2/video_generation`.
  - `generate_audio` to parametr boolean, domyslnie true; false daje wideo bez dzwieku. W cenniku nie znalazlem osobnej ceny za audio ani rozdzielenia cen z dzwiekiem i bez. Wniosek, ze ta sama cena obejmuje oba warianty, jest NIEPOTWIERDZONY.
  - Wymiary 2K w pikselach dla wideo nie sa podane. Dla H3-Image 2K 16:9 to 2720x1536 (to dane dla obrazu, nie dla wideo).
  - Audio wejsciowe jest bezplatne. Pierwsze 5 obrazow w zadaniu jest bezplatnych, kolejne po 0,04 USD.
  - Blog MiniMax: natywny dzwiek stereo, do 2K i 15 s; dialogi w 11 jezykach bez polskiego (temat RESEARCH-002).
- **MiniMax-H3-Lite:**
  - Cena 0,04 USD/s (768P) i 0,025 USD/s (480P) za sekunde wyjscia: `docs/pricing/overview`. W rundzie 2 potwierdzilo ja kolejne wyszukiwanie.
  - Dlugosc 4-15 s (liczby calkowite) i rozdzielczosc 480P/768P bez 2K podaja dwie strony rzedu 1: `api-reference/video-generation-v2-create` oraz `api-reference/api-overview` (odczyt z wyszukiwarki, 2026-11-27). Status: POTWIERDZONE zrodlem rzedu 1. Pewnosc: **srednia**, bo nie moglem otworzyc samej strony (zob. "Uwaga o metodzie").
  - Starsze przewodniki (`guides/video-generation`, `faq/models`) nie wymieniaja Lite.
  - Audio w Lite: NIEPOTWIERDZONE (nie znalazlem tego w dokumentacji).
- **MiniMax-H3-Max:** 0,08 USD/s (768P) i 0,05 USD/s (480P), 5-15 s, bez 2K. Wyszukiwarka wiaze go z dostawca fal.
- **MiniMax-H3-Max-Turbo** (zrodlo rzedu 1: `https://platform.minimax.io/docs/pricing/overview`, sekcja "H3 series extended models"; odczyt z wyszukiwarki 2026-11-27, wiek strony w indeksie ok. 179 dni):
  - Cennik podaje go jako "Provider: fal". To szybsza i tansza wersja H3-Max. Jest to post-trening fal, udostepniany przez API MiniMax.
  - Ceny za sekunde: 0,04 USD przy 768P (T2V/I2V) i 0,025 USD przy 480P (T2V/I2V). Tryb reference: 0,08 USD przy 768P (wejsciowe wideo 0,12 USD/s) i 0,05 USD przy 480P (wejsciowe wideo 0,04 USD/s). Obrazy wejsciowe ponad dwa: po 0,06 USD.
  - Limity: 5-15 s, tylko 480P/768P (bez 2K i bez 1080P). Tryby: T2V, I2V (klatka pierwsza/ostatnia), referencje.
  - Natywne audio: NIEPOTWIERDZONE.
  - Pewnosc: srednia. Na nowszej stronie `guides/pricing-video` (ok. 113 dni w indeksie) Turbo nie wystepuje, wiec mogl zostac wycofany albo przeniesiony. NIEPOTWIERDZONE, czy nadal jest dostepny.
- **Najtanszy wariant: REMIS.** H3-Lite i H3-Max-Turbo kosztuja tyle samo, 0,04 USD/s przy 768P, czyli 2,40 USD/min. W tabeli jest Lite. Kryterium wyboru: przy rownej cenie pierwszenstwo ma model wlasny MiniMax (Lite) przed modelem partnera (Turbo, fal). Lite jest tez potwierdzony na dwoch stronach API reference, a Turbo tylko w jednej tabeli cennika (strona starsza). Oba sa ponizej 1080p. Na pole cost_usd_per_minute (2,40) wybor nie wplywa.
- **MiniMax-H3-Highspeed:** 0,06 USD/s (768P), bez 2K. Ani Max, ani Max-Turbo, ani Highspeed nie wchodzi do tabeli (limit 4 wariantow). Max-Turbo jest najtanszy ex aequo, ale jest opisany wyzej.
- **Hailuo-2.3 / Hailuo-02:**
  - Wedlug referencji T2V i noty wydania z 2025-10-28: 768P (6 s, 10 s) i 1080P (tylko 6 s).
  - Hailuo-02 ma te same ceny co 2.3 (0,28 / 0,56 / 0,49), dlatego go nie powielam.
  - Cennik oznacza te modele jako starsze (legacy).
  - Nie znalazlem w dokumentacji potwierdzenia, czy generuja dzwiek. Pole native_audio zostawiam puste (BRAK DANYCH).
- **Hailuo-2.3-Fast:** tylko obraz -> wideo (I2V). Wymaga klatki startowej.

## Zrodla

Rzad 1 (oficjalne), data odczytu 2026-11-27. Odczyt posredni przez wyszukiwarke; bezposredni dostep zablokowany.
- https://platform.minimax.io/docs/guides/pricing-paygo — ceny pay-as-you-go H3, Hailuo-2.3, 2.3-Fast, 02.
- https://platform.minimax.io/docs/guides/pricing-video — H3 0,08 / 0,13 USD/s; H3-Max; H3 nieobslugiwany w pakietach.
- https://platform.minimax.io/docs/pricing/overview — H3-Highspeed, H3-Lite (0,04/0,025 USD/s), H3-Max-Turbo (sekcja extended models, Provider: fal; 0,04/0,025 USD/s, 5-15 s, 480P/768P).
- https://platform.minimax.io/docs/api-reference/api-overview — H3-Lite: 480P/768P, 4-15 s, bez 2K.
- https://platform.minimax.io/docs/api-reference/video-generation-v2-create — H3: 480P/768P/2K, 4-15 s, `generate_audio`; H3-Lite: 480P/768P, 4-15 s.
- https://platform.minimax.io/docs/guides/video-generation — przyklad v2 z `generate_audio`, 2K.
- https://platform.minimax.io/docs/api-reference/video-generation-t2v — Hailuo-2.3/02: 1080P tylko 6 s, 768P 6/10 s.
- https://platform.minimax.io/docs/release-notes/models — Hailuo 2.3 (2025-10), 2.3-Fast tylko I2V.
- https://platform.minimax.io/docs/faq/models — lista modeli, H3 768P/2K 4-15 s.
- https://minimax.io/blog/minimax-h3 — natywny dzwiek stereo H3, 2K, 15 s.

Rzad 4-5 (poszlaka, NIEPOTWIERDZONE, nie uzyte w liczbach):
- https://www.atlascloud.ai/pl/blog/guides/hailuo-ai-pricing-cost — agregator; ceny posrednika, nie MiniMax.

## Niepewnosc / czego nie potwierdzono

1. Brak bezposredniego odczytu oficjalnych stron (blokada sieci). Liczby wymagaja potwierdzenia przez Evaluatora.
2. Daty cennika nie ma na stronach (wyszukiwarka nie zwrocila daty). Jako date podaje date odczytu 2026-11-27.
3. Zaden model H3 nie ma opcji 1080P. Do Full HD trzeba albo uzyc 2K (drozej), albo Hailuo 2.3 w 1080P (maks. 6 s).
4. Cena i limity H3-Lite sa potwierdzone zrodlami rzedu 1 (odczyt z wyszukiwarki). Audio w Lite, H3-Max-Turbo i Hailuo 2.x: niepotwierdzone. Nie potwierdzilem, czy H3-Max-Turbo jest nadal dostepny (brak go w nowszym cenniku `guides/pricing-video`).
5. Brak rozdzielenia ceny z dzwiekiem i bez w H3.
