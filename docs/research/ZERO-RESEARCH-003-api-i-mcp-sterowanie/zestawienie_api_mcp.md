# ZERO-RESEARCH-003 — Zestawienie: API, SDK i serwery MCP do sterowania generowaniem wideo z Claude Code

Synteza tematu ZERO-RESEARCH-003-api-i-mcp-sterowanie. Rola: Operator (Opus 5.5), runda 3 z 3 syntezy (naprawa E-2-1: Seedance K7=0 — wymog weryfikacji real-name takze w kanale Volcengine; zmienione sekcje 2 wiersz Dostep, 3.2, 3.3 Seedance, 4, 6, 7 pkt 5, 8). Stan na **2026-11-27**.
Podstawa: piec plikow wezlow (status PASS), czytanych tylko do odczytu, oraz jedno zrodlo rzedu 1 dodane w naprawie E-2-1 (strona Volcengine, odczyt bezposredni Final Control, powtorzony przez Operatora; sekcja 6); zadnych kont, kluczy, instalacji ani wywolan API. Zadnych kluczy i sekretow w tym pliku.

| Plik wezla | Dostawca | Runda PASS | SHA-256 (odczyt przed synteza) |
|---|---|---|---|
| `kling.md` | Kling (Kuaishou) | r4 | `7f0058f7e38511cad68e53d2f349c00cac4f726bc8773c7e27d0e170a69ca670` |
| `seedance.md` | Seedance (ByteDance: BytePlus ModelArk / Volcengine Ark) | r5 | `534edcb5f8c6e10c9ada819300b4ebcf5e6d7623db80255bd5a97ef5d8726239` |
| `veo.md` | Google (Veo 3.1 i Gemini Omni Flash) | r6 | `92c9c7cc878d7ca1523ab5ecf0cb7dedf6453dce0ec8b0f8c3cfb4e3758c9b42` |
| `sora2.md` | OpenAI Sora 2 / Sora 2 Pro | r4 | `23c13e34443a7fb495ac3be545684c6df9aed95dc797be626acbac2f794376b4` |
| `minimax.md` | MiniMax (API Platform) | r5 | `1787b5de619216adeab721b76e7412fe918bfe9a56ad72fe32d8298b2d78bc49` |

Odwolania w tekscie maja postac `<plik wezla> <ID zrodla>` (np. `kling.md Z4`) albo `<plik> sekcja N`.

## 1. Stan dostepnosci na 2026-11-27 (najpierw)

- **Sora 2 — API WYLACZONE 2026-09-24.** Videos API oraz `sora-2`, `sora-2-pro` i snapshoty usuniete z API OpenAI 2026-09-24, bez zastepcy; potwierdzone bezposrednio w kodzie oficjalnych SDK (`openai-python` 3.60.0 i `openai-node` 7.65.0: kazda metoda `videos.*` z dekoratorem deprecated "The Sora API is scheduled to permanently shut down on September 24, 2026") oraz posrednio na stronach deprecations i pomocy OpenAI. Kanal Azure OpenAI / Foundry tez wycofany. Faktycznego stanu endpointu nie sprawdzano wywolaniem (zakaz). Zgodnie z ECHO-024 Sora 2 zostaje w zestawieniu jako **pozycja informacyjna** (`sora2.md` sekcja 0, Z1, Z2, Z5, Z6, Z13).
- **Google Veo w Gemini API — WYLACZONE 2026-10-22.** Strona Veo w Gemini API: "Veo 3.1 Preview ... in the Gemini API was shut down on October 22, 2026. Migrate to Gemini Omni Flash (`gemini-omni-1.2-flash`) or the GA models available through the Gemini Enterprise Agent Platform"; Veo 3.0 i 2.0 wylaczone 2026-06-30; SDK `google-genai`: `generate_videos` tylko w trybie Agent Platform (`veo.md` sekcja 0a, Z2, Z9, Z11).
  - **Sciezka Agent Platform (dawniej Vertex AI), droga A:** Veo 3.1 GA (`veo-3.1-generate-001`, `veo-3.1-fast-generate-001`, wydane 17.11.2025, wycofanie "May 4, 2027 or later"; `veo-3.1-lite-generate-001` Preview), region `us-central1`, `POST .../publishers/google/models/{MODEL_ID}:predictLongRunning` -> `:fetchPredictOperation`; uwierzytelnienie ADC/OAuth projektu Google Cloud z rozliczeniem albo klucz API w trybie express / powiazany z kontem serwisowym. Karta modelu: "Pay-as-you-go: Not supported", "Fixed quota: Supported" — znaczenie dla zwyklego projektu NIEPOTWIERDZONE (`veo.md` N6). Na Agent Platform dostepny tez Gemini Omni (`v1beta1/.../locations/global/interactions`) (`veo.md` Z7, Z10, Z13).
  - **Gemini Developer API, droga B:** dla wideo tylko **Gemini Omni** (`gemini-omni-1.2-flash`, `POST /v1beta/interactions`), wymaga co najmniej Tier 1 (projekt z aktywnym kontem rozliczeniowym; Free: "Not supported") (`veo.md` Z3, Z18, Z19).
  - Wniosek wezla: Veo przez API = tylko droga A; Omni = droga A lub B. Kazda instrukcja lub serwer MCP z `veo-3.1-*-preview` i `GEMINI_API_KEY` jest nieaktualna (`veo.md` N2).
