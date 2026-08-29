# Roadmapa — Inżynier chmury / AI v2

## Cel końcowy

Po 18–24 miesiącach:

**Inżynier chmury / AI z doświadczeniem w budowie aplikacji biznesowych, automatyzacji procesów, integracji LLM, Azure, tożsamości/bezpieczeństwie i SQL.**

Docelowy stos technologiczny:
- C# / .NET / ASP.NET Core
- Python / FastAPI
- SQL / PostgreSQL / Azure SQL
- Azure Container Apps / Functions / Storage / Key Vault
- Entra ID / Tożsamość zarządzana / RBAC
- Docker / Docker Compose
- GitHub Actions / CI/CD
- Bicep
- Service Bus
- Application Insights / Azure Monitor
- API LLM / Azure OpenAI
- RAG / wyszukiwanie wektorowe
- wywoływanie narzędzi / agenci
- ocena AI / bezpieczeństwo AI

## Jak czytać roadmapę

Każdy etap ma cztery poziomy:

1. **Nauka** — pojęcia, które trzeba rozumieć.
2. **Budowanie** — rzeczy, które trzeba zastosować w projekcie.
3. **Sprawdzenie wiedzy** — rzeczy, które trzeba umieć wyjaśnić lub zrobić bez prowadzenia AI.
4. **Kryteria ukończenia** — warunek przejścia do kolejnego etapu.

Nie trzeba znać każdego tematu ekspercko. Celem jest przejście od rozumienia → praktyki → samodzielności.

---

# ETAP 0 — miesiąc 1
## Środowisko i fundamenty

### Nauka
- [ ] Git: gałąź, commit, scalanie, rebase, schowek
- [ ] podstawy terminala i Linux/bash
- [ ] HTTP: żądanie/odpowiedź, metody, kody stanu, nagłówki
- [ ] REST i JSON na poziomie praktycznym

### Konfiguracja
- [ ] Git / GitHub
- [ ] Visual Studio / VS Code
- [ ] .NET SDK
- [ ] Python
- [ ] Docker
- [ ] PostgreSQL

### Budowanie
- [ ] utwórz repo `enterprise-ai-workflow`
- [ ] wykonaj pierwszą gałąź → commit → scalenie
- [ ] uruchom prosty kontener Docker
- [ ] uruchom lokalnie PostgreSQL
- [ ] wykonaj proste żądanie HTTP do testowego API

### Sprawdzenie wiedzy
- [ ] potrafię wyjaśnić różnicę między commitem, gałęzią i scaleniem
- [ ] potrafię wyjaśnić żądanie a odpowiedź
- [ ] rozumiem podstawowe metody HTTP i kody stanu
- [ ] potrafię poruszać się po terminalu i katalogach

### Kryteria ukończenia
- [ ] środowisko działa
- [ ] repozytorium istnieje i ma poprawny przepływ pracy Git
- [ ] Docker działa
- [ ] PostgreSQL działa lokalnie
- [ ] potrafię wykonać podstawowe operacje bez prowadzenia krok po kroku przez AI

---

# ETAP 1 — miesiące 2–4
## Zaplecze C# / .NET

### Nauka
- [ ] ASP.NET Core
- [ ] projektowanie REST API
- [ ] kontrolery / minimalne API
- [ ] wstrzykiwanie zależności
- [ ] konfiguracja
- [ ] middleware
- [ ] rejestrowanie zdarzeń
- [ ] obsługa błędów
- [ ] walidacja
- [ ] EF Core
- [ ] migracje
- [ ] testy jednostkowe
- [ ] testy integracyjne
- [ ] podstawy uwierzytelniania / autoryzacji — koncepcyjnie

### Budowanie
**API korporacyjnego przepływu pracy**

Główne pojęcia wymagane w V1:
- Użytkownik
- Wniosek
- Zdarzenie audytowe

Potencjalne pojęcie:
- Zatwierdzenie — jeśli wynika z Twojego modelu domenowego

Późniejsze wersje:
- Dokument
- Zadanie — dopiero gdy pojawi się rzeczywisty przypadek użycia

Endpointy:
- [ ] POST /requests
- [ ] GET /requests
- [ ] GET /requests/{id}
- [ ] POST /requests/{id}/approve
- [ ] POST /requests/{id}/reject
- [ ] GET /requests/{id}/history

Technicznie:
- [ ] PostgreSQL
- [ ] EF Core + migracje
- [ ] walidacja
- [ ] globalna obsługa błędów
- [ ] rejestrowanie zdarzeń
- [ ] podstawowe testy jednostkowe
- [ ] testy integracyjne
- [ ] Docker Compose dla API + DB

