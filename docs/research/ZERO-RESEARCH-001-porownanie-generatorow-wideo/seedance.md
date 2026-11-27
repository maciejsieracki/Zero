# ZERO-RESEARCH-001 — wezel b: Seedance (ByteDance)

Runda 4 z 4. Data odczytu zrodel: 2026-11-27. Kanal: oficjalne API BytePlus ModelArk (region ap-southeast-1), rozliczenie pay-as-you-go za tokeny ("Online inference"). **Status wezla: dane ze zrodel rzedu 1.**

## Jak odczytano zrodla (odpowiedz na zarzut ENV-1)

- WebFetch nadal zwraca `ENOTFOUND docs.byteplus.com` (narzedzie rozwiazuje DNS poza proxy sesji). Strony pobrano wiec `curl` przez proxy sesji i odczytano tresc dokumentu osadzona w HTML (pole markdown dokumentu).
- `https://docs.byteplus.com/en/docs/ModelArk/1544106` -> 302 -> `https://docs.byteplus.com/en/docs/modelark/model-pricing?redirect=1` (kod 200). Tytul dokumentu: "Pricing"; metadane strony: `UpdatedTime 2026-11-26T11:25:02Z`.
- `https://docs.byteplus.com/en/docs/modelark/model-list` (200) — tabele "Video generation": Capabilities, Output (rozdzielczosc, fps, dlugosc).
- `https://docs.byteplus.com/en/docs/modelark/seedance-2-5` (200) — "Dreamina Seedance 2.5 series tutorial", tabela "Capabilities overview" (takze dla serii 2.0), w tym wiersz "Generate video with audio".
- `https://ai.byteplus.com/ark/region:ap-southeast-1/docs/model-pricing` (200) — kanoniczny adres cennika, do ktorego odsyla sam dokument.
- Volcengine: `https://www.volcengine.com/docs/82379/1544106` przekierowuje na `docs.volcengine.com`, ktory nie odpowiada w sieci sesji (kod 000). Cennika Volcengine (rynek chinski, CNY) nie odczytano — patrz "Czego nie potwierdzono".

## Tabela modeli (zrodla rzedu 1, 2026-11-27)

| Model (ID w API) | Maks. klip | Maks. rozdz. | 1080p | Audio natywne | Cena / 1 mln tokenow (bez wejscia wideo) | Cena / s | Koszt 1 min | Pewnosc |
|---|---|---|---|---|---|---|---|---|
| Dreamina Seedance 2.5 (`dreamina-seedance-2-5-260628`) — najlepszy | 30 s (4-30 s) | 4K | tak (10-bit) | tak (`generate_audio`) | 11,7 USD (1080p) | **0,56862 USD @1080p** | **34,12 USD @1080p** | wysoka |
| Dreamina Seedance 2.0 (`dreamina-seedance-2-0-260128`) | 15 s (4-15 s) | 4K | tak (8-bit) | tak | 7,7 USD (1080p) | **0,37422 USD @1080p** | **22,45 USD @1080p** | wysoka |
| Dreamina Seedance 2.0 Fast (`dreamina-seedance-2-0-fast-260128`) | 15 s (4-15 s) | 720p | **nie** | tak | 5,6 USD (480p/720p) | 0,12096 USD @720p (nie 1080p) | 7,26 USD @720p (nie 1080p) | wysoka |
| Dreamina Seedance 2.0 Mini (`dreamina-seedance-2-0-mini-260615`) — najtanszy | 15 s (4-15 s) | 720p | **nie** | tak | 3,5 USD (480p/720p) | 0,0756 USD @720p (nie 1080p) | 4,54 USD @720p (nie 1080p) | wysoka |

Poza tabela (limit 4 modeli): Dreamina Seedance 2.5 Flash (`dreamina-seedance-2-5-flash-261115`) — 4-30 s, maks. 720p (1080p: "Not supported"), audio tak, 7,0 USD / 1 mln -> 0,1512 USD/s @720p -> 9,07 USD/min @720p. Starsze Seedance 1.0 Pro / 1.0 Pro Fast — 2-12 s, 1080p, w tabeli mozliwosci brak wiersza audio dla serii 1.0 (nie badano, model poprzedniej generacji).

## Rachunek kosztu krok po kroku

Wzor z cennika ("Billing rules"): `Estimated token consumption = (Input video duration + output video duration) x output video width x output video height x output video frame rate / 1024`; `Estimated video price = Token unit price x token consumption`. Bez wejscia wideo: input video duration = 0. Frame rate = 24 fps (model-list, kolumna "Frame rate", wszystkie modele). Wymiary 1920x1080 i 1280x720 dla 16:9 to przyjecie operatora — zgodnosc potwierdzona przykladami z cennika (krok 4 kazdego wiersza).

**Seedance 2.5 @1080p**
1. Tokeny/s = 1920 x 1080 x 24 / 1024 = 48 600.
2. Cena/s = 48 600 x 11,7 / 1 000 000 = 0,56862 USD.
3. Koszt 1 min = 0,56862 x 60 = 34,1172 = **34,12 USD**.
4. Kontrola: 5 s = 2,8431 USD; cennik (Billing examples, 1080p 16:9, 5 s): "$2.843 per video, $0.569 per second". Z przykladu: 2,843 / 5 x 60 = 34,116 USD — zgodne.

**Seedance 2.0 @1080p**
1. Tokeny/s = 48 600.
2. Cena/s = 48 600 x 7,7 / 1 000 000 = 0,37422 USD.
3. Koszt 1 min = 0,37422 x 60 = 22,4532 = **22,45 USD**.
4. Kontrola: 5 s = 1,8711 USD; cennik: "$1.87 per video, $0.37 per second". Z przykladu: 1,87 / 5 x 60 = 22,44 USD (roznica 0,01 USD z zaokraglenia 1,87).