- **Kling, Seedance, MiniMax — aktywne** (Kling 4.0 API od 2026-10-28; Seedance 2.5 "fully available", dokumentacja z 2026-11-27; MiniMax H3 w API v2, CLI 1.0.29 z 2026-11-10) (`kling.md` Z7; `seedance.md` Z1; `minimax.md` sekcja 1).

## 2. Tabela dostawcow

| Pole | Kling | Seedance | Google (Veo 3.1 / Omni) | Sora 2 | MiniMax |
|---|---|---|---|---|---|
| Publiczne API REST dzis | TAK — `https://api-singapore.klingai.com` (Chiny: `api-beijing`), klucz API Bearer | TAK — BytePlus `https://ark.ap-southeast.bytepluses.com/api/v3/contents/generations/tasks`; Volcengine `https://ark.cn-beijing.volces.com/api/v3/...` | TAK — Veo: Agent Platform `:predictLongRunning`; Omni: `generativelanguage.googleapis.com/v1beta/interactions` lub Agent Platform | **NIE** (wylaczone 2026-09-24) | TAK — `https://api.minimax.io` (`/v2/video_generation` H3, `/v1/video_generation` Hailuo) |
| Dostep (onboarding) | konto Kling = konto konsoli; zakup pakietu Units lub saldo; klucz w `kling.ai/dev/api-key`; regulamin API bez weryfikacji firmy, KYC i listy oczekujacych | konto BytePlus, aktywacja modelu przy saldzie/planie/pakiecie >= 30 USD ("If you are verified to use Pay by Credits" — zakres weryfikacji NIEPOTWIERDZONY); Volcengine: >= 200 CNY i obowiazkowa weryfikacja real-name konta przed aktywacja duzego modelu ("开通大模型前必须进行账号实名认证，否则不能开通") | Omni (Gemini API): Tier 1 = projekt z kontem rozliczeniowym; Agent Platform: projekt GCP z rozliczeniem lub tryb express (Preview) | brak (HIST: klucz OpenAI) | klucz pay-as-you-go, saldo; regulamin wymaga "real-name authentication" |
| Zadania asynchroniczne / webhook | TAK / TAK (`GET /tasks?task_ids=`, `options.callback_url`) | TAK / TAK (`GET .../tasks/{id}`, `callback_url`) | TAK / TAK dla Omni w Gemini API (`background: true`, webhooki Preview); Veo na Agent Platform: LRO, webhook NIE | HIST | TAK / TAK (`GET /v2/query/video_generation/{task_id}`, `callback_url` z `challenge`) |
| Limity | brak limitu QPS API; wspolbieznosc wg pakietu (kod 1303); MCP/CLI 5 QPS (P) | Individual: 180 RPM, 3 zadania rownolegle (2.x bez 4K) | Omni Gemini API Tier 1: 8 RPM / 40 RPD; Veo AP: 50/min (karta) | BRAK DANYCH (HIST) | H3: 300 RPM, 30 zadan w toku; Hailuo: 20 RPM |
| Obraz do wideo: start / koniec | TAK / TAK (4.0: `first_frame`, `last_frame`; Flash tylko start) | TAK / TAK (`role: first_frame`/`last_frame`) | TAK / TAK (Veo `image`, `lastFrame`; Omni 2 obrazy, 3-10 s) | HIST: start TAK, koniec NIE | TAK / TAK (H3 `first_frame`/`last_frame`) |
| Obrazy referencyjne postaci | TAK (Elements `/v1/general/advanced-custom-elements` + `/omni-video/kling-4.0`) | TAK (`reference_image` do 30 w 2.5; prawdziwe twarze tylko przez `asset://`) | TAK (Veo: do 3 obrazow `asset`, tylko 8 s; Omni: do 6 obrazow, do 2 postaci) | HIST: Characters API | TAK (H3 `reference_image` do 9; tryb referencji wyklucza klatki) |
| Przedluzanie klipu | 4.0: "Coming soon"; V1.0-V1.6: bylo | TAK (2.5/2.0 `extend`) | TAK (Veo "Extend videos: Supported"; Omni +3..10 s do 30 s) | HIST: TAK | BRAK endpointu |
| Audio / rozdzielczosc / dlugosc | 4.0 Omni `settings.audio`; 720p/1080p/4K; 3-30 s | `generate_audio`; do 4K; 2.5: 4-30 s | Veo `generateAudio`, 720p-4K, 4/6/8 s; Omni 360p-4k, 3-15 s, bez wejsc audio | HIST | H3 `generate_audio`; 480P/768P/2K; 4-15 s |
| Oficjalne SDK | NIE (jest CLI `@klingai/cli-global` = klient MCP i Skill-skrypt `kling.mjs`) | TAK — `arkruntime` (Python), `ark-runtime-go`, `ark-runtime` (Java), Apache-2.0; CLI `arkcli` | TAK — `google-genai` (Python), `@google/genai`, Go, Java; Apache-2.0; CLI `gemini-api` (beta, tylko Omni) | SDK `openai` istnieje, metody wideo deprecated i bez backendu | TAK — `mmx-cli/sdk` (JS/TS); CLI `mmx` (licencja: README MIT, brak pliku LICENSE) |
| Oficjalny serwer MCP | TAK — `io.github.klingai-dev/kling-ai` (zdalny `https://kling.ai/mcp/plugin`, OAuth), repo `klingai-tech/claude-plugin` (MIT, 2026-11-25); rozlicza kredyty aplikacji, nie Units API | NIE (`byteplus-sa/ark-mcp` polooficjalny, bez rejestru i odnosnika w dokumentacji = rzad 4) | NIE do wideo — zdalny MCP Agent Platform bez narzedzi wideo; `mcp-veo-go`/`mcp-omni-go` w repo GoogleCloudPlatform oznaczone "not an officially supported Google product ... demonstration" | NIE (nigdy nie bylo) | TAK — `MiniMax-AI/MiniMax-MCP` (PyPI 0.0.20, 2026-11-10) i `-MCP-JS` (2026-08-21), MIT; wideo tylko modele v1 (bez H3) |
| MCP spolecznosciowy (rzad 4, NIEPOTWIERDZONE co do jakosci) | AceDataCloud KlingMCP (MIT, 2026-11-27), RunAPI kling-mcp (Apache-2.0, 2026-10-22) | atharva3vedi/seedance-mcp (MIT, 2026-10-14), AceDataCloud SeedanceMCP (MIT, 2026-11-27), ark-mcp (MIT, 2026-11-27) i in. | genmedia `mcp-veo-go`/`mcp-omni-go` (Apache-2.0, 2026-11-25, demo), u2n4 omni-mcp-server (MIT, 2026-11-06) i in. | wszystkie z martwym backendem lub wycofane | AceDataCloud MinimaxMCP (MIT, 2026-11-27, H3), RunAPI hailuo-mcp (Apache-2.0, 2026-10-22) |
| Alternatywne drogi (rzad 4-5, NIEPOTWIERDZONE) | AceDataCloud, RunAPI, fal.ai (P) | Volcengine (kanal dostawcy, rzad 1), AceDataCloud, KreatorFlow, useapi.net, fal.ai (P), Replicate (P) | fal.ai, OpenRouter, Vercel AI Gateway (P), AceDataCloud, RunAPI | brak potwierdzonej dzialajacej | fal.ai (P; cennik MiniMax wskazuje fal przy H3-Max), AceDataCloud, RunAPI, useapi.net, RunningHub |
| Minimalna sciezka z Claude Code | (a) oficjalny MCP/plugin; (a') CLI `kling`; (b) HTTP | (b) HTTP/SDK `arkruntime` lub CLI `arkcli`; (a) tylko MCP rzedu 4 | (b) CLI `gemini-api` (Omni) lub HTTP/SDK (Veo na Agent Platform); (a) tylko MCP demo | **(c) BRAK** | (a') CLI/SDK `mmx` (pelne H3); (b) HTTP; (a) oficjalny MCP tylko v1 |
| Pewnosc glownych twierdzen | wysoka (dokumentacja API odczytana bezposrednio) | wysoka (BytePlus i Volcengine bezposrednio) | wysoka (aistudio.google.com, docs.cloud.google.com bezposrednio) | wysoka co do wylaczenia (kod SDK); dokumentacja OpenAI posrednio | wysoka (platform.minimax.io bezposrednio) |

