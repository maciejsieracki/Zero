# ZERO-RESEARCH-003-e — MiniMax (API Platform): API, SDK, MCP i sterowanie z Claude Code

Wezel: e (MiniMax przez API Platform; lokalny model open source odpada — ECHO-007). Runda 5 z 5 (ECHO-025; wersja z poprawkami z rund 1-4, ponowny odczyt bezposredni dokumentacji API Platform). Rola: Operator (Opus 5.5). Data odczytu wszystkich zrodel: 2026-11-27 (dokumentacja API Platform odczytana ponownie bezposrednio 2026-11-27 ok. 18:15-18:22 UTC).
Zakres: wylacznie odczyt dokumentacji, repozytoriow i rejestrow. NIE zalozono kont ani kluczy, NIE zainstalowano serwerow MCP, CLI ani bibliotek, NIE wykonano zadnego wywolania API MiniMax ani platform posredniczacych, NIE uruchomiono kodu z repozytoriow. Zadnych kluczy i sekretow w tym pliku.

## 0. Zastrzezenie o dostepie do zrodel (czytac najpierw)

- **Korekta rundy 5:** twierdzenie z rund 1-4 o zablokowanym hoscie `platform.minimax.io` (kod 000) jest **nieaktualne**. W rundzie 5 host jest dopuszczony w sieci sesji: `curl` (GET przez proxy sesji, 2026-11-27) zwrocil **HTTP 200** dla wersji `.md` wszystkich stron D1-D10 (m.in. `api-reference/video-generation-v2-create.md`, `guides/rate-limits.md`, `guides/mcp-guide.md`) oraz dla indeksu `docs/llms.txt`. Dokumentacja API (D1-D12) jest teraz **odczytem bezposrednim** (B), pewnosc `wysoka`, o ile nie zaznaczono inaczej. Twierdzenia z rund 1-4, ktorych ponowny odczyt nie potwierdzil, zostaly usuniete lub oznaczone NIEPOTWIERDZONE (patrz 3 i 11).
- Nadal zablokowany: `www.minimax.io` (curl 2026-11-27 18:22 UTC: proxy 403, kod 000) — strona glowna nie byla potrzebna, regulamin odczytano z `platform.minimax.io/protocol/terms-of-service` (D11).
- Odczytane **bezposrednio** (B, tylko odczyt): oficjalne repozytoria `github.com/MiniMax-AI/*` (pliki README, SKILL, referencje i kod zrodlowy pobrane jako tekst z `raw.githubusercontent.com`, bez uruchamiania), daty ostatnich commitow przez `git clone --depth 1 --filter=blob:none --no-checkout` do katalogu tymczasowego (bez checkoutu), rejestr MCP `registry.modelcontextprotocol.io`, PyPI (`pypi.org/pypi/<pakiet>/json`), npm (`registry.npmjs.org`). `gh api` / `api.github.com` zwraca 403 — licencje ustalono z plikow LICENSE i metadanych pakietow.
- **Kod zrodlowy oficjalnego CLI** (`MiniMax-AI/cli`: `src/client/endpoints.ts`, `src/video/v2.ts`, `src/commands/video/generate.ts`) jest zrodlem rzedu 1 odczytanym bezposrednio i potwierdza sciezki endpointow, role obrazow i `callback_url`; w rundzie 5 te same sciezki i pola potwierdzono w specyfikacji OpenAPI osadzonej w dokumentacji (D2, D6, D7) — oba zrodla sa zgodne.
- `fal.ai`, `replicate.com` sa poza lista hostow dopuszczonych w rundzie 5 (w rundach 1-4: kod 000) — platformy posredniczace potwierdzone posrednio, przez rejestry lub przez cennik MiniMax (D9).

## 1. Publiczne API (REST) — dostepnosc dla zwyklego konta

