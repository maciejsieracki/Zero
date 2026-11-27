# ZERO-RESEARCH-001-a — Kling (Kuaishou)

Wezel: a (Kling). Runda 2 z 3 (poprawki po zarzutach E-a-1-1, E-a-1-2, E-a-1-3). Data odczytu zrodel: 2026-11-27. Operator (Opus 5.5).

## Zastrzezenie infrastrukturalne (czytac najpierw)

Domeny oficjalne Kling (`kling.ai`, `klingai.com`, `app.klingai.com`) sa **zablokowane w sieci tej sesji** (WebFetch 2026-11-27: ENOTFOUND kling.ai). Wszystkie liczby ponizej pochodza z **indeksu wyszukiwarki (WebSearch) ograniczonego do domen kling.ai / klingai.com**, czyli z tresci oficjalnych stron rzedu 1 odczytanych posrednio (fragmenty indeksu, nie pelna strona). Dlatego pewnosc wynosi najwyzej `srednia`. Aby potwierdzic liczby bezposrednio, host `kling.ai` trzeba dopuscic w ustawieniach sieci sesji.

## Rozliczenie pay-as-you-go (API)

Kling Open Platform (API) rozlicza sie w **jednostkach (Units)**. To nie jest abonament; jest oddzielne od planow czlonkowskich aplikacji (te pominieto zgodnie z regula). **Stawka USD za Unit zalezy od rodziny modelu** (poprawka E-a-1-1 / E-a-1-2): cennik podaje dwie rozne ceny Unit dla dwoch roznych rodzin modeli, a nie dwa stany w czasie.

| Rodzina modeli | Cena 1 Unit w cenniku | Przyklad z cennika | Zrodlo |
|---|---|---|---|
| Kling 4.0, Kling 4.0 Flash | $0.157 katalogowo; pakiety przedplacone (Standard Package 1-3) | "1.5 Units ($0.235) /s" dla 4.0 1080p | Z1, Z2 |
| Kling 3.0, 3.0 Omni, 3.0 Turbo, 2.6, 2.5 Turbo | $0.14 (cena podana wprost w USD przy kazdej stawce) | "1.2 Units ($0.168) /s" dla 3.0 z audio 1080p; "1.0 Unit ($0.14) /s"; 2.6 bez audio 1080p "0.5 Units ($0.07) /s" | Z1, Z2 |

Pakiety przedplacone dla rodziny 4.0 (Z1): Standard Package 1 = $500 za 3 250 Units (-2%, $0.153846/Unit), Package 2 = $2 000 za 13 135 Units (-3%), Package 3 = $8 000 za 53 640 Units (-5%); waznosc 180 dni, bez przedluzenia, 20 zadan rownoleglych.

**Podstawa przeliczenia:**
- Rodzina 4.0 / 4.0 Flash: najtanszy oficjalny pakiet jednorazowy = Standard Package 1: $500 / 3 250 = **$0.153846 za Unit**.
- Rodzina 3.x / 2.6: cena USD podana w cenniku przy kazdej stawce = **$0.14 za Unit** (rodzina nie jest objeta Standard Package 1). Nie znaleziono w indeksie osobnego pakietu dla 3.x z inna cena — przyjeto cene cennikowa.
- Pakiet Trial (starszy snapshot: $9.8 za 100 Units) — **NIEPOTWIERDZONE** w biezacym stanie, pominiety.

## Tabela modeli (wariant: generacja bez wideo wejsciowego; z natywnym audio, jesli model je generuje)

Kolejnosc rosnaco po koszcie 1 min przy 1080p; model bez 1080p na koncu.

| Model | Maks. klip (s) | Maks. rozdzielczosc | 1080p | Audio natywne | Units/s (rozdz. ceny) | Cena Unit | USD/s | USD/min | Pewnosc |
|---|---|---|---|---|---|---|---|---|---|
| Kling 3.0 Omni (audio natywne) | 15 | 4K | TAK | TAK | 1.0 (1080p) | $0.14 | 0.14 | **8.40** | srednia |
| Kling 3.0 (audio natywne) | 15 | 4K | TAK | TAK | 1.2 (1080p) | $0.14 | 0.168 | **10.08** | srednia |
| Kling 4.0 (najlepszy) | 30 | 4K (od 2026-11-19) | TAK | TAK (Z3, rzad 1); osobna stawka audio i parametr `audio` w endpoincie 4.0 NIEPOTWIERDZONE | 1.5 (1080p) | $0.153846 | 0.2308 | **13.85** | srednia |
| Kling 4.0 Flash (najtanszy z rodziny 4.0; bez 1080p) | 20 | 720p | NIE | NIEPOTWIERDZONE | 0.6 (720p) | $0.153846 | 0.0923 | **5.54** (720p, nie 1080p) | srednia |

