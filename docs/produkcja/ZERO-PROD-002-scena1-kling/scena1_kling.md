# ZERO — E01 ADAM — Scena 1 — plik produkcyjny dla Kling 4.0

Temat: ZERO-PROD-002-scena1-kling (ECHO-036, sprostowanie ECHO-037: narzedzie docelowe = **Kling 4.0**, nie Seedance, nie Veo). Rola: Operator (Opus 5.5), runda 3 z 3 (poprawki rund 2-3: E-1-x, E-2-1). Data: 2026-11-28.
Status: plan wzorcowy do pierwszego testu. Niczego nie wygenerowano, nie wywolano API ani MCP, nie zalozono kont ani kluczy (granice zlecenia).

**Zastrzezenie nadrzedne (czytac najpierw).** Os czasu w tym pliku jest zapisana co do milisekundy i co do klatki, ale **to jest plan i kryterium kontroli, a nie gwarancja generatora**. Zatwierdzone badania nie podaja zadnego parametru, ktory pozwalalby Klingowi 4.0 kazac rozpoczac kwestie w zadanej milisekundzie: API przyjmuje tekst promptu, dlugosc klipu w pelnych sekundach i referencje (R003 `kling.md` sek. 4), a synchronizacja obrazu z dzwiekiem jest deklaracja dostawcy ("naturally synchronized", R008 sek. B.2). Czasy w promptach sa wskazowka dla modelu. Precyzje do klatki osiaga sie dopiero procedura z sekcji 6: pomiar transkrypcja ze znacznikami slow, porownanie z osia czasu, korekta w montazu albo powtorka klipu.

## Zrodla i skroty

| Skrot | Plik (tylko odczyt) | Rzad |
|---|---|---|
| SCEN | `scenariusze/ZERO_mini_serial_E01_ADAM_rev.md`, SCENA 1, linie 62-123 (SHA-256 `b0264c950cbafe7181234554136f6cb65a826c12c88a96730917f9c0825f4340`, zgodny z `scenariusze/MANIFEST.sha256`) | 1 (rozstrzyga tresc) |
| ECHO | `autobot/DECYZJE.md` (ECHO-008, 020, 027, 036, 037) | 2 |
| R001 | `docs/research/ZERO-RESEARCH-001-porownanie-generatorow-wideo/kling.md` | zatwierdzone badanie |
| R002 | `docs/research/ZERO-RESEARCH-002-audio-i-jezyk-polski/kling.md` | zatwierdzone badanie |
| R003 | `docs/research/ZERO-RESEARCH-003-api-i-mcp-sterowanie/kling.md` | zatwierdzone badanie |
| R005 | `docs/research/ZERO-RESEARCH-005-zestawienie-zbiorcze/zestawienie_zbiorcze.md` | zatwierdzone badanie |
| R008 | `docs/research/ZERO-RESEARCH-008-omni-vs-kling-jakosc/omni_vs_kling.md` | zatwierdzone badanie (wpisy rzedu 4 = NIEPOTWIERDZONE) |
| ROZP | archiwum: `ZERO_produkcja_flow/ZERO_E01_rozpiska_sekundowa.md`, sekcja SCENA 1 (8 ujec U1-U8, tempo 2,5-3 sl/s) | 4 |
| BEAT | archiwum: `ZERO_produkcja_flow/ZERO_Scena1_beaty_7s_ENG.md` oraz `ZERO_E01_S1_Clip00..11.md` (Clip10 pusty) | 4 |
| FLOW | uploads: `ZERO_instrukcje_dla_agenta_Flow.md`, `ZERO_INSTRUKCJA_Flow_scena1_ciaglosc.md`, `ZERO_metoda_AB_montaz.md` (w archiwum `ZERO_INSTRUKCJA_Flow_scena1_ciaglosc.md` jest pusty, uzyto kopii z uploads) | 4 |
| VEO | archiwum: `ZERO_VEO3_E01_Scena1_FULL_ENG.md` i `_FULL_ENG_edited.md` | 4 |
| PROD | archiwum `ZERO_E01_produkcja/`: `01_nota_rezyserska.md`, `02_charakterystyki_postaci.md`, `03_opisy_wizualne_scen.md`, `04_dzwiek_i_muzyka.md`, `05_inserty_closeup.md`, `06_przejscia_scen.md`, `07_podtekst_dialogowy.md`, `08_noty_techniczne.md`; oraz `ZERO_decyzje_rewizja.md`, `ZERO_repercusje_spojnosc.md`, `ZERO_konsultacja_scenariuszowa.md`, `ZERO_porownanie_Veo_vs_Kling.md` | 4 |

Hierarchia przy sprzecznosci (zlecenie): SCEN > ECHO > dokumenty produkcyjne (rzad 4). Przy konflikcie o czasie: SCEN i ROZP, z adnotacja. `ZERO_porownanie_Veo_vs_Kling.md` dotyczy Kling 2.6/3.0 i nie jest podstawa zadnego twierdzenia o Klingu 4.0 w tym pliku.

Konwencje: `BRAK DANYCH` = zatwierdzone badania milcza (podany sposob sprawdzenia w pierwszym tescie); `NIEPOTWIERDZONE` = zrodlo rzedu 4 albo wniosek; `ZALOZENIE` = przyjete na potrzeby planu, do zmierzenia; `PROPOZYCJA` = nie kanon (G2, G3). Tekst roboczy po polsku bez diakrytykow (styl repozytorium); kanon polski cytowany doslownie z diakrytykami; prompty i dialogi do wklejenia po angielsku.

---

## 0. Cel i sposob uzycia

**Cel.** Jeden plik, z ktorego wlasciciel generuje Scene 1 E01 (Nowy Swiat, murek, Karolina i Michal, telefon od Marty, "kawa po wykladzie", pusty murek) w Klingu 4.0 klip po klipie, a potem sklada ja w montazu tak, zeby kazda kwestia, kazdy dzwiek tla i kazde zdarzenie obrazu stalo w zaplanowanej milisekundzie (klatce) albo zostalo do niej dociagniete.

**Jak czytac plik.** Sekcja 4 jest jedyna os czasu (master timeline). Sekcja 5 zawiera prompty wyprowadzone z sekcji 4 tym samym skryptem (czasy w promptach = czasy lokalne klipu z sekcji 4). Sekcja 6 mowi, jak sprawdzic wynik i co zrobic przy odchyleniu.

**Kolejnosc pracy (obie drogi).**
1. Przygotowac zasoby z sekcji 3 (zdjecia referencyjne, plansze tla, probki glosu). W repozytorium ich nie ma.
2. Test zerowy (sekcja 7, poz. 4): jeden klip K05 albo K04 na najnizszym koszcie, zeby zmierzyc fps i tempo mowy; to, czy `omni_ref_video` przyjmuje `first_frame`, sprawdza sie tylko na K04 (K05 nie ma `first_frame`).
3. Generowac K01 -> K08 w kolejnosci; po kazdym klipie procedura z sekcji 6; ostatnia klatka zaakceptowanego klipu staje sie `first_frame` nastepnego tam, gdzie sekcja 5 tak wskazuje.
4. Montaz wg sekcji 4 i 6.

**Droga A — MCP z konta aplikacji Kling** (R003 sek. 6.1 i 8a). Oficjalny serwer `io.github.klingai-dev/kling-ai`, zdalny `https://kling.ai/mcp/plugin` (albo `https://kling.ai/mcp`), logowanie OAuth kontem Kling Global; instalacja w Claude Code: `claude plugin marketplace add klingai-tech/claude-plugin` i `claude plugin install kling-ai@klingai` albo `claude mcp add --transport http klingai --scope user https://kling.ai/mcp`. Narzedzia uzywane w tym pliku:
- `who_am_i` — pierwsze wywolanie: serwer deklaruje modele i parametry dynamicznie (R003 sek. 4, uwaga pod tabela). **Nazwy argumentow podane w sek. 5 (Wersja MCP) trzeba potwierdzic tym wywolaniem** — zatwierdzone badania podaja nazwy narzedzi, nie ich schematy;
- `file_upload` — zdjecia postaci, plansze tla, klatki `first_frame`;
- `element_create` (oraz `element_list/get/update/delete`) — postacie jako Elements;
- `image_to_video`, `omni_ref_video`, `text_to_video` — generowanie;
- `query_tasks` — status po `generationId`, wynik w `works[].url`.
Rozliczenie: kredyty konta aplikacji, nie pakiety Units API (R003 sek. 4 uwaga, sek. 11 pkt 5). Limity: 5 QPS; bez subskrypcji 1 rownolegle zadanie wideo (R003 sek. 3, odczyt posredni — NIEPOTWIERDZONE). **Linki wynikow w MCP wygasaja po 24 h** (R003 sek. 2) — pobierac od razu. Webhooka w MCP brak (R003 sek. 6.1).

**Droga B — API Kling Open Platform** (R003 sek. 1, 2, 8b). Baza `https://api-singapore.klingai.com`, naglowek `Authorization: Bearer <API Key>`, klucz z konsoli `kling.ai/dev/api-key` po zakupie pakietu Units lub doladowaniu salda (R003 sek. 1). Endpointy uzywane w tym pliku:
- `POST /image-to-video/kling-4.0` (`contents[].type` = `prompt`, `first_frame`, `middle_frame`, `last_frame`);
- `POST /omni-video/kling-4.0` (`contents[].type` m.in. `element`, `refer_image`, `voice`; `settings.audio`);
- `POST /text-to-video/kling-4.0` (`prompt` + `settings` + `options`);
- Elements: `POST /v1/general/advanced-custom-elements` (pola `element_name`, `element_description`, `reference_type` = `image_refer` / `video_refer`, `element_image_list`, `element_video_list`, `element_voice_id`), odczyt `GET /v1/general/advanced-custom-elements/{id}`;
- status: `GET /tasks?task_ids=<id>` albo `GET /tasks?external_task_ids=<id>`; opcjonalnie `options.callback_url`; wynik `url` wideo, przechowywany 30 dni (R003 sek. 2).
Brak oficjalnego SDK (R003 sek. 5) — wywolania curl/skryptem albo oficjalnym Skillem `kling.mjs` (R003 sek. 5, repozytorium i licencja NIEPOTWIERDZONE).

**Wybor drogi nalezy do wlasciciela** (ECHO-037 pkt 4). Plik nie rekomenduje zadnej z nich ani zadnego narzedzia (ECHO-027). Tresc promptow jest identyczna w obu drogach; rozni sie tylko opakowanie wywolania (sek. 5).

---

## 1. Parametry techniczne Kling 4.0 (tylko z zatwierdzonych badan)

| Parametr | Wartosc w tym pliku | Co mowi zrodlo | Zrodlo |
|---|---|---|---|
| Model | `kling-4.0` (wersja w sciezce endpointu) | nowy standard API: wersja modelu w sciezce, np. `/text-to-video/kling-4.0`; API Key dla wszystkich modeli | R003 sek. 1 (Uwierzytelnianie), sek. 8b |
| Proporcje | `16:9` — wpisywac jawnie w kazdym zadaniu | T2V 4.0: `16:9` domyslnie; Omni 4.0: domyslnie `adaptive` (dlatego jawnie) | R003 sek. 4 (Proporcje) |
| Rozdzielczosc | `1080p` | `720p`, `1080p` (domyslnie), `4k`; `dynamic_range` `sdr`/`hdr` (hdr tylko 1080p/4k) | R003 sek. 4 (Rozdzielczosc) |
| Dlugosc klipu | 3-30 s, **liczby calkowite**; w planie: 9, 6, 3, 20, 19, 8, 5, 5 s | `settings.duration` 3-30 s (liczby calkowite; bez parametru domyslnie 10 s) | R003 sek. 4 (Dlugosc) |
| Dzwiek | T2V i I2V: dzwiek stereo generowany z opisu w prompcie (brak parametru audio); Omni: `settings.audio` = `native` (domyslnie) albo `original` | "Audio output is two-channel stereo"; calego audio nie da sie wylaczyc; muzyke wylacza sie tylko zdaniem w prompcie "no background music" | R003 sek. 4 (Audio); R002 tab. 1, pola 1, 5 |
| Jezyk mowy | dialog zapisany po angielsku w cudzyslowie (PROPOZYCJA EN) | "write the dialogue in that language directly inside quotation marks"; 9 jezykow (ZH, EN, JA, KO, ES, PT, DE, FR, HI) + "other languages" bez nazw; **polski oficjalnie niewspierany jako jezyk mowy: nie ma go na liscie 9 jezykow (status w R002: BRAK DANYCH, bo "other languages" bez nazw)**; test rzedu 4: 3 z 3 polskich kwestii bez bledu (NIEPOTWIERDZONE) | R008 sek. C.2; R002 tab. 1, pola 3, 3a |
| Mowcy w klipie | plan: kilku mowcow w jednym klipie, zawsze jeden naraz | przyklad producenta z 3 mowcami, "One speaker at a time"; **limit liczbowy BRAK DANYCH** | R002 tab. 1, pole 4a |
| Glosy | glos przypisany do Elementu (`element_voice_id`) albo profil `voice` (maks. 3 na zadanie), probka 5-30 s, <= 50 MB | "Audio input is supported only as voice profiles, used to assign a voice to a speaker" | R002 tab. 1, pole 6; R008 sek. B.2; R003 sek. 4 |
| Elements | `reference_type` `image_refer` / `video_refer`; na zadanie Omni do 15 zasobow (do 10 obrazow, do 5 wideo lacznie <= 30 s, do 7 elementow) | Element Management 4.0 | R003 sek. 4 (Obrazy referencyjne) |
| Klatki kluczowe | I2V 4.0: `first_frame`, `middle_frame`, `last_frame`, do 10 obrazow; .jpg/.jpeg/.png, <= 30 MB, >= 300 px, proporcje 2:5-5:2 | I2V 4.0 nie przyjmuje Elements ("use the Omni reference-to-video API") | R003 sek. 4 (Obraz do wideo) |
| `first_frame` w Omni 4.0 | **BRAK DANYCH** — badania wymieniaja typy `element`, `refer_image`, `voice` "m.in." | sprawdzic w `who_am_i` (MCP) lub na stronie endpointu Omni 4.0 przed testem zerowym | R003 sek. 4; R002 tab. 1, pole 8a (Omni 3.0 i Flash maja `first_frame`, nie 4.0) |
| Seed | brak — powtorzenie klipu nie odtworzy wyniku | tabele parametrow 4.0 nie zawieraja `seed` | R003 sek. 4 (Seed) |
| Przedluzanie | brak — kazda ciaglosc przez `first_frame` = ostatnia klatka poprzedniego klipu albo przez jeden dluzszy klip (do 30 s) | "Video Extension (Coming Soon)"; brak narzedzia extend w MCP | R003 sek. 4 (Przedluzanie) |
| Negatywny prompt | blok "Avoid: ..." wewnatrz promptu | osobnego parametru negatywnego w tabelach 4.0 badania nie wymieniaja (T2V: `prompt` + `settings` + `options`) | R003 sek. 4 (Tekst do wideo) |
| **fps** | **BRAK DANYCH. ZALOZENIE: 24 fps** (1 klatka = 41,667 ms); wszystkie czasy na siatce 125 ms = dokladnie 3 klatki | zadne z badan R001, R002, R003, R005, R008 nie podaje liczby klatek na sekunde dla Kling 4.0 | sprawdzenie: sek. 6 krok 2 i pytanie P-9 |
| Koszt orientacyjny | szacunek w sek. 7 poz. 5 | 1080p: 0.2308 USD/s (pakiet; cena pakietu NIEPOTWIERDZONE), 13.85 USD/min; katalogowo 0.235 USD/s; cennik bez wariantu bez audio. MCP: kredyty aplikacji — przelicznik dla 4.0 BRAK DANYCH | R001 (Rachunek), R002 sek. 4 N2, R005 tab. 1 |
| Wariant 4.0 Flash | nieuzywany w planie | 720p, 3-20 s, I2V tylko `first_frame`, "Voice Cloning / Element-Bound Voice: Not supported" | R003 sek. 4; R002 tab. 1 pole 6 |

Granice jakosci zgloszone w zrodlach rzedu 4 (R008 sek. A.2, B.2 — NIEPOTWIERDZONE, ale istotne dla planu kontroli): muzyka w tle mimo prosby o jej brak, niechciane ciecia kamery, dryf twarzy przy szybkich obrotach, wiecej bledow w dlugich klipach ("a completed 30-second output is not necessarily a successful 30-second scene"). Dlatego najdluzszy klip w planie ma 20 s, a kazdy klip przechodzi kontrole z sekcji 6.

---

## 2. Stale zasady (obowiazuja w kazdym klipie i sa powtarzane w kazdym prompcie)

Kling nie ma "instrukcji dla agenta" jak Flow; zasady sa wpisane w kazdy prompt (sek. 5). Zmiana wzgledem FLOW: zasady trafiaja do tresci promptu, nie do panelu.

| # | Zasada | Zrodlo | Sprzecznosc / adnotacja |
|---|---|---|---|
| Z1 | **Michal ZAWSZE po LEWEJ, Karolina ZAWSZE po PRAWEJ**; bez lustrzanego odbicia kadru; takze gdy ida tylem do kamery | FLOW (instrukcje dla agenta), BEAT | brak |
| Z2 | Michal, 22 lata (SCEN obsada): jasnozolty sweter z nadrukiem **jednego** dinozaura **w okularach** (SCEN l. 73); brazowe wlosy srednie, lagodna twarz (FLOW). Czego NIE ma: drugiego dinozaura, innego nadruku | SCEN l. 73, FLOW | FLOW opisuje "green cartoon dinosaur" bez okularow; obowiazuje SCEN: dinozaur w okularach (kolor dinozaura nieokreslony w SCEN — w promptach pominiety) |
| Z3 | Karolina, 19 lat (SCEN obsada): **zielona kurtka** na kremowej bluzce; **bez** zoltego swetra, **bez** dinozaura, **bez obraczek**, pierscionkow, bransoletek i bizuterii (gole dlonie) | FLOW, metoda A/B (zasada naczelna "co ma i czego nie ma") | **Wlosy: sprzecznosc** — `02_charakterystyki_postaci.md`: "Jasne wlosy, niski kucyk lub luzno"; FLOW: "Dark brown shoulder-length hair". SCEN milczy. Przyjeto tymczasowo FLOW (ciemnobrazowe, do ramion), bo na nim powstal juz CLIP 0 we Flow (metoda A/B, status). Do decyzji: P-5 |
| Z4 | Lokacja: staly fragment Nowego Swiatu w Warszawie, kamienice, szyldy, linia tramwajowa z zoltym tramwajem, niski szary kamienny murek przed budynkiem uczelni; tlo statyczne; ruchome tylko: tramwaj, przechodnie (kobiety i mezczyzni razem), rowery, pies na smyczy, ptaki | SCEN l. 68-72; FLOW; `08_noty_techniczne.md` sek. 7 (mieszane miasto, ostatnie takie w serialu) | brak |
| Z5 | Swiatlo: zlociste, nasycone, poranne, nisko z LEWEJ; miekkie dlugie cienie; filmowe ziarno | SCEN l. 66 ("Barwy: zlociste, nasycone"); FLOW | brak |
| Z6 | Dialog po angielsku, **w cudzyslowie**, w prompcie; polski kanon bez zmian w sek. 4; angielskie brzmienie = PROPOZYCJA (G2) | R008 sek. C.2; ECHO-036 pkt 4; G2 | polski jako jezyk mowy w Klingu: BRAK DANYCH (R002) — pytanie P-2 |
| Z7 | **Mowi jedna osoba naraz**; sluchajacy ma zamkniete usta; nikt inny nie wypowiada slow; glos Marty tylko z telefonu (poza kadrem) | FLOW; R002 pole 4a ("One speaker at a time") | FLOW/BEAT: "jedna osoba w klipie" — **przeksztalcone**: Kling dopuszcza kilku mowcow w klipie, wiec zasada brzmi "jedna osoba naraz" (wariant zapasowy "jedna kwestia = jeden klip": sek. 7 poz. 11) |
| Z8 | Dzwiek w klipie: **tylko ambient miasta** (tramwaj, kroki, glosy, ptaki) i dzwieki zdarzen ze sceny (wibracja telefonu, smiech, dzwonek roweru); w kazdym prompcie jawnie "no background music"; bez napisow i tekstu w kadrze | FLOW; R002 pole 5 (wylaczenie muzyki tylko promptem) | **Sprzecznosc z SCEN l. 65** ("Muzyka: ciepla, ambientowa, miejska") i `04_dzwiek_i_muzyka.md` ("Pelna ... trwa pod rozmowa"). Przyjeto: brak muzyki w klipach (zasada wlasciciela z handoffu, odczyt ECHO-008); muzyka scenariusza moze wejsc dopiero w montazu — decyzja P-8 |
| Z9 | Tempo: kwestia startuje w pierwszych 0,5-1,5 s klipu dialogowego, przerwa przy zmianie mowcy 375 ms (przy przerwaniu w pol zdania 0 ms), bez martwej ciszy na koncu klipu (koniec = krotka reakcja) | FLOW ("tnij martwa cisze"); SCEN (kwestie "--" = przerwanie) | brak |
| Z10 | Ruch i mimika naturalne, subtelne; jedno ciagle ujecie na klip (bez ciec wewnatrz klipu) | FLOW (MOTION); R008 sek. A.2 (zgloszone niechciane ciecia, rzad 4) | brak |