| Pytanie | Odpowiedz | Zrodlo | Pewnosc |
|---|---|---|---|
| Czy istnieje publiczne API REST | **TAK** — MiniMax API Platform: wideo v1 (`/v1/video_generation`, modele Hailuo 2.3 / 2.3-Fast / 02, S2V-01) i v2 (`/v2/video_generation`, rodzina MiniMax-H3) | D1, D2, D3 (OpenAPI: `servers: https://api.minimax.io`, `POST /v2/video_generation`, `POST /v1/video_generation`); zgodnie z kodem CLI Z5 | wysoka (B) |
| Jak uzyskac dostep | Rejestracja konta na API Platform -> "API Keys" -> utworzenie klucza pay-as-you-go ("obsluguje wszystkie modalnosci": jezyk, wideo, obraz, mowa) -> doladowanie salda (Billing/Balance) | D4 (quickstart-preparation: "Pay-as-you-go supports all modality models, including language, Video, Image, and Speech"); D2: modele H3 wymagaja "Pay-as-you-go API" | wysoka (B) |
| Typ klucza dla H3 | Wymagany **klucz pay-as-you-go** (D2: "To use the flagship models ... please select the Pay-as-you-go API"); klucz M Plan (dawniej Token Plan) jest odrebny i "nie moze byc uzywany zamiennie" z kluczem standardowym (D5 FAQ); referencja CLI: klucz Token Plan/OAuth nie dziala dla H3 (blad `2013`) | D2, D5, Z6 | wysoka (B) |
| Uwierzytelnianie | Naglowek `Authorization: Bearer <klucz>` (kod klienta przewiduje tez wariant `x-api-key` dla niektorych uslug) | Z5 (`src/client/http.ts`), D4 | wysoka (B) |
| Adres bazowy / regiony | Globalny `https://api.minimax.io`; Chiny kontynentalne `https://api.minimaxi.com`; klucz musi pasowac do regionu hosta (inaczej "invalid api key") | D2 (`servers`), D10 (`MINIMAX_API_HOST`), Z1, Z4; FAQ CLI: region klucza `global`/`cn` (D5) | wysoka (B) |
| Ograniczenia regionalne | Regulamin API Platform (dostawca: Nanonoble Pte Ltd.), sekcja "Export Controls and Sanctions": uslugi nie dla osob z list sankcyjnych ani "established, operating, or residing in a comprehensively sanctioned country or region" (wymienione: Iran, Kuba, Korea Pln., Syria, Krym/Sewastopol, tzw. DRL i LRL). Polska/UE nie sa wymienione jako wykluczone. Wczesniejsze twierdzenia z odczytu posredniego (API "dostepne globalnie"; ograniczenia UE/UK/USA/Korea Pld. dla wag H3) **nie zostaly potwierdzone** w ponownym odczycie (strona `m-plan/faq` w obecnej wersji ich nie zawiera) — usuniete | D11 (B) | wysoka (regulamin) |
| Weryfikacja firmy / lista oczekujacych | Listy oczekujacych **brak** w odczytanych stronach. **Regulamin wymaga weryfikacji tozsamosci:** "you must complete real-name authentication in compliance with national regulations and MINIMAX Open Platform procedures" (z autoryzacja weryfikacji przez podmioty trzecie). Kiedy dokladnie jest wymuszana (przy rejestracji, przed doladowaniem czy przed uzyciem wideo) — NIEPOTWIERDZONE (nie zakladano konta). Weryfikacja firmy nie jest wymagana do wideo; dane firmy tylko do faktur (D9) | D11, D4 (B) | wysoka (zapis w regulaminie) / niska (moment wymuszenia) |
| Stan na 2026-11-27 | Aktywne: oficjalne CLI 1.0.29 opublikowane 2026-11-10, commit CLI 2026-11-10 (obsluga H3-Image); dokumentacja v2 (enum `model`) wymienia: `MiniMax-H3`, `-Highspeed`, `-Lite`, `-Max`, `-Max-Turbo`, `-MG` (hostowany przez MachGen), `-NC` (Nunchux AI); 480P dla `MiniMax-H3` obsluguje RunningHub | Z4, Z7, D2 | wysoka (B) |

## 2. Model pracy (asynchronicznosc)

- **Zadanie asynchroniczne: TAK.** POST tworzy zadanie i zwraca `task_id`; status przez zapytanie; po sukcesie pobranie pliku. D2, D6, Z5.
- **Endpointy (dokumentacja OpenAPI, B; zgodne z kodem CLI Z5):**
  - v2 (H3): `POST /v2/video_generation` -> `GET /v2/query/video_generation/{task_id}` -> wynik `content.url` (adres pobrania wideo). Dodatkowo: lista zadan `GET /v2/query/video_generation` (paginacja, filtry), anulowanie/usuniecie `DELETE /v2/video_generation/{task_id}` (zadanie `queued` -> `cancelled` bez oplaty; `running` nie mozna anulowac), regeneracja `POST /v2/video_regeneration` (podniesienie wideo 768P H3 do 2K, przez `source_task_id` lub `base_video`). D2, D6, D7, D12, Z5.
  - v1 (Hailuo, S2V-01): `POST /v1/video_generation` -> `GET /v1/query/video_generation?task_id=<id>` -> `file_id` -> `GET /v1/files/retrieve?file_id=<id>` (adres pobrania). Z5, Z1 (kod `server.py`).
  - Pliki: `POST /v1/files/upload`, `/v1/files/list`, `/v1/files/delete`; zasoby mozna przekazac jako `mm_file://<file-id>`. Z5, Z6.
- **Statusy:** v2 (enum `status` w D6): `queued`, `running`, `succeeded`, `failed`, `cancelled` (referencja CLI Z6 dodaje `expired` — w dokumentacji brak, NIEPOTWIERDZONE). v1 (D6): `Preparing`, `Queueing`, `Processing`, `Success`, `Fail`. Pisownia zalezy od wersji endpointu.
- **Webhook/callback: TAK.** Parametr `callback_url` przy tworzeniu zadania (v1 i v2); w v1 i v2 najpierw weryfikacja: serwer MiniMax wysyla zadanie z polem `challenge`, ktore trzeba odeslac bez zmian w 3 s; potem POST przy kazdej zmianie statusu, cialo jak odpowiedz Query Task; statusy callbacku v2: `queued`, `running`, `succeeded`, `failed`, `cancelled` (D2). Opcja `--callback-url` w oficjalnym CLI, mapowana na `callback_url` w zadaniu v2. D2, D3, Z5 (`v2.ts`, `generate.ts`).
- **Pobranie wyniku / retencja:** zapytanie i lista obejmuja zadania z ostatnich **7 dni** (okno `[T-7d, T)`, starsze `task_id` -> `invalid task_id`); regeneracja wymaga zadania zrodlowego z ostatnich 7 dni. v2: `content.url` jest "time-limited" — po wygasnieciu ponowne zapytanie zwraca nowy URL; dokladny czas waznosci **nie jest podany** (NIEPOTWIERDZONE). v1: `download_url` z `/v1/files/retrieve` wazny **1 godzine**. D6, D7.
- **Zalecany polling:** co 10 s (przyklad w przewodniku: "A recommended polling interval is 10 seconds"); brak publikowanego ETA (D2, Z6).

## 3. Limity

