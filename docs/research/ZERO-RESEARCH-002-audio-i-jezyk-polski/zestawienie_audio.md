# ZERO-RESEARCH-002 — zestawienie: audio natywne i jezyk polski w generatorach wideo AI

Data zestawienia: **2026-11-27**. Rola: Operator (synteza), runda 1 z 3.
Zakres: Kling (wezel a), Seedance / BytePlus ModelArk i Volcengine Ark (wezel b), Google Veo 3.1 i Gemini Omni Flash (wezel c), OpenAI Sora 2 (wezel d), MiniMax przez API (wezel e).
Dane: wylacznie z plikow wezlow w tym katalogu (stan PASS po rundzie 5; pliki tylko do odczytu) oraz z `docs/research/ZERO-RESEARCH-001-porownanie-generatorow-wideo/` (ceny, tylko odczyt). Zadnych nowych odczytow zrodel, wywolan API ani twierdzen z pamieci w syntezie. Punkty przeliczone od zera z tresci tabel pol wezlow (nie przepisane z punktacji wstepnych wezlow) — wynik zgodny z punktacjami wezlow.

Pliki wezlow (SHA-256 w chwili syntezy):
- `kling.md` a6742ebf2a36c0dab9eea06cadfe5cf6cc31a5ff0e0f843cf3eba3e509ca2671
- `seedance.md` 7eb598b6da6a9eed173ca113ef64f93eec5048ded4d38d01fb3a020ab1ccf7dd
- `veo.md` 48631cb60fa7dd550f90a29bf1762840c91b133b5a4beb25cffe038b6b8867f3
- `sora2.md` 6f9e7dc60c38cb6d4a907cbbac7f300459f144662d7f8035aef1cf5691432006
- `minimax.md` 54f1798bc4f325890bb67e75a1a42c4280b9ff2b40a93e636bcf1ebb621991cd

Konwencje (jak w wezlach): `TAK` / `NIE` = stwierdzone w zrodle rzedu 1; `NIEPOTWIERDZONE` = poszlaka, rzad 4-5 albo zrodlo nie wskazuje wprost modelu; `BRAK DANYCH` = zrodla milcza (to nie jest `NIE`). Status polskiego: `OFICJALNIE` tylko gdy zrodlo rzedu 1 wymienia polski jako jezyk mowy modelu wideo; `W PRAKTYCE` = niezalezny test lub opinia (rzad 4, NIEPOTWIERDZONE). Audio natywne modelu wideo jest oddzielone od osobnych uslug TTS / dubbingu / lip-sync dostawcy (sekcja 5).

## 1. Tabela wszystkich modeli (pola 1-9 z S-R8)

Skroty zrodel: `K-Zn` = `kling.md` zrodlo Zn, `S-Zn` = `seedance.md`, `V-Zn` = `veo.md`, `O-Zn` = `sora2.md`, `M-Zn` = `minimax.md`. Ceny: z RESEARCH-001 (USD za 1 minute; rozdzielczosc w nawiasie). URL-e zrodel rzedu 1 per pozycja w sekcji 3.