---

## 3. Referencje i Elements do przygotowania

**Stan:** w repozytorium nie ma zadnych obrazow, nagran ani wideo (wyszukiwanie plikow .png/.jpg/.jpeg/.webp/.mp4/.wav/.mp3 w repozytorium: 0 wynikow, 2026-11-28). Gotowe klatki istnieja tylko poza repozytorium (CLIP 0 z Flow, wg `ZERO_metoda_AB_montaz.md`) — ich uzycie jako referencji to decyzja wlasciciela (P-5, sek. 7 poz. 1).

Ograniczenia zasobow (R003 sek. 4; R002 pole 6): obrazy .jpg/.jpeg/.png, <= 30 MB, >= 300 px, proporcje 2:5-5:2; I2V do 10 obrazow na zadanie; Omni do 15 zasobow (do 10 obrazow, do 5 wideo lacznie <= 30 s, do 7 elementow); profil glosu: probka 5-30 s, <= 50 MB, maks. 3 glosy na zadanie. Ile zdjec przyjmuje jeden Element (`element_image_list`) — BRAK DANYCH (sprawdzic przy `element_create`).

| ID zasobu | Rodzaj | Zawartosc | Uzycie | Uwagi |
|---|---|---|---|---|
| EL_MICHAL | Element (`image_refer`) + `element_voice_id` | 3-4 zdjecia: przod, 3/4 lewy, 3/4 prawy, sylwetka do pasa; jasnozolty sweter z jednym dinozaurem w okularach dobrze widocznym | K02-K07 (Omni) | `element_description` = blok MICHAL z sek. 5 (Characters); glos: probka 5-30 s (VOICE_MICHAL) |
| EL_KAROLINA | Element (`image_refer`) + `element_voice_id` | 3-4 zdjecia: przod, 3/4, sylwetka; zielona kurtka, kremowa bluzka, gole dlonie widoczne (bez pierscionkow) | K02, K04-K07 | wlosy wg decyzji P-5; glos VOICE_KAROLINA |
| VOICE_MICHAL, VOICE_KAROLINA | probki glosu (Voice Management / profil) | czysta mowa 5-30 s, jeden glos, bez szumu | glosy elementow | pochodzenie glosu (aktor, synteza) i zgody — decyzja wlasciciela (sek. 7 poz. 2) |
| VOICE_MARTA | profil `voice` | czysta mowa 5-30 s; Marta 38 lat (SCEN obsada) | K05 (L08, L10) | Marta wraca w Scenie 2 — ten sam glos; wariant bez profilu: P-4 |
| REF_TLO_NOWY_SWIAT | `refer_image` | plansza tla: murek przed uczelnia, kamienice, tory, swiatlo z lewej, bez ludzi na murku | K02, K05 (i kontrola tla K04-K06) | jedna plansza dla calej sceny = staly kadr tla |
| REF_SWETER_DINOZAUR | `refer_image` | zblizenie nadruku: jeden dinozaur w okularach na zoltej dzianinie | K03 | ten sam nadruk co w EL_MICHAL |
| REF_TLO_WEJSCIE_UCZELNI | `refer_image` | wejscie do budynku uczelni widziane od murku | K07 | |
| REF_MUREK_PUSTY | `first_frame` (I2V) | pusty murek w tym samym kadrze szerokim, statyw | K08 | moze byc ta sama plansza co REF_TLO_NOWY_SWIAT w planie szerokim |
| REF_TRAMWAJ | `refer_image` (opcjonalnie) | zolty tramwaj warszawski z boku | K01, K08 (opcjonalnie) | marka i wyglad pojazdu — tylko ogolny "yellow tram"; realne oznaczenia przewoznika do decyzji (ECHO-023, temat praw) |
| Kxx_last_frame.png | `first_frame` | ostatnia klatka zaakceptowanego klipu (sek. 6 krok 8) | K04 <- K02, K06 <- K05 (K05 bez `first_frame`: ciecie na zblizenie telefonu, kl. 912) | w Omni 4.0 `first_frame` BRAK DANYCH; zapas: I2V (bez Elements) |

Zmiana wzgledem Flow (zaznaczona): "Postacie"/Entity we Flow -> **Elements** w Klingu; "Save frame -> Start Image" -> `first_frame`; Extend w SceneBuilder -> **brak** (4.0 "Coming soon"), zastapione dluzszym klipem (do 30 s) albo lancuchem `first_frame`.

---

## 4. OS CZASU W MILISEKUNDACH (master timeline)

### 4.0 Konwencje

- Czas 0 ms = pierwsza klatka K01 (poczatek Sceny 1, bez czolowki). Kolumny "start ms"/"koniec ms" = czas w scenie; "lok." = czas od poczatku danego klipu (tego, ktory wychodzi z Klinga).
- **Klatki przy ZALOZENIU 24 fps** (fps Klinga 4.0: BRAK DANYCH, sek. 1): klatka = ms x 24 / 1000; numeracja od 0; "klatka koniec" = pierwsza klatka PO zdarzeniu (zdarzenie zajmuje klatki od "klatka start" do "klatka koniec" - 1). Wszystkie czasy leza na siatce 125 ms = dokladnie 3 klatki, wiec przeliczenie jest bez zaokraglen. Jesli test zerowy pokaze inny fps (np. 30), ms zostaja bez zmian, a klatki przelicza sie wzorem klatka = ms x fps / 1000 (pytanie P-9).
- **Tory** w kazdym klipie: `obraz` (akcja w kadrze), `kamera`, `kwestia` (mowa; okresy bez mowy jako wiersze "(brak mowy)"), `ambient` (podklad miasta), `SFX` (dzwieki zdarzen; okresy bez SFX jako "brak SFX"); w K01 dodatkowo `obraz (napis, montaz)`. **Kazdy tor jest ciagly w obrebie klipu: bez luk i bez nakladek** (zdarzenia roznych torow nakladaja sie z definicji, np. ambient pod kwestia). Sprawdzone skryptem (`assert`) przy generowaniu tabeli.
- **Tempo mowy: 2,8 slowa/s**, czas kwestii = liczba slow / 2,8, zaokraglony w gore do 125 ms. Uzasadnienie: ROZP, naglowek: "Tempo dialogu: ~2,5-3 slowa/sekunde (polski, naturalny)" i adnotacja pod Scena 1: "dialogi na 84s sa realistyczne przy ~2,8 sl/s". Dla angielskich wersji (to one sa mowione w klipie) zatwierdzone zrodla nie podaja tempa — **ZALOZENIE: to samo 2,8 sl/s**, do zmierzenia w tescie zerowym (sek. 6 krok 3). Polska dlugosc kazdej kwestii jest podana osobno (tabela 4.2) do planu glosu polskiego w montazu.
- Poziomy dzwieku = docelowy miks w montazu w dB wzgledem dialogu (dialog = 0 dB ref.). Kling nie przyjmuje poziomow; w promptach sa slowa (distant / soft / present / low, under the dialogue). To PROPOZYCJA miksu.
- Kwestie EN = PROPOZYCJA (G2); kwestie PL = kanon SCEN doslownie.

### 4.1 Klipy i sumy

| klip | ujecie rozpiski | tresc | tryb Kling (narzedzie / endpoint) | `duration` s | start ms | koniec ms | klatka start | klatka koniec |
|---|---|---|---|---|---|---|---|---|
| K01 | U1 | Nowy Swiat z gory, zejscie kamery do ulicy | `text_to_video` | 9 | 0 | 9000 | 0 | 216 |
| K02 | U2 | Dwojka na murku, plan sredni | `omni_ref_video` | 6 | 9000 | 15000 | 216 | 360 |
| K03 | U3 | Insert: sweter z dinozaurem | `omni_ref_video` | 3 | 15000 | 18000 | 360 | 432 |
| K04 | U4 | Dialog: skad ten sweter | `omni_ref_video` | 20 | 18000 | 38000 | 432 | 912 |
| K05 | U5 | Telefon od mamy | `omni_ref_video` | 19 | 38000 | 57000 | 912 | 1368 |
| K06 | U6 | Rytual: kawa po wykladzie | `omni_ref_video` | 8 | 57000 | 65000 | 1368 | 1560 |
| K07 | U7 | Plan szeroki: ida do budynku, Michal rozklada rece | `omni_ref_video` | 5 | 65000 | 70000 | 1560 | 1680 |
| K08 | U8 | Pusty murek | `image_to_video` | 5 | 70000 | 75000 | 1680 | 1800 |
| **SUMA** | U1-U8 | Scena 1 | - | **75** | 0 | 75000 | 0 | 1800 |

Suma dlugosci klipow: 9 + 6 + 3 + 20 + 19 + 8 + 5 + 5 = **75 s = 75 000 ms = 1800 klatek** (24 fps, ZALOZENIE). Kazdy klip: suma czasow wierszy kazdego toru = `duration` klipu.

**Odstepstwa od dokumentow o czasie (jawnie):**

| # | Dokument | Wartosc w dokumencie | W planie | Powod |
|---|---|---|---|---|
| T1 | SCEN l. 62 | "CZAS: ok. 3,5 min" (210 s) | 75 s | dialog i zdarzenia SCEN przy tempie 2,8 sl/s mieszcza sie w 75 s; ROZP sama liczy 84 s i "przyjmuje 210 s z uwzglednieniem szerszego montazu miejskiego w intro". Brakujace ok. 135 s to wylacznie montaz miejski, ktorego SCEN nie rozpisuje — **do decyzji P-1** (wariant rozszerzenia: sek. 7 poz. 12) |
| T2 | ROZP U2 | 9 s; "Michal mowi, gestykuluje ... konczy zdanie" | K02 = 6 s, bez mowy | SCEN nie zawiera zadnej kwestii przed "Skad ty w ogole..." — dopisanie mowy = nowa kwestia (zakaz G2); skrocono, by nie bylo martwej ciszy |
| T3 | ROZP U3 / `05_inserty_closeup.md` | 3 s / "2 sekundy" | K03 = 3 s | Kling 4.0: minimum 3 s (R003 sek. 4); przyciecie do 2 s w montazu tylko po decyzji P-6 |
| T4 | ROZP U4 | 19 s | K04 = 20 s | kwestie EN dluzsze od PL (np. L02: 12 slow EN vs 8 PL) + 2 s smiechu + 1,5 s gestu reki; duration musi byc calkowite |
| T5 | ROZP U5 | 22 s; brak kwestii "Moja mama." | K05 = 19 s; L05 "Moja mama." dodana | SCEN l. 92-93 zawiera kwestie Karoliny "Moja mama." — obowiazuje SCEN; nizsze przerwy (0 ms przy przerwaniach "--") |
| T6 | BEAT 7, 8 / Clip07, Clip08 | kwestie Marty tylko jako "faint mother voice" bez slow | L08 i L10 z pelnym tekstem kanonu | SCEN l. 101-102 i 107-108 — obowiazuje SCEN |
| T7 | ROZP U6 | 12 s | K06 = 8 s | 1,5 s spojrzen + 2 kwestie + skinienie + 1,625 s odejscia; dalsze odejscie przejmuje K07 |
| T8 | ROZP U7, U8 | 5 s + 5 s | K07 = 5 s, K08 = 5 s | zgodne |
| T9 | ROZP U1 | 9 s | K01 = 9 s | zgodne; napis "ZERO" (BEAT, Clip00, VEO: tylko rzad 4, nie SCEN) w montazu 6000-8000 ms — decyzja P-7 |
| T10 | BEAT / FLOW | klipy ~7-10 s, jedna osoba w klipie, Extend | klipy 3-20 s, kilku mowcow w klipie (jeden naraz), bez Extend | przeksztalcenie z Flow/Veo na Kling 4.0 (R003 sek. 4: 3-30 s, brak przedluzania; R002 pole 4a) |
| T11 | ROZP U6 0-3 s vs BEAT 9 | ROZP: "Michal patrzy przed siebie. Karolina zerka na niego. On czuje wzrok, odwraca sie powoli"; BEAT 9: oboje stoja przy murku twarza w twarz ok. 50 cm, on patrzy jej w oczy | K06 0-1500 ms (E088): stoja twarza w twarz ok. 50 cm; Karolina patrzy na niego, Michal ma wzrok chwile opuszczony i powoli podnosi oczy na jej oczy; bez obrotu ciala | sprzecznosc rzedu 4 (stanie twarza w twarz wyklucza patrzenie przed siebie i odwracanie sie); SCEN l. 107-108 jej nie rozstrzyga. Przyjeto BEAT 9, bo zgadza sie z koncem K05 (E086a, kl. 1368 = `first_frame` K06) - obrot ciala w K06 zerwalby ciaglosc z pierwsza klatka; z ROZP zachowano tylko rytm "ona patrzy - on czuje wzrok - spojrzenia sie spotykaja", przeniesiony z obrotu na ruch oczu |

### 4.2 Kwestie (wyciag z osi czasu)

Wszystkie 12 kwestii SCEN l. 75-117 w kolejnosci scenariusza. Przerwy miedzy kwestiami: 375 ms przy zmianie mowcy, 0 ms przy przerwaniu w pol zdania (L07->L08 "wiem, że --" / Marta wchodzi; L08->L09 "bo --" / Karolina przerywa), 250 ms przed L10, 625 ms na odebranie telefonu przed L07. W kazdej chwili mowi najwyzej jedna osoba (kwestie w tabeli nie nakladaja sie; sprawdzone skryptem). Smiech obojga (SCEN l. 87: "Karolina śmieje się głośno. Michał też.") nie jest mowa — tor SFX, 34 500-36 500 ms.

| kwestia | linia scen. | mowca | klip | start ms | koniec ms | klatka start | klatka koniec | dl. EN ms (sl. EN) | dl. PL ms przy 2,8 sl/s (sl. PL) | PL zakres 2,5-3,0 sl/s ms |
|---|---|---|---|---|---|---|---|---|---|---|
| L01 | 76 | Karolina | K04 | 18500 | 21375 | 444 | 513 | 2875 (8) | 2500 (7) | 2375-2875 |
| L02 | 79 | Michal | K04 | 21750 | 26125 | 522 | 627 | 4375 (12) | 2875 (8) | 2750-3250 |
| L03 | 82 | Karolina | K04 | 26500 | 30125 | 636 | 723 | 3625 (10) | 2500 (7) | 2375-2875 |
| L04 | 85 | Michal | K04 | 30500 | 34500 | 732 | 828 | 4000 (11) | 4000 (11) | 3750-4500 |
| L05 | 93 | Karolina | K05 | 39500 | 40250 | 948 | 966 | 750 (2) | 750 (2) | 750-875 |
| L06 | 96 | Michal | K05 | 40625 | 42125 | 975 | 1011 | 1500 (4) | 750 (2) | 750-875 |
| L07 | 99 | Karolina | K05 | 42750 | 46000 | 1026 | 1104 | 3250 (9) | 2250 (6) | 2000-2500 |
| L08 | 102 | Marta (telefon) | K05 | 46000 | 48875 | 1104 | 1173 | 2875 (8) | 2500 (7) | 2375-2875 |
| L09 | 105 | Karolina | K05 | 48875 | 51375 | 1173 | 1233 | 2500 (7) | 2250 (6) | 2000-2500 |
| L10 | 108 | Marta (telefon) | K05 | 51625 | 53875 | 1239 | 1293 | 2250 (6) | 2250 (6) | 2000-2500 |
| L11 | 114 | Michal | K06 | 58500 | 60750 | 1404 | 1458 | 2250 (6) | 2250 (6) | 2000-2500 |
| L12 | 117 | Karolina | K06 | 61125 | 62625 | 1467 | 1503 | 1500 (4) | 1125 (3) | 1000-1250 |

Kolumna "PL zakres" = dlugosc polskiej kwestii przy 3,0 i 2,5 sl/s (zakres z ROZP); sluzy do dopasowania polskiego glosu w montazu (sek. 6 krok 11). Liczba slow: slowa oddzielone spacja, bez myslnikow "--".

### 4.3 Master timeline (wszystkie zdarzenia)

Wiersz pogrubiony = naglowek klipu (granice klipu w scenie). E001-E118 oraz E086a = zdarzenia (E086a dopisane w rundzie 2 bez przenumerowania: Karolina wstaje pod koniec K05). Wiersze tego samego klipu posortowane po starcie.

