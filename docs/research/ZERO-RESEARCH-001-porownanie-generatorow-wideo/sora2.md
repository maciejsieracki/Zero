# ZERO-RESEARCH-001 — wezel d: OpenAI Sora 2 / Sora 2 Pro

Data odczytu: 2026-11-27. Runda 1 z 3. Operator (wezel d).

## Wniosek glowny (najwazniejsze dla wyboru narzedzia)

**Na dzien 2026-11-27 Sora 2 NIE jest dostepna przez API.** OpenAI wylaczyl Videos API oraz modele `sora-2`, `sora-2-pro` (i ich snapshoty, m.in. `sora-2-pro-2025-10-06`) **2026-09-24**. Tabela deprecations nie wskazuje zastepcy. Aplikacja i strona Sora (konsumencka) zostaly zamkniete wczesniej, **2026-04-26**. Zrodla rzedu 1: deprecations OpenAI, artykul pomocy OpenAI "What to know about the Sora discontinuation", strona referencyjna "Create a video" (komunikat o trwalym wylaczeniu 2026-09-24).

Ponizsze ceny to **ostatni oficjalny cennik API przed wylaczeniem**. Sa podane wylacznie dla porownania; **nie da sie z nich dzis skorzystac**. W zestawieniu ten dostawca powinien trafic na koniec z oznaczeniem "NIEDOSTEPNE (API wylaczone 2026-09-24)".

Kanal posredni: Azure OpenAI (Microsoft Foundry) oferowal Sore 2 w preview. Watek na forum OpenAI (rzad 4, NIEPOTWIERDZONE) podaje, ze Azure zakonczyl wsparcie wczesniej, 2026-06-06. Strona learn.microsoft.com byla zablokowana w sieci tej sesji, wiec dostepnosci przez Azure nie potwierdzilem. Agregatory (fal.ai, OpenRouter, Picsart i inne, rzad 4-5) korzystaly z API OpenAI, wiec po 2026-09-24 nie powinny dzialac. NIEPOTWIERDZONE.

## Tabela modeli (ostatni cennik standard, pay-as-you-go API, z natywnym audio)

| Model / wariant | Maks. 1 klip (s) | Maks. rozdzielczosc | 1080p? | Natywne audio | Cena USD/s | Rozdzielczosc ceny | Koszt 1 min (USD) | 1080p w koszcie? | Data cennika | Pewnosc |
|---|---|---|---|---|---|---|---|---|---|---|
| sora-2 (najtanszy) | 20 (rozbieznosc: 12) | 1280x720 / 720x1280 | NIE | TAK | 0.10 | 720p | 6.00 | NIE | odczyt 2026-11-27 (cennik archiwalny) | srednia |
| sora-2-pro 720p | 20 (rozbieznosc: 12) | 1920x1080 | TAK | TAK | 0.30 | 720p | 18.00 | NIE | odczyt 2026-11-27 | srednia |
| sora-2-pro 1024p | 20 (rozbieznosc: 12) | 1920x1080 | TAK | TAK | 0.50 | 1024p (1792x1024) | 30.00 | NIE | odczyt 2026-11-27 | srednia |
| sora-2-pro 1080p (najlepszy) | 20 (rozbieznosc: 12) | 1920x1080 / 1080x1920 | TAK | TAK | 0.70 | 1080p | 42.00 | TAK | changelog 2026-03-12 | srednia |

Dostepnosc na 2026-11-27 dla wszystkich wierszy: **NIE** (API wylaczone 2026-09-24).

## Rachunek kosztu krok po kroku

- sora-2, 720p: 0.10 USD/s x 60 s = **6.00 USD/min**. Model nie ma 1080p, wiec to koszt przy najwyzszej dostepnej rozdzielczosci (720p), nie przy Full HD.
- sora-2-pro, 720p: 0.30 x 60 = **18.00 USD/min**
- sora-2-pro, 1024p: 0.50 x 60 = **30.00 USD/min**
- sora-2-pro, 1080p: 0.70 x 60 = **42.00 USD/min**. To liczba docelowa dla Full HD.
- Dla porownania, tier Batch (asynchroniczny, nie do zwyklej pracy interaktywnej): 720p 0.15, 1024p 0.25, 1080p 0.35 USD/s, czyli przy 1080p 0.35 x 60 = 21.00 USD/min. Nie uzywam go jako liczby docelowej.
- Brak wariantu "bez audio" z osobna cena: audio generuje sie zawsze, w jednej cenie. Nie ma wiec ryzyka pomieszania wariantow z dzwiekiem i bez.
- Abonamentu (ChatGPT Plus/Pro) nie uzylem jako podstawy. Aplikacja Sora i tak jest zamknieta od 2026-04-26.

## Uwagi o niepewnosci i o tym, czego nie potwierdzilem

