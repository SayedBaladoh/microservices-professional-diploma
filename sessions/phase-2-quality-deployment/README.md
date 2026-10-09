# Phase 2 — Quality & Deployment (Sessions 9–16)

**Question answered:** *How do we prove it works and deliver it automatically?*

| S | Topic | Capability added | Lab | Checkpoint commit |
|---|---|---|---|---|
| 9 | Docker containerization *(offline)* + **Mid-Course Exam** | Reproducible, containerized platform | Lab 8A | `session-09: dockerize-all-platform-services` |
| 10 | Testing — Unit & Integration | Test pyramid, Testcontainers | Lab 9A | `session-10: add-integration-tests-product-service` |
| 11 | Testing — Contract & Chaos | Pact contracts, WireMock, chaos demo | Lab 9B | `session-11: add-contract-tests-wiremock-order-inventory` |
| 12 | Saga Orchestration | Explicit saga control (plain Spring Boot) | Lab 10A | `session-12: add-orchestration-saga-order-service` |
| 13 | CI/CD — GitHub Actions | Quality gates + full Notification Service | Lab 11A | `session-13: add-ci-pipeline-and-notification-service` |
| 14 | GitOps & Deployments | ArgoCD, canary 80/20 | Lab 11B | `session-14: add-k8s-manifests-and-argocd-application` |
| 15 | Kubernetes — Core | Probes, Secrets, production-ready Deployment | Lab 12A | `session-15: add-probes-and-secret-product-service` |
| 16 | Kubernetes — Advanced | HPA, Helm, RBAC | Lab 12B | `session-16: add-hpa-and-helm-chart-product-service` |

Mid-Course Exam commit: `exam-session-09: mid-course-exam` (see [ASSESSMENT.md](../../ASSESSMENT.md)).

Tools to install during this phase: `kubectl`, minikube or kind (S14–S15), Helm (S16) — see [SETUP.md](../../SETUP.md).

## Materials

Slides are the session presentation. Extended tutorials explain the same topics step by step, with more detail than the slides — read them when a slide feels too compact.

| Session | Slides | Extended tutorial |
|---|---|---|
| 9 | [PDF](Session_09_Docker_Containerization.pdf) | [PDF](Session_09_Docker_Containerization_Tutorial.pdf) |
| 10 | [PDF](Session_10_Testing_Unit_Integration.pdf) | [PDF](Session_10_Testing_Essentials_Tutorial.pdf) |
| 11 | [PDF](Session_11_Testing_Contract_Chaos.pdf) | — |
| 12 | [PDF](Session_12_Saga_Orchestration.pdf) | — |
| 13 | [PDF](Session_13_CICD_Pipelines.pdf) | [PDF](Session_13_CICD_Pipelines_Tutorial.pdf) |
| 14 | [PDF](Session_14_GitOps_Deployments.pdf) | [PDF](Session_14_GitOps_Deployments_Tutorial.pdf) |
| 15 | [PDF](Session_15_Kubernetes_Core.pdf) | [PDF](Session_15_Kubernetes_Core_Tutorial.pdf) |
| 16 | [PDF](Session_16_Kubernetes_Advanced.pdf) | [PDF](Session_16_Kubernetes_Advanced_Tutorial.pdf) |

## Phase 2 completion checklist

- [ ] All services have Dockerfiles (multi-stage, non-root) and CI workflows
- [ ] `product-service`: `@WebMvcTest` + Testcontainers integration test
- [ ] `order-service` ↔ `inventory-service`: Pact contract test
- [ ] `OrderSagaOrchestrator`: state machine + compensation path
- [ ] `notification-service`: `@RetryableTopic` + `@DltHandler`
- [ ] `product-service`: ArgoCD Application + canary 80/20
- [ ] `product-service`: liveness + readiness probes, Secret for the DB password
- [ ] `product-service`: HPA (CPU ≥ 70 %) and a Helm chart with ServiceAccount + Role

Previous: [Phase 1](../phase-1-foundation/README.md) · Next: [Phase 3](../phase-3-advanced-enterprise/README.md)
