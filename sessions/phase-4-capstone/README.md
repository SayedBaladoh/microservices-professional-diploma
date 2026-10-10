# Phase 4 — Capstone (Sessions 25–29)

**Question answered:** *Can you build the whole thing once, in its final form, as a team — and defend it?*

Sessions 26–28 are **gate reviews**, not lectures. The building happens in your own time between sessions. The binding document is the **Capstone Project Brief** distributed in Session 25; the short version is [CAPSTONE.md](../../CAPSTONE.md).

| S | Format | Gate | Layers | You show live | You commit |
|---|---|---|---|---|---|
| 25 | Offline 5 h | Kickoff | L0 | Repo + infra healthy, `verify-l0.sh` passes, peer-reviewed ADD, backlog | `session-25: capstone-kickoff-add-and-backlog` |
| 26 | Online | **G1** | L1 + L2 | Public GET, 401 without token, ADMIN rules, order pre-check via Feign with resilience, idempotent payment | `capstone-Lx: …` — PRs merged with tests; README with curl commands |
| 27 | Online | **G2** | L3 + L4 | Saga happy path + compensation; DLT; running in a Kubernetes cluster; probes, Secrets, ArgoCD Synced/Healthy | Dockerfiles, CI workflows, Helm charts, manifests |
| 28 | Online | **G3** | L5 | k6 smoke/load/stress; one bottleneck found and fixed; trace across HTTP + Kafka; Grafana panel | k6 scripts, Performance Report |
| 29 | Offline 5 h | **G4** | L6 | Full demo including the Bonus; individual oral Q&A | Final ADD, README, diagrams, slides, final report |

## Gate status

🟢 **Green** — Definition of Done demonstrated live · 🟡 **Amber** — partly done, written recovery plan, allowed once per team · 🔴 **Red** — nothing demonstrable, 30-minute trainer intervention.

**If you are behind, cut in this order:** stretch goals → Bonus "Could" stories → FR-14 → FR-13 → FR-12 → reduce Bonus Core (never drop it).
**Never cut:** tests, security rules, the compensation path, deployment.

## Team rules (summary)

- 3 teams × 3 trainees; roles rotate at every gate (Tech Lead · DevOps/Security · QA/Docs).
- `main` protected; short-lived branches; every change by Pull Request with one teammate review within 24 hours.
- Commit format `capstone-Lx: short-description`; pair work uses `Co-authored-by:`.
- Each member commits in at least 3 different services — the git log is part of the individual grade.
- No secrets in Git.

## Materials in this folder

- [`CAPSTONE-GATES.md`](CAPSTONE-GATES.md) — exactly what to show at each gate (S26–S29).
- [`Capstone_Project_Brief_Trainees.pdf`](Capstone_Project_Brief_Trainees.pdf) — the full trainee handbook (binding document).
- [`Session_25_Capstone_TeamFormation.pdf`](Session_25_Capstone_TeamFormation.pdf) — kickoff slides.
- Gate sessions (S26–S29) are run from the Capstone Brief and your own repositories; no slide decks are needed.

Previous: [Phase 3](../phase-3-advanced-enterprise/README.md)