| # | Dostawca i model | Dostepny przez API 2026-11-27 | 1. Audio natywne; zakres | 2. Audio i wideo w jednym przebiegu | 3. Jezyki mowy; status polskiego | 4. Lip-sync; mowcy w klipie | 5. Wylaczenie muzyki (z zachowaniem dialogu) | 6. Wlasne audio / glos jako wejscie | 7. Eksport sciezki audio osobno | 8. Audio przy klatce startowej (I2V) / przy przedluzaniu | 9. Cena 1 min z audio / bez audio (RESEARCH-001); data cennika | Pewnosc |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Kling 4.0 (`kling-4.0`) | tak | TAK; dialog/lektor, ambient, muzyka, efekty, stereo (K-Z3, K-Z21) | TAK, AV-sync domyslnie w API (K-Z3) | ZH, EN, JA, KO, ES, PT, DE, FR, HI + "other languages" bez nazw (K-Z3, K-Z7); polski **BRAK DANYCH** | TAK (K-Z3); wielu, przyklad 3 mowcow, do 3 profili glosu, limit BRAK DANYCH (K-Z3, K-Z21) | TAK promptem "no background music" (K-Z3 sek. 8.7); calego audio nie da sie wylaczyc | TAK glos: `voice` z `voice_id`, maks. 3 (K-Z21, K-Z3) | NIEPOTWIERDZONE (ogolny schemat wynikow, K-Z22) | I2V: audio generowane (wniosek, pewnosc srednia, K-Z3, K-Z22) / przedluzanie "Coming Soon" (K-Z3) | 13.85 (1080p) / wariantu bez audio brak w cenniku; 2026-11-27 (odczyt) | wysoka (audio, jezyki, glos); srednia (I2V) |
| 2 | Kling 3.0 Omni (`kling-v3-omni`) | tak | TAK (`audio: native/original/off`); mowa, efekty, tlo; muzyka BRAK DANYCH (K-Z6, K-Z19) | TAK (K-Z6) | ZH, EN, JA, KO, ES (K-Z8); polski **BRAK DANYCH** | TAK (K-Z19); wielu (przyklad 2 postaci), limit BRAK DANYCH (K-Z19) | tylko cale audio (`audio: off`) — 0 | TAK glos: `element_voice_id` (K-Z25, K-Z19); wlasnej sciezki dialogu NIE | NIEPOTWIERDZONE (K-Z6) | I2V: TAK (`first_frame` + native, K-Z6) / przy wideo wejsciowym native niedostepne (K-Z6) | 8.40 / 6.72 (1080p); 2026-11-27 (odczyt) | wysoka / srednia (mowcy z przykladu) |
| 3 | Kling 3.0 | tak | TAK (`audio: native/off`); mowa, ambient (K-Z5, K-Z11, K-Z20) | TAK (K-Z5, K-Z20) | ZH, EN, JA, KO, ES; inne jezyki tlumaczone na angielski (K-Z11); polski **NIE** | TAK (K-Z11); wielu, "Multi-Character Coreference (3+)" (K-Z11) | tylko cale audio (`audio: off`) — 0 | TAK glos (voice tone control, element z glosem; K-Z11, K-Z20, K-Z25) | NIEPOTWIERDZONE (K-Z5) | I2V: TAK (`settings.audio` w I2V, K-Z20) / przedluzanie BRAK DANYCH | 10.08 (1080p) / brak w RESEARCH-001 (cennik: 6.72 — zgloszenie N-1); 2026-11-27 (odczyt) | wysoka |
| 4 | Kling 4.0 Flash | tak | TAK (omni-video `native` domyslnie); dialog, ambient, muzyka, efekty (K-Z23, K-Z3) | TAK (K-Z23) | NIEPOTWIERDZONE (tabela jezykow 4.0 bez przypisania do Flash); polski **BRAK DANYCH** | NIEPOTWIERDZONE; mowcy NIEPOTWIERDZONE (K-Z3, K-Z23) | TAK promptem (odeslanie K-Z23 -> K-Z3 sek. 8.7, pewnosc srednia) | **NIE** ("Voice Cloning: Not supported", K-Z3 sek. 5.1) | NIEPOTWIERDZONE (K-Z24) | I2V: NIEPOTWIERDZONE (T2V/I2V bez parametru audio; w omni-video `first_frame` + native, K-Z23, K-Z24) / przedluzania brak | 5.54 (720p, nie Full HD) / wariantu bez audio brak; 2026-11-27 (odczyt) | wysoka (audio) / srednia (muzyka) / niska (jezyki, lip-sync, mowcy) |
| 5 | Seedance 2.5 (`dreamina-seedance-2-5-260628`) | tak | TAK (`generate_audio`, domyslnie true); mowa, efekty, muzyka, ambient, stereo (S-Z1, S-Z2, S-Z3) | TAK, jedno zadanie (S-Z2) | 11 jezykow: ZH, EN, ES, ID, MS, TH, AR, PT, VI, JA, KO (S-Z1, S-Z12); polski **BRAK DANYCH** (brak na liscie) | TAK (S-Z3, S-Z1); co najmniej 2, limit BRAK DANYCH (S-Z3) | TAK promptem "no BGM" (S-Z3); dostawca opisuje przypadki niepelnego dzialania (S-Z13) | TAK `reference_audio` do 10 klipow, barwa glosu (S-Z2, S-Z1) | **NIE** (tylko `video_url`, S-Z6) | I2V: TAK (S-Z1, S-Z2; bez laczenia z `reference_audio`) / przedluzanie z ciagloscia audio TAK (S-Z3) | 34.12 (1080p) / ta sama cena; 2026-11-26 | wysoka |
| 6 | Seedance 2.5 flash (`...-2-5-flash-261115`) — poza tabela zestawienia RESEARCH-001 | tak | TAK; jw. (S-Z1, S-Z2, S-Z3) | TAK (S-Z2) | jw. (seria 2.5); polski **BRAK DANYCH** | TAK (S-Z3); co najmniej 2 (S-Z3) | TAK promptem (S-Z3, S-Z13) | TAK do 5 klipow (S-Z2, S-Z1) | **NIE** (S-Z6) | jw. | 9.07 (720p, nie Full HD; RESEARCH-001 `seedance.md` "poza tabela") / ta sama cena; 2026-11-26 | wysoka |
| 7 | Seedance 2.0 (`...-2-0-260128`) | tak | TAK; mowa, efekty, muzyka (S-Z2, S-Z5) | TAK (S-Z2) | lista nie podana; ZH, EN, inne wymagaja oznaczenia (S-Z5, S-Z15); polski **BRAK DANYCH** | BRAK DANYCH w rzedzie 1 (rzad 4 twierdzi TAK, NIEPOTWIERDZONE; S-Z9); co najmniej 2 (S-Z5) | tylko cale audio (`generate_audio: false`) — 0 | TAK `reference_audio` do 3 klipow (S-Z2, S-Z4) | **NIE** (S-Z6) | I2V: TAK (S-Z2) / przedluzanie jest, ciaglosc audio BRAK DANYCH (S-Z4) | 22.45 (1080p) / ta sama cena; 2026-11-26 | srednia |
| 8 | Seedance 2.0 Fast | tak | jw. | TAK | jw.; polski **BRAK DANYCH** | jw. | jw. — 0 | jw. | **NIE** | jw. | 7.26 (720p, nie Full HD) / ta sama cena; 2026-11-26 | srednia |
| 9 | Seedance 2.0 Mini | tak | jw. | TAK | jw.; polski **BRAK DANYCH** | jw. | jw. — 0 | jw. | **NIE** | jw. | 4.54 (720p, nie Full HD) / ta sama cena; 2026-11-26 | srednia |
| 10 | Gemini Omni 1.2 Flash (`gemini-omni-1.2-flash`, GA) | tak | TAK w kazdym wyjsciu; mowa, muzyka, efekty (V-Z5, V-Z9, V-Z10) | TAK (V-Z9, V-Z10) | "English (EN) is fully supported, but other languages have not been evaluated" (V-Z10); polski **BRAK DANYCH** | TAK "clearer lip-sync" (V-Z1); wielu, "distinct multi-speaker conditioning" (V-Z1) | tylko porada promptowa ("No dialogue", "No extra sound effects"), o muzyce wprost brak — 0 (V-Z10) | **NIE dla zwyklego konta** (V-Z9, V-Z10); referencje audio tylko po allowliscie (V-Z1) | BRAK DANYCH (wynik `video/mp4`, V-Z10) | I2V: TAK z audio (V-Z9, V-Z10) / przedluzanie z mowa TAK, do 30 s (Gemini API) lub 40 s (Vertex) (V-Z10, V-Z12) | 6.26 (1080p z upscalingu) / wariantu bez audio brak; 2026-11-27 | wysoka; srednia (muzyka) |
| 11 | Veo 3.1 (`veo-3.1-generate-001`) | tak (tylko Vertex; droga preview w Gemini API wylaczona 2026-10-22) | TAK; dialog, SFX, ambient, muzyka (V-Z2, V-Z4, V-Z6, V-Z7) | TAK (`generateAudio` domyslnie true, V-Z8) | EN "fully supported", inne "not evaluated" (V-Z7); polski **BRAK DANYCH** | TAK (V-Z2, V-Z4, V-Z7); wielu, "multi-person conversations" (V-Z4, V-Z7) | tylko cale audio (`generateAudio`) — 0 (V-Z8) | **NIE** ("Audio — Not supported", V-Z6) | BRAK DANYCH (wynik `gcsUris[]`, V-Z8) | I2V: TAK z audio (V-Z4, V-Z19) / przedluzanie +7 s do 37 s, ciaglosc glosu NIEPOTWIERDZONA (V-Z12) | 24.00 / 12.00 (1080p); 2026-11-27 | wysoka; srednia (przedluzanie) |
| 12 | Veo 3.1 Fast (`veo-3.1-fast-generate-001`) | tak (Vertex) | TAK (V-Z2, V-Z3, V-Z6) | TAK (V-Z2, V-Z8) | jw.; polski **BRAK DANYCH** | TAK wg "synchronized speech" (V-Z2), jakosc NIEPOTWIERDZONA; mowcy NIEPOTWIERDZONE | tylko cale audio — 0 | **NIE** (V-Z6) | BRAK DANYCH | I2V: obslugiwane, audio domyslnie, jakosc NIEPOTWIERDZONA (V-Z6, V-Z8) / przedluzanie obslugiwane, audio NIEPOTWIERDZONE (V-Z12) | 7.20 / 6.00 (1080p); 2026-11-27 | wysoka (pola 1-3, 6, 7); srednia (4, 8) |
| 13 | Veo 3.1 Lite (`veo-3.1-lite-generate-001`, Preview) | tak (Vertex, Preview) | TAK (V-Z2, V-Z3, V-Z6) | TAK (V-Z2, V-Z8) | jw.; polski **BRAK DANYCH** | TAK wg "synchronized speech" (V-Z2), jakosc NIEPOTWIERDZONA; mowcy NIEPOTWIERDZONE | tylko cale audio — 0 | **NIE** (V-Z6) | BRAK DANYCH | I2V: sprzecznosc w karcie modelu, audio NIEPOTWIERDZONE (V-Z6, N3) / przedluzanie preview, audio BRAK DANYCH (V-Z12) | 4.80 / 3.00 (1080p); 2026-11-27 | srednia |
| 14 | Gemini Omni 1.1 Flash (`gemini-omni-1.1-flash`) — od 2026-12-03 przekierowany na 1.2 | tak (do 2026-12-03) | TAK (V-Z5) | TAK | jw. (V-Z10); polski **BRAK DANYCH** | NIEPOTWIERDZONE (ulepszenia opisane dla 1.2); mowcy NIEPOTWIERDZONE | 0 (jak 1.2) | **NIE** (V-Z10) | BRAK DANYCH | BRAK DANYCH (opis w wezle tylko ogolny) | 9.12 (1080p z upscalingu; RESEARCH-001 `veo.md` "Dodatkowo") / wariantu bez audio brak; 2026-11-27 | srednia |
| 15 | MiniMax-H3 | tak | TAK (`generate_audio`, domyslnie true); dialog, ambient, efekty, muzyka, 32 kHz stereo (M-Z1, M-Z2, M-Z9, M-Z10) | TAK (M-Z1, M-Z9) | 11 stabilnie: AR, ZH, EN, FR, DE, IT, JA, KO, PT, RU, ES + "additional languages ... varying degrees" (M-Z9, M-Z3); polski **BRAK DANYCH** | NIEPOTWIERDZONE (brak deklaracji, tylko przyklady i rzad 4; M-Z9, M-Z15); wielu, `(S1)`, `(S2)` (M-Z10) | TAK promptem (`non_diegetic_music` = "N/A", M-Z10); skutecznosc wg rzedu 4 niepewna (M-Z15, M-Z18) | TAK `audio_url` do 3 klipow, barwa glosu (M-Z1, M-Z10) | BRAK DANYCH (wynik `content.url`, M-Z12) | I2V: TAK z audio, ale bez `audio_url` (M-Z1, M-Z2) / extend brak; regeneracja dziedziczy audio (M-Z13) | 7.80 (2K, nie Full HD; brak 1080P) / cennik nie rozroznia (ta sama cena NIEPOTWIERDZONE); 2026-11-27 (odczyt) | srednia (API odczyt posredni) |
| 16 | MiniMax-H3-Lite | tak | NIEPOTWIERDZONE (M-Z1, M-Z4) | NIEPOTWIERDZONE | BRAK DANYCH; polski **BRAK DANYCH** | BRAK DANYCH; BRAK DANYCH | BRAK DANYCH — 0 | TAK (wejscie audio w reference, M-Z1, M-Z8) | BRAK DANYCH | I2V TAK, audio NIEPOTWIERDZONE (M-Z1) / BRAK DANYCH | 2.40 (768P, nie Full HD) / cennik nie rozroznia; 2026-11-27 (odczyt) | niska (audio) / srednia (wejscie) |
| 17 | MiniMax-Hailuo-2.3-Fast (tylko I2V) | tak | BRAK DANYCH (endpoint v1 bez parametru audio, M-Z5, M-Z6) | BRAK DANYCH | nie dotyczy; polski **BRAK DANYCH** | BRAK DANYCH | BRAK DANYCH — 0 | BRAK DANYCH | BRAK DANYCH | I2V tak, audio BRAK DANYCH / BRAK DANYCH | 3.30 (1080P) / audio nie dotyczy; 2026-11-27 (odczyt) | srednia |
| 18 | MiniMax-Hailuo-2.3 (legacy) | tak | BRAK DANYCH (M-Z5, M-Z6, M-Z7) | BRAK DANYCH | nie dotyczy; polski **BRAK DANYCH** | BRAK DANYCH | BRAK DANYCH — 0 | BRAK DANYCH | BRAK DANYCH | jw. | 4.90 (1080P) / audio nie dotyczy; 2026-11-27 (odczyt) | srednia |
| 19 | OpenAI `sora-2-pro` | **NIE — API wylaczone 2026-09-24** (O-Z1, O-Z2, O-Z17) | TAK (historycznie); mowa, efekty, ambient; muzyka NIEPOTWIERDZONE (O-Z3, O-Z17) | TAK (O-Z5, O-Z17, O-Z18) | BRAK DANYCH; polski **BRAK DANYCH** | TAK (O-Z3, O-Z6); wielu (O-Z6) | TAK promptem ("No added score", O-Z6) | NIE (wlasna sciezka); glos BRAK DANYCH (O-Z5, O-Z18) | **NIE** (`variant` bez audio, O-Z8) | I2V: audio BRAK DANYCH / przedluzanie: audio BRAK DANYCH (O-Z18) | 42.00 (1080p); 18.00 (720p); 30.00 (1024p) / wariantu bez audio brak; 1080p: 2026-03-12, reszta odczyt 2026-11-27 | wysoka (status niedostepnosci, parametry) |
| 20 | OpenAI `sora-2` | **NIE — API wylaczone 2026-09-24** | jw. | TAK | jw.; polski **BRAK DANYCH** | jw. | jw. | jw. | **NIE** | jw. | 6.00 (720p, nie Full HD) / wariantu bez audio brak; odczyt 2026-11-27 (cennik archiwalny) | wysoka |

