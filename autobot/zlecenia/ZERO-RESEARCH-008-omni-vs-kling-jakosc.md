# ZERO-RESEARCH-008-omni-vs-kling-jakosc

WYZWALACZ:  polecenie wlasciciela ECHO-034 (2026-11-28): znalezc porownania samego Gemini Omni z Kling pod katem jakosci wideo, synchronizacji z dzwiekiem oraz lektorow/glosow (w tym polskiego); tylko to teraz rozwazamy.
GOAL:       Istnieje zweryfikowane zestawienie dostepnych porownan, testow i opinii o Gemini Omni 1.2 Flash i Kling 4.0 (z 4.0 Flash) w trzech obszarach: jakosc obrazu wideo, synchronizacja dzwieku z obrazem oraz glosy i jezyk polski; z oznaczeniem rodzaju i pewnosci zrodel (zrodla niezalezne to rzad 4, NIEPOTWIERDZONE), bez rankingu i rekomendacji, tak aby wlasciciel mogl sam wybrac.
KONIEC:     PRAWDA gdy scenariusze S-R32..S-R36 przechodza. Zadna zmiana poza allowlista.

ZADANIE: utworz plik `docs/research/ZERO-RESEARCH-008-omni-vs-kling-jakosc/omni_vs_kling.md` (po polsku; nazwy techniczne bez znakow diakrytycznych). Struktura:
 1. Naglowek: data 2026-11-28, zakres (Gemini Omni 1.2 Flash vs Kling 4.0 / 4.0 Flash), legenda rzedow zrodel i oznaczen (NIEPOTWIERDZONE, odczyt posredni, BRAK DANYCH), zasada neutralnosci (ECHO-027).
 2. Obszar A — jakosc obrazu wideo: dla kazdego systemu osobno oraz porownania bezposrednie (ten sam prompt/obraz w obu): realizm, ruch i fizyka, spojnosc postaci i twarzy, artefakty, rozdzielczosc natywna a upscaling (wiadomo z zatwierdzonych badan: Omni 1.2 baza 360p/720p i skalowanie do 1080p/4K; Kling 4.0 do 4K natywnie wg dokumentacji — traktuj jako fakty rzedu 1 z `docs/research/ZERO-RESEARCH-005-zestawienie-zbiorcze/zestawienie_zbiorcze.md`), ewentualne wyniki rankingow (np. aren wideo, Elo) jako cytaty z data i wersja.
 3. Obszar B — synchronizacja dzwieku z obrazem: lip-sync, trafnosc efektow i ambientu, rozjazdy, liczba mowcow, zachowanie przy przedluzaniu (Omni: extend +3-10 s do 30 s; Kling 4.0: 3-30 s).
 4. Obszar C — glosy i jezyk polski: jakosc i naturalnosc mowy, akcent, mozliwosc wyboru lub sklonowania glosu, jezyki wspierane oficjalnie (z zatwierdzonych badan: Kling 4.0 — 9 jezykow bez polskiego; Omni — EN w pelni, inne "not evaluated"; polski u obu BRAK DANYCH w oficjalnych zrodlach), relacje uzytkownikow o mowie po polsku, obejscia (zewnetrzny polski TTS, dubbing, lip-sync obcy) — z oznaczeniem zrodel.
 5. Sprzecznosci miedzy zrodlami (zapisane obok siebie, bez rozstrzygania) i Luki (czego nie znaleziono, gdzie szukano, ktore hosty byly zablokowane).
 6. Zrodla: lista z URL, data, rodzaj (oficjalne/test/ranking/recenzja/opinia), wersja modelu, rzad, oznaczenie i status odczytu (bezposredni/posredni).
 Zadnych punktow, rankingu wlasnego, sekcji OPINIA, wniosku o wyborze i slow "najlepszy", "polecam".

REGULA PRZECIW SAMOOSZUKIWANIU:
 - Zakaz twierdzen z pamieci; kazde twierdzenie z URL i data. Wyszukuj WebSearch (tryb "extended" dla niszowych faktow: porownania, testy, recenzje, rankingi, relacje uzytkownikow, wpisy o polskim) i czytaj WebFetch tam, gdzie host jest dopuszczony; wiele stron niezaleznych (reddit, youtube, rankingi, serwisy technologiczne) jest w sesji zablokowanych — wtedy wynik wyszukiwarki to odczyt posredni, oznacz go i nie zmyslaj tresci strony.
 - Zakaz uznawania opinii, testow i rankingow za fakt: rzad 4 = NIEPOTWIERDZONE; zakaz wnioskowania "ktory jest lepszy" w imieniu wlasciciela.
 - Zakaz mieszania wersji: podawaj wersje modelu w kazdym zrodle; wpisy o starszych wersjach oznacz i trzymaj osobno.
 - Zakaz zmyslania relacji o polskim: jesli brak zrodel, wpisz BRAK DANYCH i opisz, gdzie szukano.
 - Zakaz generowania wideo, zakladania kont i kluczy, instalacji i wywolan API; zakaz zapisu sekretow.
 - Zakaz edycji plikow poza allowlista; pliki pomocnicze tylko w scratchpadzie sesji.
 - Pisz plik etapami (kilka dopisan).

PROCEDURA NAPRAWCZA PRZY FAIL: Evaluator numeruje zarzuty (miejsce, punkt listy, reprodukcja). Operator (w obronie) odpowiada PRZYJMUJE/ODRZUCAM z dowodem; po werdykcie NAPRAW poprawia tylko wskazane miejsca.

ALLOWLISTA:
  - `docs/research/ZERO-RESEARCH-008-omni-vs-kling-jakosc/omni_vs_kling.md` (nowy plik)
ZAKAZANE BEZWZGLEDNIE: `scenariusze/`, `autobot/`, `docs/analiza/`, `docs/audiobook/`, `docs/proces/`, `docs/przeglad-2026-11-27/`, `docs/rozbieznosci/`, `docs/research/ZERO-RESEARCH-001-*` do `-007-*` (tylko odczyt), polecenia git zmieniajace stan (poza rola Integration), sekrety, zakladanie kont i kluczy, wywolania API, generowanie wideo.

MIEJSCE PRACY: `docs/research/ZERO-RESEARCH-008-omni-vs-kling-jakosc/`
BAZA:          HEAD galezi roboczej
OBIEG:         Operator -> Evaluator (10 punktow) -> Obrona przy zarzutach -> Final Control (per zarzut) -> Integration

RUNDA: w toku (rundy 1-3 z 3; licznik w rejestrze aktualizuje orkiestrator po zakonczeniu workflow)