| Limit | Wartosc | Zrodlo | Pewnosc |
|---|---|---|---|
| Zapytania na minute (pay-as-you-go) | Tabela "Video" na stronie Rate Limits: `Video Generation` / `Hailuo series` **20 RPM**, max inflight `—`; `Video Generation V2` / `MiniMax-H3` **300 RPM** | D8 (B, odczyt 2026-11-27) | wysoka |
| Zadania rownolegle | V2 (`MiniMax-H3`): **30** "Max inflight tasks"; Hailuo: brak wartosci (`—`). Podwyzszenie limitow: kontakt `api@minimax.io` | D8 (B) | wysoka |
| Pakiety wideo | Twierdzenie z rund 1-4 (pakiety wideo 20-50 RPM) **nie potwierdzone**: obecny cennik (D9) ma tylko pakiety audio (Audio Packages) i rozliczenie pay-as-you-go; usuniete | D9 (B) | wysoka (brak) |
| Subskrypcje (M Plan, dawniej Token Plan) | modele obrazu i wideo objete tylko **tygodniowym** oknem limitu (bez okna 5-godzinnego); M Plan przeznaczony do uzytku interaktywnego, do produkcji zalecane pay-as-you-go; limity moga byc zaostrzane w szczycie. Liczby klipow dziennie z rund 1-4 (3/5 dziennie) **nie potwierdzone** w ponownym odczycie — usuniete. H3 przez API wymaga klucza pay-as-you-go | D5, D8b (B), Z6 | wysoka |
| Kody bledow | `1002`/HTTP 429 (limit), `1008`/402 (saldo), `1004`/`2049`/401/403 (uwierzytelnienie), `1026`/`1027`/422 (tresci wrazliwe), `2013` (typ klucza nieobslugujacy H3) | Z6 | wysoka (B) |
| Limity wejsc H3 | (referencja CLI; dokumentacja D2 potwierdza m.in. proporcje obrazu w/h [0.4, 2.5] i wideo/audio ref. 2-15 s, lacznie <= 15 s) obraz <= 30 MB; wideo ref. <= 3, 2-15 s kazde, lacznie <= 15 s; audio ref. <= 3, 2-15 s, lacznie <= 15 s; obrazy ref. <= 9; razem referencji <= 12; prompt <= 7000 znakow; cialo JSON <= 64 MB | Z6 | wysoka (B) |

## 4. Zakres API wzgledem aplikacji

| Funkcja | API REST | Zrodlo | Pewnosc |
|---|---|---|---|
| Tekst do wideo | TAK: H3 (`/v2/video_generation`, `content[]` z `type: text`; kazde zadanie musi miec niepusty element `text`), Hailuo 2.3 / 02, T2V-01(-Director) (`/v1/video_generation`) | D2, D3, Z5 | wysoka (B) |
| Obraz do wideo — klatka startowa | TAK: H3 `image_url` z rola `first_frame`; Hailuo 2.3 / 2.3-Fast `first_frame_image` (2.3-Fast tylko I2V) | D2, D3, Z5 | wysoka (B) |
| Klatka koncowa | TAK: H3 rola `last_frame` (mozliwa sama, bez pierwszej); v1: First & Last Frame (`first_frame_image` + `last_frame_image`, wymagane oba) tylko `MiniMax-Hailuo-02`, bez 512P | D2, D3, Z5, Z6 | wysoka (B) |
| Obrazy referencyjne postaci/obiektow | TAK: H3 tryb reference — do 9 `reference_image`, do 3 `reference_video`, do 3 `reference_audio` (audio wymaga obrazu lub wideo); legacy S2V-01 `subject_reference` (`type: character`). **Tryb klatek i tryb referencji wykluczaja sie** (D2: gdy w `content` jest rola `reference_*`, role `first_frame`/`last_frame` nie moga wystapic) | D2, D3, Z6, Z5 | wysoka (B) |
| Przedluzanie klipu | **BRAK** osobnego endpointu w indeksie dokumentacji `llms.txt` (lista endpointow wideo: v2 create/query/list/delete, H3-Context-IR, regeneration; v1 t2v/i2v/fl2v/s2v/query/download; Video Agent) i w kodzie CLI. `POST /v2/video_regeneration` nie przedluza, tylko podnosi 768P do 2K. Pośrednio: wideo referencyjne (`reference_video`) | D12, D7, Z5 | wysoka (brak endpointu) |
| Parametry audio | H3: `generate_audio` (boolean, domyslnie `true`; `false` = wideo bez dzwieku); audio referencyjne `reference_audio` jako wejscie. Hailuo v1: brak parametru audio w schemacie t2v/i2v | D2, D3 (B) | wysoka |
| Rozdzielczosc | pole `resolution` (wymagane), enum `480P` / `768P` / `2K`; `MiniMax-H3`: wszystkie trzy (480P obsluguje RunningHub); `-MG`: 768P/2K; pozostale H3: 480P/768P. Hailuo 2.3 / 02: 768P (domyslnie) lub 1080P (tylko 6 s); inne v1: 720P | D2, D3 (B) | wysoka |
| Dlugosc | pole `duration` (wymagane, integer): H3 **4-15 s** (`-Max`, `-Max-Turbo`: 5-15 s); Hailuo 2.3 / 02: 6 lub 10 s (domyslnie 6) | D2, D3 (B) | wysoka |
| Proporcje | pole JSON **`ratio`** (np. `"ratio": "16:9"` w przykladzie v2-create): `adaptive` (domyslnie), `21:9`, `16:9`, `4:3`, `1:1`, `3:4`, `9:16`. T2V: wymagane, bez `adaptive`; I2V (klatki): zawsze `adaptive` (inna wartosc ignorowana); referencje: opcjonalne (`-Lite`, `-NC` bez `adaptive`) | D2 (B), Z5 | wysoka |
| Seed | **BRAK** pola `seed` w schemacie zadania v2 (`VideoGenerationV2Req`: `model`, `content`, `resolution`, `duration`, `ratio`, `extra`, `generate_audio`, `callback_url`, `response_format`) ani w schematach v1 t2v/i2v; w CLI `--seed` tylko dla obrazow `image-01` | D2, D3 (B), Z4 | wysoka |

