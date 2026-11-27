# ZERO-RESEARCH-003-c — Google (Veo 3.1 i Gemini Omni Flash): API, SDK, MCP i sterowanie z Claude Code

Wezel: c (Google: Veo i Gemini Omni; Vertex AI = Gemini Enterprise Agent Platform oraz Gemini API). **Runda 6 z 6 (ECHO-026, ostatnia)** — poprawka zarzutu E-5-1: legenda rzedow zrodel (sekcja 0b) i oznaczenie NIEPOTWIERDZONE wszystkich twierdzen opartych na zrodlach rzedu 4-5 (sekcje 6, 7, 8, 9); pozostala tresc bez zmian wzgledem rundy 5. Historia: runda 3 z 3 (poprawka INFRA-EV-2), runda 4 z 4 (ECHO-019, odczyt nieudany), runda 5 z 5 (ECHO-025, ponowny odczyt BEZPOSREDNI dokumentacji Gemini API `aistudio.google.com` i Agent Platform `docs.cloud.google.com`). Rola: Operator (Opus 5.5). Data odczytu wszystkich zrodel: 2026-11-27.
Zakres: wylacznie odczyt dokumentacji, repozytoriow i rejestrow. NIE zalozono kont ani kluczy, NIE zainstalowano serwerow MCP, SDK ani CLI (w tym `gemini-api`), NIE wykonano zadnego wywolania API Google ani platform posredniczacych, NIE uruchomiono kodu z repozytoriow. Zadnych kluczy i sekretow w tym pliku (nazwy zmiennych srodowiskowych podane bez wartosci).

## 0. Dostep do zrodel (czytac najpierw)

- **Runda 5 (ECHO-025), 2026-11-27 — odczyt bezposredni UDANY** przez `curl` (GET, proxy sesji):
  - `aistudio.google.com`: `/docs/veo`, `/docs/omni`, `/docs/webhooks(.md)`, `/docs/rate-limits`, `/docs/deprecations`, `/docs/cli.md`, `/docs/coding-agents.md`, `/docs/models/gemini-omni-flash.md`, `/docs/api-key.md`, `/docs/libraries.md`, `/docs/video.md`, `/llms.txt` — wszystkie HTTP 200 (strony serwowane jako Markdown).
  - `docs.cloud.google.com`: `/gemini-enterprise-agent-platform/models/veo/3-1-generate` (ostatnia aktualizacja strony 2026-11-24), `/models/video/generate-videos-from-references` (2026-11-24), `/models/video/generate-videos-from-text` (2026-11-24), `/models/video/overview` (2026-11-20), `/models/quotas` (2026-11-20), `/models/start/express-mode/overview`, `/reference/mcp` (2026-07-30), `/reference/use-agent-platform-mcp` (2026-11-20), `/mcp/supported-products` — HTTP 200 (stare adresy `vertex-ai/...` przekierowuja 301 na `gemini-enterprise-agent-platform/...`).
  - Repozytoria GitHub: `git clone --depth 1 --filter=blob:none --no-checkout` (odczyt `git show HEAD:<plik>`, nic nie uruchamiano).
- **Skutek:** pola oznaczone w rundach 1-4 jako "posr." (Z3, Z7-Z13, Z16) sa teraz **bezposrednie (rzad 1)**; pewnosc podniesiona. Kilka twierdzen z rund 1-4 **skorygowano** na podstawie odczytu (lista: sekcja "Zmiany w rundzie 5").
- **Nadal posrednie:** platformy posredniczace `fal.ai`, `openrouter.ai`, `vercel.com` (hosty spoza listy ECHO-025; nie ponawiano) — Z15, rzad 5, **NIEPOTWIERDZONE** (sekcja 0b). Rejestr `registry.modelcontextprotocol.io` nie jest na liscie ECHO-025, wiec w rundzie 5 go nie odpytywano; wpisy rejestru pochodza z odczytu bezposredniego w rundach 3-4 (2026-11-27).

### Zmiany w rundzie 5 (wzgledem rundy 4)

| # | Bylo (runda 4) | Jest (runda 5, odczyt bezposr.) | Zrodlo |
|---|---|---|---|
| R5-1 | Limity Omni w Gemini API: NIEPOTWIERDZONE | Tier 1: 8 RPM / 40 RPD; Tier 2: 16 / 200; Tier 3: 40 / 2000; **Free: "Not supported"** | Z18 |
| R5-2 | Omni wymaga Tier 1 — NIEPOTWIERDZONE (rzad 4) | **POTWIERDZONE**: Free tier "Not supported" (limity) i "Not available" (cennik); Tier 1 = podlaczone konto rozliczeniowe | Z18, Z19 |
| R5-3 | Data wycofania Veo 3.1 sprzeczna (17.11.2026 vs 4.05.2027) | `veo-3.1-generate-001` i `-fast-generate-001`: GA, wydane 17.11.2025, wycofanie "May 4, 2027 or later" | Z10 |
| R5-4 | Referencje audio Omni "po allowliscie" (RESEARCH-002) | Strona Omni 1.2: "Uploading audio inputs or audio references is unsupported in the current version of the API" | Z3 |
| R5-5 | Omni: do 10 obrazow referencyjnych (repo MCP) | Dokumentacja Omni 1.2: **do 6 obrazow referencyjnych** (do 3 na postac, do 2 postaci); do 3 wideo referencyjnych (3-10 s) lub 1 (11-15 s) | Z3, Z13 |
| R5-6 | Omni: brak seed (wg narzedzia MCP) | Agent Platform: `generation_config.seed` dla `gemini-omni-1.2-flash` | Z13 |
| R5-7 | Brak dedykowanego CLI | **Jest oficjalne CLI `gemini-api`** (google-gemini/gemini-api-cli, Apache-2.0, beta), polecenie `video` (Omni, tylko Gemini API) | Z20 |
| R5-8 | Zdalny MCP Google Cloud dla wideo — NIEPOTWIERDZONE | Zdalny MCP Agent Platform istnieje (`https://aiplatform.googleapis.com/mcp/...`), ale zestawy narzedzi nie maja narzedzia do wideo/`predictLongRunning` | Z16, Z21 |
| R5-9 | Webhook Gemini API (posr.) | Bezposr.: webhooki (Preview) dla Batch, Interactions i generowania wideo; statyczne i dynamiczne; zdarzenia `interaction.completed`, `interaction.failed`, `interaction.cancelled`, `interaction.requires_action`, `video.generated` | Z3 |
| R5-10 | Przedluzanie Veo: wejscie 1-30 s, +7 s (repo MCP) | Gemini API (historycznie, dla wylaczonych preview): +7 s, do 20 razy, wejscie do 141 s, 720p, wynik do 148 s. Agent Platform: "Extend videos: Supported" (karta modelu) | Z9, Z10 |

