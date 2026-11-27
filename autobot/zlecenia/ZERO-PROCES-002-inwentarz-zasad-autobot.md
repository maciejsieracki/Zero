# ZERO-PROCES-002-inwentarz-zasad-autobot

WYZWALACZ:  decyzja wlasciciela ECHO-010 (2026-11-27): wskazac, ktore zestawy zasad AutoBot sa przestarzale i bez obrony (do skasowania przez wlasciciela) oraz zastosowac najnowsza wersje z obrona. Uwaga: wczesniejsze identyfikatory "ZERO-PROCES-001-Q1..Q3" dotycza pytan kalibracyjnych (ECHO-001..003); numer 001 jest zajety, dlatego 002.
GOAL:       Istnieje zweryfikowany inwentarz wszystkich zestawow zasad AutoBot (Autobot.rar, paczka v2 z 2026-09-16, wersja z listy umiejetnosci sesji): dla kazdego data, wersja, zakres, czy definiuje obrone i osobna role Integration, status i rekomendacja usuniecia lub zachowania, oraz wskazanie najnowszego zestawu z obrona i roznic wzgledem v2.
KONIEC:     PRAWDA gdy scenariusze S-P1..S-P6 przechodza. Zadna zmiana poza allowlista.

ZADANIE:
1. Utworz NOWE PUSTE katalogi robocze w scratchpadzie sesji (/tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/): jeden na rozpakowanie archiwum /root/.claude/uploads/3337db06-529b-5b00-81d6-a0a7013a451d/a4edf6ca-Autobot.rar (unrar x), drugi na rozpakowanie zawartego w nim autobot-skills.zip (unzip). Porownaj zawartosc zip z folderem autobot-skills w archiwum (hashe). Paczka v2 z 2026-09-16 jest juz rozpakowana (tylko odczyt): scratchpad/autobot-zip/ (oryginal: /root/.claude/uploads/3337db06-529b-5b00-81d6-a0a7013a451d/93c21342-autobot-universal-skills-2026-09-16-v2.zip). Wersja z listy umiejetnosci sesji (tylko odczyt): /root/.claude/skills/synced/a8b5d1c2-8fcc-4315-8ad2-e24d641c1f99_6ffe6d7a-cafc-4ff9-b7d6-6e69485369af/autobot/SKILL.md.
2. Zinwentaryzuj KAZDY zestaw zasad: (a) autobotSKILL.md; (b) civautobotSKILL.md; (c) AutoBot-Orkiestrator-SKILL.md; (d) AutoBot-Orkiestrator-v1.1.0-SKILL.md; (e) pakiet Pythona autobot/ (README i kod — ustal, czy to implementacja czy zasady); (f) autobot-skills (10 skilli i referencje, w tym autobot-orchestrator i wzorce bledow orkiestratora); (g) skasujzmergowanegalezieautobot.sh (NIE URUCHAMIAC; opisz tylko co robi); (h) paczka v2 z 2026-09-16; (i) wersja z listy umiejetnosci sesji. Dla kazdego: data (mtime i data/wersja wewnatrz tresci), wersja, zakres, role, czy zdefiniowana obrona (Defense) — tak/nie z cytatem i linia, czy osobna rola Integration, czy checklista Evaluatora (ile punktow), czy receipts, czy wskazuje nastepce lub zastapiony, STATUS: NAJNOWSZY Z OBRONA / AKTUALNY / ZASTAPIONY / PRZESTARZALY BEZ OBRONY / NIE DOTYCZY, REKOMENDACJA: USUNAC / ZACHOWAC / NIE DOTYCZY z uzasadnieniem.
3. Wskaz jeden NAJNOWSZY zestaw zawierajacy obrone (uzasadnij datami i trescia) i podaj roznice funkcjonalne wzgledem paczki v2 z 2026-09-16 (role, przejscia, checklista, receipts, integracja, orkiestrator) z cytatami oraz liste konkretnych regul do przeniesienia do procesu ZERO.
4. Zapisz wynik w pliku z allowlisty.

REGULA PRZECIW SAMOOSZUKIWANIU:
- Zakaz uznania "ma obrone" lub "nie ma obrony" bez doslownego cytatu z numerem linii albo bez potwierdzonego braku (grep -n -i z pustym wynikiem, wpisz uzyte polecenie).
- Zakaz oceny wersji wylacznie po nazwie pliku lub dacie; tresc rozstrzyga, daty to poszlaka (mtime moze sie roznic od daty wewnatrz).
- Zakaz uruchamiania jakichkolwiek skryptow z archiwum (.sh, .py, testy, demo) i importowania modulow; tylko odczyt tekstu i hashowanie (python3 -I).
- Zakaz rekomendacji USUNAC dla pliku, ktorego tresci nie przeczytano w calosci.
- Zakaz modyfikacji archiwum i oryginalow w uploads.

PROCEDURA NAPRAWCZA PRZY FAIL: Evaluator numeruje zarzuty (plik, linia, punkt listy kontrolnej, reprodukcja). Operator (w obronie) odpowiada na kazdy numer; po werdykcie NAPRAW poprawia tylko wskazane miejsca inwentarza.

ALLOWLISTA: `docs/proces/ZERO-PROCES-002-inwentarz-zasad-autobot/inwentarz.md`
ZAKAZANE BEZWZGLEDNIE: wszystko inne w repozytorium (w tym `autobot/`, `scenariusze/`, `docs/analiza/`, `docs/research/`), uploads, wykonywanie skryptow z archiwum, git zmieniajacy stan (poza rola Integration), sekrety.

MIEJSCE PRACY: `docs/proces/ZERO-PROCES-002-inwentarz-zasad-autobot/`
BAZA:          HEAD galezi roboczej
OBIEG:         Operator -> Evaluator (10 punktow) -> Obrona przy zarzutach -> Final Control (per zarzut) -> Integration (commit allowlisty, bez push)

RUNDA: 3 z 3 (limit wyczerpany; wstrzymany — patrz REJESTR_TEMATOW.md; Evaluator r2 = CLEAR, 2 zarzuty procesowe FC dotyczyly zapisow orkiestratora)