## 5. Oficjalne SDK lub CLI

| Element | Stan | Szczegoly | Zrodlo | Pewnosc |
|---|---|---|---|---|
| Oficjalne CLI | **TAK**: `mmx-cli` (npm), komenda `mmx`, Node >= 18; `mmx video generate` (Hailuo 2.3 / H3, `--image`, `--last-frame`, `--reference-image/-video/-audio`, `--duration`, `--resolution`, `--ratio`, `--callback-url`, `--async`, `--download`), `mmx video task get`, `mmx video download`; logowanie `mmx auth login` (OAuth lub klucz; dla H3 tylko klucz pay-as-you-go) | npm 1.0.29 opublikowana 2026-11-10 (pierwsza wersja 2026-04-08); repo `github.com/MiniMax-AI/cli`, ostatni commit **2026-11-10** (ae29aae); licencja: README deklaruje **MIT**, ale w repo brak pliku LICENSE w katalogu glownym (404) i pole `license` w npm puste | Z4, Z7 | wysoka |
| Oficjalne SDK | **TAK (JS/TS)**: `mmx-cli/sdk` (`import { MiniMaxSDK } from 'mmx-cli/sdk'`), `sdk.video.generate({ model: 'MiniMax-H3' | 'MiniMax-Hailuo-2.3', async: true })`, `sdk.video.getTask`, `sdk.video.download` | czesc pakietu `mmx-cli` (jw.); plik `SDK.md` | Z8 | wysoka (B) |
| SDK Python | Oficjalne SDK Python do wideo — **NIE znaleziono**; strona "Integrate via SDK" dotyczy SDK Anthropic/OpenAI dla modeli tekstowych (nie wideo). Pakiet PyPI `minimax` jest obcy (inny autor) | D4 (B), PyPI | wysoka (strona D4) / srednia (brak dowodu negatywnego) |
| Oficjalne Skills dla agentow | **TAK**: (a) Skill `h3-video` w repo CLI (`npx skills add MiniMax-AI/cli -y -g`, wymienia Claude Code); (b) `github.com/MiniMax-AI/skills` — plugin Claude Code (`claude plugin marketplace add https://github.com/MiniMax-AI/skills`, `claude plugin install minimax-skills`), Skill `minimax-multimodal-toolkit` (wideo: T2V, I2V, klatka start-koniec, referencja postaci) | (b) MIT (Copyright 2026 MiniMax), ostatni commit **2026-11-10** (02853d8) | Z4, Z6, Z9 | wysoka |

## 6. Serwer MCP

### 6.1 Oficjalny (dostawca)

| Pole | Wartosc | Zrodlo |
|---|---|---|
| Nazwa / pakiety | **MiniMax-MCP** (Python, PyPI `minimax-mcp`, uruchamiany `uvx minimax-mcp`) oraz **MiniMax-MCP-JS** (npm `minimax-mcp-js`, `npx`). README: "Official MiniMax Model Context Protocol (MCP) server" | Z1, Z2 |
| Repozytoria | `https://github.com/MiniMax-AI/MiniMax-MCP` — ostatni commit **2026-11-10** (2904f33, H3-Image); PyPI 0.0.20 z 2026-11-10 (pierwsza 0.0.1: 2025-04-09). `https://github.com/MiniMax-AI/MiniMax-MCP-JS` — ostatni commit **2026-08-21** (8032f83); npm 0.0.18 z 2026-08-21 | Z1, Z2 (B) |
| Licencja | **MIT** (Copyright 2025 MiniMax AI) — oba repozytoria i metadane pakietow | Z1, Z2 (B) |
| Oficjalny rejestr MCP | **Nie wystepuje** w `registry.modelcontextprotocol.io` (wyszukiwanie "minimax", "MiniMax-AI", "hailuo" 2026-11-27 zwraca tylko serwery spolecznosciowe: `io.github.AceDataCloud/mcp-minimax`, `io.github.AceDataCloud/mcp-hailuo`, `io.github.runapi-builder/hailuo-mcp`, `net.useapi/minimax` — wszystkie opisane w 6.2) | Z10 (B) |
| Typ / transport | lokalny: stdio; Python tez SSE (wdrazalny lokalnie lub w chmurze); uwierzytelnienie zmiennymi `MINIMAX_API_KEY`, `MINIMAX_API_HOST` | Z1 |
| Narzedzia wideo | `generate_video` (`model`, `prompt`, `first_frame_image`, `duration`, `resolution`, `async_mode`) + `query_video_generation` (`task_id`). Modele wg opisu narzedzia: `T2V-01`, `T2V-01-Director`, `I2V-01`, `I2V-01-Director`, `I2V-01-live`, `MiniMax-Hailuo-02` (JS tez `S2V-01`). Pozostale narzedzia: `text_to_audio`, `list_voices`, `voice_clone`, `voice_design`, `text_to_image`, `image_edit`, `play_audio` | Z1 (README i kod `server.py`), Z2 |
| **Ograniczenie kluczowe** | Narzedzie wideo wywoluje tylko `/v1/video_generation` (kod `server.py`), wiec **nie obsluguje MiniMax-H3** (endpoint v2), klatki koncowej ani referencji H3; Hailuo 2.3 nie jest na liscie modeli narzedzia (czy przejdzie jako dowolny ciag `model` — NIEPOTWIERDZONE). README samo rekomenduje oficjalne CLI `mmx-cli` jako nowsza droge ("latest models") | Z1 (B) |
| Model pracy w MCP | domyslnie synchronicznie (serwer sam odpytuje i pobiera plik); `async_mode=true` zwraca `task_id`, wynik przez `query_video_generation`; brak webhooka w MCP | Z1 (kod) |
| Dokumentacja dostawcy | strona MCP Guide na API Platform: "MiniMax provides official Python and JavaScript implementations of the MCP server" (linki do obu repozytoriow); transport Python stdio/SSE, JS stdio/REST/SSE; narzedzia `generate_video` (prompt <= 2000 znakow), `image_to_video` (tylko JS), `query_video_generation`; konfiguracja `uvx`/`npx` z `MINIMAX_API_KEY`, `MINIMAX_API_HOST`, `MINIMAX_API_RESOURCE_MODE` (url/local); instrukcje dla Claude Desktop i Cursor (bez osobnej dla Claude Code) | D10 (B) |
| Ocena | **ISTNIEJE, oficjalny** (repozytoria organizacji `MiniMax-AI`, licencja MiniMax AI, opis na API Platform), ale z zakresem wideo ograniczonym do modeli legacy v1 | Z1, Z2, D10 |

