# ZERO-RESEARCH-003-a — Kling (Kuaishou): API, SDK, MCP i sterowanie z Claude Code

Wezel: a (Kling). Tresc z rundy 1 z 3; rundy 2 i 3 bez zmian merytorycznych (jedyna poprawka rundy 3, PROC-R2-1, dotyczy `autobot/REJESTR_TEMATOW.md` po stronie orkiestratora, poza allowlista Operatora). **Runda 4 z 4 (dodatkowe przejscie, zgoda ECHO-019):** po dopuszczeniu `kling.ai` / `klingai.com` / `app.klingai.com` ponowiono odczyt BEZPOSREDNI zrodel dotad posrednich; zmienione tylko pola, ktorych dotyczyl odczyt posredni lub luki (oznaczenia "R4" w tekscie). Rola: Operator (Opus 5.5). Data odczytu wszystkich zrodel: 2026-11-27.
Zakres: wylacznie odczyt dokumentacji, repozytoriow i rejestrow. NIE zalozono kont ani kluczy, NIE zainstalowano serwerow MCP, CLI ani bibliotek, NIE wykonano zadnego wywolania API Kling ani platform posredniczacych, NIE uruchomiono kodu z repozytoriow. Zadnych kluczy i sekretow w tym pliku.

## 0. Zastrzezenie o dostepie do zrodel (czytac najpierw)

- ~~Domeny `kling.ai`, `klingai.com` zablokowane~~ — stan rund 1-3. **R4 (2026-11-27):** narzedzie WebFetch nadal zwraca `getaddrinfo ENOTFOUND kling.ai` (rozwiazywanie nazw po stronie narzedzia), ale `curl` przez proxy sesji odczytuje `kling.ai` i `klingai.com` (HTTP 200). Dokumentacja API Kling udostepnia **pelne strony w formacie Markdown** (indeks: `https://kling.ai/document-api/llms.txt`; kazda strona pod `<adres>.md`, naglowek "Source: ..."). Odczytano je w calosci bezposrednio (tylko GET, bez kont i kluczy) = **odczyt bezposredni (B)**. Strony aplikacji renderowane po stronie klienta (`kling.ai/app/mcp/guide`, `kling.ai/app/cli`) zwracaja tylko szkielet HTML bez tresci — te twierdzenia pozostaja **odczytem posrednim (P)**. Zrodla rund 1-3 zaktualizowano w tabeli 9 (kolumna Sposob i uwagi R4).
- Odczytane **bezposrednio** (curl/git, tylko odczyt): oficjalny rejestr MCP `registry.modelcontextprotocol.io`, rejestr npm `registry.npmjs.org`, PyPI `pypi.org/pypi/...json`, pliki README/SKILL z `raw.githubusercontent.com`, daty ostatnich commitow przez `git clone --depth 1 --filter=blob:none --no-checkout` do katalogu tymczasowego (bez checkoutu i bez uruchamiania czegokolwiek). API GitHub (`gh api`) zwrocilo 403 (repozytoria nie dolaczone do sesji) — dlatego daty i licencje ustalono z commitow i plikow LICENSE.
- `fal.ai` i `replicate.com` tez zablokowane (ENOTFOUND) — platformy posredniczace potwierdzone tylko posrednio lub przez rejestry pakietow.

## 1. Publiczne API (REST) — dostepnosc dla zwyklego konta

| Pytanie | Odpowiedz | Zrodlo | Pewnosc |
|---|---|---|---|
| Czy istnieje publiczne API REST | **TAK** — Kling Open Platform (dokumentacja `kling.ai/document-api/...`); indeks dokumentacji wymienia strony API dla 4.0, 4.0 Flash, 3.0 Turbo, 3.0 / 3.0 Omni, O1, 2.6, 2.5 Turbo (wideo) | Z29 (indeks), Z3 | **wysoka (R4, B)** |
| Jak uzyskac dostep | Quick Start: krok 1 `https://kling.ai/dev`; krok 2 zakup pakietu zasobow (Basic / Pro / General / Flagship dla wideo) lub doladowanie salda; krok 3 konsola `https://kling.ai/dev/api-key`, "Log in using your email. Your console account is the same as your Kling AI web account."; krok 4 "+ Create a new API Key", klucz pokazywany tylko raz | Z4 | **wysoka (R4, B)** |
| Uwierzytelnianie | **R4 rozstrzygniete:** "API Key authentication must be used to call Kling AI API" — sekcja "API Key (for all models)", naglowek `Authorization: Bearer <API Key>`. Para AccessKey/SecretKey -> JWT (HS256, `iss`=AK, `exp`, `nbf`) dotyczy **tylko API w starym standardzie** (model w parametrze `model_name`; nowy standard = wersja modelu w sciezce, np. `/text-to-video/kling-4.0`) | Z5 | **wysoka (R4, B)** |
| Adres bazowy | Globalny: `https://api-singapore.klingai.com` ("changed from https://api.klingai.com", dla serwerow poza Chinami); Chiny: `https://api-beijing.klingai.com` (strona chinska `klingai.com`, "适用于服务器在中国地区的用户") | Z5, Z30 | **wysoka (R4, B)** |
| Rozliczenie | Pakiety przedplacone (Units) lub saldo: "Kling API supports calls billed by unit and balance"; pakiety API oddzielne od czlonkostwa w aplikacji; "Unused resource package balance does not carry over and will be cleared upon expiration" | Z4, Z1 | **wysoka (R4, B)** |
| Ograniczenia regionalne | Dwie domeny i dwa adresy API (Global/Singapur, Chiny/Pekin); konta i kredyty Global i China rozdzielne (MCP/CLI, Z14). Regulamin API (Z31, wersja z 2026-04-21) **nie zawiera** listy krajow wykluczonych; nakazuje uzytkownikowi zapewnic zgodnosc z prawem swojego kraju (pkt 5.4). Wprost wymienionego zakazu dla Polski/UE w odczytanych zrodlach **brak**; formalny dowod negatywny (np. lista krajow platnosci) — NIEPOTWIERDZONE | Z5, Z30, Z31, Z14 | srednia |
| Weryfikacja firmy / lista oczekujacych | **R4:** pelny regulamin API odczytany bezposrednio — brak wymogu weryfikacji firmy, KYC i listy oczekujacych; dostep "after you complete the steps to obtain the API Service ... and after successful payment of the service fee" (pkt 2.6); wiek minimalny 13 lat (osoby niepelnoletnie przez opiekuna). Wymagana jest wylacznie przedplata | Z31, Z4 | **srednia (R4, B; brak dowodu z panelu rejestracji)** |
| Stan na 2026-11-27 | Aktywne. Changelog API (bezposrednio): 2026-10-28 "Kling 4.0 API Is Now Fully Available ... up to 30s"; 2026-11-04 "Kling 4.0 Flash API Is Now Available ... up to 20s"; 2026-11-14 proporcje 4:3 i 3:4; 2026-11-19 "Kling 4.0 adds 4K resolution and supports HDR output at 1080p and 4K" | Z7 | **wysoka (R4, B)** |

