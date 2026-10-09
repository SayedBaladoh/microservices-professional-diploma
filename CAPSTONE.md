# Capstone — Phase 4 (Sessions 25–29)

> **Vision:** *Rebuild the platform we learned — once, in its final form — into a product a stranger can run, deploy, load-test and question.*

This page is the short version. The full **Capstone Project Brief** (trainee handbook) is distributed in Session 25 and is the binding document.

## 1. Why a clean rebuild?

During Sessions 1–24 some components were built one way and rebuilt another way later. That was right for *learning* and wrong for *building*. In the Capstone every team starts from the same Starter Repo and builds each component once, in its final shape.

| Aspect | Sessions 1–24 | Capstone |
|---|---|---|
| Repository | One personal repo | One repo per team, from the Starter Repo |
| Security | `JwtAuthFilter` → Resource Server | Keycloak Resource Server from day one |
| Stock data | In-memory → database | PostgreSQL + Flyway from day one |
| Saga | Choreography, then Orchestration | **One** style, chosen and justified in the ADD |
| Debt fixes | Added in S22 | Built in from the first commit |
| Work mode | Individual labs | Team of 3, rotating roles, PR review |

## 2. Teams and sessions

3 teams × 3 trainees. Build window ≈ 2.5 weeks, about 2 hours per day per person.

| Session | Format | What happens | You deliver |
|---|---|---|---|
| S25 Kickoff | Offline 5 h | Charter, team formation, architecture review, Sprint 0 | Repo + L0, peer-reviewed ADD, backlog, Team Charter |
| S26 Gate G1 | Online | Live review, PR reviews | L1 + L2 working |
| S27 Gate G2 | Online | Saga + deployment review | L3 + L4 in a Kubernetes cluster |
| S28 Gate G3 | Online | Load tests, bottleneck | L5: k6 results + Performance Report |
| S29 Final | Offline 5 h | Presentations, demo, oral Q&A | L6: Bonus, docs, demo |

## 3. What you build

Eight services plus infrastructure: config-server, eureka-server, api-gateway, product-service, order-service, payment-service, inventory-service, notification-service — and **one Bonus Feature** per team.

Core requirements (MoSCoW): browse products publicly (FR-01), admin product management (FR-02), Keycloak sign-in (FR-04), place an order that answers `PENDING` immediately (FR-05), synchronous stock pre-check (FR-06), reserve/release stock (FR-07), **exactly-once payment** via idempotency (FR-08), `CONFIRMED` / `CANCELLED` with compensation (FR-09), order status (FR-10), notifications with retry + DLT (FR-11).

Non-functional targets: P95 < 200 ms on cached product reads and < 800 ms on order creation at 20 virtual users, one trace across HTTP + Kafka, ≥ 60 % coverage, Flyway migrations, `/api/v1` everywhere, no secrets in Git, non-root containers.

## 4. Layers and gates

| Layer | Content | Gate |
|---|---|---|
| L0 | Repo from Starter, infra up, Config + Eureka | S25 |
| L1 | Product + Gateway + Keycloak security | G1 — S26 |
| L2 | Inventory + Payment + Order (sync part) | G1 — S26 |
| L3 | Saga + Outbox + Notification | G2 — S27 |
| L4 | Docker, CI, Kubernetes, Helm, GitOps + hardening | G2 — S27 |
| L5 | Observability + k6 + optimization | G3 — S28 |
| L6 | Bonus Feature + docs + demo | G4 — S29 |

**If you are behind, cut in this order:** stretch goals → Bonus "Could" stories → FR-14 → FR-13 → FR-12 → reduce (never drop) Bonus Core.
**Never cut:** tests, security rules, the compensation path, deployment.
Tell the trainer early: an Amber with a plan is fine; a silent Red is not.

## 5. Technology levels

| Level | Meaning |
|---|---|
| 🔒 Fixed | Java 21 / Spring Boot 3, Keycloak, PostgreSQL + Flyway, Kafka, Docker, k6 — not negotiable |
| 🟢 Default | Eureka, Config Server, Redis, OpenFeign, Resilience4j, Outbox, GitHub Actions, Helm, ArgoCD… — replace only with a written justification in the ADD |
| 🔓 Open | Saga style, read-model approach, service mesh — your decision, recorded in the ADD |
| ⛔ Not allowed | Elasticsearch, extra databases or brokers, Axon, Event Sourcing |

## 6. Bonus Features (one primary per team)

| Bonus | Idea |
|---|---|
| B1 — Product Reviews & Ratings | New `review-service`; average rating updated through an event |
| B2 — Order Analytics Dashboard | Read model from order events + Grafana panels |
| B3 — Multi-Tenant Gateway | Tenant from a JWT claim; data isolation; per-tenant rate limit |
| B4 — Real-Time Inventory Alerts | `LowStock` event pushed to admins within 2 seconds (SSE/WebSocket) |

## 7. Ways of working

- **Roles rotate at every gate:** Tech Lead · DevOps/Security · QA/Docs.
- `main` is protected. Short-lived branches, Pull Request, one teammate review (answered within 24 hours).
- Commit format: `capstone-Lx: short-description` — e.g. `capstone-L2: add-payment-idempotency`. Pair work: add `Co-authored-by:`.
- Each member commits in **at least 3 different services** (part of the individual grade).
- No secrets in Git, ever.

## 8. Required documents

- **ADD (Architecture Decision Document)** — 8 sections: problem, bounded context, API + events, data model, communication (including your Saga decision and what would make you switch), failure modes (≥ 5), security & deployment, test & load plan + risks.
- **Backlog** — 12–15 stories, none above 4 hours, each with an observable Definition of Done.
- **Three paper drawings**, a signed **Team Charter**, a **Performance Report** (S28), and the final README and diagrams (S29).

## 9. Grading

Capstone = 35 % of the course. Team 70 % (Architecture 25 · Implementation + Tests 35 · Deployment + Security 20 · Presentation 20) and Individual 30 % (Oral Q&A 60 · git-log contribution 40). See [ASSESSMENT.md](ASSESSMENT.md).

## 10. Before Session 25

- Review the Technical Debt Register v2 from Session 24 and your Session 23 reflection notes.
- Docker Desktop with at least 6 GB RAM; Keycloak needs about 60 seconds to start.
- Be ready for three Knowledge Check questions on open technical debt, the three Session 22 fixes, and why the Capstone builds the final form directly.