| id | klip | start ms | koniec ms | klatka start | klatka koniec | lok. start ms (kl.) | lok. koniec ms (kl.) | typ | opis | mowca | kwestia EN (PROPOZYCJA) | kwestia PL (kanon) | poziom dzwieku |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| **K01** | **U1** | **0** | **9000** | **0** | **216** | **0 (0)** | **9000 (216)** | klip | **Nowy Swiat z gory, zejscie kamery do ulicy** (9 s, `text_to_video`) | - | - | - | - |
| E001 | K01 | 0 | 9000 | 0 | 216 | 0 (0) | 9000 (216) | kwestia | (brak mowy) brak mowy; tylko nieczytelny gwar tlumu (ambient) | - | - | - | - |
| E002 | K01 | 0 | 3000 | 0 | 72 | 0 (0) | 3000 (72) | obraz | wysoki widok z powietrza: zolty tramwaj na Nowym Swiecie, ludzie mali na chodniku | - | - | - | - |
| E003 | K01 | 0 | 6000 | 0 | 144 | 0 (0) | 6000 (144) | kamera | powolne zjazd/zejscie kamery z gory do poziomu ulicy, plynnie | - | - | - | - |
| E004 | K01 | 0 | 3000 | 0 | 72 | 0 (0) | 3000 (72) | ambient | miasto z oddali: szum ulicy, ptaki, daleki gwar | - | - | - | -24 dB |
| E005 | K01 | 0 | 1000 | 0 | 24 | 0 (0) | 1000 (24) | SFX | brak SFX | - | - | - | - |
| E006 | K01 | 0 | 6000 | 0 | 144 | 0 (0) | 6000 (144) | obraz (napis, montaz) | brak napisu | - | - | - | - |
| E007 | K01 | 1000 | 5000 | 24 | 120 | 1000 (24) | 5000 (120) | SFX | tramwaj: przejazd, toczenie kol, lekki pisk na szynach | - | - | - | -10 dB szczyt |
| E008 | K01 | 3000 | 6000 | 72 | 144 | 3000 (72) | 6000 (144) | obraz | kamera na wysokosci fasad kamienic: szyldy sklepow, druty tramwajowe, mieszany tlum (kobiety i mezczyzni razem), kawy na wynos, rowery, pies na smyczy | - | - | - | - |
| E009 | K01 | 3000 | 6000 | 72 | 144 | 3000 (72) | 6000 (144) | ambient | miasto blizej: kroki, glosy, ptaki | - | - | - | -18 dB |
| E010 | K01 | 5000 | 6250 | 120 | 150 | 5000 (120) | 6250 (150) | SFX | brak SFX | - | - | - | - |
| E011 | K01 | 6000 | 9000 | 144 | 216 | 6000 (144) | 9000 (216) | obraz | poziom ulicy: przechodzi para, mezczyzna pije kawe, kobieta czyta telefon; smiech przy stolikach kawiarni | - | - | - | - |
| E012 | K01 | 6000 | 9000 | 144 | 216 | 6000 (144) | 9000 (216) | kamera | przejscie w lekka kamere z reki na poziomie chodnika | - | - | - | - |
| E013 | K01 | 6000 | 9000 | 144 | 216 | 6000 (144) | 9000 (216) | ambient | miasto z poziomu ulicy: kroki po bruku, glosy, ptaki | - | - | - | -14 dB |
| E014 | K01 | 6000 | 6500 | 144 | 156 | 6000 (144) | 6500 (156) | obraz (napis, montaz) | napis "ZERO" (bialy, minimalny, srodek kadru) - wejscie (fade in) - NAKLADANY W MONTAZU | - | - | - | - |
| E015 | K01 | 6250 | 6750 | 150 | 162 | 6250 (150) | 6750 (162) | SFX | dzwonek rowerowy (pojedynczy, blisko) | - | - | - | -16 dB |
| E016 | K01 | 6500 | 7500 | 156 | 180 | 6500 (156) | 7500 (180) | obraz (napis, montaz) | napis "ZERO" - stoi | - | - | - | - |
| E017 | K01 | 6750 | 7500 | 162 | 180 | 6750 (162) | 7500 (180) | SFX | brak SFX | - | - | - | - |
| E018 | K01 | 7500 | 9000 | 180 | 216 | 7500 (180) | 9000 (216) | SFX | smiech przy stolikach kawiarni (kilka osob, nieczytelne slowa) | - | - | - | -16 dB |
| E019 | K01 | 7500 | 8000 | 180 | 192 | 7500 (180) | 8000 (192) | obraz (napis, montaz) | napis "ZERO" - wyjscie (fade out) | - | - | - | - |
| E020 | K01 | 8000 | 9000 | 192 | 216 | 8000 (192) | 9000 (216) | obraz (napis, montaz) | brak napisu | - | - | - | - |
| **K02** | **U2** | **9000** | **15000** | **216** | **360** | **0 (0)** | **6000 (144)** | klip | **Dwojka na murku, plan sredni** (6 s, `omni_ref_video`) | - | - | - | - |
| E021 | K02 | 9000 | 15000 | 216 | 360 | 0 (0) | 6000 (144) | kwestia | (brak mowy) brak mowy (rozpiska: "Michal mowi" - bez kwestii w scenariuszu, usuniete) | - | - | - | - |
| E022 | K02 | 9000 | 12000 | 216 | 288 | 0 (0) | 3000 (72) | obraz | Michal (LEWA) i Karolina (PRAWA) siedza na niskim kamiennym murku przed budynkiem uczelni; Michal w jasnozoltym swetrze z JEDNYM dinozaurem w okularach; oboje spokojnie patrza na ulice | - | - | - | - |
| E023 | K02 | 9000 | 15000 | 216 | 360 | 0 (0) | 6000 (144) | kamera | plan sredni dwojki, poziom oczu, lekka kamera z reki; cieple boczne swiatlo poranne z LEWEJ | - | - | - | - |
| E024 | K02 | 9000 | 15000 | 216 | 360 | 0 (0) | 6000 (144) | ambient | miasto: kroki, glosy w oddali, ptaki | - | - | - | -14 dB |
| E025 | K02 | 9000 | 10500 | 216 | 252 | 0 (0) | 1500 (36) | SFX | brak SFX | - | - | - | - |
| E026 | K02 | 10500 | 12500 | 252 | 300 | 1500 (36) | 3500 (84) | SFX | kroki przechodnia za murkiem (z lewej do prawej) | - | - | - | -18 dB |
| E027 | K02 | 12000 | 15000 | 288 | 360 | 3000 (72) | 6000 (144) | obraz | Karolina zerka na sweter Michala z cichym usmiechem | - | - | - | - |
| E028 | K02 | 12500 | 15000 | 300 | 360 | 3500 (84) | 6000 (144) | SFX | brak SFX | - | - | - | - |
| **K03** | **U3** | **15000** | **18000** | **360** | **432** | **0 (0)** | **3000 (72)** | klip | **Insert: sweter z dinozaurem** (3 s, `omni_ref_video`) | - | - | - | - |
| E029 | K03 | 15000 | 18000 | 360 | 432 | 0 (0) | 3000 (72) | kwestia | (brak mowy) brak mowy | - | - | - | - |
| E030 | K03 | 15000 | 16000 | 360 | 384 | 0 (0) | 1000 (24) | obraz | skrajne zblizenie: zolta dzianina swetra, nadruk JEDNEGO dinozaura w okularach; w tle rozmyte zlote bokeh | - | - | - | - |
| E031 | K03 | 15000 | 18000 | 360 | 432 | 0 (0) | 3000 (72) | kamera | kamera statyczna, makro, plytka glebia ostrosci | - | - | - | - |
| E032 | K03 | 15000 | 18000 | 360 | 432 | 0 (0) | 3000 (72) | ambient | miasto przytlumione (zblizenie): ptaki, daleki gwar | - | - | - | -18 dB |
| E033 | K03 | 15000 | 18000 | 360 | 432 | 0 (0) | 3000 (72) | SFX | brak SFX | - | - | - | - |
| E034 | K03 | 16000 | 17000 | 384 | 408 | 1000 (24) | 2000 (48) | obraz | Michal oddycha - sweter delikatnie sie unosi | - | - | - | - |
| E035 | K03 | 17000 | 18000 | 408 | 432 | 2000 (48) | 3000 (72) | obraz | sweter nieruchomy, dinozaur w kadrze | - | - | - | - |
| **K04** | **U4** | **18000** | **38000** | **432** | **912** | **0 (0)** | **20000 (480)** | klip | **Dialog: skad ten sweter** (20 s, `omni_ref_video`) | - | - | - | - |
| E036 | K04 | 18000 | 18500 | 432 | 444 | 0 (0) | 500 (12) | kwestia | (brak mowy) cisza dialogowa (Karolina patrzy na sweter z ironicznym usmiechem) | - | - | - | - |
| E037 | K04 | 18000 | 21375 | 432 | 513 | 0 (0) | 3375 (81) | obraz | Karolina (PRAWA) patrzy na sweter z ironicznym usmiechem, wskazuje JEDNEGO dinozaura prawym palcem wskazujacym i mowi L01, potem patrzy mu w oczy; Michal (LEWA) milczy, usta zamkniete | - | - | - | - |
| E038 | K04 | 18000 | 38000 | 432 | 912 | 0 (0) | 20000 (480) | kamera | plan polpelny dwojki na murku, poziom oczu, lekka kamera z reki; tlo i swiatlo bez zmian | - | - | - | - |
| E039 | K04 | 18000 | 34500 | 432 | 828 | 0 (0) | 16500 (396) | ambient | miasto pod dialogiem: kroki, dalekie glosy, ptaki (nisko, nie maskuje mowy) | - | - | - | -22 dB |
| E040 | K04 | 18000 | 34500 | 432 | 828 | 0 (0) | 16500 (396) | SFX | brak SFX | - | - | - | - |
| E041 | K04 | 18500 | 21375 | 444 | 513 | 500 (12) | 3375 (81) | kwestia | L01: Karolina mowi (8 sl. EN / 7 sl. PL; PL przy 2,8 sl/s = 2500 ms) | Karolina | "Where do you even get things like this." | Skąd ty w ogóle masz takie rzeczy. | dialog 0 dB (ref.) |
| E042 | K04 | 21375 | 21750 | 513 | 522 | 3375 (81) | 3750 (90) | kwestia | (brak mowy) zmiana mowcy (Michal wzrusza ramionami) | - | - | - | - |
| E043 | K04 | 21375 | 26125 | 513 | 627 | 3375 (81) | 8125 (195) | obraz | Michal wzrusza ramionami, bez wstydu, mowi L02; Karolina slucha, usta zamkniete, usmiech narasta | - | - | - | - |
| E044 | K04 | 21750 | 26125 | 522 | 627 | 3750 (90) | 8125 (195) | kwestia | L02: Michal mowi (12 sl. EN / 8 sl. PL; PL przy 2,8 sl/s = 2875 ms) | Michal | "Mom bought it for Saint Nicholas Day. I said it was nice." | Mama kupiła na świętego Mikołaja. Powiedziałem, że ładny. | dialog 0 dB (ref.) |
| E045 | K04 | 26125 | 26500 | 627 | 636 | 8125 (195) | 8500 (204) | kwestia | (brak mowy) zmiana mowcy (reakcja Karoliny: niedowierzanie) | - | - | - | - |
| E046 | K04 | 26125 | 30125 | 627 | 723 | 8125 (195) | 12125 (291) | obraz | Karolina z wyrazem niedowierzania mowi L03; Michal milczy, usmiecha sie | - | - | - | - |
| E047 | K04 | 26500 | 30125 | 636 | 723 | 8500 (204) | 12125 (291) | kwestia | L03: Karolina mowi (10 sl. EN / 7 sl. PL; PL przy 2,8 sl/s = 2500 ms) | Karolina | "Saint Nicholas brings gifts to children up to age six." | Mikołaj przynosi dzieciom do szóstego roku życia. | dialog 0 dB (ref.) |
| E048 | K04 | 30125 | 30500 | 723 | 732 | 12125 (291) | 12500 (300) | kwestia | (brak mowy) zmiana mowcy | - | - | - | - |
| E049 | K04 | 30125 | 34500 | 723 | 828 | 12125 (291) | 16500 (396) | obraz | Michal z rozbrajajaca szczeroscia stuka raz w dinozaura i mowi L04; Karolina milczy | - | - | - | - |
| E050 | K04 | 30500 | 34500 | 732 | 828 | 12500 (300) | 16500 (396) | kwestia | L04: Michal mowi (11 sl. EN / 11 sl. PL; PL przy 2,8 sl/s = 4000 ms) | Michal | "He still brings them to me, because mom says I'm well-behaved." | A mi przynosi do teraz, bo mama mówi, że jestem grzeczny. | dialog 0 dB (ref.) |
| E051 | K04 | 34500 | 38000 | 828 | 912 | 16500 (396) | 20000 (480) | kwestia | (brak mowy) brak kwestii: smiech obojga, Michal bierze ja za reke, chwila | - | - | - | - |
| E052 | K04 | 34500 | 36500 | 828 | 876 | 16500 (396) | 18500 (444) | obraz | Karolina smieje sie glosno; Michal tez sie smieje | - | - | - | - |
| E053 | K04 | 34500 | 38000 | 828 | 912 | 16500 (396) | 20000 (480) | ambient | miasto bez dialogu | - | - | - | -16 dB |
| E054 | K04 | 34500 | 36500 | 828 | 876 | 16500 (396) | 18500 (444) | SFX | smiech Karoliny (glosny) i Michala - diegetyczny | - | - | - | -6 dB |
| E055 | K04 | 36500 | 38000 | 876 | 912 | 18500 (444) | 20000 (480) | obraz | Michal lewa reka bierze jej prawa dlon; zwykla, mloda chwila - oboje usmiechnieci | - | - | - | - |
| E056 | K04 | 36500 | 38000 | 876 | 912 | 18500 (444) | 20000 (480) | SFX | brak SFX | - | - | - | - |
| **K05** | **U5** | **38000** | **57000** | **912** | **1368** | **0 (0)** | **19000 (456)** | klip | **Telefon od mamy** (19 s, `omni_ref_video`) | - | - | - | - |
| E057 | K05 | 38000 | 39500 | 912 | 948 | 0 (0) | 1500 (36) | kwestia | (brak mowy) brak mowy (telefon wibruje na murku) | - | - | - | - |
| E058 | K05 | 38000 | 39500 | 912 | 948 | 0 (0) | 1500 (36) | obraz | telefon Karoliny wibruje na murku obok niej; ekran swieci (bez czytelnego tekstu); Karolina spoglada na ekran | - | - | - | - |
| E059 | K05 | 38000 | 39500 | 912 | 948 | 0 (0) | 1500 (36) | kamera | zblizenie na telefon na murku (plan zblizony) | - | - | - | - |
| E060 | K05 | 38000 | 39500 | 912 | 948 | 0 (0) | 1500 (36) | ambient | miasto (bez dialogu) | - | - | - | -16 dB |
| E061 | K05 | 38000 | 39500 | 912 | 948 | 0 (0) | 1500 (36) | SFX | wibracja telefonu na kamieniu (2 krotkie bzyczenia) | - | - | - | -12 dB |
| E062 | K05 | 39500 | 40250 | 948 | 966 | 1500 (36) | 2250 (54) | kwestia | L05: Karolina mowi (2 sl. EN / 2 sl. PL; PL przy 2,8 sl/s = 750 ms) | Karolina | "My mom." | Moja mama. | dialog 0 dB (ref.) |
| E063 | K05 | 39500 | 40250 | 948 | 966 | 1500 (36) | 2250 (54) | obraz | Karolina patrzy na ekran i mowi L05; Michal milczy, patrzy | - | - | - | - |
| E064 | K05 | 39500 | 57000 | 948 | 1368 | 1500 (36) | 19000 (456) | kamera | dwojka na murku, poziom oczu, lekka kamera z reki | - | - | - | - |
| E065 | K05 | 39500 | 53875 | 948 | 1293 | 1500 (36) | 15875 (381) | ambient | miasto pod dialogiem i rozmowa telefoniczna | - | - | - | -22 dB |
| E066 | K05 | 39500 | 53875 | 948 | 1293 | 1500 (36) | 15875 (381) | SFX | brak SFX (glos Marty jest kwestia, nie SFX) | - | - | - | - |
| E067 | K05 | 40250 | 40625 | 966 | 975 | 2250 (54) | 2625 (63) | kwestia | (brak mowy) zmiana mowcy | - | - | - | - |
| E068 | K05 | 40250 | 42125 | 966 | 1011 | 2250 (54) | 4125 (99) | obraz | Michal lekko kiwa glowa, maly gest dlonia, mowi L06; Karolina milczy | - | - | - | - |
| E069 | K05 | 40625 | 42125 | 975 | 1011 | 2625 (63) | 4125 (99) | kwestia | L06: Michal mowi (4 sl. EN / 2 sl. PL; PL przy 2,8 sl/s = 750 ms) | Michal | "Answer it, answer it." | Odbierz, odbierz. | dialog 0 dB (ref.) |
| E070 | K05 | 42125 | 42750 | 1011 | 1026 | 4125 (99) | 4750 (114) | kwestia | (brak mowy) Karolina odbiera telefon | - | - | - | - |
| E071 | K05 | 42125 | 42750 | 1011 | 1026 | 4125 (99) | 4750 (114) | obraz | Karolina podnosi telefon do ucha (zostaje po PRAWEJ) | - | - | - | - |
| E072 | K05 | 42750 | 46000 | 1026 | 1104 | 4750 (114) | 8000 (192) | kwestia | L07: Karolina mowi (9 sl. EN / 6 sl. PL; PL przy 2,8 sl/s = 2250 ms) | Karolina | "Mom, yes, I was already leaving, I know that..." | Mamo -- tak, już wychodziłam, wiem, że -- | dialog 0 dB (ref.) |
| E073 | K05 | 42750 | 46000 | 1026 | 1104 | 4750 (114) | 8000 (192) | obraz | Karolina z telefonem przy uchu mowi L07, w pospiechu; Michal milczy, patrzy na jej profil | - | - | - | - |
| E074 | K05 | 46000 | 48875 | 1104 | 1173 | 8000 (192) | 10875 (261) | kwestia | L08: Marta (telefon) mowi (8 sl. EN / 7 sl. PL; PL przy 2,8 sl/s = 2500 ms) | Marta (telefon) | "Karolina, did you take the basement keys, because..." | Karolina, czy wzięłaś klucze od piwnicy, bo -- | telefon -8 dB, filtr pasmowy |
| E075 | K05 | 46000 | 48875 | 1104 | 1173 | 8000 (192) | 10875 (261) | obraz | Karolina slucha (usta zamkniete); z telefonu slychac cichy glos Marty (L08); Marta NIE jest widoczna | - | - | - | - |
| E076 | K05 | 48875 | 51375 | 1173 | 1233 | 10875 (261) | 13375 (321) | kwestia | L09: Karolina mowi (7 sl. EN / 6 sl. PL; PL przy 2,8 sl/s = 2250 ms) | Karolina | "Mom, I have class in eight minutes." | Mamo, mam zajęcia za osiem minut. | dialog 0 dB (ref.) |
| E077 | K05 | 48875 | 51375 | 1173 | 1233 | 10875 (261) | 13375 (321) | obraz | Karolina przerywa i mowi L09; Michal milczy | - | - | - | - |
| E078 | K05 | 51375 | 51625 | 1233 | 1239 | 13375 (321) | 13625 (327) | kwestia | (brak mowy) zmiana mowcy | - | - | - | - |
| E079 | K05 | 51375 | 53875 | 1233 | 1293 | 13375 (321) | 15875 (381) | obraz | Karolina slucha (usta zamkniete); z telefonu cichy glos Marty (L10) | - | - | - | - |
| E080 | K05 | 51625 | 53875 | 1239 | 1293 | 13625 (327) | 15875 (381) | kwestia | L10: Marta (telefon) mowi (6 sl. EN / 6 sl. PL; PL przy 2,8 sl/s = 2250 ms) | Marta (telefon) | "Yes, yes, okay, see you tonight." | Tak, tak, dobrze, to do wieczora. | telefon -8 dB, filtr pasmowy |
| E081 | K05 | 53875 | 57000 | 1293 | 1368 | 15875 (381) | 19000 (456) | kwestia | (brak mowy) brak kwestii: rozlaczenie, Karolina chowa telefon, Michal wstaje i podaje jej reke, Karolina wstaje | - | - | - | - |
| E082 | K05 | 53875 | 54875 | 1293 | 1317 | 15875 (381) | 16875 (405) | obraz | rozlaczenie; Karolina opuszcza telefon | - | - | - | - |
| E083 | K05 | 53875 | 57000 | 1293 | 1368 | 15875 (381) | 19000 (456) | ambient | miasto bez dialogu | - | - | - | -16 dB |
| E084 | K05 | 53875 | 54125 | 1293 | 1299 | 15875 (381) | 16125 (387) | SFX | krotki sygnal zakonczenia polaczenia w sluchawce (cichy) | - | - | - | -24 dB |
| E085 | K05 | 54125 | 57000 | 1299 | 1368 | 16125 (387) | 19000 (456) | SFX | brak SFX | - | - | - | - |
| E086 | K05 | 54875 | 56000 | 1317 | 1344 | 16875 (405) | 18000 (432) | obraz | Karolina chowa telefon; Michal wstaje z murku i podaje jej reke | - | - | - | - |
| E086a | K05 | 56000 | 57000 | 1344 | 1368 | 18000 (432) | 19000 (456) | obraz | Karolina bierze jego reke i wstaje; w kl. 1368 oboje stoja przy murku twarza w twarz ok. 50 cm (Michal LEWA, Karolina PRAWA), dlonie juz puszczone - kadr koncowy = pierwsza klatka K06 (E088) | - | - | - | - |
| **K06** | **U6** | **57000** | **65000** | **1368** | **1560** | **0 (0)** | **8000 (192)** | klip | **Rytual: kawa po wykladzie** (8 s, `omni_ref_video`) | - | - | - | - |
| E087 | K06 | 57000 | 58500 | 1368 | 1404 | 0 (0) | 1500 (36) | kwestia | (brak mowy) brak mowy (spojrzenia) | - | - | - | - |
| E088 | K06 | 57000 | 58500 | 1368 | 1404 | 0 (0) | 1500 (36) | obraz | oboje stoja przy murku, twarza w twarz ok. 50 cm (Michal LEWA, Karolina PRAWA); Karolina patrzy na niego; Michal ma wzrok chwile opuszczony, czuje jej spojrzenie i powoli podnosi oczy na jej oczy (bez obrotu ciala - wersja przyjeta w T11) | - | - | - | - |
| E089 | K06 | 57000 | 65000 | 1368 | 1560 | 0 (0) | 8000 (192) | kamera | zblizona dwojka, poziom oczu, lekka kamera z reki | - | - | - | - |
| E090 | K06 | 57000 | 58500 | 1368 | 1404 | 0 (0) | 1500 (36) | ambient | miasto (bez dialogu) | - | - | - | -16 dB |
| E091 | K06 | 57000 | 62625 | 1368 | 1503 | 0 (0) | 5625 (135) | SFX | brak SFX | - | - | - | - |
| E092 | K06 | 58500 | 60750 | 1404 | 1458 | 1500 (36) | 3750 (90) | kwestia | L11: Michal mowi (6 sl. EN / 6 sl. PL; PL przy 2,8 sl/s = 2250 ms) | Michal | "So then, coffee after the lecture?" | No to co, kawa po wykładzie? | dialog 0 dB (ref.) |
| E093 | K06 | 58500 | 60750 | 1404 | 1458 | 1500 (36) | 3750 (90) | obraz | ich oczy sie spotykaja; Michal spokojnie mowi L11; Karolina milczy | - | - | - | - |
| E094 | K06 | 58500 | 62625 | 1404 | 1503 | 1500 (36) | 5625 (135) | ambient | miasto pod dialogiem | - | - | - | -22 dB |
| E095 | K06 | 60750 | 61125 | 1458 | 1467 | 3750 (90) | 4125 (99) | kwestia | (brak mowy) zmiana mowcy | - | - | - | - |
| E096 | K06 | 60750 | 62625 | 1458 | 1503 | 3750 (90) | 5625 (135) | obraz | Karolina zatrzymuje na nim wzrok i mowi L12; Michal milczy | - | - | - | - |
| E097 | K06 | 61125 | 62625 | 1467 | 1503 | 4125 (99) | 5625 (135) | kwestia | L12: Karolina mowi (4 sl. EN / 3 sl. PL; PL przy 2,8 sl/s = 1125 ms) | Karolina | "Coffee after the lecture." | Kawa po wykładzie. | dialog 0 dB (ref.) |
| E098 | K06 | 62625 | 65000 | 1503 | 1560 | 5625 (135) | 8000 (192) | kwestia | (brak mowy) brak kwestii: skinienie glowy, oboje odwracaja sie i ruszaja w strone budynku | - | - | - | - |
| E099 | K06 | 62625 | 63375 | 1503 | 1521 | 5625 (135) | 6375 (153) | obraz | Karolina delikatnie sklania glowe; Michal male skinienie | - | - | - | - |
| E100 | K06 | 62625 | 65000 | 1503 | 1560 | 5625 (135) | 8000 (192) | ambient | miasto bez dialogu | - | - | - | -16 dB |
| E101 | K06 | 62625 | 65000 | 1503 | 1560 | 5625 (135) | 8000 (192) | SFX | kroki obojga po chodniku (ruszaja) | - | - | - | -18 dB |
| E102 | K06 | 63375 | 65000 | 1521 | 1560 | 6375 (153) | 8000 (192) | obraz | oboje odwracaja sie i ida razem w strone budynku uczelni (Michal LEWA, Karolina PRAWA) | - | - | - | - |
| **K07** | **U7** | **65000** | **70000** | **1560** | **1680** | **0 (0)** | **5000 (120)** | klip | **Plan szeroki: ida do budynku, Michal rozklada rece** (5 s, `omni_ref_video`) | - | - | - | - |
| E103 | K07 | 65000 | 70000 | 1560 | 1680 | 0 (0) | 5000 (120) | kwestia | (brak mowy) brak kwestii (smiech Karoliny bez slow - tor SFX) | - | - | - | - |
| E104 | K07 | 65000 | 67000 | 1560 | 1608 | 0 (0) | 2000 (48) | obraz | ida razem w strone wejscia, tylem do kamery (Michal LEWA, Karolina PRAWA); Karolina odwraca sie raz jeszcze przez lewe ramie i patrzy na jego sweter ze smiechem | - | - | - | - |
| E105 | K07 | 65000 | 70000 | 1560 | 1680 | 0 (0) | 5000 (120) | kamera | plan pelny, kamera z reki lekko sie cofa | - | - | - | - |
| E106 | K07 | 65000 | 70000 | 1560 | 1680 | 0 (0) | 5000 (120) | ambient | miasto: kroki, glosy, ptaki | - | - | - | -16 dB |
| E107 | K07 | 65000 | 67000 | 1560 | 1608 | 0 (0) | 2000 (48) | SFX | krotki smiech Karoliny (bez slow) | - | - | - | -12 dB |
| E108 | K07 | 67000 | 70000 | 1608 | 1680 | 2000 (48) | 5000 (120) | obraz | Michal rozklada rece gestem "co z tego"; oboje znikaja w wejsciu budynku | - | - | - | - |
| E109 | K07 | 67000 | 70000 | 1608 | 1680 | 2000 (48) | 5000 (120) | SFX | kroki obojga oddalajace sie | - | - | - | -20 dB |
| **K08** | **U8** | **70000** | **75000** | **1680** | **1800** | **0 (0)** | **5000 (120)** | klip | **Pusty murek** (5 s, `image_to_video`) | - | - | - | - |
| E110 | K08 | 70000 | 75000 | 1680 | 1800 | 0 (0) | 5000 (120) | kwestia | (brak mowy) brak mowy | - | - | - | - |
| E111 | K08 | 70000 | 72000 | 1680 | 1728 | 0 (0) | 2000 (48) | obraz | pusty kamienny murek; ulica zyje dalej; nikt nie patrzy na murek | - | - | - | - |
| E112 | K08 | 70000 | 75000 | 1680 | 1800 | 0 (0) | 5000 (120) | kamera | plan szeroki, kamera nieruchoma na statywie | - | - | - | - |
| E113 | K08 | 70000 | 75000 | 1680 | 1800 | 0 (0) | 5000 (120) | ambient | miasto: kroki, glosy, ptaki | - | - | - | -16 dB |
| E114 | K08 | 70000 | 72000 | 1680 | 1728 | 0 (0) | 2000 (48) | SFX | brak SFX | - | - | - | - |
| E115 | K08 | 72000 | 74000 | 1728 | 1776 | 2000 (48) | 4000 (96) | obraz | przejezdza zolty tramwaj w tle | - | - | - | - |
| E116 | K08 | 72000 | 74500 | 1728 | 1788 | 2000 (48) | 4500 (108) | SFX | tramwaj: przejazd z prawej do lewej, toczenie kol | - | - | - | -10 dB szczyt |
| E117 | K08 | 74000 | 75000 | 1776 | 1800 | 4000 (96) | 5000 (120) | obraz | przechodzi kobieta; murek pusty | - | - | - | - |
| E118 | K08 | 74500 | 75000 | 1788 | 1800 | 4500 (108) | 5000 (120) | SFX | kroki przechodzacej kobiety | - | - | - | -18 dB |
### 4.4 Kluczowe zdarzenia obrazu i dzwieku (skrot z 4.3)

