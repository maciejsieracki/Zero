# ZERO-PROCES-004-przejecie-regul-autobot

WYZWALACZ:  decyzja wlasciciela ECHO-015 pkt 3 = A (2026-11-27): przejac nowsze reguly AutoBot, zachowujac nasze reguly usuniete w nowszym zestawie. Zmiana procesu jest osobnym tematem (tryb zmiany procesu, R11). Zalezy od zamknietego ZERO-PROCES-002 (inwentarz).
GOAL:       Istnieje zweryfikowany dokument zasad procesu ZERO (`autobot/ZASADY_PROCESU.md`), ktory zawiera reguly R1-R12 z najnowszego zestawu AutoBot oraz zachowane z poprzedniej wersji reguly roli orkiestratora, bez elementow wykluczonych, z odwzorowaniem na obecny workflow i lista wymaganych zmian w dokumentach.
KONIEC:     PRAWDA gdy scenariusze S-P11..S-P14 przechodza. Zadna zmiana poza allowlista.

ZADANIE: utworz nowy plik `autobot/ZASADY_PROCESU.md` (po polsku) z sekcjami:
1. REGULY PRZEJETE (R1-R12 z `docs/proces/ZERO-PROCES-002-inwentarz-zasad-autobot/inwentarz.md`, sekcja 6): obieg Operator -> Evaluator -> Obrona (tylko przy zarzutach) -> Final Control -> Integration; obrona (ten sam Operator odpowiada na kazdy numer PRZYJMUJE/ODRZUCAM z dowodem, brak odpowiedzi = PRZYJMUJE); Final Control per zarzut (NAPRAW/ODDAL/DO DECYZJI CZLOWIEKA); Evaluator 10 punktow PASS/FAIL/NOT_RUN; Integration jako osobna rola (allowlista, hashe przed i po, bez push/merge/deploy, bez git add . i -A); uczciwy model kontroli (independent-sessions tylko przy faktycznie roznych sesjach, inaczej logical-single-session); kontynuacja po wyniku terminalnym; czas w ISO-8601 UTC (brak = TIMESTAMP_UNVERIFIED); BLOCK dopiero po petli naprawczej; ponowny SHA-256 po korekcie i oznaczenie SUPERSEDED; zmiana normatywna procesu tylko po niezaleznym Evaluatorze, Final Control i ECHO; raport terminalny z polami TR-001..TR-010. Kazda regule opatrz odnosnikiem do zrodla (plik i linia) w ORYGINALE.
2. REGULY ZACHOWANE Z POPRZEDNIEJ WERSJI (rola orkiestratora; nowszy zestaw je usuwa lub oslabia): (a) eskalacja przez orkiestratora — subagent nie rozstrzyga bezposrednio z wlascicielem, "do decyzji czlowieka" analizuje najpierw orkiestrator, do wlasciciela trafia tylko nierozstrzygalna reszta (v2 ref l. 64-66; v2 controller l. 228-230); (b) orkiestrator autoryzuje/akceptuje integracje i jako jedyny zapisuje READY_FOR_DEPLOY (v2 ref l. 136-137; v2 controller l. 246-247); (c) orkiestrator nie wykonuje pracy merytorycznej, ktora sam ma oceniac (v2 ref l. 138); (d) nie zmienia po cichu GOAL, granic ani limitow (v2 ref l. 138-139); (e) nie publikuje bez zgody (v2 ref l. 139) — ZAKRES ZGODY DO DOPRECYZOWANIA wedlug ECHO-017 (do czasu odpowiedzi wlasciciela obowiazuje ECHO-004: commit i push na galaz robocza; inne dzialania zewnetrzne tylko na wyrazne polecenie; w dokumencie wpisz tylko ten stan, bez poszerzania). ZACHOWUJEMY TEZ nowsze uprawnienie koordynatora: samodzielne decyzje techniczne w granicach kontraktu (f ref l. 189-190), z zastrzezeniem, ze decyzje z konsekwencja dla pieniedzy, danych, prawa, ryzyka, zakresu lub odwracalnosci ida do wlasciciela jako pytanie ABC (ECHO-017). Dla kazdej podaj cytat z paczki v2 i wskaz, czy nowszy zestaw ja usuwa, oslabia czy zachowuje (z linia).
3. CZEGO NIE PRZEJMUJEMY (z uzasadnieniem, inwentarz sekcja 5): autonomiczne dzialania live i wdrozenie bez osobnej bramki; elementy srodowiska OpenClaw (Lobster, Managed Task Flow, sessions_spawn, memory-core, USER.md/MEMORY.md, heartbeat); zuzycie tokenow per faza; nazewnictwo rol A-main/B i podzial na 10 modulow (decyzja ECHO-016: Orkiestrator = glowny agent sesji, Wykonawca = workflow i wszyscy jego subagenci; nazewnictwo A-main/B nie wchodzi do zasad).
4. ODWZOROWANIE NA OBECNY WORKFLOW ZERO (najpierw odwzoruj role: Orkiestrator = glowny agent sesji; Wykonawca = workflow i subagenci Operator/Evaluator/Obrona/Final Control/Integration; potem reguly): dla kazdej reguly R1-R12 i zachowanej: czy juz dziala w skrypcie `zero-autobot-v2` (obrona, FC per zarzut, Integration, hashe per plik), czy wymaga zmiany (np. czas UTC — skrypt workflow nie ma dostepu do daty, wiec wymaga zapisu przez agenta lub orkiestratora; oznaczenie trybu kontroli), czy jest niewykonalna w tym srodowisku (podaj powod).
5. WYMAGANE ZMIANY W DOKUMENTACH I SKRYPCIE: lista konkretnych miejsc (plik, sekcja, co zmienic) w `autobot/00_PUNKT_STARTOWY.md`, `autobot/WYBORY_TRWALE.md`, `autobot/REJESTR_TEMATOW.md` (np. licznik rund) i skrypcie workflow; BEZ wykonywania tych zmian (osobne tematy).

