# ZERO-PAKIET-024-kadry-uzupelniajace-s1

WYZWALACZ:  decyzje wlasciciela ECHO-040 i ECHO-041 (2026-11-28): pakiet ma zachowac przejscia i kadry bez postaci, ktore nadaja filmowi realny wyglad; pozycja dodatkowa: Kadry uzupelniajace i przejscia Sceny 1; fala 2.
GOAL:       Istnieje zweryfikowany plik `docs/produkcja/pakiet/B07_kadry_uzupelniajace_i_przejscia_s1.md`: Kadry uzupelniajace i przejscia Sceny 1 dla odcinka E01 serialu ZERO (narzedzie docelowe Kling 4.0), kompletny wg specyfikacji, oparty na scenariuszu E01 i zatwierdzonych materialach, z propozycjami reżyserskimi oznaczonymi jako PROPOZYCJA, jawnymi rozbieznosciami zrodel i pytaniami ABC, bez nowych faktow kanonu.
KONIEC:     PRAWDA gdy scenariusze S-D1..S-D5, S-D7 oraz S-D6, S-U9 przechodza (opisy w `autobot/SCENARIUSZE.md`). Zadna zmiana poza allowlista.

WEJSCIA (tylko odczyt; hierarchia przy sprzecznosci: scenariusz E01 rank 1 > decyzje wlasciciela ECHO > raport ANALIZA-003 i dokumenty produkcyjne rank 4; sprzecznosci zapisuj jawnie z dwoma cytatami, nie rozstrzygaj):
 - `scenariusze/ZERO_mini_serial_E01_ADAM_rev.md` i `MANIFEST.sha256`; `docs/analiza/ZERO-ANALIZA-001-e01-logika-timing-napiecie/`; `docs/analiza/ZERO-ANALIZA-003-produkcja-e01-spojnosc/` (raport.md, tabela_rozbieznosci.md);
 - `autobot/DECYZJE.md` (ECHO-020, 027, 036, 037, 040, 041), `PLAN_WDROZENIA_ZERO.md`;
 - materialy produkcyjne: kopia archiwum /tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/zero-extract/Zero/ZERO_DO_PRZENIESIENIA/ (ZERO_E01_produkcja/ — w szczegolnosci 03_opisy_wizualne_scen, 05_inserty_closeup, 06_przejscia_scen, 04_dzwiek_i_muzyka; ZERO_produkcja_flow/ — rozpiska sekundowa, beaty 7 s, instrukcje) oraz pliki wgrane przez wlasciciela w /root/.claude/uploads/3337db06-529b-5b00-81d6-a0a7013a451d/;
 - badania Klinga: `docs/research/ZERO-RESEARCH-001-*/kling.md`, `-002-*/kling.md`, `-003-*/kling.md`, `-005-*/zestawienie_zbiorcze.md`, `-008-*/omni_vs_kling.md`; plik Sceny 1 `docs/produkcja/ZERO-PROD-002-scena1-kling/scena1_kling.md`.

ZADANIE: utworz plik `docs/produkcja/pakiet/B07_kadry_uzupelniajace_i_przejscia_s1.md` (po polsku; nazwy techniczne bez znakow diakrytycznych; prompty po angielsku). Zawartosc: Warstwa kadrow uzupelniajacych i przejsc dla Sceny 1 (Warszawa, Nowy Swiat, ranek): (1) co scenariusz i rozpiska juz maja bez postaci lub z minimalnym udzialem postaci (ujecie z powietrza tramwaju na Nowym Swiecie, insert swetra, pusty murek, kadry miasta) z miejscem w osi czasu; (2) co najmniej 6 propozycji kadrow uzupelniajacych (np. detale ulicy, tramwaj i druty, szyldy bez czytelnych marek, golebie, kawa i telefon na murku, rece, cienie, przechodnie bez twarzy) z miejscem miedzy istniejacymi ujeciami (start i koniec w ms, klatki), czasem, promptem EN, wykonaniem w Klingu, dzwiekiem i wplywem na sume czasu sceny (nie zmieniaj czasu ani kolejnosci kanonicznych kwestii); (3) przejscia wewnatrz Sceny 1 i do Sceny 2 (CUT TO na PSE; pusty murek jako ostatnia klatka) z mostem dzwiekowym; (4) wersja wariantow: minimalna (tylko ze scenariuszem) i rozszerzona (z kadrami uzupelniajacymi) z roznica czasu; (5) pytania ABC do wlasciciela (czy dopuszczamy kadry spoza scenariusza, ile); (6) zgodnosc z osia czasu ZERO-PROD-002 (jesli zamkniety) i lista korekt, ktore trzeba tam wprowadzic.
 Na poczatku pliku: naglowek z ID, data (2026-11-28), zakres, zrodla z hashami SHA-256 i legenda oznaczen. Na koncu: pytania ABC, powiazania z innymi plikami pakietu i "Co jeszcze dolozyc".

REGULA PRZECIW SAMOOSZUKIWANIU:
 - Zakaz dopisywania faktow kanonu; kadry i przejscia spoza scenariusza to PROPOZYCJA REZYSERSKA; decyzje kanoniczne i produktowe tylko jako pytania ABC (G2, G3).
 - Kazda informacja z odnosnikiem (plik i sekcja); sprzecznosci jawnie z dwoma cytatami; obowiazuje scenariusz i decyzje wlasciciela.
 - Zakaz twierdzen o mozliwosciach Klinga z pamieci; tylko z zatwierdzonych badan z odnosnikiem albo BRAK DANYCH; precyzja ms to plan, nie gwarancja modelu.
 - Zakaz rankingu i wyboru narzedzia (ECHO-027); zakaz sieci, kont, kluczy, wywolan API i generowania obrazow i wideo; zakaz edycji plikow wejsciowych i poza allowlista; skrypty tylko w scratchpadzie; pisz plik etapami.
 - Zakres: E01 (E03 poza zakresem); szczegolowo tylko Scena 1.

PROCEDURA NAPRAWCZA PRZY FAIL: Evaluator numeruje zarzuty; Operator odpowiada PRZYJMUJE/ODRZUCAM z dowodem; po werdykcie NAPRAW poprawia tylko wskazane miejsca.

ALLOWLISTA:
  - `docs/produkcja/pakiet/B07_kadry_uzupelniajace_i_przejscia_s1.md` (nowy plik)
ZAKAZANE BEZWZGLEDNIE: `scenariusze/`, `autobot/`, `docs/analiza/`, `docs/research/*`, inne pliki `docs/produkcja/` (tylko odczyt), pliki wejsciowe, polecenia git zmieniajace stan (poza rola Integration), sekrety, siec.

MIEJSCE PRACY: `docs/produkcja/pakiet/`
BAZA:          HEAD galezi roboczej
OBIEG:         Operator -> Evaluator (10 punktow) -> Obrona przy zarzutach -> Final Control (per zarzut) -> Integration (osobny commit na temat, ECHO-042)

RUNDA: w kolejce, Sonnet 5.5 (ECHO-042) (fala 2); rundy 1-3 z 3; licznik w rejestrze aktualizuje orkiestrator po zakonczeniu workflow
