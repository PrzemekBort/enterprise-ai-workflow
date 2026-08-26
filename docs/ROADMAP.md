# Roadmap — Cloud / AI Engineer

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

---

# ETAP 0 — miesiąc 1
## Środowisko i fundamenty

### Zakres
- [ ] Git / GitHub
- [ ] Visual Studio / VS Code
- [ ] .NET SDK
- [ ] Python
- [ ] Docker
- [ ] PostgreSQL
- [ ] podstawy Linux/bash
- [ ] HTTP / REST / JSON

### Git praktycznie
- [ ] clone
- [ ] branch / switch
- [ ] add / commit / push / pull
- [ ] merge
- [ ] rebase
- [ ] stash

### Definition of Done
- [ ] repo `enterprise-ai-workflow` istnieje
- [ ] lokalne środowisko działa
- [ ] umiem samodzielnie pracować na branchach i commitach

---

# ETAP 1 — miesiące 2–4
## C# / .NET Backend

### Zakres
- [ ] ASP.NET Core
- [ ] REST
- [ ] Controllers / Minimal APIs
- [ ] dependency injection
- [ ] configuration
- [ ] middleware
- [ ] logging
- [ ] error handling
- [ ] validation
- [ ] EF Core
- [ ] migrations
- [ ] authentication
- [ ] authorization
- [ ] unit tests
- [ ] integration tests

### Projekt
**Enterprise Workflow API**

Model:
- Users
- Requests
- Documents
- Tasks
- Approvals
- AuditEvents

Przykładowe endpointy:
- POST /requests
- GET /requests
- GET /requests/{id}
- POST /requests/{id}/approve
- POST /requests/{id}/reject
- GET /requests/{id}/history

### Definition of Done
- [ ] API działa
- [ ] PostgreSQL działa
- [ ] EF Core + migrations działają
- [ ] walidacja i obsługa błędów są wdrożone
- [ ] podstawowe testy działają
- [ ] system uruchamia się przez Docker Compose
- [ ] potrafię wyjaśnić architekturę bez pomocy AI

---

# ETAP 2 — miesiące 5–6
## Python jako język AI

### Zakres
- [ ] typing
- [ ] dataclasses
- [ ] Pydantic
- [ ] async
- [ ] requests/httpx
- [ ] pytest
- [ ] logging
- [ ] environment variables
- [ ] FastAPI

### Projekt
**Document Service**

Endpointy:
- POST /documents
- GET /documents/{id}
- POST /documents/{id}/process

Pipeline:
dokument → ekstrakcja tekstu → storage / SQL

### Definition of Done
- [ ] Python service działa niezależnie
- [ ] komunikuje się z backendem lub bazą
- [ ] ma testy
- [ ] rozumiem odpowiedzialność .NET vs Python

---

# ETAP 3 — miesiące 7–9
## Azure + Docker + CI/CD

### Priorytet Azure
- [ ] Azure Container Apps
- [ ] Azure SQL
- [ ] Storage Account
- [ ] Key Vault
- [ ] Managed Identity
- [ ] Entra ID
- [ ] Application Insights
- [ ] Azure Monitor
- [ ] Service Bus
- [ ] API Management

### DevOps
- [ ] Dockerfile
- [ ] Docker Compose
- [ ] GitHub Actions
- [ ] build
- [ ] test
- [ ] Docker image
- [ ] deploy Azure

### Definition of Done
- [ ] .NET API działa w Azure
- [ ] Python service działa w Azure
- [ ] baza działa
- [ ] deployment jest automatyczny
- [ ] sekrety nie są w repo
- [ ] monitoring działa
- [ ] podstawowe security działa

---

# ETAP 4 — miesiące 10–12
## LLM Engineering

### Zakres
- [ ] LLM API
- [ ] tokens
- [ ] context window
- [ ] system/user messages
- [ ] structured output
- [ ] function calling
- [ ] embeddings
- [ ] temperature
- [ ] hallucinations
- [ ] retries
- [ ] rate limits
- [ ] cost tracking

### Projekt
**AI Document Processing**

Pipeline:
PDF → text extraction → LLM → structured JSON → validation → SQL

### Obowiązkowo
- [ ] schema validation
- [ ] business rules
- [ ] retry
- [ ] manual review
- [ ] audit log
- [ ] błędy modelu są obsługiwane

### Definition of Done
- [ ] LLM zwraca dane w kontrolowanym formacie
- [ ] model nie jest traktowany jako źródło prawdy
- [ ] potrafię wyjaśnić failure modes
- [ ] mierzę koszt i latency

---

# ETAP 5 — miesiące 13–15
## RAG

### Zakres
- [ ] embeddings
- [ ] vector search
- [ ] chunking
- [ ] metadata
- [ ] similarity
- [ ] hybrid search
- [ ] reranking

### Projekt
**Enterprise Knowledge Assistant**

Pipeline:
Documents → Chunking → Embeddings → Vector DB → Retrieval → Context → LLM → Answer

### Definition of Done
- [ ] odpowiedzi zawierają źródła
- [ ] potrafię mierzyć jakość retrievalu
- [ ] rozumiem wpływ chunkingu
- [ ] potrafię odróżnić problem retrievalu od problemu generacji

---

# ETAP 6 — miesiące 16–18
## Agents + Tool Calling

### Zakres
- [ ] tool calling
- [ ] bezpieczne wykonywanie akcji
- [ ] allowlist narzędzi
- [ ] walidacja parametrów
- [ ] audit log
- [ ] kontrola uprawnień

### Projekt
Przykład:
LLM → get_user_requests() → SQL → analiza → odpowiedź

Później:
LLM → check_request() → validate_documents() → start_workflow() → audit_log()

### Definition of Done
- [ ] agent może bezpiecznie wywołać wybrane narzędzia
- [ ] każda akcja jest audytowana
- [ ] krytyczne akcje są kontrolowane
- [ ] potrafię wyjaśnić ryzyko excessive agency

---

# ETAP 7 — miesiące 19–21
## Security + Production AI

### Identity
- [ ] OAuth 2.0
- [ ] OpenID Connect
- [ ] access tokens
- [ ] ID tokens
- [ ] scopes
- [ ] roles
- [ ] app registrations
- [ ] service principals
- [ ] managed identities

### AI Security
- [ ] prompt injection
- [ ] indirect prompt injection
- [ ] data exfiltration
- [ ] insecure tool calling
- [ ] excessive agency
- [ ] sensitive data exposure
- [ ] output validation

### Definition of Done
- [ ] RAG respektuje uprawnienia użytkownika
- [ ] API ma poprawną autoryzację
- [ ] sekrety i identity są poprawnie obsługiwane
- [ ] istnieje prosty threat model

---

# ETAP 8 — miesiące 22–24
## Production + rekrutacja

### Observability
- [ ] logs
- [ ] traces
- [ ] metrics
- [ ] Application Insights
- [ ] token usage
- [ ] latency
- [ ] cost

### Reliability
- [ ] retries
- [ ] timeout
- [ ] circuit breaker
- [ ] queues
- [ ] caching
- [ ] fallback

### AI Evaluation
- [ ] test dataset
- [ ] expected answers
- [ ] retrieval evaluation
- [ ] hallucination checks
- [ ] regression tests

### IaC
- [ ] Bicep
- [ ] opcjonalnie Terraform

### Definition of Done
- [ ] system działa end-to-end
- [ ] deployment jest powtarzalny
- [ ] security jest opisane
- [ ] monitoring działa
- [ ] istnieje dokumentacja architektury
- [ ] potrafię obronić decyzje projektowe na rozmowie technicznej
