# ZERO-RESEARCH-001-c — Google Veo i Gemini Omni (Vertex AI / Gemini API)

Wezel: c (Google). Runda: 2 z 3 (poprawki wg zarzutow E-c-1-1, E-c-1-2). Data odczytu zrodel: 2026-11-27 (UTC).
Rozliczenie: pay-as-you-go: cena za sekunde wygenerowanego wideo (Veo) albo cena za tokeny wyjsciowe wideo przeliczona na sekunde (Gemini Omni), cennik Vertex AI / Gemini Enterprise Agent Platform. Abonamenty (Google AI Pro/Ultra, Flow, Gemini for business) NIE sa podstawa zadnej liczby.

## Ograniczenia srodowiska (wazne dla Evaluatora)

- `cloud.google.com` (cennik i Cloud Blog): dostepne, odczyt bezposredni (curl, HTML).
- `ai.google.dev`, `docs.cloud.google.com`, `blog.google`, `deepmind.google`: ZABLOKOWANE w sieci sesji (ENOTFOUND / proxy 403). Dane z tych stron znane tylko ze streszczen wyszukiwarki (WebSearch) stron oficjalnych.
- Zeby podniesc pewnosc, trzeba dopuscic w ustawieniach sieci hosty `ai.google.dev` i `docs.cloud.google.com` i ponowic odczyt.

## Zakres (decyzja wezla)

Zarzut E-c-1-1 przyjety: Gemini Omni Flash to rodzina wideo Google dostepna przez API (Gemini API i Vertex), z natywnym audio, ujeta w tym samym cenniku co Veo. Dodana do wezla. Limit zlecenia: maks. 4 modele w tabeli glownej (w tym najtanszy i najlepszy jakosciowo). W tabeli glownej: Veo 3.1 Lite (najtanszy), Gemini Omni 1.2 Flash, Veo 3.1 Fast, Veo 3.1 (najlepszy jakosciowo). Gemini Omni 1.1 Flash (poprzednia, drozsza wersja tej samej rodziny) jest opisany w pelni w sekcji "Dodatkowo", z rachunkiem.

## Tabela modeli (wariant z natywnym audio, 1080p), posortowana od najtanszego

| Model | Maks. klip (s) | Maks. rozdz. | 1080p | Natywne audio | Cena/s 1080p z audio (USD) | Koszt 1 min (USD) | Cena/s 1080p bez audio | 1 min bez audio | Pewnosc |
|---|---|---|---|---|---|---|---|---|---|
| Veo 3.1 Lite (najtanszy) | 8 | 1080p (brak 4K) | tak | tak | 0.08 | 4.80 | 0.05 | 3.00 | srednia |
| Gemini Omni 1.2 Flash | 15 | 4K (upscaling) | tak, przez upscaling (baza 360p/720p) | tak | 0.104256 | 6.26 | brak wariantu w cenniku | — | srednia |
| Veo 3.1 Fast | 8 | 4K | tak | tak | 0.12 | 7.20 | 0.10 | 6.00 | srednia |
| Veo 3.1 (najlepszy jakosciowo) | 8 | 4K | tak | tak | 0.40 | 24.00 | 0.20 | 12.00 | srednia |

Dodatkowo (poza limitem 4):

| Model | Maks. klip (s) | Maks. rozdz. | 1080p | Natywne audio | Cena/s 1080p z audio (USD) | Koszt 1 min (USD) | Pewnosc |
|---|---|---|---|---|---|---|---|
| Gemini Omni 1.1 Flash (= "Gemini Omni Flash") | 10 | 4K (upscaling) | tak, przez upscaling | tak | 0.15204 | 9.12 | srednia |

