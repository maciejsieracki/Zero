# ZERO — rejestr scenariuszy sprawdzenia

Zrodlo kryteriow konca. Sprawdza Evaluator **recznie i od zera, wlasnym narzedziem**; nie opiera sie na raporcie Operatora ani nie odpala jego skryptow.

## Temat ZERO-BAZA-001-import-scenariuszy

- **S-I1** Trzy pliki scenariuszy (`ZERO_mini_serial_E01_ADAM_rev.md`, `ZERO_mini_serial_E02_EWA_rev.md`, `ZERO_mini_serial_E03_ARES_rev.md`) istnieja w `scenariusze/`, a ich SHA-256 jest rowny SHA-256 oryginalow wyliczonemu niezaleznie z archiwum zrodlowego (swieza ekstrakcja w nowym pustym katalogu).
- **S-I2** W `scenariusze/` nie ma innych plikow niz te trzy i `MANIFEST.sha256`; zadne inne pliki repozytorium (poza `scenariusze/`) nie zostaly zmienione przez temat.
- **S-I3** `MANIFEST.sha256` jest zgodny z plikami (`sha256sum -c` przechodzi).

## Tematy ZERO-ANALIZA-001-e01-... i ZERO-ANALIZA-002-e02-...

- **S-A1 (cytaty)** Dla kazdego punktu raportu o wadze KRYTYCZNA lub WYSOKA oraz dla losowej proby co najmniej 20 pozostalych punktow (lub wszystkich, jesli mniej) cytat wystepuje doslownie w `scenariusze/` pod podanym numerem linii (tolerancja +-2). Jeden niezgodny cytat sposrod KRYTYCZNYCH/WYSOKICH = FALSZ.
- **S-A2 (timing)** Czasy scen i sumy przeliczone od zera z etykiet CZAS i tabeli czasow w scenariuszu sa zgodne z wartosciami w raporcie; kazda rozbieznosc miedzy naglowkiem, tabela, suma naglowkow scen i suma policzona jest wypisana; raport zawiera analize rytmu (udzial blokow, dlugie odcinki statyczne, przyspieszenia i zwolnienia).
- **S-A3 (napiecie)** Krzywa napiecia obejmuje 100% scen i blokow odcinka (lista numerow scen z pliku scenariusza = lista w raporcie); kazda ocena ma uzasadnienie wskazujace konkretne zdarzenie z tekstu (cytat i linia); wskazane sa miejsca spadku napiecia, zbyt wczesnego ujawnienia informacji (wiedza widza vs wiedza postaci) i kandydaci na cliffhangery.
- **S-A4 (weryfikacja ustalen)** Kazde ustalenie z materialow wejsciowych dotyczace tego odcinka (ID punktow z `docs/rozbieznosci/<E>_audyt.md`, punkty A/B/C/D handoffu, notatki `docs/przeglad-2026-11-27/`) ma status POTWIERDZONE / OBALONE / ZAWEZONE / NIEZBADANE z cytatem; NIEZBADANE niedopuszczalne dla KRYTYCZNYCH i WYSOKICH.
- **S-A5 (brak zmian)** Zadna zmiana poza allowlista zlecenia; pliki w `scenariusze/` nie zmienione (hash przed i po).
- **S-A6 (propozycje)** Kazdy wariant naprawy i kazde nowe brzmienie kwestii jest oznaczone PROPOZYCJA i wystepuje tylko w raporcie (ECHO-003, G2, G3).
- **S-A7 (kompletnosc)** Raport zawiera sekcje: logika, timing, napiecie, kolejnosc rekomendowanych poprawek i liste decyzji kanonicznych wymaganych od wlasciciela, oraz tabele scen (`tabela_scen.md`).
- **S-A8 (raport terminalny)** Raport terminalny Operatora do 400 slow, w formacie kontraktu, bez surowych danych.
- **S-A9 (zrodla)** Fakty naukowe, techniczne i branzowe nieweryfikowalne w tekscie scenariusza sa oznaczone NIEPOTWIERDZONE (zadnych twierdzen z pamieci jako faktow).

## Temat ZERO-RESEARCH-001-porownanie-generatorow-wideo (wezly -a Kling, -b Seedance, -c Veo, -d Sora 2, -e MiniMax API)

- **S-R1 (kompletnosc danych)** Dla kazdego uwzglednionego modelu sa: maks. dlugosc jednego klipu (s), maks. rozdzielczosc, informacja czy 1080p jest dostepne, cena za sekunde przy 1080p (lub przy najwyzszej dostepnej, z oznaczeniem) w rozliczeniu pay-as-you-go / API / kredytow, koszt 1 minuty, data cennika i co najmniej jeden URL zrodla rzedu 1 (oficjalny cennik lub dokumentacja).
- **S-R2 (potwierdzenie zrodel)** Evaluator niezaleznie pobiera cytowane zrodla (lub szuka niezaleznie) i potwierdza kazda liczbe (dlugosc, rozdzielczosc, cena). Rozbieznosc powyzej 5% albo brak potwierdzenia = FALSZ.
- **S-R3 (arytmetyka)** Koszt 1 min = cena za sekunde x 60 (lub kredyty za sekunde x cena kredytu x 60) przeliczony od zera przez Evaluatora; zgodnosc do 1 centa.
- **S-R4 (sortowanie)** Zestawienie jest posortowane rosnaco po koszcie 1 minuty przy 1080p; modele bez 1080p lub bez ceny sa na koncu i jawnie oznaczone; Evaluator sprawdza kolejnosc.
- **S-R5 (zrodla i abonamenty)** Kazdy fakt z zrodla rzedu 4-5 jest oznaczony NIEPOTWIERDZONE (pewnosc niska); zadna liczba docelowa nie opiera sie na abonamencie miesiecznym; brak twierdzen z pamieci.
- **S-R6 (zakres)** Uwzglednione sa: Kling, Seedance, Google Veo, Sora 2, MiniMax (API). Jesli ktorys nie jest dostepny przez API/kredyty, jest to jawnie opisane z zrodlem.
- **S-R7 (brak zmian)** Zadne zmiany poza allowlista zlecenia.