## 2. Ranking zgodnosci z wymaganiami ZERO (ECHO-008)

### 2.1 Jawna punktacja

| Kryterium | Punkty | Kiedy przyznane |
|---|---|---|
| Audio natywne | 2 | pole 1 = `TAK` w zrodle rzedu 1 |
| Jednoczesnosc audio i wideo (jeden przebieg) | 2 | pole 2 = `TAK` |
| Jezyk polski | 3 za `OFICJALNIE`; 1 za `W PRAKTYCE` | status polskiego z pola 3 |
| Lip-sync | 2 | pole 4 (lip-sync) = `TAK` |
| Wielu mowcow w klipie | 1 | pole 4 (mowcy) = co najmniej 2 mowcow stwierdzonych w zrodle rzedu 1 (opis lub przyklad dostawcy) |
| Wylaczenie muzyki | 1 | udokumentowana mozliwosc usuniecia muzyki **przy zachowaniu dialogu** (parametr albo oficjalna metoda promptowa); samo wylaczenie calego audio = 0 |
| Audio / glos jako wejscie | 1 | pole 6 = `TAK` dla zwyklego konta (funkcja tylko po allowliscie = 0) |
| Eksport sciezki audio osobno | 1 | pole 7 = `TAK` |
| **Maksimum** | **13** | |