Zrodla wierszy: `kling.md` sekcje 1-8; `seedance.md` sekcje 1-8; `veo.md` sekcje 0a-8; `sora2.md` sekcje 0-8; `minimax.md` sekcje 1-8.

## 3. Jawna punktacja gotowosci do sterowania z Claude Code

### 3.1 Kryteria (max 12 pkt) i reguly przyznawania

| # | Kryterium | Pkt | Regula przyznania (stosowana jednakowo do kazdego dostawcy) |
|---|---|---|---|
| K1 | Publiczne API dla zwyklego konta | 3 | Na 2026-11-27 istnieje REST API wideo dostepne samoobslugowo (konto + klucz/projekt), potwierdzone zrodlem rzedu 1. API wylaczone = 0. |
| K2 | Obraz do wideo z klatka startowa | 2 | Parametr klatki startowej w aktualnie dostepnym API (rzad 1). |
| K3 | Obrazy referencyjne postaci | 2 | Parametr obrazow referencyjnych postaci/obiektow w aktualnie dostepnym API (rzad 1). |
| K4 | Zadania asynchroniczne i webhook | 1 | Oba: zadanie asynchroniczne (id + status) **i** webhook/callback w oficjalnym API (rzad 1). |
| K5 | Oficjalne SDK | 1 | Biblioteka programistyczna (pakiet do importu) wydana przez dostawce, obslugujaca dzialajace endpointy wideo. Samo CLI, Skill lub skrypt nie jest SDK. Metody wideo bez backendu = 0. |
| K6 | Serwer MCP: oficjalny 2 / spolecznosciowy 1 | 2 | **2** — serwer wydany przez dostawce (repozytorium organizacji dostawcy, namespace dostawcy w oficjalnym rejestrze MCP lub opis w dokumentacji dostawcy), nieoznaczony jako demo/"not officially supported", z narzedziem generowania wideo dla modelu dostepnego dzis. **1** — brak takiego, ale istnieje serwer spolecznosciowy (rzad 4) z repozytorium odczytanym bezposrednio, licencja i data ostatniej aktywnosci, kierowany na backend dostepny dzis (jakosc NIEPOTWIERDZONA). **0** — brak obu. |
| K7 | Brak barier onboardingu | 1 | **1** — odczytane zrodla rzedu 1 o dostepie (quick start, aktywacja, regulamin) nie zawieraja wymogu weryfikacji (tozsamosci, firmy, uprawnienia platniczego) ani listy oczekujacych; wymagane sa tylko konto, klucz i platnosc/rozliczenie. Wg zasady wspolnej wystarczy jedna aktualnie dostepna oficjalna droga (kanal dostawcy) spelniajaca ten warunek. **0** — zrodla rzedu 1 kazdej oficjalnej drogi wymieniaja taki wymog (takze gdy jego zakres jest niepotwierdzony) albo dostepu brak. |

