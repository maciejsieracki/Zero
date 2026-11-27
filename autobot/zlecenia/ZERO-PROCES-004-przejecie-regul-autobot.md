# ZERO-PROCES-004-przejecie-regul-autobot

WYZWALACZ:  decyzje wlasciciela ECHO-015 pkt 3 = A, ECHO-016, ECHO-017 i zlecenie ECHO-018 (2026-11-27): przygotowac najnowszy, pelny i samodzielny plik zasad AutoBot dla innych agentow, zgodny z ustaleniami. Zmiana procesu jest osobnym tematem (tryb zmiany procesu, R11). Zalezy od zamknietego ZERO-PROCES-002 (inwentarz).
GOAL:       Istnieje zweryfikowany, pelny i samodzielny dokument zasad procesu AutoBot dla innych agentow (`autobot/ZASADY_PROCESU.md`): czesc uniwersalna (wszystkie obowiazujace zasady) i lokalne wypelnienie dla ZERO, zgodny z decyzjami wlasciciela ECHO-010..ECHO-018, z jawnie oznaczonymi punktami otwartymi i z lista wymaganych zmian w istniejacych dokumentach i skrypcie.
KONIEC:     PRAWDA gdy scenariusze S-P11..S-P16 przechodza. Zadna zmiana poza allowlista.

ZADANIE: utworz nowy plik `autobot/ZASADY_PROCESU.md` (po polsku; nazwy techniczne i identyfikatory bez znakow diakrytycznych) jako dokument SAMODZIELNY: nowy agent bez dostepu do tej rozmowy ma moc na nim pracowac. Struktura:
CZESC I — ZASADY UNIWERSALNE (komplet, pelna tresc regul, nie odsylacze):
 1. Zasada nadrzedna: pelne ID, GOAL, kryteria z numerami scenariuszy, allowlista, izolacja, plan sprawdzenia; co oznacza READY_FOR_DEPLOY; co NIE jest dowodem zakonczenia; przekazanie na zewnatrz jako osobna bramka.
 2. Role i odwzorowanie (ECHO-016): Orkiestrator = glowny agent sesji; Wykonawca = workflow i wszyscy jego subagenci; role robocze: Operator, Evaluator, Obrona, Final Control, Integration; zasada "nikt nie wykonuje, ocenia i zatwierdza tego samego wyniku".
 3. Obieg i rundy: Operator -> Evaluator -> Obrona (tylko przy zarzutach) -> Final Control (per zarzut) -> Integration -> READY_FOR_DEPLOY; limit rund, licznik nigdy nie resetowany, manual resume tylko za jawna zgoda wlasciciela z zachowaniem ID i licznika; PASS-WITH-NOTES; pauza tylko tematu czekajacego na decyzje.
 4. Kontrakty rol w pieciu polach (WEJSCIE, ODPOWIEDZIALNOSC, ZAKAZY, DOWOD, WYNIK): Orkiestrator (w tym: samodzielne decyzje techniczne w granicach kontraktu, eskalacja przez orkiestratora, autoryzacja integracji i wylaczny zapis READY_FOR_DEPLOY, zakaz pracy merytorycznej, ktora sam ma oceniac, zakaz cichej zmiany GOAL/granic/limitow — ECHO-017), Operator, Evaluator (10 punktow PASS/FAIL/NOT_RUN z expected/observed/evidence; CLEAR tylko przy 10 PASS), Obrona (brak odpowiedzi = PRZYJMUJE), Final Control (NAPRAW/ODDAL/DO DECYZJI CZLOWIEKA per zarzut), Integration (allowlista, hashe przed i po, bez push/merge/deploy, bez git add . i -A).
 5. Zapis zlecenia (dispatch) przed startem; ID PREFIKS-ETAP-NNN-slug niezmienne i nieuzywane ponownie; pytanie decyzyjne ID-Qn; wyzwalacze; zakaz uzupelniania zapisow wstecz.
 6. Allowlista, izolacja, granice nienaruszalne, sekrety, usuniecia, kolizje; domyslna odmowa.
 7. Dowod i statusy: PASS wymaga artefaktu, testow i niezaleznego odczytu; statusy (PASS, FAIL, BLOCK, INFRA, TIMEOUT, ZWIS, DECISION_REQUIRED...); BLOCK dopiero po wyczerpaniu petli naprawczej; czas ISO-8601 UTC albo TIMESTAMP_UNVERIFIED; ponowny SHA-256 po korekcie i SUPERSEDED; hashe per plik (nie zbiorcze).
 8. Delegowanie: zlecenie czterema polami (zadanie, regula przeciw samooszukiwaniu, binarne kryterium, procedura naprawcza); wezly i najmniejszy skuteczny graf; sprawdzenie pisze inny wezel niz wykonanie.
 9. Decyzje: ABC/ECHO (co rozstrzyga wlasciciel, co orkiestrator; format pytania z dwoma za i dwoma przeciw; test zrozumialosci; ECHO dopiero po jednoznacznej odpowiedzi; ODCZYT ORKIESTRATORA przy niejednoznacznosci).
 10. Dyscyplina zrodel (rzedy 1-5, korygowanie wlasnych bledow) i dyscyplina zakresu (nie gonimy parytetu, lista rzeczy, ktorych nie robimy).
 11. Raporty: kontrakt raportu terminalnego (pola, limit objetosci, destylat); raport Evaluatora, Obrony, Final Control, Integration.
 12. Pliki trwalej prawdy i miejsca zapisu (co gdzie trafia); zmiana samego procesu (tylko osobny temat PROCES, niezalezny Evaluator, Final Control i ECHO — R11).
 13. Uczciwy model kontroli (R6), kontynuacja po wyniku terminalnym (R7), reguly R1-R12 z najnowszego zestawu — kazda z odnosnikiem do zrodla (plik i linia).
 14. Czego NIE przejmujemy (z uzasadnieniem): autonomiczne dzialania live, elementy OpenClaw, zuzycie tokenow per faza, nazewnictwo A-main/B i 10 modulow.
