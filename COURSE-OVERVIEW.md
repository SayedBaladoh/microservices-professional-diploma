# Course Overview

**Microservices Course — Spring Boot & Spring Cloud · Professional Edition**
ITSharks — IT Learning & Training Center

---

## 1. The North Star

> *Can this trainee design, build, deploy and operate a production-grade microservices system — and explain every decision they made?*

Every session, lab and quiz serves that question. Frameworks are tools; **engineering judgement** is the skill.

## 2. Program at a glance

| | |
|---|---|
| Sessions | 29 |
| Total time | ≈ 80 hours |
| Offline anchor days | 4 × 5 h — Sessions **1, 9, 17, 25** (Wednesday 10:00 AM–3:00 PM) |
| Offline final day | Session **29** — final presentations and oral Q&A (5 h) |
| Online sessions | 24 × 2.5 h (Monday / Wednesday 3:00–5:30 PM) |
| Phases | 4 (≈ 20 h each) |
| Duration | ≈ 15 weeks at two sessions per week — see [COURSE-SCHEDULE.md](COURSE-SCHEDULE.md) |
| Project | One Enterprise E-Commerce Platform |
| Assessment | Quizzes 10 % · Labs 40 % · Mid-Course Exam 15 % · Capstone 35 % |

## 3. The learning model: one platform, then a clean rebuild

- **Sessions 1–24 — Continuous platform.** You build and evolve *one* system. Every lab adds a capability; nothing is thrown away. Some components are intentionally rebuilt in a better form later (for example, the hand-written `JwtAuthFilter` of Session 3 is replaced by a Keycloak Resource Server in Session 20) — that is part of learning *why* the better form exists.
- **Sessions 25–29 — Capstone.** Teams of three start once more from a shared Starter Repo and build the platform **in its final form**, using everything learned, and defend every decision. See [CAPSTONE.md](CAPSTONE.md).

## 4. The three layers we teach

| Layer | You can… | Measured by |
|---|---|---|
| **1 — Knowledge** | Explain what a pattern is | Daily quizzes |
| **2 — Skill** | Implement it | Lab grades, Mid-Course Exam |
| **3 — Judgement** | Decide when *not* to use it | Architecture Clinics (S8, S24), Capstone review and oral Q&A |

## 5. All 29 sessions

Lab IDs follow each session's own handout. Format: **OFF** = offline 5 h, **ON** = online 2.5 h.

### Phase 1 — Foundation & Core Patterns (S1–S8)

| S | Day | Fmt | Topic | Capability added | Lab |
|---|---|---|---|---|---|
| 1 | Wed | OFF | Architecture & Spring Cloud | Service discovery & centralized config | Lab 1 |
| 2 | Mon | ON | API Gateway — Core | Single entry point | Lab 2A |
| 3 | Wed | ON | API Gateway — Advanced | Security & abuse protection (JWT, rate limiting) | Lab 2B |
| 4 | Mon | ON | Resilience — Circuit Breaker & Retry | Graceful degradation | Lab 3A |
| 5 | Wed | ON | Resilience — Bulkhead & TimeLimiter | Complete resilience layer | Lab 3B |
| 6 | Mon | ON | Inter-Service Communication | Synchronous service-to-service calls (OpenFeign) | Lab 4A |
| 7 | Wed | ON | Distributed Transactions — Saga + Kafka | Distributed business transactions | Lab 5A |
| 8 | Mon | ON | Caching + Architecture Clinic #1 | Performance + architecture validation | Lab 6A |

### Phase 2 — Quality & Deployment (S9–S16)

| S | Day | Fmt | Topic | Capability added | Lab |
|---|---|---|---|---|---|
| 9 | Wed | OFF | Docker containerization **+ Mid-Course Exam** | Reproducible, containerized platform | Lab 8A |
| 10 | Mon | ON | Testing — Unit & Integration | Layered test suite (Testcontainers) | Lab 9A |
| 11 | Wed | ON | Testing — Contract & Chaos | Contract safety net + chaos validation | Lab 9B |
| 12 | Mon | ON | Saga Orchestration (plain Spring Boot) | Explicit saga control | Lab 10A |
| 13 | Wed | ON | CI/CD — GitHub Actions | Automated quality gates + full Notification Service | Lab 11A |
| 14 | Mon | ON | GitOps & Deployments | ArgoCD delivery, canary deployment | Lab 11B |
| 15 | Wed | ON | Kubernetes — Core | Probes, Secrets, production-ready Deployment | Lab 12A |
| 16 | Mon | ON | Kubernetes — Advanced | HPA, Helm, RBAC · Phase 2 complete | Lab 12B |

