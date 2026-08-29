# Wytyczne dotyczące repozytorium

## Struktura projektu i organizacja modułów

To repozytorium koncentruje się obecnie na dokumentacji; projekty aplikacji i testów jeszcze nie istnieją. Wytyczne projektu znajdują się w `docs/`:

- `03_PROJECT_REQUIREMENTS.md` definiuje zachowanie produktu i kryteria akceptacji.
- `02_ROADMAP.md` definiuje kolejność nauki i docelowy stos technologiczny.
- `05_SPRINT.md` i `04_PROGRESS.md` śledzą bieżącą pracę.
- `DECISIONS.md` zapisuje wybory architektoniczne w formie uproszczonych wpisów ADR.
- `.codex/agents/` zawiera projektowe definicje Inżyniera, Tutora i Recenzenta.

Po rozpoczęciu implementacji używaj czytelnych ścieżek najwyższego poziomu, takich jak `src/Workflow.Api/`, `services/document-service/` i `tests/`. Dodawaj technologię tylko na potrzeby bieżącego wymagania; odłożone pomysły zapisuj w `docs/LATER.md`.

## Polecenia budowania, testowania i pracy lokalnej

Nie istnieją jeszcze manifesty budowania ani uruchamialne usługi. Roadmapa przewiduje:

- `dotnet build` — kompiluje rozwiązanie ASP.NET Core.
- `dotnet test` — uruchamia testy .NET.
- `pytest` — uruchamia testy usługi Python.
- `docker compose up` — uruchamia docelowy zestaw API i bazy danych.

Po wprowadzeniu zweryfikowanych poleceń opisz je w `docs/01_README.md`.

## Styl kodowania i konwencje nazewnictwa

Stosuj domyślne ustawienia formaterów oraz wcięcia o szerokości czterech spacji w C# i Pythonie. Używaj `PascalCase` dla typów i publicznych składowych C#, `camelCase` dla zmiennych lokalnych oraz `snake_case` dla modułów i funkcji Pythona. Nazywaj testy według zachowania, na przykład `ApproveRequest_WhenSubmitted_ChangesStatus` lub `test_rejects_invalid_transition`. Zachowuj spójną terminologię w Markdown (`Wniosek`, `Dokument`, `Zdarzenie audytowe`).

## Wytyczne dotyczące testowania

Traktuj priorytetowo reguły cyklu życia, nieprawidłowe przejścia, walidację, historię audytu i ścieżki błędów. Reguły biznesowe obejmuj testami jednostkowymi, a granice API i bazy danych — testami integracyjnymi. Przed naprawą błędu preferuj przygotowanie nieprzechodzącego testu regresji. Nie określono progu pokrycia; obejmij testami krytyczne ścieżki akceptacji z `docs/03_PROJECT_REQUIREMENTS.md`.

## Wytyczne dotyczące commitów i żądań scalenia

Krótka historia repozytorium używa zwięzłych polskich tematów commitów (na przykład `Aktualizacja plików projektowych`). Utrzymuj wąski zakres commitów, a w tematach stosuj tryb rozkazujący lub opis rezultatu. Żądanie scalenia powinno wyjaśniać cel, podsumowywać zmiany, wymieniać polecenia weryfikacyjne, wskazywać powiązane zgłoszenie lub element sprintu oraz zawierać zrzuty ekranu zmian interfejsu. Wyróżniaj migracje, zmiany konfiguracji i nierozstrzygnięte kompromisy.

## Instrukcje dla agentów

Traktuj `docs/02_ROADMAP.md` i `docs/03_PROJECT_REQUIREMENTS.md` jako pliki tylko do odczytu, chyba że deweloper wyraźnie zatwierdzi zmiany. Nie implementuj funkcji, nie wybieraj architektury ani nie poprawiaj uwag z przeglądu bez wyraźnej prośby. Podczas przeglądu zgłaszaj uwagi bez edytowania; podczas debugowania zacznij od hipotez i kroków diagnostycznych. Projektowe role `inzynier`, `tutor` i `recenzent` są zdefiniowane w `.codex/agents/` i mogą być wskazywane przy delegowaniu odpowiednich zadań.
