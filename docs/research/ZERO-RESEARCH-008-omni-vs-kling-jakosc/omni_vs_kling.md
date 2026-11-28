# ZERO-RESEARCH-008 — Gemini Omni 1.2 Flash vs Kling 4.0 / 4.0 Flash: jakosc obrazu, synchronizacja dzwieku, glosy i jezyk polski

## 1. Naglowek

- **Data zestawienia i odczytu:** 2026-11-28.
- **Zakres (ECHO-034):** wylacznie Google Gemini Omni 1.2 Flash (`gemini-omni-1.2-flash`, GA od 2026-11-05/06) oraz Kling 4.0 (`kling-4.0`, API od 2026-10-28) z wariantem Kling 4.0 Flash (API od 2026-11-04). Daty wg zatwierdzonego zestawienia `docs/research/ZERO-RESEARCH-005-zestawienie-zbiorcze/zestawienie_zbiorcze.md` (sek. 1.1, tylko odczyt).
- **Trzy obszary:** (A) jakosc obrazu wideo, (B) synchronizacja dzwieku z obrazem, (C) glosy i jezyk polski.
- **Zasada neutralnosci (ECHO-027):** plik zbiera charakterystyke i cytaty ze zrodel. Nie zawiera rankingu wlasnego, punktow, opinii Operatora, rekomendacji ani wniosku o wyborze. Oceny liczbowe i miejsca w rankingach pochodza wylacznie od zrodel zewnetrznych i sa podane jako cytat z nazwa zrodla, data i wersja. Wybor nalezy do wlasciciela.

### Legenda

| Oznaczenie | Znaczenie |
|---|---|
| **rzad 1** | dokumentacja lub ogloszenie dostawcy (Google, Kuaishou/Kling). Fakt o deklaracji dostawcy, nie o jakosci zmierzonej niezaleznie. |
| **rzad 4** | test, ranking, recenzja, opinia uzytkownika, blog posrednika. Zawsze **NIEPOTWIERDZONE**. |
| **NIEPOTWIERDZONE** | twierdzenie nie jest faktem; to relacja zrodla. |
| **[B]** odczyt bezposredni | tresc strony pobrana w tej sesji (curl / WebFetch) i przeczytana. |
| **[P]** odczyt posredni | host zablokowany w sesji; tresc znana tylko ze streszczenia wyszukiwarki (WebSearch, 2026-11-28). Strony nie czytalem; streszczenie moze byc niedokladne. |
| **[Z5]** | fakt rzedu 1 przejety z zatwierdzonego zestawienia ZERO-RESEARCH-005 (z jego zrodlami), bez nowego odczytu. |
| **BRAK DANYCH** | nie znalazlem zrodla; obok opis, gdzie szukano. |
| **[STARSZA WERSJA]** | wpis dotyczy Kling 3.0, Omni 1.1 / "Omni Flash" bez numeru lub innego modelu — trzymany osobno, nie dotyczy wersji z zakresu. |

Identyfikatory zrodel (O1..., N1...) odsylaja do sekcji 6. Daty "odczyt 2026-11-28" oznaczaja date odczytu; data publikacji jest podana, gdy zrodlo lub streszczenie ja wskazuje.

## 2. Obszar A — jakosc obrazu wideo

### A.1 Gemini Omni 1.2 Flash

| Cecha | Wpis (cytat lub streszczenie zrodla) | Wersja w zrodle | Zrodlo, data | Rzad / oznaczenie / odczyt |
|---|---|---|---|---|
| Rozdzielczosc natywna a upscaling | Baza 360p/720p; 1080p i 4K skalowane w gore (upscaling), nie natywna generacja. Dokumentacja: "`1080p` — 1080p output (upscaled)", "`4k` — 4K output (upscaled)". | 1.2 Flash | [Z5] sek. 2 tab. 1 (z R001 Z8); O2, odczyt 2026-11-28 | rzad 1 / fakt dokumentacji / [B] |
| Spojnosc postaci (deklaracja) | "using up to 6 reference images to keep characters and objects consistent across shots". | Omni (strona API Omni; model domyslny 1.2 Flash) | O2, odczyt 2026-11-28 | rzad 1 / deklaracja dostawcy / [B] |
| Spojnosc (deklaracja) | "More consistent results: stronger adherence to image and video references keeps products, characters, and brand details consistent from shot to shot." | 1.2 Flash | O1, publ. 2026-11-06 | rzad 1 / deklaracja dostawcy / [B] |
| Spojnosc — wlasne porownanie dostawcy | Wg streszczenia: Google podaje w porownaniu 1.2 vs 1.1 "62% to 38%" (text-to-video, visual consistency) i 63% vs 37% (reference-to-video, identity consistency); inne serwisy podaja dla image-to-video 60/40 i 57/43. Metoda, liczba ocen i oceniajacy: BRAK DANYCH. Strony DeepMind nie odczytalem (host niedostepny). | 1.2 Flash vs 1.1 | N1 (deepmind.google), N2 (eesel.ai) i inne z wyniku; odczyt 2026-11-28 | rzad 1 przez posrednika (liczby z wyszukiwarki) — NIEPOTWIERDZONE / [P] |
| Ograniczenia ruchu i fizyki | Wg streszczenia: Google pisze, ze szybka akcja sportowa i zlozona fizyka sa "still in development", "expect the occasional weird artifact". Tego zdania nie znalazlem w odczytanej bezposrednio sekcji "Limitations" O2 (tam tylko ograniczenia funkcji). | Omni (bez pewnosci, czy 1.2) | streszczenie wyniku dla N3 (buildfastwithai.com) i in.; odczyt 2026-11-28 | rzad 4 — NIEPOTWIERDZONE / [P] |
| Artefakty i fizyka (recenzje) | Wg streszczenia: "physics still wobble"; tester fizyki: cegly "suddenly disappear or morph into others"; inna recenzja: fizyka "strong, but not better than Seedance 2.0"; woda i tkanina wypadaja dobrze. | czesc recenzji dotyczy "Omni Flash" bez numeru [STARSZA WERSJA mozliwa] | N3, N4 (eesel.ai), N5 (invideo.io); odczyt 2026-11-28 | rzad 4 — NIEPOTWIERDZONE / [P] |
| Spojnosc twarzy przy edycji | Wg streszczenia: po trzech turach edycji linia zuchwy zmienila sie subtelnie, kolor oczu z brazowego na piwny po zmianie tla. | Omni Flash (wersja niejednoznaczna w streszczeniu) | N3/N4 (wynik wyszukiwania); odczyt 2026-11-28 | rzad 4 — NIEPOTWIERDZONE / [P] |
| Ruch kamery | Wg streszczenia: w tescie 6 modeli "Omni 1.2 jako jedyny zrobil prawdziwy obrot bez ciec". | 1.2 (obok Omni 1.1, Veo 3.1 Lite, Seedance 2.0 Fast, Wan 3.0, Kling 3.0) | N10 (promptowy.com), odczyt 2026-11-28 | rzad 4 — NIEPOTWIERDZONE / [P] |
| Ranking zewnetrzny (Arena) | Cytat ze streszczenia: Arena (arena.ai), tablica Text-to-Video, stan 2026-11-08: "Gemini Omni 1.2 Flash ... 1540±16 with 1,714 votes", oznaczony jako "Preliminary"; teamday.ai podaje migawke z 2026-11-06: 1541 (preliminary). | 1.2 Flash | N6 (arena.ai), N7 (infosdivers.com), N8 (teamday.ai); odczyt 2026-11-28 | rzad 4 (ranking) — NIEPOTWIERDZONE / [P] |
| Ranking zewnetrzny (Artificial Analysis) | Wpisu "Gemini Omni 1.2 Flash" w tablicy AA-Video-T2V v2.1 nie znalazlem. Starsze wpisy dotycza "Gemini Omni Flash" (np. 1238, 2026-09-02, tablica "with audio") — [STARSZA WERSJA], skala Elo innej wersji tablicy, nieporownywalna. | "Gemini Omni Flash" = 1.1 | N9 (artificialanalysis.ai), odczyt 2026-11-28 | rzad 4 — NIEPOTWIERDZONE / [P] |

