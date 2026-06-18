# Course: Constructor Gears for Developers

> A 4-hour, hands-on online course that introduces **Constructor Fabric Gears** —
> a secure and modular framework for building service platforms.

---

## Course Metadata

| Field | Value |
|-------|-------|
| **Title** | Constructor Gears for Developers |
| **Duration** | 4.5 hours of learning materials |
| **Level** | Beginner → Intermediate |
| **Format** | Recorded lessons + demos + offline exercises |
| **Delivery** | Self-paced online course |

### Who this course is for

- Backend and platform developers building **XaaS / SaaS** products
- Engineers coming from **Go, C#, Java, Python, or TypeScript**
- Teams exploring Gears for a **new product** or for **adding it into an existing platform**
- GenAI builders who need a secure, multi-tenant platform base

### Background prerequisite

- **No deep Rust knowledge is required.** If you know backend or service development in any typed language, that is enough.
- A short intro module explains only the terms you need for the examples.
- Rust is used in the code, but learning Rust is **not** the main goal of the course.

### Tooling prerequisites (sent before the course)

- Rust stable toolchain + Cargo (Edition 2024, MSRV 1.95.0)
- `protoc` (Protocol Buffers compiler)
- SQLite (bundled or in-memory is fine) — no external database required
- An IDE with `rust-analyzer` (VS Code or similar)
- Git (with submodule support)

### Learning outcomes

By the end of the course, participants will be able to:

1. Explain **what XaaS is** and the main things teams must build for it: multi-tenancy, access control, licensing, usage tracking, security, APIs, scaling, operations, and compliance.
2. Explain **what Gears is**, who should use it, when it fits well, and when it does not.
3. Explain at a high level **why the implementation approach matters** and what benefits it gives teams using Gears.
4. Describe the main parts of a gear and the **three-tier architecture**: Toolkit, System gears, and Service gears.
5. Run a Gears workspace locally, see which gears are active, and open the generated API docs.
6. Explain the core Gears model: **gear contract**, **gear implementation**, **application**, **runtime**, and **plugin extension points**.
7. Follow one request from start to finish through routing, security, business logic, data access, response building, and error handling.
8. Understand **security by default**: tenancy, policy-based authorization, licensing, usage tracking, and compliance support.
9. Explain the **AI-native developer experience**: spec-driven development, Constructor Studio workflows, traceability, and local-first quality loops.
10. Plan a first greenfield Gear using a practical implementation checklist.
11. Choose how to integrate Gears into an existing platform through plugins, GTS-based custom types, native UI integration, and custom logic/FaaS hooks.
12. Debug common beginner problems using API docs, config, logs, tests, and framework feedback while understanding how local composition maps to real deployment profiles.

---

## Time Budget at a Glance (270 min)

| # | Module | Time | Recorded format |
|---|--------|------|-----------------|
| 0 | Welcome, setup & course vocabulary | 15 min | Orientation + primer |
| 1 | XaaS development and why Gears exists | 25 min | Concept lesson |
| 2 | What is Gears and why its implementation approach helps | 25 min | Concept lesson + diagrams |
| 3 | Run Gears locally with `cargo gears` / quickstart | 20 min | Demo + offline exercise |
| 4 | Gear anatomy using one running example | 30 min | Code walkthrough |
| 5 | Request lifecycle: route → auth → domain → DB → response | 30 min | End-to-end trace |
| 6 | Gears mental model: contract, app, runtime, plugins | 30 min | Architecture walkthrough |
| 7 | Security, tenancy, licensing, usage, compliance | 30 min | Architecture walkthrough |
| 8 | AI-native dev experience | 30 min | Workflow + tooling walkthrough |
| 9 | Adoption Path A — Gears adoption for a new (greenfield) projects | 25 min | Guided implementation plan |
| 10 | Adoption Path B — Gears adoption in existing platforms and services | 30 min | Integration walkthrough |
| 11 | Wrap-up, roadmap, next steps | 10 min | Summary |


---

## Module 0 — Welcome, Setup & Course Vocabulary (15 min)

**Goal:** give learners just enough vocabulary to follow the code examples without turning the course into a Rust class.

- 0.1 Course orientation and how to use the offline exercises (3 min)
- 0.2 Environment checklist — toolchain, `protoc`, SQLite, IDE, Git (4 min)
- 0.3 Just-enough vocabulary for this course (8 min)
  - Strong typing and explicit errors, explained simply
  - Why the implementation language helps with safety and predictable behavior
  - Interfaces, generated helpers, and common framework patterns
  - The goal: feel comfortable reading the examples shown in the course

