# ZERO-RESEARCH-003-d — OpenAI Sora 2 / Sora 2 Pro: API, SDK, MCP i sterowanie z Claude Code

Wezel: d (Sora 2). Tresc z rundy 1 z 3; runda 3 z 3: jedyna poprawka Final Control (PROC-R2-1, licznik w `autobot/REJESTR_TEMATOW.md`) nie dotyczy tego pliku, tresc merytoryczna bez zmian. Kontrola punktowa w rundzie 3 (2026-11-27, B): PyPI `openai` nadal 3.60.0; `src/openai/resources/videos.py` na `main` nadal z dekoratorem deprecated (2026-09-24); rejestr MCP: wszystkie wersje `io.github.AceDataCloud/mcp-sora` nadal `deprecated`. Rola: Operator (Opus 5.5). Data odczytu wszystkich zrodel: 2026-11-27.
Zakres: wylacznie odczyt dokumentacji, repozytoriow i rejestrow. NIE zalozono kont ani kluczy, NIE zainstalowano serwerow MCP, SDK ani bibliotek, NIE wykonano zadnego wywolania API OpenAI, Azure ani platform posredniczacych, NIE uruchomiono kodu z repozytoriow (pliki zrodlowe czytane przez `git show` bez checkoutu). Zadnych kluczy i sekretow w tym pliku.

## 0. STATUS NA 2026-11-27: API WYLACZONE — dane o mozliwosciach sa HISTORYCZNE

**Teza z RESEARCH-001 ("API Sora 2 wylaczone 2026-09-24") — POTWIERDZONA** trzema niezaleznymi zrodlami rzedu 1:

| # | Zrodlo rzedu 1 | Co stwierdza | Sposob odczytu |
|---|---|---|---|
| 1 | Strona deprecations OpenAI (Z1) | 2026-03-24 powiadomienie deweloperow Videos API; Videos API oraz `sora-2`, `sora-2-pro` i snapshoty usuniete z API **2026-09-24**; brak rekomendowanego zastepcy | posredni (indeks wyszukiwarki) |
| 2 | Artykul pomocy "What to know about the Sora discontinuation" (Z2) | aplikacja/strona Sora wylaczone 2026-04-26; Sora API wylaczone 2026-09-24 ("was discontinued"; starsze kopie w czasie przyszlym, ta sama data) | posredni |
| 3 | **Kod oficjalnego SDK Python `openai/openai-python`** (Z5), HEAD f2b2399 z 2026-11-26 (wydanie 3.60.0) | kazda metoda `client.videos.*` ma dekorator `@typing_extensions.deprecated("The Sora API is scheduled to permanently shut down on September 24, 2026.")`; CHANGELOG: "deprecate Sora video APIs" w wydaniu 3.1.0 (2026-08-14) | **bezposredni** (git, tylko odczyt) |
| 4 | Kod oficjalnego SDK Node `openai/openai-node` (Z6), HEAD 3ee4d75 z 2026-11-26 (7.65.0) | `src/resources/videos.ts`: `@deprecated The Sora API is scheduled to permanently shut down on September 24, 2026.` | **bezposredni** |

Dodatkowe poszlaki (rzad 4, NIEPOTWIERDZONE): Replicate wyswietla na stronach `openai/sora-2` i `openai/sora-2-pro` komunikat "OpenAI is discontinuing Sora 2 on September 24, 2026" (Z14); posrednik AceDataCloud oznaczyl swoj serwer MCP Sora jako `deprecated` w oficjalnym rejestrze MCP (2026-10-18) i opisal integracje jako "retired" (Z9); serwer `@infimind/video-mcp-cli` 1.0.15 (2026-11-12) odrzuca Sora 2 bledem `MODEL_RETIRED` (Z12).

**Czego NIE potwierdzono:** faktycznego stanu endpointu `https://api.openai.com/v1/videos` dzis (wymagaloby wywolania API, zakazanego w tym badaniu). Data 2026-09-24 jest w zrodlach rzedu 1 data usuniecia; brak zrodla o przedluzeniu. Nowego modelu wideo OpenAI w API na 2026-11-27 nie znaleziono (wyszukiwanie w domenach openai.com / developers.openai.com / help.openai.com; Z1 nie wskazuje zastepcy).