### A.2 Kling 4.0

| Cecha | Wpis | Wersja w zrodle | Zrodlo, data | Rzad / oznaczenie / odczyt |
|---|---|---|---|---|
| Rozdzielczosc natywna | "Kling 4.0 supports native 4K and 10-bit output"; tryby "720p / 1080p / 4K / 1080p HDR / 4K HDR", domyslnie 1080p. 4K od 2026-11-19. | 4.0 | O3 (sek. 5.1, 6.10), odczyt 2026-11-28; [Z5] sek. 2 | rzad 1 / deklaracja dostawcy / [B] |
| Ruch (deklaracja) | "Kling 4.0 improves stability for large-scale motion, continuous action, and complex camera movements." | 4.0 | O3 sek. 4.1, odczyt 2026-11-28 | rzad 1 / deklaracja dostawcy / [B] |
| Ruch i fizyka (recenzje) | Wg streszczenia: dobre wyniki dla wody i czastek; "slight morphing during structural disintegration"; przy szybkiej walce "limb distortion, sliding feet, ... sudden character teleportation"; inny serwis: Seedance 2.5 "noticeably superior" w rozprysku i odlamkach. | 4.0 | N11 (youart.ai), N12 (dxbuilder.io), N13 (jxp.com / miraflow.ai); odczyt 2026-11-28 | rzad 4 — NIEPOTWIERDZONE / [P] |
| Spojnosc twarzy | Wg streszczenia: portret stabilny przez caly klip; przy zmianie twarzy "visible subject inconsistency within the first two seconds"; Virse: "CGI-like movement, unwanted camera cuts, facial inconsistencies"; dxbuilder: "facial identity drift" przy szybkich obrotach (video-to-video). | 4.0 | N11, N14 (virse.ai), N12; odczyt 2026-11-28 | rzad 4 — NIEPOTWIERDZONE / [P] |
| Artefakty | Wg streszczenia: "occasional anatomical awkwardness" przy szybkim kontakcie; dedykowanego testu dloni nie znaleziono. | 4.0 | N11/N12; odczyt 2026-11-28 | rzad 4 — NIEPOTWIERDZONE / [P] |
| Ranking zewnetrzny (Artificial Analysis) | Cytat ze streszczenia: AA text-to-video: Kling 4.0 "rank 11 with an Elo of 1144 (95% interval 1129 to 1159), from 3,895 samples"; image-to-video: "rank 6 with an Elo of 1139 (interval 1123 to 1155)". Data migawki: BRAK DANYCH. | 4.0 | N9, odczyt 2026-11-28 | rzad 4 (ranking) — NIEPOTWIERDZONE / [P] |
| Ranking zewnetrzny (Arena) | Wg streszczenia: recenzja z 2026-10-21 podaje "Not rated yet"; w odczytanej przez wyszukiwarke migawce Arena widoczny tylko Kling 2.5 Turbo [STARSZA WERSJA]. Wpisu Kling 4.0 na Arenie: BRAK DANYCH. | 4.0 | N6, N15 (moelueker.com); odczyt 2026-11-28 | rzad 4 — NIEPOTWIERDZONE / [P] |
| [STARSZA WERSJA] | llm-stats: "Kling v3" 1934 (76 glosow, wlasna skala, preliminary) — Kling 3.0, nie z zakresu. | 3.0 | N16 (llm-stats.com) | rzad 4 — NIEPOTWIERDZONE / [P] |

### A.3 Kling 4.0 Flash

| Cecha | Wpis | Wersja | Zrodlo, data | Rzad / oznaczenie / odczyt |
|---|---|---|---|---|
| Rozdzielczosc | Tylko "720p" (tabela 5.1); 3-20 s; bez pierwszej+ostatniej klatki i wielu klatek kluczowych. | 4.0 Flash | O3 sek. 5.1, odczyt 2026-11-28; [Z5] | rzad 1 / [B] |
| Jakosc obrazu wzgledem 4.0 | Wg streszczenia: tester kie.ai: pelny Kling 4.0 "beats Flash on picture and audio clarity and on lip sync"; inna recenzja: zgloszone "extra music and extra cuts"; atlascloud: "subtle structural distortion on fast wing motion". | 4.0 Flash | N17 (kie.ai), N18 (atlascloud.ai, Flash vs MiniMax H3), N19 (atlascloud.ai, problemy Flash); odczyt 2026-11-28 | rzad 4 — NIEPOTWIERDZONE / [P] |
| Ranking zewnetrzny | Osobnego wpisu Kling 4.0 Flash w rankingach (Arena, AA): BRAK DANYCH. Szukano: WebSearch "Kling 4.0 Flash" + leaderboard/Elo; strony rankingow zablokowane. | — | — | BRAK DANYCH |

### A.4 Porownania bezposrednie (ten sam prompt lub obraz w obu systemach)

