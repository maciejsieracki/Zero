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

## Temat ZERO-PROCES-002-inwentarz-zasad-autobot

- **S-P1 (kompletnosc)** Kazdy plik z archiwum Autobot.rar (62 wpisy wg listy, w tym zawartosc autobot-skills.zip), z paczki v2 z 2026-09-16 i z wersji z listy umiejetnosci sesji jest sklasyfikowany albo jawnie pominiety z powodem (np. __pycache__, dane uruchomien).
- **S-P2 (obrona: tak/nie z dowodem)** Dla kazdego zestawu zasad twierdzenie "definiuje obrone" i "definiuje osobna rola Integration" jest poparte dosłownym cytatem z numerem linii albo potwierdzonym brakiem (grep -n -i z pustym wynikiem); Evaluator weryfikuje grepem niezaleznie.
- **S-P3 (najnowszy zestaw)** Najnowszy zestaw z obrona wskazany na podstawie dat (mtime i data/wersja w tresci) oraz tresci (odwolania do poprzednich wersji); Evaluator potwierdza daty i odwolania.
- **S-P4 (roznice vs v2)** Lista roznic funkcjonalnych wzgledem v2 (role, przejscia, checklista Evaluatora, receipts, integracja, orkiestrator) z cytatami i z lista konkretnych regul do przeniesienia do procesu ZERO.
- **S-P5 (rekomendacje)** Dla kazdego zestawu/pliku: USUNAC / ZACHOWAC / NIE DOTYCZY z uzasadnieniem; rekomendacja USUNAC tylko dla plikow przeczytanych w calosci; archiwum i oryginaly niezmienione (hash przed i po).
- **S-P6 (bezpieczenstwo)** Zadne skrypty z archiwum nie zostaly uruchomione (.sh, .py, testy, demo), brak sekretow w raporcie, brak zmian poza allowlista.

## Temat ZERO-PROCES-003-komenda-usuwania-plikow

- **S-P7 (lista i hashe)** Lista plikow do usuniecia i ich pelne SHA-256 w skrypcie sa identyczne z lista kasacji (inwentarz, sekcja 7) i hashami z sekcji 8.5; Evaluator sam wyodrebnia te pliki z archiwum Autobot.rar do NOWEGO pustego katalogu i porownuje SHA-256 z hashami wpisanymi w skrypcie.
- **S-P8 (bezpieczenstwo)** Skrypt domyslnie pracuje w trybie podgladu (nic nie usuwa); usuwa tylko pliki o nazwie i hashu zgodnych z lista; usuwa do Kosza (przywracalnie), pojedynczo, przez -LiteralPath, bez -Recurse, bez wildcardow i bez usuwania katalogow; pomija i raportuje pliki o zgodnej nazwie, ale innym hashu; nie dotyka folderu autobot-skills, pakietu autobot (Python), paczki v2 ani niczego spoza listy; plik zip usuwa tylko gdy obok istnieje folder autobot-skills.
- **S-P9 (skladnia i zgodnosc)** Skladnia PowerShell sprawdzona parserem (jesli pwsh dostepny w kontenerze) albo jawnie oznaczona NIE URUCHOMIONO z lista ryzyk i przegladem linia po linii; zgodnosc z PowerShell 5.1 i 7; poprawna obsluga sciezki ze spacjami i znakiem "_" (-LiteralPath, cudzyslowy); domyslna sciezka dokladnie `C:\Users\Maciej Sieracki\OneDrive - NASTER S.A\_NOWA_STRUKTURA\Caude`.
- **S-P10 (uzycie)** README w 5 krokach (wklej, sprawdz tabele podgladu, zmien flage, uruchom, sprawdz Kosz) oraz blok kodu gotowy do wklejenia w czacie; zadne skrypty nie zostaly uruchomione w kontenerze, brak sekretow, brak zmian poza allowlista.

## Temat ZERO-AUDIO-001-e01-audiobook

- **S-U1 (kompletnosc)** Tekst audiobooka obejmuje KAZDY segment scenariusza E01 w kolejnosci pliku (sceny numerowane, montaz Zero Day, bloki przeszlosci P1-P4, wstawki medialne): Evaluator sam wypisuje liste segmentow z pliku scenariusza i dopasowuje do naglowkow w audiobooku; brak segmentu = FALSZ.
- **S-U2 (dialogi dosłownie)** Kazda kwestia dialogowa scenariusza wystepuje w audiobooku w tej samej kolejnosci i z tymi samymi slowami (po normalizacji: wielkosc liter, interpunkcja, myslniki); liczba kwestii zgodna; w kwestiach nie dodano ani nie usunieto slow; dopuszczalne sa tylko dopiski o mowcy poza kwestia. Evaluator sprawdza wlasnym skryptem (python3 -I) 100% kwestii oraz recznie co najmniej 30 losowych.
- **S-U3 (brak nowych faktow)** Kazdy dodany opis jest wyprowadzony z tekstu scenariusza (didaskalia, naglowek sceny, kontekst) albo jest ogolnym szczegolem zmyslowym (swiatlo, dzwiek, pogoda, ruch) niewprowadzajacym faktow fabularnych (nazw, dat, liczb, wieku, motywow, relacji, wydarzen). Evaluator sprawdza probe co najmniej 25 dodatkow wedlug pliku sladu (dodatek -> linia zrodlowa); fakt nieobecny w scenariuszu = FALSZ.
- **S-U4 (czytelnosc dla lektora)** W tekscie czytanym brak timecodow, etykiet CZAS, oznaczen UJECIE, nawiasow scenicznych, skrotow i symboli; liczby, godziny i skroty oddane slowami; sredni dlugosc zdania narracji nie wiecej niz 22 slowa (policzone); kazda kwestia ma czytelnego mowce (dopisek lub oczywista zmiana mowcy); teksty ekranowe (paski, napisy, plansze) zamienione na narracje; trudne nazwy i terminy w notatce dla lektora z zapisem wymowy.
- **S-U5 (PDF i znaki)** Plik PDF powstal z tego samego tekstu; polskie znaki poprawne (pdftotext bez znakow zastepczych), czcionka osadzona, koniec oznaczony "Koniec odcinka"; liczba slow i szacowany czas czytania (150 slow/min) per segment i lacznie w notatce dla lektora.
- **S-U6 (granice)** `scenariusze/` niezmienione (sha256sum -c); sprzecznosci kanoniczne (np. wiedza widza o Adze, os milczenia Ares IV) odtworzone bez rozstrzygania i wypisane w notatce dla lektora jako "do decyzji autora"; brak sekretow; brak zmian poza allowlista.
- **S-U7 (raport)** Raport terminalny Operatora do 400 slow; plik sladu dodatkow zawiera co najmniej jeden wpis na kazdy segment.
