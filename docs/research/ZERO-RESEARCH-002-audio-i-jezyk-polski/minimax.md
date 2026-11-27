# ZERO-RESEARCH-002-e — MiniMax (API Platform): audio i jezyk polski

Wezel: e (MiniMax przez API Platform; lokalny model open source odpada — ECHO-007). Runda 1 z 3. Rola: Operator (Opus 5.5). Data odczytu zrodel: 2026-11-27.
Lista modeli: z `docs/research/ZERO-RESEARCH-001-porownanie-generatorow-wideo/zestawienie.md` (poz. 1, 3, 13, 18): MiniMax-Hailuo-2.3-Fast, MiniMax-Hailuo-2.3, MiniMax-H3-Lite, MiniMax-H3. Warianty H3 opisane w RESEARCH-001 poza tabela (H3-Max, H3-Max-Turbo, H3-Highspeed) oraz modele nowsze niz RESEARCH-001 (H3-MG, H3-NC) — sekcja 4 (zgloszenie, zgodnie z S-R10).

## 0. Zastrzezenie infrastrukturalne (czytac najpierw)

Hosty `platform.minimax.io` i `www.minimax.io` sa **zablokowane w sieci tej sesji** (WebFetch 2026-11-27: `getaddrinfo ENOTFOUND platform.minimax.io`, `getaddrinfo ENOTFOUND www.minimax.io`). Dokumentacje API odczytalem **posrednio**: indeks wyszukiwarki (WebSearch) z ograniczeniem do domen `platform.minimax.io` / `minimax.io` — fragmenty oficjalnych stron rzedu 1, nie pelne strony. Pewnosc tych pozycji: najwyzej **srednia**.
Wyjatek — **odczyt bezposredni**: oficjalne repozytorium `github.com/MiniMax-AI/MiniMax-H3` (README i `skills/h3-prompt-writing/references/ref-en.txt`) otwarlem WebFetch 2026-11-27. To zrodlo rzedu 1 dostawcy, ale opisuje **model H3 (wagi otwarte)**; przenoszenie na API H3 oznaczam wprost. Bezposrednie potwierdzenie dokumentacji API wymaga dopuszczenia hosta `platform.minimax.io` w sieci sesji.

Konwencje: `TAK`/`NIE` = stwierdzone w zrodle rzedu 1; `NIEPOTWIERDZONE` = poszlaka albo zrodlo nie wskazuje modelu; `BRAK DANYCH` = zrodla milcza (brak wzmianki to NIE jest "NIE"). Audio natywne modelu wideo jest **oddzielone** od osobnych uslug MiniMax (Speech/T2A, Voice Clone, Music) — te sa w sekcji 3.

## 1. Tabela zbiorcza (pola 1-10 zlecenia / S-R8)