**Kanal Azure OpenAI / Microsoft Foundry: tez wycofany.** Microsoft Learn "Retired Foundry Models" (Z13, rzad 1 dla Azure, odczyt posredni): `sora-2` 2025-10-06 wycofany 2026-07-15, `sora-2` 2025-12-08 wycofany 2026-11-02; strona harmonogramu podaje dla 2025-12-08 date 2026-10-15 (rozbieznosc dat miedzy stronami Microsoft; obie przed 2026-11-27). Watek Q&A Microsoft (rzad 4) zglasza blad wdrozenia `ServiceModelDeprecated` dla 2025-12-08.

**Wniosek:** na 2026-11-27 nie istnieje oficjalna droga sterowania generowaniem Sora 2 (ani z Claude Code, ani inaczej). Pola 1-8 ponizej opisuja stan **sprzed wylaczenia** (oznaczone HIST), zeby synteza i wlasciciel mieli pelny obraz, ale nie da sie z nich skorzystac.

### 0.1 Zastrzezenie o dostepie do zrodel

- Hosty `developers.openai.com`, `platform.openai.com`, `help.openai.com`, `openai.com`, `learn.microsoft.com`, `community.openai.com` sa w tej sesji niedostepne (curl: kod 000 / proxy 403 `connect_rejected`). Tresc dokumentacji OpenAI i Microsoft = **odczyt posredni** (WebSearch z filtrem `allowed_domains` na domeny dostawcy). Pewnosc tych twierdzen najwyzej `srednia`.
- Odczytane **bezposrednio**: oficjalne repozytoria SDK (`git clone --depth 1 --filter=blob:none --no-checkout` + `git show` plikow, bez uruchamiania), rejestr npm, PyPI, oficjalny rejestr MCP `registry.modelcontextprotocol.io`, repozytoria serwerow spolecznosciowych (jw.).
- Konwencje: `B` = odczyt bezposredni, `P` = odczyt posredni; `HIST` = stan sprzed 2026-09-24; `NIEPOTWIERDZONE` = rzad 4-5 albo zrodlo nie mowi wprost.

## 1. Publiczne API (REST) — dostepnosc dla zwyklego konta

| Pytanie | Odpowiedz | Zrodlo | Pewnosc |
|---|---|---|---|
| Czy istnieje publiczne API REST **dzis (2026-11-27)** | **NIE** — Videos API i modele `sora-2*` usuniete 2026-09-24, bez zastepcy | Z1, Z2, Z5, Z6 | wysoka (zgodnosc rzedu 1 posredniego i bezposredniego kodu SDK) |
| Czy istnialo (HIST) | TAK — endpoint `v1/videos` uruchomiony w pazdzierniku 2025 (changelog), rozszerzony 2026-03 (postacie, extensions, 1080p, Batch) | Z3 | srednia (P) |
| Jak sie je uzyskiwalo (HIST) | klucz API platformy OpenAI (naglowek `Authorization: Bearer`, standard SDK); model musial byc dostepny dla organizacji. Weryfikacja organizacji: strona pomocy OpenAI mowi ogolnie, ze "may be required for certain products, models, or features" — czy byla wymagana dla Sora, **NIEPOTWIERDZONE** (brak zrodla wprost) | Z5, Z15 | niska |
| Ograniczenia regionalne / lista oczekujacych (HIST) | BRAK DANYCH w odczytanych zrodlach rzedu 1 | — | brak |
| Azure OpenAI (HIST) | osobny kanal, osobne konto Azure; wycofany (zob. sekcja 0) | Z13 | srednia (P) |

## 2. Model pracy (asynchronicznosc) — HIST

- **Zadanie asynchroniczne: TAK (HIST).** `POST /videos` zwraca obiekt `video` z `id`, `status`, `progress`; pola obiektu wg typu SDK: `id`, `created_at`, `completed_at`, `expires_at`, `error`, `model`, `progress`, `prompt`, `remixed_from_video_id`, `seconds`, `size`, `status` (Z5 `types/video.py`, B).
- **Statusy:** `queued`, `in_progress`, `completed`, `failed` (Z5, B; potwierdzone tez w Z4, P).
- **Status:** `GET /videos/{video_id}`; lista: `GET /videos`; usuniecie: `DELETE /videos/{video_id}` (Z5, B).
- **Pobranie wyniku:** `GET /videos/{video_id}/content` z parametrem `variant` = `video` / `thumbnail` / `spritesheet` (Z5, B). Wg strony "Data controls" pobranie bylo mozliwe przez 48 h, potem 30 dni retencji (Z3b, P).
- **Polling w SDK:** metody pomocnicze `create_and_poll()` i `poll()` z `poll_interval_ms` (Z5, B).
- **Webhook: TAK (HIST)** — zdarzenia `video.completed` i `video.failed`, wybierane przy tworzeniu endpointu webhook organizacji; ladunek zawiera id wideo (Z4, P; japonska wersja przewodnika "video-generation" + strona "Create Webhook Endpoint").
- **Batch:** `/v1/videos` dodany do Batch API (SDK 2.29.0, 2026-03-17; changelog OpenAI 2026-03) (Z5, B; Z3, P).

