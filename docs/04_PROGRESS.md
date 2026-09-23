# Bieżące postępy v2

## Bieżący etap
ETAP 0 — Środowisko i fundamenty, ukończony 2026-09-23

## Bieżąca wersja projektu
V0 / konfiguracja — repozytorium dokumentacyjne, bez aplikacji i testów

## Bieżący sprint
Sprint 02 — ukończony 2026-09-23

## Bieżący obszar pracy
Planowanie ETAPU 1 i zakresu pierwszej wersji API Wniosków. Implementacja V1 jeszcze się nie rozpoczęła.

## Nauka
**Ukończone:**
- Git: gałąź, commit i scalanie.
- Podstawy terminala oraz diagnozowanie dostępności poleceń w `PATH`.
- Docker i lokalne uruchamianie PostgreSQL.
- HTTP: żądanie i odpowiedź.
- Podstawowe metody i kody stanu.
- REST i JSON na poziomie praktycznym.

## Budowanie
**Ukończone:**
- Repozytorium `enterprise-ai-workflow` istnieje i ma historię commitów na gałęzi `main`.
- Środowisko lokalne zostało zweryfikowane: Git, .NET, Python i Docker są dostępne.
- Samodzielnie wykonano przepływ gałąź → commit → scalenie.
- Uruchomiono kontener PostgreSQL, wykonano zapytanie przed i po restarcie oraz bezpiecznie zatrzymano kontener.
- Wykonanie prostego żądania GET do testowego API.
- Wykonanie żądania zawierającego JSON.
- Interpretacja metody, URL, statusu, nagłówków i body odpowiedzi.

## Sprawdzenie wiedzy
**Potwierdzone:**
- Git/GitHub: poziom 3 — samodzielne użycie.
- Docker: poziom 2 — rozumienie i użycie z pomocą.
- PostgreSQL: poziom 2 — rozumienie i użycie z pomocą.
- HTTP/REST: poziom 3 — samodzielne podstawowe użycie.
- Wyjaśnienie różnicy między żądaniem a odpowiedzią HTTP.
- Rozpoznawanie zastosowania GET i POST oraz podstawowych grup kodów stanu.
- Odróżnienie HTTP od JSON.
- Samodzielne wykonanie prostego żądania do testowego API.

## Kryteria ukończenia ETAPU 0
- [x] Środowisko działa; Git, .NET, Python i Docker są dostępne, a PostgreSQL działa w kontenerze.
- [x] Repozytorium ma poprawny, samodzielnie wykonany przepływ pracy gałąź → commit → scalenie.
- [x] Docker działa, a PostgreSQL można uruchomić lokalnie i wykonać na nim proste zapytanie.
- [x] Wykonano proste żądanie HTTP do testowego API i wyjaśniono żądanie oraz odpowiedź.
- [x] Przeprowadzono przegląd końcowy i potwierdzono podstawowe operacje ETAPU 0 bez prowadzenia krok po kroku przez AI.

## Blokady
- Brak

## Otwarte luki w wiedzy
| Luka | Pewność 0–5 | Blokuje etap? | Powrót |
|---|---:|---|---|
| Samodzielna diagnostyka Docker/PostgreSQL bez instrukcji | 2 | Nie | Naturalna dalsza praktyka |

## Następne 3 kroki
1. Ustalić ograniczony zakres kolejnego sprintu w ETAPIE 1 na podstawie roadmapy i wymagań V1.
2. Zaplanować pierwsze ćwiczenie C# / ASP.NET Core bez przedwczesnego projektowania całego systemu.
3. Utrwalać diagnostykę Docker/PostgreSQL przy okazji naturalnej pracy z projektem.

## Bieżące ryzyka
- Przedwczesne rozszerzenie V1 o mechanizmy późniejszych wersji.
