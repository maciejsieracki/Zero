# ZERO-PROCES-002-inwentarz-zasad-autobot — inwentarz zestawow zasad AutoBot

Runda: 3 z 3. Rola autora: Operator (wytwor do niezaleznej oceny; nie jest to akceptacja). Runda 3: werdykty NAPRAW P-2-1 (rejestr tematow i licznik rund w zapisie zlecenia — Orkiestrator) i P-2-2 (zakres kontroli Evaluatora — Evaluator) leza poza allowlista Operatora; tresc merytoryczna inwentarza bez zmian wzgledem rundy 2, ponownie potwierdzono hashe zrodel (sekcja 9). Runda 2 poprawila wylacznie zakres werdyktow NAPRAW E-1-1 (numery linii controllera v2: tabela 1 wiersz h, sekcja 3.h), E-1-2 (roznice rol v2 vs f: sekcja 2, 3.h, 4, 6) i E-1-3 (numer linii w 3.d). P-1-1 dotyczy rejestru Orkiestratora (poza allowlista).
Data wykonania: 2026-11-27 (czas sesji). Nic nie zostalo skasowane ani zmienione w zrodlach; kasuje wylacznie wlasciciel (ECHO-010).

GOAL: Istnieje zweryfikowany inwentarz wszystkich zestawow zasad AutoBot (Autobot.rar, paczka v2 z 2026-09-16, wersja z listy umiejetnosci sesji): dla kazdego data, wersja, zakres, czy definiuje obrone i osobna role Integration, status i rekomendacja usuniecia lub zachowania, oraz wskazanie najnowszego zestawu z obrona i roznic wzgledem v2.

---

## 0. Metoda i dowody wykonania

### 0.1 Zrodla (tylko odczyt)

| Zrodlo | Sciezka | SHA-256 (przed i po pracy) |
|---|---|---|
| Autobot.rar | `/root/.claude/uploads/3337db06-529b-5b00-81d6-a0a7013a451d/a4edf6ca-Autobot.rar` | `8d0b81b432030baa7499c5868d386b7c6866c0379ead94c16c4b77cea3c51eb5` |
| Paczka v2 (oryginal) | `/root/.claude/uploads/3337db06-529b-5b00-81d6-a0a7013a451d/93c21342-autobot-universal-skills-2026-09-16-v2.zip` | `76f58a584e215099f144d5cfe65e026632cf110f4abaacfa7723f187aff2a83d` |
| Wersja z listy umiejetnosci sesji | `/root/.claude/skills/synced/a8b5d1c2-8fcc-4315-8ad2-e24d641c1f99_6ffe6d7a-cafc-4ff9-b7d6-6e69485369af/autobot/SKILL.md` | `cee845edec45a55dc8a08b818b32b091400e71f992a716181617ced5bc6ff609` |

Hash archiwow policzony na poczatku i ponownie na koncu pracy (sekcja 9) — identyczny.

### 0.2 Katalogi robocze (nowe, puste przed ekstrakcja; poza repozytorium)

- `/tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/p002-rar/` — `unrar x -o- <Autobot.rar>`; wynik: 62 wpisy (42 pliki + 20 katalogow), zgodnie z `unrar l`.
- `/tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/p002-zip/` — `unzip -q p002-rar/autobot-skills.zip`; wynik: 14 plikow.
- Paczka v2: odczyt z istniejacego `scratchpad/autobot-zip/` (tylko odczyt). Zgodnosc z oryginalem sprawdzona niezaleznie: `unzip -p <oryginal> <plik> | sha256sum` vs `sha256sum scratchpad/autobot-zip/<plik>` — 7/7 plikow zgodnych.

### 0.3 Porownanie `autobot-skills.zip` z folderem `autobot-skills/` w archiwum

Polecenie: dla kazdego pliku z p002-zip `sha256sum` vs ten sam plik w `p002-rar/autobot-skills/`. Wynik: **14/14 bajtowo identycznych** (np. `autobot-orchestrator/SKILL.md` = `6e8e071694bd1a51…` w obu; `autobot-reference-contract.md` = `2b531cf9f5fbb5ed…` w obu). Roznica tylko w mtime wpisow ZIP (przesuniecie +2 h = strefa czasu zapisu, np. orchestrator 12:40 w ZIP vs 10:40 w RAR). Wniosek: `autobot-skills.zip` jest duplikatem folderu `autobot-skills/`.

### 0.4 Uzyte polecenia potwierdzajace obecnosc/brak obrony i Integration

Dla kazdego pliku tekstowego:
`grep -c -i -E 'defen[cs]e|obron' <plik>` oraz `grep -c -i -E 'integration' <plik>`, a dla trafien `grep -n -i -E 'defen[cs]e|obron|integration' <plik>` (cytaty z numerami linii ponizej). Wynik zerowy = potwierdzony brak.

### 0.5 Bezpieczenstwo

Nie uruchomiono zadnego skryptu z archiwum (.sh, .py, testy, demo) ani nie importowano modulow. Pliki odczytano jako tekst (`cat -n`, `grep`, `diff`, `sha256sum`); jedyny kod Pythona to wlasne jednolinijkowe parsowanie `runs.jsonl` przez `python3 -I -c` (json.loads, bez importu pakietu z archiwum). Pliki `.pyc` nie byly ani uruchamiane, ani czytane (binarne). Raport nie zawiera sekretow (archiwum ich nie zawiera: `grep -n -i -E 'token|password|haslo|hasło|secret|api[_-]?key'` na danych = brak trafien).

---

## 1. Zestawienie zbiorcze (dziewiec zestawow a–i)

Legenda: Obrona = czy zdefiniowana rola/faza Defense (obrona Operatora wobec zarzutow). Integration = czy osobna rola Integration. mtime = data pliku w archiwum (poszlaka); "w tresci" = data/wersja zapisana w samym tekscie (rozstrzyga razem z trescia).