Zasada wspolna: `NIEPOTWIERDZONE`, `BRAK DANYCH`, `NIE` = 0 pkt. Zrodla rzedu 4-5 nie daja punktow.
Kolejnosc: malejaco po sumie punktow. Remisy: tanszy koszt 1 minuty z RESEARCH-001, przy czym — zgodnie z konwencja RESEARCH-001 (S-R4) — najpierw pozycje z cena przy 1080p (koszt 1 minuty Full HD, sekcja A RESEARCH-001), potem pozycje bez ceny przy 1080p (sekcja B), kazda grupa rosnaco po swoim koszcie. Modele niedostepne przez API (Sora 2) sa poza rankingiem (ECHO-024: pozycja informacyjna), z punktami historycznymi w 2.3.

### 2.2 Ranking modeli dostepnych przez API (punkty przeliczone od zera z pol tabeli 1)

| Miejsce | Model | Audio (2) | Jedn. (2) | Polski (3) | Lip-sync (2) | Mowcy (1) | Bez muzyki (1) | Audio/glos wejscie (1) | Eksport (1) | **Suma (max 13)** | Koszt 1 min (RESEARCH-001) — rozstrzyga remis |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Kling 4.0 | 2 | 2 | 0 | 2 | 1 | 1 | 1 | 0 | **9** | 13.85 (1080p) |
| 2 | Seedance 2.5 | 2 | 2 | 0 | 2 | 1 | 1 | 1 | 0 | **9** | 34.12 (1080p) |
| 3 | Seedance 2.5 flash | 2 | 2 | 0 | 2 | 1 | 1 | 1 | 0 | **9** | 9.07 (720p, bez 1080p) |
| 4 | Kling 3.0 Omni | 2 | 2 | 0 | 2 | 1 | 0 | 1 | 0 | **8** | 8.40 (1080p) |
| 5 | Kling 3.0 | 2 | 2 | 0 | 2 | 1 | 0 | 1 | 0 | **8** | 10.08 (1080p) |
| 6 | Gemini Omni 1.2 Flash | 2 | 2 | 0 | 2 | 1 | 0 | 0 | 0 | **7** | 6.26 (1080p, upscaling) |
| 7 | Veo 3.1 | 2 | 2 | 0 | 2 | 1 | 0 | 0 | 0 | **7** | 24.00 (1080p) |
| 8 | MiniMax-H3 | 2 | 2 | 0 | 0 | 1 | 1 | 1 | 0 | **7** | 7.80 (2K, bez 1080p) |
| 9 | Veo 3.1 Lite | 2 | 2 | 0 | 2 | 0 | 0 | 0 | 0 | **6** | 4.80 (1080p) |
| 10 | Veo 3.1 Fast | 2 | 2 | 0 | 2 | 0 | 0 | 0 | 0 | **6** | 7.20 (1080p) |
| 11 | Seedance 2.0 | 2 | 2 | 0 | 0 | 1 | 0 | 1 | 0 | **6** | 22.45 (1080p) |
| 12 | Seedance 2.0 Mini | 2 | 2 | 0 | 0 | 1 | 0 | 1 | 0 | **6** | 4.54 (720p, bez 1080p) |
| 13 | Seedance 2.0 Fast | 2 | 2 | 0 | 0 | 1 | 0 | 1 | 0 | **6** | 7.26 (720p, bez 1080p) |
| 14 | Kling 4.0 Flash | 2 | 2 | 0 | 0 | 0 | 1 | 0 | 0 | **5** | 5.54 (720p, bez 1080p) |
| 15 | Gemini Omni 1.1 Flash (wygasa 2026-12-03) | 2 | 2 | 0 | 0 | 0 | 0 | 0 | 0 | **4** | 9.12 (1080p, upscaling) |
| 16 | MiniMax-H3-Lite | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | **1** | 2.40 (768P, bez 1080p) |
| 17 | MiniMax-Hailuo-2.3-Fast | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | **0** | 3.30 (1080P) |
| 18 | MiniMax-Hailuo-2.3 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | **0** | 4.90 (1080P) |

