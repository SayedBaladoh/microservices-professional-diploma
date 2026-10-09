# Microservices Course — Spring Boot & Spring Cloud · Professional Edition

> A project-based program for experienced Java engineers: design, build, test, deploy, secure and operate a production-grade microservices platform — and explain every decision you made.

**ITSharks — IT Learning & Training Center** · Trainer: Dr. ElSayed Mohamed Elsayed Baladoh

| | |
|---|---|
| **Format** | 29 sessions · ≈ 80 hours · 4 phases |
| **Delivery** | 4 offline anchor days (5 h, Wednesday) + 25 online sessions (2.5 h, Monday / Wednesday, 3:00–5:30 PM) |
| **Project** | One Enterprise E-Commerce Platform, built session by session (S1–S24), then rebuilt in final form by teams (S25–S29) |
| **Language** | English materials · Arabic / English instruction |

---

## Start here (new trainee)

1. Read **[SETUP.md](SETUP.md)** and prepare your machine **before Session 1** (≈ 1.5–2 hours).
2. Read the **[Trainee Onboarding Guide](docs/Trainee_Onboarding_Guide.pdf)** and **[GitHub Workflow](docs/onboarding/github-workflow.md)**.
3. Create your **own private copy** of the platform repository: [`microservices-pro-platform`](https://github.com/SayedBaladoh/microservices-pro-platform) → *Use this template*.
4. Read **[ASSESSMENT.md](ASSESSMENT.md)** and **[COURSE-RULES.md](COURSE-RULES.md)** so nothing about grading surprises you.

## Your loop in every session

```
Pre-reading (15 min) → Knowledge Check → Concept → Live coding → Lab
        → mvn test (green) → commit "session-NN: what-you-did" → push → Quiz
```

1. Open the session folder under [`sessions/`](sessions/) and use the slides (PDF) and tutorials.
2. Do the lab in **your own** platform repository (`main` branch).
3. All tests pass: `mvn test`.
4. Commit with the required format and push:
   ```bash
   git commit -m "session-07: add-choreography-saga-order-inventory-payment"
   git push origin main
   ```
5. Stuck? Compare with the instructor's `reference` branch — read it, never merge it ([details](docs/onboarding/github-workflow.md)).

**Labs that are not committed and pushed are not graded.**

---

## Repositories

| Repository | Purpose | Who writes to it |
|---|---|---|
| **microservices-professional-diploma** (this repo) | Slides, tutorials, course documents | Trainer only |
| [**microservices-pro-platform**](https://github.com/SayedBaladoh/microservices-pro-platform) | The platform code. `main` = your starting point · `reference` = instructor implementation · tags `milestone-01…05` | Trainer (you copy it) |
| **Your personal copy** of the platform | Where you do every lab (Sessions 1–24) | You |
| **Your team repository** | Capstone (Sessions 25–29), created from the Capstone Starter Repo | Your team of 3 |

---

## What you will build

| Service | Port | Introduced |
|---|---|---|
| Config Server | 8888 | S1 |
| Eureka Server | 8761 | S1 |
| API Gateway | 8080 | S2–S3 |
| Product Service | 8081 | S1 |
| Order Service | 8082 | S4 |
| Payment Service | 8083 | S4 |
| Inventory Service | 8084 | S6 |
| Notification Service | 8085 | S7 (bonus) · S13 (full) |

Infrastructure (PostgreSQL, Kafka, Redis, Zipkin, later Keycloak / Prometheus / Grafana) runs in Docker Compose. Each component is **taught in its own session** — see [SETUP.md](SETUP.md) for what to ignore until then.

## The four phases

| Phase | Sessions | Focus | Folder |
|---|---|---|---|
| **1 — Foundation & Core Patterns** | S1–S8 | Discovery, Config, Gateway, Resilience, Feign, Saga + Kafka, Caching | [`phase-1-foundation`](sessions/phase-1-foundation) |
| **2 — Quality & Deployment** | S9–S16 | Docker, Testing, Saga Orchestration, CI/CD, GitOps, Kubernetes | [`phase-2-quality-deployment`](sessions/phase-2-quality-deployment) |
| **3 — Advanced & Enterprise** | S17–S24 | Observability, CQRS, Security, Service Mesh, Advanced Patterns, Load Testing | [`phase-3-advanced-enterprise`](sessions/phase-3-advanced-enterprise) |
| **4 — Capstone** | S25–S29 | Team build, deploy, secure, test, present | [`phase-4-capstone`](sessions/phase-4-capstone) |

Full session-by-session table: **[COURSE-OVERVIEW.md](COURSE-OVERVIEW.md)**.

## Grading at a glance

| Daily Quizzes | Labs | Mid-Course Exam | Capstone |
|:---:|:---:|:---:|:---:|
| **10 %** | **40 %** | **15 %** (Session 9) | **35 %** (Team 70 / Individual 30) |

Distinction 90–100 · Merit 75–89 · Pass 60–74 · Retake below 60. Details: **[ASSESSMENT.md](ASSESSMENT.md)**.

## How we teach (the 9 standards)

Every session follows the same standards: problem first, two outcomes (learning vs platform), Knowledge Check, Capability Added, failure flows next to happy paths, Definition of Done, Common Issues, dev-vs-production labelling, and architecture before code. See **[docs/standards](docs/standards/COURSE-STANDARDS.md)**.

## Document map

| Document | What it answers |
|---|---|
| [SETUP.md](SETUP.md) | What do I install, and how do I verify it? |
| [COURSE-OVERVIEW.md](COURSE-OVERVIEW.md) | What is taught in each of the 29 sessions? |
| [COURSE-ROADMAP.md](COURSE-ROADMAP.md) | How does the platform grow across phases? |
| [COURSE-SCHEDULE.md](COURSE-SCHEDULE.md) | When and how are sessions delivered? |
| [ASSESSMENT.md](ASSESSMENT.md) | How am I graded? |
| [CAPSTONE.md](CAPSTONE.md) | What is Phase 4 and what must my team deliver? |
| [COURSE-RULES.md](COURSE-RULES.md) | What behaviour and process rules apply? |
| [CONTRIBUTING.md](CONTRIBUTING.md) | How do I report a mistake in the materials? |

## License

Course materials are provided for educational purposes — see [LICENSE](LICENSE).