CZESC II — LOKALNE WYPELNIENIE DLA ZERO: parametry (z `autobot/WYBORY_TRWALE.md`: limit rund 3, pula 2, raport 400 slow, modele, ZWIS, jezyk, miejsce pracy, baza, integracja); granice G1-G7; lista rzeczy, ktorych swiadomie nie robimy; kolejnosc plikow startowych i odwzorowanie pojec; zakres zgody na dzialania zewnetrzne (obowiazuje ECHO-004; PUNKT OTWARTY: ECHO-017 pkt 3 — wpisz jawnie jako otwarty); lista decyzji procesowych ECHO-010..ECHO-018 z jednozdaniowym skutkiem; znane pulapki tego projektu (np. subagent odpowiadajacy na wiadomosc uzytkownika z kontekstu sesji zamiast na zlecenie; hash zbiorczy zamiast per plik; nieaktualizowany licznik rund w rejestrze; blokady sieci dostawcow; restart kontenera; niecommitowanie niezatwierdzonych wytworow).
CZESC III — SZABLONY: zapis zlecenia, zlecenie dla wykonawcy (4 pola), pytanie ABC, wpis ECHO, raport terminalny.
CZESC IV — ODWZOROWANIE NA WORKFLOW ZERO I WYMAGANE ZMIANY: dla kazdej reguly: czy dziala w skrypcie `zero-autobot-v2` (obrona, FC per zarzut, Integration, hashe per plik, tryb wezlow), czy wymaga zmiany, czy niewykonalna w srodowisku (np. czas UTC — skrypt nie ma dostepu do daty); lista konkretnych zmian w `autobot/00_PUNKT_STARTOWY.md`, `autobot/WYBORY_TRWALE.md`, `autobot/REJESTR_TEMATOW.md` i skrypcie — BEZ wykonywania tych zmian (osobne tematy).