Kontrola sum (wiersz = suma kolumn): 9 = 2+2+0+2+1+1+1+0; 8 = 2+2+0+2+1+0+1+0; 7 (Omni 1.2, Veo 3.1) = 2+2+0+2+1+0+0+0; 7 (H3) = 2+2+0+0+1+1+1+0; 6 (Veo Lite/Fast) = 2+2+0+2+0+0+0+0; 6 (Seedance 2.0) = 2+2+0+0+1+0+1+0; 5 = 2+2+0+0+0+1+0+0; 4 = 2+2; 1 = 1; 0 = 0.

Rozstrzygniecia remisow:
- 9 pkt: Kling 4.0 (13.85, 1080p) przed Seedance 2.5 (34.12, 1080p); Seedance 2.5 flash (bez 1080p) za nimi.
- 8 pkt: Kling 3.0 Omni (8.40) przed Kling 3.0 (10.08).
- 7 pkt: Gemini Omni 1.2 Flash (6.26) przed Veo 3.1 (24.00); MiniMax-H3 (bez ceny 1080p) za nimi.
- 6 pkt: Veo 3.1 Lite (4.80) < Veo 3.1 Fast (7.20) < Seedance 2.0 (22.45); potem bez 1080p: Seedance 2.0 Mini (4.54) < Seedance 2.0 Fast (7.26).
- 0 pkt: Hailuo-2.3-Fast (3.30) przed Hailuo-2.3 (4.90).