### Sprawdzenie wiedzy
- [ ] potrafię wyjaśnić czasy życia: przejściowy/o określonym zakresie/pojedynczy
- [ ] rozumiem rolę middleware
- [ ] potrafię wyjaśnić DbContext i migracje
- [ ] rozumiem różnicę między testem jednostkowym a integracyjnym
- [ ] potrafię samodzielnie zdiagnozować typowy błąd połączenia API ↔ DB

### Kryteria ukończenia
- [ ] API działa lokalnie od początku do końca
- [ ] baza działa i migracje są powtarzalne
- [ ] walidacja i obsługa błędów działają
- [ ] testy obejmują krytyczne ścieżki
- [ ] `docker compose up` uruchamia system
- [ ] potrafię wyjaśnić architekturę bez pomocy AI

> Pełne OAuth/OIDC i Entra zostają na późniejszy etap. Tutaj wystarczy rozumieć podstawy uwierzytelniania i autoryzacji.

---

# ETAP 2 — miesiące 5–6
## Python jako język AI

### Nauka
- [ ] typowanie
- [ ] klasy danych
- [ ] Pydantic
- [ ] programowanie asynchroniczne
- [ ] requests/httpx
- [ ] pytest
- [ ] rejestrowanie zdarzeń
- [ ] zmienne środowiskowe
- [ ] FastAPI

### Budowanie
**Usługa dokumentów**
- [ ] system potrafi przyjąć dokument powiązany z wnioskiem
- [ ] można pobrać informacje o dokumencie
- [ ] można zainicjować przetwarzanie dokumentu
- [ ] status i wynik przetwarzania są dostępne
- [ ] ekstrakcja tekstu działa bez AI
- [ ] metadane / wynik są zapisywane lub wskazywane przez odwołanie
- [ ] komunikacja z głównym zapleczem działa

> Kształt API, przetwarzanie synchroniczne lub asynchroniczne oraz sposób komunikacji .NET ↔ Python pozostają Twoją decyzją projektową.

### Sprawdzenie wiedzy
- [ ] rozumiem różnicę między kodem synchronicznym i asynchronicznym w Pythonie
- [ ] potrafię wyjaśnić rolę Pydantic
- [ ] potrafię napisać prosty endpoint FastAPI bez kopiowania gotowca
- [ ] rozumiem podział odpowiedzialności .NET vs Python

### Kryteria ukończenia
- [ ] usługa Python działa niezależnie
- [ ] komunikuje się z systemem
- [ ] ma testy
- [ ] ma rejestrowanie zdarzeń i konfigurację przez zmienne środowiskowe
- [ ] potrafię samodzielnie dodać nowy prosty endpoint

---

# ETAP 3 — miesiące 7–9
## Platforma aplikacyjna Azure + Docker + CI/CD

### Nauka
Priorytet podstawowy:
- [ ] Azure Container Apps
- [ ] Azure SQL
- [ ] Konto magazynu Azure
- [ ] Key Vault
- [ ] Tożsamość zarządzana
- [ ] Entra ID — integracja aplikacji
- [ ] Application Insights
- [ ] Azure Monitor

Wprowadzenie, bez głębokiego wdrażania:
- [ ] Service Bus — po co istnieje
- [ ] API Management — po co istnieje

DevOps:
- [ ] Dockerfile
- [ ] Docker Compose
- [ ] GitHub Actions
- [ ] potok budowania/testowania/wdrażania

### Budowanie
- [ ] wdroż .NET API do Azure
- [ ] wdroż usługę Python
- [ ] podłącz Azure SQL
- [ ] użyj konta magazynu Azure
- [ ] sekrety przenieś do Key Vault
- [ ] użyj tożsamości zarządzanej tam, gdzie ma sens
- [ ] włącz Application Insights
- [ ] zbuduj CI/CD w GitHub Actions

### Sprawdzenie wiedzy
- [ ] potrafię uzasadnić wybór Container Apps, App Service lub Functions w prostym scenariuszu
- [ ] rozumiem różnicę między tożsamością zarządzaną a sekretem
- [ ] potrafię wyjaśnić, gdzie powinny znajdować się sekrety
- [ ] potrafię prześledzić potok od wypchnięcia zmian do wdrożenia
- [ ] rozumiem podstawowy przepływ logów i telemetrii

### Kryteria ukończenia
- [ ] system działa w Azure
- [ ] wdrożenie jest automatyczne
- [ ] sekrety nie są w repo
- [ ] monitorowanie działa
- [ ] aplikacja ma podstawową obsługę tożsamości/bezpieczeństwa
- [ ] potrafię odtworzyć wdrożenie bez instrukcji krok po kroku

---

# ETAP 4 — miesiące 10–12
## Inżynieria LLM

