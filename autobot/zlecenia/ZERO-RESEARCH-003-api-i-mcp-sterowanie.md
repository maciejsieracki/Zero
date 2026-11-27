# ZERO-RESEARCH-003-api-i-mcp-sterowanie

WYZWALACZ:  decyzja wlasciciela ECHO-009 (2026-11-27): sprawdzic, czy dla kazdego dostawcy istnieje API lub system MCP pozwalajacy sterowac praca z Claude Code. RESEARCH-001 zamkniety (lista dostawcow i modeli w repozytorium); slot wolny.
GOAL:       Istnieje zweryfikowane zestawienie, ktorzy dostawcy wideo AI (Kling, Seedance, Google Veo, Sora 2, MiniMax) udostepniaja API, oficjalne SDK i serwer MCP (oficjalny lub spolecznosciowy) pozwalajace sterowac generowaniem z Claude Code, z punktowa ocena gotowosci i oznaczeniem pewnosci zrodel.
KONIEC:     PRAWDA gdy scenariusze S-R13..S-R17 przechodza. Zadna zmiana poza allowlista.

STRUKTURA: pieciu dostawcow = pieciu wezlow (Operator -> Evaluator -> Obrona -> Final Control, bez wlasnej integracji), potem synteza `zestawienie_api_mcp.md` (Operator -> Evaluator -> Obrona -> Final Control -> Integration, ktory zatwierdza WSZYSTKIE szesc plikow).

ZADANIE (kazdy wezel: jeden dostawca): w pliku wezla (`docs/research/ZERO-RESEARCH-003-api-i-mcp-sterowanie/<dostawca>.md`) opisz pola z S-R13:
1. czy istnieje publiczne API (REST) dostepne dla zwyklego konta i jak sie je uzyskuje (klucz, rejestracja, ograniczenia regionalne, weryfikacja firmy, lista oczekujacych); wskaz stan na 2026-11-27 (uwaga: API Sora 2 wg RESEARCH-001 zostalo wylaczone 2026-09-24 — potwierdz lub obal i opisz alternatywne drogi dostepu);
2. model pracy: zadanie asynchroniczne (id zadania, sprawdzanie statusu, pobranie wyniku), webhook/callback;
3. limity: zapytania na minute, zadania rownolegle;
4. zakres API wzgledem aplikacji: tekst do wideo, obraz do wideo z klatka startowa i koncowa, przedluzanie klipu, obrazy referencyjne postaci/obiektow (dla spojnosci postaci), parametry audio, rozdzielczosc, dlugosc, seed;
5. oficjalne SDK lub CLI (jezyki, repozytorium, ostatnia aktywnosc, licencja);
6. serwer MCP: oficjalny dostawcy i spolecznosciowe (nazwa, repozytorium, licencja, data ostatniej aktywnosci, zakres narzedzi); sprawdz repozytoria i rejestry (tylko odczyt);
7. alternatywne drogi dostepu do tego samego modelu (platformy posredniczace) — tylko wymien z dowodem dostepnosci, bez porownywania cen;
8. minimalna sciezka sterowania z Claude Code: (a) przez serwer MCP, (b) przez wywolania HTTP/SDK z narzedzia powloki, (c) brak — z nazwami endpointow lub narzedzi wynikajacymi ze zrodel;
9. zrodla rzedu 1 (dokumentacja API, oficjalne repozytoria; URL i data odczytu) i pewnosc.
SYNTEZA: `zestawienie_api_mcp.md`: tabela dostawcow, punktowa ocena gotowosci wg JAWNEJ punktacji w pliku: publiczne API dla zwyklego konta 3 pkt; obraz do wideo z klatka startowa 2; obrazy referencyjne postaci 2; zadania asynchroniczne i webhook 1; oficjalne SDK 1; oficjalny serwer MCP 2 (spolecznosciowy 1); brak barier onboardingu 1 (max 12); kolejnosc z punktow; lista zrodel; uwagi o niepewnosci; krotka sekcja OPINIA (maks. 8 linii).

REGULA PRZECIW SAMOOSZUKIWANIU:
- BADANIE JEST WYLACZNIE ODCZYTEM dokumentacji, repozytoriow i rejestrow. Zakaz zakladania kont i kluczy API, instalowania serwerow MCP lub bibliotek dostawcow, wykonywania wywolan API (w tym platnych), uruchamiania kodu z repozytoriow.
- Zakaz uznania, ze serwer MCP lub SDK istnieje, bez adresu repozytorium lub rejestru i daty ostatniej aktywnosci; serwery spolecznosciowe to rzad 4 (NIEPOTWIERDZONE co do jakosci).
- Zakaz podawania endpointow, parametrow i limitow z pamieci; tylko ze zrodel rzedu 1 odczytanych na 2026-11-27.
- Hosty niektorych dostawcow sa w tej sesji zablokowane; wtedy uzyj wyszukiwarki z ograniczeniem do oficjalnych domen i oznacz "odczyt posredni".
- Zakaz zapisu jakichkolwiek kluczy i sekretow.
- Zakaz edycji plikow poza allowlista.

PROCEDURA NAPRAWCZA PRZY FAIL: Evaluator numeruje zarzuty (plik, miejsce, punkt listy, reprodukcja). Operator (w obronie) odpowiada na kazdy numer PRZYJMUJE/ODRZUCAM z dowodem; po werdykcie NAPRAW poprawia tylko wskazane pola.

ALLOWLISTA (katalog `docs/research/ZERO-RESEARCH-003-api-i-mcp-sterowanie/`):
  - `kling.md`, `seedance.md`, `veo.md`, `sora2.md`, `minimax.md` (po jednym na wezel)
  - `zestawienie_api_mcp.md` (synteza)
ZAKAZANE BEZWZGLEDNIE: `scenariusze/`, `autobot/`, `docs/analiza/`, `docs/audiobook/`, `docs/proces/`, `docs/przeglad-2026-11-27/`, `docs/rozbieznosci/`, `docs/research/ZERO-RESEARCH-001-*` i `-002-*` (tylko odczyt), polecenia git zmieniajace stan (poza rola Integration), sekrety, zakladanie kont i kluczy, instalowanie serwerow MCP, wywolania API.

MIEJSCE PRACY: `docs/research/ZERO-RESEARCH-003-api-i-mcp-sterowanie/`
BAZA:          HEAD galezi roboczej
OBIEG:         Operator -> Evaluator (10 punktow) -> Obrona przy zarzutach -> Final Control (per zarzut) -> Integration (po syntezie)

RUNDA: w toku (rundy 1-3 z 3 na wezel; licznik w rejestrze aktualizuje orkiestrator po zakonczeniu workflow)