Zgodnosc z wezlami: wszystkie sumy przeliczone tu sa rowne punktacjom wstepnym w plikach wezlow (kling.md sek. 2, seedance.md "Punktacja wstepna", veo.md sek. 2, sora2.md sek. 2, minimax.md sek. 2). Kolejnosc wewnatrz wezlow tez zgodna.

### 2.3 Poza rankingiem — modele niedostepne (Sora 2, punkty historyczne)

| Model | Audio | Jedn. | Polski | Lip-sync | Mowcy | Bez muzyki | Wejscie | Eksport | Suma | Koszt 1 min (RESEARCH-001) |
|---|---|---|---|---|---|---|---|---|---|---|
| sora-2-pro | 2 | 2 | 0 | 2 | 1 | 1 | 0 | 0 | **8** | 42.00 (1080p) |
| sora-2 | 2 | 2 | 0 | 2 | 1 | 1 | 0 | 0 | **8** | 6.00 (720p) |

API Videos, `sora-2` i `sora-2-pro` wylaczone 2026-09-24, bez zastepcy (sora2.md sek. 0; O-Z1, O-Z2, O-Z17). Z punktow nie da sie skorzystac.

## 3. Zrodla per pozycja (rzad 1, data odczytu 2026-11-27, wg plikow wezlow)

1. Kling 4.0: https://kling.ai/document-api/api/usage-guide/kling-4-0 ; https://kling.ai/quickstart/kling-4-model-user-guide ; https://kling.ai/document-api/api/video/4-0/video-omni ; https://kling.ai/document-api/api/video/4-0/text-to-video ; https://kling.ai/document-api/api/video/4-0/image-to-video ; https://kling.ai/document-api/pricing/base/video
2. Kling 3.0 Omni: https://kling.ai/document-api/api/video/3-0-omni/video-omni ; https://kling.ai/quickstart/klingai-video-3-omni-model-user-guide ; https://kling.ai/feature/lip-sync ; https://kling.ai/document-api/api/video/3-0-omni/elements ; https://kling.ai/document-api/pricing/base/video
3. Kling 3.0: https://kling.ai/document-api/api/video/3-0-omni/text-to-video ; https://kling.ai/document-api/api/video/3-0-omni/image-to-video ; https://kling.ai/quickstart/klingai-video-3-model-user-guide ; https://kling.ai/document-api/pricing/base/video
4. Kling 4.0 Flash: https://kling.ai/document-api/api/video/4-0-flash/video-omni ; https://kling.ai/document-api/api/video/4-0-flash/text-to-video ; https://kling.ai/document-api/api/video/4-0-flash/image-to-video ; https://kling.ai/document-api/api/usage-guide/kling-4-0 ; https://kling.ai/document-api/pricing/base/video
5. Seedance 2.5: https://docs.byteplus.com/en/docs/modelark/seedance-2-5 ; https://docs.byteplus.com/en/docs/modelark/create-video-generation-task-api ; https://docs.byteplus.com/en/docs/modelark/seedance-2-5-prompt-guide ; https://docs.byteplus.com/en/docs/modelark/get-video-generation-task-api ; https://docs.volcengine.com/docs/ark/seedance-2-5?lang=zh ; https://docs.volcengine.com/docs/ark/seedance-2-5-prompt-guide?lang=zh ; https://docs.byteplus.com/en/docs/modelark/model-pricing
6. Seedance 2.5 flash: jak poz. 5 (te same dokumenty serii 2.5)
7-9. Seedance 2.0 / 2.0 Fast / 2.0 Mini: https://docs.byteplus.com/en/docs/modelark/seedance-2-0 ; https://docs.byteplus.com/en/docs/modelark/seedance-2-0-prompt-guide ; https://docs.byteplus.com/en/docs/modelark/create-video-generation-task-api ; https://docs.byteplus.com/en/docs/modelark/get-video-generation-task-api ; https://docs.volcengine.com/docs/ark/seedance-2-0?lang=zh ; https://docs.volcengine.com/docs/ark/seedance-2-0-prompt-guide?lang=zh ; https://docs.byteplus.com/en/docs/modelark/model-pricing
10. Gemini Omni 1.2 Flash: https://cloud.google.com/blog/products/ai-machine-learning/gemini-omni-1-2-flash-generally-available ; https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/gemini/omni-1-2-flash ; https://aistudio.google.com/docs/omni ; https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/video/extend-videos ; https://cloud.google.com/vertex-ai/generative-ai/pricing
11-13. Veo 3.1 / Fast / Lite: https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/veo/3-1-generate ; https://docs.cloud.google.com/gemini-enterprise-agent-platform/reference/rest/Shared.Types/VideoGenerationModelParams ; https://aistudio.google.com/docs/veo ; https://cloud.google.com/blog/products/ai-machine-learning/ultimate-prompting-guide-for-veo-3-1 ; https://cloud.google.com/blog/products/ai-machine-learning/veo-3-1-lite-and-a-new-veo-upscaling-capability-on-vertex-ai ; https://cloud.google.com/vertex-ai/generative-ai/pricing
14. Gemini Omni 1.1 Flash: https://cloud.google.com/blog/products/ai-machine-learning/nano-banana-2-lite-and-gemini-omni-flash-available ; https://aistudio.google.com/docs/omni ; https://aistudio.google.com/docs/deprecations
15. MiniMax-H3: https://platform.minimax.io/docs/api-reference/video-generation-v2-create (odczyt posredni) ; https://platform.minimax.io/docs/guides/video-generation (posredni) ; https://github.com/MiniMax-AI/MiniMax-H3 (bezposredni, model otwarty) ; https://github.com/MiniMax-AI/MiniMax-H3/blob/main/skills/h3-prompt-writing/references/ref-en.txt (bezposredni) ; https://platform.minimax.io/docs/api-reference/video-generation-v2-query (posredni)
16. MiniMax-H3-Lite: https://platform.minimax.io/docs/api-reference/video-generation-v2-create ; https://platform.minimax.io/docs/pricing/overview (posredni)
17-18. MiniMax-Hailuo-2.3-Fast / 2.3: https://platform.minimax.io/docs/api-reference/video-generation-t2v ; https://platform.minimax.io/docs/release-notes/models ; https://platform.minimax.io/docs/api-reference/video-generation-i2v (posredni)
19-20. Sora 2 / Sora 2 Pro: https://developers.openai.com/api/docs/deprecations ; https://help.openai.com/en/articles/20001152-what-to-know-about-the-sora-discontinuation ; https://developers.openai.com/api/docs/models/sora-2 ; https://developers.openai.com/api/docs/models/sora-2-pro ; https://developers.openai.com/api/reference/resources/videos/methods/create ; https://developers.openai.com/cookbook/examples/sora/sora2_prompting_guide ; https://developers.openai.com/api/reference/resources/videos/methods/download_content ; https://openai.com/index/sora-2/

