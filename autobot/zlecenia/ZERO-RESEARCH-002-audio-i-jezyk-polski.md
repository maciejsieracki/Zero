# ZERO-RESEARCH-002-audio-i-jezyk-polski

WYZWALACZ:  decyzja wlasciciela ECHO-008 (2026-11-27): system wideo ma generowac obraz i dzwiek, jezyk polski jest wazny (inaczej angielski), rownoczesna sciezka audio jest plusem. Zalezy od ZERO-RESEARCH-001 (lista modeli i ceny); start dopiero po zwolnieniu slotu (pula 2).
GOAL:       Istnieje zweryfikowane zestawienie, ktore generatory wideo AI (Kling, Seedance, Google Veo, Sora 2, MiniMax przez API) tworza dzwiek razem z obrazem, jak obsluguja jezyk polski (mowa, synchronizacja ust) i czy sciezka audio powstaje jednoczesnie z wideo w jednym przebiegu, z oznaczeniem pewnosci zrodel i punktowym rankingiem zgodnosci z wymaganiami ZERO.
KONIEC:     PRAWDA gdy scenariusze S-R8..S-R12 przechodza. Zadna zmiana poza allowlista.

PODZIAL NA WEZLY: -a Kling, -b Seedance, -c Google Veo, -d Sora 2, -e MiniMax (API); potem synteza (zestawienie_audio) i Final Control. Licznik rund liczy sie dla calego tematu.

ALLOWLISTA (katalog `docs/research/ZERO-RESEARCH-002-audio-i-jezyk-polski/`):
  - `kling.md`, `seedance.md`, `veo.md`, `sora2.md`, `minimax.md` (po jednym na wezel)
  - `zestawienie_audio.md` (synteza)
ZAKAZANE BEZWZGLEDNIE: `scenariusze/`, `autobot/`, `docs/analiza/`, `docs/przeglad-2026-11-27/`, `docs/rozbieznosci/`, `docs/research/ZERO-RESEARCH-001-*` (tylko odczyt), polecenia git zmieniajace stan, sekrety.

MATERIAL WEJSCIOWY: wynik RESEARCH-001 (`docs/research/ZERO-RESEARCH-001-porownanie-generatorow-wideo/`) — lista modeli i ceny; rzad 2 po przejsciu Final Control tego tematu.
ZRODLA (rzad 1 rozstrzyga): oficjalna dokumentacja, strony produktow i ogloszenia dostawcow na dzien 2026-11-27; testy niezalezne to rzad 4 (NIEPOTWIERDZONE).

WYMAGANIA ZERO (ECHO-008), punktacja do opisania w zestawieniu: audio natywne; audio i wideo w jednym przebiegu; polski (mowa) — oficjalnie / w praktyce / brak; synchronizacja ust; wielu mowcow w klipie; wylaczenie muzyki; wlasne audio lub glos jako wejscie; eksport sciezki audio osobno.

MIEJSCE PRACY: `docs/research/ZERO-RESEARCH-002-audio-i-jezyk-polski/`
BAZA:          HEAD galezi roboczej

PLAN SPRAWDZENIA: S-R8 kompletnosc pol audio; S-R9 niezalezne potwierdzenie; S-R10 spojnosc z RESEARCH-001; S-R11 ranking jawny; S-R12 zrodla i zakres.

RUNDA: 0 z 3
