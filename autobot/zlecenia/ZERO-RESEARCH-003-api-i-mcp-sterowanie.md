# ZERO-RESEARCH-003-api-i-mcp-sterowanie

WYZWALACZ:  decyzja wlasciciela ECHO-009 (2026-11-27): sprawdzic, czy dla kazdego dostawcy istnieje API lub system MCP pozwalajacy sterowac praca z Claude Code. Zalezy od ZERO-RESEARCH-001 (lista dostawcow i modeli); start po zwolnieniu slotu (pula 2).
GOAL:       Istnieje zweryfikowane zestawienie, ktorzy dostawcy wideo AI (Kling, Seedance, Google Veo, Sora 2, MiniMax) udostepniaja API, oficjalne SDK i serwer MCP (oficjalny lub spolecznosciowy) pozwalajace sterowac generowaniem z Claude Code, z punktowa ocena gotowosci i oznaczeniem pewnosci zrodel.
KONIEC:     PRAWDA gdy scenariusze S-R13..S-R17 przechodza. Zadna zmiana poza allowlista.

PODZIAL NA WEZLY: -a Kling, -b Seedance, -c Google Veo, -d Sora 2, -e MiniMax (API); potem synteza (zestawienie_api_mcp) i Final Control. Licznik rund liczy sie dla calego tematu.

ALLOWLISTA (katalog `docs/research/ZERO-RESEARCH-003-api-i-mcp-sterowanie/`):
  - `kling.md`, `seedance.md`, `veo.md`, `sora2.md`, `minimax.md` (po jednym na wezel)
  - `zestawienie_api_mcp.md` (synteza)
ZAKAZANE BEZWZGLEDNIE: `scenariusze/`, `autobot/`, `docs/analiza/`, `docs/przeglad-2026-11-27/`, `docs/rozbieznosci/`, `docs/research/ZERO-RESEARCH-001-*` i `-002-*` (tylko odczyt), polecenia git zmieniajace stan; **zakaz zakladania kont i kluczy API, instalowania serwerow MCP, wykonywania wywolan API (w tym platnych) — badanie jest wylacznie odczytem dokumentacji, repozytoriow i rejestrow**; sekrety.

MATERIAL WEJSCIOWY: wynik RESEARCH-001 (lista dostawcow i modeli, ceny) — rzad 2 po przejsciu Final Control tego tematu.
ZRODLA (rzad 1 rozstrzyga): oficjalna dokumentacja API i oficjalne repozytoria dostawcow na dzien 2026-11-27; repozytoria i rejestry serwerow MCP to rzad 4 (z data ostatniej aktywnosci i licencja).

MIEJSCE PRACY: `docs/research/ZERO-RESEARCH-003-api-i-mcp-sterowanie/`
BAZA:          HEAD galezi roboczej

PLAN SPRAWDZENIA: S-R13 kompletnosc; S-R14 niezalezne potwierdzenie; S-R15 sterowalnosc z Claude Code bez wywolan; S-R16 ocena jawna; S-R17 zrodla, zakres, bezpieczenstwo.

RUNDA: 0 z 3