| Zdarzenie | id | start ms (klatka) | koniec ms (klatka) | Zrodlo |
|---|---|---|---|---|
| Tramwaj na Nowym Swiecie (obraz, widok z gory) | E002 | 0 (0) | 3000 (72) | SCEN l. 68; ROZP U1 0-3 s |
| Tramwaj — dzwiek przejazdu | E007 | 1000 (24) | 5000 (120) | SCEN l. 68 (tramwaj); poziom PROPOZYCJA |
| Mieszany tlum, kawy, rowery, pies | E008 | 3000 (72) | 6000 (144) | SCEN l. 68-70 |
| Napis "ZERO" — wejscie / stoi / wyjscie (montaz) | E014 / E016 / E019 | 6000 (144) | 8000 (192) | BEAT 0, Clip00, VEO CLIP 0 (rzad 4; brak w SCEN) — P-7 |
| Dzwonek roweru | E015 | 6250 (150) | 6750 (162) | SCEN l. 69 (rowery); VEO CLIP 0 (bicycle bell) |
| Smiech przy stolikach | E018 | 7500 (180) | 9000 (216) | SCEN l. 70 |
| Karolina zerka na sweter | E027 | 12000 (288) | 15000 (360) | ROZP U2 6-9 s |
| Pierwsza kwestia sceny (L01) | E041 | 18500 (444) | 21375 (513) | SCEN l. 76 |
| Smiech obojga (obraz / dzwiek) | E052 / E054 | 34500 (828) | 36500 (876) | SCEN l. 87 |
| Michal bierze ja za reke | E055 | 36500 (876) | 38000 (912) | SCEN l. 87 |
| Telefon wibruje | E061 | 38000 (912) | 39500 (948) | SCEN l. 90 |
| Rozlaczenie (sygnal) | E084 | 53875 (1293) | 54125 (1299) | SCEN l. 110 ("Rozłączenie") |
| Karolina odwraca sie, patrzy na sweter ze smiechem | E104 | 65000 (1560) | 67000 (1608) | SCEN l. 119-120 |
| Michal rozklada rece, znikaja w wejsciu | E108 | 67000 (1608) | 70000 (1680) | SCEN l. 120 |
| Pusty murek (caly K08) | E111, E115, E117 | 70000 (1680) | 75000 (1800) | SCEN l. 122 (ostatni kadr) |
| Tramwaj przejezdza za pustym murkiem | E115 / E116 | 72000 (1728) | 74000 (1776) / 74500 (1788) | ROZP U8 ("W sekundzie 2. przejezdza tramwaj") |
| Przechodzi kobieta | E117 | 74000 (1776) | 75000 (1800) | ROZP U8 ("W sekundzie 4.") |

W razie rozbieznosci miedzy ta tabela a 4.3 obowiazuje 4.3.

---

## 5. Prompty ujec (po angielsku) — wersje dla MCP i dla API

Zasady wspolne:
- Tresc promptu jest jedna dla obu drog; rozni sie opakowanie. Czasy w promptach to **czasy lokalne klipu** z kolumny "lok." w 4.3 (ta sama tabela danych, ten sam skrypt).
- Kazdy prompt powtarza stale zasady z sek. 2 (Characters, Location, Light, Audio rules, Avoid), bo model gubi kontekst miedzy zadaniami (metoda A/B, zasada naczelna).
- Blok `[Audio]` wg szablonu przewodnika 4.0 (`[Audio] Who says what ... Ambient sounds ... Music ... Sound effects`, R002 tab. 1 pole 1a) z jawnym "no background music" (R002 pole 5).
- Jak w prompcie Omni odwolac sie do konkretnego Elementu (np. przez nazwe z "@", jak w przykladzie 3.0 Omni, R002 pole 4a) — BRAK DANYCH dla 4.0; w promptach postacie nazwane sa imieniem i opisem; sprawdzic w `who_am_i` / na stronie Omni 4.0 przed testem zerowym.
- **Wersja API — pola wartosci to ZALOZENIE.** Zatwierdzone badania potwierdzaja sciezki, `contents[].type` (`prompt`, `first_frame`, `element`, `refer_image`, `voice`), `settings` (`resolution`, `aspect_ratio`, `duration`, `audio`) i `options` (`callback_url`, `external_task_id`) (R003 sek. 4, 8b), ale nie nazwy pol z wartoscia w elementach `contents` (`text`, `element_id`, `voice_id`, `url`) ani typ `duration` (liczba czy tekst). Przed pierwszym wywolaniem porownac z dokumentacja endpointu (R003 Z3a, Z3b, Z3e).
- Parametru `seed` nie ma (R003 sek. 4) — kolejne proby tego samego promptu daja rozne wyniki; numerowac `external_task_id` (`-t1`, `-t2`...).
- Tryb klipu: `text_to_video` (K01), `omni_ref_video` (K02-K07, bo tylko Omni przyjmuje Elements i glosy, R003 sek. 4), `image_to_video` (K08, `first_frame` = pusty murek).

### 5.1 K01 - Nowy Swiat z gory, zejscie kamery do ulicy (9 s; start w scenie 0 ms, klatka 0)

Uwagi: Brak postaci, brak Elements. Napis "ZERO" NIE jest w prompcie - nakladany w montazu (os czasu E006, E014, E016, E019, E020 - tor napis).

**PROMPT K01** (wspolny dla MCP i API; czasy lokalne w klipie, zgodne z sek. 4):

```text
[Shot] Aerial establishing shot of Nowy Swiat, Warsaw, descending to street level. Michal and Karolina are NOT visible in this clip. Duration: 9 seconds, one continuous take, no cuts.
Location: one fixed stretch of Nowy Swiat street in Warsaw on an ordinary warm morning: pale historic tenement facades, shopfronts, one tram line with a yellow tram, a low grey stone wall in front of a university building. The background stays static and identical; only moving elements: the tram, pedestrians (women and men together), cyclists, a dog on a leash, birds.
Light and look: natural golden morning light, low, from the LEFT; warm saturated colours; soft long shadows; cinematic film look with slight grain; 16:9.
[Camera] 0.000-6.000 s: slow, smooth descent from high above down toward street level. 6.000-9.000 s: transition into gentle handheld at pavement level.
[Timeline - picture] 0.000-3.000 s: high aerial view: a yellow tram on Nowy Swiat, people small on the pavement. 3.000-6.000 s: camera at the height of the tenement facades: shop signs, tram wires, a mixed crowd of women and men together, people with takeaway coffee, bicycles, a dog on a leash. 6.000-9.000 s: street level: a couple walks past, a man sips coffee, a woman reads her phone; people laugh at cafe tables.
[Audio] Dialogue rules: dialogue is in English and written in quotes; only one person speaks at a time; the listener keeps lips closed; nobody else says any words. Ambient: natural Warsaw street sounds only. Music: none - no background music, no score, no singing. No subtitles, no captions, no on-screen text.
Dialogue: none - nobody speaks in this clip, mouths closed.
Ambient sounds: 0.000-3.000 s: distant city hum, birds, far-away voices (distant); 3.000-6.000 s: closer: footsteps, voices, birds (soft); 6.000-9.000 s: street level: footsteps on cobblestones, voices, birds (present).
Sound effects: 1.000-5.000 s: a yellow tram rolls past (wheels on rails, light rail squeal); 6.250-6.750 s: a single bicycle bell nearby; 7.500-9.000 s: laughter at cafe tables, several people, no intelligible words.
Music: none. No background music.
Avoid: background music, score, singing, subtitles, captions, any text or logo, a second dinosaur, a dinosaur on Karolina, a yellow sweater on Karolina, rings or jewelry, swapped left/right positions, mirrored frame, extra speaking voices, two people speaking at the same time, face morphing, changing background, cuts inside the clip.
```

**Wersja MCP:**

```text
Narzedzie MCP: `text_to_video` -> potem `query_tasks` (polling po `generationId`) -> pobrac `works[].url` od razu (link wazny 24 h).
Argumenty (NAZWY POL DO POTWIERDZENIA w `who_am_i` - serwer deklaruje modele i parametry dynamicznie):
  - model: "kling-4.0"
  - prompt: <PROMPT K01 powyzej, w calosci>
  - duration: 9
  - aspect_ratio: "16:9"
  - resolution: "1080p"
```

**Wersja API (Open Platform):**

`POST https://api-singapore.klingai.com/text-to-video/kling-4.0`
Naglowki: `Authorization: Bearer <API Key>`, `Content-Type: application/json`
Status: `GET https://api-singapore.klingai.com/tasks?task_ids=<id>` (albo `?external_task_ids=ZERO-E01-S1-K01-t1`); wynik: `url` wideo (pobrac, przechowanie 30 dni).

```json
{
  "prompt": "[Shot] Aerial establishing shot of Nowy Swiat, Warsaw, descending to street level. Michal and Karolina are NOT visible in this clip. Duration: 9 seconds, one continuous take, no cuts.\nLocation: one fixed stretch of Nowy Swiat street in Warsaw on an ordinary warm morning: pale historic tenement facades, shopfronts, one tram line with a yellow tram, a low grey stone wall in front of a university building. The background stays static and identical; only moving elements: the tram, pedestrians (women and men together), cyclists, a dog on a leash, birds.\nLight and look: natural golden morning light, low, from the LEFT; warm saturated colours; soft long shadows; cinematic film look with slight grain; 16:9.\n[Camera] 0.000-6.000 s: slow, smooth descent from high above down toward street level. 6.000-9.000 s: transition into gentle handheld at pavement level.\n[Timeline - picture] 0.000-3.000 s: high aerial view: a yellow tram on Nowy Swiat, people small on the pavement. 3.000-6.000 s: camera at the height of the tenement facades: shop signs, tram wires, a mixed crowd of women and men together, people with takeaway coffee, bicycles, a dog on a leash. 6.000-9.000 s: street level: a couple walks past, a man sips coffee, a woman reads her phone; people laugh at cafe tables.\n[Audio] Dialogue rules: dialogue is in English and written in quotes; only one person speaks at a time; the listener keeps lips closed; nobody else says any words. Ambient: natural Warsaw street sounds only. Music: none - no background music, no score, no singing. No subtitles, no captions, no on-screen text.\nDialogue: none - nobody speaks in this clip, mouths closed.\nAmbient sounds: 0.000-3.000 s: distant city hum, birds, far-away voices (distant); 3.000-6.000 s: closer: footsteps, voices, birds (soft); 6.000-9.000 s: street level: footsteps on cobblestones, voices, birds (present).\nSound effects: 1.000-5.000 s: a yellow tram rolls past (wheels on rails, light rail squeal); 6.250-6.750 s: a single bicycle bell nearby; 7.500-9.000 s: laughter at cafe tables, several people, no intelligible words.\nMusic: none. No background music.\nAvoid: background music, score, singing, subtitles, captions, any text or logo, a second dinosaur, a dinosaur on Karolina, a yellow sweater on Karolina, rings or jewelry, swapped left/right positions, mirrored frame, extra speaking voices, two people speaking at the same time, face morphing, changing background, cuts inside the clip.",
  "settings": {
    "resolution": "1080p",
    "aspect_ratio": "16:9",
    "duration": 9
  },
  "options": {
    "external_task_id": "ZERO-E01-S1-K01-t1"
  }
}
```

### 5.2 K02 - Dwojka na murku, plan sredni (6 s; start w scenie 9000 ms, klatka 216)