Zasady wspolne:
- Ocenia sie dostawce (ekosystem), a nie jeden model: kryterium jest spelnione, jesli spelnia je co najmniej jeden **aktualnie dostepny** model dostawcy przez **oficjalna** droge.
- Twierdzenia oparte wylacznie na zrodlach rzedu 4-5 lub na odczycie posrednim (P) bez potwierdzenia rzedu 1 sa NIEPOTWIERDZONE i nie daja punktow w kryteriach tak/nie (K1-K5, K7). W K6 wartosc 1 pkt opiera sie na bezposrednio odczytanym repozytorium (istnienie, licencja, data), a jakosc serwera pozostaje NIEPOTWIERDZONA.
- Punkty przeliczono samodzielnie z plikow wezlow; propozycje wezlow (sekcje 10) traktowano tylko jako dane wejsciowe.

### 3.2 Punkty

| Kryterium (max) | Kling | Seedance | Google | Sora 2 | MiniMax |
|---|---|---|---|---|---|
| K1 API (3) | 3 | 3 | 3 | 0 | 3 |
| K2 Klatka startowa (2) | 2 | 2 | 2 | 0 | 2 |
| K3 Referencje postaci (2) | 2 | 2 | 2 | 0 | 2 |
| K4 Async + webhook (1) | 1 | 1 | 1 | 0 | 1 |
| K5 Oficjalne SDK (1) | 0 | 1 | 1 | 0 | 1 |
| K6 MCP 2/1 (2) | 2 | 1 | 1 | 0 | 2 |
| K7 Brak barier (1) | 1 | 0 | 1 | 0 | 0 |
| **Suma (12)** | **11** | **10** | **11** | **0** | **11** |

### 3.3 Uzasadnienie kazdej komorki

**Kling (11)**
- K1=3: konsola kluczy na zwyklym koncie, "Your console account is the same as your Kling AI web account"; API Key Bearer dla wszystkich modeli (`kling.md` Z4, Z5; B).
- K2=2: `POST /image-to-video/kling-4.0`, `contents[].type` = `first_frame` (Z3b; B).
- K3=2: Elements `POST /v1/general/advanced-custom-elements` + `POST /omni-video/kling-4.0` z `element`/`refer_image` (Z3d, Z3e; B).
- K4=1: `GET /tasks?task_ids=` + `options.callback_url`, protokol callback (Z3a, Z32; B).
- K5=0: indeks dokumentacji API (76 stron) bez SDK; CLI `@klingai/cli-global` to "thin MCP client", a "Kling AI Skill" to skrypt `kling.mjs` — wg K5 nie sa SDK (Z29, Z21, Z23).
- K6=2: `io.github.klingai-dev/kling-ai` w oficjalnym rejestrze MCP, repo `klingai-tech/claude-plugin` MIT (KLING AI Pte Ltd), commit 2026-11-25; narzedzia `text_to_video`, `image_to_video`, `omni_ref_video` (Z13, Z15, Z16).
- K7=1: pelny regulamin API (Z31; B) bez weryfikacji firmy, KYC i listy oczekujacych; dostep po oplacie pakietu/salda (Z4). Pewnosc srednia (panel rejestracji nieodczytany).

**Seedance (10)**
- K1=3: ModelArk Video Generation API, limity "Individual" (konto indywidualne wywoluje API) (`seedance.md` Z1, Z3, Z8; B).
- K2=2: `image_url` z `role: "first_frame"`, wszystkie modele (Z1; B).
- K3=2: `role: "reference_image"` (2.5: 1-30 obrazow); zastrzezenie: prawdziwe twarze tylko przez `asset://` (Z1, Z9; B).
- K4=1: zadanie asynchroniczne (`id`, `GET .../tasks/{id}`) + `callback_url` (Z1, Z2, Z5; B).
- K5=1: `arkruntime` (PyPI 0.23.0, 2026-11-23), `ark-runtime-go`, `ark-runtime` (Java), Apache-2.0, instalowane w dokumentacji BytePlus (Z4, Z11; B).
- K6=1: oficjalnego brak (rejestr: 0 wynikow `byteplus`; `volcengine/mcp-server` bez Seedance) (Z12, Z13); `byteplus-sa/ark-mcp` bez wpisu w rejestrze i bez odnosnika w dokumentacji = rzad 4 (Z17); spolecznosciowe z repozytorium, licencja i data na backendzie BytePlus: `atharva3vedi/seedance-mcp` (MIT, 2026-10-14) (Z18), AceDataCloud (MIT, 2026-11-27) (Z15).
- K7=0: wymog weryfikacji jest w kazdej oficjalnej drodze. BytePlus (`seedance.md` Z7; B): "If you are verified to use Pay by Credits ...". Volcengine Ark: oficjalna dokumentacja Volcengine (zrodlo V1 w sekcji 6, rzad 1, odczyt bezposredni Final Control, powtorzony przez Operatora 2026-11-27, HTTP 200, SHA-256 `56fbbb334cbab09422d5ae4839e5c61920083bfcceb4b1b1c314eeea528f13a8`), l.47: "注意：开通大模型前必须进行账号实名认证，否则不能开通！！！" (przed aktywacja duzego modelu konto musi przejsc weryfikacje real-name, inaczej aktywacja jest niemozliwa); l.53 i l.57 opisuja te weryfikacje. Strony Z20/Z14 wezla tego wymogu nie wymienialy, ale brak wzmianki nie przeczy wprost odczytanemu wymogowi. Wg reguly K7 (sekcja 3.1: 0, gdy wymog jest w kazdej oficjalnej drodze, takze przy niepotwierdzonym zakresie) i tak samo jak MiniMax (real-name, K7=0) daje 0. Przeliczenie: 3+2+2+1+1+1+0=10.