| Test | Wpis (wg streszczenia wyszukiwarki) | Wersje w tescie | Zrodlo, data | Rzad / oznaczenie / odczyt |
|---|---|---|---|---|
| CellCog, 11 testow, jedno ujecie na model, te same referencje, prompt, dlugosc i rozdzielczosc | Bez wskazania zwyciezcy. Test 2 (dialog w kawiarni): wszystkie trzy przypisaly kwestie wlasciwym mowcom i utrzymaly twarze; "Omni had the most natural back-and-forth"; u Kling palce na moment zlaly sie z uchem filizanki. Test 3 (nalesnik): Omni — jeden obrot, ladowanie plasko; Kling — nalesnik "flew almost to the top of the frame before landing". Serwis deklaruje, ze jego agent wideo dziala na Seedance 2.5 (konflikt interesow). | Gemini Omni 1.2 Flash, Kling 4.0, Seedance 2.5 | N20 (cellcog.ai), publ. ok. 3 tygodnie przed 2026-11-28 (dokladna data BRAK DANYCH) | rzad 4 (test) — NIEPOTWIERDZONE / [P] |
| Clipia, recenzja MAGI-2, 4 identyczne prompty | "on the picture, Gemini Omni 1.2 and Seedance 2.5 take the top two places, while MAGI-2 and Kling 4.0 share third and fourth"; obraz Kling opisany jako "calm and realistic". Streszczenie zaznacza wewnetrzne niespojnosci artykulu co do kolejnosci. | Gemini Omni 1.2, Kling 4.0, Seedance 2.5, MAGI-2 | N21 (clipia.ai); data BRAK DANYCH | rzad 4 (test) — NIEPOTWIERDZONE / [P] |
| Wpis na X (jezyk japonski) | Wg streszczenia: Gemini Omni "looked best visually", Kling 4.0 "strongest on backgrounds". | "Gemini Omni" (bez numeru wersji) i Kling 4.0 | N22 (x.com/muku_sns); data BRAK DANYCH | rzad 4 (opinia) — NIEPOTWIERDZONE / [P] |
| Wideo YouTube, identyczne prompty, 4 modele | Wg streszczenia: komentujacy ocenil "Gemini 1.2 Flash lowest of the four" i napisal o Kling "so bad in terms of the cost effectiveness and texture"; transkrypcja obcieta. | Seedance 2.5 Flash, Seedance 2.5, Gemini Omni 1.2 Flash, Kling 4.0 | N23 (youtube.com/watch?v=CVBOhyiUt04); data BRAK DANYCH | rzad 4 (opinia) — NIEPOTWIERDZONE / [P] |
| Inne zestawienia "Omni vs Kling 4.0" | creatify.ai, comparegen.ai, tech-insider.org, nanobanana-pro.studio, opus.pro — wg streszczen porownuja specyfikacje (dlugosc, rozdzielczosc, cena), nie wyniki testow. comparegen.ai: pod-ocena jakosci 80 (Gemini Omni Flash) vs 82 (Kling AI), podstawa oceny nieopisana, wersje niejednoznaczne. | mieszane / niejednoznaczne | N24 (creatify.ai), N25 (comparegen.ai), N26 (tech-insider.org); odczyt 2026-11-28 | rzad 4 — NIEPOTWIERDZONE / [P] |
| [STARSZA WERSJA] | Wideo "Kling 4.0 vs Seedance 2.5 vs Gemini Omni Flash 1.1 vs Minimax H3" — dotyczy Omni 1.1, nie 1.2; tresci nie odczytano. promptsrush.com / aimagic.fun — Kling 3.0. | Omni 1.1; Kling 3.0 | N27 (youtube.com/watch?v=uMfZfEEIZm4), N28 (promptsrush.com) | rzad 4 — NIEPOTWIERDZONE / [P] |

## 3. Obszar B — synchronizacja dzwieku z obrazem

Fakty rzedu 1 o funkcjach audio (bez powtarzania szczegolow): Omni 1.2 Flash — audio w kazdym wyjsciu, mowa, muzyka, efekty, brak wejscia audio i referencji audio w API; przedluzanie +3..10 s na ture do 30 s (Gemini API) lub 40 s (Vertex, rozbieznosc R-11). Kling 4.0 — audio stereo, AV-sync domyslnie w API, 3-30 s, przedluzanie "Coming Soon"; 4.0 Flash — audio natywne w omni-video, 3-20 s, bez przedluzania. Zrodlo: [Z5] sek. 2-3 (wiersze Omni 1.2 Flash, Kling 4.0, Kling 4.0 Flash; rozbieznosci R-1, R-11, R-12).

### B.1 Gemini Omni 1.2 Flash

| Cecha | Wpis | Wersja | Zrodlo, data | Rzad / oznaczenie / odczyt |
|---|---|---|---|---|
| Lip-sync, wielu mowcow (deklaracja) | "More natural speech: You can generate scenes with more fluid, natural-sounding dialogue, clearer lip-sync, and distinct multi-speaker conditioning." | 1.2 Flash | O1, publ. 2026-11-06 | rzad 1 / deklaracja dostawcy / [B] |
| Przedluzanie z mowa (ograniczenie) | "You cannot extend an uploaded video where someone is talking to add additional dialogue (characters can remain silent, or multi-turn extension with `previous_interaction_id` can be used)." | Omni (strona API; 1.2 Flash) | O2 "Limitations", odczyt 2026-11-28 | rzad 1 / [B] |
| Rozjazd dzwieku przy edycji | Wg streszczenia: w tescie praktycznym dzwiek "drifted slightly with each edit", przesuniecie ok. jednej klatki, rosnace w kolejnych edycjach. | 1.2 Flash (wg streszczenia; wersja nie w pelni pewna) | wynik wyszukiwania z N29 (datacamp.com) / N30 (recraft.ai) — przypisanie do konkretnej strony niepewne; odczyt 2026-11-28 | rzad 4 — NIEPOTWIERDZONE / [P] |
| Powtarzanie slow w mowie | Watek na forum deweloperow Google: Omni 1.2 Flash "randomly repeats words or phrases in generated speech"; ponowne wygenerowanie czasem daje czysta mowe. | 1.2 Flash | N31 (discuss.ai.google.dev, watek 204773); data BRAK DANYCH | rzad 4 (opinia uzytkownika na forum dostawcy) — NIEPOTWIERDZONE / [P] |
| Zmiana glosu postaci miedzy kwestiami | Wg streszczenia: poradnik testowania dialogow (5-8 tur) zaleca sprawdzac, czy glos postaci zostaje ten sam przy powrocie po innym mowcy (problem: "correct mouth moving while the speaker's voice changes on their second turn"). To kryterium kontroli, nie wynik pomiaru. | 1.2 Flash | N32 (atlascloud.ai, multi-speaker dialogue); data BRAK DANYCH | rzad 4 — NIEPOTWIERDZONE / [P] |
| [STARSZA WERSJA] | Recenzja oryginalnego "Omni Flash" (1.1): dwoch mowcow w kadrze "remain a weak spot", model "often drops sync or misattributes dialogue"; inny blog: spojnosc przez ok. 4 tury edycji. Nie dotyczy 1.2. | Omni Flash (1.1) | N5 (invideo.io), N33 (happycapy.ai) | rzad 4 — NIEPOTWIERDZONE / [P] |
| Efekty i ambient | Wpis z cytatu klienta w ogloszeniu: "...the physics and sound feel real." (invideo). Niezaleznego testu trafnosci efektow i ambientu dla 1.2: BRAK DANYCH (szukano: WebSearch "Gemini Omni 1.2 Flash audio sync problems", "sound effects"). | 1.2 Flash | O1 (cytat partnera w materiale dostawcy), publ. 2026-11-06 | rzad 1 (material dostawcy, opinia partnera) — NIEPOTWIERDZONE jako ocena jakosci / [B] |

### B.2 Kling 4.0

