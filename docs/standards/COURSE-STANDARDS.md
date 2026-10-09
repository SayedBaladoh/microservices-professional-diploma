# Course Delivery Standards

Every session in this course follows nine standards. Knowing them helps you recognise *why* each session is shaped the way it is.

| # | Standard | What you will see |
|---|---|---|
| CS-01 | **Problem first** | Every pattern is introduced by the problem it solves — a short story — never by its API |
| CS-02 | **Learning outcome ≠ platform outcome** | Two banners on every session: what *you* learn, and what the *platform* gains |
| CS-03 | **Knowledge Check** | Three named questions on the pre-reading at the start of each session |
| CS-04 | **Capability Added** | 🎯 Capability (business terms) + 📦 Services updated, every session |
| CS-05 | **Failure flows** | The failure path is drawn next to the happy path — failures are first-class scenarios |
| CS-06 | **Checkpoint commit (Definition of Done)** | A checklist and a git commit end every session |
| CS-07 | **Common Issues & Solutions** | Five real errors with exact fixes per session |
| CS-08 | **Dev vs Production** | Dev-only configuration is explicitly labelled in code comments |
| CS-09 | **Architecture before code** | You draw the design on paper before implementing |

## Decision badges

| Badge | Meaning | Format |
|---|---|---|
| ⚖ **Engineering Decision** | A tactical implementation trade-off (e.g. Semaphore vs ThreadPool Bulkhead) | If/then rules or comparison |
| 🎯 **Design Choice** | An architectural decision that shapes the system (e.g. Choreography vs Orchestration) | `If X → then Y` rules |

## Commit convention

```
session-NN: short-description-of-what-was-done      # Sessions 1–24
capstone-Lx: short-description                      # Capstone
exam-session-09: mid-course-exam                    # Mid-Course Exam
```

Use lowercase and hyphens. Example: `session-04: add-circuit-breaker-and-retry-on-order-payment`.

## Dev-only markers you will see

```yaml
# DEV ONLY — discovery.locator.enabled: true → production uses explicit routes
# DEV ONLY — placeholder secret; real secrets never go to Git
# DEV ONLY — enable-self-preservation: false
```

Learn which habits to unlearn before they reach production.

## Testing is not optional

Every lab includes unit tests and 20 % of the lab grade. See [ASSESSMENT.md](../../ASSESSMENT.md).
