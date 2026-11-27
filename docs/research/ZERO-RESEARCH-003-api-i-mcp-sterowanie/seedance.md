# ZERO-RESEARCH-003-b — Seedance (ByteDance): API, SDK, MCP i sterowanie z Claude Code

Wezel: b (Seedance). **Runda 5 z 5** (ostatnia, zgoda wlasciciela ECHO-025; naprawa zarzutu Final Control z rundy 4: rozdzielenie wymogow kanalu BytePlus i Volcengine w sekcji 8 wg zrodel Z7 i Z20 — poprawione sekcje 0, 1, 8, 9, 11). Runda 4: dodatkowe przejscie wg ECHO-019 (bezposredni odczyt Volcengine). Rola: Operator (Opus 5.5). Data odczytu wszystkich zrodel: 2026-11-27.
Kanaly dostawcy: **BytePlus ModelArk** (rynek miedzynarodowy, region `ap-southeast-1`) i **Volcengine Ark / 火山方舟** (rynek chinski).
Zakres: wylacznie odczyt dokumentacji, repozytoriow i rejestrow. NIE zalozono kont ani kluczy, NIE zainstalowano serwerow MCP, SDK, CLI ani bibliotek, NIE wykonano zadnego wywolania API Seedance ani platform posredniczacych, NIE uruchomiono kodu z repozytoriow. Zadnych kluczy i sekretow w tym pliku (w dokumentacji wystepuje tylko nazwa zmiennej `ARK_API_KEY`).

## 0. Sposob odczytu zrodel (czytac najpierw)

- **BytePlus — odczyt bezposredni.** WebFetch zwraca `getaddrinfo ENOTFOUND` (narzedzie rozwiazuje DNS poza proxy sesji), dlatego strony `docs.byteplus.com` pobrano `curl` przez proxy sesji (kod 200) i odczytano tresc dokumentu osadzona w HTML (pole `MDContent`). Metadane stron: `UpdatedTime` 2026-11-27. Kazdy adres w sekcji 9 z dopiskiem "B".
- **Volcengine — odczyt posredni.** `www.volcengine.com/docs/82379/...` przekierowuje na `docs.volcengine.com`; proxy sesji odrzuca `docs.volcengine.com`, `ark.volcengine.com`, `console.volcengine.com` (HTTP 403, 2026-11-27), WebFetch: `ENOTFOUND www.volcengine.com`. Tresc Volcengine pochodzi z indeksu wyszukiwarki ograniczonego do `volcengine.com` = **odczyt posredni**, pewnosc najwyzej `srednia`. Aby potwierdzic bezposrednio, trzeba dopuscic `docs.volcengine.com` i `ark.volcengine.com` w ustawieniach sieci sesji (ECHO-012 obejmowal tylko `www.volcengine.com`, ktory przekierowuje dalej).
- **Runda 2 — ponowna weryfikacja dostepu (2026-11-27, ok. 15:02 UTC), poprawka P2.** Wynik bez zmian: `curl` przez proxy sesji -> `docs.volcengine.com`, `ark.volcengine.com`, `console.volcengine.com`: `HTTP/1.1 403 Forbidden (agent proxy: no rule or network setting allows this host)`; `www.volcengine.com/docs/82379/1366799` -> 301 na `docs.volcengine.com` (zablokowany); WebFetch: `getaddrinfo ENOTFOUND docs.volcengine.com` oraz `ENOTFOUND docs.byteplus.com` (BytePlus nadal czytany `curl`-em, kod 200). Wniosek: hosty Volcengine **nie** sa w tej sesji dopuszczone, wbrew wytycznym wezla; tresc Volcengine pozostaje **odczytem posrednim** (Z14), pewnosc najwyzej `srednia`. Bezposredni odczyt wymaga dopuszczenia `docs.volcengine.com` i `ark.volcengine.com` w ustawieniach sieci (decyzja orkiestratora/wlasciciela, nie Operatora). Wiersze z BytePlus (rzad 1, B) nie zaleza od tej blokady.
- **Runda 4 — odczyt bezposredni Volcengine (2026-11-27, ok. 17:53 UTC).** Po dopuszczeniu hostow (ECHO-019): `curl` przez proxy sesji -> `docs.volcengine.com/docs/ark/create-video-generation-task-api?lang=zh` **HTTP 200**, `ark.volcengine.com/region:cn-beijing/docs/video-generation-tutorial` **HTTP 200**; `www.volcengine.com/docs/82379/1366799` -> 301 na `docs.volcengine.com/docs/82379/1366799` (200). WebFetch nadal zwraca `getaddrinfo ENOTFOUND docs.volcengine.com` (narzedzie rozwiazuje DNS poza proxy sesji — ta sama przyczyna co dla BytePlus), dlatego tresc pobrano `curl`-em: wersje Markdown dokumentow wskazane przez sama strone (pole `LlmsMdUrl`: `https://docs.volcengine.com/docs/zh/ark/<kod>.md`, kod 200) i porownano z polem `MDContent` w HTML (zgodne; `UpdatedTime` 2026-11-27). **Status Volcengine zmieniony: odczyt posredni -> odczyt bezposredni (B), rzad 1.** Zrodla Z14, Z20 w sekcji 9. Wynik zastepuje wpisy rund 1-2 powyzej (pozostawione jako historia).
- **Runda 5 — ponowny odczyt wymogow aktywacji obu kanalow (2026-11-27, ok. 18:19 UTC).** `curl` przez proxy sesji: `https://docs.volcengine.com/docs/zh/ark/seedance-model-activation-usage-and-refund.md` **HTTP 200** (Z20), `https://docs.byteplus.com/en/docs/modelark/seedance-model-activation-usage-and-refund` **HTTP 200** (Z7); `https://docs.volcengine.com/docs/zh/ark/quick-start.md` **HTTP 200**. Wynik: strona Volcengine (linie 7-13 pliku .md; kroki aktywacji l. 17-19) podaje prog **200 元 (CNY)** dla salda konta, planu oszczednosciowego i pakietu zasobow, aktywacje w konsoli `ark.volcengine.com` ("开通管理") i klucz w "API Key 管理"; odsyla do konsol `console.volcengine.com` i **nie wspomina o koncie BytePlus ani o progu w USD**. Strona BytePlus podaje prog **USD 30** ("Pay by Credits", AI Savings Plan, pakiet zasobow) i konsole `console.byteplus.com`. Na tej podstawie sekcja 8 rozdziela wymogi obu kanalow (naprawa zarzutu z rundy 4).
- **Rejestry i repozytoria — odczyt bezposredni:** oficjalny rejestr MCP (`registry.modelcontextprotocol.io`), PyPI JSON, npm registry, `proxy.golang.org`, Maven Central (`repo1.maven.org`), repozytoria GitHub przez `git clone --depth 1 --filter=blob:none --no-checkout` do katalogu tymczasowego (tylko `git log` i `git show` plikow README/LICENSE/pyproject; bez checkoutu, bez uruchamiania). API GitHub dla organizacji niedostepne w sesji (odpowiedz: sesja ograniczona do skonfigurowanych repozytoriow).