Inny oficjalny serwer: `github.com/MiniMax-AI/MiniMax-Coding-Plan-MCP` (commit 2026-08-20) — dla subskrypcji Coding/Token Plan; w README brak narzedzi wideo (nie dotyczy sterowania wideo).

### 6.2 Spolecznosciowe (rzad 4 — NIEPOTWIERDZONE co do jakosci)

| Nazwa | Repozytorium / rejestr | Licencja | Ostatnia aktywnosc | Backend i zakres narzedzi |
|---|---|---|---|---|
| AceDataCloud MinimaxMCP (PyPI `mcp-minimax`; `io.github.AceDataCloud/mcp-minimax` w oficjalnym rejestrze) | github.com/AceDataCloud/MinimaxMCP | MIT (LICENSE: Copyright 2025 AceDataCloud; PyPI MIT) | commit **2026-11-27** (bfc3a33); rejestr i PyPI 2026.11.27.0 z 2026-11-27 | Posrednik AceDataCloud (wlasne konto i token, nie klucz MiniMax); hostowany `https://minimax.mcp.acedata.cloud/mcp` (OAuth lub Bearer) albo lokalny stdio; MiniMax H3: `minimax_generate_video_from_text`, `_from_images` (1-9 obrazow), `_from_audio`, `minimax_generate_video` (pelny schemat `content`), `minimax_get_task`, `minimax_get_tasks_batch`, `minimax_list_tasks`, `minimax_delete_task`, `minimax_list_models`; README podaje komende `claude mcp add --transport http --scope user minimax https://minimax.mcp.acedata.cloud/mcp` |
| AceDataCloud Hailuo MCP (pakiet `mcp-hailuo` wg rejestru i README; `io.github.AceDataCloud/mcp-hailuo` w oficjalnym rejestrze) | github.com/AceDataCloud/HailuoMCP | MIT (LICENSE: Copyright 2025 AceDataCloud) | commit **2026-11-27** (2187983); rejestr 2026.11.27.0 z 2026-11-27 (najnowsza) | Posrednik AceDataCloud (wlasne konto i token `ACEDATACLOUD_API_TOKEN`, nie klucz MiniMax); hostowany `https://hailuo.mcp.acedata.cloud/mcp` (OAuth lub Bearer) albo lokalny stdio; narzedzia: `hailuo_generate_video` (tekst), `hailuo_generate_video_from_image` (obraz referencyjny), `hailuo_get_task`, `hailuo_get_tasks_batch`, `hailuo_list_models`, `hailuo_list_actions`; README podaje `claude mcp add --transport http --scope user hailuo https://hailuo.mcp.acedata.cloud/mcp` + `claude mcp login hailuo`. Modele wg README (Features i tabela "Available Models"): `minimax-t2v` (domyslny), `minimax-i2v`, `minimax-i2v-director` — **bez H3** (Z13) |
| RunAPI Hailuo MCP (npm `@runapi.ai/hailuo-mcp`; `io.github.runapi-builder/hailuo-mcp` w oficjalnym rejestrze) | github.com/runapi-ai/hailuo-mcp | Apache-2.0 (plik LICENSE) | commit **2026-10-22** (f7c0b69, "Release hailuo-mcp v0.3.1"); rejestr 0.3.1 z 2026-10-22 (najnowsza) | Posrednik RunAPI (wlasne konto, `RUNAPI_API_KEY` lub logowanie narzedziem `login`); lokalny stdio przez `npx`; narzedzia: `text_to_video`, `image_to_video`, `get_task`, `check_pricing`; modele wg README: `hailuo-02-*` (tekst i obraz) oraz `hailuo-2.3-image-to-video-{pro,standard}` — **bez H3**; README podaje `claude mcp add hailuo -s user -- npx -y @runapi.ai/hailuo-mcp` (Z13) |
| useapi.net MiniMax (`net.useapi/minimax`) | tylko wpis w oficjalnym rejestrze; zdalny `https://api.useapi.net/v1/minimax/mcp`; **brak repozytorium** | NIEPOTWIERDZONE | wpis 1.0.0 z 2026-11-21 | Hostowany posrednik; opis: wideo, obrazy, muzyka, mowa, klonowanie glosu (Hailuo). Bez repozytorium i licencji — nie liczyc jako potwierdzony |

## 7. Alternatywne drogi dostepu do modeli MiniMax (platformy posredniczace)

