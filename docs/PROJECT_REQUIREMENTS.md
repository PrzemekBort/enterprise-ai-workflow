# Enterprise AI Workflow — Project Requirements

## 1. Purpose
`Enterprise AI Workflow` is a generic internal enterprise application for handling business requests, documents, approvals, workflow history and, in later versions, AI-assisted processing and actions.

This document defines **what the system is expected to do**, not how it must be implemented. Architectural and implementation decisions not explicitly constrained here remain the developer's responsibility.

## 2. Core business concept
A user creates an internal business request. A request may contain data and documents. It can move through a controlled workflow, be reviewed, approved or rejected, and retain a history of important actions.

Over time the system gains:
- document processing,
- cloud deployment,
- LLM-based document extraction,
- enterprise knowledge search / RAG,
- AI tool calling,
- enterprise identity and authorization,
- production observability and reliability.

## 3. Core business concepts
The system should eventually represent:
- **User** — person using the system,
- **Request** — business request,
- **Document** — file associated with a request,
- **Approval** — decision associated with a request,
- **Task** — work resulting from a process,
- **Audit Event** — record of an important action or state change.

This does not prescribe separate entities, aggregates, modules or services.

## 4. Request lifecycle

The initial V1 lifecycle is intentionally simple:

```text
Draft
  ↓
Submitted
  ├──→ Approved
  └──→ Rejected
```

`UnderReview`, `Completed` and other states may be introduced later only when a concrete business requirement justifies them.

The system must:
- reject invalid state transitions,
- preserve important lifecycle history,
- make the current state unambiguous.

Open decisions include transition rules, approval modeling and where workflow logic belongs.

---

# 5. V1 — Request Management

## Business goal
An employee can create and submit a request. An authorized reviewer can approve or reject it. Important actions remain visible in history.

In V1, user identity and reviewer permissions may be simulated or represented by a simplified application-level mechanism. Production identity and authorization are introduced in V7.

## Required capabilities
- create a request,
- retrieve one request,
- list requests,
- modify allowed data in an appropriate state,
- submit a request,
- approve a request,
- reject a request,
- view request history.

## Minimum request information
- unique identifier,
- author,
- title,
- description,
- status,
- creation timestamp,
- last modification timestamp.

## Business rules
- approval is allowed only from valid states,
- rejection is allowed only from valid states,
- invalid transitions are rejected,
- invalid input cannot silently create inconsistent data,
- important state-changing operations are recorded.

## Audit expectation
The system should answer: **who performed what action, when, and on which request?**

Example events:
- `RequestCreated`
- `RequestUpdated`
- `RequestSubmitted`
- `RequestApproved`
- `RequestRejected`

## Acceptance criteria
V1 is complete when:
- a request can be created,
- it can move through its intended lifecycle,
- invalid transitions are rejected,
- approve/reject work only when allowed,
- current state can be retrieved,
- meaningful history can be retrieved,
- invalid input is handled safely.

## Explicit non-requirements
V1 does not require:
- Entra ID,
- production-grade authorization,
- AI,
- cloud deployment,
- microservices,
- Service Bus,
- advanced document processing,
- complex frontend UI.

---

# 6. V2 — Documents and Document Processing

## Business goal
A request can contain documents. The system can process an uploaded document and expose processing status and result.

## Required document information
- identifier,
- file name,
- type/content type,
- size,
- upload timestamp,
- uploader,
- relationship to a request.

## Required capabilities
- attach a document to a request,
- accept it for processing,
- extract basic text/content without AI,
- store/reference the result,
- detect processing failure,
- expose processing status,
- retry failed processing where appropriate.

## Acceptance criteria
- documents can be attached,
- metadata is preserved,
- processing can succeed or fail explicitly,
- failure does not leave undefined state,
- retry is possible where allowed.

## Open decisions
- physical storage,
- metadata ownership,
- entity/aggregate modeling,
- API shape,
- sync vs async processing,
- .NET ↔ Python communication,
- retry semantics.

---

# 7. V3 — Cloud Deployment

## Business goal
The application operates as a cloud-hosted system in Azure.

## Required capabilities
- application backend,
- database,
- document storage,
- safe secret/config handling,
- automated deployment,
- monitoring.

## Acceptance criteria
- core application works in Azure,
- deployment is repeatable,
- secrets are not stored in source code,
- health/failures are observable,
- database and document storage work from the deployed application.

A cloud service should be introduced only to solve a concrete requirement.

---

# 8. V4 — AI Document Processing

## Business goal
The system uses an LLM to extract structured business information from documents.

Example:

```text
Invoice.pdf
    ↓
AI processing
    ↓
{
  "invoiceNumber": "...",
  "seller": "...",
  "amount": 1234.56,
  "currency": "PLN",
  "date": "..."
}
```

The schema is illustrative.

## Required capabilities
- send extracted content to an LLM,
- structured output,
- schema validation,
- business validation,
- missing/invalid value handling,
- retry where justified,
- manual review,
- accept/reject AI extraction,
- audit important AI actions,
- measure basic latency and cost.

## Core rule
**The LLM is not the source of truth.**

## Acceptance criteria
- at least one document type can be converted to structured data,
- malformed output is handled,
- invalid data can be rejected,
- a human can review extracted data,
- important actions are auditable,
- latency and cost can be observed.

## Open decisions
- document type,
- schema,
- prompts,
- model,
- retry rules,
- confidence representation,
- review flow,
- storage of extracted data.

---

# 9. V5 — Enterprise Knowledge Assistant