## 3. Limity — HIST

| Limit | Wartosc | Zrodlo | Pewnosc |
|---|---|---|---|
| Zapytania na minute (RPM) dla `sora-2` / `sora-2-pro` | **BRAK DANYCH** — wyszukiwanie w domenach OpenAI nie zwrocilo liczb per model; strona "Rate limits" opisuje ogolnie RPM/RPD, poziomy uzycia i to, ze limity zaleza od modelu i sa widoczne w konsoli organizacji | Z16 | brak (liczb nie podaje sie z pamieci) |
| Zadania rownolegle | BRAK DANYCH | — | brak |
| Dzis | nie dotyczy (API wylaczone) | Z1 | — |

## 4. Zakres API wzgledem aplikacji — HIST

| Funkcja | API (HIST) | Zrodlo | Pewnosc |
|---|---|---|---|
| Tekst do wideo | TAK: `POST /videos`, `prompt` (wymagany), `model` (`sora-2` / `sora-2-pro`) | Z5 (B), Z4 | wysoka (kod SDK) |
| Obraz do wideo — klatka startowa | TAK: `input_reference` (upload albo obiekt z dokladnie jednym z `image_url` / `file_id`); prompting guide: obraz jako kotwica pierwszej klatki | Z5 (B), Z4, Z7 (P) | srednia |
| Klatka koncowa | **NIE** — brak takiego parametru w `VideoCreateParams` (pola: `prompt`, `input_reference`, `model`, `seconds`, `size`) | Z5 (B) | wysoka |
| Przedluzanie klipu | TAK: `POST /videos/extensions` (caly oryginalny klip jako kontekst) | Z5 (B), Z4 (P) | wysoka |
| Edycja / remix | TAK: `POST /videos/edits`, `POST /videos/{video_id}/remix` | Z5 (B) | wysoka |
| Obrazy referencyjne postaci (spojnosc) | TAK: Characters API `POST /videos/characters`, `GET /videos/characters/{character_id}`; prompting guide: do 2 postaci na generacje | Z5 (B), Z7 (P) | srednia (limit 2 — P) |
| Parametry audio | NIE ma parametru audio w `VideoCreateParams` (audio generowane zawsze, sterowane promptem — RESEARCH-002) | Z5 (B) | wysoka |
| Rozdzielczosc | SDK 3.60.0: `size` = `720x1280`, `1280x720`, `1024x1792`, `1792x1024`; changelog 2026-03: 1080p dla `sora-2-pro` (wartosci 1080p brak w typie SDK — rozbieznosc) | Z5 (B), Z3 (P) | srednia |
| Dlugosc | SDK i strona referencyjna: `seconds` = 4, 8, 12 (domyslnie 4); changelog 2026-03 i archiwalny prompting guide: do 20 s (4/8/12/16/20) — **rozbieznosc** (ta sama, co w RESEARCH-001) | Z5 (B), Z3, Z7 (P) | srednia |
| Seed | **NIE** — brak parametru w `VideoCreateParams` | Z5 (B) | wysoka |
| Modele / snapshoty | `sora-2`, `sora-2-pro`, `sora-2-2025-10-06`, `sora-2-pro-2025-10-06`, `sora-2-2025-12-08` | Z5 `types/video_model.py` (B) | wysoka |

## 5. Oficjalne SDK lub CLI