Uwagi: Elements: Michal, Karolina (z glosami, choc w tym klipie nikt nie mowi). Tlo jako `refer_image`. Brak `first_frame` (pierwsze ujecie z postaciami).

**PROMPT K02** (wspolny dla MCP i API; czasy lokalne w klipie, zgodne z sek. 4):

```text
[Shot] Medium two-shot of Michal and Karolina sitting on the stone wall. Duration: 6 seconds, one continuous take, no cuts.
Characters (identical in every clip, never change): MICHAL - young man, 22, brown medium-length hair, gentle open face; a bright light-yellow knitted sweater with EXACTLY ONE printed cartoon dinosaur wearing glasses, centered on the chest - one dinosaur only, no second dinosaur, no other print or pattern anywhere. KAROLINA - young woman, 19, dark brown shoulder-length hair, warm face; a GREEN jacket over a cream top; she wears NO yellow sweater and has NO dinosaur anywhere; bare hands - no rings, no bracelets, no jewelry. Positions: MICHAL is ALWAYS on the LEFT of the frame, KAROLINA is ALWAYS on the RIGHT; never swap sides, never mirror the frame.
Location: one fixed stretch of Nowy Swiat street in Warsaw on an ordinary warm morning: pale historic tenement facades, shopfronts, one tram line with a yellow tram, a low grey stone wall in front of a university building. The background stays static and identical; only moving elements: the tram, pedestrians (women and men together), cyclists, a dog on a leash, birds.
Light and look: natural golden morning light, low, from the LEFT; warm saturated colours; soft long shadows; cinematic film look with slight grain; 16:9.
[Camera] 0.000-6.000 s: medium two-shot, eye level, gentle handheld, warm side light from the LEFT.
[Timeline - picture] 0.000-3.000 s: Michal (LEFT) and Karolina (RIGHT) sit on the low stone wall; both look calmly at the street; nobody speaks. 3.000-6.000 s: Karolina glances at Michal's sweater with a quiet smile; nobody speaks.
[Audio] Dialogue rules: dialogue is in English and written in quotes; only one person speaks at a time; the listener keeps lips closed; nobody else says any words. Ambient: natural Warsaw street sounds only. Music: none - no background music, no score, no singing. No subtitles, no captions, no on-screen text.
Dialogue: none - nobody speaks in this clip, mouths closed.
Ambient sounds: 0.000-6.000 s: Warsaw street ambience: footsteps, distant voices, birds (present).
Sound effects: 1.500-3.500 s: footsteps of a passer-by behind the wall, left to right.
Music: none. No background music.
Avoid: background music, score, singing, subtitles, captions, any text or logo, a second dinosaur, a dinosaur on Karolina, a yellow sweater on Karolina, rings or jewelry, swapped left/right positions, mirrored frame, extra speaking voices, two people speaking at the same time, face morphing, changing background, cuts inside the clip.
```

**Wersja MCP:**

```text
Narzedzie MCP: `omni_ref_video` -> potem `query_tasks` (polling po `generationId`) -> pobrac `works[].url` od razu (link wazny 24 h).
Argumenty (NAZWY POL DO POTWIERDZENIA w `who_am_i` - serwer deklaruje modele i parametry dynamicznie):
  - model: "kling-4.0"
  - prompt: <PROMPT K02 powyzej, w calosci>
  - duration: 6
  - aspect_ratio: "16:9"
  - resolution: "1080p"
  - element: <id elementu EL_MICHAL z element_create>
  - element: <id elementu EL_KAROLINA z element_create>
  - refer_image: <plik REF_TLO_NOWY_SWIAT.png wgrany przez file_upload>
  - audio: "native" (odpowiednik settings.audio; jesli who_am_i deklaruje)
```

**Wersja API (Open Platform):**

`POST https://api-singapore.klingai.com/omni-video/kling-4.0`
Naglowki: `Authorization: Bearer <API Key>`, `Content-Type: application/json`
Status: `GET https://api-singapore.klingai.com/tasks?task_ids=<id>` (albo `?external_task_ids=ZERO-E01-S1-K02-t1`); wynik: `url` wideo (pobrac, przechowanie 30 dni).

```json
{
  "contents": [
    {
      "type": "prompt",
      "text": "[Shot] Medium two-shot of Michal and Karolina sitting on the stone wall. Duration: 6 seconds, one continuous take, no cuts.\nCharacters (identical in every clip, never change): MICHAL - young man, 22, brown medium-length hair, gentle open face; a bright light-yellow knitted sweater with EXACTLY ONE printed cartoon dinosaur wearing glasses, centered on the chest - one dinosaur only, no second dinosaur, no other print or pattern anywhere. KAROLINA - young woman, 19, dark brown shoulder-length hair, warm face; a GREEN jacket over a cream top; she wears NO yellow sweater and has NO dinosaur anywhere; bare hands - no rings, no bracelets, no jewelry. Positions: MICHAL is ALWAYS on the LEFT of the frame, KAROLINA is ALWAYS on the RIGHT; never swap sides, never mirror the frame.\nLocation: one fixed stretch of Nowy Swiat street in Warsaw on an ordinary warm morning: pale historic tenement facades, shopfronts, one tram line with a yellow tram, a low grey stone wall in front of a university building. The background stays static and identical; only moving elements: the tram, pedestrians (women and men together), cyclists, a dog on a leash, birds.\nLight and look: natural golden morning light, low, from the LEFT; warm saturated colours; soft long shadows; cinematic film look with slight grain; 16:9.\n[Camera] 0.000-6.000 s: medium two-shot, eye level, gentle handheld, warm side light from the LEFT.\n[Timeline - picture] 0.000-3.000 s: Michal (LEFT) and Karolina (RIGHT) sit on the low stone wall; both look calmly at the street; nobody speaks. 3.000-6.000 s: Karolina glances at Michal's sweater with a quiet smile; nobody speaks.\n[Audio] Dialogue rules: dialogue is in English and written in quotes; only one person speaks at a time; the listener keeps lips closed; nobody else says any words. Ambient: natural Warsaw street sounds only. Music: none - no background music, no score, no singing. No subtitles, no captions, no on-screen text.\nDialogue: none - nobody speaks in this clip, mouths closed.\nAmbient sounds: 0.000-6.000 s: Warsaw street ambience: footsteps, distant voices, birds (present).\nSound effects: 1.500-3.500 s: footsteps of a passer-by behind the wall, left to right.\nMusic: none. No background music.\nAvoid: background music, score, singing, subtitles, captions, any text or logo, a second dinosaur, a dinosaur on Karolina, a yellow sweater on Karolina, rings or jewelry, swapped left/right positions, mirrored frame, extra speaking voices, two people speaking at the same time, face morphing, changing background, cuts inside the clip."
    },
    {
      "type": "element",
      "element_id": "<EL_MICHAL>"
    },
    {
      "type": "element",
      "element_id": "<EL_KAROLINA>"
    },
    {
      "type": "refer_image",
      "url": "<URL lub base64: REF_TLO_NOWY_SWIAT.png>"
    }
  ],
  "settings": {
    "resolution": "1080p",
    "aspect_ratio": "16:9",
    "duration": 6,
    "audio": "native"
  },
  "options": {
    "external_task_id": "ZERO-E01-S1-K02-t1"
  }
}
```

### 5.3 K03 - Insert: sweter z dinozaurem (3 s; start w scenie 15000 ms, klatka 360)

Uwagi: Element: Michal (sweter). `refer_image`: zblizenie nadruku z arkusza referencji. Kling 4.0 przyjmuje min. 3 s; rozpiska ma 3 s, 05_inserty_closeup 2 s - przyciac w montazu do 2 s tylko po decyzji (pytanie P-6).

**PROMPT K03** (wspolny dla MCP i API; czasy lokalne w klipie, zgodne z sek. 4):

```text
[Shot] Extreme close-up insert of Michal's sweater. Duration: 3 seconds, one continuous take, no cuts.
Characters (identical in every clip, never change): MICHAL - young man, 22, brown medium-length hair, gentle open face; a bright light-yellow knitted sweater with EXACTLY ONE printed cartoon dinosaur wearing glasses, centered on the chest - one dinosaur only, no second dinosaur, no other print or pattern anywhere. KAROLINA - young woman, 19, dark brown shoulder-length hair, warm face; a GREEN jacket over a cream top; she wears NO yellow sweater and has NO dinosaur anywhere; bare hands - no rings, no bracelets, no jewelry. Positions: MICHAL is ALWAYS on the LEFT of the frame, KAROLINA is ALWAYS on the RIGHT; never swap sides, never mirror the frame.
Location: one fixed stretch of Nowy Swiat street in Warsaw on an ordinary warm morning: pale historic tenement facades, shopfronts, one tram line with a yellow tram, a low grey stone wall in front of a university building. The background stays static and identical; only moving elements: the tram, pedestrians (women and men together), cyclists, a dog on a leash, birds.
Light and look: natural golden morning light, low, from the LEFT; warm saturated colours; soft long shadows; cinematic film look with slight grain; 16:9.
[Camera] 0.000-3.000 s: static camera, macro, shallow depth of field.
[Timeline - picture] 0.000-1.000 s: extreme close-up of the yellow knit and the print of ONE cartoon dinosaur wearing glasses; soft golden bokeh behind. 1.000-2.000 s: Michal breathes in - the sweater rises gently. 2.000-3.000 s: the sweater settles; the dinosaur stays in frame.
[Audio] Dialogue rules: dialogue is in English and written in quotes; only one person speaks at a time; the listener keeps lips closed; nobody else says any words. Ambient: natural Warsaw street sounds only. Music: none - no background music, no score, no singing. No subtitles, no captions, no on-screen text.
Dialogue: none - nobody speaks in this clip, mouths closed.
Ambient sounds: 0.000-3.000 s: Warsaw street ambience: footsteps, distant voices, birds (soft).
Sound effects: none.
Music: none. No background music.
Avoid: background music, score, singing, subtitles, captions, any text or logo, a second dinosaur, a dinosaur on Karolina, a yellow sweater on Karolina, rings or jewelry, swapped left/right positions, mirrored frame, extra speaking voices, two people speaking at the same time, face morphing, changing background, cuts inside the clip.
```

**Wersja MCP:**

```text
Narzedzie MCP: `omni_ref_video` -> potem `query_tasks` (polling po `generationId`) -> pobrac `works[].url` od razu (link wazny 24 h).
Argumenty (NAZWY POL DO POTWIERDZENIA w `who_am_i` - serwer deklaruje modele i parametry dynamicznie):
  - model: "kling-4.0"
  - prompt: <PROMPT K03 powyzej, w calosci>
  - duration: 3
  - aspect_ratio: "16:9"
  - resolution: "1080p"
  - element: <id elementu EL_MICHAL z element_create>
  - refer_image: <plik REF_SWETER_DINOZAUR.png wgrany przez file_upload>
  - audio: "native" (odpowiednik settings.audio; jesli who_am_i deklaruje)
```

**Wersja API (Open Platform):**

`POST https://api-singapore.klingai.com/omni-video/kling-4.0`
Naglowki: `Authorization: Bearer <API Key>`, `Content-Type: application/json`
Status: `GET https://api-singapore.klingai.com/tasks?task_ids=<id>` (albo `?external_task_ids=ZERO-E01-S1-K03-t1`); wynik: `url` wideo (pobrac, przechowanie 30 dni).

```json
{
  "contents": [
    {
      "type": "prompt",
      "text": "[Shot] Extreme close-up insert of Michal's sweater. Duration: 3 seconds, one continuous take, no cuts.\nCharacters (identical in every clip, never change): MICHAL - young man, 22, brown medium-length hair, gentle open face; a bright light-yellow knitted sweater with EXACTLY ONE printed cartoon dinosaur wearing glasses, centered on the chest - one dinosaur only, no second dinosaur, no other print or pattern anywhere. KAROLINA - young woman, 19, dark brown shoulder-length hair, warm face; a GREEN jacket over a cream top; she wears NO yellow sweater and has NO dinosaur anywhere; bare hands - no rings, no bracelets, no jewelry. Positions: MICHAL is ALWAYS on the LEFT of the frame, KAROLINA is ALWAYS on the RIGHT; never swap sides, never mirror the frame.\nLocation: one fixed stretch of Nowy Swiat street in Warsaw on an ordinary warm morning: pale historic tenement facades, shopfronts, one tram line with a yellow tram, a low grey stone wall in front of a university building. The background stays static and identical; only moving elements: the tram, pedestrians (women and men together), cyclists, a dog on a leash, birds.\nLight and look: natural golden morning light, low, from the LEFT; warm saturated colours; soft long shadows; cinematic film look with slight grain; 16:9.\n[Camera] 0.000-3.000 s: static camera, macro, shallow depth of field.\n[Timeline - picture] 0.000-1.000 s: extreme close-up of the yellow knit and the print of ONE cartoon dinosaur wearing glasses; soft golden bokeh behind. 1.000-2.000 s: Michal breathes in - the sweater rises gently. 2.000-3.000 s: the sweater settles; the dinosaur stays in frame.\n[Audio] Dialogue rules: dialogue is in English and written in quotes; only one person speaks at a time; the listener keeps lips closed; nobody else says any words. Ambient: natural Warsaw street sounds only. Music: none - no background music, no score, no singing. No subtitles, no captions, no on-screen text.\nDialogue: none - nobody speaks in this clip, mouths closed.\nAmbient sounds: 0.000-3.000 s: Warsaw street ambience: footsteps, distant voices, birds (soft).\nSound effects: none.\nMusic: none. No background music.\nAvoid: background music, score, singing, subtitles, captions, any text or logo, a second dinosaur, a dinosaur on Karolina, a yellow sweater on Karolina, rings or jewelry, swapped left/right positions, mirrored frame, extra speaking voices, two people speaking at the same time, face morphing, changing background, cuts inside the clip."
    },
    {
      "type": "element",
      "element_id": "<EL_MICHAL>"
    },
    {
      "type": "refer_image",
      "url": "<URL lub base64: REF_SWETER_DINOZAUR.png>"
    }
  ],
  "settings": {
    "resolution": "1080p",
    "aspect_ratio": "16:9",
    "duration": 3,
    "audio": "native"
  },
  "options": {
    "external_task_id": "ZERO-E01-S1-K03-t1"
  }
}
```

### 5.4 K04 - Dialog: skad ten sweter (20 s; start w scenie 18000 ms, klatka 432)

Uwagi: Ciaglosc: `first_frame` = ostatnia klatka zaakceptowanego K02 (ten sam uklad). Czy `/omni-video/kling-4.0` przyjmuje `first_frame` - BRAK DANYCH w zatwierdzonych badaniach (sek. 1, P-3). Zapas: `POST /image-to-video/kling-4.0` z `first_frame` (bez Elements i bez glosow elementow).

**PROMPT K04** (wspolny dla MCP i API; czasy lokalne w klipie, zgodne z sek. 4):

```text
[Shot] Two-shot (medium-wide) of Michal and Karolina sitting on the stone wall. Duration: 20 seconds, one continuous take, no cuts.
Characters (identical in every clip, never change): MICHAL - young man, 22, brown medium-length hair, gentle open face; a bright light-yellow knitted sweater with EXACTLY ONE printed cartoon dinosaur wearing glasses, centered on the chest - one dinosaur only, no second dinosaur, no other print or pattern anywhere. KAROLINA - young woman, 19, dark brown shoulder-length hair, warm face; a GREEN jacket over a cream top; she wears NO yellow sweater and has NO dinosaur anywhere; bare hands - no rings, no bracelets, no jewelry. Positions: MICHAL is ALWAYS on the LEFT of the frame, KAROLINA is ALWAYS on the RIGHT; never swap sides, never mirror the frame.
Location: one fixed stretch of Nowy Swiat street in Warsaw on an ordinary warm morning: pale historic tenement facades, shopfronts, one tram line with a yellow tram, a low grey stone wall in front of a university building. The background stays static and identical; only moving elements: the tram, pedestrians (women and men together), cyclists, a dog on a leash, birds.
Light and look: natural golden morning light, low, from the LEFT; warm saturated colours; soft long shadows; cinematic film look with slight grain; 16:9.
[Camera] 0.000-20.000 s: medium-wide two-shot on the wall, eye level, gentle handheld; background and light unchanged.
[Timeline - picture] 0.000-3.375 s: Karolina (RIGHT) looks at the sweater with an ironic smile, points at the ONE dinosaur with her right index finger and says her line, then looks into his eyes; Michal (LEFT) silent, lips closed. 3.375-8.125 s: Michal shrugs, unashamed, and says his line; Karolina listens, lips closed, smile growing. 8.125-12.125 s: Karolina, in playful disbelief, says her line; Michal silent, smiling. 12.125-16.500 s: Michal, disarmingly sincere, taps the dinosaur once and says his line; Karolina silent. 16.500-18.500 s: Karolina laughs out loud; Michal laughs too (laughter, no words). 18.500-20.000 s: Michal's left hand takes her right hand; a simple, young, ordinary moment, both smiling.
[Audio] Dialogue rules: dialogue is in English and written in quotes; only one person speaks at a time; the listener keeps lips closed; nobody else says any words. Ambient: natural Warsaw street sounds only. Music: none - no background music, no score, no singing. No subtitles, no captions, no on-screen text.
Dialogue: 0.500-3.375 s: KAROLINA (right, young woman, warm voice) says: "Where do you even get things like this." 3.750-8.125 s: MICHAL (left, young man, calm warm voice) says: "Mom bought it for Saint Nicholas Day. I said it was nice." 8.500-12.125 s: KAROLINA (right, young woman, warm voice) says: "Saint Nicholas brings gifts to children up to age six." 12.500-16.500 s: MICHAL (left, young man, calm warm voice) says: "He still brings them to me, because mom says I'm well-behaved."
Ambient sounds: 0.000-16.500 s: Warsaw street ambience: footsteps, distant voices, birds (low, under the dialogue); 16.500-20.000 s: Warsaw street ambience: footsteps, distant voices, birds (present).
Sound effects: 16.500-18.500 s: laughter of Karolina (loud) and Michal.
Music: none. No background music.
Avoid: background music, score, singing, subtitles, captions, any text or logo, a second dinosaur, a dinosaur on Karolina, a yellow sweater on Karolina, rings or jewelry, swapped left/right positions, mirrored frame, extra speaking voices, two people speaking at the same time, face morphing, changing background, cuts inside the clip.
```

**Wersja MCP:**

```text
Narzedzie MCP: `omni_ref_video` -> potem `query_tasks` (polling po `generationId`) -> pobrac `works[].url` od razu (link wazny 24 h).
Argumenty (NAZWY POL DO POTWIERDZENIA w `who_am_i` - serwer deklaruje modele i parametry dynamicznie):
  - model: "kling-4.0"
  - prompt: <PROMPT K04 powyzej, w calosci>
  - duration: 20
  - aspect_ratio: "16:9"
  - resolution: "1080p"
  - element: <id elementu EL_MICHAL z element_create>
  - element: <id elementu EL_KAROLINA z element_create>
  - first_frame: <plik K02_last_frame.png wgrany przez file_upload>
  - audio: "native" (odpowiednik settings.audio; jesli who_am_i deklaruje)
```

**Wersja API (Open Platform):**

`POST https://api-singapore.klingai.com/omni-video/kling-4.0`
Naglowki: `Authorization: Bearer <API Key>`, `Content-Type: application/json`
Status: `GET https://api-singapore.klingai.com/tasks?task_ids=<id>` (albo `?external_task_ids=ZERO-E01-S1-K04-t1`); wynik: `url` wideo (pobrac, przechowanie 30 dni).