| Cecha | Wpis | Wersja | Zrodlo, data | Rzad / oznaczenie / odczyt |
|---|---|---|---|---|
| AV-sync (deklaracja) | "It supports high-quality audio and two-channel stereo, keeping voices, dialogue, and performances naturally synchronized." | 4.0 | O3 sek. 4.1, odczyt 2026-11-28 | rzad 1 / deklaracja dostawcy / [B] |
| Wejscie audio | "Audio input is supported only as voice profiles, used to assign a voice to a speaker. Background music and sound effects are generated by the model from the visuals and should be described in the audio portion of the prompt." | 4.0 | O3, odczyt 2026-11-28 | rzad 1 / [B] |
| Lip-sync, test dialogu | Wg streszczenia: ChatCut, test 10 s w kawiarni: oba glosy przepisane slowo w slowo, zaden mowca nie poruszal ustami w trakcie kwestii drugiego. Pojedynczy test. | 4.0 | N34 (chatcut.io); data BRAK DANYCH | rzad 4 (test) — NIEPOTWIERDZONE / [P] |
| Niechciana muzyka i efekty | Wg streszczenia: kilka recenzji zglasza muzyke w tle mimo prosby o jej brak; zalecane "dialogue only, no background music" i kontrola pliku; zgloszone "unintended voices, music, or sound effects". | 4.0 i 4.0 Flash | N14 (virse.ai), N19 (atlascloud.ai), N36 (seaart.ai); odczyt 2026-11-28 | rzad 4 — NIEPOTWIERDZONE / [P] |
| Brakujace efekty | Wg streszczenia: dxbuilder — przy szybkiej walce "missing impact sound effects". | 4.0 | N12; odczyt 2026-11-28 | rzad 4 — NIEPOTWIERDZONE / [P] |
| Jakosc dialogu — relacje sprzeczne | Wg streszczenia: jedna recenzja: "kept voice tracks distortion-free across every dialogue test"; inna: audio to "hit-or-miss area". Zapisane obok siebie (sek. 5). | 4.0 | N13, N14; odczyt 2026-11-28 | rzad 4 — NIEPOTWIERDZONE / [P] |
| Dlugie klipy (do 30 s) | Wg streszczenia: dluzsze klipy daja "more opportunities for missed actions, unexpected cuts, character drift, and audio problems"; "a completed 30-second output is not necessarily a successful 30-second scene". Pomiaru rozjazdu dialogu w 30 s: BRAK DANYCH. | 4.0 | N14, N36; odczyt 2026-11-28 | rzad 4 — NIEPOTWIERDZONE / [P] |

### B.3 Kling 4.0 Flash

| Cecha | Wpis | Wersja | Zrodlo, data | Rzad / oznaczenie / odczyt |
|---|---|---|---|---|
| Audio i lip-sync | Wg streszczenia: atlascloud — "strong audio-visual alignment on solo speech turns"; ChatCut — audio stereo zweryfikowane; kie.ai — pelny 4.0 lepszy od Flash w lip-sync; MaxVideoAI — klatki i transkrypcje "do not establish precise lip sync". | 4.0 Flash | N18, N34, N17, N37 (maxvideoai.com); odczyt 2026-11-28 | rzad 4 — NIEPOTWIERDZONE / [P] |
| Lip-sync wzgledem 3.0 (wczesny dostep Flash) | Wg streszczenia (odczyt posredni, strony nie otwarto): MindStudio testowal build wczesnego dostepu Kling 4.0 Flash (720p), nie pelny model — streszczenie: "this is the Flash variant rather than the full model"; o lip-sync: "lip sync drift ... appears to be largely fixed in 4.0" (doslowne brzmienie cytatu, w tym slowo "drift", niepotwierdzone; moje zapytanie WebSearch extended 2026-11-28 "MindStudio Kling 4.0 first look early access Flash 720p lip sync" nie zwrocilo strony MindStudio, a streszczenie innych zrodel podaje, ze drift lip-sync "appears to be largely fixed" w testach dialogowych). Wniosku dla pelnego 4.0 z tego wpisu nie wyciagam. | 4.0 Flash (early access, 720p) | N35 (mindstudio.ai, host zablokowany ENOTFOUND); data BRAK DANYCH; odczyt 2026-11-28 | rzad 4 — NIEPOTWIERDZONE / [P] |
| Wielu mowcow | Liczba mowcow dla Flash: NIEPOTWIERDZONE w rzedzie 1 ([Z5] tab. 2); niezaleznego testu wielu mowcow dla Flash: BRAK DANYCH (szukano: WebSearch "Kling 4.0 Flash review quality 720p audio lip-sync test"). | 4.0 Flash | [Z5] | BRAK DANYCH |

### B.4 Porownania bezposrednie

| Test | Wpis (wg streszczenia) | Wersje | Zrodlo, data | Rzad / oznaczenie / odczyt |
|---|---|---|---|---|
| CellCog, test 8 (piekarz mowi zadana kwestie) | Wszystkie trzy modele wypowiedzialy kazde slowo. Warunki rozne: Kling dostal glos sklonowany z nagrania, Omni tylko tekst ("its API takes no audio input today"), Seedance nagranie jako referencje. | Omni 1.2 Flash, Kling 4.0, Seedance 2.5 | N20; publ. ok. 3 tyg. przed 2026-11-28 | rzad 4 (test) — NIEPOTWIERDZONE / [P] |
| CellCog, test 2 (dialog dwoch osob) | Kwestie przypisane wlasciwym mowcom u wszystkich; "Omni had the most natural back-and-forth". | jw. | N20 | rzad 4 — NIEPOTWIERDZONE / [P] |
| Clipia (recenzja MAGI-2), dialog dwoch postaci i lip-sync | "Gemini Omni 1.2 is the only model that kept the face, the aspect ratio and the lip-sync at the same time"; Kling 4.0 na 3.-4. miejscu w tym tescie (miejsca wg zrodla). | Omni 1.2, Kling 4.0, Seedance 2.5, MAGI-2 | N21; data BRAK DANYCH | rzad 4 (test) — NIEPOTWIERDZONE / [P] |
| gemini-omni.dev | Wg streszczenia: blog o charakterze promocyjnym pisze, ze Kling 4.0 ma "basic lip sync", a Omni "48kHz audiovisual output". Serwis o nazwie produktu Google — powiazanie z dostawca BRAK DANYCH. | Kling 4.0 vs "Gemini Omni" (wersja niejednoznaczna) | N38 (gemini-omni.dev); data BRAK DANYCH | rzad 4 — NIEPOTWIERDZONE / [P] |

## 4. Obszar C — glosy i jezyk polski

### C.1 Gemini Omni 1.2 Flash