## Business goal
A user can ask questions about documents available in the system and receive an answer supported by sources.

## Required capabilities
- ingest documents into a searchable pipeline,
- retrieve relevant content,
- generate an answer using retrieved content,
- identify source material.

## Core rule
An answer without source information is not a complete implementation.

## Acceptance criteria
- user can ask a question,
- relevant content is retrieved,
- answer contains source references,
- retrieval can be evaluated,
- retrieval failures can be distinguished from generation failures.

## Open decisions
- vector store,
- chunking,
- metadata,
- retrieval algorithm,
- hybrid search,
- reranking,
- evaluation dataset and metrics.

---

# 10. V6 — AI Assistant and Tool Calling

## Business goal
AI can interact with selected application functions, not only generate text.

Examples:
- `get_user_requests(...)`
- `submit_request(...)`

## Required capabilities
- limited explicit tool set,
- parameter validation,
- authorization outside the LLM,
- action audit,
- stronger controls for state-changing actions,
- safe failure handling.

## Core rules
- the LLM is not the authorization authority,
- tools do not trust model-generated identity/permissions,
- state-changing actions require stronger controls than read-only actions.

## Acceptance criteria
- at least one read-only tool works,
- at least one controlled state-changing tool works,
- invalid calls are rejected,
- unauthorized calls are rejected,
- actions are auditable,
- failure handling is defined.

## Open decisions
- tool contracts,
- confirmation requirements,
- orchestration,
- service boundaries,
- sync vs async execution,
- messaging use.

---

# 11. V7 — Enterprise Identity and Security

## Business goal
Users and AI-assisted functionality respect real enterprise identity and authorization boundaries.

## Required capabilities
- Entra ID authentication,
- roles/scopes or equivalent,
- authorization for business operations,
- request/document permissions,
- permission-aware RAG,
- least privilege,
- secure service-to-service identity,
- safe secret handling.

## Core security rule
**If a user cannot access a resource through the normal application/API, AI and RAG must not expose it either.**

## Acceptance criteria
- authenticated users have identifiable permissions,
- unauthorized API operations are rejected,
- unauthorized documents are not exposed through RAG,
- AI tools enforce authorization independently of the model,
- service identities use least privilege,
- a basic threat model exists.

---

# 12. V8 — Production Hardening

## Business goal
The application behaves like an operational system rather than only a prototype.

## Required capabilities

### Observability
- logs,
- metrics,
- traces,
- request correlation,
- AI latency,
- token/cost usage,
- meaningful health information.

### Reliability
Where justified:
- retries,
- timeouts,
- circuit breaking,
- queues,
- caching,
- fallback behavior.

### AI quality
- evaluation dataset,
- expected behavior,
- retrieval evaluation,
- regression checks,
- hallucination/error checks.

### Infrastructure and documentation
- repeatable IaC for key Azure resources,
- architecture description,
- important decisions,
- operational assumptions,
- portfolio-ready README.

## Acceptance criteria
- important requests can be traced end-to-end,
- common failures can be diagnosed from telemetry,
- deployment/infrastructure is repeatable,
- reliability mechanisms are deliberate,
- AI behavior has repeatable basic evaluation,
- architecture and trade-offs are documented.

---

# 13. Global project constraints

## Prefer simplicity
Use the simplest reasonable architecture that satisfies the **current** version.

## Technology must solve a problem
Do not introduce messaging, microservices, caching, extra databases, orchestration frameworks or cloud services only because they may be useful later.

## Incremental architecture is expected
Refactoring is allowed and expected. Early decisions do not have to survive to V8.

## One main product
The main project remains `Enterprise AI Workflow`. Small labs may be used to learn isolated concepts.

---

# 14. Out of scope unless explicitly added later
- production-quality visual design,
- mobile application,
- Kubernetes,
- custom LLM training,
- advanced ML model development,
- full BPMN/workflow engine,
- ERP-scale functionality,
- complex multi-tenancy,
- billing,
- dozens of workflow types,
- microservices for every component,
- AWS/GCP versions.

A simple graphical interface may exist, but frontend engineering is not a primary requirement.

---

# 15. Decisions intentionally left open
The following are intentionally not predefined:
- domain model details,
- database schema,
- solution/project structure,
- controllers vs minimal APIs,
- error model,
- validation implementation,
- audit implementation,
- workflow implementation,
- module boundaries,
- .NET ↔ Python communication,
- file storage strategy,
- sync vs async processing,
- REST vs messaging,
- Service Bus usage,
- AI integration design,
- prompts,
- RAG architecture,
- vector storage,
- chunking,
- authorization model,
- reliability mechanisms.

Important decisions should be recorded in `DECISIONS.md`.

---

# 16. Reviewer guidance

A Reviewer evaluates the implementation against the **current project version**, not against an imagined final architecture.

The Reviewer should ask:
1. Does the implementation satisfy current business requirements?
2. Are acceptance criteria met?
3. Are business invariants enforced?
4. Is the solution unnecessarily complex?
5. Was any technology introduced without a concrete requirement?
6. Are important decisions justified?
7. Are later-version features being implemented prematurely?
8. Does the current design create a serious problem for the next known stage?
9. Are current security boundaries respected?
10. Does the developer understand and own the implementation?

A valid V1 solution should not be rejected because it does not yet contain V7/V8 mechanisms.

---

# 17. Initial implementation brief

> Build the backend of a system in which a user can create a business request, submit it for review, and another user can approve or reject it. The system must enforce valid state transitions and preserve the history of important operations.

This defines required behavior. The developer decides how the solution is modeled and implemented.