## 1. Publiczne API (REST) — dostepnosc dla zwyklego konta

| Pytanie | Odpowiedz | Zrodlo | Pewnosc |
|---|---|---|---|
| Czy istnieje publiczne API REST | **TAK** — BytePlus ModelArk "Video Generation API": `POST https://ark.ap-southeast.bytepluses.com/api/v3/contents/generations/tasks`; modele m.in. `dreamina-seedance-2-5-260628`, `dreamina-seedance-2-5-flash-261115`, `dreamina-seedance-2-0-260128`, `-2-0-fast-260128`, `-2-0-mini-260615`, `seedance-1-0-pro-250528`, `seedance-1-0-pro-fast-251015` | Z1, Z5 | wysoka |
| Volcengine (Chiny) | **TAK** (runda 4: odczyt bezposredni): `POST https://ark.cn-beijing.volces.com/api/v3/contents/generations/tasks`; uwierzytelnianie API Key (`Authorization: Bearer $ARK_API_KEY`) lub Access Key (wtedy `model` = Endpoint ID); modele `doubao-seedance-2-5-260628`, `doubao-seedance-2-5-flash-261115`, `doubao-seedance-2-0-260128`, `-2-0-fast-260128`, `-2-0-mini-260615`; osobny adres dla klucza "Agent Plan" (abonament): `https://ark.cn-beijing.volces.com/api/plan/v3/contents/generations/tasks` (wymaga klucza Agent Plan i "专属 Base URL") | Z14, Z20 | wysoka |
| Prog aktywacji Seedance 2.x (Volcengine) | Jeden z warunkow: saldo konta >= **200 CNY** ("账户可用余额达到 200 元"), albo plan oszczednosciowy >= 200 CNY z saldem (200 CNY: 30 dni; 500/1000 CNY: 90 dni), albo pakiet zasobow Seedance 2.0/2.5 >= 200 CNY z pozostalym limitem (90 dni); potem aktywacja modelu w konsoli `ark.volcengine.com` ("开通管理") i klucz na stronie "API Key 管理". Doladowanie i rozliczenie w konsoli `console.volcengine.com` (konto Volcengine); strona **nie wymienia** konta BytePlus ani progu w USD (runda 5) | Z14, Z20 | wysoka |
| Jak uzyskac dostep (BytePlus) | (1) konto BytePlus i logowanie ("Register an account"); (2) aktywacja modelu na stronie Model activation; (3) utworzenie klucza na stronie API Keys ("Create API Key"); klucz w zmiennej `ARK_API_KEY` | Z4, Z7, Z8 | wysoka |
| Uwierzytelnianie | "This API supports only API Key authentication" — naglowek `Authorization: Bearer $ARK_API_KEY` | Z1, Z4 | wysoka |
| Prog aktywacji Seedance 2.x (BytePlus) | Jeden z warunkow: saldo konta > **30 USD** ("If you are verified to use Pay by Credits ... balance ... reaches USD 30"), albo AI Savings Plan >= 30 USD, albo pakiet zasobow Seedance >= 30 USD; kredytow, planu i pakietu nie mozna wycofac/anulowac | Z7, Z1 | wysoka |
| Konto indywidualne | **TAK** — tabela limitow rozroznia "Individual" i "Enterprise" (indywidualne: nizsze limity), czyli konto indywidualne moze wywolywac API | Z3 | wysoka |
| Weryfikacja / lista oczekujacych | Listy oczekujacych **brak** w odczytanych zrodlach. Sformulowanie "if you are verified to use Pay by Credits" wskazuje na weryfikacje uprawnienia do platnosci kredytowej — zakres tej weryfikacji **NIEPOTWIERDZONY** (strona rozliczen BytePlus nieodczytana) | Z7 | niska |
| Ograniczenia regionalne | API BytePlus w regionie `ap-southeast-1` (jedyny adres bazowy w dokumentacji). Ograniczenia rejestracji wg kraju — **NIEPOTWIERDZONE** (brak w odczytanych zrodlach). Volcengine: region `cn-beijing` (jedyny adres bazowy w odczytanych stronach: `https://ark.cn-beijing.volces.com/api/v3`); wymogi konta (np. weryfikacja tozsamosci, dostep spoza Chin) — w odczytanych bezposrednio stronach (quick-start, Base URL i uwierzytelnianie, aktywacja) **brak wzmianki**, wiec **NIEPOTWIERDZONE** | Z1, Z4, Z20 | niska |
| Ograniczenie tresci istotne dla projektu | Seedance 2.5 i 2.0 **nie przyjmuja bezposrednio obrazow/wideo referencyjnych z prawdziwymi twarzami**; obejscia: (a) wyniki z twarzami wygenerowane na tym samym koncie (Seedance 2.x, Seedream 5.0) zaufane przez 30 dni, (b) gotowe "digital characters" (`asset://<ID>`), (c) zasoby prawdziwych osob po weryfikacji i autoryzacji osoby | Z1, Z9 | wysoka |
| Stan na 2026-11-27 | **Aktywne**: dokumentacja zaktualizowana 2026-11-27; "Dreamina Seedance 2.5 ... are now fully available" | Z1 | wysoka |

## 2. Model pracy (asynchronicznosc)