| Cecha | Wpis | Wersja | Zrodlo, data | Rzad / oznaczenie / odczyt |
|---|---|---|---|---|
| Jezyki oficjalnie | "English (EN) is fully supported, but other languages have not been evaluated, so they may work but results can vary." | Omni (strona API; 1.2 Flash) | O2 "Technical details", odczyt 2026-11-28; [Z5] tab. 2 | rzad 1 / [B] |
| **Polski — oficjalnie** | BRAK DANYCH: polski nie jest wymieniony; status "not evaluated" (jw.). | 1.2 Flash | O2; [Z5] | rzad 1 / BRAK DANYCH (wsparcie) |
| Wybor glosu / sklonowany glos | "Voice editing is not supported."; "Uploading audio inputs or audio references is unsupported in the current version of the API." Ogloszenie: "Audio references are gated behind allowlisting." (rozbieznosc R-12 w [Z5]). Parametru wyboru glosu w API: BRAK DANYCH. | 1.2 Flash | O2, O1; [Z5] R-12 | rzad 1 / [B] |
| Lektor (glos zza kadru) | Glos zza kadru generowany promptem; w dokumentacji przyklad wylaczenia "No dialogue or voiceover." ([Z5]/R002 Z20). Testu jakosci polskiego lektora: BRAK DANYCH. | 1.2 Flash | [Z5] (R002 veo.md Z20) | rzad 1 / BRAK DANYCH (jakosc) |
| **Polski — relacje uzytkownikow** | Wg streszczen (jeden autor, serwis promptowy.com): scena wigilijna z trzema glosami — bez bledow w transkrypcji Whisper large-v3; scena z nauczycielka — tekst i data poprawnie; scena przy grillu — zgubiona fraza "nie z Lidla" (ta sama scena z klatka referencyjna — pelna); autor: polski "bardzo dobrze, ale nie zawsze w calosci"; ruch warg oceniany "na oko". | 1.2 Flash | N39 (promptowy.com/gemini-omni-1-2-po-polsku), N40 (promptowy.com/gemini-omni-1-2-flash-test); data publikacji BRAK DANYCH (streszczenie wskazuje niespojne daty w tekstach) | rzad 4 (test autorski) — NIEPOTWIERDZONE / [P] |
| Polski — porownanie wielu modeli | Wg streszczenia: w scenie z polskim dialogiem Omni 1.2 "zgubil koncowke pierwszego zdania"; w tym samym tescie Kling 3.0 [STARSZA WERSJA] "przerobil tekst na inny". Kling 4.0 nie byl w tym tescie (test z 2026-10-08, model niedostepny w API). | Omni 1.2; Kling 3.0 | N10 (promptowy.com/gemini-omni-1-2-vs-seedance-kling-veo-wan) | rzad 4 — NIEPOTWIERDZONE / [P] |
| Akcent, naturalnosc polskiej mowy | BRAK DANYCH: zadne streszczenie nie opisuje akcentu Omni 1.2 po polsku. Szukano: WebSearch "Gemini Omni 1.2 Flash polski jezyk dialog test", "promptowy ... Gemini Omni 1.2 po polsku lip-sync". | 1.2 Flash | — | BRAK DANYCH |
| [STARSZA WERSJA] | Wg streszczenia: "Gemini Omni Flash 1.1" wymieniony wsrod modeli, ktore bezblednie powiedzialy trudne polskie zdanie. Nie dotyczy 1.2. | Omni 1.1 | N41 (promptowy.com/ai-do-tworzenia-filmow) | rzad 4 — NIEPOTWIERDZONE / [P] |

### C.2 Kling 4.0

| Cecha | Wpis | Wersja | Zrodlo, data | Rzad / oznaczenie / odczyt |
|---|---|---|---|---|
| Jezyki oficjalnie | Tabela: "Chinese, English, Japanese, Korean, Spanish, Portuguese, German, French, Hindi"; sek. 4.4: "...Hindi, and other languages, along with multiple accents and dialects". | 4.0 | O3 (sek. 4.4 i tabela audio), odczyt 2026-11-28; [Z5] tab. 2 | rzad 1 / [B] |
| **Polski — oficjalnie** | BRAK DANYCH: polski nie jest wymieniony; tylko ogolne "other languages" bez nazw. | 4.0 | O3; [Z5] | rzad 1 / BRAK DANYCH (wsparcie) |
| Jak uzyskac dialog w jezyku | "To generate dialogue in a specific language, write the dialogue in that language directly inside quotation marks"; mozna podac wiek, ton, tempo, emocje. | 4.0 | O3, odczyt 2026-11-28 | rzad 1 / [B] |
| Wybor / sklonowany glos | Tabela 5.1: "Voice Cloning — Supported", "Element-Bound Voice — Supported" (4.0); profile glosu do 3, probka 5-30 s. | 4.0 | O3 sek. 5.1; [Z5] tab. 2 | rzad 1 / [B] |
| **Polski — relacje uzytkownikow** | Wg streszczen (jeden autor, promptowy.com): test z 2026-10-21, 3 klipy, transkrypcja faster-whisper large-v3: "3 z 3 polskich kwestii bez bledu", WER 0, w tym lamaniec ze Szczebrzeszynem; Whisper rozpoznal jezyk jako polski z pewnoscia 0,97-0,99; klipy 720p, generowane recznie na kling.ai (nie przez API); nie testowano dlugich dialogow dwoch postaci po polsku. Autor: "wynik mojego testu, nie deklaracja producenta". Osobny tekst: 5 scen, polska mowa 9,5/10 (ocena autora). | 4.0 | N42 (promptowy.com/kling-4-0-po-polsku), N43 (promptowy.com/kling-4-0-test); test 2026-10-21 | rzad 4 (test autorski) — NIEPOTWIERDZONE / [P] |
| Spiew po polsku | Istnieje wpis "Kling 4.0: teledysk disco polo ze spiewem po polsku" — tresci nie odczytano (ani bezposrednio, ani w streszczeniu). | 4.0 | N44 (promptowy.com/kling-4-0-teledysk-disco-polo) | rzad 4 — NIEPOTWIERDZONE / [P], tresc BRAK DANYCH |
| Akcent | Dla 4.0: BRAK DANYCH o akcencie polskiej mowy (streszczenia podaja tylko poprawnosc slow). Szukano: WebSearch "Kling 4.0 polski jezyk mowa test lip sync", "promptowy.com Kling 4.0 po polsku". | 4.0 | — | BRAK DANYCH |
| [STARSZA WERSJA] | Kling 3.0, test 2026-09-28: mylil 4-10 z 12 slow lamanca; wczesniejszy tekst: "obca wymowa", Whisper zle rozpoznal 33-83%. Nie dotyczy 4.0. | 3.0 | N45 (promptowy.com/kling-po-polsku), N42 | rzad 4 — NIEPOTWIERDZONE / [P] |

### C.3 Kling 4.0 Flash

| Cecha | Wpis | Wersja | Zrodlo, data | Rzad / oznaczenie / odczyt |
|---|---|---|---|---|
| Jezyki oficjalnie | NIEPOTWIERDZONE: tabela jezykow 4.0 bez przypisania do Flash ([Z5] tab. 2). | 4.0 Flash | [Z5] | rzad 1 / NIEPOTWIERDZONE |
| **Polski — oficjalnie** | BRAK DANYCH. | 4.0 Flash | [Z5] | BRAK DANYCH |
| Wybor / sklonowany glos | "Voice Cloning — Not supported", "Element-Bound Voice — Not supported". | 4.0 Flash | O3 sek. 5.1, odczyt 2026-11-28 | rzad 1 / [B] |
| **Polski — relacje uzytkownikow** | BRAK DANYCH: zadnego testu polskiej mowy dla 4.0 Flash nie znalazlem. Szukano: WebSearch "\"Kling 4.0 Flash\" po polsku mowa test" (wyniki dotycza 4.0 i 3.0). | 4.0 Flash | — | BRAK DANYCH |

