# ZERO-RESEARCH-001 — zestawienie generatorow wideo AI (koszt 1 minuty Full HD, API / pay-as-you-go)

Data zestawienia: **2026-11-27**
Zakres: Kling (wezel a), Seedance / BytePlus ModelArk (wezel b), Google Veo i Gemini Omni (wezel c), OpenAI Sora 2 (wezel d), MiniMax przez API (wezel e).
Dane: wylacznie z raportow wezlow (`kling.md`, `seedance.md`, `veo.md`, `sora2.md`, `minimax.md`) po weryfikacji przez Evaluatorow. Kolejnosc ustalona kodem: rosnaco po koszcie 1 minuty przy 1080p; pozycje bez ceny przy 1080p na koncu (sekcja B).

## 1. Tabela

Legenda: koszt 1 minuty = cena za sekunde x 60. Kolumna "x2" = koszt 1 minuty x 2 (dwie proby na kazdy klip), tylko informacyjnie, nie jest liczba docelowa. "nie (NIEPOTWIERDZONE)" przy audio oznacza brak potwierdzenia w zrodle, nie potwierdzony brak.

### A. Cena przy 1080p (posortowane od najtanszego)

| poz. | dostawca i model | maks. dlugosc klipu (s) | maks. rozdzielczosc | 1080p dostepne | audio natywne | cena za sekunde (USD) przy podanej rozdzielczosci | koszt 1 minuty Full HD (USD) | koszt 1 minuty przy 2 probach (x2, informacyjnie) | pewnosc | data cennika |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | MiniMax — MiniMax-Hailuo-2.3-Fast (tylko I2V) | 10 (przy 1080P maks. 6) | 1080P | tak | nie (BRAK DANYCH) | 0.055 @ 1080P | 3.3 | 6.60 | srednia | 2026-11-27 (data odczytu) |
| 2 | Google — Veo 3.1 Lite (veo-3.1-lite-generate-001) | 8 | 1080p | tak | tak | 0.08 @ 1080p | 4.8 | 9.60 | srednia | 2026-11-27 |
| 3 | MiniMax — MiniMax-Hailuo-2.3 (legacy) | 10 (przy 1080P maks. 6) | 1080P | tak | nie (BRAK DANYCH) | 0.081667 @ 1080P | 4.9 | 9.80 | srednia | 2026-11-27 (data odczytu) |
| 4 | Google — Gemini Omni 1.2 Flash | 15 | 4K (upscaling) | tak (upscaling) | tak | 0.104256 @ 1080p (upscaling z bazy 360p/720p) | 6.26 | 12.52 | srednia | 2026-11-27 |
| 5 | Google — Veo 3.1 Fast | 8 | 4K | tak | tak | 0.12 @ 1080p | 7.2 | 14.40 | srednia | 2026-11-27 |
| 6 | Kling — Kling 3.0 Omni (kling-v3-omni, audio natywne) | 15 | 4K | tak | tak | 0.14 @ 1080p | 8.4 | 16.80 | srednia | 2026-11-27 (data odczytu; cennik bez daty) |
| 7 | Kling — Kling 3.0 (audio natywne) | 15 | 4K | tak | tak | 0.168 @ 1080p | 10.08 | 20.16 | srednia | 2026-11-27 (data odczytu; cennik bez daty) |
| 8 | Kling — Kling 4.0 (kling-4.0, najlepszy) | 30 | 4K | tak | tak | 0.2308 @ 1080p | 13.85 | 27.70 | srednia | 2026-11-27 (data odczytu; 4K od 2026-11-19) |
| 9 | Seedance — Dreamina Seedance 2.0 (dreamina-seedance-2-0-260128) | 15 | 4K | tak | tak | 0.37422 @ 1080p | 22.45 | 44.90 | wysoka | 2026-11-26 |
| 10 | Google — Veo 3.1 (veo-3.1-generate-001) | 8 | 4K | tak | tak | 0.4 @ 1080p | 24 | 48.00 | srednia | 2026-11-27 |
| 11 | Seedance — Dreamina Seedance 2.5 (dreamina-seedance-2-5-260628) | 30 | 4K | tak | tak | 0.56862 @ 1080p | 34.12 | 68.24 | wysoka | 2026-11-26 |
| 12 | OpenAI — sora-2-pro 1080p **(NIEDOSTEPNY od 2026-09-24)** | 20 | 1920x1080 | tak | tak | 0.7 @ 1080p | 42 | 84.00 | srednia | 2026-03-12 (changelog OpenAI) |