- **Zadanie asynchroniczne: TAK.** "The video generation task creation is an asynchronous API." POST zwraca `id` zadania; status: `GET https://ark.ap-southeast.bytepluses.com/api/v3/contents/generations/tasks/{id}`. Z1, Z2.
- **Statusy:** `queued`, `running`, `succeeded`, `failed`, `expired`, `cancelled` (anulowac mozna tylko zadanie `queued`; rekord anulowanego zadania usuwany po 24 h). Z2.
- **Lista zadan:** `GET .../contents/generations/tasks?page_num=&page_size=&filter.status=&filter.task_ids=&filter.model=`. Z6.
- **Anulowanie/usuniecie:** `DELETE https://ark.ap-southeast.bytepluses.com/api/v3/contents/generations/tasks/{id}` — runda 4: potwierdzone na stronie referencyjnej BytePlus "cancel-or-delete-video-generation-tasks-api" (pole `MDContent`, `UpdatedTime` 2026-11-27) oraz Volcengine `DELETE https://ark.cn-beijing.volces.com/api/v3/contents/generations/tasks/{id}`: `queued` -> `cancelled`; `running` — nie; `succeeded`/`failed`/`cancelled`/`expired` — usuniecie rekordu. Z5, Z21, Z20. Pewnosc: wysoka.
- **Volcengine (runda 4, odczyt bezposredni):** ten sam model pracy — "创建视频生成任务为**异步接口**", `GET https://ark.cn-beijing.volces.com/api/v3/contents/generations/tasks/{id}`, lista `GET .../tasks` z filtrami, `callback_url` (POST przy zmianie statusu, 3 ponowienia po 5 s dla `succeeded`/`failed`), `execution_expires_after` 172800 s (zakres 3600-259200), `priority` 0-9, `video_url` wazny 24 h (Seedance 2.5: maks. 100 pobran). Z14, Z20. Pewnosc: wysoka.
- **Webhook/callback: TAK.** Parametr `callback_url`: "When the status of the video generation task changes, ModelArk will send a POST request to this address"; tresc jak odpowiedz GET; przy braku potwierdzenia w 5 s — 3 ponowienia (dla `succeeded`/`failed`); wymaga wlasnego publicznego serwera. Z1, Z5.
- **Wygasanie:** `execution_expires_after` domyslnie 172800 s (48 h), zakres 3600-259200 s. ID zadania wazne 7 dni (Draft: 14 dni dla ID od 2026-10-28). Z1, Z2.
- **Pobranie wyniku:** `content.video_url` w odpowiedzi GET — **wazny 24 h**; opcjonalnie `return_last_frame: true` -> URL ostatniej klatki (24 h) do lancuchowania klipow. Z2, Z1.
- **Priorytet kolejki:** `priority` (domyslnie 0) zmienia tylko kolejnosc zadan `queued`. Z1.

## 3. Limity (BytePlus, tryb domyslny online)

| Model | Maks. RPM | Maks. zadan rownoleglych | Zrodlo | Pewnosc |
|---|---|---|---|---|
| Seedance 2.5, 2.5 flash, 2.0 mini, 2.0 fast | Enterprise 600 / **Individual 180** | Enterprise 10 / **Individual 3** | Z3 | wysoka |
| Seedance 2.0 (bez 4K) | Enterprise 600 / Individual 180 | Enterprise 10 / Individual 3 | Z3 | wysoka |
| Seedance 2.0 4K | 15 (wszyscy) | 1 (wszyscy) | Z3 | wysoka |
| Seedance 1.0 pro / pro fast | 600 | 10 (+ tryb flex: TPD 500B) | Z3 | wysoka |

Uwagi: "The rate limits in this document are theoretical maximum values. Actual limits depend on platform load" (Z3). Tryb `service_tier=flex` (offline, 50% ceny) — nieobslugiwany dla serii 2.5 i 2.0 (Z1). Limity Volcengine (runda 4, odczyt bezposredni, strona "model-list"): `doubao-seedance-2-5-260628` i `doubao-seedance-2-0-260128` bez 4K — RPM 企业用户 600 / 个人用户 **180**, wspolbieznosc 10 / **3**; 4K — RPM 15, wspolbieznosc 1 (wszyscy); `-2-5-flash-261115`, `-2-0-fast-260128`, `-2-0-mini-260615` — RPM 600/180, wspolbieznosc 10/3 (Z20, pewnosc wysoka). Wartosci identyczne z BytePlus.

## 4. Zakres API wzgledem aplikacji

| Funkcja | API (BytePlus ModelArk) | Zrodlo | Pewnosc |
|---|---|---|---|
| Tekst do wideo | TAK — wszystkie modele; `content` = `[{type:"text", text:...}]` | Z1 | wysoka |
| Obraz do wideo — klatka startowa | TAK — wszystkie modele; `image_url` z `role: "first_frame"` (lub bez roli) | Z1 | wysoka |
| Obraz do wideo — klatka startowa i koncowa | TAK — Seedance 2.5 (obie), 2.0 (wszystkie), 1.0 pro; `role: "first_frame"` + `role: "last_frame"`; 1.0 pro fast — tylko klatka startowa | Z1 | wysoka |
| Obrazy referencyjne postaci/obiektow | TAK — "omni reference-to-video": `role: "reference_image"`; Seedance 2.5: 1-30 obrazow, 2.5 flash: 1-10, 2.0: 1-9; plus `reference_video` (2.5: do 10, 2.0: do 3) i `reference_audio`. Tryby first/last frame i reference **nie lacza sie** w jednym zadaniu. Prawdziwe twarze — tylko przez zasoby `asset://` (sekcja 1) | Z1, Z9 | wysoka |
| Przedluzanie klipu | TAK — Seedance 2.5 i 2.0: `omni_reference_task_type: "extend"` (2.5), `reference_video` + intencja w prompcie ("Extend @Video 1 ..."), `ratio` tylko `adaptive`; takze edycja wideo (`edit`). Laczna dlugosc wideo wejsciowych: 2.5 <= 30 s, 2.0 <= 15 s | Z1, Z10 | wysoka |
| Audio | `generate_audio` (domyslnie `true`; Seedance 2.5 i 2.0): mowa, efekty i muzyka zsynchronizowane z obrazem, stereo; `false` = wideo bez dzwieku. Brak osobnego parametru wylaczenia samej muzyki w odczytanych zrodlach | Z1 | wysoka |
| Rozdzielczosc | 2.5 i 2.0: `480p`, `720p`, `1080p`, `4k` (domyslnie 720p); 2.5 flash, 2.0 fast, 2.0 mini: 480p/720p; 1.0: do 1080p. 1080p 16:9 = 1920x1080 (2.x) | Z1, Z3 | wysoka |
| Dlugosc | 2.5: 4-30 s lub `-1` (auto); 2.0: 4-15 s lub `-1`; 1.0: 2-12 s (`frames` 29-289) | Z1, Z3 | wysoka |
| Proporcje | `ratio`: `16:9`, `4:3`, `1:1`, `3:4`, `9:16`, `21:9`, `adaptive` (w 2.5 dla I2V/extend/edit tylko `adaptive`) | Z1 | wysoka |
| Seed | TAK — `seed` (domyslnie -1 = losowy); ten sam seed daje "similar results", bez gwarancji identycznosci | Z1 | wysoka |
| Inne | `watermark` (domyslnie false), `output_format` `mp4`/`mov`, `draft` (podglad 480p, potem final z `draft_task.id`), `camera_fixed`, jezyki promptu (2.5: EN + 9 innych, bez polskiego) | Z1 | wysoka |