| Element | Stan | Szczegoly | Zrodlo | Pewnosc |
|---|---|---|---|---|
| SDK Python `openai` | **ISTNIEJE, ale zasob `videos` przestarzaly (deprecated) i bez dzialajacego backendu** | PyPI `openai` 3.60.0 (2026-11-26); repozytorium `github.com/openai/openai-python`, ostatni commit 2026-11-26 (f2b2399), licencja Apache-2.0 (plik LICENSE); `src/openai/resources/videos.py`: `create`, `retrieve`, `list`, `delete`, `create_character`, `get_character`, `download_content`, `edit`, `extend`, `remix`, `create_and_poll`, `poll` — wszystkie z dekoratorem deprecated (data 2026-09-24) | Z5, Z10 (B) | wysoka |
| SDK Node/TypeScript `openai` | **ISTNIEJE, zasob `videos` deprecated** | npm `openai` 7.65.0 (2026-11-26), licencja Apache-2.0; repozytorium `github.com/openai/openai-node`, commit 2026-11-26 (3ee4d75); `src/resources/videos.ts` z `@deprecated` | Z6, Z11 (B) | wysoka |
| Inne jezyki | Dokumentacja referencyjna OpenAI ma warianty `typescript`, `ruby`, `python` metod wideo (np. `.../ruby/resources/videos/methods/extend`) — tylko odczyt P, nie sprawdzano repozytoriow | Z4 | srednia |
| Oficjalne CLI do Sora | Nie znaleziono | — | srednia (brak dowodu negatywnego) |

Wniosek: SDK istnieje i jest aktywnie utrzymywane, ale metody wideo prowadza do usunietego API — **do sterowania Sora 2 dzis bezuzyteczne** (historyczne).

## 6. Serwer MCP

### 6.1 Oficjalny (OpenAI)

**NIE znaleziono.** W oficjalnym rejestrze MCP (`registry.modelcontextprotocol.io`, wyszukiwanie `sora` — 81 wpisow, `openai` — wszystkie strony) brak serwera w przestrzeni nazw OpenAI (`com.openai.*`, `io.github.openai/*`) dotyczacego wideo (Z8, B). Wyszukiwanie w domenach openai.com / developers.openai.com / github.com nie zwrocilo oficjalnego serwera MCP dla Sory (Z17, P). Pewnosc: srednia (brak dowodu negatywnego w pelnej dokumentacji).

### 6.2 Spolecznosciowe / posrednikow (rzad 4 — NIEPOTWIERDZONE co do jakosci; wszystkie HISTORYCZNE)

Wszystkie ponizsze korzystaly z API OpenAI (lub posrednika), wiec po 2026-09-24 **nie moga generowac Sora 2**. Nie instalowano, nie uruchamiano.

| Nazwa | Repozytorium / rejestr | Licencja | Ostatnia aktywnosc | Backend i narzedzia | Stan |
|---|---|---|---|---|---|
| AceDataCloud SoraMCP (`mcp-sora`; `io.github.AceDataCloud/mcp-sora`) | github.com/AceDataCloud/SoraMCP; PyPI `mcp-sora` | MIT (LICENSE, PyPI) | commit 2026-11-24 (d8ff51c, porzadki po wycofaniu); PyPI 2026.10.8.0 z 2026-10-08; rejestr: wszystkie wersje `deprecated` od 2026-10-18 | posrednik AceDataCloud; narzedzia (CHANGELOG): `sora_generate_video`, `sora_generate_video_from_image`, `sora_generate_video_with_character`, `sora_generate_video_async`, `sora_get_task`, `sora_get_tasks_batch`, `sora_list_models`, `sora_list_actions` | **WYCOFANY** — README: "The AceDataCloud Sora integration is retired. Its hosted MCP server and public Sora API endpoints are no longer offered." (Z9, B) |
| Doriandarko/sora-mcp (npm `@iflow-mcp/sora-mcp-server` 1.0.0 to kopia z 2025-12-02) | github.com/Doriandarko/sora-mcp | MIT (LICENSE) | commit 2025-10-08 (8f569eb) — nieaktywny ok. 13,5 mies. | bezposrednio API OpenAI (klucz OpenAI z dostepem do Sora); `create-video`, `get-video-status`, `list-videos`, `download-video`, `remix-video`, `delete-video` | martwy backend (API OpenAI wylaczone) (Z12b, B) |
| strato-space/media-gen-mcp | github.com/strato-space/media-gen-mcp | MIT (LICENSE, package.json 1.0.2) | commit 2026-01-30 (893feb7) | API OpenAI (obrazy + Sora) i Google Veo; narzedzia `openai-videos-create/remix/list/retrieve/delete/retrieve-content` | czesc Sora martwa; czesc Veo poza tym wezlem (Z12c, B) |
| airsulG/sora-mcp | github.com/airsulG/sora-mcp | MIT (LICENSE) | commit 2025-10-17 (e19a16a) | API OpenAI; narzedzie `generate_video` | martwy backend (Z12d, B) |
| nanameru/Sora2-MCP | github.com/nanameru/Sora2-MCP | MIT tylko w package.json (brak pliku LICENSE) | commit 2025-10-07 (554f938) | API OpenAI; `create_video`, `get_video_status`, `remix_video` (wg wyszukiwarki) | martwy backend (Z12e, B; narzedzia P) |
| `@infimind/video-mcp-cli` | npm (brak repozytorium w metadanych) | MIT (npm) | npm 1.0.15 z 2026-11-12 | wlasna aplikacja "Sora AI Video Generator" (nie OpenAI); README: model `SA` (Sora 2) "is retired ... rejected with `MODEL_RETIRED`" | Sora 2 niedostepna (Z12, B) |
| `com.jojapi/openai-sora` | tylko oficjalny rejestr MCP (zdalny `https://mcp.jojapi.com/openai-sora`), brak repozytorium | brak danych | opublikowany 2026-08-19, status `active` | opis: "OpenAI Sora: Sora & Sora 2 (new social media like TikTok) API" — z opisu wynika raczej dostep do serwisu spolecznosciowego Sora niz generowanie; zakres narzedzi nieznany | **NIEPOTWIERDZONE**; nie liczyc (brak repozytorium i licencji; aplikacja Sora zamknieta 2026-04-26) (Z8, B) |

