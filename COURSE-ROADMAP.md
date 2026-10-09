# Course Roadmap

How the Enterprise E-Commerce Platform grows across the four phases. Session-by-session detail: [COURSE-OVERVIEW.md](COURSE-OVERVIEW.md).

## The journey in one picture

```
PHASE 1  Foundation & Core Patterns      S1 ───────────────── S8      "Build it right"
PHASE 2  Quality & Deployment            S9 ───────────────── S16     "Ship it reliably"
PHASE 3  Advanced & Enterprise           S17 ──────────────── S24     "Operate it with confidence"
PHASE 4  Capstone                        S25 ───────────────── S29    "Rebuild it, own it, defend it"
```

## Phase 1 — Foundation & Core Patterns (S1–S8)

**Question answered:** *How do independent services find, protect, call and trust each other?*

| Step | Sessions | Platform gains |
|---|---|---|
| Foundation | S1–S3 | Config Server, Eureka, Product Service, API Gateway with JWT validation and rate limiting |
| Resilience | S4–S5 | Payment + Order services protected by Circuit Breaker, Retry, Bulkhead, TimeLimiter |
| Communication | S6 | Inventory Service, synchronous calls with OpenFeign |
| Distributed transactions | S7 | Choreography Saga over Kafka with compensation |
| Validation | S8 | Redis cache-aside on Product Service; Architecture Clinic #1; Technical Debt Register v1 |

Git tags in the platform repo: `milestone-01` (S1) · `milestone-02` (S3) · `milestone-03` (S5) · `milestone-04` (S7) · `milestone-05` (S8).

## Phase 2 — Quality & Deployment (S9–S16)

**Question answered:** *How do we prove it works and deliver it automatically?*

| Step | Sessions | Platform gains |
|---|---|---|
| Containers | S9 | Every service dockerized; `docker compose up -d` starts everything. **Mid-Course Exam** |
| Testing | S10–S11 | Unit, slice, integration (Testcontainers), contract (Pact), WireMock, chaos demo |
| Saga control | S12 | Orchestration saga in plain Spring Boot, next to the S7 choreography |
| Delivery | S13–S14 | GitHub Actions CI, full Notification Service, ArgoCD GitOps, canary deployment |
| Kubernetes | S15–S16 | Probes, Secrets, HPA, Helm chart, least-privilege ServiceAccount |

## Phase 3 — Advanced & Enterprise (S17–S24)

**Question answered:** *Can we see inside it, secure it properly, and trust it under load?*

| Step | Sessions | Platform gains |
|---|---|---|
| Observability | S17 | Zipkin traces, Prometheus metrics, Grafana, structured JSON logs |
| Design | S18 | CQRS read/write split on Product Service |
| Security | S19–S20 | Keycloak identity provider; Gateway becomes an OAuth2 Resource Server; `JwtAuthFilter` retired; Client Credentials |
| Mesh | S21 | Istio mTLS, weighted traffic, mesh-level outlier detection |
| Reliability | S22 | Outbox, idempotency keys, API versioning — closes named technical debt |
| Verification | S23–S24 | k6 load/stress tests; Architecture Clinic #2; Technical Debt Register v2 |

## Phase 4 — Capstone (S25–S29)

**Question answered:** *Can you build the whole thing once, in its final form, as a team — and defend it?*

| Layer | Content | Gate |
|---|---|---|
| L0 | Team repo, infrastructure, Config + Eureka | S25 |
| L1–L2 | Product, Gateway + Keycloak, Inventory, Payment, Order (sync path) | G1 — S26 |
| L3–L4 | Saga + Outbox + Notification; Docker, CI, Kubernetes, Helm, GitOps | G2 — S27 |
| L5 | Observability, k6, bottleneck found and fixed | G3 — S28 |
| L6 | Bonus Feature, documentation, live demo, oral Q&A | G4 — S29 |

Full details: [CAPSTONE.md](CAPSTONE.md).

## Technology by phase

| Area | Introduced in |
|---|---|
| Spring Cloud Config, Eureka | S1 |
| Spring Cloud Gateway (WebFlux) | S2–S3 |
| Resilience4j | S4–S5 |
| OpenFeign | S6 |
| Kafka, Saga | S7 |
| Redis cache | S8 |
| Docker / Compose | S9 |
| JUnit 5, Mockito, Testcontainers, Pact, WireMock | S10–S11 |
| GitHub Actions, ArgoCD | S13–S14 |
| Kubernetes, Helm | S15–S16 |
| Micrometer, Zipkin, Prometheus, Grafana | S17 |
| Keycloak, OAuth2 | S19–S20 |
| Istio | S21 |
| k6 | S23 |