## 5. Oficjalne SDK lub CLI

| Element | Stan | Szczegoly | Zrodlo | Pewnosc |
|---|---|---|---|---|
| Python | **TAK** — `arkruntime` (`pip install --upgrade arkruntime`, `from arkruntime import Ark`, `client.content_generation.tasks.create/get`); Python >= 3.8 | PyPI 0.23.0 z 2026-11-23; repo `github.com/volcengine/ark-runtime-python`, ostatni commit 2026-11-23 (31b3c27); **Apache-2.0** | Z4, Z11 | wysoka |
| Go | **TAK** — `github.com/volcengine/ark-runtime-go` (Go >= 1.20) | proxy.golang.org v0.24.0 z 2026-11-23; ostatni commit 2026-11-23 (6d65880); **Apache-2.0** | Z4, Z11 | wysoka |
| Java | **TAK** — Maven `com.volcengine:ark-runtime` (Java >= 1.8) | Maven Central latest 0.20.0, lastUpdated 2026-11-26; repo `volcengine/ark-runtime-java`, commit 2026-11-26 (a19b85d); **Apache-2.0** | Z4, Z11 | wysoka |
| OpenAI SDK | dokumentacja dopuszcza `openai` dla tekstu; dla wideo przyklady uzywaja `arkruntime` | — | Z4 | srednia |
| Oficjalne CLI | **TAK** (korekta w rundzie 4; wczesniej "nie znaleziono"). BytePlus: "Ark CLI is the official command-line tool for BytePlus ModelArk" — `npm install -g @byteplus/ark-cli`, polecenie `arkcli`, Node.js >= 16, logowanie `arkcli auth login`, generowanie `arkcli +gen` (obraz i wideo z tekstu, obrazow lub zasobow referencyjnych), `arkcli +connect` instaluje umiejetnosci (skills) w agentach "such as Claude Code". Volcengine: `@volcengine/ark-cli` (ta sama funkcja; przyklady `arkcli +gen "..." --modality video --duration 5 --ratio 16:9 [--wait --save-to ./out]`, `arkcli gen get <id>`, `arkcli gen list`, `arkcli gen delete <id>`) | npm `@byteplus/ark-cli` 1.0.70 opublikowany 2026-11-27, licencja Apache-2.0, repo `github.com/byteplus-sdk/ark-cli` (commit 002e597, 2026-11-11, LICENSE Apache-2.0); npm `@volcengine/ark-cli` 1.0.70 z 2026-11-27, Apache-2.0, repo `github.com/volcengine/ark-cli` (commit 3b51e44, 2026-11-11; repo zawiera `skills/`, `dsh-plugins/`, README i LICENSE) | Z22 | wysoka (dokumentacja dostawcy + rejestr npm + repo); dzialania nie sprawdzano (zakaz instalacji) |

Uwaga: SDK sa publikowane pod marka Volcengine (`volcengine/*`, `com.volcengine`), a dokumentacja BytePlus wprost je instaluje z adresem bazowym `https://ark.ap-southeast.bytepluses.com/api/v3` — status oficjalny potwierdza dokumentacja dostawcy (Z4).

## 6. Serwer MCP

### 6.1 Oficjalny (dostawca)

| Pole | Wartosc | Zrodlo |
|---|---|---|
| Wpis w oficjalnym rejestrze MCP | **BRAK** — wyszukiwanie `byteplus`: 0 wynikow; `seedance`, `volcengine`, `bytedance`, `dreamina`: tylko podmioty trzecie lub serwery niezwiazane z wideo (`io.github.bytedance/mcp-server-browser` itp.) | Z12 |
| Dokumentacja BytePlus | Brak serwera MCP dla Seedance; "MCP" wystepuje tylko jako funkcja modeli tekstowych (wywolywanie zdalnych MCP przez LLM) | Z3, Z4 |
| Volcengine `volcengine/mcp-server` (oficjalne repo, MIT, commit 2026-11-23, 567b960) | Zawiera ok. 80 serwerow uslug chmurowych; `mcp_server_ark` = rozmowa z "零代码应用" (bot_chat, web_search, link_reader, caculator) — **bez generowania wideo**; README `mcp_server_vod`, `mcp_server_veimagex` bez Seedance; `mcp_server_mediakit` — montaz/narracja, nie Seedance | Z13 |
| Ocena | **Oficjalny serwer MCP Seedance: NIE ISTNIEJE** (stan 2026-11-27, w zbadanych rejestrach i dokumentacji) | Z12, Z13, Z3 |

### 6.2 Polooficjalny — oznaczony osobno (do rozstrzygniecia w syntezie)