1. **Dostep do zrodel rzedu 1 byl tylko posredni.** Hosty developers.openai.com, openai.com, platform.openai.com, help.openai.com i learn.microsoft.com sa zablokowane w sieci tej sesji (ENOTFOUND). Tresc stron oficjalnych odczytalem przez wyniki wyszukiwarki (WebSearch z filtrem domen OpenAI), a nie przez bezposrednie pobranie. Dlatego pewnosc liczb to **srednia**, a nie wysoka. Evaluator powinien potwierdzic liczby bezposrednim pobraniem.
2. **Maks. dlugosc klipu jest rozbiezna.** Changelog z 2026-03-12 ("longer Sora generations") i Prompting Guide podaja `seconds` = 4, 8, 12, 16, 20, czyli maks. 20 s. Strona referencyjna "Create a video" w wyniku wyszukiwania pokazywala tylko 4, 8, 12, czyli maks. 12 s. Prompting Guide jest oznaczony jako archiwalny. Przyjmuje 20 s jako wartosc po aktualizacji z marca 2026. Dla obu wariantow liczba jest niepewna.
3. **Cena 720p sora-2-pro:** jeden fragment strony cennika pokazywal 0.15 (tier Batch) bez etykiety. Wartosc standard 0.30 pochodzi z drugiego fragmentu tej samej strony i ze strony modelu.
4. **Data cennika:** strona pricing nie podaje daty publikacji. Jedyna konkretna data to changelog 2026-03-12, ktory wprowadzil 1080p za 0.70 USD/s. Dla pozostalych pozycji data to data odczytu.
5. **Azure OpenAI:** dostepnosci Sory 2 na Azure po 2026-06-06 nie potwierdzilem (NIEPOTWIERDZONE, rzad 4).
6. Strony agregatorow (BenchLM, CometAPI, eesel.ai, dev.to, wavespeed, invideo, Wikipedia) potwierdzaja ceny i daty wylaczenia. Sa to zrodla rzedu 4-5, tylko poszlaka (NIEPOTWIERDZONE).

## Zrodla

| # | URL | Rzad | Co potwierdza | Data odczytu |
|---|---|---|---|---|
| 1 | https://developers.openai.com/api/docs/deprecations | 1 | wylaczenie Videos API, sora-2, sora-2-pro i snapshotow 2026-09-24, brak zastepcy | 2026-11-27 (przez wyszukiwarke) |
| 2 | https://help.openai.com/en/articles/20001152-what-to-know-about-the-sora-discontinuation | 1 | aplikacja zamknieta 2026-04-26, API wylaczone 2026-09-24 | 2026-11-27 (przez wyszukiwarke) |
| 3 | https://developers.openai.com/api/reference/resources/videos/methods/create | 1 | komunikat o trwalym wylaczeniu 2026-09-24; `seconds` 4/8/12 | 2026-11-27 (przez wyszukiwarke) |
| 4 | https://developers.openai.com/api/docs/pricing | 1 | sora-2 720p 0.10; sora-2-pro 720p 0.30, 1024p 0.50, 1080p 0.70; Batch 0.15/0.25/0.35 | 2026-11-27 (przez wyszukiwarke) |
| 5 | https://developers.openai.com/api/docs/models/sora-2 | 1 | sora-2: 0.10 USD/s, 720x1280 i 1280x720 | 2026-11-27 (przez wyszukiwarke) |
| 6 | https://developers.openai.com/api/docs/models/sora-2-pro | 1 | ceny sora-2-pro wg rozdzielczosci | 2026-11-27 (przez wyszukiwarke) |
| 7 | https://developers.openai.com/api/docs/changelog | 1 | 2026-03-12: dluzsze generacje, 1080p dla sora-2-pro za 0.70 USD/s, extensions, Batch | 2026-11-27 (przez wyszukiwarke) |
| 8 | https://developers.openai.com/cookbook/examples/sora/sora2_prompting_guide.md | 1 (archiwalny) | `seconds` 4/8/12/16/20; rozmiary sora-2-pro do 1920x1080; dialog w promptcie | 2026-11-27 (przez wyszukiwarke) |
| 9 | https://openai.com/index/sora-2/ | 1 | natywne audio (mowa, efekty, tlo); komunikat "As of April 26, 2026, the Sora product is no longer available" | 2026-11-27 (przez wyszukiwarke) |
| 10 | https://community.openai.com/t/azure-openai-is-prematurely-cutting-off-support-for-sora-2-too-early/1380475 | 4 | Azure: koniec wsparcia 2026-06-06 (NIEPOTWIERDZONE) | 2026-11-27 |
| 11 | https://benchlm.ai/media-pricing/sora | 4 | te same ceny (NIEPOTWIERDZONE) | 2026-11-27 |
| 12 | https://dev.to/mr_manushukla/sora-2-and-the-videos-api-shut-down-on-24-september-2026-the-migration-and-the-real-cost-per-second-bek | 5 | data wylaczenia (NIEPOTWIERDZONE) | 2026-11-27 |