### Phase 3 — Advanced & Enterprise (S17–S24)

| S | Day | Fmt | Topic | Capability added | Lab |
|---|---|---|---|---|---|
| 17 | Wed | OFF | Observability | Tracing, metrics, structured logs | Lab 13 |
| 18 | Mon | ON | CQRS | Read/write separation | Lab 14 |
| 19 | Wed | ON | Security Part 1 — Keycloak & OAuth2 | Real identity provider, Authorization Code Flow | Lab 15 |
| 20 | Mon | ON | Security Part 2 — Client Credentials & Resource Server | Production-grade security | Lab 16 |
| 21 | Wed | ON | Service Mesh — Istio | mTLS, traffic management | Lab 17 |
| 22 | Mon | ON | Advanced Patterns | Outbox, idempotency keys, API versioning | Lab 18 |
| 23 | Wed | ON | Performance & Load Testing (k6) | Resilience verified under real load | Lab 19 |
| 24 | Mon | ON | Architecture Clinic #2 | Technical Debt Register v2 · Phase 3 complete | Clinic output |

### Phase 4 — Capstone (S25–S29)

| S | Day | Fmt | Topic | Gate | You show |
|---|---|---|---|---|---|
| 25 | Wed | OFF | Capstone Kickoff — charter, teams, ADD | L0 | Repo + infra running, peer-reviewed ADD, backlog |
| 26 | Mon | ON | Gate G1 | L1 + L2 | Product, Gateway/Keycloak security, Inventory, Payment, Order (sync path) |
| 27 | Wed | ON | Gate G2 | L3 + L4 | Saga + Outbox + Notification; running in Kubernetes with GitOps |
| 28 | Mon | ON | Gate G3 | L5 | Observability, k6 results, one bottleneck found and fixed |
| 29 | Wed | OFF | Final presentations & oral Q&A | L6 | Bonus feature, docs, live demo |

## 6. The platform you build

| Service | Port | Store | Role |
|---|---|---|---|
| config-server | 8888 | Git config repo | Central configuration |
| eureka-server | 8761 | — | Service discovery |
| api-gateway | 8080 | Redis | Entry point, security, rate limiting |
| product-service | 8081 | PostgreSQL, Redis | Catalogue, cache, read model |
| order-service | 8082 | PostgreSQL | Orders, saga |
| payment-service | 8083 | PostgreSQL | Payments, idempotency |
| inventory-service | 8084 | PostgreSQL | Stock, reservation |
| notification-service | 8085 | — | Kafka consumer, retry, DLT |

## 7. Capability milestones

| Milestone | Sessions | Meaning | Git tag |
|---|---|---|---|
| M1 | 1–3 | Platform foundation (Config, Eureka, Gateway, security, rate limiting) | `milestone-01` (S1), `milestone-02` (S3) |
| M2 | 4–5 | Resilience layer | `milestone-03` (S5) |
| M3 | 6 | Synchronous service communication | — |
| M4 | 7 | Distributed transactions (Saga) | `milestone-04` (S7) |
| M5 | 8 | Performance & validation — Phase 1 complete | `milestone-05` (S8) |

## 8. Intentionally *not* covered

Keeping scope tight is a design decision. This course is **not**: a Spring Boot basics tutorial, a Kafka deep-dive (Kafka is the event transport for the Saga), a cloud-provider tutorial (Kubernetes is used generically), an Axon / Event Sourcing course, a full ELK logging stack, or certification preparation.

## 9. Who this is for

Java / Spring Boot developers, backend and full-stack engineers, architects, and DevOps engineers moving toward cloud-native development.

**Required before Session 1:** strong Java and Spring Boot (REST, DI, JPA), solid SQL, Maven, Git (daily use), basic Docker, basic Linux command line. If you are unsure about Java or Spring Boot, complete a refresher first — this course builds on them.

## 10. Where to go next

- Prepare your machine → [SETUP.md](SETUP.md)
- Understand grading → [ASSESSMENT.md](ASSESSMENT.md)
- Browse the materials → [`sessions/`](sessions/)