| Nazwa | Repozytorium | Licencja | Ostatnia aktywnosc | Backend i narzedzia | Status |
|---|---|---|---|---|---|
| Ark Seed Multimodal MCP Server (`ark-mcp`, serwer `ark-seed`) | github.com/byteplus-sa/ark-mcp (tagi v0.2.0-v0.5.0) | MIT ("Copyright (c) 2026 Ark Seed MCP Server contributors") | commit 2026-11-27 (8a9977a, = tag v0.5.0) | BytePlus ModelArk bezposrednio (klucz `ARK_API_KEY` w pliku .env); stdio lub HTTP; 32 narzedzia, w tym `seedance_create_task` (2.5, 2.5 flash, 2.0; `first_frame`/`last_frame`/`reference_image`/`reference_video`/`reference_audio`), `gen_task_get`, `gen_task_list`, `gen_task_cancel_or_delete`, `ark_asset_*` (zasoby portretowe), `seed_media_get_artifact`, `ark_job_submit/get/cancel`, `ark_list_models`; instrukcja dla Claude Code: `claude mcp add ark-seed --transport stdio ...` | Autor w `pyproject.toml` z adresem `@bytedance.com`; SECURITY.md odsyla do "BytePlus/ByteDance maintainer channel". **Brak** wpisu w oficjalnym rejestrze MCP, **brak** odnosnika w dokumentacji BytePlus, PyPI "not configured". Traktowac jako **rzad 4 — NIEPOTWIERDZONE jako oficjalny** |
| Seed MCP (`seed-mcp`) | github.com/byteplus-sa/seed-mcp | MIT | commit 2026-11-27 (7a693e4) | pochodna `ark-mcp` (hostowany, wielodostepny, klucz uzytkownika); `seedance_create_task`, `gen_task_get/list/cancel_or_delete` | jw. — rzad 4, NIEPOTWIERDZONE |

### 6.3 Spolecznosciowe (rzad 4 — NIEPOTWIERDZONE co do jakosci)

| Nazwa | Repozytorium / rejestr | Licencja | Ostatnia aktywnosc | Backend i zakres narzedzi |
|---|---|---|---|---|
| seedance-mcp (atharva3vedi) | github.com/atharva3vedi/seedance-mcp | MIT | commit 2026-10-14 (f541519) | BytePlus ModelArk, wlasny `ARK_API_KEY`; `claude mcp add seedance ... uvx --from git+https://github.com/atharva3vedi/seedance-mcp seedance-mcp --budget 50`; narzedzia m.in. `generate_video`, `video_task`, `list_video_tasks`, `cancel_video_task`, `estimate_cost`, `spend_status`, `preapprove_spend`, `generate_image`, `check_setup`; straznik wydatkow; deklaruje brak afiliacji z ByteDance/BytePlus |
| AceDataCloud SeedanceMCP (`mcp-seedance` PyPI; `io.github.AceDataCloud/mcp-seedance` w oficjalnym rejestrze) | github.com/AceDataCloud/SeedanceMCP | MIT | commit 2026-11-27 (6b7c226); PyPI 2026.11.27.0 z 2026-11-27 | Posrednik AceDataCloud (`ACEDATACLOUD_API_TOKEN`, nie klucz BytePlus); hostowany `https://seedance.mcp.acedata.cloud/mcp` lub stdio; `seedance_generate_video`, `seedance_generate_video_from_image`, `seedance_get_task`, `seedance_get_tasks_batch`, `seedance_list_models`, `seedance_list_resolutions`, `seedance_list_actions` |
| seedance-2-mcp (leonaiuv) | github.com/leonaiuv/seedance-2-mcp | MIT | commit 2026-05-02 (fdf1157) | Volcengine Ark (`ARK_API_KEY`, domyslnie `https://ark.cn-beijing.volces.com/api/v3`, adres nadpisywalny); `seedance_create_task`, `seedance_check_task`, `seedance_usage_guide` |
| volcengine-ark-media-mcp (MrLinWang; npm; `io.github.MrLinWang/volcengine-ark-media-mcp` w rejestrze) | github.com/MrLinWang/volcengine-ark-media-mcp | MIT | commit 2026-11-20 (1c6b3cb); npm 1.0.0 z 2026-11-20 | Volcengine "Agent Plan" (`ARC_AGENT_PLAN_KEY`); `ark_create_video_task`, `ark_get_video_task`, `ark_wait_video_task`, `ark_list_video_tasks`, `ark_delete_video_task` + obraz/TTS/ASR; README: plan "Medium" nie obsluguje wideo |
| seedream-mcp (nsmao-com) | github.com/nsmao-com/seedream-mcp | MIT | commit 2026-03-05 (5f322f2) | Volcengine Ark (`ARK_API_KEY`); generowanie obrazu i wideo (asynchroniczne, `callback_url`, polling), stdio/http; domyslny model wideo starszej generacji |
| seedance-mcp (npm, opiekun `super7ao`) | tylko npm `seedance-mcp` 1.1.1 (2026-05-23), brak repozytorium w metadanych | MIT (npm) | 2026-05-23 | opis: Seedance dla Claude Code; zakresu narzedzi nie zweryfikowano — NIEPOTWIERDZONE |
| volcengine-video-mcp (PyPI) | tylko PyPI 0.1.1 (2025-11-06), brak adresu repozytorium | MIT (PyPI) | 2025-11-06 — **nieaktywny ok. 12 mies.** | Volcengine (Doubao) Video Generation API; narzedzi nie zweryfikowano |
| KreatorFlow (`ai.kreatorflow/seedance-api`, rejestr) | brak repozytorium; zdalny `https://kreatorflow.ai/v1/mcp` | NIEPOTWIERDZONE | wpis 1.0.1 z 2026-10-18 | posrednik KreatorFlow (wlasny klucz); Seedance 2.5/2.0 |
| useapi.net Dreamina (`net.useapi/dreamina`, rejestr) | brak repozytorium; zdalny `https://api.useapi.net/v1/dreamina/mcp` | NIEPOTWIERDZONE | wpis 1.0.1 z 2026-11-21 | posrednik do aplikacji Dreamina (CapCut); Seedance 2.5/2.0 |

Nie liczyc jako MCP: `tomaibuilder/seedance-clip-skill` (Skill Claude Code, nie serwer MCP; brak pliku LICENSE; commit 2026-10-19).

## 7. Alternatywne drogi dostepu do modeli Seedance (platformy posredniczace)