**Seedance 2.0 Fast @720p (1080p niedostepne)**
1. Tokeny/s = 1280 x 720 x 24 / 1024 = 21 600.
2. Cena/s = 21 600 x 5,6 / 1 000 000 = 0,12096 USD.
3. Koszt 1 min = 0,12096 x 60 = 7,2576 = **7,26 USD @720p**.
4. Kontrola: cennik 720p 5 s: "$0.60 per video, $0.12 per second" (0,6048 po zaokragleniu).

**Seedance 2.0 Mini @720p (1080p niedostepne)**
1. Tokeny/s = 21 600.
2. Cena/s = 21 600 x 3,5 / 1 000 000 = 0,0756 USD.
3. Koszt 1 min = 0,0756 x 60 = 4,536 = **4,54 USD @720p**.
4. Kontrola: cennik 720p 5 s: "$0.38 per video, $0.08 per second" (0,378 po zaokragleniu).

## Audio, warianty i inne roznice cen

- Wszystkie piec modeli serii 2.x ma w tabeli "Capabilities overview" wiersz "Generate video with audio" = ● (dokument seedance-2-5); w API parametr `generate_audio`. Cennik nie rozroznia ceny z dzwiekiem i bez dzwieku dla serii 2.x (jedna stawka za token, brak kolumny audio) — liczby powyzej dotycza wariantu z natywnym audio i sa takie same bez audio. (Rozroznienie audio/bez audio wystepuje w cenniku tylko dla trybu Draft Seedance 1.5 Pro: wspolczynnik 0,6 z audio, 0,7 bez — nie dotyczy tabeli.)
- Wejscie wideo (edycja, przedluzanie, referencja wideo) ma nizsza stawke za token, ale tokeny licza sie od sumy czasu wejscia i wyjscia i obowiazuje minimalne zuzycie: 1080p Seedance 2.5 = 7,0 USD / 1 mln, Seedance 2.0 = 4,7 USD / 1 mln. Przyklady z cennika (wyjscie 5 s 1080p): 2.5: 3,062-11,907 USD; 2.0: 2,06-4,57 USD. Nie uzyte jako liczba docelowa.
- 4K: Seedance 2.5 = 4,7 USD / 1 mln (przyklad 5 s: 4,568 USD, 0,914 USD/s); Seedance 2.0 = 4,0 USD / 1 mln (3,89 USD, 0,78 USD/s).
- Jezyki mowy w Seedance 2.5 (dokument seedance-2-5): 11 jezykow — chinski, angielski, hiszpanski, indonezyjski, malajski, tajski, arabski, portugalski, wietnamski, japonski, koreanski. Polskiego nie ma na liscie (temat RESEARCH-002).
- Limity domyslne (model-list): konto indywidualne 180 RPM i 3 zadania rownolegle; Seedance 2.0 4K: 1 zadanie rownolegle. Offline inference dla serii 2.x: "Not supported".

## Czego nie potwierdzono / niepewnosc

- Dokladne wymiary pikseli 1080p/720p w serii 2.x nie sa podane w cenniku (dla Seedance 1.0 Pro cennik podaje 1920x1088). Przyjeto 1920x1080 i 1280x720 — wynik zgadza sie z oficjalnymi przykladami do 0,001 USD; przy 1920x1088 cena/s 2.5 bylaby 0,57283 USD (34,37 USD/min, +0,7%).
- Rzeczywiste zuzycie okresla `usage.completion_tokens` w odpowiedzi API; cennik nazywa wzor "estimate".
- Cennika Volcengine (CNY) nie odczytano: `docs.volcengine.com` niedostepny w sieci sesji.
- Ceny dotycza regionu ap-southeast-1 (BytePlus); inne regiony nie sprawdzane. Pakiety tokenow / plany ("Seedance 2.5 Plan", Coding/Agent Plan) nie byly podstawa kosztu.
- Poszlaki z rund 1-3 (np. "Seedance 2.5 coming soon" wg CometAPI) sa nieaktualne: Seedance 2.5 jest w cenniku i liscie modeli.

## Zrodla

| URL | Rzad | Odczyt 2026-11-27 | Co potwierdza |
|---|---|---|---|
| https://docs.byteplus.com/en/docs/modelark/model-pricing?redirect=1 (z https://docs.byteplus.com/en/docs/ModelArk/1544106) | 1 | tak (curl, 200; UpdatedTime 2026-11-26) | stawki za 1 mln tokenow, wzor tokenow, przyklady cen 5 s, brak 1080p dla Fast/Mini/2.5 Flash |
| https://ai.byteplus.com/ark/region:ap-southeast-1/docs/model-pricing | 1 | tak (200; adres kanoniczny cennika) | jw. |
| https://docs.byteplus.com/en/docs/modelark/model-list | 1 | tak (200) | rozdzielczosci, 24 fps, dlugosci 4-15 s / 4-30 s, limity |
| https://docs.byteplus.com/en/docs/modelark/seedance-2-5 | 1 | tak (200) | audio natywne (Generate video with audio, `generate_audio`), 30 s dla 2.5, jezyki |
| https://www.volcengine.com/docs/82379/1544106 | 1 | NIE (przekierowanie na docs.volcengine.com, brak polaczenia) | — |
| https://www.cometapi.com/seedance-2-5-api-pricing/ | 4 | runda 1, tylko streszczenie | nieuzywane (NIEPOTWIERDZONE, nieaktualne) |