**Google — Veo 3.1 / Gemini Omni (11)**
- K1=3: Omni przez Gemini API (klucz AI Studio, Tier 1 = projekt z kontem rozliczeniowym) i Veo/Omni przez Agent Platform (projekt z rozliczeniem) (`veo.md` Z3, Z7, Z13, Z18; B). Veo przez Gemini API wylaczone 2026-10-22 — nie wplywa na K1, bo droga A dziala.
- K2=2: Veo 3.1 GA "image to video" (Z10); Omni: obraz startowy (Z3; B).
- K3=2: Veo `referenceImages` z `referenceType: "asset"` (do 3); Omni do 6 obrazow referencyjnych (Z13, Z3; B).
- K4=1: Omni w Gemini API: `background: true` (id interakcji) + webhooki (Preview), zdarzenie `video.generated` (Z3; B). Veo na Agent Platform: LRO bez webhooka — punkt przyznany na podstawie Omni.
- K5=1: `google-genai` (Python 3.6.1), `@google/genai`, Go, Java; Apache-2.0; `generate_videos` (Veo, Agent Platform) i `interactions.create` (Omni) (Z1, Z2, Z4; B).
- K6=1: zdalny MCP Agent Platform jest oficjalny, ale bez narzedzia `predictLongRunning`/Interactions (Z16, Z21); `mcp-veo-go`/`mcp-omni-go` (GoogleCloudPlatform, Apache-2.0, commit 2026-11-25) maja narzedzia Veo/Omni, ale README: "This is not an officially supported Google product ... demonstration purposes only" — wg K6 nie oficjalny, liczy sie jako 1 (repozytorium odczytane bezposrednio, backend Veo GA dziala) (Z5); takze u2n4 omni-mcp-server (MIT, 2026-11-06, Omni przez Gemini API) (Z14).
- K7=1: Tier 1 to podlaczone konto rozliczeniowe; "some projects need verification" dotyczy tylko Free tier, na ktorym Omni i tak nie dziala; brak weryfikacji firmy i listy oczekujacych w odczytanych stronach (Z18, Z19, Z3; B). Ryzyko dla Veo: N6 ("Pay-as-you-go: Not supported") — nie zmienia punktu, bo droga Omni spelnia regule.

**Sora 2 (0) — NIEDOSTEPNE (API wylaczone 2026-09-24)**
- K1-K4=0: brak API na 2026-11-27 (`sora2.md` Z1, Z2, Z5, Z6).
- K5=0: SDK `openai` istnieje, ale `videos.*` deprecated i bez backendu (Z5, Z6; B).
- K6=0: oficjalnego MCP nigdy nie bylo (Z8; B); spolecznosciowe bez dzialajacego backendu lub wycofane (AceDataCloud: "retired") (Z9, Z12*).
- K7=0: brak dostepu.
- Informacyjnie (HIST, przed 2026-09-24, wg wezla): 10/12 — nie uzywane w kolejnosci.

**MiniMax (11)**
- K1=3: klucz pay-as-you-go z API Platform, "Pay-as-you-go supports all modality models, including ... Video" (`minimax.md` D4, D2; B).
- K2=2: H3 `image_url` z rola `first_frame`; Hailuo `first_frame_image` (D2, D3; B).
- K3=2: H3 tryb reference, do 9 `reference_image`; legacy S2V-01 `subject_reference` (D2, D6; B).
- K4=1: `task_id` + `GET /v2/query/video_generation/{task_id}` + `callback_url` z weryfikacja `challenge` (D2, D6; B).
- K5=1: `mmx-cli/sdk` (`MiniMaxSDK`, `sdk.video.generate/getTask/download`) w oficjalnym repo `MiniMax-AI/cli` (Z8; B). Zastrzezenie: licencja tylko w README (brak pliku LICENSE) — licencja nie jest warunkiem K5.
- K6=2: `MiniMax-AI/MiniMax-MCP` i `MiniMax-AI/MiniMax-MCP-JS`, MIT, opisane jako oficjalne na API Platform (D10), narzedzie `generate_video` dla modeli v1 (`MiniMax-Hailuo-02`, dostepny dzis) (Z1, Z2; B). Zastrzezenie: brak H3 w oficjalnym MCP; K6 nie wymaga najnowszego modelu.
- K7=0: regulamin (D11; B): "you must complete real-name authentication" — wymog weryfikacji tozsamosci.

## 4. Kolejnosc (z punktow)