Tylko wymienione z dowodem dostepnosci, bez porownywania cen:
- **Volcengine Ark (ByteDance, Chiny)** — drugi kanal dostawcy, nie posrednik; dowod bezposredni od rundy 4 (Z14, Z20); w tym abonament "Agent Plan" z osobnym adresem `.../api/plan/v3`.
- **AceDataCloud** — PyPI `mcp-seedance` 2026.11.27.0 i wpis w oficjalnym rejestrze MCP (Z15, Z12). Rzad 4.
- **KreatorFlow** — wpis `ai.kreatorflow/seedance-api` w oficjalnym rejestrze MCP (Z12). Rzad 4.
- **useapi.net (Dreamina)** — wpis `net.useapi/dreamina` w oficjalnym rejestrze MCP (Z12). Rzad 4.
- **fal.ai** — odczyt posredni (indeks wyszukiwarki ograniczony do fal.ai): endpointy `bytedance/seedance-2.0/image-to-video`, `bytedance/seedance-2.0/fast/image-to-video`, `.../fast/reference-to-video` (Z16). Seedance 2.5 na fal.ai — NIEPOTWIERDZONE. Rzad 4.
- **Replicate** — odczyt posredni: strona `replicate.com/bytedance/seedance-2.0-fast` (Z16). Rzad 4.

## 8. Minimalna sciezka sterowania z Claude Code

**(a) Przez serwer MCP — DOSTEPNA tylko spolecznosciowo/polooficjalnie (brak oficjalnego):**
- Najblizej dostawcy: `byteplus-sa/ark-mcp` (stdio, klucz BytePlus w pliku .env): `claude mcp add ark-seed --transport stdio --scope user --env ARK_MCP_ENV_FILE=<sciezka> ... -- uv --directory <checkout> run --locked --no-sync python -m ark_mcp`, potem `/mcp` -> `ark-seed`. Narzedzia: `ark_list_models` -> (opcjonalnie `media_upload`) -> `seedance_create_task` (przez `ark_job_submit` w tle) -> `gen_task_get` -> `seed_media_get_artifact` / `seed_media_export_artifact` (Z17).
- Prostsza alternatywa: `atharva3vedi/seedance-mcp` przez `uvx` (Z18): `generate_video` -> `video_task` -> pobranie `video_url`.
- Wszystkie: rzad 4, NIEPOTWIERDZONE co do jakosci. Wymogi zaleza od backendu serwera: serwery na BytePlus ModelArk (`ark-mcp`, `seed-mcp`, `atharva3vedi/seedance-mcp`) — konto BytePlus, aktywacja modelu z progiem 30 USD (Z7) i klucz API BytePlus; serwery na Volcengine Ark (`leonaiuv/seedance-2-mcp`, `seedream-mcp`, `volcengine-ark-media-mcp`) — konto Volcengine, aktywacja z progiem 200 CNY (Z20) i klucz API Volcengine (lub klucz Agent Plan); serwery posrednikow — token posrednika.

**(b) Przez HTTP/SDK z narzedzia powloki — DOSTEPNA (oficjalna):**
1. `POST https://ark.ap-southeast.bytepluses.com/api/v3/contents/generations/tasks`, naglowek `Authorization: Bearer $ARK_API_KEY`; cialo: `model` (np. `dreamina-seedance-2-5-260628`), `content` (`text`; `image_url` z `role` `first_frame`/`last_frame` albo `reference_image`; `video_url`/`audio_url` z `role` `reference_*`), `resolution`, `ratio`, `duration`, `seed`, `generate_audio`, `return_last_frame`, opcjonalnie `callback_url`, `execution_expires_after`.
2. Polling: `GET .../contents/generations/tasks/{id}` do `status=succeeded`; lista: `GET .../contents/generations/tasks?filter.status=...`; anulowanie: `DELETE .../contents/generations/tasks/{id}`.
3. Pobranie `content.video_url` (i `last_frame_url`) w ciagu 24 h.
SDK: `arkruntime` (`client.content_generation.tasks.create(...)` / `.get(task_id=...)`), Go `ark-runtime-go`, Java `ark-runtime` (Z4).
Wariant oficjalnego CLI (runda 4, Z22): `arkcli` (`@byteplus/ark-cli`) z narzedzia powloki — `arkcli auth login`, potem `arkcli +gen "<prompt>" --modality video --duration 5 --ratio 16:9 --wait --save-to ./out` (skladnia z dokumentacji Volcengine; dokumentacja BytePlus potwierdza `arkcli +gen` dla wideo), `arkcli gen get|list|delete`; `arkcli +connect` instaluje skills dla Claude Code (nie jest to serwer MCP). Nie instalowano i nie uruchamiano.
Wymogi wstepne — osobno dla kazdego kanalu (runda 5, naprawa zarzutu Final Control):
- **Kanal BytePlus ModelArk** (adres `https://ark.ap-southeast.bytepluses.com/api/v3`): konto BytePlus; aktywacja modelu przy saldzie "Pay by Credits" >= **30 USD** albo AI Savings Plan >= 30 USD, albo pakiecie zasobow Seedance >= 30 USD; klucz API BytePlus (strona API Keys). Zrodla: Z7, Z4, Z1.
- **Kanal Volcengine Ark** (adres `https://ark.cn-beijing.volces.com/api/v3`, model np. `doubao-seedance-2-5-260628`; albo `.../api/plan/v3` z kluczem Agent Plan i "专属 Base URL"): te same kroki 1-3 (POST, GET, DELETE `/contents/generations/tasks`); aktywacja modelu w "开通管理" przy saldzie konta >= **200 CNY** albo planie oszczednosciowym >= 200 CNY, albo pakiecie zasobow Seedance 2.0/2.5 >= 200 CNY; klucz API z "API Key 管理"; rozliczenie w konsoli Volcengine (`console.volcengine.com`). Zrodlo Z20 (`seedance-model-activation-usage-and-refund.md`, l. 7-13 progi, l. 17-19 aktywacja i klucz) nie wymaga konta BytePlus. Wymogi rejestracji konta Volcengine (weryfikacja tozsamosci, dostep spoza Chin) — NIEPOTWIERDZONE (brak w odczytanych stronach). Zrodla: Z14, Z20.
Webhook wymaga publicznego serwera — z Claude Code praktyczny jest polling.

**(c) Brak sterowania — NIE dotyczy** (droga (b) istnieje oficjalnie).

## 9. Zrodla

Rzad: 1 = dokumentacja/repozytorium/rejestr/pakiet dostawcy; 4 = spolecznosc/posrednicy (NIEPOTWIERDZONE co do jakosci). Sposob: B = odczyt bezposredni; P = odczyt posredni (indeks wyszukiwarki, host zablokowany).