| Pole | MiniMax-H3 | MiniMax-H3-Lite | MiniMax-Hailuo-2.3 | MiniMax-Hailuo-2.3-Fast |
|---|---|---|---|---|
| 1. Audio natywne | **TAK** — parametr `generate_audio` (boolean, opcjonalny, domyslnie `true`; `false` = wideo bez dzwieku) w `POST /v2/video_generation` (Z1, Z2); "native stereo audio", 32 kHz stereo (Z3, Z9) | **NIEPOTWIERDZONE** — `generate_audio` jest parametrem wspolnego endpointu v2 (wszystkie modele H3 maja wspolny protokol `content[]`, Z4), ale zaden fragment nie stwierdza wprost wyjscia audio dla Lite; RESEARCH-001 tez NIEPOTWIERDZONE | **BRAK DANYCH** — strony rzedu 1 (release notes 2025-10-28, model list, referencje T2V/I2V v1) opisuja tylko obraz (ruch, mimika, fizyka); w parametrach endpointu v1 (`prompt`, `duration`, `resolution`, `prompt_optimizer`, `fast_pretreatment`) brak parametru audio (Z5, Z6, Z7); brak zdania "bez dzwieku" | **BRAK DANYCH** — jw.; tylko I2V (Z6) |
| 1a. Zakres audio | dialog/mowa (tagi `<d>[Jezyk] ...</d>`), ambient i efekty (`overall_soundscape`), muzyka pozadiegetyczna (`non_diegetic_music`) (Z10); dialog, ambient, efekty, muzyka (Z11) | NIEPOTWIERDZONE | BRAK DANYCH | BRAK DANYCH |
| 2. Jeden przebieg | **TAK** — Omni-Transformer "jointly predicts video and audio latents" dekodowane do wideo i audio stereo (Z9, model); w API audio w tym samym zadaniu (`generate_audio` w zadaniu wideo, Z1) | NIEPOTWIERDZONE | BRAK DANYCH | BRAK DANYCH |
| 3. Jezyki mowy | stabilnie 11: arabski, chinski, angielski, francuski, niemiecki, wloski, japonski, koreanski, portugalski, rosyjski, hiszpanski; "Additional languages are also supported to varying degrees" (bez nazw) (Z9, Z3) | BRAK DANYCH | nie dotyczy (brak audio w zrodlach) | nie dotyczy |
| 3a. Status polskiego | **BRAK DANYCH** — polski nie jest na liscie 11 jezykow stabilnych; zdanie o "dodatkowych jezykach w roznym stopniu" nie wymienia polskiego, wiec to nie jest "NIE" (Z9) | **BRAK DANYCH** | **BRAK DANYCH** | **BRAK DANYCH** |
| 3b. Polski W PRAKTYCE | brak niezaleznych testow polskiej mowy H3 (wyszukiwanie 2026-11-27: testy Atlas Cloud tylko po chinsku, Z16; poradnik WaveSpeedAI bez polskiego, Z17) | jw. | jw. | jw. |
| 4. Lip-sync | **NIEPOTWIERDZONE** — dokumentacja i README nie opisuja lip-syncu jako funkcji ani parametru (Z9, Z10); jedynie przykladowe opisy w materialach dostawcy ("mouth movements naturally syncing to the new dialogue" — przyklad wyjscia Context-IR, Z9; edycja, w ktorej twarz postaci "speak[s] the user-provided dialogue", Z3). Rzad 4: lip-sync "mostly accurate", dryf w ostatnich 1-2 s (post spolecznosci, Z15); mieszane wyniki w testach chinskich (Z16) | BRAK DANYCH | BRAK DANYCH | BRAK DANYCH |
| 4a. Mowcy w klipie | **TAK (wielu)** — oficjalny przewodnik promptu: "Give vocal sources stable `(S1)`, `(S2)`, and subsequent IDs"; `(Sx)` = faktyczny mowca (Z10). Limit liczbowy: BRAK DANYCH | BRAK DANYCH | BRAK DANYCH | BRAK DANYCH |
| 5. Wylaczenie muzyki | **przez prompt** — pole `non_diegetic_music` = "N/A" w oficjalnym przykladzie (Z10); osobnego parametru muzyki w API BRAK DANYCH; `generate_audio=false` wycina cale audio (tez mowe). Rzad 4: "No background music." bywa ignorowane, model dodaje ambient mimo zakazu (Z15, Z18) — NIEPOTWIERDZONE skutecznosc | BRAK DANYCH (tylko `generate_audio`, jesli dziala — NIEPOTWIERDZONE) | BRAK DANYCH | BRAK DANYCH |
| 6. Wlasne audio / glos | **TAK** — `audio_url` (WAV/MP3, <= 15 MB, do 3 klipow, kazdy 2-15 s, lacznie <= 15 s) tylko w trybie reference (Z1, Z9); referencja barwy glosu postaci: "`<Audio 1>` is the voice-timbre reference for `<Subject 1>` (S1)" (Z10); audio referencyjne moze przenosic barwe, rytm, styl muzyki, **tresc dialogu** lub fakture dzwieku (Z10). Audio wejsciowe bezplatne (Z8). Wymaga obrazu lub wideo obok (Z1, starsza wersja) | **TAK** (wejscie) — Lite obsluguje reference-to-video z obrazem/wideo/**audio** (Z1, Z8) | BRAK DANYCH (endpoint v1 bez wejscia audio, Z5, Z7) | BRAK DANYCH |
| 7. Eksport audio osobno | **BRAK DANYCH** — zapytanie v2 zwraca jeden adres pobrania wideo (`content.url`), bez osobnej sciezki audio (Z12); model dekoduje audio osobno (Z9), ale API nie wystawia go jako pliku w znalezionych zrodlach | BRAK DANYCH | BRAK DANYCH | BRAK DANYCH |
| 8a. Klatka startowa (I2V) | **TAK z audio** — `generate_audio` ustawialny dla T2V, I2V i reference (Z2); `first_frame` / `last_frame`. **Uwaga:** I2V i reference wykluczaja sie — przy `first_frame`/`last_frame` nie wolno podac `audio_url` (Z1), wiec referencja glosu i klatka startowa nie ida razem | I2V (first/last frame) TAK (Z1); audio NIEPOTWIERDZONE | I2V TAK; audio BRAK DANYCH | tylko I2V; audio BRAK DANYCH |
| 8b. Przedluzanie / wideo wejsciowe | osobnego endpointu "extend" brak w zrodlach; kontynuacja klipu przez reference video (do 3 klipow, lacznie <= 15 s) — wzmianka "clip continuation" (Z3), zachowanie audio BRAK DANYCH. Regeneracja (`video-generation-v2-regeneration`): ustawienie audio dziedziczone; jesli zrodlo mialo `generate_audio=false`, wynik zawsze bez dzwieku (Z13) | BRAK DANYCH | BRAK DANYCH | BRAK DANYCH |
| 9. Cena z audio / bez (z RESEARCH-001) | 2K 0.13 USD/s = **7.80 USD/min** (nie Full HD; brak 1080P); 768P 0.08 USD/s = 4.80 USD/min. Cennik **nie rozroznia** audio; ta sama cena bez audio — NIEPOTWIERDZONE (zgodnie z RESEARCH-001; ponowne wyszukiwanie 2026-11-27 tez bez wierszy audio, Z8) | 768P 0.04 USD/s = **2.40 USD/min** (nie Full HD); cennik nie rozroznia audio | 1080P 0.49 USD/6 s = **4.90 USD/min**; audio nie dotyczy (BRAK DANYCH) | 1080P 0.33 USD/6 s = **3.30 USD/min**; audio nie dotyczy (BRAK DANYCH) |
| Data cennika (RESEARCH-001) | 2026-11-27 (data odczytu) | 2026-11-27 (data odczytu; brak daty na stronie) | 2026-11-27 (data odczytu) | 2026-11-27 (data odczytu) |
| 10. Zrodla rzedu 1 / pewnosc | Z1, Z2, Z3, Z9, Z10; **srednia** (API: odczyt posredni; README/ref: bezposredni, ale dla modelu otwartego) | Z1, Z4, Z8; **niska** (audio) / srednia (wejscie, cena) | Z5, Z6, Z7; **srednia** (brak wzmianki o audio) | Z5, Z6; **srednia** |

### Rozstrzygniecie BRAK DANYCH z RESEARCH-001 dla Hailuo 2.3 / 2.3-Fast

Zlecenie wezla prosi o rozstrzygniecie zrodlem rzedu 1. Wynik: **nie rozstrzygnieto — pozostaje BRAK DANYCH.** Zadne zrodlo rzedu 1 (release notes, model list, referencje endpointow v1, wpis "Hailuo 2.3" na minimax.io/news) nie mowi, ze Hailuo 2.3 generuje dzwiek, ani ze daje wideo nieme (Z5, Z6, Z7, Z14). Poszlaki przeciw audio: brak parametru audio w endpoincie v1; parametr `generate_audio` opisany wylacznie przy v2/H3 (Z2). Zgodnie z regula "brak wzmianki to BRAK DANYCH, a nie NIE" nie wpisuje NIE. Rozstrzygniecie wymaga bezposredniego odczytu `platform.minimax.io/docs/api-reference/video-generation-t2v` (pelna lista parametrow) albo testu (bez wykonywania w tym temacie).

## 2. Wstepna punktacja zgodnosci z ECHO-008 (dla syntezy; klucz ze zlecenia)

Klucz: audio natywne 2; jednoczesnosc 2; polski OFICJALNIE 3 (W PRAKTYCE 1); lip-sync 2; wielu mowcow 1; wylaczenie muzyki 1; audio/glos jako wejscie 1; eksport sciezki audio 1; max 13. Zasada (jak w wezle a): punkt tylko za `TAK` ze zrodla rzedu 1; `NIEPOTWIERDZONE`, `BRAK DANYCH`, `NIE` = 0. "Wylaczenie muzyki" = mozliwosc usuniecia muzyki przy zachowaniu dialogu; udokumentowana oficjalnie metoda promptowa liczy sie (1), sam `generate_audio=false` nie (0).

| Model | Audio (2) | Jedn. (2) | Polski (3) | Lip-sync (2) | Mowcy (1) | Bez muzyki (1) | Glos-wejscie (1) | Eksport (1) | Suma | Koszt 1 min (RESEARCH-001) |
|---|---|---|---|---|---|---|---|---|---|---|
| MiniMax-H3 | 2 | 2 | 0 | 0 | 1 | 1 | 1 | 0 | **7** | 7.80 (2K, nie Full HD) |
| MiniMax-H3-Lite | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | **1** | 2.40 (768P, nie Full HD) |
| MiniMax-Hailuo-2.3-Fast | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | **0** | 3.30 (1080P) |
| MiniMax-Hailuo-2.3 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | **0** | 4.90 (1080P) |

Kolejnosc wezla: 1. H3 (7), 2. H3-Lite (1), 3. Hailuo-2.3-Fast (0; remis rozstrzygniety nizszym kosztem 1 min), 4. Hailuo-2.3 (0).
Warianty warunkowe (NIE liczone): H3 z potwierdzonym lip-syncem = 9. H3-Lite, gdyby potwierdzono dla niego pola H3 (audio, jednoczesnosc, mowcy, muzyka promptem) = 7.

## 3. Uslugi audio MiniMax poza modelem wideo (NIE sa "audio natywnym")

- **Speech / T2A** (synchroniczne, asynchroniczne, WebSocket): przewodnik podaje 40 jezykow, **polski na liscie**; `language_boost` ma wartosc Polish (Z19). To osobne wywolanie TTS — **nie** jest jezykiem mowy modelu wideo i nie daje punktu "polski" w rankingu.
- **Voice Clone**: klonowanie glosu, `language_boost` z polskim (Z19). Osobna usluga.
- **Music**: osobny model muzyki (styl + tekst) (Z11). Osobna usluga.
- **Mozliwa droga dla polskiego (NIEPOTWIERDZONE, wymaga testu):** polska kwestia z T2A (oficjalnie polski) -> `audio_url` w trybie reference H3 (referencja moze przenosic "dialogue content", Z10) + obraz postaci. Ograniczenia: tryb reference wyklucza `first_frame` (Z1); czy H3 wiernie odda polski tekst i zsynchronizuje usta — brak zrodla; rzad 4 mowi o lip-syncu do `@Audio1`, ale z dodawanym ambientem i dryfem pod koniec klipu (Z15).

## 4. Spojnosc z RESEARCH-001 i zgloszenia (S-R10)

- **Lista i ceny** przepisane z `zestawienie.md` (poz. 1, 3, 13, 18) i `minimax.md` RESEARCH-001; data cennika 2026-11-27 (data odczytu). Niezgodnosci cen nie stwierdzilem.
- **N1 (H3 — cena bez audio):** jak w RESEARCH-001: cennik nie rozroznia audio; strona cennika podaje, ze dla tego samego modelu i rozdzielczosci wszystkie typy zadan maja te sama cene jednostkowa (Z8) — o audio nie mowi. Ta sama cena bez audio: NIEPOTWIERDZONE.
- **N2 (H3-Lite — audio):** RESEARCH-001 "nie (NIEPOTWIERDZONE)" — bez zmian w wyjsciu; nowa informacja: Lite przyjmuje audio jako wejscie referencyjne (Z1, Z8).
- **N3 (warianty H3 poza tabela RESEARCH-001):** H3-Max (cennik RESEARCH-001: 0.08 USD/s 768P), H3-Max-Turbo (0.04 USD/s 768P), H3-Highspeed (0.06 USD/s 768P). Biezaca referencja create wymienia jako dostepne: MiniMax-H3, -Highspeed, -Lite, -Max, -Max-Turbo, -MG, -NC (Z1, odczyt posredni) — wiec H3-Max-Turbo **jest** na liscie (RESEARCH-001 mial watpliwosc). Audio: changelog MiniMax Code (Z20) podaje dla H3 Max "synchronized audio generation" — to produkt agenta, nie dokumentacja API: dla API NIEPOTWIERDZONE. Pozostale: audio NIEPOTWIERDZONE.
- **N4 (modele nowsze niz RESEARCH-001 — zarzut do syntezy):** **MiniMax-H3-MG** (hostowany przez MachGen, do 2K; cennik wg wyszukiwarki: 768P 0.04 USD/s, 2K 0.10 USD/s T2V/I2V) i **MiniMax-H3-NC** ("H3 Fast by Nunchux AI", 480P/768P, 4-15 s; 768P 0.03 USD/s) (Z1, Z8, odczyt posredni). Ceny **nie** pochodza z RESEARCH-001, nie sa uzyte w rankingu i wymagaja weryfikacji w temacie cenowym. Audio: NIEPOTWIERDZONE (wspolny endpoint v2, brak zdania per model). Blog "The H3 Family" (2026-11-26, Z21) — tresci nie udalo sie odczytac (tylko tytul i streszczenie indeksu).
- **N5 (Hailuo 2.3):** RESEARCH-001 "nie (BRAK DANYCH)" — bez zmian, zob. sekcja 1 "Rozstrzygniecie".

## 5. Zrodla

Rzad 1 (oficjalne MiniMax), data odczytu 2026-11-27. "posr." = odczyt posredni przez wyszukiwarke (host zablokowany); "bezp." = odczyt bezposredni.
- Z1 https://platform.minimax.io/docs/api-reference/video-generation-v2-create — `generate_audio` (domyslnie true, false = nieme); `audio_url` tylko w reference (WAV/MP3, 15 MB, 3 klipy, 2-15 s, lacznie <= 15 s); I2V i reference wykluczaja sie; lista modeli H3 (w tym -MG, -NC); H3-Lite: T2V/I2V/reference (obraz/wideo/audio), 480P/768P, 4-15 s. posr.
- Z2 https://platform.minimax.io/docs/guides/video-generation — `generate_audio` dla T2V, I2V i reference; przyklad v2. posr.
- Z3 https://www.minimax.io/news/minimax-h3-open-source — 11 jezykow stabilnie + "additional languages ... varying degrees"; native stereo audio; przyklad edycji z dialogiem uzytkownika i barwa glosu z referencji; "clip continuation". posr.
- Z4 https://platform.minimax.io/docs/api-reference/api-overview — wspolny protokol `content[]` i zapytania dla wszystkich modeli. posr.
- Z5 https://platform.minimax.io/docs/api-reference/video-generation-t2v — Hailuo-2.3: `prompt`, `duration` 6/10, `resolution` 768P/1080P, `prompt_optimizer`, `fast_pretreatment`; brak parametru audio we fragmentach. posr.
- Z6 https://platform.minimax.io/docs/release-notes/models oraz https://platform.minimax.io/docs/release-notes/apis — Hailuo 2.3 i 2.3-Fast (2025-10-28), 2.3-Fast tylko I2V; opis bez audio. posr.
- Z7 https://platform.minimax.io/docs/api-reference/video-generation-i2v oraz https://platform.minimax.io/docs/faq/models — Hailuo T2V/I2V, bez audio. posr.
- Z8 https://platform.minimax.io/docs/pricing/overview oraz https://platform.minimax.io/docs/guides/pricing-video — ceny wg modelu i rozdzielczosci, bez wierszy audio; audio wejsciowe bezplatne; H3-Lite wejscia obraz/wideo/audio; H3-MG, H3-NC. posr.
- Z9 https://github.com/MiniMax-AI/MiniMax-H3 (README) — 11 jezykow; "32 kHz stereo"; Omni-Transformer "jointly predicts video and audio latents"; limity Ref2VA (audio <= 3 klipy, 2-15 s, lacznie <= 15 s); brak opisu lip-syncu, mowcow, przedluzania. bezp. (model otwarty).
- Z10 https://github.com/MiniMax-AI/MiniMax-H3/blob/main/skills/h3-prompt-writing/references/ref-en.txt — `<d>[Language] ...</d>`; `(S1)`, `(S2)` dla zrodel glosu; `<Audio 1>` jako referencja barwy glosu; `overall_soundscape`; `non_diegetic_music` = "N/A"; referencja "dialogue content". bezp.
- Z11 https://platform.minimax.io/docs/guides/video-prompt (H3 Feature Highlights) — dialog, efekty, muzyka w promptcie; https://platform.minimax.io/docs/guides/music-generation — osobny model muzyki. posr.
- Z12 https://platform.minimax.io/docs/api-reference/video-generation-v2-query — wynik: adres pobrania wideo `content.url`. posr.
- Z13 https://platform.minimax.io/docs/api-reference/video-generation-v2-regeneration — dziedziczenie `generate_audio`; zrodlo nieme = wynik nieme. posr.
- Z14 https://www.minimax.io/news/minimax-hailuo-23 — Hailuo 2.3: ruch, mimika, fizyka; bez wzmianki o audio. posr.
- Z19 https://platform.minimax.io/docs/guides/speech-t2a-async oraz https://platform.minimax.io/docs/api-reference/speech-t2a-http — T2A: 40 jezykow, Polish w `language_boost` (usluga TTS, nie wideo). posr.
- Z20 https://agent.minimax.io/docs/changelog — H3 Max z "synchronized audio generation" (produkt MiniMax Code, nie dokumentacja API). posr.
- Z21 https://www.minimax.io/blog/minimax-h3-family — "The H3 Family" (2026-11-26); tresci nie odczytano. posr.

Rzad 4-5 (poszlaka, NIEPOTWIERDZONE, nie uzyte w punktacji):
- Z15 https://www.minimax.io/community/m/1533272195890155722 — post uzytkownika: lip-sync do `@Audio1`, dryf w ostatnich 1-2 s, ambient mimo zakazu.
- Z16 https://www.atlascloud.ai/blog/tips/minimax-h3-chinese-dialogue-accuracy — test chinskiego dialogu (~83%), lip-sync mieszany; agregator.
- Z17 https://wavespeed.ai/blog/minimax-h3/minimax-h3-dialogue-speech-support/ — dialog trudniejszy niz ambient, dryf lip-syncu.
- Z18 https://gist.github.com/Naxdy/43b7422a1e4a79fb8b0489c6c39eaace — "No background music." czasem ignorowane bez ulepszenia promptu.

## 6. Niepewnosc / czego nie potwierdzono

1. Dokumentacja API tylko posrednio (blokada `platform.minimax.io`, `www.minimax.io`); wszystkie pola API wymagaja potwierdzenia przez Evaluatora z dostepem.
2. Polski: BRAK DANYCH dla wszystkich modeli; brak niezaleznych testow polskiej mowy.
3. Lip-sync H3: brak deklaracji funkcji w dokumentacji — tylko przyklady i rzad 4.
4. Audio H3-Lite, H3-Max, H3-Max-Turbo, H3-Highspeed, H3-MG, H3-NC: NIEPOTWIERDZONE per model.
5. Hailuo 2.3 / 2.3-Fast: audio BRAK DANYCH (nie rozstrzygnieto).
6. Cena H3 bez audio: NIEPOTWIERDZONE (cennik nie rozroznia).
7. Eksport osobnej sciezki audio: brak w zrodlach dla wszystkich modeli.