## 2. Model pracy (asynchronicznosc)

- **Zadanie asynchroniczne: TAK.** Utworzenie zadania (`POST /text-to-video/kling-4.0` itd.) zwraca identyfikator zadania i `status`; status sprawdza sie zapytaniem. "Note: The API currently supports querying async tasks only". Z3a, Z8. **(R4, B, wysoka)**
- **Statusy (nowy standard API, w tym 4.0):** `submitted`, `processing`, `succeeded`, `failed` (tabela odpowiedzi 4.0 i protokol callback "New Callback Function"). Pisownia `succeed` wystepowala w starszych produktach (rundy 1-3, odczyt posredni) — w odczycie bezposrednim stron 4.0 jest `succeeded`. Z3a, Z32. **(R4, B, wysoka)**
- **Zapytanie o status — R4 rozstrzygniete dla 4.0:** `GET /tasks?task_ids=<id>` (wiele id po przecinku) albo `GET /tasks?external_task_ids=<id>` (nie razem); dodatkowo `POST /tasks` = zapytanie kursorem z filtrami (`status`, `product_type`). Przyklad z dokumentacji: `https://api-singapore.klingai.com/tasks?task_ids=123`. Z3a. **(R4, B, wysoka)**
- **Webhook/callback: TAK.** W 4.0: `options.callback_url` ("the server will actively notify when the task status changes") i `options.external_task_id`; w Video to Audio i Element Management `callback_url` na najwyzszym poziomie. **R4:** protokol callback odczytany: ladunek zawiera `id`, `status`, `message`, `create_time`, `update_time`, `external_id` i wyniki; strona opisuje tez podpis webhooka ("Webhook Signature"). Z3a, Z9, Z32. **(R4, B, wysoka)**
- **Pobranie wyniku:** URL-e w odpowiedzi zapytania (`type: video`, `url`, `duration`; `usage.output_duration` do rozliczenia); "generated images/videos will be cleared after 30 days" (Video to Audio); Skill API: "Generated assets are retained for 30 days". W MCP/CLI linki wygasaja po 24 h (Z15). Z3a, Z9, Z23, Z15. **(R4, B)**

## 3. Limity

| Limit | Wartosc | Zrodlo | Pewnosc |
|---|---|---|---|
| Zadania rownolegle (API) | **R4 (B):** "Independently calculated by account, model version, and resource package type (video/image) ... with shared quotas for all API keys"; przy kilku aktywnych pakietach tego samego typu obowiazuje najwyzsza wartosc; zadanie zajmuje slot od `Submitted` do zakonczenia (takze bledu); wideo = 1 slot, obraz = `n` slotow; przekroczenie: kod 1303 "parallel task over resource pack limit". Cennik (HTML odczytany bezposrednio): "Concurrent videos = the number of videos being generated simultaneously. The concurrent number does not increase when purchasing additional resource packages." Konkretna liczba **20** dla pakietow — tylko z odczytu posredniego rund 1-3 (liczby ladowane dynamicznie, brak w statycznym HTML) | Z10, Z1 | wysoka (zasady) / srednia (liczba 20) |
| Zapytania na minute (API) | **R4 (B):** "This limitation concerns the number of concurrent tasks and is unrelated to Queries Per Second (QPS). The system does not impose any QPS limits."; "query interfaces do not consume concurrency". Jednoczesnie tabela kodow bledow zawiera 1302 "Too many requests; rate limit exceeded" | Z10, Z11 | wysoka |
| Kody bledow | **R4 (B):** 401/1000-1004 (uwierzytelnienie), 429/1100 (stan konta), 429/1101 (zaleglosc), 429/1102 (pakiet wyczerpany/wygasly), 403/1103 (brak uprawnien do API/modelu), 400/1301 (polityka bezpieczenstwa tresci), 429/1302 (rate limit), 429/1303 (wspolbieznosc lub QPS pakietu), 429/1304 (whitelist IP), 5000-5002; zalecany wykladniczy backoff od >= 1 s | Z10, Z11 | wysoka |
| MCP / CLI | **5 QPS**; bez subskrypcji aplikacji: **1 rownolegle zadanie wideo**; subskrybenci bez limitu zadan. R4: strony `kling.ai/app/mcp/guide` i `kling.ai/app/cli` pobrane bezposrednio, ale renderowane po stronie klienta (brak tresci w HTML) — liczby nadal z odczytu posredniego; w README pluginu i Skilla (B) brak tych liczb | Z14 | srednia (P) |