## 0b. Legenda rzedow zrodel i oznaczen (runda 6, E-5-1)

| Rzad | Zrodlo | Oznaczenie twierdzenia w tym pliku |
|---|---|---|
| 1 | dokumentacja API dostawcy (aistudio.google.com, docs.cloud.google.com), oficjalne repozytoria Google (github.com/googleapis, google-gemini, GoogleCloudPlatform), rejestry pakietow (PyPI, npm) i rejestr MCP | pewnosc wysoka/srednia wg tabeli; bez dopisku |
| 2 | oficjalne komunikaty dostawcy (blog, changelog) | nie uzyto w tym wezle |
| 3 | testy i artykuly niezalezne | nie uzyto w tym wezle |
| 4 | repozytoria spolecznosciowe (serwery MCP osob trzecich), forum (discuss.ai.google.dev) | **NIEPOTWIERDZONE** (istnienie, licencja i data z repozytorium; jakosc i dzialanie niepotwierdzone) |
| 5 | platformy posredniczace (fal.ai, OpenRouter, Vercel AI Gateway, AceDataCloud, RunAPI, kie.ai) oraz odczyt posredni z indeksu wyszukiwarki (rundy 1-3) | **NIEPOTWIERDZONE** (bez wzgledu na sposob odczytu) |

Zasada: kazde twierdzenie oparte wylacznie na zrodle rzedu 4 lub 5 ma w tym pliku dopisek NIEPOTWIERDZONE; takie twierdzenia nie wplywaja na odpowiedzi tak/nie w sekcjach 1-5 i 8(b) (te opieraja sie na rzedzie 1).

## 0a. Dwie drogi API Google (kluczowe rozroznienie)

| Droga | Co obsluguje dla wideo (stan 2026-11-27) | Uwierzytelnianie | Zrodlo |
|---|---|---|---|
| **A. Gemini Enterprise Agent Platform (dawniej Vertex AI)**, `aiplatform.googleapis.com` | **Veo**: `veo-3.1-generate-001`, `veo-3.1-fast-generate-001` (GA), `veo-3.1-lite-generate-001` (Preview), region `us-central1`, przez `:predictLongRunning`. **Gemini Omni** (`gemini-omni-1.2-flash`) przez Interactions API `v1beta1/projects/{P}/locations/global/interactions` | dane uwierzytelniajace Google Cloud (ADC/OAuth) + projekt; albo klucz API (tryb express lub klucz powiazany z kontem serwisowym) | Z10, Z13, Z8, Z21 |
| **B. Gemini Developer API**, `generativelanguage.googleapis.com` | **tylko Gemini Omni** (`POST /v1beta/interactions`). Veo 3.1 preview (`veo-3.1-generate-preview`, `-fast-`, `-lite-`) **wylaczone 2026-10-22**; Veo 3.0 i 2.0 wylaczone 2026-06-30; zalecany zamiennik: `gemini-omni-1.2-flash` albo modele GA na Agent Platform | klucz API z Google AI Studio (`x-goog-api-key` / `GEMINI_API_KEY`) | Z11, Z3, Z9 |

Dowody bezposrednie: strona Veo w Gemini API ma ostrzezenie "Veo 3.1 Preview ... in the Gemini API was shut down on October 22, 2026. Migrate to Gemini Omni Flash (`gemini-omni-1.2-flash`) or the GA models available through the Gemini Enterprise Agent Platform" (Z9); tabela wycofan (Z11); kod SDK Python: `generate_videos` rzuca `'This method is only supported in Gemini Enterprise Agent Platform mode, not in Gemini Developer API mode.'` (Z2). Wniosek: **Veo przez API = tylko droga A; Omni = droga A lub B.**

## 1. Publiczne API (REST) — dostepnosc dla zwyklego konta

