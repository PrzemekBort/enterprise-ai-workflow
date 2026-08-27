# Roadmap — Cloud / AI Engineer v2

## Cel końcowy

Po 18–24 miesiącach:

**Cloud / AI Engineer z doświadczeniem w budowie aplikacji biznesowych, automatyzacji procesów, integracji LLM, Azure, identity/security i SQL.**

Docelowy stack:
- C# / .NET / ASP.NET Core
- Python / FastAPI
- SQL / PostgreSQL / Azure SQL
- Azure Container Apps / Functions / Storage / Key Vault
- Entra ID / Managed Identity / RBAC
- Docker / Docker Compose
- GitHub Actions / CI/CD
- Bicep
- Service Bus
- Application Insights / Azure Monitor
- LLM APIs / Azure OpenAI
- RAG / vector search
- tool calling / agents
- AI evaluation / AI security

## Jak czytać roadmapę

Każdy etap ma cztery poziomy:

1. **Learn** — pojęcia, które trzeba rozumieć.
2. **Build** — rzeczy, które trzeba zastosować w projekcie.
3. **Knowledge Check** — rzeczy, które trzeba umieć wyjaśnić lub zrobić bez prowadzenia AI.
4. **Definition of Done** — warunek przejścia do kolejnego etapu.

Nie trzeba znać każdego tematu ekspercko. Celem jest przejście od rozumienia → praktyki → samodzielności.

---

# ETAP 0 — miesiąc 1
## Środowisko i fundamenty

### Learn
- [ ] Git: branch, commit, merge, rebase, stash
- [ ] podstawy terminala i Linux/bash
- [ ] HTTP: request/response, methods, status codes, headers
- [ ] REST i JSON na poziomie praktycznym

### Setup
- [ ] Git / GitHub
- [ ] Visual Studio / VS Code
- [ ] .NET SDK
- [ ] Python
- [ ] Docker
- [ ] PostgreSQL

### Build
- [ ] utwórz repo `enterprise-ai-workflow`
- [ ] wykonaj pierwszy branch → commit → merge
- [ ] uruchom prosty kontener Docker
- [ ] uruchom lokalnie PostgreSQL
- [ ] wykonaj prosty request HTTP do testowego API

### Knowledge Check
- [ ] potrafię wyjaśnić różnicę między commit, branch i merge
- [ ] potrafię wyjaśnić request vs response
- [ ] rozumiem podstawowe metody HTTP i status codes
- [ ] potrafię poruszać się po terminalu i katalogach

### Definition of Done
- [ ] środowisko działa
- [ ] repo istnieje i ma poprawny workflow Git
- [ ] Docker działa
- [ ] PostgreSQL działa lokalnie
- [ ] potrafię wykonać podstawowe operacje bez prowadzenia krok po kroku przez AI

---

# ETAP 1 — miesiące 2–4
## C# / .NET Backend

### Learn
- [ ] ASP.NET Core
- [ ] REST API design
- [ ] Controllers / Minimal APIs
- [ ] dependency injection
- [ ] configuration
- [ ] middleware
- [ ] logging
- [ ] error handling
- [ ] validation
- [ ] EF Core
- [ ] migrations
- [ ] unit tests
- [ ] integration tests
- [ ] podstawy authentication / authorization — koncepcyjnie

### Build
**Enterprise Workflow API**

Core concepts required in V1:
- User
- Request
- AuditEvent

Potential concept:
- Approval — jeśli wynika z Twojego modelu domenowego

Later versions:
- Document
- Task — dopiero gdy pojawi się realny use case

Endpointy:
- [ ] POST /requests
- [ ] GET /requests
- [ ] GET /requests/{id}
- [ ] POST /requests/{id}/approve
- [ ] POST /requests/{id}/reject
- [ ] GET /requests/{id}/history

Technicznie:
- [ ] PostgreSQL
- [ ] EF Core + migrations
- [ ] validation
- [ ] global error handling
- [ ] logging
- [ ] podstawowe unit tests
- [ ] integration tests
- [ ] Docker Compose dla API + DB

### Knowledge Check
- [ ] potrafię wyjaśnić lifetime: transient/scoped/singleton
- [ ] rozumiem rolę middleware
- [ ] potrafię wyjaśnić DbContext i migrations
- [ ] rozumiem różnicę unit vs integration test
- [ ] potrafię samodzielnie zdiagnozować typowy błąd połączenia API ↔ DB

### Definition of Done
- [ ] API działa end-to-end lokalnie
- [ ] baza działa i migracje są powtarzalne
- [ ] walidacja i obsługa błędów działają
- [ ] testy obejmują krytyczne ścieżki
- [ ] `docker compose up` uruchamia system
- [ ] potrafię wyjaśnić architekturę bez pomocy AI

> Pełne OAuth/OIDC i Entra zostają na późniejszy etap. Tutaj wystarczy rozumieć podstawy auth.

---

# ETAP 2 — miesiące 5–6
## Python jako język AI

### Learn
- [ ] typing
- [ ] dataclasses
- [ ] Pydantic
- [ ] async
- [ ] requests/httpx
- [ ] pytest
- [ ] logging
- [ ] environment variables
- [ ] FastAPI