Sprzecznosc: "brak limitu QPS" (API) vs "5 QPS" (MCP/CLI) — dotycza roznych powierzchni (API Open Platform vs MCP konta aplikacji, por. uwaga pod tabela 4); w samym API brak limitu QPS przy istnieniu kodu 1302 — dokumentacja nie podaje progu dla 1302 (NIEPOTWIERDZONE, kiedy wystepuje).

## 4. Zakres API wzgledem aplikacji

| Funkcja | API REST (Open Platform) | MCP/CLI oficjalne | Zrodlo | Pewnosc |
|---|---|---|---|---|
| Tekst do wideo | TAK (R4, B): `POST /text-to-video/kling-4.0` i `POST /text-to-video/kling-4.0-flash`; cialo: `prompt` (wymagane) + `settings` (`resolution`, `dynamic_range`, `aspect_ratio`, `duration`) + `options` (`callback_url`, `external_task_id`, `watermark_info`); 3.0: `POST /text-to-video/kling-3.0` | TAK: `text_to_video` | Z3a, Z8 | wysoka |
| Obraz do wideo — klatka startowa i koncowa | TAK (R4, B): `POST /image-to-video/kling-4.0`, `contents[].type` = `prompt`, `first_frame`, `middle_frame`, `last_frame`; "up to 10 images per request"; obrazy .jpg/.jpeg/.png, <= 30 MB, >= 300 px, proporcje 2:5-5:2. **Kling 4.0 Flash — R4 rozstrzygniete:** `POST /image-to-video/kling-4.0-flash`, `contents[].type` = `prompt`, `first_frame`; "Only first-frame-to-video generation is supported" (zgodnie z tabela 5.1 instrukcji: First and Last Frames "Not supported"). Starsze modele: `image` + `image_tail` (changelog) | TAK: `image_to_video`; plugin: 4.0 = first/last/intermediate, 4.0 Flash = tylko pierwsza klatka | Z3b, Z3c, Z3, Z7, Z15 | wysoka |
| Obrazy referencyjne postaci/obiektow (spojnosc) | TAK (R4, B): Element Management 4.0: `POST /v1/general/advanced-custom-elements` (pola `element_name`, `element_description`, `reference_type` = `image_refer` / `video_refer`, `element_image_list`, `element_video_list`, `element_voice_id`, `callback_url`), zapytanie `GET /v1/general/advanced-custom-elements/{id}`, lista, presety `/v1/general/advanced-presets-elements`, usuniecie `/v1/general/delete-advanced-elements`. Uzycie: `POST /omni-video/kling-4.0`, `contents[].type` m.in. `element`, `refer_image`, `voice`; image-to-video 4.0: "To provide reference videos, elements, or other reference assets, use the Omni reference-to-video API". Limit: do 15 zasobow na zadanie (do 10 obrazow, do 5 wideo lacznie <= 30 s, do 7 elementow) | TAK: `element_create/list/get/update/delete`, `omni_ref_video` | Z3d, Z3e, Z3b, Z3, Z16 | wysoka |
| Przedluzanie klipu | **R4 (B):** dla 4.0 **NIE ma obecnie** — instrukcja 4.0: "4.6 Video Extension (Coming Soon) ... extend it multiple times, up to 2 minutes", tabela: "Video Extension — Coming soon". Dla starszych modeli changelog (B): V1.0 (extend o 4-5 s), "V1.5 and V1.6 models support video extension" (2025-03-31); cennik wymienia "Video Extension" dla modeli V1.0-V2.1. Biezacy indeks dokumentacji (`llms.txt`) **nie zawiera** strony Video Extension (stary URL 1.6 zwraca tylko szkielet HTML) | Brak narzedzia extend w oficjalnym MCP (lista 13 narzedzi) | Z3, Z7, Z29, Z1 | wysoka (4.0: brak) |
| Audio | **R4 (B):** 4.0 Omni: `settings.audio` = `native` (domyslnie; "Generates audio alongside the video") / `original` (zachowuje dzwiek z `base_video` lub `feature_video`); 4.0 text-to-video i image-to-video: **brak parametru audio** w tabeli parametrow, a instrukcja 4.0 opisuje dzwiek stereo generowany z opisu w prompcie ("Audio output is two-channel stereo"); wejscie audio tylko jako profile glosu (do 3, 5-30 s). 3.0: `settings.audio` = `native` / `off` (domyslnie `off`). Osobne endpointy Text to Audio / Video to Audio | Plugin: dla Omni "synchronized sound" lub dzwiek wideo referencyjnego | Z3e, Z3a, Z3, Z8, Z9 | wysoka |
| Rozdzielczosc | **R4 (B):** 4.0: `720p`, `1080p` (domyslnie), `4k`; `dynamic_range` `sdr`/`hdr` (hdr tylko 1080p/4k); 4.0 Flash: tylko `720p` | 4.0: 720p, 1080p i 4K "for eligible accounts" | Z3a, Z3c, Z7, Z15 | wysoka |
| Dlugosc | **R4 (B):** 4.0: `settings.duration` 3-30 s (liczby calkowite; bez parametru i bez dlugosci w prompcie domyslnie 10 s); 4.0 Flash: 3-20 s; 3.0 (`/text-to-video/kling-3.0`) i 3.0 Omni (`/omni-video/kling-3.0-omni`): 3-15 s, domyslnie 5 s (R4, B) | jw. (plugin: 3-30 s / 3-20 s) | Z3a, Z3c, Z8, Z19, Z15 | wysoka |
| Proporcje | **R4 (B):** 4.0 T2V: `21:9`, `16:9` (domyslnie), `9:16`, `1:1`, `4:3`, `3:4`; 4.0 Omni dodatkowo `adaptive` (domyslnie) | z `who_am_i` | Z3a, Z3e | wysoka |
| Seed | **R4 (B):** tabele parametrow 4.0 (T2V, I2V, Omni), 4.0 Flash I2V i 3.0 T2V **nie zawieraja** parametru `seed`; slowo nie wystepuje w instrukcji 4.0 ani w changelogu. Wniosek: API nie udostepnia seed (w odczytanych stronach) | brak w kontrakcie | Z3a, Z3b, Z3c, Z3e, Z8, Z3, Z7 | srednia (dowod z braku) |