### C.4 Obejscia (zewnetrzny polski glos, dubbing, lip-sync z wlasnym nagraniem)

| Droga | Wpis | Dotyczy | Zrodlo, data | Rzad / oznaczenie / odczyt |
|---|---|---|---|---|
| Kling: lip-sync z wgranym nagraniem | Osobny endpoint `/v1/videos/advanced-lip-sync`: wgrane audio 2-60 s. Jezyk nagrania: dowolny plik audio; jakosc dla polskiego BRAK DANYCH. | Kling (endpoint, nie model 4.0) | zatwierdzone R002 `kling.md` Z17 (kling.ai/document-api/api/video/lip-sync) | rzad 1 / [B w R002] |
| Kling: TTS dostawcy | `/v1/audio/tts`: `voice_language` tylko zh/en. | Kling | R002 `kling.md` Z18 | rzad 1 / [B w R002] |
| Kling 4.0: profil glosu z nagrania | Voice cloning / profil glosu (5-30 s) w 4.0 — czy profil z polskiej probki daje polska mowe: BRAK DANYCH. | 4.0 | O3; [Z5] | rzad 1 (funkcja) / BRAK DANYCH (polski) |
| Omni: wlasne nagranie | Wejscie audio i referencje audio nieobslugiwane w API (O2); dubbing musi byc poza modelem. | 1.2 Flash | O2 | rzad 1 / [B] |
| Google: osobny TTS z polskim | Gemini TTS: Polish obslugiwany; Cloud TTS: "Polish (Poland) pl-PL GA" — osobne uslugi, nie Omni. | uslugi TTS Google | R002 `veo.md` Z13 | rzad 1 / [B w R002] |
| Dubbing zewnetrzny + lip-sync | Wg streszczen: ElevenLabs Dubbing obsluguje polski, "does not offer lip sync in Dubbing"; sync.so laczy glos ElevenLabs z lip-sync; polskie poradniki opisuja zestaw "ElevenLabs + osobny modul lip-sync". Testu takiej sciezki na klipach Omni 1.2 lub Kling 4.0: BRAK DANYCH. | narzedzia zewnetrzne | N46 (elevenlabs.io), N47 (sync.so), N48 (promptowy.com/dubbing-ai), N49 (oscarrak.pl); odczyt 2026-11-28 | rzad 4 — NIEPOTWIERDZONE / [P] |

## 5. Sprzecznosci miedzy zrodlami i Luki

### 5.1 Sprzecznosci (zapisane obok siebie, bez rozstrzygania)

| Nr | Temat | Zrodlo X | Zrodlo Y |
|---|---|---|---|
| S-1 | Lip-sync Kling 4.0 w dialogu wzgledem Omni 1.2 | N21 (Clipia): Kling 4.0 na 3.-4. miejscu w tescie dialogu i lip-sync; Omni 1.2 jako jedyny utrzymal twarz, proporcje i lip-sync | N34 (ChatCut): w tescie dialogu Kling 4.0 oba glosy slowo w slowo, poprawny podzial kwestii; N20 (CellCog): wszystkie trzy modele przypisaly kwestie wlasciwym mowcom |
| S-2 | Jakosc dialogu Kling 4.0 | N13: "kept voice tracks distortion-free across every dialogue test" | N14: audio "hit-or-miss area" |
| S-3 | Jakosc obrazu Omni 1.2 vs Kling 4.0 | N21: obraz Omni 1.2 i Seedance 2.5 na dwoch pierwszych miejscach, Kling 4.0 3.-4.; N22: Omni "looked best visually" | N23: komentujacy stawia Gemini 1.2 Flash na ostatnim miejscu z czterech; N25: pod-ocena jakosci 80 (Omni Flash) vs 82 (Kling AI) |
| S-4 | Polski w Omni 1.2 (ten sam autor) | N39/N40: scena z trzema glosami bez bledow; wg innego streszczenia "0% bledow slow" w tescie 1.2 | N10: Omni 1.2 "zgubil koncowke pierwszego zdania"; N39: zgubiona fraza w scenie przy grillu |
| S-5 | Ranking Omni 1.2 Flash | N6/N7: Arena 1540±16 (2026-11-08) | N8: 1541 (migawka 2026-11-06); obie oznaczone "preliminary" |
| S-6 | Porownanie 1.2 vs 1.1 (dane Google przez posrednikow) | N1/N2: 62/38 (T2V visual consistency), 63/37 (R2V identity) | inne serwisy z tego samego wyniku: 60/40 i 57/43 (image-to-video) |
| S-7 | Lista jezykow Kling 4.0 | O3 (rzad 1, [B]): 9 jezykow z hindi | wg streszczenia wyniku z promptowy.com: lista 4.0 z indonezyjskim ("Indonesian (with Hindi noted elsewhere)") — por. R002 `kling.md` Z10: ta rozbieznosc nie zostala potwierdzona |
| S-8 | Ograniczenia fizyki Omni | wg streszczenia (N3 i in.): Google pisze o "occasional weird artifact" i fizyce "still in development" | O2 (rzad 1, [B]): sekcja "Limitations" takiego zdania nie zawiera (zawiera tylko ograniczenia funkcji) |

### 5.2 Luki