| ID | URL | Rzad | Sposob | Data odczytu | Co potwierdza |
|---|---|---|---|---|---|
| Z1 | https://docs.byteplus.com/en/docs/modelark/create-video-generation-task-api (z /docs/ModelArk/1520757) | 1 | B | 2026-11-27 | endpoint POST, API Key, prog 30 USD, role obrazow, `generate_audio`, `resolution`, `ratio`, `duration`, `seed`, `callback_url`, `execution_expires_after`, `draft`, `return_last_frame`, zakaz prawdziwych twarzy |
| Z2 | https://docs.byteplus.com/en/docs/modelark/get-video-generation-task-api (z /docs/ModelArk/1521309) | 1 | B | 2026-11-27 | GET `/tasks/{id}`, statusy, `video_url` 24 h, ID 7 dni |
| Z3 | https://docs.byteplus.com/en/docs/modelark/model-list | 1 | B | 2026-11-27 | RPM i wspolbieznosc Individual/Enterprise, rozdzielczosci, dlugosci, MCP tylko dla LLM |
| Z4 | https://docs.byteplus.com/en/docs/modelark/quick-start | 1 | B | 2026-11-27 | klucz API, `ARK_API_KEY`, SDK Python/Go/Java, przyklad wideo z pollingiem |
| Z5 | https://docs.byteplus.com/en/docs/modelark/video-generation-tutorial | 1 | B | 2026-11-27 | webhook (`callback_url`, przyklad serwera), polling, `DELETE .../tasks/<TASK_ID>` |
| Z6 | https://docs.byteplus.com/en/docs/modelark/list-video-generation-tasks-api | 1 | B | 2026-11-27 | GET lista zadan z filtrami |
| Z7 | https://docs.byteplus.com/en/docs/modelark/seedance-model-activation-usage-and-refund | 1 | B | 2026-11-27 (ponownie odczytana w rundzie 5, HTTP 200) | warunki aktywacji kanalu BytePlus 30 USD (saldo, AI Savings Plan, pakiet), "verified to use Pay by Credits", brak zwrotow |
| Z8 | https://docs.byteplus.com/en/docs/modelark/seedance-2-5 (= /docs/ModelArk/2607688) ; https://docs.byteplus.com/en/docs/modelark/seedance-2-0 (= /docs/ModelArk/2291680) | 1 | B | 2026-11-27 | rejestracja konta, klucz, typy zadan, extend/edit |
| Z9 | https://docs.byteplus.com/en/docs/modelark/seedance-portrait-asset-guide | 1 | B | 2026-11-27 | zasoby portretowe `asset://`, zaufane wyniki 30 dni, autoryzowane osoby |
| Z10 | = Z8 (sekcja Video extension, `omni_reference_task_type: extend`) | 1 | B | 2026-11-27 | przedluzanie klipu |
| Z11 | https://pypi.org/pypi/arkruntime/json ; https://proxy.golang.org/github.com/volcengine/ark-runtime-go/@latest ; https://repo1.maven.org/maven2/com/volcengine/ark-runtime/maven-metadata.xml ; github.com/volcengine/ark-runtime-python (31b3c27), -go (6d65880), -java (a19b85d) + pliki LICENSE | 1 | B | 2026-11-27 | wersje, daty, Apache-2.0 |
| Z12 | https://registry.modelcontextprotocol.io/v0/servers?search=seedance (oraz `byteplus`, `volcengine`, `bytedance`, `ark`, `dreamina`) | 1 (rejestr) | B | 2026-11-27 | brak oficjalnego wpisu; wpisy AceDataCloud, KreatorFlow, useapi, MrLinWang, ExpertVagabond |
| Z13 | https://github.com/volcengine/mcp-server (commit 567b960; `server/mcp_server_ark/README.md`, README vod/mediakit/veimagex) | 1 | B | 2026-11-27 | oficjalne MCP Volcengine bez Seedance |
| Z14 | https://docs.volcengine.com/docs/ark/create-video-generation-task-api?lang=zh (= .md: https://docs.volcengine.com/docs/zh/ark/create-video-generation-task-api.md) ; https://ark.volcengine.com/region:cn-beijing/docs/video-generation-tutorial (= .md: https://docs.volcengine.com/docs/zh/ark/video-generation-tutorial.md) ; https://www.volcengine.com/docs/82379/1366799 (301 -> docs.volcengine.com) | 1 | **B** (runda 4; rundy 1-2: P) | 2026-11-27 | endpoint POST `ark.cn-beijing.volces.com/api/v3/contents/generations/tasks`, API Key, prog 200 CNY, role `first_frame`/`last_frame`/`reference_image`/`reference_video`/`reference_audio`, `resolution`, `duration`, `generate_audio`, `callback_url`, `execution_expires_after`, `priority`, `draft`, `return_last_frame`, async, zakaz prawdziwych twarzy |
| Z20 | https://docs.volcengine.com/docs/zh/ark/ + `model-list.md`, `base-url-and-authentication.md`, `get-video-generation-task-api.md`, `list-video-generation-tasks-api.md`, `cancel-or-delete-video-generation-tasks-api.md`, `seedance-model-activation-usage-and-refund.md`, `quick-start.md`, `agent-plan-personal-visual-models.md` | 1 | B | 2026-11-27 (aktywacja ponownie odczytana w rundzie 5, HTTP 200) | RPM/wspolbieznosc 个人/企业, Base URL i uwierzytelnianie, GET/lista/DELETE, `video_url` 24 h, prog 200 CNY (saldo, plan, pakiet; l. 7-13, aktywacja l. 17-19 pliku `seedance-model-activation-usage-and-refund.md`) bez wzmianki o koncie BytePlus, konsola `console.volcengine.com`, adres Agent Plan `.../api/plan/v3` |
| Z21 | https://docs.byteplus.com/en/docs/modelark/cancel-or-delete-video-generation-tasks-api | 1 | B | 2026-11-27 | `DELETE .../contents/generations/tasks/{id}` (BytePlus) |
| Z22 | https://docs.byteplus.com/en/docs/modelark/ark-cli ; https://docs.volcengine.com/docs/zh/ark/ark-cli.md ; https://docs.volcengine.com/docs/zh/ark/agent-plan-personal-ark-cli.md ; https://registry.npmjs.org/@byteplus%2fark-cli ; https://registry.npmjs.org/@volcengine%2fark-cli ; github.com/byteplus-sdk/ark-cli (002e597) ; github.com/volcengine/ark-cli (3b51e44) | 1 | B | 2026-11-27 | oficjalne CLI `arkcli`, wersja 1.0.70, Apache-2.0, `+gen` wideo, `+connect` dla Claude Code |
| Z15 | https://pypi.org/pypi/mcp-seedance/json ; https://github.com/AceDataCloud/SeedanceMCP (6b7c226) | 4 | B | 2026-11-27 | MCP AceDataCloud |
| Z16 | https://fal.ai/models/bytedance/seedance-2.0/image-to-video/api ; https://fal.ai/models/bytedance/seedance-2.0/fast/reference-to-video ; https://replicate.com/bytedance/seedance-2.0-fast | 4 | P | 2026-11-27 | Seedance 2.0 na fal.ai i Replicate |
| Z17 | https://github.com/byteplus-sa/ark-mcp (8a9977a; README.md, LICENSE, pyproject.toml, SECURITY.md, docs/integrations/claude-code.md) ; https://github.com/byteplus-sa/seed-mcp (7a693e4) | 4 (polooficjalne, NIEPOTWIERDZONE) | B | 2026-11-27 | narzedzia, licencja MIT, autor z domeny bytedance.com, instrukcja Claude Code |
| Z18 | https://github.com/atharva3vedi/seedance-mcp (f541519) | 4 | B | 2026-11-27 | MCP spolecznosciowy na kluczu BytePlus |
| Z19 | https://github.com/leonaiuv/seedance-2-mcp (fdf1157) ; https://github.com/MrLinWang/volcengine-ark-media-mcp (1c6b3cb) + https://registry.npmjs.org/volcengine-ark-media-mcp ; https://github.com/nsmao-com/seedream-mcp (5f322f2) ; https://registry.npmjs.org/seedance-mcp ; https://pypi.org/pypi/volcengine-video-mcp/json | 4 | B | 2026-11-27 | pozostale MCP spolecznosciowe |