Zrodla rzedu 4-5 (NIEPOTWIERDZONE, nie daja punktow): K-Z14 (atlascloud.ai), S-Z9 (artykuly volcengine.com/article), V-Z15 (discuss.ai.google.dev), V-Z16 (android.com.pl), O-Z9, O-Z10, O-Z10b, O-Z11, M-Z15-M-Z18.

## 4. Spojnosc z RESEARCH-001 (S-R10) — zgloszenia

Ceny z audio i bez audio oraz daty cennika we wszystkich wierszach tabeli 1 sa przepisane z RESEARCH-001 (`zestawienie.md` poz. 1-20, uwagi sek. 4; dla Seedance 2.5 flash i Omni 1.1 — pliki wezlow `seedance.md` i `veo.md` RESEARCH-001). Niezgodnosci cen nie stwierdzono w zadnym wezle. Zgloszenia:
- **Z-1 (model poza zestawieniem, nowszy):** Seedance 2.5 flash — dostepny przez API, nieobecny w tabeli `zestawienie.md` RESEARCH-001 (tylko "poza tabela" w wezle). Ujety w rankingu (poz. 3).
- **Z-2 (modele poza lista):** Kling 3.0 Turbo (w API od 2026-06-17, swiadomie pominiety w RESEARCH-001; kling.md N5); MiniMax-H3-Max, -Max-Turbo, -Highspeed, oraz nowsze -MG, -NC (minimax.md N3, N4; audio per model NIEPOTWIERDZONE). Nieopisane w tabeli i rankingu.
- **Z-3 (audio Kling 4.0 Flash):** RESEARCH-001 "nie (NIEPOTWIERDZONE)", wezel ustala TAK (K-Z23) — niezgodnosc kolumny "audio natywne" RESEARCH-001.
- **Z-4 (Kling 3.0 bez audio):** cena 6.72 USD/min (1080p) jest w cenniku (K-Z1), brak jej w RESEARCH-001 (kling.md N1).
- **Z-5 (Veo 3.1 na Vertex):** karta modelu podaje "Pay-as-you-go — Not supported" (V-Z6; veo.md N8) — mozliwa niezgodnosc z zalozeniem rozliczenia pay-as-you-go dla Veo 3.1 / Fast / Lite w RESEARCH-001. Droga Veo 3.1 preview w Gemini API wylaczona 2026-10-22 (veo.md N1).
- **Z-6 (Gemini Omni 1.1 Flash):** od 2026-12-03 zapytania przekierowane na 1.2 (veo.md, V-Z10, V-Z17).
- **Z-7 (Sora 2):** dodatkowy snapshot `sora-2-2025-12-08` i daty Azure inne niz w RESEARCH-001 (sora2.md N1, N2); wniosek bez zmian — niedostepne.

## 5. Narzedzia audio poza modelem wideo (nie liczone w rankingu)

Polski jest **oficjalnie** obslugiwany przez osobne uslugi TTS dwoch dostawcow: Gemini TTS / Cloud TTS (Polish ✔, pl-PL GA; veo.md sek. 3, V-Z13) oraz MiniMax Speech T2A i Voice Clone (polski na liscie, `language_boost`; minimax.md sek. 3, M-Z19 — odczyt posredni). Kling TTS: polski NIE (tylko zh/en, K-Z18); Kling Lip Sync przyjmuje wgrane audio, jezyki BRAK DANYCH (K-Z17, K-Z8). OpenAI gpt-realtime-translate (polski) nie jest czescia Sory (sora2.md sek. 3). To sa osobne wywolania (dubbing/TTS), nie audio natywne — nie zmieniaja statusu polskiego modeli wideo.

## 6. Uwagi o niepewnosci