| Pytanie | Odpowiedz | Zrodlo | Pewnosc |
|---|---|---|---|
| Czy istnieje publiczne API REST | **TAK** — Veo: `POST https://us-central1-aiplatform.googleapis.com/v1/projects/{PROJECT_ID}/locations/us-central1/publishers/google/models/{MODEL_ID}:predictLongRunning`; Omni: `POST https://generativelanguage.googleapis.com/v1beta/interactions` (Gemini API) lub `POST https://aiplatform.googleapis.com/v1beta1/projects/{PROJECT_ID}/locations/global/interactions` (Agent Platform) | Z7, Z13, Z3, Z2 | **wysoka** (bezposr., dokumentacja + kod SDK) |
| Dostep — droga A (Veo, Omni) | projekt Google Cloud z wlaczonym rozliczeniem i API Agent Platform; albo **tryb express** (Preview): konto @gmail.com, klucz API, dla nowych uzytkownikow 90 dni darmowego poziomu w limitach bez danych rozliczeniowych; po wlaczeniu rozliczenia przejscie na plan platny. Karta modelu Veo 3.1: "Pay-as-you-go: Not supported", "Fixed quota: Supported", "Provisioned Throughput: Supported" (oznaczenia z karty; znaczenie dla zwyklego projektu — patrz N6). Czy Veo/Omni sa w darmowym trybie express — **NIEPOTWIERDZONE** (nie odczytano listy modeli express) | Z1a, Z8, Z10 | wysoka / srednia (express dla wideo) |
| Dostep — droga B (Omni) | klucz API z Google AI Studio; **Omni wymaga co najmniej Tier 1** = projekt z podlaczonym aktywnym kontem rozliczeniowym (Free tier: "Not supported"); limit wydatkow Tier 1: 10 USD / 10 min, limit rozliczeniowy 250 USD; Tier 2 po 100 USD + 3 dniach | Z18, Z19 | **wysoka** (bezposr.) |
| Ograniczenia regionalne | **Veo (Gemini API, sekcja Limitations):** "In EU, UK, CH, MENA locations, `allow_adult` is the only allowed value for `personGeneration`". **Veo (Agent Platform):** `personGeneration` = `allow_adult` (domyslnie) lub `disallow`; model dostepny w `us-central1`. **Omni:** edycja i przedluzanie WGRANYCH wideo niedostepne w EOG, Szwajcarii i UK (wideo wygenerowane przez model — dozwolone); wgrywanie obrazow z nieletnimi niedostepne w EOG/CH/UK; endpoint Agent Platform tylko `global`. Polska = EOG | Z9, Z7, Z10, Z3, Z13 | **wysoka** |
| Weryfikacja firmy / lista oczekujacych | Brak w odczytanych zrodlach dla Veo/Omni. Free tier Gemini API: "some projects need verification" (dotyczy Free, a Omni i tak nie dziala na Free). Referencje audio Omni: niedostepne w API (R5-4) — nie lista oczekujacych | Z18, Z3 | wysoka |
| Stan na 2026-11-27 | Aktywne: Veo 3.1 GA na Agent Platform (wycofanie "May 4, 2027 or later"); `gemini-omni-1.2-flash` wydany 5.11.2026, bez daty wylaczenia; `gemini-omni-1.1-flash` od 3.12.2026 automatycznie przekierowany na 1.2; SDK 3.6.1 (2026-11-18); CLI `gemini-api` v0.5.0 (commit 2026-11-26) | Z10, Z11, Z19, Z4, Z20 | **wysoka** |

## 2. Model pracy (asynchronicznosc)

**Veo (droga A):**
- **Zadanie asynchroniczne: TAK.** `POST ...:predictLongRunning` zwraca operacje; status: `POST ...publishers/google/models/{MODEL_ID}:fetchPredictOperation` z `{"operationName": ...}` (dokumentacja Agent Platform, bezposr.; kod SDK: `'{model}:predictLongRunning'`, `'{resourceName}:fetchPredictOperation'`). Z7, Z2.
- **Pobranie wyniku:** z parametrem `storageUri` wynik w Cloud Storage; bez niego bajty w odpowiedzi; w SDK `operation.response.generated_videos[0].video`. Z7, Z1.
- **Powiadomienia:** pole SDK `pubsub_topic` jest przekazywane do Agent Platform (bezposr. Z2), ale w odczytanych stronach dokumentacji uslugi (generate-videos-from-text, references) **nie wystepuje** -> dzialanie **NIEPOTWIERDZONE**. Webhook dla Veo na Agent Platform: **NIE** (SDK: `'webhook_config parameter is only supported in Gemini Developer API mode'`). Z2, Z7.

**Gemini Omni (Interactions API):**
- **Gemini API (B):** tryby synchroniczny i `background: true` (zwraca id interakcji, wynik pozniej); `delivery: "uri"` dla wideo > 4 MB — URI hostowany przez Google, odpytywany do stanu `ACTIVE`; w REST wynik w `steps[].content[]` (`interaction.output_video` tylko w SDK). Z3.
- **Agent Platform (A):** tryby "Synchronous: stateless" (`store: false`), "stateful" (`store: true`), "stateful streaming", "Asynchronous" (`background: true`, odbior po id interakcji przez `GET .../locations/global/interactions/{INTERACTION_ID}`); interakcje przechowywane do 7 dni; `delivery: "uri"` wymaga `gcs_uri`. Z13.
- **Webhook: TAK w Gemini API** (funkcja Preview): webhooki statyczne (na projekt, WebhookService API, sekret podpisu HMAC) i dynamiczne (w konkretnym zadaniu, podpis JWKS); obejmuja Batch, Interactions i generowanie wideo; zdarzenia m.in. `interaction.completed`, `interaction.failed`, `interaction.cancelled`, `video.generated`. Na Agent Platform webhook dla Omni — **NIEPOTWIERDZONE** (nie znaleziono w odczytanych stronach). Z3.

## 3. Limity

| Limit | Wartosc | Zrodlo | Pewnosc |
|---|---|---|---|
| Veo 3.1 (Agent Platform) — zapytania/min | karta modelu: "Regional online prediction requests per base model per minute per base model: 50" (jednostka na stronie opisana jako "tokens per minute" — blad redakcyjny strony); metryka kwoty w konsoli: `long_running_online_prediction_requests_per_base_model` (edytowalna przez "Edit quota") | Z10, Z22 | **wysoka** (bezposr.; wartosc efektywna widoczna w konsoli projektu) |
| Omni (Agent Platform) — zapytania/min | metryka `global_generate_content_requests_per_minute_per_project_per_base_model` (wartosc w konsoli; nie podana na stronie) | Z22 | wysoka co do metryki; wartosc: brak |
| Omni (Gemini API) — RPM/RPD | Free: nieobslugiwane; Tier 1: 8 RPM / 40 RPD; Tier 2: 16 / 200; Tier 3: 40 / 2000; limity per projekt, nie per klucz; RPD zeruje sie o polnocy czasu pacyficznego; dodatkowo limity wydatkow (Tier 1: 10 USD / 10 min) | Z18 | **wysoka** |
| Zadania rownolegle | Veo: osobnego limitu wspolbieznosci **nie znaleziono**. Agent Platform, interakcje odroczone (deferred): "Concurrent interaction generations: Up to 500, depending on your project's quota tier" — tabela dotyczy trybu deferred, czy obejmuje Omni — **NIEPOTWIERDZONE** | Z22 | niska (dla Omni) |
| Filmy na zadanie | Veo: `sampleCount` 1-4 (karta: "Maximum number of output videos per prompt: 4"); Omni: brak pola w dokumentacji Gemini API | Z7, Z10 | wysoka |
| Czas generacji | Veo w Gemini API (dot. wylaczonych preview): min. 11 s, maks. 6 min; Omni: "Video generation can take over a minute" (Agent Platform) | Z9, Z13 | srednia |
| Przechowywanie wyniku | Veo w Gemini API: 2 dni (historycznie); Omni na Agent Platform: interakcje do 7 dni | Z9, Z13 | wysoka |

