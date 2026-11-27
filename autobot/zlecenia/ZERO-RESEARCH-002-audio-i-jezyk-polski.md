# ZERO-RESEARCH-002-audio-i-jezyk-polski

WYZWALACZ:  decyzja wlasciciela ECHO-008 (2026-11-27): system wideo ma generowac obraz i dzwiek, jezyk polski jest wazny (inaczej angielski), rownoczesna sciezka audio jest plusem. RESEARCH-001 zamkniety (lista modeli i ceny w repozytorium); slot wolny.
GOAL:       Istnieje zweryfikowane zestawienie, ktore generatory wideo AI (Kling, Seedance, Google Veo, Sora 2, MiniMax przez API) tworza dzwiek razem z obrazem, jak obsluguja jezyk polski (mowa, synchronizacja ust) i czy sciezka audio powstaje jednoczesnie z wideo w jednym przebiegu, z oznaczeniem pewnosci zrodel i punktowym rankingiem zgodnosci z wymaganiami ZERO.
KONIEC:     PRAWDA gdy scenariusze S-R8..S-R12 przechodza. Zadna zmiana poza allowlista.

STRUKTURA: pieciu dostawcow = pieciu wezlow (kazdy przechodzi Operator -> Evaluator -> Obrona -> Final Control, bez wlasnej integracji), potem synteza `zestawienie_audio.md` (Operator -> Evaluator -> Obrona -> Final Control -> Integration, ktory zatwierdza WSZYSTKIE szesc plikow).

ZADANIE (kazdy wezel: jeden dostawca): dla kazdego istotnego modelu dostawcy — liste wezla bierz z `docs/research/ZERO-RESEARCH-001-porownanie-generatorow-wideo/zestawienie.md` (tylko odczyt) oraz z nowszych modeli dostepnych przez API na 2026-11-27 — ustal i opisz w pliku wezla (`docs/research/ZERO-RESEARCH-002-audio-i-jezyk-polski/<dostawca>.md`) pola z S-R8:
1. audio natywne (tak / nie / BRAK DANYCH) i jego zakres: mowa/dialog, efekty, ambient, muzyka;
2. czy audio i wideo powstaja w jednym przebiegu (jednoczesnie) czy osobno (np. post-dubbing, osobne wywolanie);
3. jezyki mowy; status polskiego: OFICJALNIE (zrodlo rzedu 1 wymienia polski) / W PRAKTYCE (niezalezny test lub opinia, rzad 4, NIEPOTWIERDZONE) / BRAK DANYCH / NIE;
4. synchronizacja ust (lip-sync) i liczba mowcow w jednym klipie;
5. mozliwosc wylaczenia muzyki (parametr, prompt, brak mozliwosci);
6. wlasne audio lub glos jako wejscie (audio-to-video, referencja glosu);
7. eksport sciezki audio osobno;
8. zachowanie audio w trybach z klatka startowa (image-to-video) i przy przedluzaniu klipu;
9. roznica ceny z audio i bez (zgodnie z RESEARCH-001 — przepisz, nie licz od nowa, a niezgodnosc zglos);
10. zrodla rzedu 1 (URL, data odczytu) i pewnosc.
SYNTEZA: `zestawienie_audio.md`: tabela wszystkich modeli (kolumny jak wyzej), ranking punktowy zgodnosci z wymaganiami ZERO wg JAWNEJ punktacji zapisanej w pliku: audio natywne 2 pkt; jednoczesnosc audio i wideo 2; polski OFICJALNIE 3 (W PRAKTYCE 1); lip-sync 2; wielu mowcow w klipie 1; wylaczenie muzyki 1; audio/glos jako wejscie 1; eksport sciezki audio 1 (max 13); kolejnosc z punktow (remisy: tanszy koszt 1 minuty z RESEARCH-001); lista zrodel per pozycja; uwagi o niepewnosci; krotka sekcja OPINIA (oznaczona jako opinia, maks. 8 linii) tylko z tego, co wynika z danych.

REGULA PRZECIW SAMOOSZUKIWANIU (z faktycznych bledow tego projektu):
- Zakaz podawania mozliwosci modeli (jezykow, lip-syncu, parametrow) z pamieci; stan wiedzy bywa nieaktualny. Wszystko ustalasz wyszukiwaniem i odczytem oficjalnych stron na 2026-11-27.
- Zakaz uznania jezyka polskiego za wspierany bez zrodla rzedu 1; brak wzmianki to BRAK DANYCH, a nie NIE; opinie i testy niezalezne to rzad 4 i maja status W PRAKTYCE, NIEPOTWIERDZONE.
- Zakaz mieszania "audio natywne" z "narzedzie do dubbingu/TTS dostawcy" — to oddzielne pola.
- Zakaz kopiowania cen z pamieci; ceny tylko z RESEARCH-001, z nota o niezgodnosci, jesli ja widzisz.
- Hosty niektorych dostawcow sa w tej sesji zablokowane; wtedy uzyj wyszukiwarki z ograniczeniem do oficjalnych domen i oznacz "odczyt posredni".
- Zakaz edycji plikow poza allowlista.

PROCEDURA NAPRAWCZA PRZY FAIL: Evaluator numeruje zarzuty (plik, miejsce, punkt listy, reprodukcja). Operator (w obronie) odpowiada na kazdy numer PRZYJMUJE/ODRZUCAM z dowodem; po werdykcie NAPRAW poprawia tylko wskazane pola.

ALLOWLISTA (katalog `docs/research/ZERO-RESEARCH-002-audio-i-jezyk-polski/`):
  - `kling.md`, `seedance.md`, `veo.md`, `sora2.md`, `minimax.md` (po jednym na wezel)
  - `zestawienie_audio.md` (synteza)
ZAKAZANE BEZWZGLEDNIE: `scenariusze/`, `autobot/`, `docs/analiza/`, `docs/audiobook/`, `docs/proces/`, `docs/przeglad-2026-11-27/`, `docs/rozbieznosci/`, `docs/research/ZERO-RESEARCH-001-*` i `-003-*` (tylko odczyt), polecenia git zmieniajace stan (poza rola Integration), sekrety (w tym klucze API), zakladanie kont, instalowanie serwerow, wywolania API (w tym platne).

MIEJSCE PRACY: `docs/research/ZERO-RESEARCH-002-audio-i-jezyk-polski/`
BAZA:          HEAD galezi roboczej
OBIEG:         Operator -> Evaluator (10 punktow) -> Obrona przy zarzutach -> Final Control (per zarzut) -> Integration (po syntezie)

RUNDA: w toku (rundy 1-3 z 3 na wezel; licznik w rejestrze aktualizuje orkiestrator po zakonczeniu workflow)