- **Brak niezaleznego, kontrolowanego benchmarku** porownujacego Omni 1.2 Flash i Kling 4.0 na tych samych promptach z jawna metoda. Znalezione porownania bezposrednie (N20, N21, N22, N23) to pojedyncze ujecia lub opinie; N20 deklaruje powiazanie z Seedance.
- **Brak wspolnego rankingu z obiema wersjami:** Arena — wpis Omni 1.2 Flash jest, Kling 4.0 BRAK DANYCH; Artificial Analysis — wpis Kling 4.0 jest (bez daty migawki), Omni 1.2 Flash BRAK DANYCH. Kling 4.0 Flash — brak w obu.
- **Polski:** jedyne relacje o polskiej mowie dla obu systemow pochodza z jednego serwisu (promptowy.com, jeden autor, male proby). Kling 4.0 Flash po polsku — BRAK DANYCH. Akcent i naturalnosc polskiej mowy (poza poprawnoscia slow) — BRAK DANYCH dla obu. Polski lektor (glos zza kadru) — BRAK DANYCH dla obu. Sklonowany glos z polskiej probki w Kling 4.0 — BRAK DANYCH.
- **Synchronizacja przy przedluzaniu:** Omni (extend do 30 s) — pomiaru rozjazdu mowy przy przedluzaniu BRAK DANYCH; Kling 4.0 — przedluzania w API brak ("Coming Soon"), wiec brak testow; dlugie klipy 30 s — tylko ogolne relacje (N14, N36).
- **Trafnosc efektow i ambientu Omni 1.2** — tylko cytat partnera w materiale dostawcy (O1); niezaleznego testu BRAK DANYCH.
- **Daty publikacji:** dla wiekszosci zrodel rzedu 4 data publikacji BRAK DANYCH (streszczenia jej nie podaja; stron nie odczytano).
- **Gdzie szukano:** WebSearch (tryb extended) 2026-11-28 — zapytania m.in.: "Gemini Omni 1.2 Flash vs Kling 4.0 comparison video quality", "Kling 4.0 vs Gemini Omni lip sync audio test", "Kling 4.0 polski jezyk mowa test lip sync", "Gemini Omni 1.2 Flash polski jezyk dialog test", "video arena leaderboard Elo Kling 4.0 Gemini Omni 1.2 Flash", "\"Kling 4.0\" leaderboard Artificial Analysis arena Elo score", "Kling 4.0 review artifacts motion physics face consistency", "Gemini Omni 1.2 Flash review artifacts physics character consistency upscaling", "Kling 4.0 Flash review quality 720p audio lip-sync test", "Gemini Omni 1.2 Flash audio sync problems extend dialogue drift", "Kling 4.0 audio issues unwanted music", "cellcog ... 11 tests", "dubbing polski AI wideo Kling lip sync ... Gemini Omni", "\"Kling 4.0 Flash\" po polsku mowa test", oraz zapytania zawezone do promptowy.com i cellcog.ai.
- **Hosty zablokowane w sesji (proba odczytu 2026-11-28):** WebFetch "ENOTFOUND": promptowy.com, clipia.ai, chatcut.io, creatify.ai, kling.ai i aistudio.google.com (dwa ostatnie odczytano jednak przez curl). curl "HTTP 403 (agent proxy)": arena.ai, artificialanalysis.ai, www.atlascloud.ai, discuss.ai.google.dev. curl bez odpowiedzi: deepmind.google. Pozostalych hostow niezaleznych (youtube.com, x.com, virse.ai, dxbuilder.io, youart.ai, cellcog.ai, mindstudio.ai, kie.ai, llm-stats.com, teamday.ai i in.) nie probowalem otwierac po serii blokad — ich tresc jest wylacznie z wyszukiwarki [P].

## 6. Zrodla

Kolumny: ID | URL | data (publikacji, jesli znana; odczytu) | rodzaj | wersja modelu | rzad | oznaczenie | odczyt.

### 6.1 Oficjalne (rzad 1)

| ID | URL | Data | Rodzaj | Wersja | Rzad | Oznaczenie | Odczyt |
|---|---|---|---|---|---|---|---|
| O1 | https://cloud.google.com/blog/products/ai-machine-learning/gemini-omni-1-2-flash-generally-available | publ. 2026-11-06; odczyt 2026-11-28 | oficjalne (ogloszenie GA) | Gemini Omni 1.2 Flash | 1 | deklaracje dostawcy; cytaty partnerow = opinia | bezposredni (WebFetch) |
| O2 | https://aistudio.google.com/docs/omni.md (cel przekierowania z https://ai.google.dev/gemini-api/docs/omni) | odczyt 2026-11-28 | oficjalne (dokumentacja Gemini API) | Omni; sekcje "Limitations", "Technical details", tabela rozdzielczosci | 1 | fakt dokumentacji | bezposredni (curl; WebFetch zwrocil ENOTFOUND) |
| O3 | https://kling.ai/document-api/api/usage-guide/kling-4-0.md | odczyt 2026-11-28 | oficjalne (przewodnik API "Kling 4.0 Video User Manual") | Kling 4.0 i 4.0 Flash (tabela 5.1) | 1 | fakt dokumentacji / deklaracja jakosci dostawcy | bezposredni (curl) |
| Z5 | docs/research/ZERO-RESEARCH-005-zestawienie-zbiorcze/zestawienie_zbiorcze.md (oraz zatwierdzone R001/R002 `veo.md`, `kling.md`: R002 Z13, Z17, Z18, Z20) | zatwierdzone 2026-11-27/28 | zatwierdzone badanie (zrodla rzedu 1 tam wskazane) | Omni 1.2 Flash, Kling 4.0, 4.0 Flash | 1 (przez zatwierdzone badanie) | jak w zrodle | odczyt pliku repozytorium |

### 6.2 Testy, rankingi, recenzje, opinie (rzad 4, wszystkie NIEPOTWIERDZONE, odczyt posredni przez WebSearch 2026-11-28)