> **Reference:** [docs/WHY_GEARS.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/WHY_GEARS.md) Part A (A.1–A.11)

---

## Part 1 — Understanding XaaS & the Gears Mental Model

### Module 1 — XaaS Development and Why Gears Exists (25 min)

**Goal:** explain why Gears is more than a framework: it gives you reusable building blocks for the hard but common parts of XaaS systems.

- 1.1 What "XaaS" means (4 min)
  - **X-as-a-Service** means software that runs as an ongoing service for many customers instead of software that customers install and manage themselves
  - It is a broad term that includes SaaS, PaaS, IaaS, and similar service models
  - The vendor — not the customer — handles planning, development, operations, security, upgrades, and SLAs
- 1.2 XaaS development requirements (9 min)
  - **Multi-tenancy & isolation** — many customers share infrastructure, but their data must stay separate
  - **Fine-grained access control** — control who can see or change which data
  - **Licensing & entitlement validation** — check at request time which features a customer can use
  - **Feature usage tracking (→ billing)** — measure API calls, compute, storage, or tokens per tenant, user, or resource
  - **Reliable APIs** — versioned, documented, paginated, filterable, with predictable errors
  - **Flexible integration surfaces** — connect existing native UIs, provider systems, custom data types, and customer-specific logic without rewriting the core platform
  - **Scalability & operability** — health checks, tracing, rate limits, lifecycle, and migrations
  - **Strong security** — layered protection, secret handling, controlled network access, secure data flow
  - **Compliance & certifications** — support for needs like GDPR, HIPAA, SOC 2 / ISO 27001, and FIPS 140-3
- 1.3 How Gears maps to the XaaS backbone (10 min)

| XaaS concern | How Gears delivers it |
|--------------|------------------------|
| Multi-tenancy & isolation | Built-in tenant scoping and isolation patterns across APIs, services, and data access |
| Granular access control | Policy-based authorization with safe defaults and scoped data access |
| Licensing & entitlements | Request-time checks with pluggable licensing integrations |
| Usage metering → billing | Usage collection and quota hooks that can later feed billing |
| Rich & reliable APIs | Consistent API rules, generated docs, filtering, and predictable errors |
| Flexible integrations | Plugin-based integrations, native UI embedding options, extensible GTS data types, and custom logic hooks / FaaS-style workflows |
| Scalability & operability | Health checks, tracing, rate limits, lifecycle management, and migration support |
| High security standards | Secure-by-default request flow, credential handling, and framework guardrails |
| Compliance & certifications | Ready-to-use building blocks such as crypto support, audit trails, and tenant isolation |

- 1.4 Current-state note: implemented capabilities vs target architecture (2 min)
  - How to read docs that separate implemented, partially implemented, and planned gears

> **References:** [docs/slides/1_OVERVIEW.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/slides/1_OVERVIEW.md) ("Principle 6 — XaaS backbone", Part 6),
> [docs/WHY_GEARS.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/WHY_GEARS.md) (Executive Summary, B.1–B.13), [docs/security/SECURITY.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/security/SECURITY.md),
> [docs/GEARS.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/GEARS.md) (Usage Collector, Quota Enforcer, Audit)

### Module 2 — What Is Gears and Why Its Implementation Approach Helps (25 min)

**Goal:** explain clearly what Gears is and why its implementation approach helps platform teams, without making the course about the language itself.

- 2.1 What is Gears, for whom, and what it is not (5 min)
  - Gears is a framework and middleware layer, not a ready-made SaaS product
  - It is for XaaS/SaaS vendors, platform teams, GenAI builders, edge/on-prem vendors, and enterprise integration teams
  - It is not a tiny micro-framework, a service catalog, or a PaaS
- 2.2 Why the implementation choice helps (8 min)
  - Safer defaults and fewer common runtime failures
  - Predictable performance and deployment size across cloud, edge, and on-prem setups
  - Clearer contracts, explicit error handling, and stronger framework feedback
  - You do **not** need deep language knowledge to follow the course
- 2.3 The running example used in the rest of the course (7 min)
  - **Todo Tasks Gear**: list, create, update, and delete tasks
  - Public contract, API layer, business logic, and storage layer
  - Optional extension points for notifications, search, or auth provider integration