Tylko wymienione z dowodem dostepnosci, bez porownywania cen:
- **fal.ai** — dowod posredni (indeks wyszukiwarki ograniczony do fal.ai; host zablokowany): endpointy `minimax/h3/image-to-video`, `minimax/h3/reference-to-video`, `minimax/h3-max/...`, `minimax/h3-max-turbo/image-to-video`, `fal-ai/minimax/hailuo-2.3/{standard,pro}/...` (Z11). Cennik MiniMax (D9, B, 2026-11-27) wskazuje "Provider: fal" przy wariantach H3-Max. Rzad 4 (strona fal nieodczytana bezposrednio).
- **AceDataCloud** — dowod: PyPI `mcp-minimax` 2026.11.27.0 i wpis w oficjalnym rejestrze MCP (Z12, Z10). Rzad 4.
- **RunAPI** — dowod: wpis `io.github.runapi-builder/hailuo-mcp` 0.3.1 w oficjalnym rejestrze MCP i repozytorium `runapi-ai/hailuo-mcp` (Z10, Z13); modele Hailuo 02 / 2.3, bez H3. Rzad 4.
- **useapi.net** — dowod: wpis `net.useapi/minimax` w oficjalnym rejestrze MCP (Z10). Rzad 4.
- **RunningHub** — cennik MiniMax (D9, B) podaje "MiniMax-H3-RH, Provider: RunningHub" (480P), a OpenAPI (D2): 480P dla `MiniMax-H3` "is served by RunningHub". Wlasne API RunningHub nieodczytane: rzad 4. Takze MachGen (`MiniMax-H3-MG`) i Nunchux AI (`MiniMax-H3-NC`) jako hostujacy warianty H3 dostepne przez API MiniMax (D2).
- **Replicate** — brak wynikow, host zablokowany: NIEPOTWIERDZONE.

## 8. Minimalna sciezka sterowania z Claude Code

**(a) Przez oficjalny serwer MCP — DOSTEPNA, ale tylko dla modeli legacy v1 (Hailuo-02, T2V/I2V-01, S2V-01 w JS):**
1. `claude mcp add` z komenda `uvx minimax-mcp -y` (Python) lub `npx minimax-mcp-js` i zmiennymi `MINIMAX_API_KEY`, `MINIMAX_API_HOST=https://api.minimax.io`, `MINIMAX_MCP_BASE_PATH` (konfiguracja z README; README pokazuje Claude Desktop/Cursor — dla Claude Code ta sama definicja stdio, bez osobnej instrukcji dostawcy) (Z1).
2. Narzedzia: `generate_video` (`model: "MiniMax-Hailuo-02"`, `first_frame_image`, `duration` 6/10, `resolution` 768P/1080P, `async_mode: true`) -> `query_video_generation` (`task_id`) -> plik zapisany lokalnie lub URL.
Nie daje H3 (audio, 2K, referencje postaci, klatka koncowa H3). Do H3 przez MCP pozostaje tylko posrednik spolecznosciowy (AceDataCloud, rzad 4, wlasne konto i rozliczenie).