### B. Na koncu: brak 1080p albo cena nie dotyczy 1080p (koszt NIE jest kosztem Full HD)

| poz. | dostawca i model | maks. dlugosc klipu (s) | maks. rozdzielczosc | 1080p dostepne | audio natywne | cena za sekunde (USD) przy podanej rozdzielczosci | koszt 1 minuty przy podanej rozdzielczosci (USD; NIE Full HD) | koszt 1 minuty przy 2 probach (x2, informacyjnie) | pewnosc | data cennika |
|---|---|---|---|---|---|---|---|---|---|---|
| 13 | MiniMax — MiniMax-H3-Lite | 15 | 768P | nie | nie (NIEPOTWIERDZONE) | 0.04 @ 768P | 2.4 (768P) | 4.80 | srednia | 2026-11-27 (data odczytu; brak daty na stronie) |
| 14 | Seedance — Dreamina Seedance 2.0 Mini (dreamina-seedance-2-0-mini-260615) | 15 | 720p | nie | tak | 0.0756 @ 720p | 4.54 (720p) | 9.08 | wysoka | 2026-11-26 |
| 15 | Kling — Kling 4.0 Flash | 20 | 720p | nie | nie (NIEPOTWIERDZONE) | 0.0923 @ 720p | 5.54 (720p) | 11.08 | srednia | 2026-11-27 (data odczytu; API od 2026-11-04) |
| 16 | OpenAI — sora-2 **(NIEDOSTEPNY od 2026-09-24)** | 20 | 1280x720 | nie | tak | 0.1 @ 720p | 6 (720p) | 12.00 | srednia | odczyt 2026-11-27 (cennik archiwalny, bez daty publikacji) |
| 17 | Seedance — Dreamina Seedance 2.0 Fast (dreamina-seedance-2-0-fast-260128) | 15 | 720p | nie | tak | 0.12096 @ 720p | 7.26 (720p) | 14.52 | wysoka | 2026-11-26 |
| 18 | MiniMax — MiniMax-H3 | 15 | 2K | nie (brak 1080P) | tak | 0.13 @ 2K | 7.8 (2K) | 15.60 | srednia | 2026-11-27 (data odczytu) |
| 19 | OpenAI — sora-2-pro 720p **(NIEDOSTEPNY od 2026-09-24)** | 20 | 1920x1080 | tak (wariant 1080p = poz. 12) | tak | 0.3 @ 720p | 18 (720p) | 36.00 | srednia | odczyt 2026-11-27 |
| 20 | OpenAI — sora-2-pro 1024p **(NIEDOSTEPNY od 2026-09-24)** | 20 | 1920x1080 | tak (wariant 1080p = poz. 12) | tak | 0.5 @ 1024p (1792x1024) | 30 (1024p) | 60.00 | srednia | odczyt 2026-11-27 |

Pozycje 19 i 20 to ten sam model co pozycja 12, w nizszej rozdzielczosci; sa w sekcji B, bo ich cena nie dotyczy 1080p.

## 2. Zrodla dla kazdej pozycji (URL, rzad)