Uwaga: oficjalny MCP/CLI **nie jest** opakowaniem API Open Platform — korzysta z konta aplikacji (OAuth) i jej kredytow ("Generation consumes credits from the connected regional Kling AI account"; "Kling MCP uses paid credits in your Personal workspace"), a nie z pakietow Units API. Modele i parametry deklaruje serwer dynamicznie (`who_am_i`). Z13, Z15.

## 5. Oficjalne SDK lub CLI

| Element | Stan | Szczegoly | Zrodlo | Pewnosc |
|---|---|---|---|---|
| Oficjalne SDK do API REST (Python/JS itd.) | **NIE znaleziono** | R4: pelny indeks dokumentacji API (`llms.txt`, 76 stron, B) nie zawiera strony SDK; strony endpointow podaja przyklady HTTP/curl, a strona uwierzytelniania fragmenty Python/Java do JWT (nie pakiet SDK). Wyszukiwanie zwrocilo wylacznie SDK spolecznosciowe/posrednikow (np. `okaris/kling`, `TechWithTy/kling`, `runapi-ai/kling-sdk`) — rzad 4, NIEPOTWIERDZONE co do jakosci | Z29, Z5, Z20 | wysoka (R4, B) |
| Oficjalne CLI | **TAK**: pakiet npm `@klingai/cli-global` (Chiny: `@klingai/cli-cn`), komenda `kling`, Node `^18.17.0 \|\| >=20.3.0`; opis pakietu: "Kling AI CLI ... (thin MCP client)" — czyli klient oficjalnego MCP, nie API REST | wersja 0.2.4, opublikowana 2026-11-19 (pierwsza 0.1.0-alpha.1: 2026-06-17); opiekun npm `klingai-fe`; repozytorium zrodlowe wewnetrzne (`git.corp.kuaishou.com`), **licencja nie podana** w npm | Z21 (npm, odczyt bezposredni), Z14 | wysoka |
| R4: Oficjalny "Kling AI Skill" do **API REST** (nie MCP) | **TAK (B, strona dokumentacji API "Kling Skills", data aktualizacji 2026-10-28)**: "KlingAI API Official Skill ... support for tools including Openclaw, Claude Code, Cursor, Codex, Copilot and Opencode"; skrypt Node.js 18+ (`kling.mjs`, "no other dependencies"), uwierzytelnienie powiazaniem konta lub `--import-credentials --api_key`, automatyczny wybor regionu (`KLING_API_BASE`); modele wideo kling-4.0 / 4.0-flash / 3.0 / 3.0-turbo / 3.0-omni / 2.6 / 2.5-turbo / o1; adres instalacji `https://clawhub.ai/klingai-dev/klingai` | Host `clawhub.ai` zablokowany w sesji (proxy 403) — repozytorium, licencja i data ostatniej aktywnosci samego Skilla **NIEPOTWIERDZONE**; to Skill (skrypt) dla agentow, nie biblioteka SDK | Z23 | wysoka (istnienie) / brak (licencja, aktywnosc) |
| Oficjalny Skill dla agentow | **TAK**: `klingai-tech/skills` (`npx skills add klingai-tech/skills`), Skill `kling-cli` v0.2.4, wspiera m.in. Claude Code; pliki: README.md, SKILL.md, api-examples.md, reference.md | ostatni commit 2026-11-26 (90a3c7c); **brak pliku LICENSE** w repozytorium | Z22 (bezposrednio), Z23 | wysoka |

## 6. Serwer MCP

### 6.1 Oficjalny (dostawca)

