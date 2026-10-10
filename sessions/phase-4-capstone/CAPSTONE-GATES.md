# Capstone Gates Guide (Sessions 26–29)

Sessions 26–28 are **gate reviews**: you show what runs, we review it together. Session 29 is the final presentation. The building happens in your own time between sessions. This guide tells you exactly what to show at each gate. The binding requirements are in the Capstone Project Brief ([PDF](Capstone_Project_Brief_Trainees.pdf)) and [CAPSTONE.md](../../CAPSTONE.md).

## How every gate works

| Time | Activity |
|---|---|
| 00:00–00:10 | Check-in: each team posts its self-assessed status (Green / Amber / Red) per layer |
| 00:10–01:25 | Team reviews, 25 min each: ≈ 15 min live demo + ≈ 10 min questions |
| 01:25–01:35 | Break |
| 01:35–02:05 | Cross-team review: pull requests / ADD changes, and unblocking help |
| 02:05–02:20 | Role rotation + plan for the next gate |
| 02:20–02:30 | Wrap-up and commit reminder |

**Rules of a good demo**

- Demo from the `main` branch of your team repository, on a clean start (`docker compose up` or your cluster) — not from a half-open IDE session.
- Use a short written script (the curl commands in your README). Do not improvise.
- Show failures as well as successes: the failure path is part of the Definition of Done.
- Every member must be able to answer questions about any part of what you show.

## Gate status

| Status | Meaning |
|---|---|
| 🟢 Green | The layer's Definition of Done is demonstrated live |
| 🟡 Amber | Partly done, with a **written recovery plan** that fits before the next gate. Allowed **once** per team |
| 🔴 Red | Nothing demonstrable. 30-minute trainer intervention, and you apply the scope-cutting order |

**If you are behind, cut in this order:** stretch goals → Bonus "Could" stories → FR-14 → FR-13 → FR-12 → reduce Bonus Core (never drop it).
**Never cut:** tests, security rules, the compensation path, deployment.
Tell the trainer early. An Amber with a plan is fine; a silent Red is not.

---

## Gate G1 — Session 26 (Layers L1 + L2)

**Pre-reading:** your own ADD §3 (API + events), read as if you were the other team. Review Session 6 (OpenFeign) and Session 5 (resilience execution order).

**Show live**

| # | What | Requirement |
|---|---|---|
| 1 | `GET /api/v1/products` without a token → 200, paginated | FR-01 |
| 2 | `POST` without a token → 401; with a customer token → 403; with an admin token → 201 | FR-02, FR-04 |
| 3 | Flyway migrations visible; product detail shows the category name | NFR-09, FR-03 |
| 4 | Redis cache: second read is served from cache; a write evicts the item **and** the list | FR-15 |
| 5 | Order pre-check via Feign: out-of-stock order is rejected and payment is never touched | FR-06 |
| 6 | Stop inventory-service → the Resilience4j fallback answers (no stack trace to the user) | NFR-01 |
| 7 | Same `Idempotency-Key` sent twice to Payment → one charge, identical responses | FR-08 |
| 8 | `mvn test` green; coverage report; at least one Testcontainers test per database-owning service | NFR-07 |

**You commit:** merged PRs with tests · README with the curl commands.

**Knowledge Check questions:** (1) Which L1 stories are late and what is the recovery plan? (2) Which field of your API contract are you least sure the other side will parse? (3) Where does the Order → Inventory fallback return, and what does the customer see?

---

## Gate G2 — Session 27 (Layers L3 + L4)

L3 and L4 are the heaviest layers. Start them early.

**Show live**

| # | What | Requirement |
|---|---|---|
| 1 | Place an order → `PENDING` immediately → `CONFIRMED` (happy path) | FR-05, FR-09 |
| 2 | Switch payment to fail → order `CANCELLED`, stock released within 30 s | FR-09, NFR-05 |
| 3 | Redeliver an event → no double processing (consumer idempotency) | NFR-10 |
| 4 | Outbox: stop the service right after the commit, restart → the event still publishes | Outbox |
| 5 | Notification: a failing send is retried, then lands in the `.DLT` topic | FR-11 |
| 6 | Images built by CI (sha tag), non-root containers | NFR-04 |
| 7 | Platform runs in a cluster via Helm (at least two services) with probes, Secrets and a ServiceAccount per service | NFR-08 |
| 8 | ArgoCD application: Synced + Healthy; delete a pod and watch it come back | L4 |

**You commit:** Dockerfiles, CI workflows, Helm charts, manifests. No secrets in Git.

---

## Gate G3 — Session 28 (Layer L5)

**Show live**

| # | What | Requirement |
|---|---|---|
| 1 | One trace in Zipkin across HTTP **and** Kafka hops; JSON logs carry the same `traceId` | NFR-06 |
| 2 | A Grafana panel fed by Prometheus | L5 |
| 3 | k6 smoke → load → stress results against your targets (reads P95 < 200 ms cached; `POST /orders` P95 < 800 ms at 20 VUs; ≥ 50 req/s on reads — or the targets you justified in the ADD) | NFR-02, NFR-03 |
| 4 | **One bottleneck found and fixed**, with before/after numbers | L5 |
| 5 | Chaos check: stop payment-service, place an order → it stays `PENDING` or is cancelled with compensation | NFR-01 |

**You commit:** k6 scripts · **Performance Report** (target, method, results, bottleneck, fix, remaining risks).

---

## Final — Session 29 (Layer L6, offline)

| Time | Activity |
|---|---|
| 10:00–10:15 | Setup: cluster and demo environments verified |
| 10:15–12:30 | Team presentations, 45 min each (≈ 30 min presentation + demo, ≈ 15 min team questions) |
| 12:30–13:00 | Lunch |
| 13:00–14:30 | Individual oral Q&A, ≈ 10 min per trainee |
| 14:30–14:50 | Trainer deliberation |
| 14:50–15:00 | Closing and certificates |

**Presentation structure**

1. **Architecture:** the problem, your boundaries, key decisions (Saga style, replaced Defaults) and the trade-offs you accepted.
2. **Implementation:** what is built, how layers map to requirements, test and coverage evidence.
3. **Live demo:** place an order end to end · a failure path (payment failure → compensation) · deployment in the cluster · a trace · the k6 result · **your Bonus Feature**.
4. **Lessons learned:** what you would change if you started again, and the technical debt you consciously left open.

**You commit:** final ADD · README · architecture diagrams · slides · final report.

**Individual oral Q&A:** each member is asked about **any** part of the system, including the decision they wrote about in the Session 25 retrospective and what happened to it. Your git log must show commits in at least **3 different services**.

---

## Your pre-gate checklist

- [ ] My layer's Definition of Done is on `main`, not on a personal branch
- [ ] `mvn test` is green; CI is green
- [ ] The README has a copy-paste demo script
- [ ] No secrets in Git
- [ ] Everyone has merged PRs and reviewed at least one PR from a teammate
- [ ] The Tech Lead role has rotated; the ADD is updated with any decision that changed
- [ ] If I am Amber or Red, the recovery plan is written and sent to the trainer **before** the session