Pozostale ceny z tego samego cennika (USD/s):
- Veo 3.1: z audio 720p 0.40, 4K 0.60; bez audio 720p 0.20, 4K 0.40.
- Veo 3.1 Fast: z audio 720p 0.10, 4K 0.30; bez audio 720p 0.08, 4K 0.25.
- Veo 3.1 Lite: z audio 720p 0.05; bez audio 720p 0.03; 4K brak w cenniku.
- Gemini Omni 1.2 Flash (z audio): 720p 0.069504, 4K 0.208512 (rachunek nizej).
- Gemini Omni 1.1 Flash (z audio): 720p 0.10136, 4K 0.30408.
- Starsze, nadal w cenniku: Veo 3 (z audio 720p/1080p 0.40; bez audio 0.20), Veo 3 Fast (z audio 720p 0.10, 1080p 0.12; bez audio 0.08 / 0.10), Veo 2 (720p, bez audio, 0.50). Pominiete: Veo 3.x ma te same ceny co 3.1 i jest starsza wersja; Veo 2 nie ma 1080p ani audio.

## Rachunek kosztu krok po kroku

Wzor Veo: koszt 1 min = cena za sekunde x 60.

- Veo 3.1 Lite, 1080p, z audio: 0.08 x 60 = 4.80 USD. (Bez audio: 0.05 x 60 = 3.00 USD.)
- Veo 3.1 Fast, 1080p, z audio: 0.12 x 60 = 7.20 USD. (Bez audio: 0.10 x 60 = 6.00 USD.)
- Veo 3.1, 1080p, z audio: 0.40 x 60 = 24.00 USD. (Bez audio: 0.20 x 60 = 12.00 USD.)

Wzor Gemini Omni: cena/s = tokeny wyjsciowe wideo na sekunde x cena za 1M tokenow / 1 000 000; koszt 1 min = cena/s x 60.
Dane z Z1: "Video Output" 1.2 Flash = 12.00 USD / 1M tokenow; Omni Flash / 1.1 Flash = 17.50 USD / 1M; przypis **: 8688 tokenow na sekunde wideo 1080p (z audio), 5792 dla 720p, 17376 dla 4K.

- Omni 1.2 Flash, 1080p: 8688 x 12.00 / 1 000 000 = 0.104256 USD/s; x 60 = 6.25536 USD, czyli 6.26 USD/min.
- Omni 1.2 Flash, 720p: 5792 x 12.00 / 1e6 = 0.069504 USD/s (zgodne z "0.07 USD per second of 720p" w Z8); x 60 = 4.17 USD/min.
- Omni 1.2 Flash, 4K: 17376 x 12.00 / 1e6 = 0.208512 USD/s; x 60 = 12.51 USD/min.
- Omni 1.1 Flash, 1080p: 8688 x 17.50 / 1e6 = 0.15204 USD/s; x 60 = 9.1224 USD, czyli 9.12 USD/min.
- Omni 1.1 Flash, 720p: 5792 x 17.50 / 1e6 = 0.10136 USD/s; x 60 = 6.08 USD/min.

Kontrola spojnosci przypisu: 8688 = 5792 (720p) + 2896 (upscaling 720p -> 1080p); 17376 = 5792 + 11584 (720p -> 4K). Stawka 1080p obejmuje wiec generacje bazowa 720p i upscaling w jednej liczbie (interpretacja wezla, nie stwierdzona wprost w cenniku).
Pominiete w koszcie: tokeny wejsciowe promptu (1.50 USD / 1M; obraz referencyjny 1120 tokenow = ok. 0.0017 USD) — ponizej 1 centa na klip.

Uwaga praktyczna (nie zmienia liczby docelowej): Veo 8 s -> 8 klipow = 64 s na minute (Lite 5.12, Fast 7.68, Veo 3.1 25.60 USD z audio). Omni 1.2 Flash pozwala na 3-15 s co 1 s, wiec 4 klipy x 15 s = dokladnie 60 s. Odrzucone ujecia mnoza koszt.

## Zrodla