### Nauka
- [ ] LLM API
- [ ] tokeny
- [ ] okno kontekstowe
- [ ] komunikaty systemowe/użytkownika
- [ ] ustrukturyzowane dane wyjściowe
- [ ] wywoływanie funkcji — podstawy
- [ ] osadzenia — intuicja, bez pełnego RAG
- [ ] temperatura
- [ ] halucynacje
- [ ] ponowienia
- [ ] limity częstotliwości
- [ ] śledzenie kosztów

### Budowanie
**Przetwarzanie dokumentów przez AI**
- [ ] PDF → ekstrakcja tekstu
- [ ] LLM → ustrukturyzowany JSON
- [ ] walidacja schematu
- [ ] reguły biznesowe
- [ ] ponowienie
- [ ] ręczny przegląd
- [ ] dziennik audytu
- [ ] obsługa błędnych odpowiedzi modelu
- [ ] pomiar kosztu i opóźnienia

### Sprawdzenie wiedzy
- [ ] potrafię wyjaśnić, dlaczego LLM nie jest źródłem prawdy
- [ ] rozumiem różnicę między ustrukturyzowanymi danymi wyjściowymi a zwykłym tekstem
- [ ] potrafię wskazać tryby awarii
- [ ] rozumiem podstawową różnicę między tworzeniem promptów a walidacją

### Kryteria ukończenia
- [ ] system wyciąga dane z dokumentów do kontrolowanego schematu
- [ ] błędy modelu są obsługiwane
- [ ] istnieje ręczny przegląd
- [ ] koszt i opóźnienie są mierzone
- [ ] potrafię wyjaśnić cały potok

---

# ETAP 5 — miesiące 13–15
## RAG

### Nauka
- [ ] osadzenia — praktycznie
- [ ] wyszukiwanie wektorowe
- [ ] dzielenie na fragmenty
- [ ] metadane
- [ ] podobieństwo
- [ ] wyszukiwanie hybrydowe
- [ ] ponowne szeregowanie wyników
- [ ] ocena wyszukiwania

### Budowanie
**Asystent wiedzy przedsiębiorstwa**
- [ ] wprowadzanie dokumentów
- [ ] dzielenie na fragmenty
- [ ] osadzenia
- [ ] magazyn wektorowy
- [ ] wyszukiwanie
- [ ] odpowiedź LLM
- [ ] cytowanie źródeł
- [ ] prosty zestaw testowy wyszukiwania

### Sprawdzenie wiedzy
- [ ] potrafię wyjaśnić wpływ rozmiaru fragmentu
- [ ] rozumiem różnicę między wyszukiwaniem a generowaniem
- [ ] potrafię wskazać, czy problem leży w wyszukiwaniu, czy w modelu
- [ ] potrafię wyjaśnić, po co ponownie szeregować wyniki

### Kryteria ukończenia
- [ ] odpowiedzi mają źródła
- [ ] wyszukiwanie jest mierzalne
- [ ] potrafię porównać co najmniej dwa warianty dzielenia na fragmenty
- [ ] system nie polega wyłącznie na „wydaje się, że działa”

---

# ETAP 6 — miesiące 16–18
## Wywoływanie narzędzi + agenci + komunikacja asynchroniczna

### Nauka
- [ ] wywoływanie narzędzi
- [ ] lista dozwolonych narzędzi
- [ ] walidacja parametrów
- [ ] dziennik audytu
- [ ] kontrola uprawnień
- [ ] nadmierna autonomia
- [ ] Service Bus praktycznie
- [ ] kolejki/tematy
- [ ] ponowienia
- [ ] kolejka utraconych wiadomości
- [ ] idempotencja
- [ ] spójność ostateczna

### Budowanie
- [ ] agent odczytuje dane przez bezpieczne narzędzia
- [ ] agent wykonuje wybraną akcję przepływu pracy
- [ ] akcje są audytowane
- [ ] pozorowany silnik przepływu pracy działa na potrzeby projektu
- [ ] Service Bus został przećwiczony praktycznie:
  - [ ] w głównym projekcie, jeśli istnieje uzasadniony przypadek użycia
  - [ ] **albo** w małym laboratorium producent → kolejka → konsument → ponowienie → DLQ
- [ ] w `DECISIONS.md` zapisano, dlaczego komunikacja asynchroniczna została lub nie została użyta w głównym systemie

### Sprawdzenie wiedzy
- [ ] potrafię uzasadnić wybór REST lub kolejki
- [ ] rozumiem idempotencję
- [ ] rozumiem DLQ
- [ ] potrafię wyjaśnić ryzyko nadmiernej autonomii
- [ ] potrafię wskazać, które akcje wymagają dodatkowego potwierdzenia