ZRODLA: (a) inwentarz (tylko odczyt): `docs/proces/ZERO-PROCES-002-inwentarz-zasad-autobot/inwentarz.md`; (b) ORYGINAL najnowszego zestawu: swieza ekstrakcja `/root/.claude/uploads/3337db06-529b-5b00-81d6-a0a7013a451d/a4edf6ca-Autobot.rar` (unrar x do NOWEGO pustego katalogu w scratchpadzie), plik `autobot-skills/skills/autobot-orchestrator/references/autobot-reference-contract.md` i skille tego zestawu; (c) paczka v2: `/tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/autobot-zip/` (tylko odczyt). Hierarchia: oryginalny tekst (rzad 1) rozstrzyga; inwentarz to rzad 2.

REGULA PRZECIW SAMOOSZUKIWANIU:
- Zakaz parafrazowania reguly bez odnosnika do zrodla (plik i linia) zweryfikowanego na ORYGINALE (nie tylko w inwentarzu).
- Zakaz przejecia regul wykluczonych (autonomiczne live, OpenClaw, tokeny per faza).
- Zakaz oslabienia lub pominiecia naszych regul roli orkiestratora (sekcja 2).
- Zakaz uruchamiania skryptow z archiwum; zakaz modyfikowania archiwum i oryginalow w uploads.
- Zakaz edycji istniejacych plikow `autobot/` w tym temacie (zmiany w nich to osobne tematy).
- Zakaz uznania odwzorowania na workflow za zgodne bez sprawdzenia skryptu (`/tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/workflows/zero-autobot-v2.js`, tylko odczyt).

PROCEDURA NAPRAWCZA PRZY FAIL: Evaluator numeruje zarzuty (sekcja dokumentu, regula, linia zrodla, reprodukcja). Operator (w obronie) odpowiada PRZYJMUJE/ODRZUCAM z dowodem; po werdykcie NAPRAW poprawia tylko wskazane reguly.

ALLOWLISTA:
  - `autobot/ZASADY_PROCESU.md` (nowy plik)
ZAKAZANE BEZWZGLEDNIE: istniejace pliki `autobot/` (00_PUNKT_STARTOWY, WYBORY_TRWALE, DECYZJE, SCENARIUSZE, REJESTR_TEMATOW, PRZEKAZANIE, zlecenia), `scenariusze/`, `docs/`, uploads, skrypt workflow, git zmieniajacy stan (poza rola Integration), sekrety.

MIEJSCE PRACY: `autobot/ZASADY_PROCESU.md`
BAZA:          HEAD galezi roboczej
OBIEG:         Operator -> Evaluator (10 punktow) -> Obrona przy zarzutach -> Final Control (per zarzut) -> Integration

RUNDA: w kolejce (rundy 1-3 z 3; licznik w rejestrze aktualizuje orkiestrator po zakonczeniu workflow)