1. MiniMax-Hailuo-2.3-Fast: https://platform.minimax.io/docs/guides/pricing-paygo (rzad 1); https://platform.minimax.io/docs/api-reference/video-generation-t2v (rzad 1)
2. Veo 3.1 Lite: https://cloud.google.com/vertex-ai/generative-ai/pricing (rzad 1, odczyt bezposredni); https://ai.google.dev/gemini-api/docs/veo (rzad 1, streszczenie: 4/6/8 s, 1080p tylko 8 s); https://docs.cloud.google.com/vertex-ai/generative-ai/docs/models/veo/3-1-lite-generate (rzad 1, streszczenie: 720p/1080p)
3. MiniMax-Hailuo-2.3: https://platform.minimax.io/docs/guides/pricing-paygo (rzad 1); https://platform.minimax.io/docs/api-reference/video-generation-t2v (rzad 1)
4. Gemini Omni 1.2 Flash: https://cloud.google.com/vertex-ai/generative-ai/pricing (rzad 1, odczyt bezposredni, sekcja Gemini Omni); https://cloud.google.com/blog/products/ai-machine-learning/gemini-omni-1-2-flash-generally-available (rzad 1, blog dostawcy: 15 s, upscaling 1080p/4K, 0.07 USD/s 720p)
5. Veo 3.1 Fast: https://cloud.google.com/vertex-ai/generative-ai/pricing (rzad 1, odczyt bezposredni); https://cloud.google.com/vertex-ai/generative-ai/docs/models/veo/3-1-fast-generate-preview (rzad 1, streszczenie: 4/6/8 s, 720p/1080p/4K)
6. Kling 3.0 Omni: https://kling.ai/dev/pricing (rzad 1); https://kling.ai/document-api/pricing/base/video (rzad 1); https://kling.ai/document-api/api/video/3-0-omni/text-to-video (rzad 1)
7. Kling 3.0: https://kling.ai/dev/pricing (rzad 1); https://kling.ai/document-api/pricing/base/video (rzad 1)
8. Kling 4.0: https://kling.ai/dev/pricing (rzad 1); https://kling.ai/document-api/api/usage-guide/kling-4-0 (rzad 1); https://kling.ai/dev/model-release/kling-4 (rzad 1)
9. Seedance 2.0: https://docs.byteplus.com/en/docs/modelark/model-pricing?redirect=1 (rzad 1, stawka 1080p 7.7 USD/M; przyklad 5 s 1.87 USD); https://docs.byteplus.com/en/docs/modelark/model-list (rzad 1, 4-15 s, do 4K, 24 fps); https://docs.byteplus.com/en/docs/modelark/seedance-2-5 (rzad 1, audio tak)
10. Veo 3.1: https://cloud.google.com/vertex-ai/generative-ai/pricing (rzad 1, odczyt bezposredni); https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/veo/3-1-generate (rzad 1, streszczenie: 4/6/8 s, 720p/1080p/4K)
11. Seedance 2.5: https://docs.byteplus.com/en/docs/modelark/model-pricing?redirect=1 (rzad 1, stawka 1080p 11.7 USD/M; przyklad 5 s 1080p 2.843 USD; UpdatedTime 2026-11-26); https://ai.byteplus.com/ark/region:ap-southeast-1/docs/model-pricing (rzad 1, kanoniczny adres cennika); https://docs.byteplus.com/en/docs/modelark/model-list (rzad 1, 4-30 s, 480p-4K, 24 fps); https://docs.byteplus.com/en/docs/modelark/seedance-2-5 (rzad 1, generowanie wideo z audio)
12. sora-2-pro 1080p: https://developers.openai.com/api/docs/changelog (rzad 1, 1080p za 0.70 USD/s od 2026-03-12); https://developers.openai.com/api/docs/pricing (rzad 1); https://developers.openai.com/api/docs/deprecations (rzad 1)
13. MiniMax-H3-Lite: https://platform.minimax.io/docs/pricing/overview (rzad 1, cena 0.04/0.025); https://platform.minimax.io/docs/api-reference/video-generation-v2-create (rzad 1, 4-15 s, 480P/768P); https://platform.minimax.io/docs/api-reference/api-overview (rzad 1, 4-15 s, 480P/768P)
14. Seedance 2.0 Mini: https://docs.byteplus.com/en/docs/modelark/model-pricing?redirect=1 (rzad 1, 1080p Not supported; 720p 5 s 0.38 USD); https://docs.byteplus.com/en/docs/modelark/model-list (rzad 1, 480p/720p, 4-15 s)
15. Kling 4.0 Flash: https://kling.ai/dev/pricing (rzad 1); https://kling.ai/document-api/updates/api (rzad 1)
16. sora-2: https://developers.openai.com/api/docs/models/sora-2 (rzad 1, 0.10 USD/s, 720x1280 i 1280x720); https://developers.openai.com/api/docs/pricing (rzad 1); https://developers.openai.com/api/docs/deprecations (rzad 1, wylaczenie 2026-09-24)
17. Seedance 2.0 Fast: https://docs.byteplus.com/en/docs/modelark/model-pricing?redirect=1 (rzad 1, 1080p Not supported; 720p 5 s 0.60 USD); https://docs.byteplus.com/en/docs/modelark/model-list (rzad 1, 480p/720p, 4-15 s)
18. MiniMax-H3: https://platform.minimax.io/docs/guides/pricing-video (rzad 1); https://platform.minimax.io/docs/api-reference/video-generation-v2-create (rzad 1)
19. sora-2-pro 720p: https://developers.openai.com/api/docs/pricing (rzad 1); https://developers.openai.com/api/docs/models/sora-2-pro (rzad 1)
20. sora-2-pro 1024p: https://developers.openai.com/api/docs/pricing (rzad 1); https://developers.openai.com/api/docs/models/sora-2-pro (rzad 1)

