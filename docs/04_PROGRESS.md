# Bieżące postępy v2

## Bieżący etap
ETAP 0 — Środowisko i fundamenty

## Bieżąca wersja projektu
V0 / konfiguracja — repozytorium dokumentacyjne, bez aplikacji i testów

## Bieżący obszar pracy
Weryfikacja środowiska lokalnego, podstawowy przepływ pracy Git oraz uruchomienie Dockera i PostgreSQL.

## Nauka
**Ukończone:**
- Brak udokumentowanych dowodów ukończenia tematów z ETAPU 0.

**W toku:**
- Git: gałąź, commit i scalanie.
- Podstawy terminala oraz diagnozowanie dostępności poleceń w `PATH`.
- Docker i lokalne uruchamianie PostgreSQL.

## Budowanie
**Ukończone:**
- Repozytorium `enterprise-ai-workflow` istnieje i ma historię commitów na gałęzi `main`.
- Utworzono dokumentacyjne podstawy prowadzenia roadmapy, sprintów, postępów i decyzji.
- Polecenia `git` i `dotnet` są dostępne w bieżącym środowisku powłoki.

**W toku:**
- Potwierdzenie pełnego przepływu gałąź → commit → scalenie; bieżąca historia nie zawiera jeszcze dowodu scalenia gałęzi roboczej.
- Weryfikacja lub konfiguracja Pythona, Dockera i PostgreSQL; polecenia `python`, `docker` i `psql` nie były dostępne w `PATH` podczas przeglądu 2026-08-29.
- Uruchomienie prostego kontenera oraz lokalnego PostgreSQL.

## Sprawdzenie wiedzy
**Potrafię bez AI:**
- Brak zapisanych dowodów w `07_LEARNING_LOG.md` lub `COMPETENCY_MATRIX.md`; poziom wymaga sprawdzenia w praktyce.

**Jeszcze z pomocą:**
- Do zweryfikowania: wyjaśnienie różnicy między commitem, gałęzią i scaleniem.
- Do zweryfikowania: samodzielna diagnostyka polecenia niedostępnego w `PATH`.
- Do zweryfikowania: uruchomienie kontenera i połączenie z lokalnym PostgreSQL.

## Kryteria ukończenia
- [ ] Środowisko działa; Git i .NET są widoczne, a Python, Docker i PostgreSQL wymagają potwierdzenia lub konfiguracji.
- [ ] Repozytorium ma poprawny, samodzielnie wykonany przepływ pracy gałąź → commit → scalenie.
- [ ] Docker działa, a PostgreSQL można uruchomić lokalnie i wykonać na nim proste zapytanie.
- [ ] Wykonano proste żądanie HTTP do testowego API i wyjaśniono żądanie oraz odpowiedź.
- [ ] Podstawowe operacje ETAPU 0 zostały wykonane bez prowadzenia krok po kroku przez AI.

## Blokady
- Potencjalna blokada środowiskowa: `python`, `docker` i `psql` nie są obecnie wykrywane jako polecenia. Najpierw trzeba odróżnić brak instalacji od problemu z `PATH`.

## Otwarte luki w wiedzy
| Luka | Pewność 0–5 | Blokuje etap? | Powrót |
|---|---:|---|---|
| Git: samodzielny przepływ gałąź → commit → scalenie | do samooceny | Tak | Sprint 01 |
| Diagnostyka instalacji i zmiennej `PATH` | do samooceny | Tak | Sprint 01 |
| Docker i lokalny PostgreSQL | do samooceny | Tak | Sprint 01 |
| HTTP/REST: żądanie, odpowiedź, metody i kody stanu | do samooceny | Tak, przed zamknięciem ETAPU 0 | Po Sprint 01 |

## Następne 3 kroki
1. Sprawdzić instalację i `PATH` dla Pythona, Dockera i PostgreSQL, zapisując wyniki poleceń wersji.
2. Samodzielnie wykonać przepływ gałąź → mała zmiana → commit → scalenie i wskazać jego ślad w historii Git.
3. Uruchomić prosty kontener, następnie PostgreSQL, połączyć się z bazą i wykonać proste zapytanie.

## Bieżące ryzyka
- Rozszerzanie zakresu: rozpoczynanie ASP.NET Core lub modelowania V1 przed zamknięciem fundamentów ETAPU 0.
- Brak regularności: brak wpisów w `07_LEARNING_LOG.md`, więc nie ma jeszcze danych o rytmie pracy.
- Zbyt długie utknięcie: problemy instalacyjne mogą pochłonąć sprint; po 2–3 h należy zapisać diagnostykę i skorzystać z Tutora.
- Zbyt duża delegacja do AI: konfiguracja bez samodzielnego odtworzenia poleceń nie stanowi dowodu kompetencji.
- Perfekcjonizm: wystarczy działające środowisko i prosty scenariusz; optymalizacja konfiguracji nie jest celem sprintu.