```json
{
  "contents": [
    {
      "type": "prompt",
      "text": "[Shot] Two-shot (medium-wide) of Michal and Karolina sitting on the stone wall. Duration: 20 seconds, one continuous take, no cuts.\nCharacters (identical in every clip, never change): MICHAL - young man, 22, brown medium-length hair, gentle open face; a bright light-yellow knitted sweater with EXACTLY ONE printed cartoon dinosaur wearing glasses, centered on the chest - one dinosaur only, no second dinosaur, no other print or pattern anywhere. KAROLINA - young woman, 19, dark brown shoulder-length hair, warm face; a GREEN jacket over a cream top; she wears NO yellow sweater and has NO dinosaur anywhere; bare hands - no rings, no bracelets, no jewelry. Positions: MICHAL is ALWAYS on the LEFT of the frame, KAROLINA is ALWAYS on the RIGHT; never swap sides, never mirror the frame.\nLocation: one fixed stretch of Nowy Swiat street in Warsaw on an ordinary warm morning: pale historic tenement facades, shopfronts, one tram line with a yellow tram, a low grey stone wall in front of a university building. The background stays static and identical; only moving elements: the tram, pedestrians (women and men together), cyclists, a dog on a leash, birds.\nLight and look: natural golden morning light, low, from the LEFT; warm saturated colours; soft long shadows; cinematic film look with slight grain; 16:9.\n[Camera] 0.000-20.000 s: medium-wide two-shot on the wall, eye level, gentle handheld; background and light unchanged.\n[Timeline - picture] 0.000-3.375 s: Karolina (RIGHT) looks at the sweater with an ironic smile, points at the ONE dinosaur with her right index finger and says her line, then looks into his eyes; Michal (LEFT) silent, lips closed. 3.375-8.125 s: Michal shrugs, unashamed, and says his line; Karolina listens, lips closed, smile growing. 8.125-12.125 s: Karolina, in playful disbelief, says her line; Michal silent, smiling. 12.125-16.500 s: Michal, disarmingly sincere, taps the dinosaur once and says his line; Karolina silent. 16.500-18.500 s: Karolina laughs out loud; Michal laughs too (laughter, no words). 18.500-20.000 s: Michal's left hand takes her right hand; a simple, young, ordinary moment, both smiling.\n[Audio] Dialogue rules: dialogue is in English and written in quotes; only one person speaks at a time; the listener keeps lips closed; nobody else says any words. Ambient: natural Warsaw street sounds only. Music: none - no background music, no score, no singing. No subtitles, no captions, no on-screen text.\nDialogue: 0.500-3.375 s: KAROLINA (right, young woman, warm voice) says: \"Where do you even get things like this.\" 3.750-8.125 s: MICHAL (left, young man, calm warm voice) says: \"Mom bought it for Saint Nicholas Day. I said it was nice.\" 8.500-12.125 s: KAROLINA (right, young woman, warm voice) says: \"Saint Nicholas brings gifts to children up to age six.\" 12.500-16.500 s: MICHAL (left, young man, calm warm voice) says: \"He still brings them to me, because mom says I'm well-behaved.\"\nAmbient sounds: 0.000-16.500 s: Warsaw street ambience: footsteps, distant voices, birds (low, under the dialogue); 16.500-20.000 s: Warsaw street ambience: footsteps, distant voices, birds (present).\nSound effects: 16.500-18.500 s: laughter of Karolina (loud) and Michal.\nMusic: none. No background music.\nAvoid: background music, score, singing, subtitles, captions, any text or logo, a second dinosaur, a dinosaur on Karolina, a yellow sweater on Karolina, rings or jewelry, swapped left/right positions, mirrored frame, extra speaking voices, two people speaking at the same time, face morphing, changing background, cuts inside the clip."
    },
    {
      "type": "element",
      "element_id": "<EL_MICHAL>"
    },
    {
      "type": "element",
      "element_id": "<EL_KAROLINA>"
    },
    {
      "type": "first_frame",
      "url": "<URL lub base64: K02_last_frame.png>"
    }
  ],
  "settings": {
    "resolution": "1080p",
    "aspect_ratio": "16:9",
    "duration": 20,
    "audio": "native"
  },
  "options": {
    "external_task_id": "ZERO-E01-S1-K04-t1"
  }
}
```

### 5.5 K05 - Telefon od mamy (19 s; start w scenie 38000 ms, klatka 912)

Uwagi: Ciaglosc: K05 jest NOWYM ujeciem i NIE ma `first_frame` (rozwiazanie zarzutu E-1-1). Klatka 912 = ciecie montazowe z planu polpelnego K04 (dwojka trzyma sie za rece) na zblizenie telefonu na murku; zblizenie nie musi kontynuowac ukladu dloni. Spojnosc postaci daja Elements, spojnosc tla `refer_image` REF_TLO_NOWY_SWIAT (jak w K02). Od 1500 ms (kl. 948) plan dwojki: oboje siedza na murku, Michal LEWA, Karolina PRAWA, dlonie juz puszczone (telefon zajmuje jej uwage) - to kontrolowac w sek. 6 krok 8 / sek. 7 poz. 7. Glos Marty: profil `voice` (maks. 3 glosy na zadanie) albo bez profilu (glos losowy, podmiana w montazu - pytanie P-4). Dwa przerwania kwestii (L07->L08, L08->L09) maja przerwe 0 ms.

**PROMPT K05** (wspolny dla MCP i API; czasy lokalne w klipie, zgodne z sek. 4):

```text
[Shot] Phone call on the stone wall; close shot of the phone, then two-shot. Duration: 19 seconds, one continuous take, no cuts.
Characters (identical in every clip, never change): MICHAL - young man, 22, brown medium-length hair, gentle open face; a bright light-yellow knitted sweater with EXACTLY ONE printed cartoon dinosaur wearing glasses, centered on the chest - one dinosaur only, no second dinosaur, no other print or pattern anywhere. KAROLINA - young woman, 19, dark brown shoulder-length hair, warm face; a GREEN jacket over a cream top; she wears NO yellow sweater and has NO dinosaur anywhere; bare hands - no rings, no bracelets, no jewelry. Positions: MICHAL is ALWAYS on the LEFT of the frame, KAROLINA is ALWAYS on the RIGHT; never swap sides, never mirror the frame.
Location: one fixed stretch of Nowy Swiat street in Warsaw on an ordinary warm morning: pale historic tenement facades, shopfronts, one tram line with a yellow tram, a low grey stone wall in front of a university building. The background stays static and identical; only moving elements: the tram, pedestrians (women and men together), cyclists, a dog on a leash, birds.
Light and look: natural golden morning light, low, from the LEFT; warm saturated colours; soft long shadows; cinematic film look with slight grain; 16:9.
[Camera] 0.000-1.500 s: close shot of the phone on the wall. 1.500-19.000 s: two-shot on the wall, eye level, gentle handheld.
[Timeline - picture] 0.000-1.500 s: Karolina's phone vibrates on the stone wall next to her; the screen glows (no readable text); she glances at it. 1.500-2.250 s: Karolina looks at the screen and says her line; Michal silent, watching. 2.250-4.125 s: Michal gives a small nod and a tiny hand wave and says his line; Karolina silent. 4.125-4.750 s: Karolina lifts the phone to her ear, staying on the RIGHT. 4.750-8.000 s: Karolina, phone at her ear, in a hurry, says her line; Michal silent, watching her profile. 8.000-10.875 s: Karolina listens, lips closed; a faint, tinny female voice comes from the phone (her mother, off-screen, never visible). 10.875-13.375 s: Karolina cuts in and says her line; Michal silent. 13.375-15.875 s: Karolina listens, lips closed; the faint voice from the phone answers. 15.875-16.875 s: the call ends; Karolina lowers the phone. 16.875-18.000 s: Karolina puts the phone away; Michal stands up from the wall and offers her his hand. 18.000-19.000 s: Karolina takes his hand and stands up; they let go; at 19.000 s both stand by the wall facing each other about 50 cm apart (Michal LEFT, Karolina RIGHT).
[Audio] Dialogue rules: dialogue is in English and written in quotes; only one person speaks at a time; the listener keeps lips closed; nobody else says any words. Ambient: natural Warsaw street sounds only. Music: none - no background music, no score, no singing. No subtitles, no captions, no on-screen text.
Dialogue: 1.500-2.250 s: KAROLINA (right, young woman, warm voice) says: "My mom." 2.625-4.125 s: MICHAL (left, young man, calm warm voice) says: "Answer it, answer it." 4.750-8.000 s: KAROLINA (right, young woman, warm voice) says: "Mom, yes, I was already leaving, I know that..." 8.000-10.875 s: the MOTHER, off-screen, a faint tinny voice through the phone speaker says: "Karolina, did you take the basement keys, because..." 10.875-13.375 s: KAROLINA (right, young woman, warm voice) says: "Mom, I have class in eight minutes." 13.625-15.875 s: the MOTHER, off-screen, a faint tinny voice through the phone speaker says: "Yes, yes, okay, see you tonight."
Ambient sounds: 0.000-1.500 s: Warsaw street ambience: footsteps, distant voices, birds (present); 1.500-15.875 s: Warsaw street ambience: footsteps, distant voices, birds (low, under the dialogue); 15.875-19.000 s: Warsaw street ambience: footsteps, distant voices, birds (present).
Sound effects: 0.000-1.500 s: the phone vibrates on the stone, two short buzzes; 15.875-16.125 s: a short quiet call-ended tone in the earpiece.
Music: none. No background music.
Avoid: background music, score, singing, subtitles, captions, any text or logo, a second dinosaur, a dinosaur on Karolina, a yellow sweater on Karolina, rings or jewelry, swapped left/right positions, mirrored frame, extra speaking voices, two people speaking at the same time, face morphing, changing background, cuts inside the clip.
```

**Wersja MCP:**

```text
Narzedzie MCP: `omni_ref_video` -> potem `query_tasks` (polling po `generationId`) -> pobrac `works[].url` od razu (link wazny 24 h).
Argumenty (NAZWY POL DO POTWIERDZENIA w `who_am_i` - serwer deklaruje modele i parametry dynamicznie):
  - model: "kling-4.0"
  - prompt: <PROMPT K05 powyzej, w calosci>
  - duration: 19
  - aspect_ratio: "16:9"
  - resolution: "1080p"
  - element: <id elementu EL_MICHAL z element_create>
  - element: <id elementu EL_KAROLINA z element_create>
  - voice: <id profilu glosu VOICE_MARTA> (jesli who_am_i deklaruje wejscie glosu)
  - refer_image: <plik REF_TLO_NOWY_SWIAT.png wgrany przez file_upload>
  - audio: "native" (odpowiednik settings.audio; jesli who_am_i deklaruje)
```

**Wersja API (Open Platform):**

`POST https://api-singapore.klingai.com/omni-video/kling-4.0`
Naglowki: `Authorization: Bearer <API Key>`, `Content-Type: application/json`
Status: `GET https://api-singapore.klingai.com/tasks?task_ids=<id>` (albo `?external_task_ids=ZERO-E01-S1-K05-t1`); wynik: `url` wideo (pobrac, przechowanie 30 dni).

```json
{
  "contents": [
    {
      "type": "prompt",
      "text": "[Shot] Phone call on the stone wall; close shot of the phone, then two-shot. Duration: 19 seconds, one continuous take, no cuts.\nCharacters (identical in every clip, never change): MICHAL - young man, 22, brown medium-length hair, gentle open face; a bright light-yellow knitted sweater with EXACTLY ONE printed cartoon dinosaur wearing glasses, centered on the chest - one dinosaur only, no second dinosaur, no other print or pattern anywhere. KAROLINA - young woman, 19, dark brown shoulder-length hair, warm face; a GREEN jacket over a cream top; she wears NO yellow sweater and has NO dinosaur anywhere; bare hands - no rings, no bracelets, no jewelry. Positions: MICHAL is ALWAYS on the LEFT of the frame, KAROLINA is ALWAYS on the RIGHT; never swap sides, never mirror the frame.\nLocation: one fixed stretch of Nowy Swiat street in Warsaw on an ordinary warm morning: pale historic tenement facades, shopfronts, one tram line with a yellow tram, a low grey stone wall in front of a university building. The background stays static and identical; only moving elements: the tram, pedestrians (women and men together), cyclists, a dog on a leash, birds.\nLight and look: natural golden morning light, low, from the LEFT; warm saturated colours; soft long shadows; cinematic film look with slight grain; 16:9.\n[Camera] 0.000-1.500 s: close shot of the phone on the wall. 1.500-19.000 s: two-shot on the wall, eye level, gentle handheld.\n[Timeline - picture] 0.000-1.500 s: Karolina's phone vibrates on the stone wall next to her; the screen glows (no readable text); she glances at it. 1.500-2.250 s: Karolina looks at the screen and says her line; Michal silent, watching. 2.250-4.125 s: Michal gives a small nod and a tiny hand wave and says his line; Karolina silent. 4.125-4.750 s: Karolina lifts the phone to her ear, staying on the RIGHT. 4.750-8.000 s: Karolina, phone at her ear, in a hurry, says her line; Michal silent, watching her profile. 8.000-10.875 s: Karolina listens, lips closed; a faint, tinny female voice comes from the phone (her mother, off-screen, never visible). 10.875-13.375 s: Karolina cuts in and says her line; Michal silent. 13.375-15.875 s: Karolina listens, lips closed; the faint voice from the phone answers. 15.875-16.875 s: the call ends; Karolina lowers the phone. 16.875-18.000 s: Karolina puts the phone away; Michal stands up from the wall and offers her his hand. 18.000-19.000 s: Karolina takes his hand and stands up; they let go; at 19.000 s both stand by the wall facing each other about 50 cm apart (Michal LEFT, Karolina RIGHT).\n[Audio] Dialogue rules: dialogue is in English and written in quotes; only one person speaks at a time; the listener keeps lips closed; nobody else says any words. Ambient: natural Warsaw street sounds only. Music: none - no background music, no score, no singing. No subtitles, no captions, no on-screen text.\nDialogue: 1.500-2.250 s: KAROLINA (right, young woman, warm voice) says: \"My mom.\" 2.625-4.125 s: MICHAL (left, young man, calm warm voice) says: \"Answer it, answer it.\" 4.750-8.000 s: KAROLINA (right, young woman, warm voice) says: \"Mom, yes, I was already leaving, I know that...\" 8.000-10.875 s: the MOTHER, off-screen, a faint tinny voice through the phone speaker says: \"Karolina, did you take the basement keys, because...\" 10.875-13.375 s: KAROLINA (right, young woman, warm voice) says: \"Mom, I have class in eight minutes.\" 13.625-15.875 s: the MOTHER, off-screen, a faint tinny voice through the phone speaker says: \"Yes, yes, okay, see you tonight.\"\nAmbient sounds: 0.000-1.500 s: Warsaw street ambience: footsteps, distant voices, birds (present); 1.500-15.875 s: Warsaw street ambience: footsteps, distant voices, birds (low, under the dialogue); 15.875-19.000 s: Warsaw street ambience: footsteps, distant voices, birds (present).\nSound effects: 0.000-1.500 s: the phone vibrates on the stone, two short buzzes; 15.875-16.125 s: a short quiet call-ended tone in the earpiece.\nMusic: none. No background music.\nAvoid: background music, score, singing, subtitles, captions, any text or logo, a second dinosaur, a dinosaur on Karolina, a yellow sweater on Karolina, rings or jewelry, swapped left/right positions, mirrored frame, extra speaking voices, two people speaking at the same time, face morphing, changing background, cuts inside the clip."
    },
    {
      "type": "element",
      "element_id": "<EL_MICHAL>"
    },
    {
      "type": "element",
      "element_id": "<EL_KAROLINA>"
    },
    {
      "type": "voice",
      "voice_id": "<VOICE_MARTA>"
    },
    {
      "type": "refer_image",
      "url": "<URL lub base64: REF_TLO_NOWY_SWIAT.png>"
    }
  ],
  "settings": {
    "resolution": "1080p",
    "aspect_ratio": "16:9",
    "duration": 19,
    "audio": "native"
  },
  "options": {
    "external_task_id": "ZERO-E01-S1-K05-t1"
  }
}
```

### 5.6 K06 - Rytual: kawa po wykladzie (8 s; start w scenie 57000 ms, klatka 1368)

Uwagi: Ciaglosc: `first_frame` = ostatnia klatka K05 (kl. 1368, E086a: oboje stoja przy murku twarza w twarz ok. 50 cm, Michal LEWA, Karolina PRAWA, dlonie puszczone) - zgodna z E088. Kadr 0-1500 ms: wariant BEAT 9 (twarza w twarz, Michal tylko podnosi wzrok, bez obrotu ciala) - sprzecznosc z ROZP U6 i wybor opisane w T11 (sek. 4.1); kontrola `first_frame`: oboje juz zwroceni do siebie. Jesli ostatnia klatka zaakceptowanego K05 tego nie pokazuje (np. Karolina jeszcze siedzi), klip K05 nie przechodzi kroku 8 sek. 6: ponowic K05 albo przyciac go do klatki, w ktorej oboje stoja, i dopiero ja uzyc jako `first_frame`. Odstepstwo od rozpiski: 8 s zamiast 12 s (sek. 4.1).

**PROMPT K06** (wspolny dla MCP i API; czasy lokalne w klipie, zgodne z sek. 4):

```text
[Shot] Close two-shot, both standing by the wall. Duration: 8 seconds, one continuous take, no cuts.
Characters (identical in every clip, never change): MICHAL - young man, 22, brown medium-length hair, gentle open face; a bright light-yellow knitted sweater with EXACTLY ONE printed cartoon dinosaur wearing glasses, centered on the chest - one dinosaur only, no second dinosaur, no other print or pattern anywhere. KAROLINA - young woman, 19, dark brown shoulder-length hair, warm face; a GREEN jacket over a cream top; she wears NO yellow sweater and has NO dinosaur anywhere; bare hands - no rings, no bracelets, no jewelry. Positions: MICHAL is ALWAYS on the LEFT of the frame, KAROLINA is ALWAYS on the RIGHT; never swap sides, never mirror the frame.
Location: one fixed stretch of Nowy Swiat street in Warsaw on an ordinary warm morning: pale historic tenement facades, shopfronts, one tram line with a yellow tram, a low grey stone wall in front of a university building. The background stays static and identical; only moving elements: the tram, pedestrians (women and men together), cyclists, a dog on a leash, birds.
Light and look: natural golden morning light, low, from the LEFT; warm saturated colours; soft long shadows; cinematic film look with slight grain; 16:9.
[Camera] 0.000-8.000 s: close two-shot, eye level, gentle handheld.
[Timeline - picture] 0.000-1.500 s: both stand by the wall, facing each other about 50 cm apart (Michal LEFT, Karolina RIGHT); Karolina looks at him; Michal's eyes are briefly lowered, he feels her gaze and slowly lifts his eyes to hers; their bodies do not turn, they stay facing each other. 1.500-3.750 s: their eyes meet; Michal says his line calmly; Karolina silent. 3.750-5.625 s: Karolina holds his gaze and says her line; Michal silent. 5.625-6.375 s: Karolina gives a slight nod; Michal a small nod. 6.375-8.000 s: both turn and start walking together toward the university building (Michal LEFT, Karolina RIGHT).
[Audio] Dialogue rules: dialogue is in English and written in quotes; only one person speaks at a time; the listener keeps lips closed; nobody else says any words. Ambient: natural Warsaw street sounds only. Music: none - no background music, no score, no singing. No subtitles, no captions, no on-screen text.
Dialogue: 1.500-3.750 s: MICHAL (left, young man, calm warm voice) says: "So then, coffee after the lecture?" 4.125-5.625 s: KAROLINA (right, young woman, warm voice) says: "Coffee after the lecture."
Ambient sounds: 0.000-1.500 s: Warsaw street ambience: footsteps, distant voices, birds (present); 1.500-5.625 s: Warsaw street ambience: footsteps, distant voices, birds (low, under the dialogue); 5.625-8.000 s: Warsaw street ambience: footsteps, distant voices, birds (present).
Sound effects: 5.625-8.000 s: their footsteps on the pavement as they start walking.
Music: none. No background music.
Avoid: background music, score, singing, subtitles, captions, any text or logo, a second dinosaur, a dinosaur on Karolina, a yellow sweater on Karolina, rings or jewelry, swapped left/right positions, mirrored frame, extra speaking voices, two people speaking at the same time, face morphing, changing background, cuts inside the clip.
```