## 4. Zakres API wzgledem aplikacji

| Funkcja | Veo 3.1 (Agent Platform, `-generate-001` / `-fast-generate-001`) | Gemini Omni 1.2 Flash (Interactions API) | Zrodlo |
|---|---|---|---|
| Tekst do wideo | TAK | TAK (`task=text_to_video` lub wnioskowane z promptu) | Z10, Z3 |
| Obraz do wideo, klatka startowa | TAK (karta: "image to video"; maks. obraz 20 MB) | TAK (jeden obraz; do 15 s) | Z10, Z3 |
| Klatka koncowa | TAK ("from first and last frame"; `lastFrame` w konfiguracji) | TAK (dwa obrazy = pierwsza i ostatnia klatka; tylko 3-10 s) | Z10, Z9, Z3 |
| Przedluzanie klipu | TAK ("Extend videos: Supported"; Lite tez). W Gemini API (historycznie) +7 s, do 20 razy, do 148 s | TAK — `task=extend` / `previous_interaction_id`: +3..10 s na ture, do 30 s lacznie, tylko na koncu klipu; przedluzanie WGRANYCH wideo niedostepne w EOG/CH/UK | Z10, Z9, Z3 |
| Obrazy referencyjne postaci/obiektow | TAK — "Use reference images: Asset images" (do 3 obrazow jednej osoby/postaci/produktu, `referenceType: "asset"`); tylko `veo-3.1-generate-001` i `-fast-generate-001`; z referencjami tylko 8 s; Lite: "Not supported". Typ `STYLE` istnieje w enumie SDK (opis pola: "Veo 2 supports ... 1 style image"); w dokumentacji Veo 3.1 tylko `asset` | TAK — do **6 obrazow** (do 3 na postac, do 2 postaci) + do 3 wideo referencyjnych (3-10 s) lub 1 (11-15 s); obrazy referencyjne dzialaja tez przy edycji i przedluzaniu | Z10, Z13, Z2, Z3 |
| Parametry audio | `generateAudio` / `generate_audio` (karta: "Sound generation: Supported") | audio natywnie w wyniku; **wgrywanie audio i referencji audio nieobslugiwane** w obecnej wersji API; edycja glosu nieobslugiwana | Z10, Z2, Z3 |
| Rozdzielczosc | wyjscie 720p, 1080p, 4K (`-generate-001`), 720p/1080p (Fast, Lite); uwaga: strona generate-videos-from-text pisze "4k (Veo 3.1 Preview models only)" — sprzecznosc z karta modelu, **NIEPOTWIERDZONE** dla 4K na GA | `resolution` 360p, 720p (domyslnie), 1080p i 4k (oba skalowane w gore), 24 FPS | Z10, Z7, Z3 |
| Dlugosc | 4, 6 lub 8 s (domyslnie 8) | 3-15 s (domyslnie 10 s); 3-10 s dla pierwszej+ostatniej klatki | Z10, Z7, Z3 |
| Seed | TAK (`seed`, uint32 0-4294967295) | TAK na Agent Platform (`generation_config.seed`); w Gemini API pola seed nie znaleziono | Z7, Z13 |
| Inne | `negativePrompt`, `aspectRatio` 16:9/9:16, `personGeneration`, `sampleCount` 1-4, `storageUri`, C2PA; jezyk promptu: angielski | edycja wideo (`edit`, wieloturowa przez `previous_interaction_id`), proporcje 16:9/9:16; nieobslugiwane: system instructions, temperature, top_p, negative prompts; angielski w pelni, inne jezyki nieocenione | Z10, Z7, Z3 |

## 5. Oficjalne SDK / CLI

| SDK / CLI | Repozytorium | Jezyk | Wersja / ostatnia aktywnosc | Licencja | Wideo |
|---|---|---|---|---|---|
| Google Gen AI SDK (`google-genai`) | https://github.com/googleapis/python-genai | Python | PyPI 3.6.1 (2026-11-18); commit 36e2970 2026-11-24 | Apache-2.0 | `client.models.generate_videos` (Veo, tylko Agent Platform), `client.operations.get`; `client.interactions.create` (Omni) |
| `@google/genai` | https://github.com/googleapis/js-genai | TypeScript/JS | npm 3.6.1 (2026-11-18); commit 3445a09 2026-11-24 | Apache-2.0 | `ai.models.generateVideos`; `ai.interactions.create` |
| `google.golang.org/genai` | https://github.com/googleapis/go-genai | Go | commit 14c5840 2026-11-24 | Apache-2.0 | `Models.GenerateVideos`; pakiet `interactions` |
| `google-genai` (Java) | https://github.com/googleapis/java-genai | Java | commit f0114a7 2026-11-25 | Apache-2.0 | przyklady Omni w Javie na stronie Omni (`com.google.genai.gaos.models.interactions`) |
| `Google.GenAI` (.NET) | https://googleapis.github.io/dotnet-genai/ (wg strony Libraries) | C# | nie odczytano repo | — | — |
| **Gemini API CLI `gemini-api`** | https://github.com/google-gemini/gemini-api-cli | Go (binarka) | tag v0.5.0; commit 3dcbb6e 2026-11-26; "open-source beta ... Breaking changes can occur between minor versions" | Apache-2.0 | `gemini-api video "<prompt>" -m gemini-omni-1.2-flash --resolution 1080p --out plik.mp4`; `--async` zwraca id, `--resume <id>`; `-i` animuje obraz. **Tylko Gemini API** (w kodzie wylacznie host `generativelanguage.googleapis.com`) -> Omni, nie Veo |
| Umiejetnosci (skills) dla agentow | https://github.com/google-gemini/gemini-skills (`gemini-api-cli`, `gemini-api-dev`, `gemini-omni-flash-api`) | Markdown + skrypty Python | commit c4d0c62 2026-11-18 | Apache-2.0 | `gemini-omni-flash-api`: t2v, pierwsza/ostatnia klatka, R2V do 6 obrazow, przedluzanie, edycja przez `google-genai` |