## Rachunek krok po kroku

- Kling 3.0 Omni, 1080p, audio: 1.0 Unit x $0.14 = $0.14/s (cennik: "1.0 Unit ($0.14) /s"); x 60 = **$8.40/min**
- Kling 3.0, 1080p, audio: 1.2 Units x $0.14 = $0.168/s (cennik: "1.2 Units ($0.168) /s"); x 60 = **$10.08/min**
- Kling 4.0, 1080p: 1.5 Units x ($500 / 3 250 = $0.1538462) = $0.2307692/s; x 60 = $13.846/min -> **$13.85/min**
- Kling 4.0 Flash, 720p: 0.6 Units x $0.1538462 = $0.0923077/s; x 60 = $5.5385/min -> **$5.54/min**

Wrazliwosc rodziny 4.0 na cene Unit (nie jako podstawa): przy cenie katalogowej $0.157 -> 4.0 1080p 1.5 x 0.157 = $0.2355/s (cennik: "$0.235"), x 60 = $14.13/min; 4.0 Flash 720p 0.6 x 0.157 = $0.0942/s, x 60 = $5.65/min.

## Szczegoly i roznice wariantow

- **Kling 4.0** (`kling-4.0`, text-to-video / image-to-video / omni-video): `duration` 3-30 s (domyslnie 10), rozdzielczosci 720p/1080p/4K (4K w API od 2026-11-19). Ceny bez wideo wejsciowego: 1.0 / 1.5 / 3.5 Units/s (720p/1080p/4K). Z wideo wejsciowym: 0.6 / 0.9 / 2.1 Units/s, rozliczany czas = 2 x czas wyjscia (gdy wejscie <= wyjscie) albo wejscie + wyjscie. HDR: +0.3 Units/s (1080p), +0.5 (4K). Audio natywne: instrukcja API Kling 4.0 (Z3, rzad 1) podaje obsluge audio wysokiej jakosci, stereo dwukanalowe, synchronizacje mowy z obrazem; dialogi w cudzyslowie. Cennik **nie podaje osobnej stawki audio** dla 4.0, a w release note 4.0 (Z10) brak wzmianki o parametrze audio — dlatego: czy audio jest wliczone w 1.5 Units/s i czy endpoint 4.0 przyjmuje `audio: native`, **NIEPOTWIERDZONE**.
- **Kling 4.0 Flash**: 3-20 s, maks. 720p (API od 2026-11-04). 0.6 Units/s bez wideo wejsciowego, 0.4 z wideo wejsciowym. Audio natywne — **NIEPOTWIERDZONE**.
- **Kling 3.0 Omni** (`kling-v3-omni`): `duration` 3-15 s, 720p/1080p/4K. Z audio natywnym (bez wideo wejsciowego): 0.8 / 1.0 / 3.0 Units/s; bez audio: 0.6 / 0.8 Units/s (720p/1080p), czyli 1080p bez audio 0.8 x $0.14 = $0.112/s, x 60 = $6.72/min. Roznica audio vs bez audio przy 1080p: $0.028/s ($1.68/min). Z wideo wejsciowym audio natywne nie jest obslugiwane (`audio` tylko `off`).
- **Kling 3.0**: 3-15 s. Z audio natywnym: 0.9 / 1.2 / 3.0 Units/s (720p/1080p/4K); 1080p = "1.2 Units ($0.168) /s". Komunikat API z 2026-06-17 o "1.0 unit/s dla 1080P" nie wskazuje modelu (moze dotyczyc 3.0 Turbo, ktory ma 1.0 Unit/s) — nie uzyty.
- **Pominiete (limit 4 modeli):** Kling 3.0 Turbo — tylko z audio, 0.8 / 1.0 Units/s (720p/1080p), 1080p = $0.14/s -> $8.40/min; maks. dlugosci nie potwierdzono. Kling 2.6 (rodzina $0.14/Unit) — bez audio 0.3 / 0.5 Units/s (720p/1080p): 1080p 0.5 x $0.14 = $0.07/s (cennik: "0.5 Units ($0.07) /s"), x 60 = **$4.20/min**; z audio 1080p 1.0 Unit ($0.14)/s -> $8.40/min; z referencja glosu 1.2 Units ($0.168)/s -> $10.08/min. Kling 2.6 bez audio to najtansze 1080p, ale bez dzwieku — nie nadaje sie do dialogow.
- **Przedluzanie klipow:** nie znaleziono w oficjalnych zrodlach biezacego mechanizmu "extend" dla 3.0/4.0 — NIEPOTWIERDZONE. Dluzsze sceny: 4.0 do 30 s w jednym przebiegu.