- 2.4 What beginners can safely ignore at first (5 min)
  - Language internals, macro details, transport internals, and advanced deployment details

> **References:** [docs/WHY_GEARS.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/WHY_GEARS.md) Part A, [docs/slides/1_OVERVIEW.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/slides/1_OVERVIEW.md) (Parts 1, 4, 5),
> [docs/GEARS.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/GEARS.md), [docs/toolkit_unified_system/README.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/toolkit_unified_system/README.md)

### Module 3 — Run Gears Locally with `cargo gears` / Quickstart (20 min)

**Goal:** let learners run a working system early, before the architecture feels too abstract.

- 3.1 Quickstart path for existing repository (5 min)
  - `make example` / `make quickstart`
  - Health endpoint and `/cf/docs` Swagger UI
  - OpenAPI export
- 3.2 `cargo gears` workspace path (8 min)
  - `cargo gears new /tmp/cf-demo`
  - `cargo gears run --app quickstart --env dev`
  - Generated server under `.gears/<name>/`
  - `GEARS_CONFIG` and runtime config files
- 3.3 Source inspection and manifest commands (4 min)
  - `cargo gears manifest validate`
  - `cargo gears manifest ls`
  - `cargo gears ls modules`
  - `cargo gears src` / `cargo gears help topic`
- 3.4 Offline exercise (3 min)
  - Run the server, open the docs, export OpenAPI, and identify which gears are active

