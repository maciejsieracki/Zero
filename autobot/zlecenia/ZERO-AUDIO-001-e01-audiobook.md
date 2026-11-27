# ZERO-AUDIO-001-e01-audiobook

WYZWALACZ:  decyzja wlasciciela ECHO-014 (2026-11-27): przygotowac E01 jako tekst audiobooka do odczytu przez lektora i wyslania recenzentowi scenariusza.
GOAL:       Istnieje zweryfikowany tekst audiobooka dla odcinka E01, gotowy do plynnego odczytu przez jednego lektora: kompletny, z dialogami slowo w slowo, z dopiskami opisowymi wyprowadzonymi ze scenariusza (bez nowych faktow), z PDF, notatka dla lektora i plikiem sladu dodatkow.
KONIEC:     PRAWDA gdy scenariusze S-U1..S-U7 przechodza. Zadna zmiana poza allowlista.

ZADANIE: na podstawie `scenariusze/ZERO_mini_serial_E01_ADAM_rev.md` (przeczytaj w calosci, Read partiami do konca) przygotuj tekst audiobooka dla E01.
1. FORMA: jeden lektor czyta calosc. Narracja w trzeciej osobie, czas terazniejszy (jak w scenariuszu). Kazdy segment scenariusza (sceny numerowane, montaz Zero Day, bloki przeszlosci P1-P4, wstawki medialne) zaczyna sie krotkim zapowiadajacym zdaniem czytanym na glos (np. "Scena pierwsza. Warszawa, Nowy Swiat, rano."), bez timecodow i etykiet CZAS.
2. DIALOGI: kazda kwestia scenariusza zostaje SLOWO W SLOWO (te same slowa, ta sama kolejnosc). Zapisuj je z myslnikiem dialogowym. Dla jednego lektora dodawaj krotkie dopiski o mowcy poza kwestia ("— powiedziala Karolina") tylko tam, gdzie zmiana mowcy nie jest oczywista; w szybkich wymianach nie powtarzaj dopiskow przy kazdej kwestii. Kwestie w innym jezyku (np. norweskim) oznacz dopiskiem, jesli scenariusz to zaznacza; nie rozstrzygaj za autora.
3. OPISY: rozwin didaskalia i opisy zdarzen w plynna narracje, aby sluchacz mogl sobie wyobrazic miejsce i czynnosc. Wolno: rozwinac to, co w scenariuszu jest zapisane skrotowo; dodac ogolne szczegoly zmyslowe (swiatlo, dzwiek, pogoda, ruch, tempo) zgodne z naglowkiem sceny. NIE wolno: wprowadzac nowych faktow fabularnych, nazw, dat, liczb, wieku, motywow, relacji ani wydarzen; zmieniac przebiegu sceny; rozstrzygac sprzecznosci kanonu (zob. `docs/analiza/ZERO-ANALIZA-001-e01-logika-timing-napiecie/raport.md` — tylko do odczytu, zeby wiedziec, gdzie sa sprzecznosci).
4. ZAMIANA ELEMENTOW NIECZYTELNYCH: teksty ekranowe (paski TV, napisy, plansze, daty) zamien na narracje ("Na ekranie pojawia sie napis: ..."); liczby, godziny i skroty zapisuj slowami; kamera i oznaczenia UJECIE zamien na naturalny opis albo pomin, jesli nic nie wnosza dla sluchacza.
5. MATERIAL POMOCNICZY (rzad 4, tylko dla nastroju; scenariusz zawsze wygrywa): dokumenty produkcyjne w `/tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/zero-unrar/Zero/ZERO_E01_produkcja/` (np. 03_opisy_wizualne_scen.md). Znane sprzecznosci tych dokumentow z scenariuszem (np. nazwisko Michala, kolor wlosow Karoliny, "ADAM-1", wiek Very w blokach P) NIE MOGA trafic do tekstu.
6. PLIKI WYJSCIOWE (allowlista):
   - `e01_audiobook.md` — tekst do odczytu (czyste zdania i kwestie, bez znacznikow roboczych; pisz go etapami, np. kilka dopisan do jednego pliku, aby uniknac przeciazenia odpowiedzi);
   - `e01_audiobook.pdf` — ten sam tekst w PDF z osadzona czcionka z polskimi znakami (np. ReportLab + DejaVuSans; ReportLab mozna doinstalowac przez pip, czcionke przez pakiet fonts-dejavu-core); sprawdz pdftotext; koniec: "Koniec odcinka.";
   - `notatka_dla_lektora.md` — instrukcja dla lektora: sposob czytania (tempo, pauzy miedzy segmentami, jak rozrozniac mowcow bez zmiany glosu), lista trudnych nazw i terminow z wymowa (np. rs1799945, HYV-1, Swinoujscie, Bielanski, nazwy norweskie), liczba slow i szacowany czas czytania per segment i lacznie (150 slow/min), oraz lista miejsc sprzecznych w scenariuszu "do decyzji autora" (odtworzonych bez rozstrzygania);
   - `slad_dodatkow.md` — tabela: dodatek opisowy -> linia i fragment scenariusza, z ktorego wynika; co najmniej jeden wpis na kazdy segment, a dla dodatkow o charakterze ogolnie zmyslowym oznaczenie "szczegol zmyslowy bez faktu".