### Build
**Document Service**
- [ ] system potrafi przyjąć dokument powiązany z requestem
- [ ] można pobrać informacje o dokumencie
- [ ] można zainicjować przetwarzanie dokumentu
- [ ] status i wynik przetwarzania są dostępne
- [ ] ekstrakcja tekstu działa bez AI
- [ ] metadata / wynik są zapisywane lub referencjonowane
- [ ] komunikacja z głównym backendem działa

> Kształt API, sync vs async oraz sposób komunikacji .NET ↔ Python pozostają Twoją decyzją projektową.

### Knowledge Check
- [ ] rozumiem różnicę między sync i async w Pythonie
- [ ] potrafię wyjaśnić rolę Pydantic
- [ ] potrafię napisać prosty endpoint FastAPI bez kopiowania gotowca
- [ ] rozumiem podział odpowiedzialności .NET vs Python

### Definition of Done
- [ ] Python service działa niezależnie
- [ ] komunikuje się z systemem
- [ ] ma testy
- [ ] ma logging i konfigurację przez env
- [ ] potrafię samodzielnie dodać nowy prosty endpoint

---

# ETAP 3 — miesiące 7–9
## Azure App Platform + Docker + CI/CD

### Learn
Priorytet podstawowy:
- [ ] Azure Container Apps
- [ ] Azure SQL
- [ ] Storage Account
- [ ] Key Vault
- [ ] Managed Identity
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
- [ ] build/test/deploy pipeline

### Build
- [ ] wdroż .NET API do Azure
- [ ] wdroż Python service
- [ ] podłącz Azure SQL
- [ ] użyj Storage Account
- [ ] sekrety przenieś do Key Vault
- [ ] użyj Managed Identity tam, gdzie ma sens
- [ ] włącz Application Insights
- [ ] zbuduj CI/CD w GitHub Actions

### Knowledge Check
- [ ] potrafię uzasadnić Container Apps vs App Service vs Functions w prostym scenariuszu
- [ ] rozumiem Managed Identity vs secret
- [ ] potrafię wyjaśnić, gdzie powinny znajdować się sekrety
- [ ] potrafię prześledzić pipeline od push do deploymentu
- [ ] rozumiem podstawowy przepływ logów i telemetry

### Definition of Done
- [ ] system działa w Azure
- [ ] deployment jest automatyczny
- [ ] sekrety nie są w repo
- [ ] monitoring działa
- [ ] aplikacja ma podstawowe identity/security
- [ ] potrafię odtworzyć deployment bez instrukcji krok po kroku

---

# ETAP 4 — miesiące 10–12
## LLM Engineering

### Learn
- [ ] LLM API
- [ ] tokens
- [ ] context window
- [ ] system/user messages
- [ ] structured output
- [ ] function calling — podstawy
- [ ] embeddings — intuicja, bez pełnego RAG
- [ ] temperature
- [ ] hallucinations
- [ ] retries
- [ ] rate limits
- [ ] cost tracking

### Build
**AI Document Processing**
- [ ] PDF → text extraction
- [ ] LLM → structured JSON
- [ ] schema validation
- [ ] business rules
- [ ] retry
- [ ] manual review
- [ ] audit log
- [ ] obsługa błędnych odpowiedzi modelu
- [ ] pomiar kosztu i latency

### Knowledge Check
- [ ] potrafię wyjaśnić, dlaczego LLM nie jest źródłem prawdy
- [ ] rozumiem structured output vs zwykły tekst
- [ ] potrafię wskazać failure modes
- [ ] rozumiem podstawową różnicę prompting vs validation

### Definition of Done
- [ ] system wyciąga dane z dokumentów do kontrolowanego schematu
- [ ] błędy modelu są obsługiwane
- [ ] istnieje manual review
- [ ] koszt i latency są mierzone
- [ ] potrafię wyjaśnić cały pipeline

---

# ETAP 5 — miesiące 13–15
## RAG

### Learn
- [ ] embeddings — praktycznie
- [ ] vector search
- [ ] chunking
- [ ] metadata
- [ ] similarity
- [ ] hybrid search
- [ ] reranking
- [ ] retrieval evaluation

### Build
**Enterprise Knowledge Assistant**
- [ ] ingestion dokumentów
- [ ] chunking
- [ ] embeddings
- [ ] vector store
- [ ] retrieval
- [ ] odpowiedź LLM
- [ ] cytowanie źródeł
- [ ] prosty zestaw testowy retrievalu

### Knowledge Check
- [ ] potrafię wyjaśnić wpływ chunk size
- [ ] rozumiem retrieval vs generation
- [ ] potrafię wskazać, czy problem leży w retrievalu czy modelu
- [ ] potrafię wyjaśnić po co reranking

### Definition of Done
- [ ] odpowiedzi mają źródła
- [ ] retrieval jest mierzalny
- [ ] potrafię porównać co najmniej dwa warianty chunkingu
- [ ] system nie polega wyłącznie na „wydaje się, że działa”

---

# ETAP 6 — miesiące 16–18
## Tool Calling + Agents + Messaging