| Miejsce | Dostawca | Punkty | Czym rozni sie od maksimum (12) |
|---|---|---|---|
| 1 (ex aequo) | Google (Veo 3.1 przez Agent Platform / Gemini Omni) | 11 | K6: brak oficjalnego MCP do wideo (tylko demo i spolecznosciowe) |
| 1 (ex aequo) | Kling | 11 | K5: brak oficjalnego SDK |
| 1 (ex aequo) | MiniMax | 11 | K7: wymog weryfikacji real-name |
| 4 | Seedance | 10 | K6: brak oficjalnego MCP (tylko spolecznosciowe); K7: wymog weryfikacji real-name (Volcengine) i "verified to use Pay by Credits" (BytePlus) |
| 5 | Sora 2 — **NIEDOSTEPNE (API wylaczone 2026-09-24)**, pozycja informacyjna (ECHO-024) | 0 | wszystkie kryteria |

**Remisy (jawnie):** Google, Kling i MiniMax maja po 11 pkt. Punktacja zlecenia nie przewiduje rozstrzygacza, wiec remis **nie jest rozstrzygany** — trzy pozycje dziela miejsce 1, kolejnosc w wierszach jest alfabetyczna i nie oznacza przewagi. Google traci punkt w K6 (brak oficjalnego MCP do wideo), Kling w K5 (brak SDK), MiniMax w K7 (real-name). Seedance (10 pkt) jest na miejscu 4 bez remisu: traci punkty w K6 i K7.

**Wrazliwosc (informacyjnie, nie zmienia rankingu):** wezly opisaly warianty zalezne od interpretacji: Seedance 11 (gdyby `ark-mcp` uznac za oficjalny; K7 pozostaje 0, bo wymog real-name Volcengine i weryfikacja BytePlus sa w zrodlach rzedu 1); MiniMax 12 (real-name nie bariera) lub 10 (gdyby MCP musial obslugiwac H3); Google 12 (gdyby demo `mcp-veo-go` uznac za oficjalny); Kling 12 (gdyby CLI/Skill uznac za SDK). Gdyby wymogu real-name nie traktowac jako bariery, MiniMax mialby 12, a Seedance 11 — reguly K7 tego nie dopuszczaja. Reguly K5-K7 w sekcji 3.1 rozstrzygaja te warianty jednoznacznie.

## 5. Minimalne sciezki sterowania z Claude Code (skrot; szczegoly w sekcjach 8 wezlow)