| Pole | Wartosc | Zrodlo |
|---|---|---|
| Nazwa w oficjalnym rejestrze MCP | `io.github.klingai-dev/kling-ai` ("Kling AI Global Plugin", v1.0.2, isLatest, status active, opublikowany 2026-11-22); region Chiny: `io.github.klingai-dev/kling-ai-cn` (v1.0.1, 2026-11-22) | Z13 (bezposrednio) |
| Typ i adres | zdalny, `streamable-http`: `https://kling.ai/mcp/plugin` (Chiny: `https://klingai.com/mcp/plugin`); w poradniku tez `https://kling.ai/mcp` (connector reczny) | Z13, Z15, Z14 |
| Uwierzytelnianie | OAuth, logowanie kontem Kling AI Global | Z13 |
| Repozytorium | `https://github.com/klingai-tech/claude-plugin` (plugin Claude: `.mcp.json` + 3 Skills: `kling-ai`, `kling-ai-generate-image`, `kling-ai-generate-video`); licencja **MIT** (Copyright 2026 KLING AI Pte Ltd); ostatni commit **2026-11-25** (5f666eb) | Z15 (bezposrednio) |
| Narzedzia (13 grup) | `who_am_i`, `text_to_image`, `image_to_image`, `text_to_video`, `image_to_video`, `omni_ref_video`, `query_tasks`, `file_upload`, `element_create/list/get/update/delete`, `motion_library_list`, `motion_control`, `feedback`, `query_membership_and_credits` (+ `logout`) | Z22 (api-examples.md), Z24 (mcp-contract.md) |
| Model pracy w MCP | generacja asynchroniczna: zwraca `generationId` (+ `status`, `creditsConsumed`), wynik przez `query_tasks` -> `works[].url`; brak webhooka w MCP | Z22, Z24 |
| Limity | 5 QPS; bez subskrypcji 1 rownolegle zadanie wideo | Z14 |
| Ocena | **ISTNIEJE, oficjalny** (namespace `io.github.klingai-dev` w oficjalnym rejestrze; repozytorium z licencja KLING AI Pte Ltd; poradnik na kling.ai) | Z13, Z15, Z14 |

### 6.2 Spolecznosciowe (rzad 4 — NIEPOTWIERDZONE co do jakosci)

| Nazwa | Repozytorium / rejestr | Licencja | Ostatnia aktywnosc | Backend i zakres narzedzi |
|---|---|---|---|---|
| AceDataCloud KlingMCP (`mcp-kling` PyPI; `io.github.AceDataCloud/mcp-kling` w oficjalnym rejestrze) | github.com/AceDataCloud/KlingMCP | MIT (PyPI + LICENSE) | commit 2026-11-27 (8df7105); PyPI 2026.11.27.0 z 2026-11-27 | Posrednik AceDataCloud (wlasny token, nie klucz Kling); hostowany `https://kling.mcp.acedata.cloud/mcp` lub lokalny stdio; narzedzia: `kling_generate_video`, `kling_generate_video_from_image` (start/koniec), `kling_extend_video`, `kling_generate_motion`, `kling_generate_storyboard`, `kling_generate_turbo_video`, `kling_generate_with_assets` (elementy/glosy), `kling_lip_sync`, `kling_get_task`, `kling_get_tasks_batch`, `kling_list_models` i in. |
| RunAPI Kling MCP (`@runapi.ai/kling-mcp`) | github.com/runapi-ai/kling-mcp | Apache-2.0 (npm + LICENSE) | commit 2026-10-22 (af2df06); npm 0.4.1 z 2026-10-22 | Posrednik RunAPI (`RUNAPI_API_KEY` lub login); narzedzia: `text_to_video`, `image_to_video`, `extend_video` (modele v2.5-turbo), `edit_video`, `motion_control`, `ai_avatar`, `get_task`, `check_pricing`; 16 wariantow modeli |
| 199-biotechnologies mcp-kling (npm `mcp-kling`) | github.com/199-biotechnologies/mcp-kling | MIT (npm + LICENSE) | commit 2025-06-14 (e9fb31f); npm 5.2.0 z 2025-06-14 — **nieaktywny od ok. 17 mies.** | Bezposrednio API Kling (`KLING_ACCESS_KEY`/`KLING_SECRET_KEY`, JWT); 13 narzedzi, m.in. `extend_video`; README marketingowe |
| useapi.net Kling MCP | tylko wynik wyszukiwania (mcpservers.org), repozytorium REST `useapi/kling-api` niezweryfikowane | NIEPOTWIERDZONE | NIEPOTWIERDZONE | Hostowany, platny; nie liczyc jako potwierdzony (brak daty i licencji) |

## 7. Alternatywne drogi dostepu do modeli Kling (platformy posredniczace)

Tylko wymienione z dowodem dostepnosci, bez porownywania cen:
- **AceDataCloud** — dowod: PyPI `mcp-kling` 2026.11.27.0 i wpis w oficjalnym rejestrze MCP (Z25, Z13). Rzad 4.
- **RunAPI** — dowod: npm `@runapi.ai/kling-mcp` 0.4.1 (2026-10-22), repozytorium SDK `runapi-ai/kling-sdk` w wynikach wyszukiwania (Z26, Z20). Rzad 4.
- **fal.ai** — dowod posredni (indeks wyszukiwarki ograniczony do fal.ai; host zablokowany): endpointy `fal-ai/kling-video/v3/pro/image-to-video`, `.../v3/4k/image-to-video`, dokumentacja V2.6 Pro, V2.1, V1.6 (Z27). Kling 4.0 na fal.ai — NIEPOTWIERDZONE. Rzad 4.
- **MuAPI** — tylko repozytorium spolecznosciowe `Anil-matcha/Kling-4-API` w wynikach wyszukiwania (Z20). NIEPOTWIERDZONE.
- **Replicate** — brak wynikow, host zablokowany: NIEPOTWIERDZONE.

## 8. Minimalna sciezka sterowania z Claude Code

