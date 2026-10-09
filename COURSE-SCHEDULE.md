# Course Schedule & Delivery Model

## Weekly rhythm

| | |
|---|---|
| Session 1 | Wednesday, offline (in person), 10:00 AM–3:00 PM |
| Every other session | Monday and Wednesday, online, 3:00–5:30 PM |
| Anchor days (offline, 5 h) | Sessions **1, 9, 17, 25** — always Wednesday, 10:00 AM–3:00 PM |
| Final session | Session 29, offline anchor-style final presentation day |
| Total length | ≈ 15 weeks (two sessions per week) |

Session 9 is followed by the **Mid-Course Exam** on the same day (see [ASSESSMENT.md](ASSESSMENT.md)).

## Week map

| Week | Monday | Wednesday |
|---|---|---|
| 1 | — | **S1** Architecture & Spring Cloud *(offline)* |
| 2 | S2 Gateway Core | S3 Gateway Advanced |
| 3 | S4 Resilience I | S5 Resilience II |
| 4 | S6 Inter-Service Communication | S7 Saga + Kafka |
| 5 | S8 Caching + Clinic #1 | **S9** Docker + Mid-Course Exam *(offline)* |
| 6 | S10 Testing I | S11 Testing II |
| 7 | S12 Saga Orchestration | S13 CI/CD |
| 8 | S14 GitOps | S15 Kubernetes Core |
| 9 | S16 Kubernetes Advanced | **S17** Observability *(offline)* |
| 10 | S18 CQRS | S19 Security I |
| 11 | S20 Security II | S21 Service Mesh |
| 12 | S22 Advanced Patterns | S23 Performance & Load Testing |
| 13 | S24 Architecture Clinic #2 | **S25** Capstone Kickoff *(offline)* |
| 14 | S26 Gate G1 | S27 Gate G2 |
| 15 | S28 Gate G3 | **S29** Final Presentations *(offline)* |

> Calendar dates are announced by the trainer for each cohort.

## Online session template (2.5 hours)

| Time | Activity |
|---|---|
| 00:00–00:10 | **Knowledge Check** — 3 questions on the pre-reading, asked by name |
| 00:10–01:10 | Concept (problem first) + live coding, with a break |
| 01:10–01:45 | Lab — you implement |
| 01:45–01:55 | Debrief — common issues, Q&A |
| 01:55–02:05 | Daily Quiz — 8 questions |
| 02:05–02:10 | Checkpoint commit instructions + next-session preview |

## Offline anchor-day template (5 hours)

| Time | Activity |
|---|---|
| 10:00–11:00 | Deep theory + whiteboard |
| 11:00–11:15 | Break |
| 11:15–12:00 | Extended live coding |
| 12:00–12:45 | Lunch |
| 12:45–14:30 | Supervised lab |
| 14:30–14:45 | Lab debrief + architecture discussion |
| 14:45–15:00 | Quiz + checkpoint + preview |

Exact timings differ slightly per session; each session's slides show the real agenda.

## Capstone rhythm (S25–S29)

Sessions 26–28 are **gate reviews**, not teaching sessions. The building happens in your own time (≈ 2 hours per day per person) between sessions. The gaps are uneven (about 5, 2, 5 and 2 days) — plan the heavy layers (L3, L4) for the long gaps. See [CAPSTONE.md](CAPSTONE.md).

## Between sessions

1. Finish the lab; `mvn test` must be green.
2. Commit with the required format and push — **before the next session**.
3. Do the 15-minute pre-reading; the Knowledge Check questions are printed at the end of each session's handout.
4. Optional homework strengthens the next session — it is never graded, but later sessions assume it.

## What is NOT carried over

Earlier versions of this schedule described a single codebase that is never discarded through all 29 sessions. That is true for Sessions 1–24. In the Capstone (S25–S29) each team starts from a fresh Starter Repo and builds the final form once.
