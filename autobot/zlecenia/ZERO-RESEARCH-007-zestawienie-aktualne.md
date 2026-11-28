# ZERO-RESEARCH-007-zestawienie-aktualne

WYZWALACZ:  polecenia wlasciciela ECHO-030 i sprostowanie ECHO-031 (2026-11-28): w porownaniu interesuja go tylko systemy "w grze" i ich najnowsze, aktualnie dostepne wersje; to, co wypada, nie jest potrzebne nawet jako nota. RESEARCH-005 i -006 zamkniete (READY_FOR_DEPLOY).
GOAL:       Zestawienie zbiorcze dostawcow wideo AI (.md i .docx) obejmuje wylacznie najnowsza, aktualnie dostepna generacje kazdego systemu (Kling, Seedance, Google Veo, Google Gemini Omni, MiniMax) z jej wariantami cenowymi — z kompletna charakterystyka (dlugosc klipu, rozdzielczosc, koszt 1 minuty Full HD, dzwiek i polski, API/SDK/MCP), bez starszych i niedostepnych modeli (Sora 2 nie wystepuje w pliku w ogole), bez rankingu i rekomendacji, z oznaczeniem pewnosci zrodel.
KONIEC:     PRAWDA gdy scenariusze S-R27..S-R31 przechodza. Zadna zmiana poza allowlista.

ZADANIE: popraw w miejscu `docs/research/ZERO-RESEARCH-005-zestawienie-zbiorcze/zestawienie_zbiorcze.md` oraz `docs/research/ZERO-RESEARCH-005-zestawienie-zbiorcze/zestawienie_zbiorcze.docx`:
 1. Ustal na podstawie zatwierdzonych badan (tylko odczyt: `docs/research/ZERO-RESEARCH-001-*`, `-002-*`, `-003-*`), ktora generacja kazdego systemu jest najnowsza dostepna na 2026-11-27 i zapisz w nowej sekcji "Zakres (najnowsze wersje)" z odnosnikami (plik, sekcja) i data wprowadzenia; "system" = Kling, Seedance, Google Veo, Google Gemini Omni, MiniMax. Wariant cenowy tej samej generacji (np. Fast, Flash, Lite, Mini, Pro) zostaje; starsze generacje znikaja.
 2. Usun z tabel 1, 2, 3 i 3b wszystkie starsze generacje, modele wygasajace i legacy oraz sekcje 5.3 (modele poza tabelami) i 2C (Sora 2) w calosci; Sora 2 i kazdy inny niedostepny lub odpadajacy model nie zostaja w pliku nawet jako nota, wzmianka w legendzie, rozbieznosciach, lukach lub zrodlach (wyjatek: cytat zrodlowy konieczny dla modelu, ktory zostaje). Sekcja "Zakres" wskazuje tylko, ktora wersja jest najnowsza i skad to wiadomo. Zachowaj wylacznie rozbieznosci i luki dotyczace pozostalych modeli; popraw numeracje (R-xx, T-xx) i odnosniki tak, by nie bylo martwych.
 3. Zachowaj strukture i zasady z RESEARCH-005 (ECHO-027: bez rankingu, punktow, opinii; kolejnosc wierszy rosnaco po koszcie 1 minuty przy 1080p, modele bez 1080p osobno z adnotacja; oznaczenia pewnosci bez zmian; sekcja zrodel z hashami SHA-256 plikow zrodlowych).
 4. Wygeneruj ponownie `.docx` z nowego `.md` tym samym sposobem co w RESEARCH-006 (pandoc i python-docx, A4 poziomo, tabela szeroka na A3 poziomo jesli trzeba, powtarzany naglowek tabel, spis tresci, czcionki tabel 7-8 pt; skrypty z poprzedniego tematu sa w scratchpadzie `/tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/word-006/` — mozesz je przeczytac i skopiowac do nowego katalogu `scratchpad/word-007/`); sprawdz wyrenderowane strony (soffice -> PDF -> obrazy).
 5. Dane tylko z zatwierdzonych plikow; zadnych nowych odczytow sieci.

REGULA PRZECIW SAMOOSZUKIWANIU:
 - Zakaz dopisywania faktow z pamieci; zakaz zmiany wartosci komorek (poza usunieciem wierszy i przenumerowaniem odnosnikow).
 - Zakaz uznania generacji za najnowsza bez odnosnika do zrodla z data; w razie sprzecznosci miedzy badaniami opisz ja jawnie i wybierz wariant zgodny z danymi rzedu 1.
 - Zakaz pozostawienia martwych odwolan do usunietych wierszy i sekcji oraz jakiejkolwiek wzmianki o Sora 2 i o innych odpadajacych modelach (po usunieciu: grep po nazwach usunietych modeli w .md i w tekscie .docx).
 - Zakaz rankingu, punktow i rekomendacji (ECHO-027).
 - Zakaz edycji plikow poza allowlista; zakaz sieci; skrypty i pliki tymczasowe tylko w scratchpadzie.
 - Zakaz uznania, ze tabele mieszcza sie w Wordzie, bez obejrzenia wyrenderowanych stron.

PROCEDURA NAPRAWCZA PRZY FAIL: Evaluator numeruje zarzuty (miejsce, punkt listy, reprodukcja). Operator (w obronie) odpowiada PRZYJMUJE/ODRZUCAM z dowodem; po werdykcie NAPRAW poprawia tylko wskazane miejsca.

ALLOWLISTA:
  - `docs/research/ZERO-RESEARCH-005-zestawienie-zbiorcze/zestawienie_zbiorcze.md` (zmiana istniejacego pliku)
  - `docs/research/ZERO-RESEARCH-005-zestawienie-zbiorcze/zestawienie_zbiorcze.docx` (zmiana istniejacego pliku)
ZAKAZANE BEZWZGLEDNIE: `scenariusze/`, `autobot/`, `docs/analiza/`, `docs/audiobook/`, `docs/proces/`, `docs/przeglad-2026-11-27/`, `docs/rozbieznosci/`, `docs/research/ZERO-RESEARCH-001-*`, `-002-*`, `-003-*` (tylko odczyt), polecenia git zmieniajace stan (poza rola Integration), sekrety, siec.

MIEJSCE PRACY: `docs/research/ZERO-RESEARCH-005-zestawienie-zbiorcze/` i scratchpad sesji (pliki pomocnicze)
BAZA:          HEAD galezi roboczej (commit 766ef04 i pozniejsze)
OBIEG:         Operator -> Evaluator (10 punktow) -> Obrona przy zarzutach -> Final Control (per zarzut) -> Integration

RUNDA: w toku (rundy 1-3 z 3; licznik w rejestrze aktualizuje orkiestrator po zakonczeniu workflow)