1. **Polski:** zaden model wideo nie ma statusu `OFICJALNIE` — status ten przysluguje tylko tam, gdzie zrodlo rzedu 1 wymienia polski jako jezyk mowy modelu, a zadne takie zrodlo nie zostalo znalezione. Zaden nie ma tez `W PRAKTYCE` (brak niezaleznych testow polskiej mowy w wezlach). Jedyne `NIE`: Kling 3.0 (lista 5 jezykow + tlumaczenie innych na angielski, K-Z11). Pozostale: `BRAK DANYCH` — w tym Seedance 2.5 (polskiego brak na jawnej liscie 11 jezykow: silna poszlaka, ale nie `NIE`), Kling 4.0 ("and other languages"), MiniMax-H3 ("additional languages ... varying degrees"), Veo / Omni ("other languages have not been evaluated"). Kolumna "Polski" daje 0 wszystkim modelom, wiec nie rozroznia rankingu; rozstrzygnie tylko test probny.
2. **Lip-sync Veo 3.1 Fast i Lite** opiera sie na zwrocie "synchronized speech" z cennika (V-Z2) — synchronizacja mowy z obrazem bez opisu ruchu ust; punkty przyznane jak w wezle, pewnosc srednia.
3. **Wylaczenie muzyki** (ECHO-008: dzwiek z modelu nie uchyla zasady "bez muzyki w klipach"): mozliwosc usuniecia samej muzyki przy zachowaniu dialogu jest udokumentowana tylko promptem (Kling 4.0, 4.0 Flash, Seedance 2.5 i 2.5 flash, MiniMax-H3, historycznie Sora 2). Zaden dostawca nie ma osobnego parametru "bez muzyki". Seedance (S-Z13) i rzad 4 dla MiniMax (M-Z15, M-Z18) opisuja, ze zakaz muzyki nie zawsze dziala. Kling 4.0 / 4.0 Flash i Gemini Omni nie pozwalaja wylaczyc calego audio; Kling 3.x, Seedance, Veo, MiniMax-H3 — pozwalaja (wtedy znika tez mowa). Ostateczna regula audio pozostaje do decyzji wlasciciela (ECHO-008).
4. **Eksport osobnej sciezki audio:** zaden model nie ma `TAK` (Seedance, Sora — `NIE`; reszta — `BRAK DANYCH` / `NIEPOTWIERDZONE`). Sciezke da sie wyodrebnic wlasnym narzedziem z pliku wideo; to nie jest funkcja dostawcy i nie daje punktu.
5. **Wielu mowcow:** zaden dostawca nie podaje liczbowego limitu; punkty wynikaja z opisow lub przykladow dostawcy.
6. **MiniMax:** dokumentacja API odczytana posrednio (blokada hostow w rundzie 1 wezla); audio Hailuo 2.3 / 2.3-Fast nierozstrzygniete (BRAK DANYCH, 0 pkt); H3-Lite audio NIEPOTWIERDZONE (warunkowo 7 pkt, gdyby potwierdzono — nieliczone).
7. **Warianty nieliczone:** Gemini Omni 1.2 Flash +1 po allowliscie referencji audio (8); Veo 3.1 Fast / Lite +1, gdyby dialog wielu osob potwierdzono wprost dla tych modeli (7); MiniMax-H3 +2 z potwierdzonym lip-synciem (9).
8. **Regula remisu:** przy porownaniu wylacznie po surowym koszcie 1 minuty (bez podzialu na 1080p / bez 1080p) zmienilyby sie trzy grupy: 9 pkt — Seedance 2.5 flash (9.07) przed Kling 4.0 i Seedance 2.5; 7 pkt — MiniMax-H3 (7.80) przed Veo 3.1 (24.00); 6 pkt — Seedance 2.0 Mini (4.54) na pierwszym miejscu grupy, Seedance 2.0 Fast (7.26) przed Seedance 2.0 (22.45). Sumy punktow sie nie zmieniaja. Zastosowano konwencje RESEARCH-001 (koszt Full HD najpierw).
9. **Ceny przy roznych rozdzielczosciach** (720p, 768P, 2K) nie sa kosztem Full HD — oznaczone w tabeli.

## 7. OPINIA (opinia Operatora syntezy, nie fakt; tylko z danych powyzej)

- OPINIA: zaden model nie ma udokumentowanego polskiego; jezyk mowy ZERO rozstrzygnie dopiero test probny jednego klipu z polskim dialogiem.
- OPINIA: najwiecej punktow (9) maja Kling 4.0 i Seedance 2.5; Kling 4.0 jest 2,5 raza tanszy przy 1080p (13.85 vs 34.12 USD/min).
- OPINIA: oba pozwalaja usunac muzyke tylko promptem, wiec zasada "bez muzyki" wymaga sprawdzenia w tescie.
- OPINIA: Gemini Omni 1.2 Flash (7 pkt, 6.26 USD/min) to najtansza pozycja z lip-synciem i wieloma mowcami, ale bez wejscia glosu.
- OPINIA: droga awaryjna dla polskiego to oficjalny polski TTS (Google lub MiniMax) plus model przyjmujacy audio/glos jako wejscie (Kling, Seedance, MiniMax-H3) — wymaga testu.
- OPINIA: Sora 2 nie wchodzi w gre (API wylaczone); Hailuo 2.3 bez danych o audio nie spelnia wymogu dzwieku z modelu.
