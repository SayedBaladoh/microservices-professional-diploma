# Assessment

## Grade composition

| Component | Weight | When | Individual / Team |
|---|:---:|---|---|
| Daily Quizzes | **10 %** | End of every session | Individual |
| Lab grades | **40 %** | After every lab | Individual |
| Mid-Course Exam | **15 %** | Session 9 (2 hours) | Individual |
| Capstone | **35 %** | Sessions 25–29 | Team 70 % + Individual 30 % |

## Grade bands

| Band | Score | Award |
|---|---|---|
| Distinction | 90–100 % | Certificate of Distinction |
| Pass with Merit | 75–89 % | Certificate of Completion |
| Pass | 60–74 % | Certificate of Completion |
| Retake required | below 60 % | Resubmit failed labs before certification |

## 1. Daily Quiz (10 %)

- 8 questions per session, about 10 minutes at the end (Google Forms or Kahoot).
- Mix of scenario, production-decision, conceptual and code-reading questions.
- **Exceptions:** Session 9 uses a shortened quiz (the exam follows); Session 24 is reflective; Session 25 replaces the quiz with a Team Retrospective.

## 2. Labs (40 %)

Every lab is graded with the same structure:

| Part | Weight | What is checked |
|---|:---:|---|
| Feature works | 70 % | Acceptance criteria pass; endpoints respond correctly |
| Unit tests | 20 % | Minimum test count met and `mvn test` is green. **No tests = 0 for this part** |
| Code quality | 10 % | Clean code, meaningful names, no obvious duplication |

- Each lab lists **bonus tasks (+5 each)**. Bonus can raise a lab score but never lifts your course grade above 100 %.
- Each session handout contains its own rubric with exact points.

### Checkpoint commit rules

1. Finish the lab; `mvn test` passes.
2. Commit with the required format: `session-NN: short-description` (e.g. `session-07: add-choreography-saga-order-inventory-payment`).
3. Push to **your own** repository before the next session starts.

**A lab that is not committed and pushed is not graded.** A wrong commit-message format means you will be asked to re-commit before grading. Late work is possible as homework, but it must be pushed before the next session.

## 3. Mid-Course Exam (15 %) — Session 9

| | |
|---|---|
| Duration | 2 hours, individual, supervised |
| Coverage | Sessions 1–8 |
| Part A | 24 multiple-choice questions (24 points) |
| Part B | A practical coding task in your repository (76 points) |
| Allowed | Your IDE, your own repository, official Spring / Java / Resilience4j documentation |
| Not allowed | AI assistants, forums, classmates, the `reference` branch (closed during the exam) |
| Submission | `git commit` + push to `main` with message `exam-session-09: mid-course-exam` |

Below 60 points → a catch-up conversation with the trainer **before** Session 10.

## 4. Capstone (35 %) — Sessions 25–29

### Team component — 70 %

| Criterion | Weight inside |
|---|:---:|
| Architecture Quality — ADD, decisions, diagrams, failure modes | 25 % |
| Implementation + Tests — Core complete + Bonus, coverage, PR quality | 35 % |
| Deployment + Security — Kubernetes, GitOps, hardening, secrets | 20 % |
| Presentation — structure, demo, honesty about trade-offs | 20 % |

A complete Core alone earns at most **85 %** of the Implementation criterion; the primary Bonus Feature provides the remaining 15 %.

### Individual component — 30 %

| Criterion | Weight inside |
|---|:---:|
| Oral Q&A in Session 29 — each member answers about *any* part of the system | 60 % |
| Code contribution — git log evidence across at least 3 different services | 40 % |

### Gate status

| Status | Meaning |
|---|---|
| 🟢 Green | The layer's Definition of Done is demonstrated live |
| 🟡 Amber | Partly done, with a written recovery plan that fits before the next gate (allowed once per team) |
| 🔴 Red | Nothing demonstrable — 30-minute trainer intervention and scope cutting |

Details and the scope-cutting order: [CAPSTONE.md](CAPSTONE.md).

## What Distinction looks like

Labs consistently complete **with** tests, strong Mid-Course Exam, and a Capstone with a working Core, a working Bonus, a live deployment, documented performance results — and a team member who can explain and defend every part of the system.

## Honesty rules

- Individual work stays individual (labs, exam). Sharing code during the exam gives zero to both.
- In the Capstone, every member must be able to explain every service. Rotate roles and review each other's pull requests.
- Never commit secrets. See [COURSE-RULES.md](COURSE-RULES.md).