**(a) Przez serwer MCP — DOSTEPNA (oficjalna, zalecana jako najprostsza):**
1. `claude plugin marketplace add klingai-tech/claude-plugin` oraz `claude plugin install kling-ai@klingai` (Z15) — albo samo MCP: `claude mcp add --transport http klingai --scope user https://kling.ai/mcp` (Z14, blog Kling).
2. W Claude Code `/mcp` -> serwer `kling-ai` -> Authenticate (OAuth kontem Kling Global).
3. Narzedzia: `who_am_i` (modele i parametry) -> opcjonalnie `file_upload` (klatki, zdjecia postaci) -> `element_create` (postac) -> `image_to_video` / `omni_ref_video` / `text_to_video` -> `query_tasks` (polling po `generationId`) -> `works[].url` (wazne 24 h, trzeba pobrac).
Wymaga: konta Kling (aplikacja) z kredytami; bez subskrypcji 1 zadanie wideo naraz.

**(a') Przez oficjalne CLI (wywolania z narzedzia powloki):** `npm i -g @klingai/cli-global`, `kling login`, `kling who_am_i`, `kling image_to_video --help`, `kling query_tasks ...` (Z14, Z21, Z22). CLI to klient tego samego MCP.

**(b) Przez HTTP z narzedzia powloki (API Open Platform) — DOSTEPNA (R4: sciezki potwierdzone bezposrednio, Z3a-Z3e):**
- naglowki `Authorization: Bearer <API Key>` (wymagany dla API w nowym standardzie; JWT z AK/SK tylko dla starego standardu) i `Content-Type: application/json`; baza `https://api-singapore.klingai.com` (Chiny: `https://api-beijing.klingai.com`);
- sciezki 4.0 **bez prefiksu wersji**, dokladnie: `POST /text-to-video/kling-4.0`, `POST /image-to-video/kling-4.0` (klatki w `contents`), `POST /omni-video/kling-4.0` (elementy, referencje, `settings.audio`); Flash: `.../kling-4.0-flash`;
- postac: `POST /v1/general/advanced-custom-elements` (zarzadzanie elementami ma prefiks `/v1/...`), odczyt `GET /v1/general/advanced-custom-elements/{id}`;
- opcjonalnie `options.callback_url`; status: `GET /tasks?task_ids=<id>` lub `GET /tasks?external_task_ids=<id>`; wynik: `url` wideo w odpowiedzi (pobrac w ciagu 30 dni).
Wymaga: klucza API i przedplaconego pakietu zasobow (lub salda). Brak oficjalnego SDK — wywolania przez curl/wlasny skrypt **albo** przez oficjalny "Kling AI Skill" do API (skrypt `kling.mjs`, Node 18+, deklarowane wsparcie Claude Code; Z23; repozytorium/licencja NIEPOTWIERDZONE).

**(c) Brak sterowania — NIE dotyczy** (obie drogi istnieja).

## 9. Zrodla

Rzad: 1 = dokumentacja/repozytorium/rejestr dostawcy; 4 = spolecznosc/posrednicy (NIEPOTWIERDZONE co do jakosci). Sposob: B = odczyt bezposredni; P = odczyt posredni (indeks wyszukiwarki, host zablokowany). R4: dla stron dokumentacji API odczyt bezposredni = pelna strona w wersji Markdown (`<URL>.md`) pobrana przez `curl` (GET, proxy sesji) w dniu 2026-11-27; WebFetch dla `kling.ai` nadal ENOTFOUND.

| ID | URL | Rzad | Sposob | Data odczytu | Co potwierdza |
|---|---|---|---|---|---|
| Z1 | https://kling.ai/dev/pricing | 1 | **B (R4: HTML)** / P (liczba 20) | 2026-11-27 | regula "Concurrent videos ... does not increase when purchasing additional resource packages"; "Video Extension" w pakietach dla V1.0-V2.1; liczba 20 tylko z P (ladowana dynamicznie) |
| Z2 | https://kling.ai/document-api/pricing/base/video.md | 1 | **B (R4)** | 2026-11-27 | cennik API wideo (Units) |
| Z3 | https://kling.ai/document-api/api/usage-guide/kling-4-0.md | 1 | **B (R4)** | 2026-11-27 | instrukcja 4.0: tabela 5.1 (4.0 vs Flash: klatki, 3-30/3-20 s, rozdzielczosci), "Video Extension (Coming Soon)", audio stereo, do 15 zasobow referencyjnych |
| Z3a | https://kling.ai/document-api/api/video/4-0/text-to-video.md | 1 | B (R4) | 2026-11-27 | `POST /text-to-video/kling-4.0`, parametry `settings`/`options`, `GET /tasks?task_ids=`, `POST /tasks`, statusy, brak `seed` i audio |
| Z3b | https://kling.ai/document-api/api/video/4-0/image-to-video.md | 1 | B (R4) | 2026-11-27 | `POST /image-to-video/kling-4.0`, `first_frame`/`middle_frame`/`last_frame`, do 10 obrazow |
| Z3c | https://kling.ai/document-api/api/video/4-0-flash/image-to-video.md | 1 | B (R4) | 2026-11-27 | `POST /image-to-video/kling-4.0-flash`, tylko `first_frame`, 720p, 3-20 s |
| Z3d | https://kling.ai/document-api/api/video/4-0/elements.md | 1 | B (R4) | 2026-11-27 | `/v1/general/advanced-custom-elements` (tworzenie, odczyt, lista), presety, usuwanie |
| Z3e | https://kling.ai/document-api/api/video/4-0/video-omni.md | 1 | B (R4) | 2026-11-27 | `POST /omni-video/kling-4.0`, typy `element`/`refer_image`/`voice`/`base_video`, `settings.audio` native/original, `adaptive` |
| Z4 | https://kling.ai/document-api/guides/get-started/quick-start.md ; (https://app.klingai.com/global/dev/document-api/quickStart/userManual -> 301 do kling.ai) | 1 | **B (R4)** | 2026-11-27 | kroki: kling.ai/dev, zakup pakietu, konsola kling.ai/dev/api-key, konto = konto web, tworzenie klucza |
| Z5 | https://kling.ai/document-api/api/get-started/authentication.md | 1 | **B (R4)** | 2026-11-27 | "API Key (for all models)"; AK/SK+JWT tylko stary standard; domena api-singapore |
| Z6 | https://kling.ai/document-api/apiReference/model/textToVideo ; https://kling.ai/document-api/api/video/lip-sync | 1 | P (rundy 1-3); R4: zastapione przez Z3a, Z5 (stare URL `apiReference/...` zwracaja tylko szkielet HTML) | 2026-11-27 | — |
| Z7 | https://kling.ai/document-api/updates/api.md | 1 | **B (R4)** | 2026-11-27 | changelog: 4.0 (2026-10-28), 4.0 Flash (2026-11-04), 4:3/3:4 (2026-11-14), 4K/HDR (2026-11-19), extend V1.0/V1.5/V1.6 |
| Z8 | https://kling.ai/document-api/api/video/3-0-omni/text-to-video.md ; (https://kling.ai/document-api/apiReference/model/OmniVideo — R4: tylko szkielet HTML) | 1 | **B (R4)** dla 3.0 | 2026-11-27 | `POST /text-to-video/kling-3.0`, `settings.audio` native/off, `/tasks` |
| Z9 | https://kling.ai/document-api/api/video/audio-generation/video-to-audio.md | 1 | **B (R4)** | 2026-11-27 | `callback_url` na najwyzszym poziomie, czyszczenie wynikow po 30 dniach |
| Z10 | https://kling.ai/document-api/api/get-started/concurrency-rules.md | 1 | **B (R4)** | 2026-11-27 | zasady wspolbieznosci, "does not impose any QPS limits", kod 1303 |
| Z11 | https://kling.ai/document-api/api/get-started/error-codes.md | 1 | **B (R4)** | 2026-11-27 | pelna tabela kodow bledow |
| Z12 | https://kling.ai/dev/model-release/kling-4 ; https://kling.ai/quickstart/kling-4-model-user-guide | 1 | P (rundy 1-3); R4: strony renderowane po stronie klienta, tresc zastapiona przez Z3, Z3a, Z3c | 2026-11-27 | — |
| Z13 | https://registry.modelcontextprotocol.io/v0/servers?search=klingai | 1 (rejestr, namespace dostawcy) | B | 2026-11-27 | oficjalny serwer MCP, adresy, OAuth, daty publikacji |
| Z14 | https://kling.ai/app/mcp/guide ; https://kling.ai/app/cli ; https://kling.ai/blog/claude-code-kling-mcp-food-promo-workflow | 1 | P (guide, cli: R4 pobrane, ale tylko szkielet HTML); **B (R4) dla bloga** | 2026-11-27 | blog (B): "claude mcp add --transport http klingai --scope user https://kling.ai/mcp"; 5 QPS i 1 zadanie bez subskrypcji — nadal P |
| Z15 | https://github.com/klingai-tech/claude-plugin (README.md, LICENSE; commit 5f666eb 2026-11-25) | 1 | B | 2026-11-27 | plugin Claude Code, komendy instalacji, MIT, modele/funkcje, linki 24 h |
| Z16 | https://github.com/klingai-tech/claude-plugin/blob/HEAD/skills/kling-ai/references/mcp-contract.md | 1 | B | 2026-11-27 | grupy narzedzi MCP, `generationId`, `works[]` |
| Z17 | https://kling.ai/document-api/apiReference/model/element | 1 | P (rundy 1-3); R4: zastapione przez Z3d (B) | 2026-11-27 | Element Management, `element_image_list` |
| Z18 | https://www.klingai.com/document-api/api/video/1-6/video-extension ; https://kling.ai/document-api/apiReference/model/videoExtension | 1 | P (tylko tytuly); R4: `.../1-6/video-extension.md` zwraca szkielet HTML, strony brak w indeksie Z29; extend potwierdzony w Z7 i Z3 (B) | 2026-11-27 | — |
| Z19 | https://kling.ai/document-api/api/video/3-0-omni/video-omni.md | 1 | B (R4) | 2026-11-27 | `POST /omni-video/kling-3.0-omni`, `settings.audio` native/original/off (domyslnie off), 3-15 s |
| Z20 | wyszukiwanie "Kling official SDK python" (github.com, kling.ai): okaris/kling, TechWithTy/kling, runapi-ai/kling-sdk, Anil-matcha/Kling-4-API | 4 | P | 2026-11-27 | brak oficjalnego SDK w wynikach; SDK spolecznosciowe |
| Z21 | https://registry.npmjs.org/@klingai%2Fcli-global | 1 (pakiet dostawcy) | B | 2026-11-27 | CLI 0.2.4 z 2026-11-19, "thin MCP client", brak licencji |
| Z22 | https://github.com/klingai-tech/skills (README.md, SKILL.md, api-examples.md; commit 90a3c7c 2026-11-26) | 1 | B | 2026-11-27 | Skill, lista 13 narzedzi, region Global/China, brak LICENSE |
| Z23 | https://kling.ai/document-api/api/get-started/kling-skills.md (stary URL `apiReference/skill` — szkielet HTML) | 1 | **B (R4)** | 2026-11-27 | "KlingAI API Official Skill", Claude Code, Node 18+, `kling.mjs`, API_KEY, ClawHub, wyniki 30 dni |
| Z24 | = Z16 | 1 | B | 2026-11-27 | — |
| Z25 | https://pypi.org/pypi/mcp-kling/json ; https://github.com/AceDataCloud/KlingMCP (commit 8df7105) | 4 | B | 2026-11-27 | MCP AceDataCloud |
| Z26 | https://registry.npmjs.org/@runapi.ai%2Fkling-mcp ; https://github.com/runapi-ai/kling-mcp (commit af2df06) | 4 | B | 2026-11-27 | MCP RunAPI |
| Z27 | https://fal.ai/models/fal-ai/kling-video/v3/pro/image-to-video (i pokrewne) | 4 | P | 2026-11-27 | Kling 3.0 na fal.ai |
| Z28 | https://registry.npmjs.org/mcp-kling ; https://github.com/199-biotechnologies/mcp-kling (commit e9fb31f) | 4 | B | 2026-11-27 | MCP spolecznosciowy (nieaktywny) |
| Z29 | https://kling.ai/document-api/llms.txt | 1 | B (R4) | 2026-11-27 | indeks 76 stron dokumentacji API; brak stron SDK i Video Extension |
| Z30 | https://klingai.com/document-api/api/get-started/authentication.md | 1 | B (R4) | 2026-11-27 | domena Chiny `https://api-beijing.klingai.com` |
| Z31 | https://kling.ai/document-api/guides/protocols/paid-service.md (Terms of API Paid Service, Effective Date 2026-04-21) | 1 | B (R4) | 2026-11-27 | brak weryfikacji firmy/listy oczekujacych; dostep po oplacie (2.6); wiek min. 13; zgodnosc z prawem lokalnym (5.4) |
| Z32 | https://kling.ai/document-api/api/get-started/callbacks.md | 1 | B (R4) | 2026-11-27 | protokol callback (nowy standard), statusy `succeeded`, podpis webhooka |

## 10. Dane wejsciowe do syntezy (propozycja punktacji wg zlecenia; przeliczy Evaluator)

| Kryterium | Pkt max | Kling | Uzasadnienie |
|---|---|---|---|
| Publiczne API dla zwyklego konta | 3 | 3 | konsola kluczy na zwyklym koncie, "console account is the same as your Kling AI web account" (Z4, Z5; R4 B) |
| Obraz do wideo z klatka startowa | 2 | 2 | `POST /image-to-video/kling-4.0`, `first_frame` (Z3b; R4 B) |
| Obrazy referencyjne postaci | 2 | 2 | Elements: `/v1/general/advanced-custom-elements` + `/omni-video/kling-4.0` (Z3d, Z3e; R4 B) |
| Zadania asynchroniczne i webhook | 1 | 1 | `GET /tasks?task_ids=` + `options.callback_url`, protokol callback (Z3a, Z32; R4 B) |
| Oficjalne SDK | 1 | 0 | brak oficjalnego SDK (indeks dokumentacji Z29, R4 B); istnieja oficjalne CLI (klient MCP) i oficjalny Skill-skrypt do API (Z23) — czy liczyc je jako "SDK", rozstrzyga synteza |
| Oficjalny serwer MCP (2) / spolecznosciowy (1) | 2 | 2 | `io.github.klingai-dev/kling-ai` (Z13, Z15) |
| Brak barier onboardingu | 1 | 1 | R4: pelny regulamin API (Z31, B) bez weryfikacji firmy, KYC i listy oczekujacych; wymagana tylko przedplata pakietu/salda (Z4); pewnosc srednia (brak odczytu panelu rejestracji/platnosci) |
| **Suma** | 12 | **11** | pewnosc oceny podniesiona w R4 (onboarding: niska -> srednia) |

## 11. Niepewnosci

1. ~~Cala dokumentacja API odczytana posrednio~~ — **R4:** dokumentacja API odczytana bezposrednio (wersje `.md`). Pozostaja posrednie: strony aplikacji `kling.ai/app/mcp/guide` i `kling.ai/app/cli` (5 QPS, 1 zadanie bez subskrypcji) oraz liczba 20 zadan rownoleglych w cenniku (renderowanie po stronie klienta).
2. **R4 rozstrzygniete:** sciezki 4.0 bez prefiksu (`/text-to-video/kling-4.0` itd.), elementy z prefiksem `/v1/general/...`; zapytanie o zadanie 4.0 `GET /tasks?task_ids=`; audio 4.0 tylko w Omni (`settings.audio`), w T2V/I2V z promptu; `seed` brak w API; extend dla 4.0 "Coming soon", istnial dla V1.0-V1.6. Otwarte: brak progu dla kodu 1302 przy deklaracji "no QPS limits".
3. **R4 rozstrzygniete:** API Key wymagany dla wszystkich modeli; AK/SK+JWT tylko dla starego standardu API.
4. Ograniczenia regionalne: regulamin bez listy krajow wykluczonych (B), ale panel rejestracji i platnosci nieodczytany (wymaga konta) — dla Polski brak dowodu negatywnego ani pozytywnego. Oficjalny Skill API: repozytorium, licencja i aktywnosc NIEPOTWIERDZONE (`clawhub.ai` zablokowany).
5. Oficjalny MCP rozlicza kredyty aplikacji (nie Units API) — sterowanie przez MCP i przez API to dwa rozne konta rozliczeniowe w tym samym ekosystemie.
6. Serwery spolecznosciowe: rzad 4, jakosci nie weryfikowano; nie instalowano.