**Wersja MCP:**

```text
Narzedzie MCP: `omni_ref_video` -> potem `query_tasks` (polling po `generationId`) -> pobrac `works[].url` od razu (link wazny 24 h).
Argumenty (NAZWY POL DO POTWIERDZENIA w `who_am_i` - serwer deklaruje modele i parametry dynamicznie):
  - model: "kling-4.0"
  - prompt: <PROMPT K06 powyzej, w calosci>
  - duration: 8
  - aspect_ratio: "16:9"
  - resolution: "1080p"
  - element: <id elementu EL_MICHAL z element_create>
  - element: <id elementu EL_KAROLINA z element_create>
  - first_frame: <plik K05_last_frame.png wgrany przez file_upload>
  - audio: "native" (odpowiednik settings.audio; jesli who_am_i deklaruje)
```

**Wersja API (Open Platform):**

`POST https://api-singapore.klingai.com/omni-video/kling-4.0`
Naglowki: `Authorization: Bearer <API Key>`, `Content-Type: application/json`
Status: `GET https://api-singapore.klingai.com/tasks?task_ids=<id>` (albo `?external_task_ids=ZERO-E01-S1-K06-t1`); wynik: `url` wideo (pobrac, przechowanie 30 dni).

```json
{
  "contents": [
    {
      "type": "prompt",
      "text": "[Shot] Close two-shot, both standing by the wall. Duration: 8 seconds, one continuous take, no cuts.\nCharacters (identical in every clip, never change): MICHAL - young man, 22, brown medium-length hair, gentle open face; a bright light-yellow knitted sweater with EXACTLY ONE printed cartoon dinosaur wearing glasses, centered on the chest - one dinosaur only, no second dinosaur, no other print or pattern anywhere. KAROLINA - young woman, 19, dark brown shoulder-length hair, warm face; a GREEN jacket over a cream top; she wears NO yellow sweater and has NO dinosaur anywhere; bare hands - no rings, no bracelets, no jewelry. Positions: MICHAL is ALWAYS on the LEFT of the frame, KAROLINA is ALWAYS on the RIGHT; never swap sides, never mirror the frame.\nLocation: one fixed stretch of Nowy Swiat street in Warsaw on an ordinary warm morning: pale historic tenement facades, shopfronts, one tram line with a yellow tram, a low grey stone wall in front of a university building. The background stays static and identical; only moving elements: the tram, pedestrians (women and men together), cyclists, a dog on a leash, birds.\nLight and look: natural golden morning light, low, from the LEFT; warm saturated colours; soft long shadows; cinematic film look with slight grain; 16:9.\n[Camera] 0.000-8.000 s: close two-shot, eye level, gentle handheld.\n[Timeline - picture] 0.000-1.500 s: both stand by the wall, facing each other about 50 cm apart (Michal LEFT, Karolina RIGHT); Karolina looks at him; Michal's eyes are briefly lowered, he feels her gaze and slowly lifts his eyes to hers; their bodies do not turn, they stay facing each other. 1.500-3.750 s: their eyes meet; Michal says his line calmly; Karolina silent. 3.750-5.625 s: Karolina holds his gaze and says her line; Michal silent. 5.625-6.375 s: Karolina gives a slight nod; Michal a small nod. 6.375-8.000 s: both turn and start walking together toward the university building (Michal LEFT, Karolina RIGHT).\n[Audio] Dialogue rules: dialogue is in English and written in quotes; only one person speaks at a time; the listener keeps lips closed; nobody else says any words. Ambient: natural Warsaw street sounds only. Music: none - no background music, no score, no singing. No subtitles, no captions, no on-screen text.\nDialogue: 1.500-3.750 s: MICHAL (left, young man, calm warm voice) says: \"So then, coffee after the lecture?\" 4.125-5.625 s: KAROLINA (right, young woman, warm voice) says: \"Coffee after the lecture.\"\nAmbient sounds: 0.000-1.500 s: Warsaw street ambience: footsteps, distant voices, birds (present); 1.500-5.625 s: Warsaw street ambience: footsteps, distant voices, birds (low, under the dialogue); 5.625-8.000 s: Warsaw street ambience: footsteps, distant voices, birds (present).\nSound effects: 5.625-8.000 s: their footsteps on the pavement as they start walking.\nMusic: none. No background music.\nAvoid: background music, score, singing, subtitles, captions, any text or logo, a second dinosaur, a dinosaur on Karolina, a yellow sweater on Karolina, rings or jewelry, swapped left/right positions, mirrored frame, extra speaking voices, two people speaking at the same time, face morphing, changing background, cuts inside the clip."
    },
    {
      "type": "element",
      "element_id": "<EL_MICHAL>"
    },
    {
      "type": "element",
      "element_id": "<EL_KAROLINA>"
    },
    {
      "type": "first_frame",
      "url": "<URL lub base64: K05_last_frame.png>"
    }
  ],
  "settings": {
    "resolution": "1080p",
    "aspect_ratio": "16:9",
    "duration": 8,
    "audio": "native"
  },
  "options": {
    "external_task_id": "ZERO-E01-S1-K06-t1"
  }
}
```

### 5.7 K07 - Plan szeroki: ida do budynku, Michal rozklada rece (5 s; start w scenie 65000 ms, klatka 1560)

Uwagi: Zmiana planu (szeroki) - bez `first_frame`; tlo wejscia jako `refer_image`. Postacie tylem - Elements pilnuja ubioru i stron L/P.

**PROMPT K07** (wspolny dla MCP i API; czasy lokalne w klipie, zgodne z sek. 4):

```text
[Shot] Wide full shot, they walk to the building. Duration: 5 seconds, one continuous take, no cuts.
Characters (identical in every clip, never change): MICHAL - young man, 22, brown medium-length hair, gentle open face; a bright light-yellow knitted sweater with EXACTLY ONE printed cartoon dinosaur wearing glasses, centered on the chest - one dinosaur only, no second dinosaur, no other print or pattern anywhere. KAROLINA - young woman, 19, dark brown shoulder-length hair, warm face; a GREEN jacket over a cream top; she wears NO yellow sweater and has NO dinosaur anywhere; bare hands - no rings, no bracelets, no jewelry. Positions: MICHAL is ALWAYS on the LEFT of the frame, KAROLINA is ALWAYS on the RIGHT; never swap sides, never mirror the frame.
Location: one fixed stretch of Nowy Swiat street in Warsaw on an ordinary warm morning: pale historic tenement facades, shopfronts, one tram line with a yellow tram, a low grey stone wall in front of a university building. The background stays static and identical; only moving elements: the tram, pedestrians (women and men together), cyclists, a dog on a leash, birds.
Light and look: natural golden morning light, low, from the LEFT; warm saturated colours; soft long shadows; cinematic film look with slight grain; 16:9.
[Camera] 0.000-5.000 s: full wide shot, handheld camera slowly pulling back.
[Timeline - picture] 0.000-2.000 s: they walk away from camera toward the entrance (Michal LEFT, Karolina RIGHT); Karolina turns back once over her left shoulder and looks at his sweater, laughing. 2.000-5.000 s: Michal spreads his arms in a 'so what' gesture; both disappear into the building entrance.
[Audio] Dialogue rules: dialogue is in English and written in quotes; only one person speaks at a time; the listener keeps lips closed; nobody else says any words. Ambient: natural Warsaw street sounds only. Music: none - no background music, no score, no singing. No subtitles, no captions, no on-screen text.
Dialogue: none - nobody speaks in this clip, mouths closed.
Ambient sounds: 0.000-5.000 s: Warsaw street ambience: footsteps, distant voices, birds (present).
Sound effects: 0.000-2.000 s: a short laugh from Karolina, no words; 2.000-5.000 s: their footsteps fading away.
Music: none. No background music.
Avoid: background music, score, singing, subtitles, captions, any text or logo, a second dinosaur, a dinosaur on Karolina, a yellow sweater on Karolina, rings or jewelry, swapped left/right positions, mirrored frame, extra speaking voices, two people speaking at the same time, face morphing, changing background, cuts inside the clip.
```

**Wersja MCP:**

```text
Narzedzie MCP: `omni_ref_video` -> potem `query_tasks` (polling po `generationId`) -> pobrac `works[].url` od razu (link wazny 24 h).
Argumenty (NAZWY POL DO POTWIERDZENIA w `who_am_i` - serwer deklaruje modele i parametry dynamicznie):
  - model: "kling-4.0"
  - prompt: <PROMPT K07 powyzej, w calosci>
  - duration: 5
  - aspect_ratio: "16:9"
  - resolution: "1080p"
  - element: <id elementu EL_MICHAL z element_create>
  - element: <id elementu EL_KAROLINA z element_create>
  - refer_image: <plik REF_TLO_WEJSCIE_UCZELNI.png wgrany przez file_upload>
  - audio: "native" (odpowiednik settings.audio; jesli who_am_i deklaruje)
```

**Wersja API (Open Platform):**

`POST https://api-singapore.klingai.com/omni-video/kling-4.0`
Naglowki: `Authorization: Bearer <API Key>`, `Content-Type: application/json`
Status: `GET https://api-singapore.klingai.com/tasks?task_ids=<id>` (albo `?external_task_ids=ZERO-E01-S1-K07-t1`); wynik: `url` wideo (pobrac, przechowanie 30 dni).

```json
{
  "contents": [
    {
      "type": "prompt",
      "text": "[Shot] Wide full shot, they walk to the building. Duration: 5 seconds, one continuous take, no cuts.\nCharacters (identical in every clip, never change): MICHAL - young man, 22, brown medium-length hair, gentle open face; a bright light-yellow knitted sweater with EXACTLY ONE printed cartoon dinosaur wearing glasses, centered on the chest - one dinosaur only, no second dinosaur, no other print or pattern anywhere. KAROLINA - young woman, 19, dark brown shoulder-length hair, warm face; a GREEN jacket over a cream top; she wears NO yellow sweater and has NO dinosaur anywhere; bare hands - no rings, no bracelets, no jewelry. Positions: MICHAL is ALWAYS on the LEFT of the frame, KAROLINA is ALWAYS on the RIGHT; never swap sides, never mirror the frame.\nLocation: one fixed stretch of Nowy Swiat street in Warsaw on an ordinary warm morning: pale historic tenement facades, shopfronts, one tram line with a yellow tram, a low grey stone wall in front of a university building. The background stays static and identical; only moving elements: the tram, pedestrians (women and men together), cyclists, a dog on a leash, birds.\nLight and look: natural golden morning light, low, from the LEFT; warm saturated colours; soft long shadows; cinematic film look with slight grain; 16:9.\n[Camera] 0.000-5.000 s: full wide shot, handheld camera slowly pulling back.\n[Timeline - picture] 0.000-2.000 s: they walk away from camera toward the entrance (Michal LEFT, Karolina RIGHT); Karolina turns back once over her left shoulder and looks at his sweater, laughing. 2.000-5.000 s: Michal spreads his arms in a 'so what' gesture; both disappear into the building entrance.\n[Audio] Dialogue rules: dialogue is in English and written in quotes; only one person speaks at a time; the listener keeps lips closed; nobody else says any words. Ambient: natural Warsaw street sounds only. Music: none - no background music, no score, no singing. No subtitles, no captions, no on-screen text.\nDialogue: none - nobody speaks in this clip, mouths closed.\nAmbient sounds: 0.000-5.000 s: Warsaw street ambience: footsteps, distant voices, birds (present).\nSound effects: 0.000-2.000 s: a short laugh from Karolina, no words; 2.000-5.000 s: their footsteps fading away.\nMusic: none. No background music.\nAvoid: background music, score, singing, subtitles, captions, any text or logo, a second dinosaur, a dinosaur on Karolina, a yellow sweater on Karolina, rings or jewelry, swapped left/right positions, mirrored frame, extra speaking voices, two people speaking at the same time, face morphing, changing background, cuts inside the clip."
    },
    {
      "type": "element",
      "element_id": "<EL_MICHAL>"
    },
    {
      "type": "element",
      "element_id": "<EL_KAROLINA>"
    },
    {
      "type": "refer_image",
      "url": "<URL lub base64: REF_TLO_WEJSCIE_UCZELNI.png>"
    }
  ],
  "settings": {
    "resolution": "1080p",
    "aspect_ratio": "16:9",
    "duration": 5,
    "audio": "native"
  },
  "options": {
    "external_task_id": "ZERO-E01-S1-K07-t1"
  }
}
```

### 5.8 K08 - Pusty murek (5 s; start w scenie 70000 ms, klatka 1680)

Uwagi: `POST /image-to-video/kling-4.0` z `first_frame` = plansza pustego murka (REF_MUREK_PUSTY). Brak postaci. Audio z promptu (w I2V brak parametru audio).

**PROMPT K08** (wspolny dla MCP i API; czasy lokalne w klipie, zgodne z sek. 4):

```text
[Shot] Static wide shot of the empty stone wall. Michal and Karolina are NOT in this clip. Duration: 5 seconds, one continuous take, no cuts.
Location: one fixed stretch of Nowy Swiat street in Warsaw on an ordinary warm morning: pale historic tenement facades, shopfronts, one tram line with a yellow tram, a low grey stone wall in front of a university building. The background stays static and identical; only moving elements: the tram, pedestrians (women and men together), cyclists, a dog on a leash, birds.
Light and look: natural golden morning light, low, from the LEFT; warm saturated colours; soft long shadows; cinematic film look with slight grain; 16:9.
[Camera] 0.000-5.000 s: wide shot, camera completely still on a tripod.
[Timeline - picture] 0.000-2.000 s: the empty stone wall; the street keeps living; nobody looks at the wall. 2.000-4.000 s: a yellow tram passes in the background. 4.000-5.000 s: a woman walks past; the wall stays empty.
[Audio] Dialogue rules: dialogue is in English and written in quotes; only one person speaks at a time; the listener keeps lips closed; nobody else says any words. Ambient: natural Warsaw street sounds only. Music: none - no background music, no score, no singing. No subtitles, no captions, no on-screen text.
Dialogue: none - nobody speaks in this clip, mouths closed.
Ambient sounds: 0.000-5.000 s: Warsaw street ambience: footsteps, distant voices, birds (present).
Sound effects: 2.000-4.500 s: the yellow tram passes right to left, wheels rolling; 4.500-5.000 s: footsteps of the passing woman.
Music: none. No background music.
Avoid: background music, score, singing, subtitles, captions, any text or logo, a second dinosaur, a dinosaur on Karolina, a yellow sweater on Karolina, rings or jewelry, swapped left/right positions, mirrored frame, extra speaking voices, two people speaking at the same time, face morphing, changing background, cuts inside the clip.
```

**Wersja MCP:**

```text
Narzedzie MCP: `image_to_video` -> potem `query_tasks` (polling po `generationId`) -> pobrac `works[].url` od razu (link wazny 24 h).
Argumenty (NAZWY POL DO POTWIERDZENIA w `who_am_i` - serwer deklaruje modele i parametry dynamicznie):
  - model: "kling-4.0"
  - prompt: <PROMPT K08 powyzej, w calosci>
  - duration: 5
  - aspect_ratio: "16:9"
  - resolution: "1080p"
  - first_frame: <plik REF_MUREK_PUSTY.png wgrany przez file_upload>
```

**Wersja API (Open Platform):**

`POST https://api-singapore.klingai.com/image-to-video/kling-4.0`
Naglowki: `Authorization: Bearer <API Key>`, `Content-Type: application/json`
Status: `GET https://api-singapore.klingai.com/tasks?task_ids=<id>` (albo `?external_task_ids=ZERO-E01-S1-K08-t1`); wynik: `url` wideo (pobrac, przechowanie 30 dni).

```json
{
  "contents": [
    {
      "type": "prompt",
      "text": "[Shot] Static wide shot of the empty stone wall. Michal and Karolina are NOT in this clip. Duration: 5 seconds, one continuous take, no cuts.\nLocation: one fixed stretch of Nowy Swiat street in Warsaw on an ordinary warm morning: pale historic tenement facades, shopfronts, one tram line with a yellow tram, a low grey stone wall in front of a university building. The background stays static and identical; only moving elements: the tram, pedestrians (women and men together), cyclists, a dog on a leash, birds.\nLight and look: natural golden morning light, low, from the LEFT; warm saturated colours; soft long shadows; cinematic film look with slight grain; 16:9.\n[Camera] 0.000-5.000 s: wide shot, camera completely still on a tripod.\n[Timeline - picture] 0.000-2.000 s: the empty stone wall; the street keeps living; nobody looks at the wall. 2.000-4.000 s: a yellow tram passes in the background. 4.000-5.000 s: a woman walks past; the wall stays empty.\n[Audio] Dialogue rules: dialogue is in English and written in quotes; only one person speaks at a time; the listener keeps lips closed; nobody else says any words. Ambient: natural Warsaw street sounds only. Music: none - no background music, no score, no singing. No subtitles, no captions, no on-screen text.\nDialogue: none - nobody speaks in this clip, mouths closed.\nAmbient sounds: 0.000-5.000 s: Warsaw street ambience: footsteps, distant voices, birds (present).\nSound effects: 2.000-4.500 s: the yellow tram passes right to left, wheels rolling; 4.500-5.000 s: footsteps of the passing woman.\nMusic: none. No background music.\nAvoid: background music, score, singing, subtitles, captions, any text or logo, a second dinosaur, a dinosaur on Karolina, a yellow sweater on Karolina, rings or jewelry, swapped left/right positions, mirrored frame, extra speaking voices, two people speaking at the same time, face morphing, changing background, cuts inside the clip."
    },
    {
      "type": "first_frame",
      "url": "<URL lub base64: REF_MUREK_PUSTY.png>"
    }
  ],
  "settings": {
    "resolution": "1080p",
    "aspect_ratio": "16:9",
    "duration": 5
  },
  "options": {
    "external_task_id": "ZERO-E01-S1-K08-t1"
  }
}
```
---

## 6. Procedura weryfikacji i montazu

Cel procedury: zamienic plan z sekcji 4 w zmierzony wynik. Generator nie gwarantuje trafienia w milisekunde (zastrzezenie nadrzedne); kazdy klip jest mierzony i albo przyjety, albo poprawiony w montazu, albo powtorzony.

**Kryterium kontroli (PROPOZYCJA, decyzja P-10):** start kazdej kwestii w zaakceptowanym klipie (po ewentualnym przesunieciu calego klipu w montazu) w granicach **+/- 2 klatki** od planu (przy 24 fps: +/- 83,333 ms); koniec kwestii +/- 4 klatki (+/- 166,667 ms); zdarzenia obrazu i SFX z tabeli 4.4 +/- 6 klatek (+/- 250 ms). Kolejnosc i przypisanie mowcow — bez tolerancji.

