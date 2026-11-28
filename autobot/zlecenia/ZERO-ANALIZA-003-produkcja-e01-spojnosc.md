# ZERO-ANALIZA-003-produkcja-e01-spojnosc

WYZWALACZ:  decyzja wlasciciela ECHO-035 (2026-11-28): przeanalizowac, czy materialy produkcyjne E01 sie zgadzaja i czy nie trzeba ich rozbudowac, zanim powstanie wsad dla Seedance.
GOAL:       Istnieje zweryfikowany raport spojnosci i kompletnosci materialow produkcyjnych E01 (dokumenty wgrane przez wlasciciela i z archiwum) wzgledem aktualnego scenariusza E01 i decyzji wlasciciela: rozbieznosci z cytatami, luki potrzebne do wsadu dla modelu wideo, podzial na to, co przenosi sie na Seedance, a co jest tylko dla Flow/Veo, oraz PROPOZYCJE rozbudowy — bez zmiany jakiegokolwiek dokumentu zrodlowego.
KONIEC:     PRAWDA gdy scenariusze S-A10..S-A14 przechodza. Zadna zmiana poza allowlista.

WEJSCIA (tylko odczyt; kazdy z hashem SHA-256 w inwentarzu raportu):
 A. Wgrane przez wlasciciela 2026-11-28 (/root/.claude/uploads/3337db06-529b-5b00-81d6-a0a7013a451d/): 4582ead6-03_opisy_wizualne_scen.md, 8d6c4388-04_dzwiek_i_muzyka.md, d029e8a1-05_inserty_closeup.md, 4f2b6ba0-06_przejscia_scen.md, 758ebb13-07_podtekst_dialogowy.md, 9db824e4-ZERO_INSTRUKCJA_Flow_scena1_ciaglosc.md, ee92a910-ZERO_instrukcje_dla_agenta_Flow.md, 85b2d98d-ZERO_konsultacja_scenariuszowa.md, 949ae02c-ZERO_metoda_AB_montaz.md, 618926d1-ZERO_porownanie_Veo_vs_Kling.md.
 B. Z archiwum (kopia rozpakowana, tylko odczyt; katalog /tmp/claude-0/-home-user-Zero/3337db06-529b-5b00-81d6-a0a7013a451d/scratchpad/zero-extract/Zero/ZERO_DO_PRZENIESIENIA/): ZERO_E01_produkcja/01_nota_rezyserska.md, 02_charakterystyki_postaci.md, 08_noty_techniczne.md; ZERO_produkcja_flow/ZERO_E01_rozpiska_sekundowa.md, ZERO_decyzje_rewizja.md, ZERO_repercusje_spojnosc.md, ZERO_E01_Scena*_beaty_7s_ENG.md, ZERO_E01_Blok*_beaty_7s_ENG.md, ZERO_E01_Wstawka_*_beaty_7s_ENG.md, ZERO_E01_ZeroDay_beaty_7s_ENG.md, ZERO_E01_S1_Clip00..11.md, ZERO_VEO3_E01_Scena1_FULL_ENG*.md; ZERO_HANDOFF_przekazanie.md (katalog nadrzedny).
 C. Aktualny scenariusz E01: `scenariusze/ZERO_mini_serial_E01_ADAM_rev.md` oraz `scenariusze/MANIFEST.sha256`; raport `docs/analiza/ZERO-ANALIZA-001-e01-logika-timing-napiecie/raport.md` i `tabela_scen.md`; konsultacja i decyzje: `autobot/DECYZJE.md` (m.in. ECHO-020, ECHO-027), `PLAN_WDROZENIA_ZERO.md`.
 D. Zatwierdzone badania dla Seedance i Klinga (do punktu przenoszalnosci): `docs/research/ZERO-RESEARCH-001-*`, `-003-*` (seedance.md), `ZERO-RESEARCH-005-zestawienie-zbiorcze/zestawienie_zbiorcze.md`, `ZERO-RESEARCH-008-omni-vs-kling-jakosc/omni_vs_kling.md`.
 Hierarchia zrodel przy sprzecznosci: oryginalny scenariusz E01 (rank 1) > decyzje wlasciciela ECHO > dokumenty produkcyjne (rank 4). Rozbieznosci nie rozstrzygaj — zapisz obie wersje.

