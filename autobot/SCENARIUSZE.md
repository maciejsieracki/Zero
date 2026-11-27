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