## 7. Alternatywne drogi dostepu do Sora 2 (platformy posredniczace)

Tylko wymienione, bez porownywania cen. Zadna nie ma wlasnych wag modelu — wszystkie korzystaly z API OpenAI lub Azure.
- **Azure OpenAI / Microsoft Foundry** — wycofane (2026-07-15 i 2026-11-02 / 2026-10-15) (Z13, rzad 1 dla Azure, P).
- **Replicate** (`openai/sora-2`, `openai/sora-2-pro`) — strona z komunikatem o wylaczeniu 2026-09-24 (Z14, rzad 4, P); stanu biezacego nie potwierdzono (host niedostepny).
- **fal.ai** (`fal-ai/sora-2/text-to-video`, `.../image-to-video`, `.../video-to-video`) — dokumentacja w indeksie wyszukiwarki nadal widoczna, bez komunikatu o wylaczeniu (Z14b, rzad 4, P). Poniewaz backendem jest API OpenAI, dostepnosc po 2026-09-24 **NIEPOTWIERDZONA i malo prawdopodobna**; strony moga byc nieaktualne w indeksie.
- **AceDataCloud** — wycofane wprost (Z9, B).
- Wynik: **brak potwierdzonej dzialajacej drogi alternatywnej** na 2026-11-27.

## 8. Minimalna sciezka sterowania z Claude Code

**(c) BRAK — na 2026-11-27 nie ma sciezki sterowania Sora 2** (API usuniete 2026-09-24, Azure wycofany, oficjalnego MCP nigdy nie bylo, serwery spolecznosciowe bez dzialajacego backendu).

Dla porzadku — sciezka historyczna (HIST, niedzialajaca):
- **(b) HTTP/SDK z narzedzia powloki (HIST):** klucz API OpenAI -> `POST /v1/videos` (`model`, `prompt`, `input_reference`, `seconds`, `size`) lub `POST /v1/videos/extensions`, `POST /v1/videos/characters` -> polling `GET /v1/videos/{video_id}` (albo webhook `video.completed` / `video.failed`) -> `GET /v1/videos/{video_id}/content?variant=video`; w SDK Python `client.videos.create_and_poll(...)` + `client.videos.download_content(...)` (Z5, Z4).
- **(a) MCP (HIST):** wylacznie serwery spolecznosciowe (np. Doriandarko/sora-mcp: `create-video` -> `get-video-status` -> `download-video`) z kluczem OpenAI (Z12b).

## 9. Zrodla

Rzad: 1 = dokumentacja/repozytorium/rejestr dostawcy; 4 = spolecznosc/posrednicy (NIEPOTWIERDZONE co do jakosci). Sposob: B = bezposredni; P = posredni (indeks wyszukiwarki, host niedostepny).