| # | URL | Rzad | Data odczytu | Co potwierdza | Sposob odczytu |
|---|---|---|---|---|---|
| Z1 | https://cloud.google.com/vertex-ai/generative-ai/pricing (przekierowanie na https://cloud.google.com/model-garden/pricing; ta sama tabela pod https://cloud.google.com/gemini-enterprise-agent-platform/generative-ai/pricing) | 1 | 2026-11-27 | wszystkie ceny Veo; sekcja "Gemini Omni": 1.2 Flash Video Output 12.00 USD/1M, Omni Flash / 1.1 Flash 17.50 USD/1M, tokeny/s 360p/720p/1080p/4K "(with audio)", tokeny upscalingu | bezposrednio (HTML) |
| Z2 | https://ai.google.dev/gemini-api/docs/pricing | 1 | 2026-11-27 | jednostka "per second" dla Veo, Lite 1080p z audio 0.08/s, 720p 0.05/s, brak 4K dla Lite | tylko streszczenie wyszukiwarki (host zablokowany) |
| Z3 | https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/veo/3-1-generate (takze .../vertex-ai/generative-ai/docs/models/veo/3-1-generate) | 1 | 2026-11-27 | Veo 3.1: dlugosci 4, 6, 8 s; 720p/1080p/4K; karta Lite (veo-3.1-lite-generate-001, Preview, 2026-04-02): 720p i 1080p | tylko streszczenie wyszukiwarki (host zablokowany) |
| Z4 | https://ai.google.dev/gemini-api/docs/veo | 1 | 2026-11-27 | tabela specyfikacji obejmujaca Lite: 4, 6, 8 s; 1080p (i 4K) tylko przy 8 s | tylko streszczenie wyszukiwarki (host zablokowany) |
| Z4a | https://cloud.google.com/vertex-ai/generative-ai/docs/models/veo/3-1-fast-generate-preview (przekierowanie na docs.cloud.google.com; wersja zh-tw .../veo/3-1-generate?hl=zh-tw) | 1 | 2026-11-27 | Veo 3.1 Fast: dlugosc 4, 6 lub 8 s; 720p, 1080p, 4K | tylko streszczenie wyszukiwarki (host zablokowany) |
| Z4b | https://docs.cloud.google.com/vertex-ai/generative-ai/docs/models/veo/3-1-lite-generate (karta Lite) | 1 | 2026-11-27 | Lite: 720p/1080p, Preview; dlugosc w streszczeniu nierozdzielona od sekcji Veo 3.1 | tylko streszczenie wyszukiwarki (host zablokowany) |
| Z5 | https://cloud.google.com/blog/products/ai-machine-learning/veo-3-1-lite-and-a-new-veo-upscaling-capability-on-vertex-ai (2026-04-03) | 1-2 (blog dostawcy) | 2026-11-27 | rodzina Veo 3.1 = trzy poziomy (3.1, Fast, Lite), wszystkie z natywnym audio | bezposrednio (HTML) |
| Z8 | https://cloud.google.com/blog/products/ai-machine-learning/gemini-omni-1-2-flash-generally-available (2026-11-06) | 1-2 (blog dostawcy) | 2026-11-27 | Omni 1.2 Flash GA na Google Cloud i przez API; klipy do 15 s (wczesniej 10 s); 0.07 USD/s 720p; drafty 360p/720p, upscaling do 1080p lub 4K; dialogi, lip-sync, wielu mowcow | bezposrednio (HTML) |
| Z9 | https://blog.google/innovation-and-ai/technology/developers-tools/introducing-gemini-omni-1-2-flash/ | 1-2 (blog dostawcy) | 2026-11-27 | dlugosc 3-15 s co 1 s; audio synchroniczne do 15 s przy 360p/720p/1080p/4K | tylko streszczenie wyszukiwarki (host zablokowany) |
| Z10 | https://ai.google.dev/gemini-api/docs/omni (oraz .../docs/models/gemini-omni-flash) | 1 | 2026-11-27 | gemini-omni-1.1-flash: 3-10 s; 360p/720p/1080p/4K, 24 FPS; domyslnie 720p; 1080p "(upscaled)" | tylko streszczenie wyszukiwarki (host zablokowany) |
| Z11 | https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/gemini/omni-1-2-flash, .../omni-1-1-flash | 1 | 2026-11-27 | istnienie kart modeli na Vertex | tylko tytul w wyniku wyszukiwarki |
| Z6 | https://discuss.ai.google.dev/t/veo-3-1-lite-pricing-shows-0-05-per-video-but-actually-costs-8-times-more/143844 | 4 (forum) | 2026-11-27 | poszlaka, ze "count" = sekunda — NIEPOTWIERDZONE | tylko wynik wyszukiwarki |
| Z7 | https://benchlm.ai/media-pricing/veo, https://wavespeed.ai/blog/cost-and-billing/google-veo-3-pricing/, https://vercel.com/ai-gateway/models/veo-3.1-lite-generate-001 | 5 (agregatory) | 2026-11-27 | poszlaki zgodne z Z1/Z4 (Lite 4/6/8 s, 720p/1080p); Vercel ma tez przyklad 5 s dla Lite — NIEPOTWIERDZONE | tylko wynik wyszukiwarki |