ZADANIE: napisz dwa pliki (po polsku; nazwy techniczne bez znakow diakrytycznych):
 1. `docs/analiza/ZERO-ANALIZA-003-produkcja-e01-spojnosc/raport.md`: (1) inwentarz wejsc z hashami i oceną; (2) rozbieznosci miedzy dokumentami i wzgledem scenariusza E01, kazda z dwoma cytatami i waga; (3) luki potrzebne do wsadu dla modelu wideo (wyglad postaci i referencje, lokacje, paleta i swiatlo na osi czasu, format i proporcje, zasady dialogow po angielsku z polskim glosem w montazu, ciaglosc rekwizytow, brakujace beaty sc. 13 i 15, spis przejsc) z PROPOZYCJAMI uzupelnienia; (4) tablica przenoszalnosci na Seedance: przenosi sie / do przeksztalcenia / tylko Flow-Veo; (5) lista decyzji wymaganych od wlasciciela (zasada: decyzje kanoniczne i produktowe tylko jako pytania, nie jako rozstrzygniecia); (6) rekomendowany zakres rozbudowy wsadu dla Seedance — jako propozycja, bez wyboru narzedzia (ECHO-027).
 2. `docs/analiza/ZERO-ANALIZA-003-produkcja-e01-spojnosc/tabela_rozbieznosci.md`: tabela wszystkich rozbieznosci (ID R-nn, dokument A, cytat A, dokument B, cytat B, waga, wplyw na generowanie, rekomendowana decyzja).

Sprawdz m.in.: liczba i numeracja scen (03 i 06 koncza na scenie 14, scenariusz ma sc. 1-15 i 4 wstawki); napisy czasowe i wiek w P1-P4 (06: "CZTERY LATA POZNIEJ", "OSIEMNASCIE LAT PO PRZYJEZDZIE" kontra konsultacja A5 i rozpiska "OK. 11 LAT PO PRZYJEZDZIE"); imiona (Marek, Dabrowski) i uzycie w podtekscie; wyglad Karoliny (wlosy, ubior) w instrukcjach, charakterystykach i beatach; metraz (rozpiska 52 min 15 s, naglowek 60, ANALIZA-001 60,5); czasy ujec (np. Zero Day: 3-4 s kontra 5 s w ostatniej sekwencji); muzyka (04: mapa muzyczna kontra zasada "bez muzyki w klipach" z Flow); dlugosci klipow (Flow 10 s, Veo 8 s, Omni Flash 10 s kontra badania); informacje ktore widz ma miec (ECHO-020: widz wie od E01, ze Vera jest matka Agi) kontra podtekst i noty; rekwizyty i ich ciaglosc (teczka, sweter, mapa PSE); inserty kontra sceny.

REGULA PRZECIW SAMOOSZUKIWANIU:
 - Zakaz zmiany jakiegokolwiek pliku wejsciowego; zakaz poprawiania scenariusza (G1, G2, G3) — tylko PROPOZYCJE w raporcie.
 - Zakaz twierdzen bez dwoch cytatow z lokalizacja; zakaz parafrazy bez odnosnika.
 - Zakaz uznania "zgodne", gdy nie przeczytano obu miejsc; zakaz rozstrzygania sprzecznosci kanonicznych (zapisz obie wersje i wskaz decyzje wlasciciela).
 - Zakaz rankingu i rekomendacji wyboru narzedzia (ECHO-027); zakaz nowych odczytow sieci.
 - Zakaz uruchamiania skryptow z archiwum; zakaz zapisu poza allowlista; zapisuj pliki etapami.

PROCEDURA NAPRAWCZA PRZY FAIL: Evaluator numeruje zarzuty (miejsce, punkt listy, reprodukcja). Operator (w obronie) odpowiada PRZYJMUJE/ODRZUCAM z dowodem; po werdykcie NAPRAW poprawia tylko wskazane miejsca.

ALLOWLISTA:
  - `docs/analiza/ZERO-ANALIZA-003-produkcja-e01-spojnosc/raport.md` (nowy plik)
  - `docs/analiza/ZERO-ANALIZA-003-produkcja-e01-spojnosc/tabela_rozbieznosci.md` (nowy plik)
ZAKAZANE BEZWZGLEDNIE: `scenariusze/`, `autobot/`, pliki wejsciowe A i B (uploads, archiwum), `docs/analiza/ZERO-ANALIZA-001-*` i `-002-*`, `docs/research/*`, `docs/audiobook/`, `docs/proces/`, `docs/przeglad-2026-11-27/`, `docs/rozbieznosci/`, polecenia git zmieniajace stan (poza rola Integration), sekrety, siec.

MIEJSCE PRACY: `docs/analiza/ZERO-ANALIZA-003-produkcja-e01-spojnosc/`
BAZA:          HEAD galezi roboczej
OBIEG:         Operator -> Evaluator (10 punktow) -> Obrona przy zarzutach -> Final Control (per zarzut) -> Integration

RUNDA: w toku (rundy 1-3 z 3; licznik w rejestrze aktualizuje orkiestrator po zakonczeniu workflow)