Zrodla: Z1, Z1a, Z2, Z4, Z19 (strona Libraries: SDK dla Python, JavaScript/TypeScript, Go, Java, C#), Z20. `gcloud` sluzy do uwierzytelnienia dla drogi A.

## 6. Serwery MCP

| Serwer | Typ / rzad | Repozytorium / rejestr | Licencja | Ostatnia aktywnosc | Narzedzia | Uwagi |
|---|---|---|---|---|---|---|
| **Zdalny serwer MCP Gemini Enterprise Agent Platform** | oficjalny produkt Google Cloud, rzad 1 | dokumentacja: `docs.cloud.google.com/gemini-enterprise-agent-platform/reference/mcp` i `.../reference/use-agent-platform-mcp`; lista "Supported products" | — (usluga) | strona "Use" zaktualizowana 2026-11-20 | zestawy: `/mcp/generate` (`generate_content`, `count_tokens`, `embed_content`), `/mcp/predict` (`predict`, `raw_predict`), `/mcp/notebook`, `/mcp/endpoints`, `/mcp/models`, `/mcp/tuning`, `/mcp/retrieval`, `/mcp/evaluation`, `/mcp/prompts` | transport Streamable HTTP, OAuth 2.0 + IAM lub klucz API (express albo powiazany z kontem serwisowym); dokumentacja wymienia Claude jako klienta. **Brak narzedzia dla `predictLongRunning` i Interactions API** -> do generowania Veo/Omni **nie nadaje sie wg listy narzedzi** (wniosek z listy; czy `generate_content` obsluguje Omni — NIEPOTWIERDZONE) |
| **Gemini Docs MCP** (`gemini-api-docs-mcp.dev`) | oficjalny (dokumentacja Gemini API), rzad 1 co do istnienia | strona Coding agent setup | — | — | `gemini_search_docs`, `gemini_get_doc` | tylko wyszukiwanie dokumentacji ("Supported in Claude Code ..."); **nie generuje wideo** |
| **MCP Servers for Google Cloud Genmedia** — `mcp-veo-go`, `mcp-omni-go` | organizacja Google (`GoogleCloudPlatform`), rzad 1 co do istnienia; **status: demo** — README: "This is not an officially supported Google product ... intended for demonstration purposes only. It is not intended for use in a production environment." | https://github.com/GoogleCloudPlatform/vertex-ai-creative-studio , katalog `experiments/mcp-genmedia/mcp-genmedia-go/`; `server.json`: `io.github.GoogleCloudPlatform/genmedia-creative-studio-mcp-veo-go` — w oficjalnym rejestrze MCP nie znaleziono (runda 3-4) | Apache-2.0 | commit 477819b 2026-11-25 (ponowiony klon w rundzie 5) | Veo: `veo_t2v`, `veo_i2v`, `veo_extend_video`, `veo_first_last_to_video`, `veo_reference_to_video`, `veo_ingredients_to_video`. Omni: `omni_video_generation`. Ten sam pakiet: Gemini TTS, Chirp 3 HD, Lyria, AVTool | Go, stdio/SSE/HTTP; tylko droga A (ADC); env `GOOGLE_CLOUD_PROJECT`, `GOOGLE_CLOUD_LOCATION`, `GENMEDIA_BUCKET`; wyniki Veo w GCS |
| `@aimuzov/veo-mcp` | spolecznosciowy, rzad 4, NIEPOTWIERDZONE | https://github.com/aimuzov/veo-mcp ; npm 0.3.7 (2026-10-29) | MIT | commit dd01e92 2026-11-23 | `generate_video`, `fetch_video`, `list_models` | Gemini API (`GEMINI_API_KEY`); domyslny model `veo-3.1-generate-preview` — **wylaczony 2026-10-22** (Z11) -> dla Veo niedzialajacy (wniosek, nie test) |
| `@houtini/gemini-mcp` | spolecznosciowy, rzad 4, NIEPOTWIERDZONE | https://github.com/houtini-ai/gemini-mcp ; npm 2.10.1 (2026-10-24) | Apache-2.0 | commit 52fbddd 2026-10-25 | `generate_video` (Veo 3.1 preview) + 13 innych | jw. — modele wylaczone; "Omni ... not wired in yet" |
| `mcp-veo` (AceDataCloud) | spolecznosciowy/posrednik, rzad 4, NIEPOTWIERDZONE | https://github.com/AceDataCloud/VeoMCP ; rejestr MCP: `io.github.AceDataCloud/mcp-veo` (2026.11.27.0) | MIT | commit b4d5064 2026-11-27 | `veo_text_to_video`, `veo_image_to_video`, `veo_get_task`, ... | wywoluje API posrednika AceDataCloud (nie Google) |
| `omni-mcp-server` (dawniej `veo-mcp-server`), u2n4 | spolecznosciowy, rzad 4, NIEPOTWIERDZONE | https://github.com/u2n4/gemini-media-mcp ; rejestr: `io.github.u2n4/veo-mcp-server` 1.1.2 (nieaktualny wpis) | MIT | commit e10cd49 2026-11-06 | 9 narzedzi `omni_*` (generowanie, i2v, extend, interpolacja, `omni_check_job`) | Omni przez Gemini API (`GEMINI_API_KEY`) |
| `@runapi.ai/veo-3-1-mcp` (RunAPI) | spolecznosciowy/posrednik, rzad 4, NIEPOTWIERDZONE | https://github.com/runapi-ai/veo-3-1-mcp ; rejestr: `io.github.runapi-builder/veo-3-1-mcp` 0.2.1 | Apache-2.0 | commit 7077987 2026-10-22 | `text_to_video`, `extend_video`, `upscale_video`, `get_task`, ... | API posrednika RunAPI (nie Google) |
| `mcp-flow-google` (openFlow) i podobne | spolecznosciowe, rzad 4, NIEPOTWIERDZONE | https://github.com/molkex/mcp-flow-google (rejestr: `io.github.molkex/omni-flash-veo3-nano-banana` 1.2.0) | MIT | commit 20da065 2026-10-19 | 31 narzedzi | automatyzuja aplikacje Google Flow, ktora wg README "has no public API"; **niezalecane** |

## 7. Alternatywne drogi dostepu (platformy posredniczace; bez porownania cen)

| Platforma | Modele Google | Dowod | Rzad | Pewnosc |
|---|---|---|---|---|
| fal.ai | `fal-ai/veo3.1` (t2v, i2v, first-last-frame, reference-to-video, extend); `google/gemini-omni-flash/v1.1/*`, `v1.2/*` | odczyt posredni z indeksu wyszukiwarki (host spoza listy, rundy 1-3) | 5 | **NIEPOTWIERDZONE** |
| OpenRouter | `google/gemini-omni-1.1-flash` | odczyt posredni z indeksu wyszukiwarki (rundy 1-3) | 5 | **NIEPOTWIERDZONE** |
| AceDataCloud | Veo (API posrednika + MCP) | repo spolecznosciowe (bezposr., commit 2026-11-27) i rejestr MCP — potwierdzaja istnienie repozytorium, nie dostepnosc modelu Google u posrednika | 4-5 | **NIEPOTWIERDZONE** |
| RunAPI | Veo 3.1 (`@runapi.ai/veo-3.1`, `@runapi.ai/veo-3-1-mcp`) | repo (bezposr.), npm (runda 3) — istnienie pakietow; dostepnosc modelu u posrednika niesprawdzona | 4-5 | **NIEPOTWIERDZONE** |
| kie.ai | "85+ video models" — czy zawiera Veo nie wiadomo | npm, tylko opis pakietu | 5 | **NIEPOTWIERDZONE** |
| Vercel AI Gateway | `veo-3.1-lite-generate-001` | RESEARCH-001 Z7 (rzad 5), odczyt posredni z indeksu wyszukiwarki | 5 | **NIEPOTWIERDZONE** |

Wszystkie pozycje tej sekcji sa rzedu 4-5 i sa NIEPOTWIERDZONE (legenda: sekcja 0b); nie sa podstawa zadnej oceny tak/nie ani punktacji.

## 8. Minimalna sciezka sterowania z Claude Code

**(b) Przez CLI/HTTP/SDK z narzedzia powloki — NAJPROSTSZA i najpewniejsza (zrodla rzedu 1):**
- **Omni przez oficjalne CLI (droga B):** binarka `gemini-api` + zmienna `GEMINI_API_KEY` (projekt na Tier 1). Polecenie: `gemini-api video "<prompt>" -m gemini-omni-1.2-flash --resolution 1080p --out klip.mp4` (czeka i zapisuje MP4, na stdout tylko sciezka); `--async` -> id interakcji, potem `gemini-api video --resume <id> --out <plik>`; `-i <obraz>` dla obrazu startowego; `--dry-run` podglada zadanie bez wywolania. Dokumentacja CLI wprost wymienia Claude Code; opcjonalna umiejetnosc `gemini-api-cli` (google-gemini/gemini-skills). Z20, Z3.
- **Omni przez REST (droga B):** `POST https://generativelanguage.googleapis.com/v1beta/interactions` z `model: "gemini-omni-1.2-flash"`, `input`, `response_format` (`type: video`, `resolution`, `duration`, `aspect_ratio`, `delivery: "uri"`), opcjonalnie `background: true` + `webhook_config`; wynik w `steps[].content[]`. Z3.
- **Veo (droga A):** `POST https://us-central1-aiplatform.googleapis.com/v1/projects/{PROJECT_ID}/locations/us-central1/publishers/google/models/veo-3.1-generate-001:predictLongRunning` (body: `instances[].prompt`, `image`, `lastFrame`, `referenceImages[{image, referenceType:"asset"}]`; `parameters`: `durationSeconds`, `resolution`, `seed`, `sampleCount`, `personGeneration`, `generateAudio`, `storageUri`) -> nazwa operacji -> `POST ...:fetchPredictOperation` z `{"operationName": ...}` w petli -> pobranie z GCS (`gcloud storage cp`) lub bajtow z odpowiedzi. Uwierzytelnienie: `gcloud auth print-access-token` (ADC). W Pythonie: `genai.Client(vertexai=True, project=..., location="us-central1")`, `client.models.generate_videos(...)`, petla `client.operations.get(operation)`. Z7, Z10, Z1, Z2.
- **Omni (droga A):** `POST https://aiplatform.googleapis.com/v1beta1/projects/{PROJECT_ID}/locations/global/interactions` (`background: true`, `generation_config.seed`, `response_format.delivery: "uri"` + `gcs_uri`), odbior `GET .../interactions/{INTERACTION_ID}`. Z13.
- Claude Code uruchamia te polecenia narzedziem Bash; dlugie zadania -> odpytywanie co 10-20 s.

**(a) Przez serwer MCP — mozliwa, ale tylko demo:** `mcp-veo-go` / `mcp-omni-go` (GoogleCloudPlatform, status demo): projekt GCP z rozliczeniem, ADC (`gcloud auth application-default login` lub `GOOGLE_APPLICATION_CREDENTIALS`), `GOOGLE_CLOUD_PROJECT`, bucket `GENMEDIA_BUCKET`; rejestracja w Claude Code jako serwer stdio (`claude mcp add ...` — wniosek ze standardowego transportu; README nie wymienia Claude Code); narzedzia `veo_t2v`, `veo_i2v`, `veo_first_last_to_video`, `veo_reference_to_video`, `veo_extend_video`, `omni_video_generation`. Instalacji (`install-online.sh`) **nie wykonywano**. Oficjalny zdalny MCP Agent Platform jest produkcyjny, ale nie ma narzedzi do wideo (sekcja 6). Serwery spolecznosciowe dla Gemini API (aimuzov, houtini; rzad 4, NIEPOTWIERDZONE) celuja w wylaczone modele Veo preview.

**(c) Brak** — nie dotyczy.

## 9. Zrodla

| # | URL | Rzad | Data odczytu | Sposob | Co potwierdza |
|---|---|---|---|---|---|
| Z1 | https://github.com/googleapis/python-genai (README.md, sekcja "Veo") | 1 | 2026-11-27 | bezposr. (git) | przyklady `generate_videos`, `client.operations.get` |
| Z1a | https://github.com/googleapis/js-genai (README.md) | 1 | 2026-11-27 | bezposr. (git; commit 3445a09, 2026-11-24) | Veo tylko na Agent Platform; wymagania dostepu |
| Z2 | python-genai: `google/genai/models.py`, `operations.py`, `types.py`, `_gaos/...` (commit 36e2970, 2026-11-24) | 1 | 2026-11-27 | bezposr. | `:predictLongRunning`, `:fetchPredictOperation`; blad `generate_videos` w Gemini API; `webhook_config` tylko Gemini API; `pubsub_topic`; enum ASSET/STYLE |
| Z3 | https://aistudio.google.com/docs/omni ; https://aistudio.google.com/docs/webhooks.md (dawniej ai.google.dev/gemini-api/docs/omni, /webhooks) | 1 | 2026-11-27 | **bezposr. (runda 5, curl 200)** | REST `/v1beta/interactions`; 3-15 s; 360p-4k; do 6 obrazow ref.; pierwsza/ostatnia klatka 3-10 s; extend +3..10 s do 30 s; ograniczenia EOG/CH/UK; brak wejsc audio; webhooki (Preview) i zdarzenia; `background`, `delivery: "uri"` |
| Z4 | https://pypi.org/pypi/google-genai/json ; https://registry.npmjs.org/@google/genai ; https://github.com/googleapis/go-genai (commit 14c5840, 2026-11-24) ; https://github.com/googleapis/java-genai (commit f0114a7, 2026-11-25) | 1 | 2026-11-27 | bezposr. (PyPI/npm w rundzie 3; git w rundzie 5) | wersje 3.6.1, Apache-2.0, aktywnosc |
| Z5 | https://github.com/GoogleCloudPlatform/vertex-ai-creative-studio (`README.md`, `LICENSE`, `experiments/mcp-genmedia/...`; commit 477819b, 2026-11-25) | 1 (istnienie); status demo | 2026-11-27 (runda 5: ponowiony klon, ten sam commit) | bezposr. | narzedzia MCP Veo/Omni, env, ADC, "not an officially supported Google product" |
| Z6 | https://registry.modelcontextprotocol.io/v0/servers?search=veo / genmedia / omni / ... | 1 (rejestr) | 2026-11-27 (rundy 3-4) | bezposr. | wpisy spolecznosciowe; brak wpisu genmedia Google |
| Z7 | https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/video/generate-videos-from-text (akt. 2026-11-24) | 1 | 2026-11-27 | **bezposr. (runda 5)** | `predictLongRunning`, `fetchPredictOperation`, parametry `sampleCount` 1-4, `durationSeconds` 4/6/8, `seed` uint32, `personGeneration` allow_adult/disallow, `resolution`, `storageUri` |
| Z8 | https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/start/express-mode/overview | 1 | 2026-11-27 | **bezposr. (runda 5)** | tryb express (Preview): @gmail.com, klucz API, 90 dni bez danych rozliczeniowych dla nowych uzytkownikow |
| Z9 | https://aistudio.google.com/docs/veo | 1 | 2026-11-27 | **bezposr. (runda 5)** | wylaczenie Veo 3.1 preview 2026-10-22 i zalecenie migracji; `personGeneration` tylko `allow_adult` w EU/UK/CH/MENA; opoznienie 11 s-6 min; przechowywanie 2 dni; extend +7 s, do 20 razy |
| Z10 | https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/veo/3-1-generate (akt. 2026-11-24) | 1 | 2026-11-27 | **bezposr. (runda 5)** | modele `-generate-001`/`-fast-`/`-lite-`, funkcje (t2v, i2v, pierwsza/ostatnia klatka, extend, asset images, dzwiek), 4/6/8 s, do 4 filmow, 720p/1080p/4K, `us-central1`, kwota 50/min, GA 17.11.2025, wycofanie "May 4, 2027 or later" |
| Z11 | https://aistudio.google.com/docs/deprecations | 1 | 2026-11-27 | **bezposr. (runda 5)** | Veo 3.1 preview wylaczone 2026-10-22; Veo 3.0/2.0 wylaczone 2026-06-30; Omni 1.2 wydany 2026-11-05 bez daty wylaczenia; 1.1 -> 1.2 od 2026-12-03 |
| Z12 | https://discuss.ai.google.dev (watki o Omni, Tier 1) | 4 | 2026-11-27 | posr. (runda 3) | **NIEPOTWIERDZONE**; zastapione przez Z18/Z19 (Tier 1 potwierdzony w rzedzie 1) |
| Z13 | https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/video/generate-videos-from-references (akt. 2026-11-24; dawniej .../use-reference-images-to-guide-video-generation) | 1 | 2026-11-27 | **bezposr. (runda 5)** | Veo: do 3 obrazow jednej osoby/postaci/produktu, tylko 3.1 i 3.1 Fast, `referenceType: "asset"`; Omni na Agent Platform: `v1beta1/.../locations/global/interactions`, tryby sync/async, retencja 7 dni, `gcs_uri`, `generation_config.seed` |
| Z14 | https://github.com/aimuzov/veo-mcp ; https://github.com/houtini-ai/gemini-mcp ; https://github.com/AceDataCloud/VeoMCP ; https://github.com/molkex/mcp-flow-google ; https://github.com/u2n4/gemini-media-mcp ; https://github.com/runapi-ai/veo-3-1-mcp | 4 (spolecznosciowe) | 2026-11-27 (runda 5: daty commitow odswiezone klonem) | bezposr. (git) | istnienie, licencje, daty; jakosc i dzialanie **NIEPOTWIERDZONE** |
| Z15 | fal.ai, openrouter.ai, Vercel AI Gateway (wg RESEARCH-001 Z7), kie.ai (opis npm) | 5 (posrednicy) | 2026-11-27 (rundy 1-3) | posr. (indeks wyszukiwarki; hosty spoza listy) | dostepnosc modeli u posrednikow — **NIEPOTWIERDZONE** |
| Z16 | https://docs.cloud.google.com/mcp/supported-products | 1 | 2026-11-27 | **bezposr. (runda 5)** | zdalne MCP Google Cloud; Agent Platform: endpointy `aiplatform.googleapis.com/mcp/{generate,predict,notebook,endpoints,models,tuning,retrieval,evaluation,prompts}`; brak osobnej pozycji dla Veo/Omni |
| Z17 | proba odczytu w rundzie 4 (ECHO-019) | — | 2026-11-27 | proba nieudana | historyczne; w rundzie 5 hosty dostepne |
| Z18 | https://aistudio.google.com/docs/rate-limits | 1 | 2026-11-27 | **bezposr. (runda 5)** | limity Omni per tier; Free "Not supported"; tiery i kwalifikacja; limity wydatkow |
| Z19 | https://aistudio.google.com/docs/models/gemini-omni-flash.md ; https://aistudio.google.com/docs/libraries.md ; https://aistudio.google.com/docs/api-key.md ; https://aistudio.google.com/llms.txt | 1 | 2026-11-27 | **bezposr. (runda 5)** | karta Omni (wejscia, 3-15 s, 24 FPS, wersje, Free "Not available"); SDK Python/JS/Go/Java/C#; klucze API i weryfikacja projektu dla Free |
| Z20 | https://aistudio.google.com/docs/cli.md ; https://aistudio.google.com/docs/coding-agents.md ; https://github.com/google-gemini/gemini-api-cli (commit 3dcbb6e 2026-11-26, tag v0.5.0, LICENSE Apache-2.0) ; https://github.com/google-gemini/gemini-skills (commit c4d0c62 2026-11-18, Apache-2.0) | 1 | 2026-11-27 | **bezposr. (runda 5; curl + git)** | CLI `gemini-api` (beta) z poleceniem `video`, `--async`/`--resume`, wsparcie Claude Code; w kodzie tylko `generativelanguage.googleapis.com`; skills; Gemini Docs MCP (`gemini_search_docs`, `gemini_get_doc`) |
| Z21 | https://docs.cloud.google.com/gemini-enterprise-agent-platform/reference/mcp (akt. 2026-07-30) ; https://docs.cloud.google.com/gemini-enterprise-agent-platform/reference/use-agent-platform-mcp (akt. 2026-11-20) | 1 | 2026-11-27 | **bezposr. (runda 5)** | zestawy narzedzi zdalnego MCP Agent Platform; Streamable HTTP; OAuth 2.0/IAM, klucz API (express lub z kontem serwisowym); Claude jako klient |
| Z22 | https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/quotas (akt. 2026-11-20) | 1 | 2026-11-27 | **bezposr. (runda 5)** | metryki kwot: Omni `global_generate_content_requests_per_minute_per_project_per_base_model`, Veo `long_running_online_prediction_requests_per_base_model`; tabela deferred interactions (do 500 rownoleglych generacji) |

## Niepewnosci i uwagi dla syntezy

- **N1:** "Oficjalny serwer MCP" dla generowania wideo Google: (i) zdalny MCP Agent Platform jest oficjalnym produktem, ale wg listy narzedzi nie generuje Veo/Omni; (ii) `mcp-veo-go`/`mcp-omni-go` generuja wideo, ale sa w repo Google z zastrzezeniem "not an officially supported Google product ... demonstration purposes only". Propozycja wezla dla punktacji: **1 pkt (jak spolecznosciowy)**; wariant 2 pkt opisany jako alternatywa — rozstrzyga synteza/Evaluator wg tresci zlecenia.
- **N2:** Veo dla zwyklego klucza Gemini API **nie istnieje** od 2026-10-22 (bezposr. Z9, Z11, Z2). Kazda instrukcja/serwer z `veo-3.1-*-preview` i `GEMINI_API_KEY` jest nieaktualna.
- **N3:** Webhook: Gemini API (Omni) TAK (Preview, bezposr.); Agent Platform — Veo: webhook NIE (kod SDK), `pubsub_topic` tylko w SDK (NIEPOTWIERDZONE w dokumentacji uslugi); Omni na Agent Platform: `background: true` + odpytywanie po id, webhook NIEPOTWIERDZONE.
- **N4:** Osobny limit zadan rownoleglych dla Veo i Omni — nie znaleziony (tylko RPM/RPD i tabela deferred interactions).
- **N5:** Dla polskiej produkcji (EOG): Veo z ludzmi tylko `allow_adult` (dorosle postacie OK); Omni — bez edycji/przedluzania WGRANYCH wideo i bez wgrywania obrazow z nieletnimi; przedluzanie wideo wygenerowanych przez model dziala.
- **N6:** Karta Veo 3.1 na Agent Platform: "Pay-as-you-go: Not supported", "Fixed quota: Supported". Rozumienie, czy zwykly projekt z rozliczeniem korzysta z "Fixed quota" bez dodatkowej umowy — **NIEPOTWIERDZONE** (strony o trybach konsumpcji nie odczytano); dokumentacja generate-videos-from-text pokazuje zwykle wywolanie REST na projekcie z rozliczeniem, bez wzmianki o umowie. Do sprawdzenia przy tescie (TASK 16) — nie wplywa na istnienie API.
- **N7:** 4K dla `veo-3.1-generate-001`: karta modelu TAK, strona parametrow "4k (Veo 3.1 Preview models only)" — sprzecznosc w dokumentacji, NIEPOTWIERDZONE.

Wstepna punktacja wg kryteriow zlecenia (do przeliczenia w syntezie): API dla zwyklego konta 3 + obraz do wideo z klatka startowa 2 + obrazy referencyjne 2 + asynchronicznosc i webhook 1 (Omni w Gemini API: `background` + webhooki; Veo: LRO) + oficjalne SDK 1 (Python/JS/Go/Java, plus CLI `gemini-api`) + MCP 1 (N1; wariant 2) + brak barier onboardingu 1 (projekt z rozliczeniem / Tier 1 to zwykla rejestracja, bez weryfikacji firmy i listy oczekujacych) = **11 / 12** (wariant 12). Ryzyko dla punktu onboardingu: N6.