> **References:** [docs/QUICKSTART_GUIDE.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/QUICKSTART_GUIDE.md), [cargo-rust repo README.md](https://github.com/constructorfabric/cargo-gears/blob/main/README.md)

### Module 4 — Gear Anatomy Using One Running Example (35 min)

**Goal:** make the structure of a gear easy to understand by using the Todo Tasks Gear as a running example.

- 4.1 Workspace and folder structure (7 min)
  - Public contract package
  - Gear implementation package
  - API layer, business logic layer, and infrastructure layer
- 4.2 Contract-first design (5 min)
  - Why the public contract stays stable while the implementation changes over time
  - Public clients and shared models as the boundary between gears
  - Clear error shapes that do not depend on a specific transport
- 4.3 API layer walkthrough (6 min)
  - Route definitions and versioned API paths
  - Auth expectations, entitlement checks, response shapes, and documented errors
- 4.4 Domain layer walkthrough (6 min)
  - Business rules, validation, and authorization entry points
  - No framework, database, or HTTP types in the domain layer
- 4.5 Infra layer walkthrough (4 min)
  - Repository ownership, migrations, and tenant-aware data access
- 4.6 Custom data Types
  - GTS (Global Type System)
  - Type registry
  - Extending of API endpoints with custom data types
- 4.7 Beginner mental checklist (2 min)
  - "If I add a feature, which layer should I change?"

> **References:** [docs/slides/1_OVERVIEW.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/slides/1_OVERVIEW.md) ("Gear anatomy"), [docs/GEARS.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/GEARS.md),
> [docs/toolkit_unified_system/README.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/toolkit_unified_system/README.md)

---

## Part 2 — Request Flow, Security, and APIs

### Module 5 — Request Lifecycle: Route → Auth → Domain → DB → Response (30 min)

**Goal:** trace one real request from start to finish so learners can see where the main Gears concepts appear.

- 5.1 Trace `GET /todo-tasks/v1/tasks` (6 min)
  - API Gateway middleware stack
  - Request ID, tracing, timeout/body limits, auth, license, router
- 5.2 Route definition and API contract (5 min)
  - HTTP method, versioned path, operation name, and summary
  - Auth and entitlement expectations
  - Generated API docs and standard error responses
- 5.3 Handler and DTO boundary (4 min)
  - Extract query options, request DTO, and `SecurityContext`
  - Return a response DTO, not internal domain types
- 5.4 Domain service and authorization boundary (5 min)
  - Policy decisions, permission checks, and scoped business logic
  - How authorization decisions affect what data is visible
- 5.5 Repository and scoped DB access (5 min)
  - Tenant-aware and policy-aware data access
  - Filtering, sorting, and pagination at the API boundary
- 5.6 Response and error mapping (3 min)
  - Standard error categories
  - RFC-9457 `Problem` responses
- 5.7 Offline exercise (2 min)
  - Pick one endpoint from Swagger UI and write down its request lifecycle

> **References:** [docs/slides/1_OVERVIEW.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/slides/1_OVERVIEW.md) ("Request lifecycle"),
> [docs/security/SECURITY.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/security/SECURITY.md), [docs/WHY_GEARS.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/WHY_GEARS.md) (B.3, B.4, B.7, B.10)

### Module 6 — Gears Mental Model: Contract, App, Runtime, Plugins (30 min)

**Goal:** give new developers a practical map of the main Gears building blocks after they have seen a real request.

- 6.1 Gear vs module vs service boundary (6 min)
  - A gear is a unit of capability with a public contract, lifecycle, and optional API
  - The application is the place that selects and wires gears together
  - A capability can start local and move across boundaries later if needed
- 6.2 The core vocabulary (10 min)
  - **Contract** — the stable public interface that other gears or apps depend on
  - **Implementation** — the API, business logic, and infrastructure behind that contract
  - **Application** — what assembles multiple gears into one runnable system
  - **Runtime** — what starts, wires, and stops the system
  - **Plugin** — a replaceable implementation behind a stable public surface
- 6.3 Application runtime and lifecycle (6 min)
  - How gears are discovered, initialized, wired together, and started
  - Where config, migrations, and startup decisions fit
- 6.4 Local-first composition model (4 min)
  - The same logical building blocks are used whether components run together or separately
  - Why this matters when moving from prototype to production
- 6.5 Why the mental model matters for beginners (4 min)
  - How to decide where to add a route, client, config, plugin, or migration

> **References:** [docs/slides/1_OVERVIEW.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/slides/1_OVERVIEW.md) (Parts 4, 5, 7), [docs/GEARS.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/GEARS.md),
> [docs/toolkit_unified_system/README.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/toolkit_unified_system/README.md), [docs/TOOLKIT_PLUGINS.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/TOOLKIT_PLUGINS.md)

### Module 7 — Security, Tenancy, Licensing, Usage, Compliance (30 min)

**Goal:** explain the secure-by-default path after learners have seen a real request and the main building blocks.

- 7.1 The linear security data-path (4 min)
  - Static checks → authentication → authorization → database scoping → credentials and egress
- 7.2 Authentication & authorization (7 min)
  - The gateway checks identity and passes security context inward
  - The policy engine makes the decision and can return data visibility rules
  - The system fails closed when decisions or constraints are missing
- 7.3 Tenant isolation by default (5 min)
  - Why tenant-aware data access is built into the flow instead of being left to convention
  - Why missing tenant filters become much harder to write by accident
- 7.4 Licensing and usage enforcement (5 min)
  - Entitlement checks at request time
  - Usage collection now, billing integration later
- 7.5 Typed extension points for secure platforms (5 min)
  - Shared definitions for settings, permissions, events, and provider contracts
  - How this supports plugins and platform integrations safely
- 7.6 Compliance enablers and responsibility boundaries (4 min)
  - FIPS 140-3 support, auditability, access trails, and tenant isolation
  - What Gears gives you versus what product and process certification still requires

> **References:** [docs/security/SECURITY.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/security/SECURITY.md), [docs/slides/1_OVERVIEW.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/slides/1_OVERVIEW.md) (Part 6),
> [docs/WHY_GEARS.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/WHY_GEARS.md) (B.3, B.4, B.9, B.12), [docs/arch/authorization/DESIGN.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/arch/authorization/DESIGN.md)

### Module 8 — AI-native Dev Experience (30 min)

**Goal:** show how Gears supports an AI-native, local-first developer workflow where specs, code, tests, and architecture feedback stay connected.

- 8.1 Spec-Driven Development in practice (7 min)
  - Requirements, design, architecture decision records, decomposition, and feature specs live alongside the code
  - The specs are not separate ceremony; they guide implementation, review, and long-term maintenance
  - Traceability matters because teams need to keep docs, code, and intent aligned as products evolve
- 8.2 Constructor Studio workflow (6 min)
  - Constructor Studio helps drive the flow from requirements to implementation and tests
  - It helps keep documentation and code consistent, with traceability across artifacts and code changes
  - It supports AI-assisted development without making architecture and quality rules optional
- 8.3 Shift-left local quality loop (7 min)
  - Local build, lint, unit, integration, and E2E feedback before CI
  - Generated docs, config inspection, logs, and framework feedback for troubleshooting
  - Why fast local feedback is especially important when AI accelerates change volume
- 8.4 Composition and deployment ergonomics (4 min)
  - Compose gears locally first, then carry the same logical model into cloud, hybrid, edge, or on-prem deployments
  - The same building blocks support development, test, and production topologies
- 8.5 Flexible extension patterns for product teams (3 min)
  - Native UI integration, custom data types, provider-specific extensions, and custom logic via hooks, workflows, or FaaS-style handlers
- 8.6 Offline exercise (3 min)
  - Pick one feature and map which artifacts, local checks, and runtime signals you would use from requirement to running implementation

> **References:** [docs/slides/1_OVERVIEW.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/slides/1_OVERVIEW.md) ("Engineering", "Principle 5", "Principle 7"),
> [docs/spec-templates/README.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/spec-templates/README.md), [docs/TESTING.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/TESTING.md), [docs/toolkit_unified_system/README.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/toolkit_unified_system/README.md)

### Module 9 — Adoption Path A: First Greenfield Gear Checklist (25 min)

**Goal:** give developers a practical checklist for building their first Gear from scratch.

- 9.1 When greenfield is the right choice (3 min)
  - A new XaaS product, an on-prem or edge appliance, or a GenAI platform backbone
- 9.2 First Gear checklist (12 min)
  1. Define the public contract
  2. Define request, response, and shared models
  3. Define clear error shapes
  4. Implement the core business rules
  5. Add persistence if needed
  6. Expose API endpoints
  7. Wire authorization, licensing, and usage checks
  8. Connect the gear into the application
  9. Add configuration
  10. Add docs or examples for consumers
  11. Add tests
  12. Run validation and quality gates
- 9.3 What you get from the platform path (5 min)
  - Multi-tenancy, authentication/authorization, licensing and quota, usage tracking, and events
  - Consistent REST + OpenAPI + OData, observability, migrations, and lifecycle support
- 9.4 Offline exercise (5 min)
  - Sketch a first `todo-tasks` feature using the checklist
  - Decide which files and layers each change belongs to

> **References:** [docs/QUICKSTART_GUIDE.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/QUICKSTART_GUIDE.md), [docs/slides/1_OVERVIEW.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/slides/1_OVERVIEW.md) (Parts 7–8),
> [docs/toolkit_unified_system/README.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/toolkit_unified_system/README.md)

### Module 10 — Adoption Path B: Gears adoption in existing platforms and services  (30 min)

**Goal:** explain how to add Gears into an existing SaaS or platform without forking the core geas

- 10.1 When to embed instead of greenfield (3 min)
  - When you already have an IdP, license engine, tenant directory, secret vault, billing platform, native UI shell, or search provider
- 10.2 Beginner view of plugins (5 min)
  - The main public gear exposes the stable API
  - Plugin gears implement behavior that can be replaced
  - Consumers call the main gear only; they do not call plugins directly
- 10.3 Native UI integration patterns (5 min)
  - Keep business capabilities in gears while integrating with an existing web console, admin UI, or product shell
  - Reuse generated APIs and typed contracts instead of duplicating backend logic in the UI layer
- 10.4 Custom data types with GTS (5 min)
  - Extend events, settings, permissions, license types, and provider-specific models without modifying the core gear
  - Use GTS as the contract for safe platform-specific customization
- 10.5 Custom logic, hooks, and FaaS-style extensibility (7 min)
  - Add custom workflows, callbacks, policy hooks, or tenant-specific automation around the stable public surface
  - Keep the integration replaceable instead of hardcoding customer-specific branches into the main gear
- 10.6 Plugin selection and rollout strategies (3 min)
  - Select by vendor config, tenant context, request parameter, priority, or fallback
  - Mix built-in plugins with external integrations and phased adoption
- 10.7 Offline exercise (2 min)
  - Choose where to connect an existing IdP, license system, native UI, or custom automation hook

> **References:** [docs/TOOLKIT_PLUGINS.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/TOOLKIT_PLUGINS.md), [docs/slides/1_OVERVIEW.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/slides/1_OVERVIEW.md) ("Plugins & extensibility",
> "Principle 7 — GTS"), [docs/GEARS.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/GEARS.md) (Core Platform Integration Gears)

### Module 11 — Wrap-up, Roadmap, Next Steps (10 min)

**Goal:** wrap up the course and point learners to the next practical step.

- 11.1 Recap: why Gears is a good fit for XaaS products (3 min)
- 11.2 When Gears is **not** the right choice (2 min)
  - Tiny standalone services, teams that want minimalism first, or products that do not need a platform, tenancy, or security backbone
- 11.3 Current state vs target architecture: how to read the repository honestly (2 min)
- 11.4 Where to go next (3 min)
  - Run quickstart and inspect `/cf/docs`
  - Build a small gear from the checklist
  - Read [docs/ARCHITECTURE_MANIFEST.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/ARCHITECTURE_MANIFEST.md), [docs/GEARS.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/GEARS.md), [docs/toolkit_unified_system/](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/toolkit_unified_system/)
  - Run local quality gates and fix one intentional violation

> **References:** [docs/WHY_GEARS.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/WHY_GEARS.md) ("When Gears is (and isn't) the right choice"),
> [docs/slides/1_OVERVIEW.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/slides/1_OVERVIEW.md) (Parts 7–8)

---

## Appendix A — Offline Exercise Index

| Exercise | Module | Outcome |
|----------|--------|---------|
| Exercise A | 3 | Run a local server, open `/cf/docs`, export OpenAPI, and identify active gears |
| Exercise B | 4 | Map a Todo Tasks feature to contract, API, business logic, and infrastructure areas |
| Exercise C | 5 | Trace one endpoint from the HTTP request to data access and response |
| Exercise D | 9 | Design a first greenfield Gear using the 12-step checklist |
| Exercise E | 10 | Decide where an existing IdP, license system, native UI, or custom automation hook should connect |
| Exercise F | 8 | Map one feature from requirement to code, tests, and runtime troubleshooting signals |

## Appendix B — Glossary (quick reference)

- **XaaS** — "anything-as-a-service"; software delivered as a running service for many customers. It is a broad term that includes SaaS, PaaS, and IaaS.
- **Multi-tenancy** — many customers (tenants) share the same infrastructure, but their data stays isolated.
- **Entitlement / licensing** — the features or limits a tenant or user is allowed to use, checked for each request.
- **Usage metering** — measuring usage such as API calls, compute, storage, or tokens; used for quotas and billing.
- **Deployment profile** — a deployment setup such as cloud-only, hybrid, cloud + edge, edge-first, mobile + cloud, or air-gapped.
- **FIPS 140-3 / GDPR / HIPAA / SOC 2 / ISO 27001** — security, crypto, and data-protection standards or certifications often relevant to XaaS products.
- **Gear** — a self-contained unit of functionality.
- **Toolkit** — the reusable foundation that every gear builds on.
- **ClientHub** — the local registry that gears use to find and call each other inside one application.
- **OperationBuilder** — the standard Gears way to define an API operation together with its documentation.
- **SecurityContext** — identity and security information about the caller, passed through the system.
- **AccessScope** — the visibility rules that control which data can be read or written.
- **PDP / PEP** — Policy Decision Point / Policy Enforcement Point.
- **SecureConn / Scopable** — framework support for tenant-aware data access that is scoped automatically.
- **GTS** — Global Type System; a system for versioned schemas, identifiers, and extension points.
- **Types Registry** — a system gear that stores GTS schemas and instances so they can be discovered.
- **`cargo gears`** — the CLI used to scaffold, configure, build, run, lint, and test Gears projects.

## Appendix C — Source Material Map

| Topic | Primary document |
|-------|------------------|
| Value proposition / language case | [docs/WHY_GEARS.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/WHY_GEARS.md) |
| Overview slides | [docs/slides/1_OVERVIEW.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/slides/1_OVERVIEW.md) |
| Architecture principles | [docs/ARCHITECTURE_MANIFEST.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/ARCHITECTURE_MANIFEST.md) |
| Gear inventory & categories | [docs/GEARS.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/GEARS.md) |
| Security & authorization | [docs/security/SECURITY.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/security/SECURITY.md), [docs/arch/authorization/DESIGN.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/arch/authorization/DESIGN.md) |
| Plugins & extension points | [docs/TOOLKIT_PLUGINS.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/TOOLKIT_PLUGINS.md) |
| Running the server | [docs/QUICKSTART_GUIDE.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/QUICKSTART_GUIDE.md) |
| Toolkit deep dive | [docs/toolkit_unified_system/README.md](https://www.github.com/constructorfabric/gears-rust/blob/main/docs/toolkit_unified_system/README.md) |
| Gears CLI | [cargo-gears README.md](https://github.com/constructorfabric/cargo-gears/blob/main/README.md) |
