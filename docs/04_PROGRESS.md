# Bieżące postępy v2

## Bieżący etap
ETAP 0 — Środowisko i fundamenty

## Bieżąca wersja projektu
V0 / konfiguracja — repozytorium dokumentacyjne, bez aplikacji i testów

## Bieżący sprint
Sprint 02 — HTTP/REST i domknięcie ETAPU 0

## Bieżący obszar pracy
HTTP/REST i praktyczne żądania do testowego API; przygotowanie do przeglądu końcowego ETAPU 0.

## Nauka
**Ukończone:**
- Git: gałąź, commit i scalanie.
- Podstawy terminala oraz diagnozowanie dostępności poleceń w `PATH`.
- Docker i lokalne uruchamianie PostgreSQL.

**W toku:**
- HTTP: żądanie i odpowiedź.
- Podstawowe metody i kody stanu.
- REST i JSON na poziomie praktycznym.

## Budowanie
**Ukończone:**
- Repozytorium `enterprise-ai-workflow` istnieje i ma historię commitów na gałęzi `main`.
- Środowisko lokalne zostało zweryfikowane: Git, .NET, Python i Docker są dostępne.
- Samodzielnie wykonano przepływ gałąź → commit → scalenie.
- Uruchomiono kontener PostgreSQL, wykonano zapytanie przed i po restarcie oraz bezpiecznie zatrzymano kontener.

**W toku:**
- Wykonanie prostego żądania GET do testowego API.
- Wykonanie żądania zawierającego JSON.
- Interpretacja metody, URL, statusu, nagłówków i body odpowiedzi.

## Sprawdzenie wiedzy
**Potwierdzone:**
- Git/GitHub: poziom 3 — samodzielne użycie.
- Docker: poziom 2 — rozumienie i użycie z pomocą.
- PostgreSQL: poziom 2 — rozumienie i użycie z pomocą.

**Do sprawdzenia w Sprincie 02:**
- Wyjaśnienie różnicy między żądaniem a odpowiedzią HTTP.
- Rozpoznawanie zastosowania GET i POST oraz podstawowych grup kodów stanu.
- Odróżnienie HTTP od JSON.
- Samodzielne wykonanie prostego żądania do testowego API.

## Kryteria ukończenia ETAPU 0
- [x] Środowisko działa; Git, .NET, Python i Docker są dostępne, a PostgreSQL działa w kontenerze.
- [x] Repozytorium ma poprawny, samodzielnie wykonany przepływ pracy gałąź → commit → scalenie.
- [x] Docker działa, a PostgreSQL można uruchomić lokalnie i wykonać na nim proste zapytanie.
- [ ] Wykonano proste żądanie HTTP do testowego API i wyjaśniono żądanie oraz odpowiedź.
- [ ] Przeprowadzono przegląd końcowy i potwierdzono podstawowe operacje ETAPU 0 bez prowadzenia krok po kroku przez AI.

## Blokady
- Brak blokady środowiskowej.
- HTTP/REST pozostaje jedynym niezrealizowanym obszarem blokującym ukończenie ETAPU 0.

## Otwarte luki w wiedzy
| Luka | Pewność 0–5 | Blokuje etap? | Powrót |
|---|---:|---|---|
| HTTP/REST: żądanie, odpowiedź, metody i kody stanu | do samooceny | Tak | Sprint 02 |
| Samodzielna diagnostyka Docker/PostgreSQL bez instrukcji | 2 | Nie | Naturalna dalsza praktyka |

## Następne 3 kroki
1. Własnymi słowami opisać przewidywany przebieg prostego żądania HTTP.
2. Wykonać i zinterpretować żądanie GET oraz żądanie zawierające JSON.
3. Zapisać dowód w dzienniku nauki i przeprowadzić przegląd końcowy ETAPU 0.

## Bieżące ryzyka
- Kopiowanie komend HTTP bez rozumienia ich elementów.
- Rozpoczęcie ASP.NET Core lub V1 przed zamknięciem ETAPU 0.
- Próba zapamiętania wszystkich kodów stanu zamiast opanowania podstawowych grup i najczęstszych przykładów.