ZRODLA (hierarchia: oryginalny tekst rzad 1; inwentarz rzad 2; ustalenia wlasciciela ECHO najwyzsze dla zakresu ZERO):
 (a) obecnie obowiazujacy skill sesji (reguly pracy, dodatki A i B, szablony), tylko odczyt: `/root/.claude/skills/synced/a8b5d1c2-8fcc-4315-8ad2-e24d641c1f99_6ffe6d7a-cafc-4ff9-b7d6-6e69485369af/autobot/SKILL.md`;
 (b) paczka v2: `/tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/autobot-zip/` (tylko odczyt);
 (c) ORYGINAL najnowszego zestawu: swieza ekstrakcja `/root/.claude/uploads/3337db06-529b-5b00-81d6-a0a7013a451d/a4edf6ca-Autobot.rar` (unrar x do NOWEGO pustego katalogu w scratchpadzie): `autobot-skills/skills/autobot-orchestrator/references/autobot-reference-contract.md` i skille tego zestawu;
 (d) inwentarz (tylko odczyt): `docs/proces/ZERO-PROCES-002-inwentarz-zasad-autobot/inwentarz.md`, sekcje 2, 4, 5, 6;
 (e) decyzje i lokalne dokumenty: `autobot/DECYZJE.md` (ECHO-010..018), `autobot/WYBORY_TRWALE.md`, `autobot/00_PUNKT_STARTOWY.md`, `autobot/REJESTR_TEMATOW.md` (tylko odczyt).

REGULA PRZECIW SAMOOSZUKIWANIU:
- Zakaz skracania regul do odsylaczy ("patrz inwentarz", "jak w v2"): kazda regula ma pelna tresc w dokumencie.
- Zakaz parafrazowania reguly z oryginalu bez odnosnika (plik i linia) zweryfikowanego na ORYGINALE; zakaz opierania sie wylacznie na inwentarzu.
- Zakaz przejecia regul wykluczonych i nazewnictwa A-main/B.
- Zakaz oslabienia regul roli orkiestratora (sekcja 4) i zakaz poszerzania zakresu zgody na publikacje ponad ECHO-004 (punkt otwarty wpisz jako otwarty).
- Zakaz wpisywania historii tego projektu do czesci I (historia i pulapki tylko w czesci II).
- Zakaz uruchamiania skryptow z archiwum; zakaz modyfikowania archiwum i oryginalow w uploads; zakaz edycji istniejacych plikow `autobot/`.
- Zakaz uznania odwzorowania na workflow za zgodne bez przeczytania skryptu `/tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/workflows/zero-autobot-v2.js` (tylko odczyt).
- Pisz plik etapami (kilka dopisan), aby uniknac przeciazenia odpowiedzi.

PROCEDURA NAPRAWCZA PRZY FAIL: Evaluator numeruje zarzuty (sekcja dokumentu, regula, linia zrodla, reprodukcja). Operator (w obronie) odpowiada PRZYJMUJE/ODRZUCAM z dowodem; po werdykcie NAPRAW poprawia tylko wskazane reguly.

ALLOWLISTA:
  - `autobot/ZASADY_PROCESU.md` (nowy plik)
ZAKAZANE BEZWZGLEDNIE: istniejace pliki `autobot/` (00_PUNKT_STARTOWY, WYBORY_TRWALE, DECYZJE, SCENARIUSZE, REJESTR_TEMATOW, PRZEKAZANIE, zlecenia), `scenariusze/`, `docs/`, uploads, skrypt workflow, git zmieniajacy stan (poza rola Integration), sekrety.

MIEJSCE PRACY: `autobot/ZASADY_PROCESU.md`
BAZA:          HEAD galezi roboczej
OBIEG:         Operator -> Evaluator (10 punktow) -> Obrona przy zarzutach -> Final Control (per zarzut) -> Integration

RUNDA: w kolejce, pierwszenstwo za badaniami (ECHO-018); rundy 1-3 z 3; licznik w rejestrze aktualizuje orkiestrator po zakonczeniu workflow