| ID | URL | Data publikacji | Rodzaj | Wersja modelu w zrodle |
|---|---|---|---|---|
| N1 | https://deepmind.google/models/gemini-omni/ | BRAK DANYCH | dane dostawcy przez wyszukiwarke (porownanie 1.2 vs 1.1) | Omni 1.2 vs 1.1 |
| N2 | https://www.eesel.ai/blog/gemini-omni-1-2-flash | BRAK DANYCH | recenzja / omowienie | Omni 1.2 Flash |
| N3 | https://buildfastwithai.com/blogs/gemini-omni-flash-review-google-ai-video-model-2026 | BRAK DANYCH | recenzja | "Omni Flash" (wersja niejednoznaczna) |
| N4 | https://www.eesel.ai/blog/gemini-omni-flash-review | BRAK DANYCH | recenzja | "Omni Flash" (wersja niejednoznaczna) |
| N5 | https://invideo.io/blog/gemini-omni-flash-review/ | BRAK DANYCH | recenzja | Omni Flash (1.1) [STARSZA WERSJA] |
| N6 | https://arena.ai/leaderboard/video/text-to-video | migawka 2026-11-08 (wg streszczenia) | ranking | Omni 1.2 Flash; Kling 4.0 brak |
| N7 | https://infosdivers.com/en/lmarena/ | BRAK DANYCH (cytuje stan 2026-11-08) | omowienie rankingu | Omni 1.2 Flash |
| N8 | https://www.teamday.ai/blog/best-ai-video-models-2026 | BRAK DANYCH (migawka 2026-11-06) | omowienie rankingu | Omni 1.2 Flash |
| N9 | https://artificialanalysis.ai/video/leaderboard/text-to-video ; https://artificialanalysis.ai/video/leaderboard/image-to-video | BRAK DANYCH | ranking | Kling 4.0; "Gemini Omni Flash" (1.1) |
| N10 | https://promptowy.com/gemini-omni-1-2-vs-seedance-kling-veo-wan/ | BRAK DANYCH (test 2026-10-08 wg streszczenia) | test autorski | Omni 1.2, Omni 1.1, Kling 3.0 |
| N11 | https://youart.ai/blog/kling-4-0-vs-kling-3-0 ; https://youart.ai/blog/how-to-use-kling-4 | BRAK DANYCH | poradnik / recenzja | Kling 4.0 (vs 3.0) |
| N12 | https://dxbuilder.io/blog/kling-4-0-review-photorealism-comparison-171026 | BRAK DANYCH | recenzja | Kling 4.0 |
| N13 | https://www.jxp.com/kling/blog/kling-4-0-review ; https://miraflow.ai/blog/kling-4-0-explained-30-second-10-keyframe-video-model-2026 | BRAK DANYCH | recenzja | Kling 4.0 |
| N14 | https://www.virse.ai/blog/kling-4-0-review ; https://www.virse.ai/blog/kling-4-0-reddit-reviews | BRAK DANYCH | recenzja / zbior opinii | Kling 4.0 |
| N15 | https://moelueker.com/blog/kling-4-review | 2026-10-21 (wg streszczenia) | recenzja | Kling 4.0 |
| N16 | https://llm-stats.com/leaderboards/best-ai-for-video-creation | BRAK DANYCH | ranking | Kling v3 [STARSZA WERSJA] |
| N17 | https://kie.ai/blog/kling-4-0-vs-seedance-2-5 | BRAK DANYCH | recenzja posrednika | Kling 4.0 i 4.0 Flash |
| N18 | https://www.atlascloud.ai/blog/tips/kling-4-flash-vs-minimax-h3 | BRAK DANYCH | test posrednika | Kling 4.0 Flash |
| N19 | https://www.atlascloud.ai/blog/tips/kling-4.0-flash-short-video-problems-fixes | BRAK DANYCH | poradnik posrednika | Kling 4.0 Flash |
| N20 | https://cellcog.ai/blog/gemini-omni-1-2-flash-vs-seedance-2-5/ | ok. 3 tygodnie przed 2026-11-28 (wg streszczenia) | test (11 prob, 1 ujecie) | Omni 1.2 Flash, Kling 4.0, Seedance 2.5 |
| N21 | https://clipia.ai/en/blog/magi-2-review-video-model-test | BRAK DANYCH | test (4 prompty) | Omni 1.2, Kling 4.0, Seedance 2.5, MAGI-2 |
| N22 | https://x.com/muku_sns/status/2126234635038286165 | BRAK DANYCH | opinia uzytkownika | "Gemini Omni" (bez numeru), Kling 4.0 |
| N23 | https://www.youtube.com/watch?v=CVBOhyiUt04 | BRAK DANYCH | opinia (wideo) | Omni 1.2 Flash, Kling 4.0, Seedance 2.5 / 2.5 Flash |
| N24 | https://creatify.ai/blog/gemini-omni-flash-vs-kling-4-0 | BRAK DANYCH | zestawienie specyfikacji | "Omni Flash" (niejednoznaczne), Kling 4.0 |
| N25 | https://www.comparegen.ai/compare/kling-vs-gemini-omni-flash | BRAK DANYCH | ocena serwisu (podstawa nieopisana) | "Kling AI", "Gemini Omni Flash" (niejednoznaczne) |
| N26 | https://tech-insider.org/ca/gemini-omni-1-2-flash-vs-kling-vs-runway-2026/ | BRAK DANYCH | zestawienie | Omni 1.2 Flash, Kling (wersja niejednoznaczna) |
| N27 | https://www.youtube.com/watch?v=uMfZfEEIZm4 | BRAK DANYCH | wideo (tresc nieodczytana) | Omni Flash 1.1 [STARSZA WERSJA], Kling 4.0 |
| N28 | https://promptsrush.com/blog/gemini-omni-vs-seedance-2-vs-kling-3-vs-wan-2-7 | BRAK DANYCH | test | Kling 3.0 [STARSZA WERSJA] |
| N29 | https://www.datacamp.com/blog/gemini-omni-1-2-flash | BRAK DANYCH | omowienie / test | Omni 1.2 Flash |
| N30 | https://www.recraft.ai/blog/gemini-omni-flash-1-2-in-recraft-studio | BRAK DANYCH | blog posrednika | Omni 1.2 Flash |
| N31 | https://discuss.ai.google.dev/t/gemini-omni-1-2-flash-generates-repeated-and-duplicated-words-in-video-voiceovers/204773 | BRAK DANYCH | opinia uzytkownika (forum) | Omni 1.2 Flash |
| N32 | https://www.atlascloud.ai/blog/tips/gemini-omni-1.2-flash-multi-speaker-dialogue | BRAK DANYCH | poradnik / test posrednika | Omni 1.2 Flash |
| N33 | https://happycapy.ai/blog/gemini-omni-flash | BRAK DANYCH | blog | Omni Flash (1.1) [STARSZA WERSJA] |
| N34 | https://chatcut.io/blog/kling-4-0-review | BRAK DANYCH | recenzja (8 testow) | Kling 4.0, 4.0 Flash |
| N35 | https://www.mindstudio.ai/blog/kling-4-0-first-look | BRAK DANYCH | recenzja (early access, odczyt posredni) | Kling 4.0 Flash (build wczesnego dostepu, 720p) |
| N36 | https://www.seaart.ai/blog/kling-4-0-review | BRAK DANYCH | recenzja | Kling 4.0 |
| N37 | https://maxvideoai.com/ai-video-engines/kling-v4-vs-kling-v4-flash | BRAK DANYCH | zestawienie | Kling 4.0 vs 4.0 Flash |
| N38 | https://gemini-omni.dev/blogs/kling-4-vs-gemini-omni | BRAK DANYCH | blog o charakterze promocyjnym | Kling 4.0, "Gemini Omni" |
| N39 | https://promptowy.com/gemini-omni-1-2-po-polsku/ | BRAK DANYCH | test autorski (polski) | Omni 1.2 |
| N40 | https://promptowy.com/gemini-omni-1-2-flash-test/ | BRAK DANYCH | test autorski (9 scen) | Omni 1.2 Flash |
| N41 | https://promptowy.com/ai-do-tworzenia-filmow/ | BRAK DANYCH | test autorski (10 modeli) | Omni 1.1, Kling 4.0 i in. |
| N42 | https://promptowy.com/kling-4-0-po-polsku/ | BRAK DANYCH (test 2026-10-21) | test autorski (polski, Whisper) | Kling 4.0 (porownanie z 3.0) |
| N43 | https://promptowy.com/kling-4-0-test/ | BRAK DANYCH | test autorski (5 scen) | Kling 4.0 |
| N44 | https://promptowy.com/kling-4-0-teledysk-disco-polo/ | BRAK DANYCH | test autorski (tresc nieodczytana) | Kling 4.0 |
| N45 | https://promptowy.com/kling-po-polsku/ | BRAK DANYCH (test 2026-09-28) | test autorski | Kling 3.0 [STARSZA WERSJA] |
| N46 | https://elevenlabs.io/lip-sync/dubbing-ai | BRAK DANYCH | strona narzedzia zewnetrznego | nie dotyczy |
| N47 | https://sync.so/blog/introducing-ai-dubbing-in-sync | BRAK DANYCH | blog narzedzia zewnetrznego | nie dotyczy |
| N48 | https://promptowy.com/dubbing-ai/ | BRAK DANYCH | poradnik | nie dotyczy |
| N49 | https://www.oscarrak.pl/blog/elevenlabs | BRAK DANYCH | poradnik | nie dotyczy |

### 6.3 Bezpieczenstwo i zakres pracy

- Zadnego wideo nie wygenerowano; nie zalozono kont ani kluczy; nie wywolano API generowania; nic nie zainstalowano; brak sekretow w pliku.
- Odczyty bezposrednie: publiczne strony bez logowania (O1, O2, O3), pobrane do scratchpadu sesji.
- Zmieniony plik: tylko `docs/research/ZERO-RESEARCH-008-omni-vs-kling-jakosc/omni_vs_kling.md`.