| Dostawca | Najprostsza oficjalna sciezka | Endpointy / narzedzia |
|---|---|---|
| Kling | (a) MCP: `claude mcp add --transport http klingai --scope user https://kling.ai/mcp` lub plugin `klingai-tech/claude-plugin`, OAuth | `who_am_i` -> `file_upload` -> `element_create` -> `image_to_video` / `omni_ref_video` -> `query_tasks` (linki 24 h). (b) HTTP: `POST /image-to-video/kling-4.0`, `POST /omni-video/kling-4.0`, `GET /tasks?task_ids=`. Uwaga: MCP = kredyty aplikacji, HTTP = pakiety Units API |
| Seedance | (b) HTTP/SDK lub CLI `arkcli` | `POST .../api/v3/contents/generations/tasks` -> `GET .../tasks/{id}` -> `content.video_url` (24 h); `DELETE .../tasks/{id}`; SDK `client.content_generation.tasks.create/get` |
| Google | (b) CLI `gemini-api video ... -m gemini-omni-1.2-flash` (Omni) lub HTTP/SDK (Veo na Agent Platform) | Omni: `POST /v1beta/interactions` (`background`, `webhook_config`); Veo: `...veo-3.1-generate-001:predictLongRunning` -> `:fetchPredictOperation` -> GCS |
| Sora 2 | **(c) brak** | — (HIST: `POST /v1/videos`, `GET /v1/videos/{id}/content`) |
| MiniMax | (a') CLI/SDK `mmx` (pelne H3) lub (b) HTTP; (a) oficjalny MCP tylko v1 | `POST /v2/video_generation` -> `GET /v2/query/video_generation/{task_id}` -> `content.url`; MCP: `generate_video` -> `query_video_generation` |

W ramach calego tematu (wezly i synteza) nie wykonano zadnego wywolania API, nie zalozono kont i kluczy, nie zainstalowano serwerow MCP, SDK ani CLI (deklaracje w naglowkach wezlow).

## 6. Lista zrodel (glowne zrodla rzedu 1 uzyte w punktacji; pelne listy w sekcjach 9 wezlow)

Data odczytu wszystkich: 2026-11-27 (przez wezly; V1 — przez Final Control i Operatora syntezy, bo pliki wezlow sa tylko do odczytu). B = odczyt bezposredni, P = posredni.

| Dostawca | ID w wezle | URL | Rzad | Sposob |
|---|---|---|---|---|
| Kling | Z4 | https://kling.ai/document-api/guides/get-started/quick-start.md | 1 | B |
| Kling | Z5 | https://kling.ai/document-api/api/get-started/authentication.md | 1 | B |
| Kling | Z3a / Z3b | https://kling.ai/document-api/api/video/4-0/text-to-video.md ; .../4-0/image-to-video.md | 1 | B |
| Kling | Z3d / Z3e | https://kling.ai/document-api/api/video/4-0/elements.md ; .../4-0/video-omni.md | 1 | B |
| Kling | Z32 | https://kling.ai/document-api/api/get-started/callbacks.md | 1 | B |
| Kling | Z29 | https://kling.ai/document-api/llms.txt | 1 | B |
| Kling | Z31 | https://kling.ai/document-api/guides/protocols/paid-service.md | 1 | B |
| Kling | Z13 | https://registry.modelcontextprotocol.io/v0/servers?search=klingai | 1 (rejestr) | B |
| Kling | Z15 | https://github.com/klingai-tech/claude-plugin | 1 | B |
| Kling | Z21 | https://registry.npmjs.org/@klingai%2Fcli-global | 1 | B |
| Seedance | Z1 | https://docs.byteplus.com/en/docs/modelark/create-video-generation-task-api | 1 | B |
| Seedance | Z2 | https://docs.byteplus.com/en/docs/modelark/get-video-generation-task-api | 1 | B |
| Seedance | Z3 | https://docs.byteplus.com/en/docs/modelark/model-list | 1 | B |
| Seedance | Z4 | https://docs.byteplus.com/en/docs/modelark/quick-start | 1 | B |
| Seedance | Z7 | https://docs.byteplus.com/en/docs/modelark/seedance-model-activation-usage-and-refund | 1 | B |
| Seedance | Z11 | https://pypi.org/pypi/arkruntime/json ; github.com/volcengine/ark-runtime-python, -go, -java | 1 | B |
| Seedance | Z12 | https://registry.modelcontextprotocol.io/v0/servers?search=seedance | 1 (rejestr) | B |
| Seedance | Z13 | https://github.com/volcengine/mcp-server | 1 | B |
| Seedance | Z14 / Z20 | https://docs.volcengine.com/docs/zh/ark/create-video-generation-task-api.md ; .../seedance-model-activation-usage-and-refund.md | 1 | B |
| Seedance | V1 (synteza, naprawa E-2-1; spoza plikow wezlow) | https://docs.volcengine.com/docs/zh/billing-center/declining-savings-plan-instructions.md (l.47 wymog 实名认证 przed aktywacja duzego modelu; odczyt 2026-11-27, HTTP 200, SHA-256 `56fbbb334cbab09422d5ae4839e5c61920083bfcceb4b1b1c314eeea528f13a8`) | 1 | B (Final Control/Evaluator; powtorzony przez Operatora) |
| Google | Z3 | https://aistudio.google.com/docs/omni ; https://aistudio.google.com/docs/webhooks.md | 1 | B |
| Google | Z9 / Z11 | https://aistudio.google.com/docs/veo ; https://aistudio.google.com/docs/deprecations | 1 | B |
| Google | Z7 | https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/video/generate-videos-from-text | 1 | B |
| Google | Z10 | https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/veo/3-1-generate | 1 | B |
| Google | Z13 | https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/video/generate-videos-from-references | 1 | B |
| Google | Z18 / Z19 | https://aistudio.google.com/docs/rate-limits ; https://aistudio.google.com/docs/models/gemini-omni-flash.md | 1 | B |
| Google | Z1 / Z2 / Z4 | https://github.com/googleapis/python-genai ; https://github.com/googleapis/js-genai ; PyPI/npm | 1 | B |
| Google | Z16 / Z21 | https://docs.cloud.google.com/mcp/supported-products ; .../reference/use-agent-platform-mcp | 1 | B |
| Google | Z5 | https://github.com/GoogleCloudPlatform/vertex-ai-creative-studio (status demo) | 1 (istnienie) | B |
| Google | Z20 | https://aistudio.google.com/docs/cli.md ; https://github.com/google-gemini/gemini-api-cli | 1 | B |
| Sora 2 | Z5 / Z6 | https://github.com/openai/openai-python ; https://github.com/openai/openai-node | 1 | B |
| Sora 2 | Z1 / Z2 | https://developers.openai.com/api/docs/deprecations ; https://help.openai.com/en/articles/20001152-what-to-know-about-the-sora-discontinuation | 1 | P |
| Sora 2 | Z8 | https://registry.modelcontextprotocol.io/v0/servers?search=sora | 1 (rejestr) | B |
| Sora 2 | Z13 | https://learn.microsoft.com/en-us/azure/foundry/openai/concepts/retired-models | 1 (Azure) | P |
| MiniMax | D2 | https://platform.minimax.io/docs/api-reference/video-generation-v2-create.md | 1 | B |
| MiniMax | D4 | https://platform.minimax.io/docs/guides/quickstart-preparation.md | 1 | B |
| MiniMax | D6 | https://platform.minimax.io/docs/api-reference/video-generation-v2-query.md | 1 | B |
| MiniMax | D8 | https://platform.minimax.io/docs/guides/rate-limits.md | 1 | B |
| MiniMax | D10 | https://platform.minimax.io/docs/guides/mcp-guide.md | 1 | B |
| MiniMax | D11 | https://platform.minimax.io/protocol/terms-of-service | 1 | B |
| MiniMax | Z1 / Z2 | https://github.com/MiniMax-AI/MiniMax-MCP ; https://github.com/MiniMax-AI/MiniMax-MCP-JS | 1 | B |
| MiniMax | Z4 / Z8 | https://github.com/MiniMax-AI/cli (README, SDK.md) | 1 | B |

Zrodla rzedu 4-5 (serwery spolecznosciowe, posrednicy, fal.ai, Replicate, OpenRouter, Vercel, forum) — wylacznie w sekcjach 6-7 i 9 wezlow; wszystkie NIEPOTWIERDZONE (sekcja 7 ponizej).

## 7. Uwagi o niepewnosci

1. **Zrodla rzedu 4-5 = NIEPOTWIERDZONE.** Dotyczy wszystkich serwerow MCP spolecznosciowych i posrednikow (AceDataCloud, RunAPI, KreatorFlow, useapi.net, `byteplus-sa/ark-mcp` i `seed-mcp`, u2n4, aimuzov, houtini, Doriandarko i in.), platform posredniczacych (fal.ai, Replicate, OpenRouter, Vercel AI Gateway, kie.ai, RunningHub/MachGen/Nunchux jako wlasne API) i forum `discuss.ai.google.dev`. Nie licza sie do punktow tak/nie (K1-K5, K7); w K6 daja najwyzej 1 pkt i tylko przy bezposrednio odczytanym repozytorium z licencja i data. Jakosci i dzialania nie sprawdzano (nie instalowano).
2. **Odczyt posredni (P) bez potwierdzenia rzedu 1 B:** Kling — 5 QPS i 1 zadanie wideo bez subskrypcji w MCP/CLI, liczba 20 zadan rownoleglych w cenniku; Sora 2 — strony dokumentacji OpenAI i Microsoft (wylaczenie potwierdzone jednak bezposrednio w kodzie SDK); fal.ai i Replicate dla wszystkich dostawcow.
3. **Sora 2:** faktycznego stanu `https://api.openai.com/v1/videos` nie sprawdzano wywolaniem (zakaz); data 2026-09-24 pochodzi ze zrodel rzedu 1. Daty wycofania w Azure rozbiezne (2026-10-15 vs 2026-11-02), obie przed 2026-11-27.
4. **Google:** (a) Veo na Agent Platform: "Pay-as-you-go: Not supported", "Fixed quota: Supported" — czy zwykly projekt z rozliczeniem korzysta bez dodatkowej umowy, NIEPOTWIERDZONE (`veo.md` N6); (b) 4K dla `veo-3.1-generate-001` — sprzecznosc karty modelu i strony parametrow (N7); (c) webhooki Gemini API maja status Preview; webhook dla Omni na Agent Platform NIEPOTWIERDZONY; (d) czy Veo/Omni sa w darmowym trybie express — NIEPOTWIERDZONE; (e) ograniczenia EOG (Polska): Veo `personGeneration` tylko `allow_adult`; Omni bez edycji/przedluzania wgranych wideo i bez obrazow z nieletnimi.
5. **Seedance:** wymog weryfikacji real-name konta Volcengine przed aktywacja duzego modelu POTWIERDZONY (V1, rzad 1, B) — stad K7=0; zakres weryfikacji "Pay by Credits" (BytePlus), forma i czas weryfikacji real-name Volcengine dla osoby spoza Chin oraz ograniczenia rejestracji BytePlus/Volcengine wg kraju (w tym Polska) — NIEPOTWIERDZONE; status `byteplus-sa/*` (autor z domeny bytedance.com, bez rejestru i odnosnika w dokumentacji) nierozstrzygniety, liczony jako rzad 4; referencje z prawdziwymi twarzami tylko przez zasoby `asset://`.
6. **Kling:** oficjalny MCP rozlicza kredyty aplikacji, API — pakiety Units (dwa rozne rozliczenia); Skill API (`clawhub.ai`) — repozytorium, licencja i aktywnosc NIEPOTWIERDZONE; brak dowodu pozytywnego lub negatywnego o rejestracji z Polski; przedluzanie klipu dla 4.0 "Coming soon".
7. **MiniMax:** moment i forma weryfikacji real-name nieznane bez konta; oficjalny MCP obsluguje tylko modele v1 (bez H3); licencja `mmx-cli` niejednoznaczna (README MIT, brak pliku LICENSE, puste pole w npm); czas waznosci `content.url` niepodany; brak endpointu przedluzania.
8. **Limity** dostawcy zastrzegaja jako teoretyczne lub zmienne w szczycie (Seedance, MiniMax); wartosci efektywne Veo/Omni na Agent Platform widoczne dopiero w konsoli projektu.

## 8. OPINIA (opinia Operatora, wylacznie z danych powyzej; nie jest decyzja)

- OPINIA: Trzech dostawcow (Google, Kling, MiniMax) ma po 11/12 pkt, Seedance 10/12; roznice dotycza innych kryteriow, wiec wybor narzedzia (D2) nie wynika z samej punktacji.
- OPINIA: Kling jako jedyny ma oficjalny, zdalny MCP z OAuth opisany dla Claude Code; przy nim rozliczenie MCP (kredyty aplikacji) jest inne niz API (Units).
- OPINIA: MiniMax ma pelne H3 tylko przez oficjalne CLI/SDK i HTTP; oficjalny MCP obejmuje modele v1.
- OPINIA: Dla Google realna droga to Omni (Gemini API, Tier 1) albo Veo GA na Agent Platform; materialy z `veo-3.1-*-preview` sa nieaktualne.
- OPINIA: Seedance (10/12) ma pelne oficjalne API i SDK, ale oba kanaly wymagaja weryfikacji konta (BytePlus, Volcengine real-name), a referencje z prawdziwymi twarzami wymagaja zasobow `asset://`.
- OPINIA: Sora 2 nie nadaje sie do uzycia (API wylaczone 2026-09-24).
- OPINIA: Niepewnosci K6/K7 (sekcja 4, wrazliwosc) warto zweryfikowac w tescie na jednym klipie (zadanie 16), nie w tym badaniu.
