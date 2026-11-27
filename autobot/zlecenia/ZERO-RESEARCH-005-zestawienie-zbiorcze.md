# ZERO-RESEARCH-005-zestawienie-zbiorcze

WYZWALACZ:  decyzje wlasciciela ECHO-027 i ECHO-028 (2026-11-27): wlasciciel chce miec zebrana pelna charakterystyke wszystkich elementow, o ktore pytal, i sam wybrac narzedzie. RESEARCH-001/-002/-003 zamkniete (READY_FOR_DEPLOY).
GOAL:       Istnieje zweryfikowane, jedno zestawienie zbiorcze: dla kazdego modelu generatorow wideo AI (Kling, Seedance, Google Veo/Gemini Omni, Sora 2, MiniMax przez API) pelna charakterystyka — maks. dlugosc klipu, maks. rozdzielczosc, koszt 1 minuty Full HD, dzwiek i jezyk polski, API/SDK/MCP — bez punktow, rankingu i rekomendacji, z oznaczeniem pewnosci zrodel, tak aby wlasciciel mogl sam wybrac narzedzie.
KONIEC:     PRAWDA gdy scenariusze S-R18..S-R22 przechodza. Zadna zmiana poza allowlista.

ZADANIE: utworz plik `docs/research/ZERO-RESEARCH-005-zestawienie-zbiorcze/zestawienie_zbiorcze.md` (po polsku; nazwy techniczne bez znakow diakrytycznych) zlozony wylacznie z danych z zatwierdzonych plikow (tylko odczyt):
 - `docs/research/ZERO-RESEARCH-001-porownanie-generatorow-wideo/` (zestawienie.md oraz kling.md, seedance.md, veo.md, sora2.md, minimax.md),
 - `docs/research/ZERO-RESEARCH-002-audio-i-jezyk-polski/` (zestawienie_audio.md i pliki wezlow),
 - `docs/research/ZERO-RESEARCH-003-api-i-mcp-sterowanie/` (zestawienie_api_mcp.md i pliki wezlow).
Struktura pliku:
 1. Naglowek: data 2026-11-27, zakres, zasada "bez rankingu i rekomendacji; wybor nalezy do wlasciciela (ECHO-027)", legenda rzedow zrodel i oznaczen (NIEPOTWIERDZONE, odczyt posredni, BRAK DANYCH).
 2. Tabela 1 — parametry i koszt (wiersz = model): maks. dlugosc klipu (takze przedluzanie), maks. rozdzielczosc, cena za sekunde (z i bez audio, jesli sa), koszt 1 minuty Full HD (1080p) wg RESEARCH-001 (przy braku 1080p jawnie "brak 1080p" z rozdzielczoscia ceny), data cennika, dostepnosc. Kolejnosc: rosnaco po koszcie 1 minuty przy 1080p; modele bez ceny 1080p na koncu z adnotacja; modele niedostepne na samym koncu (kolejnosc zamowiona przez wlasciciela w ECHO-007).
 3. Tabela 2 — dzwiek i jezyk (ta sama kolejnosc wierszy): dzwiek natywny i zakres, jednoczesnosc audio i wideo, status polskiego (OFICJALNIE / W PRAKTYCE / BRAK DANYCH / NIE) i jezyki, lip-sync, liczba mowcow, wylaczenie muzyki, audio/glos jako wejscie, eksport audio, audio przy start-klatce i przedluzaniu.
 4. Tabela 3 — sterowanie z Claude Code (wiersz = dostawca/kanal): publiczne API i onboarding, zadania asynchroniczne i webhook, limity, start/koniec klatki, obrazy referencyjne postaci, oficjalne SDK, serwer MCP (oficjalny; spolecznosciowy z licencja i data), platformy posredniczace (z dowodem dostepnosci), minimalna sciezka sterowania.
 5. Rozbieznosci i luki: wszystko, co badania zglaszaja jako niezgodnosc miedzy soba lub BRAK DANYCH, z odnosnikiem do pliku zrodlowego.
 6. Zrodla: dla kazdej grupy pol — plik i sekcja zatwierdzonego badania, z hashem SHA-256 pliku zrodlowego.
 Bez kolumn z punktami, bez numeracji miejsc, bez sekcji OPINIA, bez wniosku, bez slow "najlepszy", "polecam", "warto wybrac".

REGULA PRZECIW SAMOOSZUKIWANIU:
 - Tylko dane z wymienionych plikow; zakaz dodawania faktow z pamieci i nowych odczytow sieci; zakaz wykonywania wywolan API, zakladania kont i kluczy.
 - Zakaz przepisywania punktow i rankingu z badan; wolno przepisac fakty (np. "polski: BRAK DANYCH"), nie oceny.
 - Zakaz uznawania rzedu 4-5 za potwierdzone; kazda taka komorka oznaczona NIEPOTWIERDZONE, tak jak w pliku zrodlowym.
 - Zakaz ukrywania rozbieznosci miedzy badaniami; zapisz je w sekcji 5.
 - Zakaz edycji plikow zrodlowych i poza allowlista.
 - Pisz plik etapami (kilka dopisan).

PROCEDURA NAPRAWCZA PRZY FAIL: Evaluator numeruje zarzuty (miejsce, punkt listy, reprodukcja). Operator (w obronie) odpowiada PRZYJMUJE/ODRZUCAM z dowodem; po werdykcie NAPRAW poprawia tylko wskazane pola.

ALLOWLISTA:
  - `docs/research/ZERO-RESEARCH-005-zestawienie-zbiorcze/zestawienie_zbiorcze.md` (nowy plik)
ZAKAZANE BEZWZGLEDNIE: `scenariusze/`, `autobot/`, `docs/analiza/`, `docs/audiobook/`, `docs/proces/`, `docs/przeglad-2026-11-27/`, `docs/rozbieznosci/`, `docs/research/ZERO-RESEARCH-001-*`, `-002-*`, `-003-*` (tylko odczyt), polecenia git zmieniajace stan (poza rola Integration), sekrety, wywolania sieci poza odczytem plikow repozytorium.

MIEJSCE PRACY: `docs/research/ZERO-RESEARCH-005-zestawienie-zbiorcze/`
BAZA:          HEAD galezi roboczej
OBIEG:         Operator -> Evaluator (10 punktow) -> Obrona przy zarzutach -> Final Control (per zarzut) -> Integration

RUNDA: w toku (rundy 1-3 z 3; licznik w rejestrze aktualizuje orkiestrator po zakonczeniu workflow)