| Krok | Co zrobic | Narzedzie / sposob | Wynik / kryterium |
|---|---|---|---|
| 1 | **Pobrac wynik od razu** po `succeeded`. MCP: `works[].url` wygasa po 24 h; API: `url`, przechowanie 30 dni (R003 sek. 2). Nazwa pliku: `E01_S1_<klip>_t<proba>.mp4`; zapisac `generationId` / `task_id` | przegladarka / curl | plik lokalnie, wpis w dzienniku prob (sek. 7 poz. 9) |
| 2 | **Zmierzyc fps, dlugosc i liczbe klatek** (pierwszy klip = odpowiedz na BRAK DANYCH o fps) | `ffprobe -v error -select_streams v:0 -count_frames -show_entries stream=r_frame_rate,nb_read_frames,duration -of csv=p=0 <plik>` | jesli fps != 24: przeliczyc klatki w 4.3 wzorem z 4.0 (ms bez zmian); jesli dlugosc != `duration` — zapisac odchylenie |
| 3 | **Transkrypcja ze znacznikami slow** | lokalnie, np. Whisper/WhisperX z `word_timestamps` (jezyk `en`; przy wariancie polskim `pl`) | lista slow ze start/koniec ms; zmierzone tempo mowy EN (sl/s) — weryfikuje ZALOZENIE 2,8 sl/s |
| 4 | **Porownanie z osia czasu**: dla kazdej kwestii klipu — start pierwszego slowa, koniec ostatniego, roznica do planu w ms i w klatkach; komplet slow (wg PROPOZYCJI EN) | arkusz: kolumny z tabeli 4.2 + "zmierzone start/koniec" + "roznica" | wszystkie kwestie w tolerancji -> krok 5; inaczej krok 10 |
| 5 | **Mowcy i usta**: przy kazdej kwestii usta rusza tylko mowiacy; sluchajacy ma zamkniete usta; brak dodatkowych glosow; Marta slyszalna tylko jako glos z telefonu | ogladanie klatka po klatce w miejscach z 4.2 | 0 bledow (kolejnosc i mowcy bez tolerancji) |
| 6 | **Dzwiek bez muzyki**: odsluch calego klipu + spektrogram (melodia, akordy, perkusja = muzyka) | odsluch, np. Audacity / spektrogram | jakakolwiek muzyka = klip odrzucony albo audio wymienione w montazu (sek. 7 poz. 6). Ryzyko zgloszone w R008 sek. B.2 (rzad 4) |
| 7 | **Kontrola obrazu**: Michal LEWA / Karolina PRAWA (takze tylem); jeden dinozaur w okularach tylko na swetrze Michala; Karolina w zielonej kurtce, bez zoltego swetra, bez obraczek i bizuterii; tlo staly fragment Nowego Swiatu; brak ciec wewnatrz klipu; brak tekstu w kadrze; twarze bez dryfu | karta QA (sek. 7 poz. 8) | kazdy punkt TAK; jedno NIE = krok 10 |
| 8 | **Ciaglosc klipow**: z zaakceptowanego klipu wyciagnac ostatnia klatke jako PNG i uzyc jako `first_frame` nastepnego (K02->K04, K05->K06; K05 bez `first_frame` - ciecie na zblizenie telefonu w kl. 912) | `ffmpeg -sseof -0.1 -i <plik> -frames:v 1 -update 1 <klip>_last_frame.png` (sprawdzic, ze to faktycznie ostatnia klatka) | PNG >= 300 px, proporcje w zakresie 2:5-5:2 (R003 sek. 4) |
| 9 | **Montaz na osi z 4.3**: klip K0x od `start ms` klipu; klipy stykaja sie bez przerw (suma 75 000 ms); zakladki tylko w dzwieku | NLE (np. DaVinci Resolve / CapCut — wybor wlasciciela) z ustawionym fps projektu = fps z kroku 2 | znaczniki (markers) na kazdym zdarzeniu z 4.4 |
| 10 | **Odchylenie**: (a) jesli wszystkie kwestie klipu sa przesuniete o te sama wartosc — przesunac klip w montazu; (b) jesli przerwa miedzy kwestiami jest za dluga, a cieciem nie naruszy sie ust ani akcji — skrocic przerwe; (c) w innym przypadku — **powtorka klipu** (nowa proba `-t2`, ten sam prompt; brak `seed`, wiec wynik bedzie inny) | NLE / nowe zadanie | po maks. 3 probach bez wyniku — zapis w dzienniku i pytanie do wlasciciela (zmiana promptu lub wariant "jedna kwestia = jeden klip", sek. 7 poz. 11) |
| 11 | **Dzwiek i polski glos w montazu**: ambient miasta ciagly pod calym K01-K08 (przenikania 250 ms na cieciach, poziomy z 4.3); SFX z tabeli 4.4 dociagniete do ms (z biblioteki, jesli model ich nie dal); polska wersja wg decyzji P-2: napisy PL (kanon z 4.2) albo polski glos wstawiony od `start ms` kwestii — tabela 4.2 pokazuje, ze przy 2,8 sl/s kazda polska kwestia jest krotsza lub rowna oknu angielskiemu (np. L02: PL 2875 ms w oknie EN 4375 ms); przy wolniejszym tempie 2,5 sl/s cztery kwestie przekraczaja okno (L04 o 500 ms, L05 o 125 ms, L10 i L11 o 250 ms) i wymagaja przyspieszenia nagrania albo uzycia przerwy po kwestii, ale ruch ust angielski nie bedzie zgodny z polskim | NLE; opcjonalnie endpoint Lip Sync `/v1/videos/advanced-lip-sync` (wgrane audio 2-60 s; jakosc dla polskiego BRAK DANYCH, R002 sek. 3) | glos PL w oknie kwestii; brak nakladania mowcow |
| 12 | **Napis "ZERO"** (jesli P-7 = A): biale, minimalne litery na srodku, 6000-8000 ms (wejscie 500 ms, stoi 1000 ms, wyjscie 500 ms) | NLE | zgodnie z E014, E016, E019 |
| 13 | **Eksport**: 16:9, 1080p, fps z kroku 2; raport z pomiarow (kroki 2-4) dolaczony do dziennika | NLE | plik sceny + dziennik |

Uwaga: kroki 2-8 nie wymagaja dostepu do Klinga — dzialaja na pobranym pliku. Zadne z tych narzedzi nie jest czescia zatwierdzonych badan; to standardowe narzedzia montazowe, wybor nalezy do wlasciciela.

---

## 7. Co jeszcze dolozyc (PROPOZYCJE, nie kanon)

Wszystko w tej sekcji to PROPOZYCJA Operatora (ECHO-036 pkt 5). Kolumna "Decyzja wlasciciela" mowi, czy pozycja wymaga jego rozstrzygniecia, zanim wejdzie do produkcji.

| # | Co dolozyc | Uzasadnienie | Decyzja wlasciciela |
|---|---|---|---|
| 1 | **Arkusz Elements postaci** (Michal, Karolina): 3-4 zdjecia na postac (przod, 3/4, sylwetka), opis "co ma i czego nie ma" jako `element_description` | Elements to jedyny mechanizm spojnosci postaci w Omni 4.0 (R003 sek. 4); w repozytorium nie ma zadnych zdjec (sek. 3) | **TAK** — zrodlo twarzy (klatki z Flow CLIP 0, inny generator obrazu, aktorzy) i wyglad wlosow Karoliny (P-5) |
| 2 | **Probki glosow** 5-30 s dla Michala, Karoliny i Marty (`element_voice_id` / profil `voice`) | bez profilu glos moze byc inny w kazdym klipie; Marta wraca w Scenie 2 (R002 pole 6) | **TAK** — czyj glos, zgody, jezyk probki (wplyw probki polskiej na mowe: BRAK DANYCH, R008 sek. C.4) |
| 3 | **Plansze tla** (REF_TLO_NOWY_SWIAT, REF_MUREK_PUSTY, REF_TLO_WEJSCIE_UCZELNI, REF_SWETER_DINOZAUR) | staly kadr tla w calej scenie; FLOW wymaga "background STATIC and IDENTICAL" | TAK — zrodlo plansz (zdjecie z planu, obraz generowany) |
| 4 | **Test zerowy (kalibracyjny)** przed seria: jeden klip (K05 — najwiecej kwestii i przerwanie) | odpowiada na BRAK DANYCH: fps, faktyczne tempo mowy EN, `first_frame` w Omni 4.0 (tylko gdy testem jest K04; K05 go nie ma), kilku mowcow w klipie, nazwy argumentow MCP (`who_am_i`); bez tego os czasu jest tylko planem | TAK — zgoda na koszt testu (poz. 5) |
| 5 | **Plan prob i szacunek kosztu** (API, 1080p, 0.2308 USD/s z pakietu — cena pakietu NIEPOTWIERDZONE; R001 Rachunek, R005 tab. 1): jedno przejscie 75 s = 17.31 USD (katalogowo 0.235 USD/s: 17.63 USD); przy 3 probach na klip = 51.93 USD; test zerowy K05 19 s = 4.39 USD; 720p (1.0 Unit/s x 0.153846 = 0.1538 USD/s, R001 "Szczegoly") dla prob ustawienia: 75 s = 11.54 USD. Droga MCP: kredyty aplikacji — przelicznik dla 4.0 BRAK DANYCH | wlasciciel zna koszt przed startem; brak `seed` oznacza, ze proby sa nieuniknione (R003 sek. 4) | **TAK** — budzet i liczba prob |
| 6 | **Warstwa ambientu i foley w montazu** (biblioteka dzwiekow z ms z tabeli 4.3: tramwaj, kroki, dzwonek, wibracja, sygnal rozlaczenia) | model generuje dzwiek z opisu i nie gwarantuje momentu (R008 sek. B.2: zgloszone brakujace efekty i niechciana muzyka, rzad 4); wlasna warstwa daje trafienie w ms | TAK — czy zastapic/uzupelnic dzwiek modelu |
| 7 | **Tabela ciaglosci klatek** miedzy klipami: K02 ostatnia -> K04 pierwsza; K04 -> K05 (ciecie, bez `first_frame`: zgodnosc ukladu siedzenia, ubioru, swiatla i tla miedzy kl. 911 i kl. 948); K05 -> K06 (oboje stoja twarza w twarz); dla kazdej pary: pozycje L/P, dlonie, swiatlo, tlo | brak Extend w 4.0 (R003 sek. 4) — ciaglosc tylko przez `first_frame` | nie (technika) |
| 8 | **Karta QA po klipie** (checklista z sek. 6 kroki 5-7, jedna strona na probe) | powtarzalna kontrola: L/P, jeden dinozaur w okularach, brak obraczek, zielona kurtka, brak muzyki, brak ciec, mowcy | nie |
| 9 | **Dziennik prob** (klip, proba, task id, data, wynik pomiaru z kroku 4, decyzja) | brak `seed` — bez dziennika nie da sie wrocic do dobrej proby; linki MCP wygasaja po 24 h | nie |
| 10 | **Kontrola ciaglosci rekwizytow**: telefon (lezy na murku od K05 0 ms, w dloni od 42 125 ms, chowany od 54 875 ms), sweter, kurtka, murek; czy Karolina ma torbe/plecak (SCEN milczy, `02_charakterystyki` wspomina zolta teczke w plecaku "widzimy dopiero w E02/03") | rekwizyty to najczestszy dryf miedzy klipami; plecak to decyzja kostiumowa, nie fakt SCEN | TAK — plecak Karoliny tak/nie |
| 11 | **Wariant zapasowy "jedna kwestia = jeden klip"**: K04 i K05 rozbite na klipy 3-5 s (po jednej kwestii, jak BEAT), z tymi samymi czasami w scenie (np. L01: 18 500-21 375 ms) i `first_frame` z poprzedniego | jesli test zerowy pokaze bledy przy kilku mowcach w klipie (limit BRAK DANYCH, R002 pole 4a) | TAK — po tescie zerowym (pytanie P-3) |
| 12 | **Wariant rozszerzenia do ok. 210 s** (SCEN "ok. 3,5 min", ROZP "przyjety czas 210 s"): dodatkowe klipy miejskie przed K02 wylacznie z elementow SCEN l. 68-70 (tramwaj, kawy na wynos, rowery, psy na smyczach, smiech przy stolikach), np. 6 klipow po 20-25 s | zgodnosc metrazu ze scenariuszem bez dopisywania tresci | **TAK** — P-1 |
| 13 | **Muzyka sceny w montazu** (SCEN l. 65: "ciepla, ambientowa, miejska"; `04_dzwiek_i_muzyka.md`: temat "Terazniejszosc", mozliwy diegetyczny z kawiarni) — osobna sciezka pod klipami bez muzyki | spelnia SCEN bez lamania zasady "bez muzyki w klipach"; muzyka z modelu bylaby nie do usuniecia (calego audio nie da sie wylaczyc, R002 pole 5) | **TAK** — P-8; licencja muzyki (temat praw ECHO-023) |
| 14 | **Plan polskiej sciezki** (tabela 4.2: dlugosci PL w oknach EN, zakres 2,5-3,0 sl/s) i ewentualny test Lip Sync z polskim nagraniem | ECHO-008: polski "bardzo wazny"; polski w Klingu 4.0 BRAK DANYCH oficjalnie, a jedyny test (rzad 4) pozytywny — R008 sek. C.2 | **TAK** — P-2 |
| 15 | **Insert ekranu telefonu "Mama"** (ROZP U5 0-2 s) jako osobna plansza w montazu, nie w klipie | tekst generowany w kadrze jest wbrew zasadzie "no on-screen text" (FLOW) i bywa znieksztalcony | TAK — czy insert jest potrzebny (SCEN: tylko "Telefon Karoliny wibruje") |

---

## 8. Ryzyka i pytania do wlasciciela

### 8.1 Ryzyka

| # | Ryzyko | Skad wiadomo | Ograniczenie w tym planie |
|---|---|---|---|
| R1 | Kwestie nie startuja w zaplanowanej milisekundzie | brak parametru czasu w API (R003 sek. 4); zastrzezenie nadrzedne | sek. 6 kroki 3-4, 10; tolerancja P-10 |
| R2 | fps inny niz 24 | BRAK DANYCH w R001-R008 | ms jako wartosc nadrzedna; przeliczenie wzorem (4.0) |
| R3 | Muzyka w klipie mimo "no background music" | R008 sek. B.2 (rzad 4, NIEPOTWIERDZONE) | sek. 6 krok 6; sek. 7 poz. 6 |
| R4 | Bledy przy kilku mowcach w jednym klipie (usta niewlasciwej osoby, nakladanie) | limit mowcow BRAK DANYCH (R002 pole 4a) | test zerowy; wariant sek. 7 poz. 11 |
| R5 | Omni 4.0 nie przyjmie `first_frame` -> utrata ciaglosci przy Elements | BRAK DANYCH (sek. 1) | P-3 |
| R6 | Dryf twarzy / ubioru (drugi dinozaur, sweter na Karolinie, obraczka) | R008 sek. A.2 (rzad 4); FLOW (doswiadczenie z Veo) | Elements + pelny opis w kazdym prompcie + karta QA |
| R7 | Polski glos niezgodny z ruchem ust (przy dubbingu) | dialog generowany po angielsku; polski BRAK DANYCH (R002) | P-2; Lip Sync jako opcja (jakosc PL BRAK DANYCH) |
| R8 | Linki MCP wygasna przed pobraniem | R003 sek. 2 (24 h) | sek. 6 krok 1 |
| R9 | Rozjazd kosztu (proby bez `seed`) | R003 sek. 4; R001 | sek. 7 poz. 5 |
| R10 | Rozbieznosc metrazu z SCEN (75 s vs ok. 210 s) | sek. 4.1 T1 | P-1 |

### 8.2 Pytania ABC (bez rozstrzygania; odpowiedz wlasciciela = wpis ECHO)

- **P-1 (metraz Sceny 1).** A) zostaje plan 75 s (dialog i zdarzenia SCEN, bez dodatkowego montazu miejskiego); B) rozszerzyc do ok. 210 s klipami miejskimi wylacznie z elementow SCEN l. 68-70 (sek. 7 poz. 12); C) dociagnac do 84 s wg ROZP (dluzsze U2 i U6 bez nowych kwestii).
- **P-2 (jezyk mowy w klipie).** A) klip po angielsku + polskie napisy z kanonu; B) klip po angielsku + polski glos w montazu (dubbing w oknach z tabeli 4.2); C) najpierw test polskiej mowy w Klingu (kwestie kanonu PL w cudzyslowie; status oficjalny BRAK DANYCH, test rzedu 4 pozytywny) i wybor po tescie.
- **P-3 (ciaglosc przy Elements).** A) Omni 4.0 z Elements i `first_frame`, jesli test zerowy potwierdzi; B) I2V 4.0 z `first_frame` bez Elements (spojnosc postaci tylko z klatki, glos bez profilu); C) Omni z Elements i `refer_image` ostatniej klatki zamiast `first_frame`.
- **P-4 (glos Marty).** A) generowany w klipie jako glos z telefonu z profilem `voice` (ten sam profil w Scenie 2); B) w klipie cisza w oknach L08/L10 (Karolina slucha), glos Marty wstawiony w montazu; C) generowany w klipie bez profilu, podmieniany w montazu.
- **P-5 (wyglad Karoliny).** A) ciemnobrazowe wlosy do ramion (FLOW, CLIP 0); B) jasne wlosy, niski kucyk lub luzno (`02_charakterystyki_postaci.md`); C) inny opis podany przez wlasciciela.
- **P-6 (insert swetra).** A) 3 s jak wygenerowany (ROZP U3); B) przyciac do 2 s w montazu (`05_inserty_closeup.md`), reszta sceny przesuwa sie o -1000 ms; C) insert usunac.
- **P-7 (napis "ZERO").** A) w montazu na K01, 6000-8000 ms (jak w 4.3); B) bez napisu w Scenie 1 (tytul tylko w czolowce 62 s); C) na poczatku K02.
- **P-8 (muzyka Sceny 1).** A) brak muzyki w calej scenie (tylko ambient); B) muzyka "ciepla, ambientowa, miejska" (SCEN l. 65) dodana w montazu pod klipami; C) tylko diegetyczna muzyka z kawiarni, cicho, w montazu.
- **P-9 (fps).** A) przyjac fps zmierzony w tescie zerowym i przeliczyc klatki w 4.3 (ms bez zmian); B) wymusic 24 fps w montazu (konwersja klatek); C) zostawic 24 fps jako zalozenie do konca serii i sprawdzac ms.
- **P-10 (tolerancja startu kwestii).** A) +/- 2 klatki (+/- 83 ms przy 24 fps); B) +/- 6 klatek (+/- 250 ms); C) inna wartosc podana przez wlasciciela.
- **P-11 (droga uruchomienia, ECHO-037 pkt 4).** A) MCP z konta aplikacji (kredyty aplikacji, linki 24 h); B) API Open Platform (pakiet Units, klucz, linki 30 dni); C) MCP do testu zerowego, API do serii.

---

## 9. Zakres i bezpieczenstwo tego pliku

- Zmieniony jest tylko ten plik (allowlista ZERO-PROD-002). Pliki wejsciowe (scenariusze, docs/research, uploads, archiwum) tylko czytane; ich SHA-256 policzone przed i po pracy w scratchpadzie sesji.
- Brak odczytow sieci, kont, kluczy, wywolan API i MCP, brak generowania wideo. Brak sekretow (w przykladach tylko `<API Key>`).
- Brak rankingu i rekomendacji wyboru narzedzia (ECHO-027); obie drogi uruchomienia opisane rownorzednie.
- Os czasu i prompty wygenerowano skryptem pomocniczym w scratchpadzie sesji (poza repozytorium), ktory sprawdza: ciaglosc kazdego toru w kazdym klipie, siatke 125 ms, sumy czasow = `duration`, brak nakladania kwestii.