| ID | URL | Rzad | Sposob | Data odczytu | Co potwierdza |
|---|---|---|---|---|---|
| Z1 | https://developers.openai.com/api/docs/deprecations | 1 | P | 2026-11-27 | powiadomienie 2026-03-24; usuniecie Videos API i `sora-2*` 2026-09-24; brak zastepcy |
| Z2 | https://help.openai.com/en/articles/20001152-what-to-know-about-the-sora-discontinuation | 1 | P | 2026-11-27 | aplikacja 2026-04-26; API 2026-09-24 |
| Z3 | https://developers.openai.com/api/docs/changelog | 1 | P | 2026-11-27 | `v1/videos` od 2025-10; 2026-03: postacie, do 20 s, 1080p `sora-2-pro`, extensions, Batch |
| Z3b | https://developers.openai.com/api/docs/guides/your-data.md | 1 | P | 2026-11-27 | 48 h na pobranie, 30 dni retencji |
| Z4 | https://developers.openai.com/api/reference/resources/videos/methods/create ; https://developers.openai.com/ja-JP/api/docs/guides/video-generation ; https://developers.openai.com/api/reference/resources/webhooks/methods/create ; https://developers.openai.com/api/reference/ruby/resources/videos/methods/extend | 1 | P | 2026-11-27 | parametry create, `input_reference`, statusy, webhook `video.completed`/`video.failed`, extensions |
| Z5 | https://github.com/openai/openai-python (HEAD f2b2399, 2026-11-26): `src/openai/resources/videos.py`, `src/openai/types/video*.py`, `CHANGELOG.md`, `LICENSE` | 1 | B | 2026-11-27 | metody i endpointy `/videos*`, dekorator deprecated (2026-09-24), parametry, `variant`, statusy, modele, seconds 4/8/12, rozmiary, Apache-2.0; changelog 3.1.0 (2026-08-14) "deprecate Sora video APIs", 2.29.0 Batch, 2.27.0 characters/extensions |
| Z6 | https://github.com/openai/openai-node (HEAD 3ee4d75, 2026-11-26): `src/resources/videos.ts`, `LICENSE` | 1 | B | 2026-11-27 | `@deprecated ... September 24, 2026`; Apache-2.0 |
| Z7 | https://developers.openai.com/cookbook/examples/sora/sora2_prompting_guide.md (archiwalny) | 1 | P | 2026-11-27 | kotwica pierwszej klatki, do 2 postaci, seconds do 20 |
| Z8 | https://registry.modelcontextprotocol.io/v0/servers?search=sora ; ?search=openai | 1 (rejestr) | B | 2026-11-27 | brak oficjalnego serwera OpenAI; `io.github.AceDataCloud/mcp-sora` deprecated; `com.jojapi/openai-sora` |
| Z9 | https://github.com/AceDataCloud/SoraMCP (commit d8ff51c 2026-11-24; README, LICENSE, CHANGELOG) ; https://pypi.org/pypi/mcp-sora/json | 4 | B | 2026-11-27 | integracja wycofana, MIT, lista narzedzi |
| Z10 | https://pypi.org/pypi/openai/json | 1 | B | 2026-11-27 | `openai` 3.60.0 z 2026-11-26 |
| Z11 | https://registry.npmjs.org/openai | 1 | B | 2026-11-27 | `openai` 7.65.0 z 2026-11-26, Apache-2.0 |
| Z12 | https://registry.npmjs.org/@infimind%2Fvideo-mcp-cli | 4 | B | 2026-11-27 | `MODEL_RETIRED` dla Sora 2 |
| Z12b | https://github.com/Doriandarko/sora-mcp (commit 8f569eb 2025-10-08) ; https://registry.npmjs.org/@iflow-mcp%2Fsora-mcp-server | 4 | B | 2026-11-27 | MCP spolecznosciowy, MIT, narzedzia |
| Z12c | https://github.com/strato-space/media-gen-mcp (commit 893feb7 2026-01-30) | 4 | B | 2026-11-27 | MCP spolecznosciowy, MIT |
| Z12d | https://github.com/airsulG/sora-mcp (commit e19a16a 2025-10-17) | 4 | B | 2026-11-27 | MCP spolecznosciowy, MIT |
| Z12e | https://github.com/nanameru/Sora2-MCP (commit 554f938 2025-10-07) | 4 | B | 2026-11-27 | MCP spolecznosciowy, MIT (package.json) |
| Z13 | https://learn.microsoft.com/en-us/azure/foundry/openai/concepts/retired-models ; https://learn.microsoft.com/en-us/azure/foundry/openai/concepts/model-retirement-schedule?view=foundry-classic ; https://learn.microsoft.com/en-us/answers/questions/6064511/sora-2-deployment-blocks-on-servicemodeldeprecated | 1 (Azure) / 4 (Q&A) | P | 2026-11-27 | wycofanie `sora-2` w Azure; rozbieznosc dat |
| Z14 | https://replicate.com/openai/sora-2 ; https://replicate.com/openai/sora-2-pro | 4 | P | 2026-11-27 | komunikat o wylaczeniu 2026-09-24 |
| Z14b | https://fal.ai/docs/model-api-reference/video-generation-api/sora-2-text-to-video ; .../sora-2-image-to-video | 4 | P | 2026-11-27 | strony dokumentacji w indeksie (stan biezacy NIEPOTWIERDZONY) |
| Z15 | https://help.openai.com/en/articles/10910291-api-organization-verification | 1 | P | 2026-11-27 | weryfikacja organizacji ogolnie "may be required" |
| Z16 | https://developers.openai.com/api/docs/guides/rate-limits | 1 | P | 2026-11-27 | ogolna struktura limitow; brak liczb dla Sora |
| Z17 | wyszukiwanie "official OpenAI MCP server Sora" (github.com, openai.com, developers.openai.com) | — | P | 2026-11-27 | brak oficjalnego MCP; repozytoria spolecznosciowe |

