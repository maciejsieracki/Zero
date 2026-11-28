**ANULOWANY (ECHO-037, 2026-11-28): bledne narzedzie docelowe — wlasciciel mial na mysli Kling. Brak wytworu; zastapiony tematem ZERO-PROD-002-scena1-kling.**

# ZERO-PROD-001-scena1-seedance

WYZWALACZ:  decyzja wlasciciela ECHO-036 (2026-11-28): plik wsadowy dla Seedance dla pierwszej sceny E01, z osia czasu co do milisekundy (kwestie, dzwieki tla, zdarzenia obrazu) i z propozycja, co jeszcze dolozyc.
GOAL:       Istnieje zweryfikowany plik produkcyjny Sceny 1 E01 dla Seedance 2.5: parametry techniczne, stale zasady, lista referencji, os czasu w milisekundach (z numerami klatek przy 24 fps) dla kwestii, dzwiekow tla i zdarzen obrazu, prompty ujec po angielsku, procedura weryfikacji i montazu oraz sekcja "Co jeszcze dolozyc" — zgodny ze scenariuszem E01 i zatwierdzonymi badaniami, z uczciwie opisanymi granicami precyzji modelu.
KONIEC:     PRAWDA gdy scenariusze S-W1..S-W6 przechodza. Zadna zmiana poza allowlista.

WEJSCIA (tylko odczyt):
 1. Scenariusz (rank 1): `scenariusze/ZERO_mini_serial_E01_ADAM_rev.md`, SCENA 1 (od linii 62; ok. 3,5 min) i `scenariusze/MANIFEST.sha256`.
 2. Materialy produkcyjne Sceny 1 (rank 4): /tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/zero-extract/Zero/ZERO_DO_PRZENIESIENIA/ZERO_produkcja_flow/ZERO_E01_rozpiska_sekundowa.md (sekcja SCENA 1, 8 ujec), ZERO_E01_S1_Clip00..11.md, ZERO_VEO3_E01_Scena1_FULL_ENG.md i _FULL_ENG_edited.md, ZERO_Scena1_beaty_7s_ENG.md, ZERO_INSTRUKCJA_Flow_scena1_ciaglosc.md, ZERO_instrukcje_dla_agenta_Flow.md, ZERO_metoda_AB_montaz.md, ZERO_decyzje_rewizja.md, ZERO_repercusje_spojnosc.md oraz /tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/zero-extract/Zero/ZERO_DO_PRZENIESIENIA/ZERO_E01_produkcja/01_nota_rezyserska.md, 02_charakterystyki_postaci.md, 08_noty_techniczne.md; ten sam zestaw wgrany przez wlasciciela w /root/.claude/uploads/3337db06-529b-5b00-81d6-a0a7013a451d/ (03_opisy_wizualne_scen, 04_dzwiek_i_muzyka, 05_inserty_closeup, 06_przejscia_scen, 07_podtekst_dialogowy, INSTRUKCJA_Flow_scena1, instrukcje_dla_agenta_Flow, metoda_AB, konsultacja_scenariuszowa).
 3. Decyzje i badania: `autobot/DECYZJE.md` (ECHO-020, 027, 036), `docs/research/ZERO-RESEARCH-001-porownanie-generatorow-wideo/seedance.md`, `docs/research/ZERO-RESEARCH-003-api-i-mcp-sterowanie/seedance.md`, `docs/research/ZERO-RESEARCH-005-zestawienie-zbiorcze/zestawienie_zbiorcze.md`.
 Hierarchia przy sprzecznosci: scenariusz E01 (rank 1) > decyzje wlasciciela (ECHO) > dokumenty produkcyjne (rank 4). Sprzecznosc oznacz w pliku i podaj, co przyjeto.