### Kryteria ukończenia
- [ ] agent bezpiecznie wywołuje wybrane narzędzia
- [ ] akcje są walidowane i audytowane
- [ ] krytyczne akcje są kontrolowane
- [ ] potrafię praktycznie użyć Service Bus i wyjaśnić ponowienie / DLQ
- [ ] decyzja o użyciu lub nieużyciu komunikacji asynchronicznej w głównym projekcie jest uzasadniona
- [ ] obsługa awarii jest udokumentowana

---

# ETAP 7 — miesiące 19–21
## Tożsamość + bezpieczeństwo + produkcyjne AI

### Nauka
Tożsamość:
- [ ] OAuth 2.0
- [ ] OpenID Connect
- [ ] tokeny dostępu
- [ ] tokeny identyfikacyjne
- [ ] zakresy
- [ ] role
- [ ] rejestracje aplikacji
- [ ] jednostki usługi
- [ ] tożsamości zarządzane

Bezpieczeństwo AI:
- [ ] wstrzykiwanie promptów
- [ ] pośrednie wstrzykiwanie promptów
- [ ] eksfiltracja danych
- [ ] niebezpieczne wywoływanie narzędzi
- [ ] nadmierna autonomia
- [ ] ujawnienie danych wrażliwych
- [ ] walidacja danych wyjściowych
- [ ] modelowanie zagrożeń — podstawy

### Budowanie
- [ ] uwierzytelnianie Entra dla użytkownika
- [ ] autoryzacja według ról/zakresów
- [ ] RAG respektuje uprawnienia
- [ ] narzędzia sprawdzają uprawnienia niezależnie od LLM
- [ ] prosty model zagrożeń
- [ ] negatywne testy bezpieczeństwa

### Sprawdzenie wiedzy
- [ ] potrafię wyjaśnić różnicę między OAuth2 a OIDC
- [ ] potrafię wyjaśnić różnicę między tokenem dostępu a tokenem identyfikacyjnym
- [ ] rozumiem zasadę najmniejszych uprawnień
- [ ] potrafię wskazać typowy przebieg wstrzykiwania promptu
- [ ] potrafię opisać granicę bezpieczeństwa systemu

### Kryteria ukończenia
- [ ] użytkownik widzi tylko dane, do których ma dostęp
- [ ] RAG respektuje listy kontroli dostępu/uprawnienia
- [ ] narzędzia nie ufają modelowi jako źródłu autoryzacji
- [ ] sekrety i tożsamość są poprawnie obsługiwane
- [ ] istnieje model zagrożeń i testy bezpieczeństwa

---

# ETAP 8 — miesiące 22–24
## Wzmocnienie produkcyjne + Rekrutacja

### Nauka
Obserwowalność:
- [ ] logi
- [ ] ślady
- [ ] metryki
- [ ] Application Insights
- [ ] wykorzystanie tokenów
- [ ] opóźnienie
- [ ] koszt

Niezawodność:
- [ ] ponowienia — wzorce produkcyjne
- [ ] limit czasu
- [ ] bezpiecznik
- [ ] kolejki — wykorzystanie produkcyjne
- [ ] buforowanie
- [ ] zachowanie awaryjne

Ocena AI:
- [ ] testowy zbiór danych
- [ ] oczekiwane odpowiedzi
- [ ] ocena wyszukiwania
- [ ] kontrole halucynacji
- [ ] testy regresji

IaC:
- [ ] Bicep
- [ ] opcjonalnie Terraform

### Budowanie
- [ ] obserwowalność od początku do końca
- [ ] panel / podstawowe alerty
- [ ] ponowienie/limit czasu/zachowanie awaryjne tam, gdzie potrzebne
- [ ] testy regresji AI
- [ ] Bicep dla kluczowych zasobów Azure
- [ ] dokumentacja architektury
- [ ] README projektu do portfolio
- [ ] przykładowy ADR dla ważnej decyzji

### Sprawdzenie wiedzy
- [ ] potrafię prześledzić żądanie od początku do końca
- [ ] potrafię zdiagnozować awarię na podstawie logów/metryk
- [ ] potrafię obronić kluczowe decyzje architektoniczne
- [ ] potrafię wyjaśnić kompromisy dotyczące kosztu / niezawodności / złożoności
- [ ] potrafię przeprowadzić techniczne omówienie projektu

### Kryteria ukończenia
- [ ] system działa od początku do końca
- [ ] wdrożenie jest powtarzalne
- [ ] bezpieczeństwo jest opisane
- [ ] monitorowanie działa
- [ ] wzorce niezawodności są użyte celowo
- [ ] ocena AI jest zautomatyzowana na podstawowym poziomie
- [ ] istnieje dokumentacja architektury i README gotowy do portfolio
- [ ] potrafię obronić system na rozmowie technicznej