## 10. Dane wejsciowe do syntezy (punktacja wg zlecenia; przeliczy Evaluator)

Zasada: punkt tylko za funkcje **dostepna na 2026-11-27** potwierdzona zrodlem. Kolumna HIST pokazuje, ile model mialby przed wylaczeniem — tylko informacyjnie, nie do rankingu.

| Kryterium | Pkt max | Sora 2 na 2026-11-27 | HIST (przed 2026-09-24) | Uzasadnienie |
|---|---|---|---|---|
| Publiczne API dla zwyklego konta | 3 | 0 | 3 | API usuniete (Z1, Z2, Z5); HIST: klucz API OpenAI |
| Obraz do wideo z klatka startowa | 2 | 0 | 2 | HIST: `input_reference` (Z5, Z7) |
| Obrazy referencyjne postaci | 2 | 0 | 2 | HIST: Characters API (Z5) |
| Zadania asynchroniczne i webhook | 1 | 0 | 1 | HIST: statusy + `video.completed` (Z5, Z4) |
| Oficjalne SDK | 1 | 0 | 1 | SDK istnieje, ale metody wideo deprecated i bez backendu (Z5, Z6) |
| Oficjalny MCP (2) / spolecznosciowy (1) | 2 | 0 | 1 | oficjalnego nigdy nie bylo; spolecznosciowe bez dzialajacego backendu (Z8, Z9, Z12*) |
| Brak barier onboardingu | 1 | 0 | 0 | dzis brak dostepu; HIST: wymogi weryfikacji NIEPOTWIERDZONE, wiec 0 |
| **Suma** | 12 | **0** | **10** | |

Rekomendacja dla syntezy: umiescic Sora 2 na koncu z oznaczeniem "NIEDOSTEPNE (API wylaczone 2026-09-24)", zgodnie z RESEARCH-001 i RESEARCH-002. To nie jest decyzja produktowa (model nie jest do uzycia).

## 11. Niepewnosci

1. Dokumentacja OpenAI i Microsoft odczytana posrednio (hosty niedostepne w sieci sesji). Fakt wylaczenia jest jednak potwierdzony takze bezposrednio w kodzie obu oficjalnych SDK (Z5, Z6).
2. Faktyczny stan endpointu po 2026-09-24 nie byl sprawdzany wywolaniem (zakaz). SDK nadal pisze "is scheduled to ... shut down" (tekst sprzed daty, nie zaktualizowany).
3. Rozbieznosci historyczne bez wplywu na wniosek: dlugosc klipu (12 vs 20 s), brak rozmiaru 1080p w typie SDK mimo changelogu, daty wycofania w Azure (2026-10-15 vs 2026-11-02).
4. fal.ai: strony Sora 2 nadal w indeksie bez komunikatu o wylaczeniu — stanu nie potwierdzono.
5. `com.jojapi/openai-sora`: zakres nieznany, brak repozytorium; nie liczony.
6. Limity RPM i rownoleglosci dla Sora: BRAK DANYCH w zrodlach rzedu 1.