**(a') Przez oficjalne CLI / Skill (wywolania z narzedzia powloki) — DOSTEPNA, pelny zakres H3 (zalecana przez samego dostawce):**
`npm install -g mmx-cli` (lub `npx skills add MiniMax-AI/cli -y -g` dla Skilla `h3-video`), `mmx auth login` (klucz pay-as-you-go), potem np. `mmx video generate --model MiniMax-H3 --prompt "..." --image start.png [--last-frame end.png] --duration 10 --resolution 768P --ratio 16:9 --async`, albo tryb referencji `--reference-image postac.png [--reference-audio ...]`; `mmx video task get --task-id <id> --model MiniMax-H3`; `mmx video download --file-id <id> --out klip.mp4` lub `--download` przy generowaniu (Z4, Z6). Alternatywnie plugin `minimax-skills` z `MiniMax-AI/skills` (Z9).

**(b) Przez HTTP z narzedzia powloki (API Platform) — DOSTEPNA:**
- naglowek `Authorization: Bearer <klucz pay-as-you-go>`; baza `https://api.minimax.io`;
- H3: `POST /v2/video_generation` z `model` (np. `MiniMax-H3`), `content[]` (`{type:"text"}`, `{type:"image_url", role:"first_frame"|"last_frame"|"reference_image"}`, `{type:"video_url", role:"reference_video"}`, `{type:"audio_url", role:"reference_audio"}`), `resolution` (`480P`/`768P`/`2K`), `duration` (4-15), `ratio`, `generate_audio`, opcjonalnie `callback_url`; status `GET /v2/query/video_generation/{task_id}` -> `content.url` (URL czasowy); anulowanie `DELETE /v2/video_generation/{task_id}`;
- Hailuo: `POST /v1/video_generation` -> `GET /v1/query/video_generation?task_id=` -> `GET /v1/files/retrieve?file_id=`;
- wgrywanie zasobow: `POST /v1/files/upload` (uzycie jako `mm_file://<id>`).
Zrodlo sciezek i pol: dokumentacja OpenAPI (B, D2/D3/D6/D7) zgodna z kodem oficjalnego CLI (B, Z5). Proporcje: pole `ratio` (np. `"16:9"`; dla T2V wymagane). Wymaga: klucza pay-as-you-go, salda i (wg regulaminu) weryfikacji tozsamosci real-name (D11).

**(c) Brak sterowania — NIE dotyczy** (drogi a, a' i b istnieja).

## 9. Zrodla

Rzad: 1 = dokumentacja/repozytorium/pakiet dostawcy; 4 = spolecznosc/posrednicy (NIEPOTWIERDZONE co do jakosci). Sposob: B = odczyt bezposredni (curl GET przez proxy sesji; strony dokumentacji w wersji `.md`, HTTP 200); P = odczyt posredni (indeks wyszukiwarki, host zablokowany). Data odczytu wszystkich: 2026-11-27. W rundzie 5 D1-D12 odczytano ponownie bezposrednio.

| ID | URL | Rzad | Sposob | Co potwierdza |
|---|---|---|---|---|
| D1 | https://platform.minimax.io/docs/api-reference/api-overview.md | 1 | B | przeglad API, modele H3, wspolny protokol `content[]` v2, zadania asynchroniczne, `content.url` |
| D2 | https://platform.minimax.io/docs/guides/video-generation.md ; https://platform.minimax.io/docs/api-reference/video-generation-v2-create.md | 1 | B | OpenAPI `POST /v2/video_generation`, `servers`, enum modeli H3, `content[]` i role, `resolution`, `duration`, `ratio` (przyklad `'16:9'`), `generate_audio`, `callback_url` + `challenge`, brak `seed`, wymog Pay-as-you-go, polling 10 s |
| D3 | https://platform.minimax.io/docs/api-reference/video-generation-t2v.md ; .../video-generation-i2v.md ; .../video-generation-fl2v.md | 1 | B | Hailuo v1 `POST /v1/video_generation`, modele, 6/10 s, 720P/768P/1080P, `first_frame_image`, `last_frame_image` (tylko Hailuo-02), `callback_url` |
| D4 | https://platform.minimax.io/docs/guides/quickstart-preparation.md | 1 | B | rejestracja, klucz pay-as-you-go dla wszystkich modalnosci (w tym wideo), klucz M Plan osobno, doladowanie salda, zmienne `MINIMAX_API_KEY`, SDK Anthropic/OpenAI tylko dla tekstu |
| D5 | https://platform.minimax.io/docs/m-plan/faq.md | 1 | B | klucz M Plan vs standardowy (niewymienne), tygodniowe okno dla wideo w M Plan, M Plan nie do produkcji, region klucza w CLI (`global`/`cn`) |
| D6 | https://platform.minimax.io/docs/api-reference/video-generation-v2-query.md ; .../video-generation-query.md ; .../video-generation-s2v.md | 1 | B | `GET /v2/query/video_generation/{task_id}`, statusy v2 i v1, okno 7 dni, `content.url` czasowy; S2V-01 `subject_reference` |
| D7 | https://platform.minimax.io/docs/api-reference/video-generation-v2-list.md ; .../video-generation-v2-regeneration.md ; .../video-generation-download.md | 1 | B | lista `GET /v2/query/video_generation` (7 dni), `POST /v2/video_regeneration` (768P -> 2K), `GET /v1/files/retrieve` (`download_url` wazny 1 h) |
| D8 | https://platform.minimax.io/docs/guides/rate-limits.md (D8b: https://platform.minimax.io/docs/m-plan/usage-rules.md) | 1 | B | tabela Video: `Hailuo series` 20 RPM / inflight `—`; `MiniMax-H3` (V2) 300 RPM / 30 inflight; D8b: wideo tylko w oknie tygodniowym M Plan |
| D9 | https://platform.minimax.io/docs/guides/pricing-video.md | 1 | B | rozliczenie pay-as-you-go, tylko pakiety audio (brak pakietow wideo z RPM), dostawcy wariantow H3: fal (H3-Max), RunningHub (H3-RH 480P); dane firmy do faktur |
| D10 | https://platform.minimax.io/docs/guides/mcp-guide.md ; https://platform.minimax.io/docs/api-reference/api-overview.md (D1) | 1 | B | oficjalny MCP Python i JS (linki do repozytoriow `MiniMax-AI`), transporty, narzedzia `generate_video`/`image_to_video`/`query_video_generation`, zmienne srodowiskowe |
| D11 | https://platform.minimax.io/docs/guides/terms-of-service.md -> przekierowanie na https://platform.minimax.io/protocol/terms-of-service (HTML) | 1 | B | dostawca Nanonoble Pte Ltd.; obowiazek "real-name authentication"; wykluczenie krajow i regionow objetych sankcjami (Iran, Kuba, Korea Pln., Syria, Krym, DRL, LRL) |
| D12 | https://platform.minimax.io/docs/llms.txt ; https://platform.minimax.io/docs/api-reference/video-generation-v2-delete.md | 1 | B | pelny indeks stron i endpointow wideo (brak "extend"); `DELETE /v2/video_generation/{task_id}` |
| Z1 | https://github.com/MiniMax-AI/MiniMax-MCP (README.md, LICENSE, `minimax_mcp/server.py`; commit 2904f33 2026-11-10) ; https://pypi.org/pypi/minimax-mcp/json | 1 | B | oficjalny MCP Python, MIT, narzedzia, endpoint v1, lista modeli, hosty regionalne, PyPI 0.0.20 (2026-11-10) |
| Z2 | https://github.com/MiniMax-AI/MiniMax-MCP-JS (README.md, LICENSE; commit 8032f83 2026-08-21) ; https://registry.npmjs.org/minimax-mcp-js | 1 | B | oficjalny MCP JS, MIT, npm 0.0.18 (2026-08-21), modele wideo |
| Z4 | https://github.com/MiniMax-AI/cli (README.md, package.json; commit ae29aae 2026-11-10) | 1 | B | CLI `mmx`, komendy wideo, auth, regiony, Skill dla Claude Code, MIT deklarowana, brak LICENSE |
| Z5 | https://github.com/MiniMax-AI/cli/blob/main/src/client/endpoints.ts ; .../src/client/http.ts ; .../src/video/v2.ts ; .../src/commands/video/generate.ts | 1 | B | sciezki v1/v2, Bearer, role obrazow/wideo/audio, 768P/2K, 4-15 s, proporcje, `callback_url` |
| Z6 | https://github.com/MiniMax-AI/cli/blob/main/skill/h3-video/references/h3-video.md ; .../skill/h3-video/SKILL.md | 1 | B | klucz pay-as-you-go dla H3, statusy, polling 10 s, limity wejsc, kody bledow, wykluczenie trybu klatek i referencji |
| Z7 | https://registry.npmjs.org/mmx-cli | 1 | B | `mmx-cli` 1.0.29 z 2026-11-10, pierwsza wersja 2026-04-08, pole licencji puste |
| Z8 | https://github.com/MiniMax-AI/cli/blob/main/SDK.md | 1 | B | SDK JS `mmx-cli/sdk`: `video.generate`, `getTask`, `download` |
| Z9 | https://github.com/MiniMax-AI/skills (README.md, LICENSE; commit 02853d8 2026-11-10) | 1 | B | plugin Claude Code `minimax-skills`, `minimax-multimodal-toolkit`, MIT |
| Z10 | https://registry.modelcontextprotocol.io/v0/servers?search=minimax (oraz `search=MiniMax-AI`, `search=hailuo`) | 1 (rejestr) / wpisy 4 | B | brak oficjalnego MiniMax w rejestrze; wpisy AceDataCloud (mcp-minimax, mcp-hailuo), RunAPI (hailuo-mcp 0.1.0-0.3.1) i useapi |
| Z11 | https://fal.ai/models/minimax/h3/image-to-video/api ; https://fal.ai/models/minimax/h3/reference-to-video/api ; https://fal.ai/models/fal-ai/minimax/hailuo-2.3/pro/text-to-video/api | 4 | P | modele MiniMax na fal.ai |
| Z12 | https://github.com/AceDataCloud/MinimaxMCP (README.md, LICENSE; commit bfc3a33 2026-11-27) ; https://pypi.org/pypi/mcp-minimax/json | 4 | B | MCP spolecznosciowy H3, MIT, narzedzia, komenda `claude mcp add` |
| Z13 | https://github.com/AceDataCloud/HailuoMCP (README.md, LICENSE; commit 2187983 2026-11-27) ; https://github.com/runapi-ai/hailuo-mcp (README.md, LICENSE; commit f7c0b69 2026-10-22) ; wpisy `search=hailuo` w Z10 | 4 | B | MCP spolecznosciowe Hailuo: licencje MIT / Apache-2.0, daty, narzedzia, komendy `claude mcp add` |

## 10. Dane wejsciowe do syntezy (propozycja punktacji wg zlecenia; przeliczy Evaluator)

| Kryterium | Pkt max | MiniMax | Uzasadnienie |
|---|---|---|---|
| Publiczne API dla zwyklego konta | 3 | 3 | klucz pay-as-you-go z konsoli API Platform na zwyklym koncie (D4, B); endpointy w OpenAPI (D2) i w kodzie CLI (Z5) |
| Obraz do wideo z klatka startowa | 2 | 2 | H3 `first_frame`, Hailuo `first_frame_image` (D2, D3, Z5) |
| Obrazy referencyjne postaci | 2 | 2 | H3 `reference_image` (do 9), legacy S2V-01 `subject_reference` (D2, D6, Z6) |
| Zadania asynchroniczne i webhook | 1 | 1 | `task_id` + `callback_url` z weryfikacja `challenge` (D2, D6) |
| Oficjalne SDK | 1 | 1 | `mmx-cli/sdk` (JS/TS) w oficjalnym repozytorium (Z8); zastrzezenie: brak pliku LICENSE, licencja tylko w README |
| Oficjalny serwer MCP (2) / spolecznosciowy (1) | 2 | 2 | `MiniMax-AI/MiniMax-MCP` i `-MCP-JS`, MIT (Z1, Z2), nazwane "official" na API Platform (D10, B); zastrzezenie: wideo tylko modele v1 (bez H3) — jesli synteza uzna, ze MCP musi obslugiwac model docelowy, wynik 1 (H3 tylko przez MCP spolecznosciowy AceDataCloud) |
| Brak barier onboardingu | 1 | 0 | **zmiana w rundzie 5:** regulamin (D11, B) wymaga "real-name authentication" (weryfikacja tozsamosci, takze przez podmioty trzecie); do tego saldo i klucz pay-as-you-go. Listy oczekujacych brak. Jesli synteza uzna sama weryfikacje tozsamosci (bez weryfikacji firmy i bez listy oczekujacych) za niebariere — 1 |
| **Suma** | 12 | **11** (12, jesli synteza uzna weryfikacje real-name za niebariere; 10, jesli dodatkowo obnizy MCP z powodu braku H3) | |

## 11. Niepewnosci

1. Runda 5: dokumentacja API Platform odczytana bezposrednio (HTTP 200); niepewnosc z rund 1-4 dotyczaca odczytu posredniego usunieta. Twierdzenia, ktorych ponowny odczyt nie potwierdzil (API "globalnie", ograniczenia wag H3, pakiety wideo 20-50 RPM, 3/5 klipow dziennie w Token Plan), usunieto. `www.minimax.io` nadal zablokowany (nie byl potrzebny).
2. Limity (20 RPM Hailuo; 300 RPM i 30 zadan w toku dla H3) odczytane bezposrednio 2026-11-27; FAQ zastrzega, ze MiniMax moze je dostosowywac w szczycie.
3. Oficjalny MCP nie obsluguje H3 (endpoint v1); przydatnosc dla ZERO (H3: audio, referencje) zalezy od drogi CLI/HTTP.
4. Licencja `mmx-cli` niejednoznaczna (README: MIT; brak pliku LICENSE; puste pole w npm).
5. Rozstrzygniete w rundzie 5: pole proporcji `ratio`, brak `seed`, brak endpointu przedluzania. Nadal NIEPOTWIERDZONE: dokladny czas waznosci `content.url` (dokumentacja: "time-limited") i status `expired` (tylko w referencji CLI).
6. Regulamin: wykluczenie krajow objetych sankcjami (Polska nie) i obowiazek weryfikacji real-name; moment i forma weryfikacji nieznane bez zakladania konta (zakazane w badaniu).
7. Serwery spolecznosciowe i platformy posredniczace: rzad 4, jakosci nie weryfikowano; nie instalowano.