### Learn
- [ ] tool calling
- [ ] allowlist narzędzi
- [ ] walidacja parametrów
- [ ] audit log
- [ ] kontrola uprawnień
- [ ] excessive agency
- [ ] Service Bus praktycznie
- [ ] queues/topics
- [ ] retries
- [ ] dead-letter queue
- [ ] idempotency
- [ ] eventual consistency

### Build
- [ ] agent odczytuje dane przez bezpieczne tools
- [ ] agent wykonuje wybraną akcję workflow
- [ ] akcje są audytowane
- [ ] mock workflow engine działa na potrzeby projektu
- [ ] Service Bus został przećwiczony praktycznie:
  - [ ] w głównym projekcie, jeśli istnieje uzasadniony use case
  - [ ] **albo** w małym laboratorium producer → queue → consumer → retry → DLQ
- [ ] w `DECISIONS.md` zapisano, dlaczego messaging został lub nie został użyty w głównym systemie

### Knowledge Check
- [ ] potrafię uzasadnić REST vs queue
- [ ] rozumiem idempotency
- [ ] rozumiem DLQ
- [ ] potrafię wyjaśnić ryzyko excessive agency
- [ ] potrafię wskazać, które akcje wymagają dodatkowego potwierdzenia

### Definition of Done
- [ ] agent bezpiecznie wywołuje wybrane narzędzia
- [ ] akcje są walidowane i audytowane
- [ ] krytyczne akcje są kontrolowane
- [ ] potrafię praktycznie użyć Service Bus i wyjaśnić retry / DLQ
- [ ] decyzja o użyciu lub nieużyciu messagingu w głównym projekcie jest uzasadniona
- [ ] failure handling jest udokumentowany

---

# ETAP 7 — miesiące 19–21
## Identity + Security + Production AI

### Learn
Identity:
- [ ] OAuth 2.0
- [ ] OpenID Connect
- [ ] access tokens
- [ ] ID tokens
- [ ] scopes
- [ ] roles
- [ ] app registrations
- [ ] service principals
- [ ] managed identities

AI Security:
- [ ] prompt injection
- [ ] indirect prompt injection
- [ ] data exfiltration
- [ ] insecure tool calling
- [ ] excessive agency
- [ ] sensitive data exposure
- [ ] output validation
- [ ] threat modeling — podstawy

### Build
- [ ] Entra authentication dla użytkownika
- [ ] authorization po rolach/scopes
- [ ] RAG respektuje uprawnienia
- [ ] narzędzia sprawdzają uprawnienia niezależnie od LLM
- [ ] prosty threat model
- [ ] testy negatywne security

### Knowledge Check
- [ ] potrafię wyjaśnić OAuth2 vs OIDC
- [ ] potrafię wyjaśnić access token vs ID token
- [ ] rozumiem zasadę least privilege
- [ ] potrafię wskazać typowy prompt injection flow
- [ ] potrafię opisać security boundary systemu

### Definition of Done
- [ ] użytkownik widzi tylko dane, do których ma dostęp
- [ ] RAG respektuje ACL/permissions
- [ ] tools nie ufają modelowi jako źródłu autoryzacji
- [ ] sekrety i identity są poprawnie obsługiwane
- [ ] istnieje threat model i testy security

---

# ETAP 8 — miesiące 22–24
## Production Hardening + Rekrutacja

### Learn
Observability:
- [ ] logs
- [ ] traces
- [ ] metrics
- [ ] Application Insights
- [ ] token usage
- [ ] latency
- [ ] cost

Reliability:
- [ ] retries — production patterns
- [ ] timeout
- [ ] circuit breaker
- [ ] queues — production usage
- [ ] caching
- [ ] fallback

AI Evaluation:
- [ ] test dataset
- [ ] expected answers
- [ ] retrieval evaluation
- [ ] hallucination checks
- [ ] regression tests

IaC:
- [ ] Bicep
- [ ] opcjonalnie Terraform

### Build
- [ ] observability end-to-end
- [ ] dashboard / podstawowe alerty
- [ ] retry/timeout/fallback tam, gdzie potrzebne
- [ ] AI regression tests
- [ ] Bicep dla kluczowych zasobów Azure
- [ ] dokumentacja architektury
- [ ] README projektu pod portfolio
- [ ] przykładowy ADR dla ważnej decyzji

### Knowledge Check
- [ ] potrafię prześledzić request end-to-end
- [ ] potrafię zdiagnozować awarię na podstawie logów/metryk
- [ ] potrafię obronić kluczowe decyzje architektoniczne
- [ ] potrafię wyjaśnić trade-offy koszt / niezawodność / złożoność
- [ ] potrafię przejść techniczny walkthrough projektu

### Definition of Done
- [ ] system działa end-to-end
- [ ] deployment jest powtarzalny
- [ ] security jest opisane
- [ ] monitoring działa
- [ ] reliability patterns są użyte celowo
- [ ] AI evaluation jest zautomatyzowane na podstawowym poziomie
- [ ] istnieje dokumentacja architektury i portfolio-ready README
- [ ] potrafię obronić system na rozmowie technicznej