| # | Zestaw | mtime | Wersja / data w tresci | Obrona | Osobna Integration | Checklista Evaluatora | Receipts | Status | Rekomendacja |
|---|---|---|---|---|---|---|---|---|---|
| a | `autobotSKILL.md` (skill `lean-loop`) | 2026-08-08 16:27 | brak wersji, brak daty | NIE (grep pusty) | NIE (grep pusty) | brak numerowanej; przeglad dwuosiowy SCOPE/bloat | NIE (grep pusty) | PRZESTARZALY BEZ OBRONY | USUNAC |
| b | `civautobotSKILL.md` (nakladka Civ "The Game") | 2026-08-08 16:27 | `Maciej 2026-08-08` (l. 43, 115); brak wersji | NIE (jedyne trafienie l. 105 to parametr gry) | NIE (grep pusty) | 3 twarde FAIL projektowe (#7–#9) + bazowe STRICT | NIE (grep pusty) | PRZESTARZALY BEZ OBRONY (nakladka innego repozytorium) | USUNAC |
| c | `AutoBot-Orkiestrator-SKILL.md` | 2026-09-17 19:24 | `version: 1.0.0` (l. 4) | NIE jako rola — tylko nazwa fazy `defense` (l. 126) | TAK (l. 30, 117) | brak | TAK (l. 45, 85, 108) | ZASTAPIONY | USUNAC |
| d | `AutoBot-Orkiestrator-v1.1.0-SKILL.md` | 2026-09-17 19:27 | `version: "1.1.0"` (l. 4), "scalona wersja kanoniczna" (l. 10) | TAK (l. 60, 176–180, 311, 329–331) | TAK (l. 177–178, 335–342) | 10 pkt przez referencje (l. 329); referencji brak obok pliku | TAK (12 trafien) | ZASTAPIONY | USUNAC |
| e | pakiet Pythona `autobot/` | 2026-08-06 19:32–19:37 | `__version__ = "1.0.0"` (`__init__.py` l. 10) | NIE (jedyne trafienie `README.md` l. 47 to "obrone" reguly w playbooku, nie rola) | NIE (grep pusty) | nie dotyczy (Evaluator = funkcja liczaca metryke) | NIE | NIE DOTYCZY (implementacja, nie zestaw zasad procesu) | NIE DOTYCZY (szczegoly per plik: sekcja 3.e) |
| f | `autobot-skills/` (10 skilli + 4 referencje) i `autobot-skills.zip` | pliki 2026-09-20 … 2026-10-08; zip 2026-10-20; katalogi 2026-10-24 | orchestrator `2.0.0`, project `2.0.0`, heartbeat `1.1.0`, pozostale `1.0.0`; "superseded 2026-10-03" (FAILURE-PATTERNS l. 3) | TAK (reference-contract l. 105, 240–251; orchestrator l. 81) | TAK (reference-contract l. 107–108, 266–277; controller l. 46) | 10 pkt (reference-contract l. 279–315) | TAK (22 trafienia w reference-contract; l. 395–401, 498–508) | **NAJNOWSZY Z OBRONA** | ZACHOWAC (zip jako duplikat: USUNAC jeden z dwoch) |
| g | `skasujzmergowanegalezieautobot.sh` | 2026-08-26 15:22 | "Wygenerowane 2026-08-26" (l. 3) | NIE (grep pusty) | NIE (grep pusty) | nie dotyczy | nie dotyczy | NIE DOTYCZY (jednorazowy skrypt operacyjny, nie zasady) | USUNAC |
| h | paczka v2 z 2026-09-16 (`autobot-universal-skills-2026-09-16-v2.zip`) | 2026-09-16 16:31 (wszystkie pliki) | "wydanie v2" (README l. 1); "Data: 2026-09-16" (test report l. 3); brak pola version w SKILL.md | TAK (controller l. 18, 99, 102, 226, 238–240; reference l. 57, 185–196) | TAK (controller l. 18, 244–248; reference l. 59–60, 211–222) | 10 pkt (reference l. 224–260) | TAK (16 trafien w reference) | ZASTAPIONY (obowiazuje w ZERO tymczasowo wg ECHO-010) | ZACHOWAC do decyzji przejmujacej nowszy zestaw, potem USUNAC (szczegoly 3.h) |
| i | wersja z listy umiejetnosci sesji (`autobot/SKILL.md`) | 2026-11-27 07:23 (czas synchronizacji do sesji, nie data tresci) | brak wersji, brak daty w tresci (`grep -n -o -E '20[0-9]{2}-[0-9]{2}-[0-9]{2}'` = pusty) | NIE (grep pusty) | NIE — wlaczanie robi Orkiestrator (l. 87–88, 122–124) | 10 pkt (l. 95–110) + 7 pkt Final Control (l. 111–120) | NIE (grep pusty) | AKTUALNY (aktywny w sesji; bez obrony) | ZACHOWAC (poza archiwum; uzupelnic regulami z sekcji 6 osobna decyzja) |

---

## 2. Wskazanie najnowszego zestawu z obrona

**Najnowszy zestaw z obrona: f — `autobot-skills/` (router `autobot-orchestrator` 2.0.0 + referencja `autobot-reference-contract.md`).** Zawartosc `autobot-skills.zip` jest bajtowo identyczna (0.3), wiec to jeden zestaw w dwoch kopiach.

Uzasadnienie datami (poszlaka):
- najmlodsze mtime plikow regul ze wszystkich zestawow z obrona: orchestrator `SKILL.md` 2026-10-03 10:40, reference-contract 2026-10-03 02:15, heartbeat 2026-10-08 15:33; zip 2026-10-20; katalogi 2026-10-24. Dla porownania: v2 = 2026-09-16, v1.1.0 = 2026-09-17.
- data w tresci: `MAIN-AGENT-ORCHESTRATOR-FAILURE-PATTERNS.md` l. 3: "recorded: 2026-09-20 | status: historical; paired-session routing superseded 2026-10-03" — wskazuje zmiane modelu z 2026-10-03, zgodna z mtime routera.
- data w sesji (zestaw i) nie jest data tresci: mtime 07:23 2026-11-27 = moment synchronizacji do tej sesji; tresc nie ma daty ani wersji.

Uzasadnienie trescia (rozstrzyga):
- Wersje: router `version: "2.0.0"` (orchestrator l. 4) wobec `1.0.0` (zestaw c, l. 4) i `"1.1.0"` (zestaw d, l. 4); `autobot-project` `version: "2.0.0"` (l. 4) wobec braku wersji w v2.
- Odwolanie do poprzednikow: orchestrator l. 152–154: "Przy konflikcie treści obowiązuje aktualny router, skille domenowe i referencja kontraktu. Historyczne snapshoty nie są aktywnymi źródłami i nie pozostają w pakiecie produkcyjnym." oraz l. 49–50: "Archiwa służą wyłącznie do audytu i nie są aktywnymi źródłami procedury."
- Tresc (prawie nadzbior, z wyjatkami w rolach): `diff` v2 `autobot-reference-contract.md` vs nowsza referencja (`diff <v2-ref> <f-ref> | grep -E '^[0-9]'` = 13 hunkow: 2c2,6; 5c9; 24a29,38; 39a54,83; 43c87; 50,55c94,103; 64,66c112,118; 131c183; 133,143c185,198; 264c319,347; 267a351,402; 394a530,543; 421a571,607). Bez zmian w f wystepuja: checklista 5, werdykty 6, przejscia 7, bezpieczenstwo 8, ABC/ECHO 9, receipts 10, raporty 11, zrodla 12 oraz kontrakty Operator/Evaluator/Defense/Final Control/Integration. **Sekcja rol 4 NIE jest bez zmian** — f usuwa lub zmienia nastepujace reguly v2 (szczegoly i cytaty: sekcja 4, wiersze "Role — Orkiestrator: kontrakt" i "Role — eskalacja subagenta"):
  - opis ról Orkiestrator/Wykonawca (v2 l. 50–55) zastapiony A-main/B/Wykonawca (f l. 94–103);
  - regula eskalacji subagenta (v2 l. 64–66: "Sub-agent nie prowadzi bezpośrednich rozstrzygnięć z człowiekiem; wraca do Wykonawcy, Orkiestratora, a dopiero potem do właściciela.") usunieta i zastapiona niezaleznoscia agentow i bezposrednia odpowiedzia A-main (f l. 112–118);
  - kontrakt `### Orkiestrator` (v2 l. 131–143, m.in. l. 137 "integrację i jako jedyny zapisuje READY_FOR_DEPLOY", l. 139 "nie publikuje bez zgody") zastapiony kontraktem `### A-main (koordynator)` (f l. 183–198, m.in. l. 190 "podejmuje decyzje techniczne w granicach kontraktu", l. 193–194 "nie publikuje ani nie zmienia live bez wymaganej zgody"), bez zdania o wylacznym zapisie READY_FOR_DEPLOY i bez "autoryzuje/akceptuje integrację".
  Pozostale zmiany v2 -> f: naglowek i nazwa modulu (2c2,6; 5c9; 43c87) oraz jednozdaniowe statusowanie (v2 l. 264) zastapione rozszerzonym (f l. 319). Dodane sa: blok `autonomy`/`localLoop` (l. 29–37), mapa pamieci (l. 54–83), A-main/B (l. 94–118), AB-T-001…AB-T-011, AB-M-001, AB-H-001/002, AB-L-001 (l. 323–393), minimalny terminal receipt (l. 395–401), TR-001…TR-010 (l. 530–542), sekcja 13 o module Controller (l. 572–607).
- Linia rozwoju: v2 controller `SKILL.md` -> v1.1.0 Orkiestrator: `diff` pokazuje tylko dodatki (granica odpowiedzialnosci, orkiestracja rownolegla, mapa pamieci OpenClaw, akapit o sessions_spawn, akapit o `interrupted`) i zmiane nazwy; zadnej usunietej reguly. v1.1.0 -> router 2.0.0: rozbicie na 10 entrypointow (orchestrator l. 38–47) z referencja wspolna.

Niezgodnosci wewnetrzne zestawu f (do wiadomosci, nie podwazaja wskazania):
1. Referencja ma dwie sekcje oznaczone `## 6.` (l. 317 "Statusowanie i watchdog", l. 403 "Werdykty, rundy i statusy") — ten sam blad byl w v2 (l. 262, 268).
2. FAILURE-PATTERNS: naglowek l. 3 "status: historical", a stopka l. 218 "**Status dokumentu:** aktywny materiał szkoleniowy".
3. Heartbeat l. 9 jest przypisany do jednego srodowiska: "W workspace 8gent ten plik jest kanoniczną instrukcją dla heartbeatów".
4. Router l. 154 deklaruje, ze historyczne snapshoty "nie pozostają w pakiecie produkcyjnym", a archiwum Autobot.rar nadal zawiera zestawy c i d.
5. Referencja f nie definiuje juz roli "Orkiestrator" (lista ról l. 94–103 i kontrakt l. 183 to A-main), ale kontrakt Integration nadal sie do niej odwoluje: l. 268 "autoryzacja Orkiestratora", l. 276–277 "Tylko Orkiestrator akceptuje pierwszy wynik i zapisuje READY_FOR_DEPLOY." Wylacznosc zapisu READY_FOR_DEPLOY przetrwala wiec tylko w kontrakcie Integration, nie w kontrakcie koordynatora.

---

## 3. Karty zestawow

### 3.a `autobotSKILL.md` — skill `lean-loop`

- Pliki: 1 (`autobotSKILL.md`, 269 linii, SHA-256 `b7ce490ca5181042…`). Przeczytany w calosci.
- Data: mtime 2026-08-08 16:27; w tresci brak wersji i daty.
- Zakres: uniwersalna dyscyplina inzynierska "Lean Loop" (l. 2 `name: lean-loop`): drabina decyzyjna przed kodem (l. 82–98), reguly budowania (l. 112–127), samoocena zakazana i przeglad zewnetrzny (l. 162–207), 5-krokowy protokol bledu (l. 209–230). Nie jest procesem Operator/Evaluator/Final Control.
- Role: brak rol procesu; przeglad niezalezny "subagent, a second model, a colleague" (l. 179–180).
- Obrona: NIE — `grep -c -i -E 'defen[cs]e|obron'` = 0. Integration: NIE — `grep -c -i -E 'integration'` = 0.
- Checklista Evaluatora: brak numerowanej; osie Scope (SCOPE / DIFF-MINIMAL / NO-REGRESSION / COUPLING) i Bloat (l. 192–202); werdykt PASS / PASS-WITH-NOTES / FAIL (l. 204).
- Receipts: NIE (grep `receipt` = 0).
- Nastepca/poprzednik: brak w tresci. Odsyla do nieobecnych w archiwum plikow `references/review-pass.md`, `references/error-protocol.md`, `references/playbook-pattern.md`, `references/high-stakes.md`, `references/writing-checklist.md` (l. 73–80) — zestaw niekompletny.
- Status: PRZESTARZALY BEZ OBRONY.
- Rekomendacja: **USUNAC** (z archiwum zasad AutoBot). Uzasadnienie: brak obrony i Integration, niekompletny (brakuje 5 referencji), najstarszy obok b; jego uzyteczne reguly (przeliczaj kazda liczbe od zera l. 120, raportuj rozbieznosci l. 121, sprawdzaj date i wersje zrodla l. 122) sa juz obecne w procesie ZERO (hierarchia zrodel w `autobot/00_PUNKT_STARTOWY.md`, regula "liczy/sprawdza od zera" w zestawie i l. 95–96). Zastrzezenie: jesli wlasciciel uzywa `lean-loop` jako osobnego skilla poza AutoBot, jego kanoniczna kopia powinna zyc tam — to nie jest przedmiot tego inwentarza.

### 3.b `civautobotSKILL.md` — nakladka Civ "The Game"

- Pliki: 1 (273 linie, SHA-256 `fd1f90877fab5dd8…`). Przeczytany w calosci.
- Data: mtime 2026-08-08 16:27; w tresci: "`R-SKILL-LEAN-LOOP-CIVAUTOBOT=B`, Maciej 2026-08-08" (l. 42–43) i "Maciej 2026-08-08" (l. 115). Brak wersji.
- Zakres: projektowa nakladka na `lean-loop` dla innego repozytorium (l. 4: "Nakładka projektowa Civ „The Game" na uniwersalny skill `lean-loop`"; l. 21: "NIE używaj do zadań spoza tego repozytorium."). Zalezy od zestawu a (l. 26–29).
- Role: Operator -> Evaluator -> final (l. 34), przydzial modeli Sonnet 5 / Opus 5 (l. 74–82), turniej ABC z Proponentami i Sedzia (l. 112–136).
- Obrona: NIE. Jedyne trafienie `grep -n -i -E 'defen[cs]e|obron'`: l. 105 "Praca / Prawo / Pieniądz / Zadowolenie / Obrona)" — to parametr rozgrywki, nie rola procesu. Integration: NIE (grep = 0).
- Checklista Evaluatora: trzy twarde FAIL domenowe #7–#9 (l. 144–146) + bazowe FAIL STRICT (l. 148–152); brak numerowanej listy 10 punktow.
- Receipts: NIE (grep = 0).
- Nastepca/poprzednik: brak.
- Status: PRZESTARZALY BEZ OBRONY (i specyficzny dla innego projektu).
- Rekomendacja: **USUNAC** (z archiwum zasad AutoBot). Uzasadnienie: brak obrony i Integration; tresc dotyczy wylacznie repozytorium gry (sciezki `gra/src`, `dyspozycje/…`), w ZERO nie ma zastosowania. Zastrzezenie: jesli projekt Civ jest aktywny, kanoniczna kopia nakladki powinna byc w jego repozytorium.

### 3.c `AutoBot-Orkiestrator-SKILL.md` — v1.0.0

- Pliki: 1 (177 linii, SHA-256 `8f3efd7f7f027af5…`). Przeczytany w calosci.
- Data: mtime 2026-09-17 19:24; w tresci `version: 1.0.0` (l. 4).
- Zakres: orkiestracja programu: hierarchia odpowiedzialnosci (l. 23–30), pamiec i zrodla prawdy (l. 32–63), otwarcie projektu, dispatch, rownoleglosc (limit 3, l. 95), wykonanie i kontrola, statusy, retry, rekoncyliacja, bezpieczenstwo.
- Role: glowny czat, Orkiestrator, Wykonawca, Evaluator, Final Control, Integration (l. 25–30).
- Obrona: NIE jako rola. `grep -n -i -E 'defen[cs]e|obron'` daje jedynie l. 126: "- `phase`: `operator`, `evaluator`, `defense`, `final-control`, `integration`;" — faza wymieniona w statusie, bez kontraktu (kto, co, PRZYJMUJE/ODRZUCAM); hierarchia l. 25–30 nie zawiera Defense.
- Integration: TAK — l. 30: "6. Integration scala dopiero po przejściu kontroli i readbacku."; l. 117: "5. Integration dopiero po potwierdzeniu wszystkich dowodów."
- Checklista Evaluatora: brak (grep `checklist` = 0).
- Receipts: TAK (l. 45, 85, 108).
- Nastepca: zestaw d z tego samego dnia (3 minuty pozniej), ktory dodaje kontrakt Defense; dalej zestaw f.
- Status: ZASTAPIONY.
- Rekomendacja: **USUNAC**. Uzasadnienie: bez zdefiniowanej obrony (tylko nazwa fazy), wszystkie jego reguly sa w f (np. limit 3 = reference-contract l. 594–596; "PASS wymaga artefaktu, testu i readbacku" l. 120 = reference-contract l. 349).

### 3.d `AutoBot-Orkiestrator-v1.1.0-SKILL.md` — v1.1.0

- Pliki: 1 (376 linii, SHA-256 `626eeb5308a843ab…`). Przeczytany w calosci.
- Data: mtime 2026-09-17 19:27; w tresci `version: "1.1.0"` (l. 4), l. 10: "> Wersja 1.1.0 — scalona wersja kanoniczna: AutoBot Controller + parallel-project-orchestration + routing pamięci."
- Zakres: v2 `autobot-controller/SKILL.md` + dodatki (porownanie `diff`: tylko dodane bloki l. 17–54, 102–137, 282–288, 319–324 i zmiana nazwy w l. 2–10).
- Role: Orkiestrator, Wykonawca, Operator, Evaluator, Defense, Final Control, Integration (l. 57–61).
- Obrona: TAK — l. 59–60 "zleca istniejące role procesu: Operatora, Evaluator, Defense, Final Control i Integration"; l. 177–178 "Defense odpowiada na każdy zarzut; Final Control rozstrzyga"; l. 311 "Obieg jest: Operator → Evaluator → Defense (tylko przy zarzutach) →"; l. 329–331 "Defense odpowiada na każdy zarzut osobno PRZYJMUJĘ/ODRZUCAM z dowodem; brak odpowiedzi oznacza PRZYJMUJĘ."
- Integration: TAK — l. 335: "Integration ma osobny kontrakt: używa wyłącznie zatwierdzonej allowlisty,"; l. 339–340: "Integration nie może sama zmienić zakresu, autoryzacji, statusu ani wykonać push/merge/deploy."
- Checklista Evaluatora: odeslanie "pełną mierzalną checklistę z referencji" (l. 328–329) do `references/autobot-reference-contract.md` (l. 142), ktorej w archiwum obok tego pliku nie ma (jest tylko w f i w v2).
- Receipts: TAK (12 trafien, np. l. 272, 309).
- Nastepca: router f 2.0.0 (ta sama nazwa `autobot-orchestrator`, wyzsza wersja; f l. 152–154 o historycznych snapshotach).
- Status: ZASTAPIONY.
- Rekomendacja: **USUNAC**. Uzasadnienie: kazda regula v1.1.0 jest w f (kontrakty rol reference-contract l. 183–277, przejscia l. 449–459, dostarczanie plikow evidence l. 26–27 i router l. 132–133); osamotniony plik odsyla do nieobecnej referencji.

### 3.e Pakiet Pythona `autobot/` — implementacja, nie zasady

- Pliki (sklasyfikowane osobno):

| Plik | Linie | SHA-256 (16) | Odczyt | Co to jest | Rekomendacja |
|---|---|---|---|---|---|
| `autobot/README.md` | 122 | `ead619621ad49b91` | w calosci | opis biblioteki "Samodoskonalący się agent w architekturze **Evaluator–Operator**" (l. 3) | NIE DOTYCZY |
| `autobot/autobot/__init__.py` | 14 | `bbf6b76da28ef3c5` | w calosci | eksport API, `__version__ = "1.0.0"` (l. 10) | NIE DOTYCZY |
| `autobot/autobot/types.py` | 116 | `e96ff599817c6b62` | w calosci | `Rule`, `ExecutionRun`, `EvaluationResult` | NIE DOTYCZY |
| `autobot/autobot/playbook.py` | 131 | `79efbb4352a10522` | w calosci | playbook regul, progi RETIRED 0,30 / QUARANTINE 0,45 / min. 5 prob | NIE DOTYCZY |
| `autobot/autobot/guardrails.py` | 85 | `5fc2f5c1b045b2de` | w calosci | bariery w kodzie: `FORBIDDEN_ACTIONS` (l. 13), `REQUIRES_APPROVAL` (l. 20), proba >= 30 i 48 h | NIE DOTYCZY |
| `autobot/autobot/operator.py` | 53 | `1ff0c87cc2b2fa92` | w calosci | wykonanie akcji przez bramke | NIE DOTYCZY |
| `autobot/autobot/evaluator.py` | 139 | `9c8925784f3cceaa` | w calosci | ocena twarda metryka; l. 23 "Rozdzielony od Operatora celowo" | NIE DOTYCZY |
| `autobot/autobot/optimizer.py` | 94 | `109698e3b41ff365` | w calosci | korelacja Pearsona, pruning cech | NIE DOTYCZY |
| `autobot/autobot/logger.py` | 70 | `62c46d69b7cbd3ff` | w calosci | log JSONL | NIE DOTYCZY |
| `autobot/demo_montazowa.py` | 126 | `68b0e19b68651711` | w calosci, NIE uruchomiony | demo kampanii sprzedazowej (symulacja CRM) | NIE DOTYCZY |
| `autobot/tests/test_autobot.py` | 224 | `871fc8c1f5552c09` | w calosci, NIE uruchomiony | testy jednostkowe | NIE DOTYCZY |
| `autobot/data/playbook.json` | 88 | `04a888da5716b8ba` | w calosci | wynik demo (5 regul, 1 RETIRED) | NIE DOTYCZY |
| `autobot/data/runs.jsonl` | 88 rekordow | `3f41213c09eac86c` | jawnie pominiety jako dane uruchomien; zweryfikowany strukturalnie (88 rekordow: EXECUTION, EVALUATION, OPTIMIZATION, BLOCKED; bez sekretow) | log demo | NIE DOTYCZY (nie przeczytany doslownie w calosci — bez rekomendacji USUNAC) |
| `autobot/autobot/__pycache__/*.cpython-310.pyc` (8 plikow) i `autobot/tests/__pycache__/test_autobot.cpython-310.pyc` (1) | binarne | sekcja 8 | jawnie pominiete: artefakty kompilacji `__pycache__`, nie czytane i nie uruchamiane | pochodne plikow .py | NIE DOTYCZY |

- Data: mtime 2026-08-06 19:32–19:37; wersja w tresci `1.0.0`.
- Zakres: biblioteka (kod) uczaca sie playbooka regul na metryce zewnetrznej; nie definiuje obiegu Operator -> Evaluator -> Final Control ani rol procesu pracy agentow.
- Obrona: NIE. Jedyne trafienie `grep -n -i -E 'defen[cs]e|obron'` w calym pakiecie: `README.md` l. 47 "reguła odstawiona na zawsze nigdy nie zebrałaby danych na swoją obronę." — to rehabilitacja reguly w playbooku, nie rola Defense. W plikach .py: 0 trafien. Integration: NIE (0 trafien we wszystkich plikach pakietu).
- Status: NIE DOTYCZY (implementacja, nie zestaw zasad). Rekomendacja: NIE DOTYCZY — kryterium "przestarzaly bez obrony" go nie obejmuje; ewentualne usuniecie to osobny wybor wlasciciela (pakiet zawiera nazwe projektu sprzedazowego i informacje o finansowaniu w `playbook.json` l. 42 — nie sekret, ale tresc biznesowa).

### 3.f `autobot-skills/` (i duplikat `autobot-skills.zip`) — NAJNOWSZY Z OBRONA

- Pliki: 14 + zip (14 tych samych bajtow). Wszystkie przeczytane w calosci.

| Plik | Wersja | mtime | Zakres | Obrona / Integration (cytat) | Rekomendacja |
|---|---|---|---|---|---|
| `skills/autobot-orchestrator/SKILL.md` | 2.0.0 | 2026-10-03 10:40 | router: mapa 10 entrypointow, A-main i subagenci, kolejnosc pracy, petla domkniecia | l. 81–82 "Prowadź obieg Operator → Evaluator → Defense (tylko przy zarzutach) → Final Control → Integration." | ZACHOWAC |
| `skills/autobot-orchestrator/references/autobot-reference-contract.md` | brak pola (referencja routera 2.0.0) | 2026-10-03 02:15 | pelny kontrakt: role, kalibracja, dispatch, checklista 10 pkt, statusy, AB-T-*, receipts, raporty TR-* | l. 105 "**Defense** — formalna obrona Operatora wobec ponumerowanych zarzutów."; l. 107–108 "**Integration** — wykonawca technicznej, autoryzowanej mutacji i kontroli stanu po integracji." | ZACHOWAC |
| `skills/autobot-orchestrator/references/MAIN-AGENT-ORCHESTRATOR-FAILURE-PATTERNS.md` | DOC-MA-ORCH-FAILURES-001 | 2026-10-03 02:15 | retrospektywa ERR-MA-001…012, algorytm MA-CTRL-000…004 | Obrona: 0 trafien; Integration l. 114 "Integration mutuje zatwierdzony zakres." | ZACHOWAC (material szkoleniowy) |
| `skills/autobot-orchestrator/references/autobot-memory-routing.md` | brak | 2026-09-20 11:19 | mapa pamieci OpenClaw | 0 / 0 | ZACHOWAC |
| `skills/autobot-controller/SKILL.md` | 1.0.0 | 2026-10-03 10:40 | launcher, Task Flow, phase ledger, runtimeMode | Integration l. 46 "9. Integration może mutować wyłącznie zatwierdzony zakres po PASS Final Control;"; Obrona 0 trafien (odsyla do routera) | ZACHOWAC |
| `skills/autobot-dispatch/SKILL.md` | 1.0.0 | 2026-10-03 10:40 | kalibracja, topicId, dispatch, fan-out 3 | 0 / 0 | ZACHOWAC |
| `skills/autobot-evidence/SKILL.md` | 1.0.0 | 2026-09-23 14:47 | dowod, receipts, SHA-256, Evaluator, werdykty FC | Obrona 0 (opisuje werdykty FC l. 19–20); Integration 0 | ZACHOWAC |
| `skills/autobot-heartbeat/SKILL.md` | 1.1.0 | 2026-10-08 15:33 | heartbeat, watcher, dedup CAS | 0 / 0; l. 9 przypisany do workspace "8gent" | ZACHOWAC |
| `skills/autobot-memory/SKILL.md` | 1.0.0 | 2026-09-20 09:32 | klasyfikacja pamieci, `DECYZJA WŁAŚCICIELA WYMAGANA` | 0 / 0 | ZACHOWAC |
| `skills/autobot-memory-routing/SKILL.md` | 1.0.0 | 2026-09-20 11:36 | skill-referencja | 0 / 0 | ZACHOWAC |
| `skills/autobot-project/SKILL.md` | 2.0.0 | 2026-10-02 14:16 | otwarcie i kalibracja projektu | l. 41–42 "Orchestrator → Operator → Evaluator → Defense tylko przy zarzutach → Final Control → Integration" | ZACHOWAC |
| `skills/autobot-project/references/otwarcie-projektu.md` | brak | 2026-09-21 12:37 | formularz 24 pytan kalibracji | l. 272 "C, pełny łańcuch z Defense i Integration — plus: formalna obrona;" | ZACHOWAC |
| `skills/autobot-project-opening/SKILL.md` | 1.0.0 | 2026-09-20 11:36 | skill-referencja | 0 / 0 | ZACHOWAC |
| `skills/autobot-reference-contract/SKILL.md` | 1.0.0 | 2026-09-20 11:36 | skill-referencja | 0 / 0 | ZACHOWAC |
| `autobot-skills.zip` | — | 2026-10-20 18:04 | 14 plikow identycznych bajtowo z folderem (0.3) | jw. | USUNAC jedna z dwoch kopii (zip albo folder); tresc przeczytana w calosci przez folder |

- Role: A-main (koordynator, nie wykonuje pracy merytorycznej), B/subagent, Wykonawca, Operator, Evaluator, Defense, Final Control, Integration, Wlasciciel (reference-contract l. 94–110).
- Checklista Evaluatora: 10 punktow (l. 287–310), CLEAR tylko przy 10 PASS (l. 283–285).
- Receipts: TAK (minimalny terminal receipt l. 395–401; receipts dispatch/launch/link/transition/approval/report/verdict/integration l. 500–508).
- Status: NAJNOWSZY Z OBRONA. Rekomendacja: ZACHOWAC.

### 3.g `skasujzmergowanegalezieautobot.sh` — NIE URUCHOMIONY

- Pliki: 1 (68 linii, SHA-256 `9df2c59f72658b04…`). Przeczytany w calosci, nie uruchomiony.
- Data: mtime 2026-08-26 15:22; w tresci "Wygenerowane 2026-08-26" (l. 3).
- Co robi (opis z tresci): w repozytorium innego projektu (l. 2: "repo maciejsieracki/The-Game") wykonuje `git fetch --prune origin` (l. 7), dla 47 wymienionych galezi `autobot/*` (l. 11–57) sprawdza `git merge-base --is-ancestor "origin/$b" origin/main` (l. 59) i zmergowane dopisuje do listy, niezmergowane pomija z komunikatem (l. 62), nastepnie **kasuje je na zdalnym repozytorium** paczkami po 20: `xargs -n 20 git push origin --delete` (l. 66), po czym ponownie `fetch --prune` (l. 67). Dzialanie nieodwracalne po stronie zdalnej (bez kopii galezi).
- Obrona / Integration: NIE / NIE (grep = 0). Nie jest zestawem zasad.
- Status: NIE DOTYCZY. Rekomendacja: **USUNAC** (z archiwum zasad). Uzasadnienie: jednorazowy skrypt operacyjny dla innego repozytorium sprzed trzech miesiecy; trzymanie go obok zasad grozi przypadkowym uruchomieniem nieodwracalnej operacji.

### 3.h Paczka v2 z 2026-09-16

- Pliki: 7 (+4 wpisy katalogow w ZIP). Wszystkie przeczytane w calosci (otwarcie-projektu v2 przez `diff` z nowsza wersja: v2 jest jej podzbiorem — nowsza dodaje wylacznie l. 3–6 i 21–52 nowszej).

| Plik | Linie | SHA-256 (16) | Zakres | Rekomendacja |
|---|---|---|---|---|
| `README.md` | 22 | `468e91a28b938c47` | opis wydania v2 (l. 1 "wydanie v2"), rozroznienie SMOKE-002 (l. 14) | ZACHOWAC tymczasowo |
| `AUTOBOT-POLICY.md` | 29 | `075bb542ddcd4339` | petla naprawcza, miejsca zapisu, dowod zakonczenia | ZACHOWAC tymczasowo |
| `AUTOBOT-CONTROLLER-TEST-REPORT.md` | 220 | `949979cb78c267f6` | raport testow pluginu z 2026-09-16 (l. 3); dowod, nie zasada | ZACHOWAC (dowod historyczny) |
| `autobot-controller/SKILL.md` | 284 | `5494732d291a3dfe` | sterownik: Orkiestrator + Wykonawca, obieg z Defense, Integration, dostarczanie plikow | ZACHOWAC tymczasowo |
| `autobot-controller/references/autobot-reference-contract.md` | 421 | `3b5e40f1898e93e8` | kontrakt rol i checklisty | ZACHOWAC tymczasowo |
| `autobot-project/SKILL.md` | 252 | `3c4bdedb1f3f08d6` | otwarcie projektu | ZACHOWAC tymczasowo |
| `autobot-project/references/otwarcie-projektu.md` | 379 | `31be6183dc191974` | formularz kalibracji | ZACHOWAC tymczasowo |

- Data: mtime 2026-09-16 16:31; w tresci "Data: 2026-09-16" (test report l. 3); brak pola `version` w obu `SKILL.md`.
- Role: Orkiestrator, Wykonawca, Operator, Evaluator, Defense, Final Control, Integration (reference l. 50–62).
- Obrona: TAK — reference l. 57 "- **Defense** — formalna obrona Operatora wobec ponumerowanych zarzutów."; l. 189–190 "ten sam Operator odpowiada na każdy numer osobno"; controller l. 226 "Obieg jest: Operator → Evaluator → Defense (tylko przy zarzutach) →"; controller l. 238–239 "Defense odpowiada / na każdy zarzut osobno PRZYJMUJĘ/ODRZUCAM z dowodem" (pozostale trafienia `grep -n 'Defense'` w controllerze: l. 18, 99, 102, 241; plik ma 284 linie).
- Integration: TAK — reference l. 59–60; controller l. 244 "Integration ma osobny kontrakt: używa wyłącznie zatwierdzonej allowlisty,"; l. 246–248 "Orkiestrator jako jedyny / autoryzuje zakres, akceptuje integration receipt i zapisuje READY_FOR_DEPLOY; / Integration nie może sama zmienić zakresu, autoryzacji, statusu ani wykonać".
- Checklista Evaluatora: 10 punktow (reference l. 232–255).
- Receipts: TAK (reference l. 365–373).
- Nastepca: v1.1.0 (zestaw d, nadzbior controllera) i f (referencja f zawiera wszystkie sekcje v2 poza zmienionymi regulami rol: eskalacja subagenta v2 l. 64–66 i kontrakt Orkiestratora v2 l. 131–143 — sekcja 2 i 4). Tresc v2 nie wskazuje nastepcy.
- Status: ZASTAPIONY (przez f). W ZERO obowiazuje tymczasowo wg ECHO-010 ("do czasu wyniku inwentaryzacji stosuje zestaw v2 z 2026-09-16 jako najnowszy znany z obrona").
- Rekomendacja: ZACHOWAC do czasu decyzji wlasciciela przejmujacej zestaw f (ECHO-010 pkt 1 przewiduje "kolejna decyzja"); po niej skille v2 mozna USUNAC (przeczytane w calosci), a `AUTOBOT-CONTROLLER-TEST-REPORT.md` zachowac jako dowod historyczny.

### 3.i Wersja z listy umiejetnosci sesji (`autobot/SKILL.md`)

- Plik: 1 (687 linii, SHA-256 `cee845edec45a55d…`). Przeczytany w calosci.
- Data: mtime 2026-11-27 07:23 = synchronizacja do sesji (nie data tresci); w tresci brak daty i wersji (`grep -n -o -E '20[0-9]{2}-[0-9]{2}-[0-9]{2}'` = pusty).
- Zakres: uniwersalny szkielet procesu "nie tylko dla informatyki" (l. 3); parametry `{…}` (l. 8–12), role, petla tematu, allowlista, granice, ABC/ECHO, kontrakt raportu, watchdog, delegowanie, zrodla, Dodatek A (kalibracja), Dodatek B (szablony). Projekt ZERO jest zbudowany wg tego szkieletu (8 funkcji dokumentow l. 536–547).
- Role: Operator, Evaluator, Final Control, Orkiestrator, Wlasciciel (l. 87–127).
- Obrona: NIE — `grep -c -i -E 'defen[cs]e|obron'` = 0; obieg l. 87–88: "Operator → Evaluator → Final Control → włączenie do stanu obowiązującego → READY_FOR_DEPLOY → bramka przekazania na zewnątrz".
- Integration: NIE jako osobna rola — `grep -c -i -E 'integration'` = 0; wlaczenie wykonuje Orkiestrator, l. 122–124: "**Orkiestrator** — prowadzi rozmowę z właścicielem. Włącza do stanu obowiązującego **wyłącznie zatwierdzoną allowlistę**".
- Checklista Evaluatora: 10 punktow (l. 98–110); Final Control 7 punktow (l. 114–120).
- Receipts: NIE (grep = 0).
- Nastepca/poprzednik: brak odwolan.
- Status: AKTUALNY (aktywny w sesji; bez obrony i bez osobnej Integration).
- Rekomendacja: ZACHOWAC — nie jest czescia archiwum Autobot.rar, a dokumenty ZERO opieraja sie na jego Dodatkach A i B. Do uzupelnienia regulami z sekcji 6 (zmiana procesu = osobny temat domeny PROCES i decyzja wlasciciela).

---

## 4. Roznice funkcjonalne: zestaw f wzgledem paczki v2

| Obszar | v2 (2026-09-16) | f (najnowszy) | Cytat f |
|---|---|---|---|
| Role — koordynacja | Orkiestrator (glowny agent) + jeden Wykonawca prowadzacy Task Flow (ref v2 l. 50–54) | A-main koordynuje i nie wykonuje pracy merytorycznej; B = dowolny subagent z ograniczonym zakresem, nie stala sesja; "Orchestrator" to funkcja proceduralna | ref l. 94–97 "**A-main** — … Nie wykonuje merytorycznej pracy zadaniowej."; router l. 32–34 "„Orchestrator” w tym pakiecie oznacza funkcję koordynacyjną/proceduralną, nie osobną sesję B" |
| Role — Orkiestrator: kontrakt | `### Orkiestrator` (ref v2 l. 131–143): "autoryzuje/akceptuje integrację i jako jedyny zapisuje READY_FOR_DEPLOY" (l. 136–137); ZAKAZY "nie wykonuje merytorycznej pracy, którą sam ma oceniać; … nie publikuje bez zgody" (l. 138–139); WYNIK m.in. "eskalacja do człowieka albo autoryzowane READY_FOR_DEPLOY" (l. 143) | `### A-main (koordynator)` (ref l. 183–198): brak autoryzacji/akceptacji integracji i brak wylacznego zapisu READY_FOR_DEPLOY; nowe uprawnienie do decyzji technicznych; zgoda wymagana tez dla zmian live; eskalacja tylko gdy decyzja "konieczna do kontynuacji". Wylacznosc READY_FOR_DEPLOY zostaje tylko w kontrakcie Integration (ref l. 276–277), ktory nadal mowi "Orkiestrator" (niespojnosc, sekcja 2 pkt 5) | ref l. 189–190 "rozlicza / evidence/readback i podejmuje decyzje techniczne w granicach kontraktu."; l. 193–194 "nie publikuje ani nie zmienia / live bez wymaganej zgody."; l. 197–198 "precyzyjna prośba o / decyzję/zgodę tylko wtedy, gdy jest ona konieczna do kontynuacji." |
| Role — eskalacja subagenta | ref v2 l. 64–66: "Sub-agent / nie prowadzi bezpośrednich rozstrzygnięć z człowiekiem; wraca do Wykonawcy, / Orkiestratora, a dopiero potem do właściciela." (tez controller v2 l. 228–230: "DO DECYZJI CZŁOWIEKA najpierw analizuje Wykonawca, potem Orkiestrator; do człowieka trafia tylko nierozstrzygalna reszta") | regula usunieta z referencji; zastapiona niezaleznoscia agentow i opcjonalnym kontaktem miedzy sesjami; A-main odpowiada wlascicielowi bezposrednio i nie przejmuje pracy subagenta | ref l. 112–116 "Agenci i / podagenci pracują niezależnie w jawnym zakresie; kontakt między sesjami jest / opcjonalny, a nie warunkiem kontynuacji. A-main odpowiada właścicielowi / bezpośrednio i deleguje każdy konkretny element pracy" |
| Role — Defense, FC, Integration | kontrakty 5-polowe (ref v2 l. 185–222) | bez zmian tresci (ref l. 240–277) | ref l. 250–251 "brak odpowiedzi na numer liczy się jako PRZYJMUJĘ" |
| Przejscia | lista przejsc (ref v2 l. 314–324) | ta sama lista (ref l. 449–459) + terminalny lancuch i najwyzej jedna kontynuacja | ref l. 359–360 "`event → readback → graph/dependency reconciliation → one bounded continuation lub NO_ELIGIBLE_TOPIC`"; l. 368–372 (AB-T-004) |
| Checklista Evaluatora | 10 pkt (ref v2 l. 224–260) | te same 10 pkt (ref l. 279–315) + numeracja zarzutow z expected/observed/result w skillu dowodu | evidence l. 17–18 "Evaluator działa niezależnie: numeruje każdy zarzut, reprodukcję i expected / observed / result." |
| Receipts i dowod | receipts dispatch/launch/…/integration (ref v2 l. 365–373) | to samo + phase event z UTC, model kontroli, fail-closed fallback, minimalny terminal receipt, ponowny hash po korekcie | ref l. 335–338 (AB-T-009) "każda faza musi mieć trwały `phaseEventId`, pełny UTC `observedAt`"; l. 339–342 (AB-T-010) "`control.runtimeMode=independent-sessions` wymaga różnych, potwierdzonych sesji Evaluatora i Final Control."; evidence l. 15–16 "Po każdej korekcie pliku, receiptu lub payloadu policz SHA-256 ponownie; stary receipt oznacz `SUPERSEDED`." |
| Statusy i czas | phase/health/outcome (ref v2 l. 264) | + `infra`, `processOutcome`, `provenance`, obowiazkowy UTC | ref l. 319 "…`provenance` (`VERIFIED`, `INFRA/UNVERIFIED`)…"; l. 353–358 (AB-T-001) "Brak wymaganego czasu oznacza `TIMESTAMP_UNVERIFIED` i wyklucza PASS." |
| Raport terminalny | pola STATUS…DEPLOY/PUSH (ref v2 l. 385–393) | + numerowane TR-001…TR-010 | ref l. 533–540 |
| Integracja | Integration po PASS FC, bez push/merge (ref v2 l. 211–222) | ten sam kontrakt; dodatkowo router dopuszcza autonomiczne wdrozenie w ramach istniejacego upowaznienia | controller l. 46 "Integration może mutować wyłącznie zatwierdzony zakres po PASS Final Control;"; router l. 106–108 "po PASS Final Control zintegruj lub wdroż w autoryzowanym zakresie"; router l. 112–114 "Istniejące upoważnienie właściciela do technicznych napraw w ramach celu obejmuje samodzielne wybory i konieczne działania live" |
| Orkiestrator | jeden skill sterujacy (controller) | 10 entrypointow (7 wykonawczych + 3 referencje), heartbeat, wzorce bledow ERR-MA-001…012 | router l. 40–41 "Pakiet ma dziesięć aktywnych entrypointów: siedem skillów wykonawczych oraz trzy skille-referencje." |
| Petla naprawcza i BLOCKED | petla naprawcza (ref v2 l. 11–23) | + obowiazkowy blok `autonomy`/`localLoop`, odrzucanie BLOCKED bez `tested=true` i `exhausted=true` | ref l. 29–34 |
| Zmiana procesu z lekcji | brak | granica uczenia: publikacja zmiany normatywnej tylko po E, FC i ECHO | ref l. 389–393 (AB-L-001) "wymaga niezależnego Evaluatora, Final Control i jawnego owner approval/ECHO" |

## 5. Czego z f NIE przenosic do ZERO (konflikt lub brak zastosowania)

- Autonomiczne dzialania live i wdrozenie bez osobnej bramki (router l. 106–119) — sprzeczne z G5 i ECHO-004 (push wylacznie na galaz robocza) oraz z zasada zestawu i l. 31–33 (przekazanie na zewnatrz to osobna bramka).
- Elementy srodowiska OpenClaw: Lobster, Managed Task Flow/SQLite, `sessions_spawn`, `memory-core`, `USER.md`/`MEMORY.md`, heartbeat z CAS (reference l. 428–447, 54–83; heartbeat calosc) — w ZERO nie ma tych komponentow.
- Usage tokenow per faza AB-T-006…008 (ref l. 321–331) — brak wymagania w ZERO.

## 6. Konkretne reguly do przeniesienia do procesu ZERO (propozycja dla osobnego tematu PROCES)

| # | Regula | Zrodlo w f |
|---|---|---|
| R1 | Obieg: Operator -> Evaluator -> Defense (tylko przy zarzutach) -> Final Control -> Integration; runda = pelny cykl, licznik nie resetowany | router l. 81–82; ref l. 405–408 |
| R2 | Defense: ten sam Operator odpowiada na kazdy numer zarzutu PRZYJMUJE/ODRZUCAM z dowodem (cytat/lokalizacja/wynik testu); brak odpowiedzi = PRZYJMUJE; nie zmienia artefaktu | ref l. 240–251 |
| R3 | Final Control: inny wykonawca niz Operator, Evaluator, Defense i Wykonawca; werdykt per zarzut NAPRAW / ODDAL / DO DECYZJI CZLOWIEKA plus agregat; PASS dopiero po zamknieciu wszystkich zarzutow | ref l. 253–264; evidence l. 19–20 |
| R4 | Evaluator: 10 punktow, kazdy PASS/FAIL/NOT_RUN z expected/observed; CLEAR tylko przy 10 PASS; kazdy FAIL z numerem, plikiem+linia, punktem listy, reprodukcja | ref l. 279–315; evidence l. 17–18 |
| R5 | Integration jako osobna rola: tylko zatwierdzona allowlista, hashe przed i po, bez push/merge/deploy, bez `git add .`/`git add -A`, integration receipt; READY_FOR_DEPLOY zapisuje wylacznie Orkiestrator | ref l. 266–277 |
| R6 | Uczciwy model kontroli: `independent-sessions` tylko gdy Evaluator i FC to faktycznie rozne sesje; inaczej jawne `logical-single-session` | ref l. 339–342; controller l. 39–42 |
| R7 | Po kazdym terminalnym wyniku: readback -> rekoncyliacja zaleznosci -> najwyzej jedna kwalifikowana kontynuacja albo `NO_ELIGIBLE_TOPIC` | ref l. 359–372 |
| R8 | Czas w raportach i receiptach jako ISO-8601 UTC z `Z`; brak = `TIMESTAMP_UNVERIFIED`, wyklucza PASS | ref l. 353–358 |
| R9 | `BLOCK` dopiero po wyczerpaniu lokalnej petli naprawczej, z nazwana zewnetrzna decyzja | ref l. 17–27 |
| R10 | Po kazdej korekcie wytworu ponowny SHA-256; stary receipt oznaczony `SUPERSEDED` | evidence l. 15–16 |
| R11 | Zmiana normatywna procesu wynikajaca z lekcji: tylko po niezaleznym Evaluatorze, FC i ECHO (zgodne z trybem zmiany procesu w `00_PUNKT_STARTOWY.md`) | ref l. 389–393 |
| R12 | Raport terminalny z polami TR-001…TR-010, w tym findings, round/max_rounds, `DEPLOY/PUSH: NIE WYKONANO` | ref l. 530–542 |
| R13 | Eskalacja przez Orkiestratora (regula z v2, usunieta w f — zachowac mimo przejscia na f): Operator/subagent nie rozstrzyga bezposrednio z wlascicielem; DO DECYZJI CZLOWIEKA analizuje najpierw Orkiestrator, do wlasciciela trafia tylko nierozstrzygalna reszta; Orkiestrator jako jedyny autoryzuje integracje i zapisuje READY_FOR_DEPLOY. W ZERO juz obowiazuje przez skill sesji (i l. 93 `DECISION_REQUIRED`, l. 122, l. 332–334), dlatego przy przejeciu f nie wolno jej zastapic modelem A-main z f l. 112–118 i 183–198 | v2 ref l. 64–66, 136–137; v2 controller l. 228–230, 246–247; f ref l. 276–277 (resztka) |

Wprowadzenie R1–R13 do dokumentow ZERO to zmiana procesu: osobny temat w domenie PROCES i decyzja wlasciciela (ECHO-010 pkt 1). Ten inwentarz niczego w procesie nie zmienia.

---

## 7. Lista kasacji dla wlasciciela (archiwum Autobot.rar)

Rekomendacje USUNAC dotycza wylacznie plikow przeczytanych w calosci:

1. `autobotSKILL.md` — PRZESTARZALY BEZ OBRONY.
2. `civautobotSKILL.md` — PRZESTARZALY BEZ OBRONY (nakladka innego repozytorium).
3. `AutoBot-Orkiestrator-SKILL.md` (1.0.0) — ZASTAPIONY, bez zdefiniowanej obrony.
4. `AutoBot-Orkiestrator-v1.1.0-SKILL.md` (1.1.0) — ZASTAPIONY (ma obrone, ale w calosci zawarty w f).
5. `skasujzmergowanegalezieautobot.sh` — jednorazowy skrypt, nie zasady.
6. Jedna z dwoch kopii zestawu f: `autobot-skills.zip` albo folder `autobot-skills/` (bajtowo identyczne).

Zachowac: `autobot-skills/` (jedna kopia). Pakiet `autobot/` (Python): NIE DOTYCZY — poza kryterium; decyzja wlasciciela niezalezna od obrony.
Poza archiwum: paczka v2 — zachowac do decyzji przejmujacej f; skill sesji — zachowac.

---

## 8. Klasyfikacja kazdego wpisu (kompletnosc S-P1)

### 8.1 Autobot.rar — 62 wpisy (42 pliki + 20 katalogow)

| # | Wpis | Typ | Zestaw | Klasyfikacja |
|---|---|---|---|---|
| 1 | `autobotSKILL.md` | plik | a | sklasyfikowany (3.a) |
| 2 | `autobot-skills.zip` | plik | f | sklasyfikowany (0.3, 3.f) |
| 3 | `civautobotSKILL.md` | plik | b | sklasyfikowany (3.b) |
| 4 | `skasujzmergowanegalezieautobot.sh` | plik | g | sklasyfikowany (3.g) |
| 5 | `autobot/autobot/evaluator.py` | plik | e | sklasyfikowany (3.e) |
| 6 | `autobot/autobot/guardrails.py` | plik | e | sklasyfikowany |
| 7 | `autobot/autobot/logger.py` | plik | e | sklasyfikowany |
| 8 | `autobot/autobot/operator.py` | plik | e | sklasyfikowany |
| 9 | `autobot/autobot/optimizer.py` | plik | e | sklasyfikowany |
| 10 | `autobot/autobot/playbook.py` | plik | e | sklasyfikowany |
| 11 | `autobot/autobot/types.py` | plik | e | sklasyfikowany |
| 12 | `autobot/autobot/__init__.py` | plik | e | sklasyfikowany |
| 13 | `autobot/autobot/__pycache__/evaluator.cpython-310.pyc` | plik | e | jawnie pominiety: `__pycache__` |
| 14 | `autobot/autobot/__pycache__/guardrails.cpython-310.pyc` | plik | e | jawnie pominiety: `__pycache__` |
| 15 | `autobot/autobot/__pycache__/logger.cpython-310.pyc` | plik | e | jawnie pominiety: `__pycache__` |
| 16 | `autobot/autobot/__pycache__/operator.cpython-310.pyc` | plik | e | jawnie pominiety: `__pycache__` |
| 17 | `autobot/autobot/__pycache__/optimizer.cpython-310.pyc` | plik | e | jawnie pominiety: `__pycache__` |
| 18 | `autobot/autobot/__pycache__/playbook.cpython-310.pyc` | plik | e | jawnie pominiety: `__pycache__` |
| 19 | `autobot/autobot/__pycache__/types.cpython-310.pyc` | plik | e | jawnie pominiety: `__pycache__` |
| 20 | `autobot/autobot/__pycache__/__init__.cpython-310.pyc` | plik | e | jawnie pominiety: `__pycache__` |
| 21 | `autobot/data/playbook.json` | plik | e | sklasyfikowany |
| 22 | `autobot/data/runs.jsonl` | plik | e | jawnie pominiety: dane uruchomien (weryfikacja strukturalna) |
| 23 | `autobot/demo_montazowa.py` | plik | e | sklasyfikowany (nie uruchomiony) |
| 24 | `autobot/README.md` | plik | e | sklasyfikowany |
| 25 | `autobot/tests/test_autobot.py` | plik | e | sklasyfikowany (nie uruchomiony) |
| 26 | `autobot/tests/__pycache__/test_autobot.cpython-310.pyc` | plik | e | jawnie pominiety: `__pycache__` |
| 27 | `autobot-skills/skills/autobot-controller/SKILL.md` | plik | f | sklasyfikowany (3.f) |
| 28 | `autobot-skills/skills/autobot-dispatch/SKILL.md` | plik | f | sklasyfikowany |
| 29 | `autobot-skills/skills/autobot-evidence/SKILL.md` | plik | f | sklasyfikowany |
| 30 | `autobot-skills/skills/autobot-heartbeat/SKILL.md` | plik | f | sklasyfikowany |
| 31 | `autobot-skills/skills/autobot-memory/SKILL.md` | plik | f | sklasyfikowany |
| 32 | `autobot-skills/skills/autobot-memory-routing/SKILL.md` | plik | f | sklasyfikowany |
| 33 | `autobot-skills/skills/autobot-orchestrator/references/autobot-memory-routing.md` | plik | f | sklasyfikowany |
| 34 | `autobot-skills/skills/autobot-orchestrator/references/autobot-reference-contract.md` | plik | f | sklasyfikowany |
| 35 | `autobot-skills/skills/autobot-orchestrator/references/MAIN-AGENT-ORCHESTRATOR-FAILURE-PATTERNS.md` | plik | f | sklasyfikowany |
| 36 | `autobot-skills/skills/autobot-orchestrator/SKILL.md` | plik | f | sklasyfikowany |
| 37 | `autobot-skills/skills/autobot-project/references/otwarcie-projektu.md` | plik | f | sklasyfikowany |
| 38 | `autobot-skills/skills/autobot-project/SKILL.md` | plik | f | sklasyfikowany |
| 39 | `autobot-skills/skills/autobot-project-opening/SKILL.md` | plik | f | sklasyfikowany |
| 40 | `autobot-skills/skills/autobot-reference-contract/SKILL.md` | plik | f | sklasyfikowany |
| 41 | `AutoBot-Orkiestrator-SKILL.md` | plik | c | sklasyfikowany (3.c) |
| 42 | `AutoBot-Orkiestrator-v1.1.0-SKILL.md` | plik | d | sklasyfikowany (3.d) |
| 43 | `autobot-skills/skills/autobot-orchestrator/references` | katalog | f | kontener — klasyfikacja wg zawartosci |
| 44 | `autobot-skills/skills/autobot-project/references` | katalog | f | kontener |
| 45 | `autobot/autobot/__pycache__` | katalog | e | kontener (pominiety jak zawartosc) |
| 46 | `autobot/tests/__pycache__` | katalog | e | kontener (pominiety jak zawartosc) |
| 47 | `autobot-skills/skills/autobot-controller` | katalog | f | kontener |
| 48 | `autobot-skills/skills/autobot-dispatch` | katalog | f | kontener |
| 49 | `autobot-skills/skills/autobot-evidence` | katalog | f | kontener |
| 50 | `autobot-skills/skills/autobot-heartbeat` | katalog | f | kontener |
| 51 | `autobot-skills/skills/autobot-memory` | katalog | f | kontener |
| 52 | `autobot-skills/skills/autobot-memory-routing` | katalog | f | kontener |
| 53 | `autobot-skills/skills/autobot-orchestrator` | katalog | f | kontener |
| 54 | `autobot-skills/skills/autobot-project` | katalog | f | kontener |
| 55 | `autobot-skills/skills/autobot-project-opening` | katalog | f | kontener |
| 56 | `autobot-skills/skills/autobot-reference-contract` | katalog | f | kontener |
| 57 | `autobot/autobot` | katalog | e | kontener |
| 58 | `autobot/data` | katalog | e | kontener |
| 59 | `autobot/tests` | katalog | e | kontener |
| 60 | `autobot-skills/skills` | katalog | f | kontener |
| 61 | `autobot` | katalog | e | kontener |
| 62 | `autobot-skills` | katalog | f | kontener |

### 8.2 Zawartosc `autobot-skills.zip` — 14 plikow

Te same sciezki co wpisy 27–40 (prefiks `skills/…`), bajtowo identyczne (0.3) — sklasyfikowane jak 27–40.

### 8.3 Paczka v2 — 11 wpisow ZIP (7 plikow + 4 katalogi)

Pliki: `README.md`, `AUTOBOT-POLICY.md`, `AUTOBOT-CONTROLLER-TEST-REPORT.md`, `autobot-controller/SKILL.md`, `autobot-controller/references/autobot-reference-contract.md`, `autobot-project/SKILL.md`, `autobot-project/references/otwarcie-projektu.md` — sklasyfikowane w 3.h. Katalogi: `autobot-controller/`, `autobot-controller/references/`, `autobot-project/`, `autobot-project/references/` — kontenery.

### 8.4 Wersja z listy umiejetnosci sesji — 1 plik

`autobot/SKILL.md` — sklasyfikowany w 3.i (katalog zawiera tylko ten plik).

### 8.5 Pelne SHA-256 plikow archiwum (po ekstrakcji)

Wynik `sha256sum` (Autobot.rar: sciezki wzgledem `scratchpad/p002-rar/`; v2: wzgledem `scratchpad/autobot-zip/`):

```
8f3efd7f7f027af556a5a723163e752fbc3e952b1547e5f4f2873535a1d37829  AutoBot-Orkiestrator-SKILL.md
626eeb5308a843abc1e3b44801feb9b7cf0b637271e21dc4f3fb3a9486a29788  AutoBot-Orkiestrator-v1.1.0-SKILL.md
44f63cfb3389aef2f3d587cd47041d395a79b5b5660dbaa9b1a1e30e37a6a242  autobot-skills.zip
37f777b58aacf904565bdabc03af83351e4efe0bf7073847eb53b5df7363786b  autobot-skills/skills/autobot-controller/SKILL.md
0aae38fcf693952e5f662dec99f230934a057a17413b2c271000dc0e1af8ef18  autobot-skills/skills/autobot-dispatch/SKILL.md
a4e7e8de594fdff925cb59f7a896af3d80eb24fe71fcce745229c3ad3e33a0c1  autobot-skills/skills/autobot-evidence/SKILL.md
313aa9b1d8d6df83e4b7fd49413bff7835b1be5449fad312757ab51988b7c64b  autobot-skills/skills/autobot-heartbeat/SKILL.md
9144eb0125204a9306d6298bf8177eec62b39808cc066aab1769c004f1dc35f9  autobot-skills/skills/autobot-memory-routing/SKILL.md
08f5ca1ed9777bdbb58f321b6dc4cb627b58610435b884cea1ef74775bf5c89f  autobot-skills/skills/autobot-memory/SKILL.md
6e8e071694bd1a51abda87cea0f758bd5b29492693d613323a85777b2b0a72b9  autobot-skills/skills/autobot-orchestrator/SKILL.md
830296fbcc7b446d926eaed70fb74a59334d2e0f50f152041169df64857aa964  autobot-skills/skills/autobot-orchestrator/references/MAIN-AGENT-ORCHESTRATOR-FAILURE-PATTERNS.md
b2ca5b605e8516cf02835334ff8e11c157e8ea8287c2d8a7eb0fe6c7cfeea2e0  autobot-skills/skills/autobot-orchestrator/references/autobot-memory-routing.md
2b531cf9f5fbb5ed0bca9b0a837cb2fa144e5c498d820c5b73d7a348c2b72e56  autobot-skills/skills/autobot-orchestrator/references/autobot-reference-contract.md
1672ae958576977da373952085c0a39de8a141ac92a244bec1e38b2aed8f218a  autobot-skills/skills/autobot-project-opening/SKILL.md
dcf052cf7f1f3d45004f13b3d9a1346aeff7e001e2fa062702816251324c1cbb  autobot-skills/skills/autobot-project/SKILL.md
7a1ea9588ea951edea860e081703e053e50694aee1c8ba2b32e878ab4be71917  autobot-skills/skills/autobot-project/references/otwarcie-projektu.md
c1f6a615827cf2dcc1e9203f5c6e37a3792c7c4d7c4af41820652594c2807c60  autobot-skills/skills/autobot-reference-contract/SKILL.md
ead619621ad49b916641d7bc2cff94c1b54e7875c7868425cd5378378d862433  autobot/README.md
bbf6b76da28ef3c5344a25a45bd26377cd115f124f8f9197e7b70ed29d0bb4a2  autobot/autobot/__init__.py
84f7ae43ebc1ff70251ea5c51e227cc461a051addbad78490113c29507ca634b  autobot/autobot/__pycache__/__init__.cpython-310.pyc
7a889e77550072457c229d6cb80dcb515d78ee7c8c1bbf56ab6e10122acd07f5  autobot/autobot/__pycache__/evaluator.cpython-310.pyc
6449d150d3027c930baa5346027c86ad8e83d0eaae8d69c8046ba8f1ea53a875  autobot/autobot/__pycache__/guardrails.cpython-310.pyc
80719b7444f02d2c9008219a9cc78fc860af3219f94acb2fdf60e10f32d46c2d  autobot/autobot/__pycache__/logger.cpython-310.pyc
226e363c9676bd200255e1081fd4a4e61cf82222430ae3338f5d37963a1e280a  autobot/autobot/__pycache__/operator.cpython-310.pyc
33542a799811b514a05ca6b4c366a062e2e884aba8814ed9852da47a712641ff  autobot/autobot/__pycache__/optimizer.cpython-310.pyc
bc53f8b2c866884e99af1f6a10b14a0aeaa3ce399c216f921e221c47e931bf2e  autobot/autobot/__pycache__/playbook.cpython-310.pyc
c2c29bfaad05a8888d8953d50bd6efa602006ee3d41e31e897129479d4c09441  autobot/autobot/__pycache__/types.cpython-310.pyc
9c8925784f3cceaab9989b3596d159c5502c506f8b6a8b646612c63d668f9f47  autobot/autobot/evaluator.py
5fc2f5c1b045b2de90fc2380da46e5e9a66195b8fa1b0e841cb5aed4935a5ca9  autobot/autobot/guardrails.py
62c46d69b7cbd3ff336ca64e18c40fa72118704156fce81933cac7067d6b90cd  autobot/autobot/logger.py
1ff0c87cc2b2fa9246457c44d55e31a65a7c10d926a4db2fbeedf9a595529e82  autobot/autobot/operator.py
109698e3b41ff3659579825259f161b05159fd5eb52fc885c16cd8eda110c823  autobot/autobot/optimizer.py
79efbb4352a10522247c68c07fe87a5676390ba30447ec7f6001b5875aabaa76  autobot/autobot/playbook.py
e96ff599817c6b628c7b9cbd4d5e199ab67a2b15ef0bd0e0cbfcba2784b1798c  autobot/autobot/types.py
04a888da5716b8ba9b164802c547cec00d3a071118794e40e1b37bd57d2219eb  autobot/data/playbook.json
3f41213c09eac86c956cd1f06cb3b4b8bdfe347177783766b612a395f32a5251  autobot/data/runs.jsonl
68b0e19b6865171106788f4cfbadb0f5f5dc43ae7852ecb83eebe0bbde99343d  autobot/demo_montazowa.py
e6a2039208a67b84ce4ba5ba6ff62c01addb8a4cfec859082a1b2da4a12d58be  autobot/tests/__pycache__/test_autobot.cpython-310.pyc
871fc8c1f5552c09d31d7501c6047b9d62f56cc22387c8fe9e9ce4bdebfdfd82  autobot/tests/test_autobot.py
b7ce490ca518104265a7670a68e9c68a5f6978bfca22cf3a4f3a00144b3d6812  autobotSKILL.md
fd1f90877fab5dd83ca488e554fe54cf0abd85f17da53519fae6d1fb1177372b  civautobotSKILL.md
9df2c59f72658b045d1fdaeb69be8f899aa097809d4688f3dea8e219ad6aa265  skasujzmergowanegalezieautobot.sh
949979cb78c267f6064c117c566799f4a177d822561c04745e8ba701e7fa221e  v2/AUTOBOT-CONTROLLER-TEST-REPORT.md
075bb542ddcd43393dc8f13081d1eeafa9e50190ee3628be4e1816ba652ed000  v2/AUTOBOT-POLICY.md
468e91a28b938c47c86ece6915da1bd458d1da31126e7ffb2211b50a75902ef2  v2/README.md
5494732d291a3dfe163131d48f4eed25523c52198c155dfecc25ef1d6f11f3fa  v2/autobot-controller/SKILL.md
3b5e40f1898e93e82012386129fc23359f6648576d7e176b56514b54cbe92772  v2/autobot-controller/references/autobot-reference-contract.md
3c4bdedb1f3f08d675221630bac9256f1a80e4e220c62f7d728188cf443adef9  v2/autobot-project/SKILL.md
31be6183dc191974f74e651b7f8548077694615b605aea89e86b62a41d8a0aa6  v2/autobot-project/references/otwarcie-projektu.md
```

---

## 9. Kontrola koncowa (hash przed i po)

Polecenie: `sha256sum` oryginalow po zakonczeniu pracy:

```
8d0b81b432030baa7499c5868d386b7c6866c0379ead94c16c4b77cea3c51eb5  a4edf6ca-Autobot.rar
76f58a584e215099f144d5cfe65e026632cf110f4abaacfa7723f187aff2a83d  93c21342-autobot-universal-skills-2026-09-16-v2.zip
cee845edec45a55dc8a08b818b32b091400e71f992a716181617ced5bc6ff609  skill-sesji/autobot/SKILL.md
```

Porownanie z sekcja 0.1: Autobot.rar `8d0b81b4…51eb5` = bez zmian; paczka v2 `76f58a58…a83d` = bez zmian; skill sesji `cee845ed…f609` = bez zmian. Zrodla nie zostaly zmodyfikowane. W repozytorium utworzono wylacznie ten plik (allowlista); katalogi robocze sa w scratchpadzie poza repozytorium.

DEPLOY/PUSH: NIE WYKONANO. Commit: nie wykonano (rola Integration).