Uwaga do zrodel OpenAI (poz. 12, 16, 19, 20): zrodla rzedu 1 odczytane tylko przez wyszukiwarke, bo hosty OpenAI sa zablokowane w sieci sesji.

## 3. Dostawcy bez dostepnego API / pay-as-you-go

**OpenAI Sora 2 / Sora 2 Pro — NIEDOSTEPNE.** API wylaczone 2026-09-24 (Videos API, sora-2, sora-2-pro i snapshoty), zastepcy brak (deprecations OpenAI, help.openai.com art. 20001152). Aplikacja Sora zamknieta 2026-04-26. Azure OpenAI: wg forum koniec 2026-06-06 — NIEPOTWIERDZONE. Ceny w tabeli (poz. 12, 16, 19, 20) to ostatni cennik standard przed wylaczeniem; dzis nie da sie z nich skorzystac. Pozycje sa w tabeli wylacznie po to, by zakres (Sora 2) byl jawnie opisany.

Pozostali czterej dostawcy (Kling, Seedance/BytePlus ModelArk, Google Vertex AI / Gemini API, MiniMax API Platform) maja ceny pay-as-you-go lub za jednostki API na dzien zestawienia.

## 4. Uwagi o metodzie i niepewnosciach

**Metoda.**
- Wszystkie ceny to rozliczenie pay-as-you-go / API / jednostki API, nie abonament miesieczny. Zadna liczba docelowa nie pochodzi z abonamentu.
- Koszt liniowy: cena za sekunde x 60. Dla Kling 4.0 i 4.0 Flash cena jednostki pochodzi z pakietu API Standard Package 1 (500 USD / 3250 Units = 0.153846 USD/Unit), dla Kling 3.x z ceny cennikowej 0.14 USD/Unit. Dla Seedance i Gemini Omni cena za sekunde wynika z ceny za 1 mln tokenow x liczba tokenow na sekunde.
- Koszt nie obejmuje prob nieudanych ani powtorzen; kolumna "x2" to tylko ilustracja przy dwoch probach na klip.
- Ceny dotycza wariantu z audio tam, gdzie dostawca je rozroznia (Veo, Kling 3.x); warianty bez audio podano w uwagach ponizej, poza tabela.
- Sortowanie: rosnaco po koszcie 1 minuty przy 1080p (sekcja A); pozycje bez 1080p lub z cena przy innej rozdzielczosci sa na koncu (sekcja B), rowniez posortowane rosnaco po swoim koszcie.

**Pozycje bez 1080p lub bez ceny przy 1080p.**
- MiniMax-H3-Lite (768P), Seedance 2.0 Mini i 2.0 Fast (720p, 1080p "Not supported"), Kling 4.0 Flash (720p), sora-2 (720p), MiniMax-H3 (2K, brak 1080P w cenniku): koszt w sekcji B nie jest kosztem Full HD.
- sora-2-pro 720p i 1024p: model ma 1080p (poz. 12), ale te ceny dotycza nizszych rozdzielczosci.