## 10. Dane wejsciowe do syntezy (propozycja punktacji wg zlecenia; przeliczy Evaluator)

| Kryterium | Pkt max | Seedance | Uzasadnienie |
|---|---|---|---|
| Publiczne API dla zwyklego konta | 3 | 3 | ModelArk API, limity "Individual" (Z1, Z3, Z8) |
| Obraz do wideo z klatka startowa | 2 | 2 | `role: first_frame`, wszystkie modele; 2.x takze `last_frame` (Z1) |
| Obrazy referencyjne postaci | 2 | 2 | `reference_image` do 30 (2.5) / 9 (2.0); zastrzezenie: prawdziwe twarze tylko przez `asset://` (Z1, Z9) |
| Zadania asynchroniczne i webhook | 1 | 1 | task `id` + `callback_url` (Z1, Z2, Z5) |
| Oficjalne SDK | 1 | 1 | `arkruntime` (Python), `ark-runtime-go`, `ark-runtime` (Java), instalowane w dokumentacji BytePlus (Z4, Z11) |
| Oficjalny serwer MCP (2) / spolecznosciowy (1) | 2 | 1 | brak oficjalnego (Z12, Z13); spolecznosciowe z repozytorium, licencja i data (Z15, Z18); `byteplus-sa/ark-mcp` polooficjalny — gdyby synteza uznala go za oficjalny, wynik 2 |
| Brak barier onboardingu | 1 | 1 | brak listy oczekujacych w odczytanych zrodlach; ale prog aktywacji 30 USD (bezzwrotny) i "verified to use Pay by Credits" — pewnosc niska (Z7); synteza moze przyznac 0 |
| **Suma** | 12 | **11** (zakres 10-12 zaleznie od rozstrzygniec syntezy w dwoch wierszach powyzej) | |

## 11. Niepewnosci

1. ~~Volcengine odczytany tylko posrednio~~ — ZAMKNIETE w rundzie 4: odczyt bezposredni `curl` (HTTP 200), endpointy, parametry, limity i prog aktywacji potwierdzone (Z14, Z20). WebFetch nadal nie rozwiazuje DNS tych hostow (sekcja 0). Otwarte pozostaja tylko wymogi konta Volcengine (weryfikacja tozsamosci, dostep spoza Chin) — w odczytanych stronach brak wzmianki, NIEPOTWIERDZONE. Runda 5: wymogi kanalow rozdzielone w sekcji 8 (BytePlus: konto BytePlus, 30 USD — Z7; Volcengine: konto Volcengine, 200 CNY — Z20); wczesniejsze zdanie laczace kanal Volcengine z kontem BytePlus i progiem 30 USD bylo bledne i zostalo usuniete.
2. Zakres weryfikacji "Pay by Credits" i ograniczenia rejestracji konta BytePlus wg kraju (w tym Polska) — nieodczytane (poza zakresem luk wskazanych w rundzie 4).
3. Status `byteplus-sa/*` (autor z domeny bytedance.com, ale bez rejestru, bez odnosnika w dokumentacji) — nie rozstrzygnieto, czy to produkt oficjalny; traktowany jako rzad 4.
4. ~~Strona "cancel-or-delete" bez tresci~~ — ZAMKNIETE w rundzie 4 (Z21, Z20).
5. ~~Brak oficjalnego CLI~~ — OBALONE w rundzie 4: oficjalne `arkcli` istnieje (Z22). Niepewnosc: dokladna skladnia flag wideo w wersji BytePlus odczytana tylko na poziomie `arkcli +gen` (pelne flagi z dokumentacji Volcengine); narzedzia nie instalowano.
8. fal.ai i Replicate (sekcja 7, rzad 4) — hosty nadal niedostepne w sesji (curl: brak polaczenia, 2026-11-27); pozostaja odczytem posrednim.
6. Ograniczenie prawdziwych twarzy w referencjach wplywa na spojnosc postaci granych przez aktorow — wymaga zasobow `asset://` (wirtualne postacie lub autoryzowane osoby).
7. Serwery spolecznosciowe: rzad 4, jakosci nie weryfikowano; nie instalowano.