## Niepewnosci i czego nie udalo sie potwierdzic

1. Jednostka ceny Veo. Cennik Vertex (Z1) podaje "$X / 1 count" bez slowa "sekunda". Interpretacja "1 count = 1 sekunda" opiera sie na Z2 (streszczenie, "per second") i poszlace Z6. Dla Omni jednostka jest jawna (tokeny na sekunde) — tu przeliczenie wynika wprost z Z1.
2. Maks. dlugosc klipu 8 s: Veo 3.1 — Z3/Z4 (streszczenia stron oficjalnych). Veo 3.1 Fast — potwierdzone posrednio (Z4a, streszczenie karty modelu: 4, 6, 8 s). Veo 3.1 Lite — potwierdzone posrednio (Z4 tabela Gemini API: 4, 6, 8 s, 1080p tylko przy 8 s; karta Z4b nie rozdziela dlugosci od sekcji Veo 3.1). Agregator Vercel (rzad 5) pokazuje przyklad 5 s dla Lite — sprzeczna poszlaka, NIEPOTWIERDZONE.
3. Przedluzanie wideo (extend) nie jest "jednym klipem" — nie liczone (Omni 1.1 wg rzedu 4-5 do 40 s przez przedluzenia — NIEPOTWIERDZONE, poza liczba docelowa).
4. Maks. rozdzielczosc Fast = 4K: wiersz 4K w Z1 i Z4a; Lite bez 4K: brak wiersza w Z1 oraz Z2/Z3.
5. Ceny Veo w Gemini API (ai.google.dev) nie odczytane bezposrednio; dla Lite streszczenie zgadza sie z Vertex. Ceny Omni w Gemini API nie odczytane — liczby wezla to cennik Vertex (Z1); 720p 0.07 USD/s z Z8 zgadza sie z przeliczeniem (0.069504).
6. Cennik nie ma jawnej daty "Last updated" w HTML; data cennika = data odczytu 2026-11-27 (cena Omni 1.2 obowiazuje od GA 2026-11-06 wg Z8).
7. Gemini Omni 1.2 Flash i Omni 1.1 Flash ("Gemini Omni Flash"): 1080p i 4K to upscaling z bazy 360p/720p (Z8 bezposrednio; Z10 "upscaled" dla 1.1), nie natywna generacja w 1080p. Liczba 1080p = stawka za wyjscie 1080p z audio z Z1 (wg kontroli 8688 = 5792 + 2896 obejmuje upscaling). Cennik Omni podaje tylko wariant "with audio"; wariantu bez audio i jego ceny nie znaleziono. Maks. klip 1.2 = 15 s (Z8 bezposrednio), 1.1 = 10 s (Z8 "up from 10s"; Z10 3-10 s, streszczenie). Kart modeli Omni na Vertex (Z11) nie odczytano.
8. Ceny w USD, bez podatku; rabaty Flexible Savings Plans i Provisioned Throughput pominiete — to zobowiazania, nie pay-as-you-go.