**Niepewnosci i uwagi szczegolowe (z raportow wezlow).**
- MiniMax Hailuo 2.3 / 2.3 Fast: przy 1080P maks. 6 s (10 s tylko przy 768P); audio BRAK DANYCH. Hailuo 2.3 oznaczony jako legacy.
- MiniMax-H3-Lite: audio natywne NIEPOTWIERDZONE. MiniMax-H3: generate_audio domyslnie true; czy cena bez audio jest ta sama — NIEPOTWIERDZONE; przy 768P 0.08 USD/s = 4.80 USD/min.
- Veo 3.1 Lite / Fast / 3.1: maks. dlugosc 8 s potwierdzona posrednio (streszczenie dokumentacji); dla Veo 3.1 jednostka "count" = sekunda potwierdzona posrednio. Bez audio: Lite 0.05/s (3.00 USD/min), Fast 0.10/s (6.00 USD/min), Veo 3.1 0.20/s (12.00 USD/min).
- Gemini Omni 1.2 Flash: 1080p to upscaling, nie natywna generacja; cennik podaje tylko wariant z audio (ceny bez audio brak). Rachunek 8688 x 12 / 1e6 = 0.104256 USD/s.
- Kling 3.0 Omni: przy wideo wejsciowym brak audio natywnego; bez audio przy 1080p 0.112 USD/s (6.72 USD/min). Kling 3.0: komunikat z 2026-06-17 o 1.0 U/s nie wskazuje modelu i nie zostal uzyty.
- Kling 4.0: przy cenie katalogowej 0.157 USD/Unit wychodzi 14.13 USD/min (w tabeli 13.85 z pakietu). Osobna stawka audio i parametr audio w endpoincie 4.0 — NIEPOTWIERDZONE.
- Kling 4.0 Flash: audio natywne NIEPOTWIERDZONE.
- Seedance 2.0 i 2.5: cena z audio i bez audio jest ta sama (cennik nie rozroznia). Seedance 2.5: wymiary 1920x1080 przyjete przez Operatora zgadzaja sie z przykladem z cennika; przy 1920x1088 wyszloby 34.37 USD/min. Wejscie wideo jest drozsze (2.0: 4.7 USD/M; 2.5: 7.0 USD/M plus minimalne zuzycie).
- Sora 2: maks. klip 20 s wg changelogu z 2026-03-12 i Prompting Guide, 12 s wg strony referencyjnej Create (rozbieznosc). Ceny batch (0.05 USD/s dla sora-2 — NIEPOTWIERDZONE) nie sa liczbami docelowymi.
- Pewnosc "srednia" wynika glownie z braku daty na stronach cennikow (data = data odczytu) albo z potwierdzenia posredniego; "wysoka" — cennik z data aktualizacji i przykladem liczbowym zgodnym z rachunkiem.

## 5. OPINIA (opinia Operatora, nie fakt)

- OPINIA: dla klipow 7-10 s przy 1080p z audio natywnym najtansze w danych sa Veo 3.1 Lite (4.8 USD/min, ale klip 8 s) i Gemini Omni 1.2 Flash (6.26 USD/min, klip 15 s, 1080p tylko z upscalingu).
- OPINIA: MiniMax Hailuo 2.3 / 2.3 Fast jest najtanszy przy 1080P, ale daje maks. 6 s i brak danych o audio, wiec dla dialogow w 7-10 s wymaga ciecia ujec i osobnego audio.
- OPINIA: Kling 3.0 Omni / 3.0 / 4.0 (8.4-13.85 USD/min) to srodek cenowy z klipami 15-30 s i audio natywnym; dluzszy klip miesci cala wymiane dialogowa w jednym ujeciu.
- OPINIA: Seedance 2.0 / 2.5 i Veo 3.1 (22.45-34.12 USD/min) sa wielokrotnie drozsze od najtanszych pozycji 1080p; bez testu nie da sie powiedziec, czy roznica przeklada sie na jakosc.
- OPINIA: Sora 2 odpada — API wylaczone od 2026-09-24.
- OPINIA: dane nie mowia nic o spojnosci postaci ani jakosci polskiej mowy; to wymaga RESEARCH-002/003 i testu probnego przed wyborem (D2).