## Zrodla

| ID | URL | Rzad | Data odczytu | Uwagi |
|---|---|---|---|---|
| Z1 | https://kling.ai/dev/pricing | 1 | 2026-11-27 | Cennik API: pakiety (Standard Package 1-3, 180 dni), stawki 4.0 / 4.0 Flash / 3.0 / 3.0 Turbo / 2.6. Odczyt posredni (indeks). |
| Z2 | https://kling.ai/document-api/pricing/base/video (oraz .md; lustro klingai.com) | 1 | 2026-11-27 | Stawki w Units z kwotami USD: 3.x/2.6 przy $0.14/Unit, 4.0 przy $0.157/Unit. |
| Z3 | https://kling.ai/document-api/api/usage-guide/kling-4-0 | 1 | 2026-11-27 | Kling 4.0: 3-30 s, 720p/1080p/4K, HDR, audio wysokiej jakosci stereo, dialogi. |
| Z4 | https://kling.ai/document-api/updates/api | 1 | 2026-11-27 | Changelog: 4.0 Flash 2026-11-04 (3-20 s, 720p); 4K dla 4.0 2026-11-19; komunikat rozliczeniowy 2026-06-17. |
| Z5 | https://kling.ai/document-api/api/video/3-0-omni/text-to-video | 1 | 2026-11-27 | `duration` 3-15, `audio`: `native`/`off` (domyslnie `off`). |
| Z6 | https://kling.ai/document-api/api/video/3-0-omni/video-omni | 1 | 2026-11-27 | Omni: 3-15 s; brak audio natywnego przy wideo wejsciowym. |
| Z7 | https://kling.ai/quickstart/kling-4-model-user-guide | 1 (material dostawcy) | 2026-11-27 | 4.0 Flash: maks. 20 s, 720p. |
| Z10 | https://kling.ai/dev/model-release/kling-4 | 1 | 2026-11-27 | Release note 4.0 (2026-10-28): do 30 s, 720p/1080p; brak wzmianki o audio. |
| Z8 | https://kling.ai/blog/kling-4-vs-3 | 4 (blog dostawcy) | 2026-11-27 | Stereo 4.0 vs mono 3.0 — poszlaka, NIEPOTWIERDZONE, nie uzyte w liczbach. |
| Z9 | https://www.atlascloud.ai/blog/tips/kling-ai-api-pricing ; https://magichour.ai/blog/kling-ai-pricing | 4-5 | 2026-11-27 | Agregatory; NIEPOTWIERDZONE, nie uzyte w liczbach. |

## Niepewnosci i czego nie potwierdzono

1. Bezposredni odczyt stron kling.ai niemozliwy (blokada sieci). Wszystkie liczby z fragmentow indeksu oficjalnych stron.
2. Cena Unit: cennik podaje dwie ceny dla **dwoch roznych rodzin modeli** — $0.14/Unit dla 3.x/2.6/2.5 Turbo oraz $0.157/Unit (pakiety $500/3 250 itd.) dla 4.0 i 4.0 Flash. Nie sa to dwa stany w czasie. Czy dla rodziny 3.x istnieja osobne pakiety z rabatem — NIEPOTWIERDZONE (przyjeto cene cennikowa $0.14).
3. Czy pakiet Trial nadal istnieje — NIEPOTWIERDZONE.
4. Kling 4.0: osobna stawka audio i parametr `audio` w endpoincie 4.0 — NIEPOTWIERDZONE (sama obsluga audio potwierdzona w Z3). Audio Kling 4.0 Flash — NIEPOTWIERDZONE.
5. Cennik nie ma daty; przyjeto date odczytu 2026-11-27 (ostatnia odnotowana zmiana API: 2026-11-19).