ZADANIE: utworz plik `docs/produkcja/ZERO-PROD-001-scena1-seedance/scena1_seedance.md` (po polsku; prompty i dialogi do wklejenia po angielsku; nazwy techniczne bez znakow diakrytycznych). Sekcje: 0 Cel i sposob uzycia; 1 Parametry techniczne Seedance 2.5 (model `dreamina-seedance-2-5-260628`, 24 fps, 16:9, 1080p, dlugosc 4-30 s, `generate_audio`, tryby first/last frame i reference nie lacza sie w jednym zadaniu, draft 480p, seed); 2 Stale zasady (postacie: Michal ZAWSZE po LEWEJ i Karolina po PRAWEJ, wyglad i ubior z dokladnym "co ma i czego nie ma" — jeden dinozaur, bez obraczek, zielona kurtka Karoliny; lokacja Nowy Swiat; swiatlo; dialog EN, mowi jedna osoba naraz; dzwiek tylko ambient miasta, bez muzyki; tempo bez martwej ciszy); 3 Referencje do przygotowania (sloty obrazow: Michal, Karolina, Nowy Swiat, tramwaj, sweter; z zastrzezeniem ograniczenia prawdziwych twarzy i ze referencji jeszcze nie ma); 4 OS CZASU W MILISEKUNDACH: tabela master timeline dla calej Sceny 1 (kolumny: id zdarzenia, klip, start ms, koniec ms, klatka start, klatka koniec przy 24 fps, typ [obraz/kamera/kwestia/ambient/SFX], opis, mowca, kwestia EN i PL kanon, poziom dzwieku); kwestie z dokladnym start i koniec ms wyliczonym z liczby slow i podanego tempa; tlo dzwiekowe (tramwaj, kroki, glosy, ptaki) z ms start/koniec i poziomem; zdarzenia obrazu (np. napis ZERO, wejscie tramwaju, pusty murek); 5 Prompty ujec po angielsku dla kazdego klipu (z segmentami czasowymi zgodnymi z osia czasu, blokiem NEGATIVE, ustawieniem pierwszej klatki lub referencji i dlugoscia klipu); 6 Procedura weryfikacji i montazu (transkrypcja ze znacznikami slow i porownanie z osia czasu, tolerancja np. +/- 2 klatki dla startu kwestii, powtorka klipu przy przekroczeniu, kontrola L/P, jeden dinozaur, ciaglosc; dopasowanie dzwieku i polskiego glosu w montazu); 7 Co jeszcze dolozyc (min. 8 pozycji z uzasadnieniem i oznaczeniem decyzji wlasciciela); 8 Ryzyka i pytania do wlasciciela (kazde jako ABC, bez rozstrzygania).
 Wlasciwosci osi czasu: 1) tabela ciagla, bez luk i nakladek w obrebie klipu; 2) tempo mowy podaj i uzasadnij zrodlem (rozpiska: 2,5-3 slowa/s dla polskiego; dla angielskich wersji osobno); 3) jedna osoba mowi naraz; 4) sumy czasow ujec = dlugosci klipow; 5) przy konflikcie dokumentow o czasie obowiazuje scenariusz i rozpiska sekundowa Sceny 1 z jawna adnotacja.

REGULA PRZECIW SAMOOSZUKIWANIU:
 - Zakaz dopisywania faktow, kwestii, postaci i zdarzen spoza scenariusza; kanon dialogow bez zmian (G2); angielskie wersje tylko jako PROPOZYCJA; wszystko "co jeszcze dolozyc" oznacz jako propozycje, nie czesc kanonu.
 - Zakaz obiecywania precyzji, ktorej model nie gwarantuje: wprost napisz, ze milisekundowa dokladnosc to plan i kryterium kontroli, a nie gwarancja generatora.
 - Zakaz twierdzen o mozliwosciach Seedance z pamieci; tylko z zatwierdzonych badan z odnosnikiem (plik i sekcja).
 - Zakaz przejmowania ograniczen Flow/Veo (klip 10 s, Entity, "Save frame") jako cech Seedance; przeksztalc je (first_frame, reference_image) i zaznacz zmiane.
 - Zakaz rankingu i rekomendacji wyboru narzedzia (ECHO-027); zakaz nowych odczytow sieci, kont, kluczy, wywolan API i generowania wideo.
 - Zakaz edycji plikow wejsciowych i poza allowlista; pliki pomocnicze tylko w scratchpadzie sesji; pisz plik etapami (kilka dopisan).

PROCEDURA NAPRAWCZA PRZY FAIL: Evaluator numeruje zarzuty (miejsce, punkt listy, reprodukcja). Operator (w obronie) odpowiada PRZYJMUJE/ODRZUCAM z dowodem; po werdykcie NAPRAW poprawia tylko wskazane miejsca.

ALLOWLISTA:
  - `docs/produkcja/ZERO-PROD-001-scena1-seedance/scena1_seedance.md` (nowy plik)
ZAKAZANE BEZWZGLEDNIE: `scenariusze/`, `autobot/`, `docs/analiza/`, `docs/research/*` (tylko odczyt), `docs/audiobook/`, `docs/proces/`, `docs/przeglad-2026-11-27/`, `docs/rozbieznosci/`, pliki wejsciowe (uploads, archiwum), polecenia git zmieniajace stan (poza rola Integration), sekrety, siec.

MIEJSCE PRACY: `docs/produkcja/ZERO-PROD-001-scena1-seedance/`
BAZA:          HEAD galezi roboczej
OBIEG:         Operator -> Evaluator (10 punktow) -> Obrona przy zarzutach -> Final Control (per zarzut) -> Integration

RUNDA: w toku (rundy 1-3 z 3; licznik w rejestrze aktualizuje orkiestrator po zakonczeniu workflow)
