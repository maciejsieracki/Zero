# ZERO — AutoBot: punkt startowy

Data zalozenia: 2026-11-27. Orkiestrator: glowny agent sesji. Wlasciciel: Maciej Sieracki ("Naster").

## Czym projekt jest, a czym nie jest

- **Jest:** polski mini-serial sci-fi "ZERO" (E01 ADAM, E02 EWA, E03 ARES) tworzony z AI. Bierzacy cel: wypuscic serial. Pierwszy etap procesu: **analiza rozbieznosci scenariuszy E01 i E02** (logika, timing, budowanie napiecia).
- **Nie jest (swiadomie nie robimy):** E03 (poza zakresem do odwolania — ECHO-005); Planify (nie dotyczy); generowanie wideo; budzet; poprawianie scenariuszy w tematach analizy (poprawki to osobne tematy po decyzjach kanonicznych).

## Kolejnosc czytania na starcie sesji

1. `autobot/00_PUNKT_STARTOWY.md` (ten plik)
2. `autobot/REJESTR_TEMATOW.md`
3. `autobot/PRZEKAZANIE.md`
4. `autobot/WYBORY_TRWALE.md`
5. `autobot/DECYZJE.md`
6. `autobot/SCENARIUSZE.md`
7. specyfikacja biezacego etapu: `PLAN_WDROZENIA_ZERO.md` (plan ogolny) i zlecenia w `autobot/zlecenia/`

Nie zaczynaj od starego czatu ani od notatek agentow. Notatki to historia rozwazan, nie routing.

## Hierarchia zrodel faktow (rzad 1 rozstrzyga)

| Rzad | Zrodlo | Status |
|---|---|---|
| 1 | Tekst scenariusza w `scenariusze/` (po imporcie, z hashem) | rozstrzygajace dla tresci scenariusza |
| 2 | Handoff 2026-10-11, decyzje wlasciciela (ECHO) | stan faktyczny i decyzje; handoff zawiera bledy (np. punkt A4 obalony) |
| 4 | Notatki przegladu (`docs/przeglad-2026-11-27/`), audyty (`docs/rozbieznosci/`), raporty agentow | poszlaka — weryfikowac w rzedzie 1 |

## Odwzorowanie pojec

| Pojecie procesu | W tym projekcie |
|---|---|
| wytwor | raport analizy w `docs/analiza/<ID>/` (analiza), pliki w `scenariusze/` (import) |
| dowod wykonania | niezalezne sprawdzenie przez Evaluatora: cytaty z numerami linii, czasy przeliczone od zera, kompletnosc krzywej napiecia, hash plikow |
| zrodlo rozstrzygajace faktu | tekst scenariusza (rzad 1), nie pamiec, nie handoff, nie wczesniejsze raporty |
| miejsce pracy w toku | `docs/analiza/<ID>/` (jedna przestrzen na temat) |
| wersja obowiazujaca | HEAD galezi `claude/friendly-franklin-mn4e88` po imporcie bazy |
| zapis punktu kontrolnego | commit na galezi roboczej (robi wylacznie orkiestrator) |
| uznanie pracy za obowiazujaca | commit orkiestratora po Final Control |
| przekazanie na zewnatrz | push do `origin` na galaz robocza (ECHO-004) |
| lista zasobow do dotkniecia | allowlista w zleceniu tematu |
| zabezpieczenie ciaglosci | historia git; backup przed kazda zmiana scenariusza |

## Tryb zmiany samego procesu

Zmiana definicji rol, granic, limitow albo tego dokumentu to **osobny temat w domenie PROCES** (ID `ZERO-PROCES-NNN-slug`). Nigdy nie jedzie w allowliscie tematu analizy czy poprawek scenariusza.