REGULA PRZECIW SAMOOSZUKIWANIU (z faktycznych bledow tego projektu):
- Zakaz uznania "dialogi zgodne" bez automatycznego porownania wszystkich kwestii (wlasny skrypt python3 -I: wyciagnij kwestie ze scenariusza i z audiobooka, znormalizuj, porownaj liczbe i kolejnosc). Podaj wynik porownania w raporcie.
- Zakaz "wzbogacania" fabuly: kazdy dodatek ma slad w scenariuszu albo jest ogolnym szczegolem zmyslowym. W razie watpliwosci dodatku NIE wpisuj.
- Zakaz kopiowania do tekstu etykiet roboczych scenariusza (CZAS, UJECIE, timecody, nawiasy sceniczne) oraz znanych bledow z dokumentow pomocniczych.
- Zakaz rozstrzygania sprzecznosci kanonu za autora i zakaz poprawiania scenariusza.
- Zakaz uznania PDF za gotowy bez sprawdzenia polskich znakow (pdftotext) i zgodnosci z tekstem.
- Zakaz edycji plikow poza allowlista.

PROCEDURA NAPRAWCZA PRZY FAIL: Evaluator numeruje zarzuty (plik, linia/segment, punkt listy, reprodukcja). Operator (w obronie) odpowiada na kazdy numer PRZYJMUJE/ODRZUCAM z dowodem; po werdykcie NAPRAW poprawia tylko wskazane miejsca (np. konkretne segmenty), bez przepisywania calosci.

ALLOWLISTA:
  - `docs/audiobook/ZERO-AUDIO-001-e01-audiobook/e01_audiobook.md`
  - `docs/audiobook/ZERO-AUDIO-001-e01-audiobook/e01_audiobook.pdf`
  - `docs/audiobook/ZERO-AUDIO-001-e01-audiobook/notatka_dla_lektora.md`
  - `docs/audiobook/ZERO-AUDIO-001-e01-audiobook/slad_dodatkow.md`
ZAKAZANE BEZWZGLEDNIE: `scenariusze/` (G1), `autobot/`, `docs/analiza/`, `docs/research/`, `docs/proces/`, `docs/przeglad-2026-11-27/`, `docs/rozbieznosci/`, E02, E03 i Planify, polecenia git zmieniajace stan (poza rola Integration), sekrety, wysylanie tekstu do jakichkolwiek zewnetrznych uslug (w tym uslug glosowych).

MIEJSCE PRACY: `docs/audiobook/ZERO-AUDIO-001-e01-audiobook/`
BAZA:          HEAD galezi roboczej (baza scenariuszy z MANIFEST.sha256)
OBIEG:         Operator -> Evaluator (10 punktow) -> Obrona przy zarzutach -> Final Control (per zarzut) -> Integration

RUNDA: 1 z 3