## Temat ZERO-RESEARCH-002-audio-i-jezyk-polski (wezly -a Kling, -b Seedance, -c Veo, -d Sora 2, -e MiniMax API)

- **S-R8 (kompletnosc pol audio)** Dla kazdego modelu z RESEARCH-001 sa: czy generuje dzwiek natywnie; zakres (mowa/dialog, efekty, ambient, muzyka); czy audio i wideo powstaja w jednym przebiegu (jednoczesnie) czy osobno; jezyki mowy, w tym status polskiego (OFICJALNIE / W PRAKTYCE / BRAK DANYCH / NIE); synchronizacja ust i liczba mowcow w klipie; mozliwosc wylaczenia muzyki; mozliwosc podania wlasnego audio lub glosu; mozliwosc wyeksportowania sciezki audio osobno; zachowanie audio w trybach start image / przedluzanie; roznica ceny z audio i bez; co najmniej jeden URL zrodla rzedu 1.
- **S-R9 (potwierdzenie)** Evaluator niezaleznie potwierdza kazde twierdzenie tak/nie o audio i jezyku w dokumentacji lub oficjalnym ogloszeniu dostawcy; status polskiego "OFICJALNIE" wymaga zrodla rzedu 1; testy niezalezne i opinie to rzad 4 i maja status W PRAKTYCE oraz NIEPOTWIERDZONE.
- **S-R10 (spojnosc z RESEARCH-001)** Lista modeli, ceny z audio i bez audio oraz data cennika sa zgodne z zestawieniem z ZERO-RESEARCH-001; nowsze modele zglaszane jako zarzut.
- **S-R11 (ranking jawny)** Zestawienie zawiera ranking zgodnosci z wymaganiami ZERO (ECHO-008) wyliczony wg jawnej, opisanej w pliku punktacji (kryteria: audio natywne, jednoczesnosc, polski, lip-sync, wielu mowcow, wylaczenie muzyki, audio-wejscie); Evaluator przelicza punkty od zera; kolejnosc wynika z punktacji, nie z opinii.
- **S-R12 (zrodla i zakres)** Brak twierdzen z pamieci; zrodla rzedu 4-5 oznaczone NIEPOTWIERDZONE; uwzglednieni wszyscy dostawcy z RESEARCH-001; zadne zmiany poza allowlista.

## Temat ZERO-RESEARCH-003-api-i-mcp-sterowanie (wezly -a Kling, -b Seedance, -c Veo, -d Sora 2, -e MiniMax API)

- **S-R13 (kompletnosc)** Dla kazdego dostawcy sa: czy istnieje publiczne API (REST) dostepne dla zwyklego konta i jak sie je uzyskuje (klucz, onboarding, ograniczenia regionalne, weryfikacja); model pracy (zadanie asynchroniczne: id, status, pobranie wyniku, webhook); limity (zapytania, zadania rownolegle); zakres API wzgledem aplikacji (tekst do wideo, obraz do wideo z klatka startowa/koncowa, przedluzanie, obrazy referencyjne postaci, parametry audio, rozdzielczosc, dlugosc); oficjalne SDK lub CLI; serwer MCP oficjalny i spolecznosciowy (nazwa, repozytorium, licencja, aktywnosc); alternatywne drogi dostepu do tego samego modelu (platformy posredniczace); co najmniej jedno zrodlo rzedu 1 (dokumentacja API, oficjalne repozytorium).
- **S-R14 (potwierdzenie)** Evaluator niezaleznie potwierdza kazde twierdzenie tak/nie (API istnieje, SDK istnieje, MCP istnieje) w dokumentacji lub w repozytorium/rejestrze; serwery MCP spolecznosciowe to rzad 4 i wymagaja daty ostatniej aktywnosci oraz licencji; nieistniejace lub niedostepne zasoby = FALSZ.
- **S-R15 (sterowalnosc z Claude Code)** Dla kazdego dostawcy opisana jest minimalna sciezka sterowania z Claude Code (MCP, wywolania HTTP/SDK przez narzedzie powloki albo brak) z wymienieniem wymaganych endpointow lub narzedzi, wynikajaca ze zrodel; w ramach badania NIE wykonano zadnego wywolania API, nie zalozono kont i kluczy, nie zainstalowano serwerow MCP.
- **S-R16 (ocena jawna)** Zestawienie zawiera punktacje gotowosci do sterowania z Claude Code wg opisanych w pliku kryteriow (API publiczne, obraz do wideo, obrazy referencyjne, asynchronicznosc i webhook, oficjalne SDK, oficjalny MCP, MCP spolecznosciowy, brak barier onboardingu); Evaluator przelicza punkty od zera.
- **S-R17 (zrodla, zakres, bezpieczenstwo)** Brak twierdzen z pamieci; rzad 4-5 oznaczony NIEPOTWIERDZONE; uwzglednieni wszyscy dostawcy; zadne klucze/sekrety w zapisach; zadne zmiany poza allowlista.
