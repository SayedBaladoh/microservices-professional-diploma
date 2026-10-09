# Phase 3 — Advanced & Enterprise (Sessions 17–24)

**Question answered:** *Can we see inside it, secure it properly, and trust it under load?*

| S | Topic | Capability added | Lab | Checkpoint commit |
|---|---|---|---|---|
| 17 | Observability *(offline)* | Tracing, metrics, structured logs | Lab 13 | `session-17: add-tracing-metrics-and-structured-logging` |
| 18 | CQRS | Read/write separation on Product Service | Lab 14 | `session-18: add-cqrs-command-query-split-product-service` |
| 19 | Security Part 1 — Keycloak & OAuth2 | Real identity provider, Authorization Code Flow | Lab 15 | `session-19: add-keycloak-realm-client-and-manual-oauth2-flow` |
| 20 | Security Part 2 — Client Credentials & Resource Server | Production-grade security; `JwtAuthFilter` retired | Lab 16 | `session-20: retire-jwtauthfilter-add-oauth2-resource-server-and-client-credentials` |
| 21 | Service Mesh — Istio | mTLS, weighted traffic, mesh-level outlier detection | Lab 17 | `session-21: add-istio-mtls-and-weighted-traffic-split` |
| 22 | Advanced Patterns | Outbox, idempotency keys, API versioning | Lab 18 | `session-22: close-[outbox\|idempotency\|versioning]-technical-debt` |
| 23 | Performance & Load Testing | k6 smoke / load / stress; resilience verified | Lab 19 | `session-23: add-k6-stress-test-and-bottleneck-findings` |
| 24 | Architecture Clinic #2 | Technical Debt Register v2 | Clinic output | `session-24: add-technical-debt-register-v2-and-phase3-retrospective` |

Tools to install during this phase: `istioctl` (S21), k6 (S23) — see [SETUP.md](../../SETUP.md).

## Materials

Slides are the session presentation. Extended tutorials explain the same topics step by step, with more detail than the slides — read them when a slide feels too compact.

| Session | Slides | Extended tutorial |
|---|---|---|
| 17 | [PDF](Session_17_Observability.pdf) | [PDF](Session_17_Observability_Tutorial.pdf) |
| 18 | [PDF](Session_18_CQRS.pdf) | [PDF](Session_18_CQRS_Tutorial.pdf) |
| 19 | [PDF](Session_19_Security_Part1.pdf) | [PDF](Sessions_19_20_Keycloak_OAuth2_Tutorial.pdf) |
| 20 | [PDF](Session_20_Security_Part2.pdf) | [PDF](Sessions_19_20_Keycloak_OAuth2_Tutorial.pdf) |
| 21 | [PDF](Session_21_Service_Mesh_Istio.pdf) | [PDF](Session_21_Service_Mesh_Istio_Tutorial.pdf) |
| 22 | [PDF](Session_22_Advanced_Patterns.pdf) | [Part 1](Session_22_Advanced_Patterns_Tutorial_1.pdf) · [Part 2](Session_22_Advanced_Patterns_Tutorial_2.pdf) |
| 23 | [PDF](Session_23_Performance_Load_Testing.pdf) | [PDF](Session_23_Performance_Load_Testing_Tutorial.pdf) |
| 24 | [PDF](Session_24_Architecture_Clinic2.pdf) | [PDF](Session_24_Architecture_Clinic2_Tutorial.pdf) |

## Phase 3 completion checklist

- [ ] A request produces one connected trace in Zipkin; a custom `@Timed` metric reaches Prometheus
- [ ] `product-service` split into Command and Query sides, with event-driven cache eviction
- [ ] Keycloak realm, Confidential client and users exist; you completed the Authorization Code Flow by hand
- [ ] `JwtAuthFilter` and `JwtUtil` are **deleted**; the Gateway is an OAuth2 Resource Server
- [ ] Istio STRICT mTLS and a weighted VirtualService are applied
- [ ] At least one of Outbox / Idempotency / API Versioning is implemented and verified
- [ ] k6 stress test run, with the actual resilience firing order documented
- [ ] Technical Debt Register v2 contributed to, and your readiness note submitted

Previous: [Phase 2](../phase-2-quality-deployment/README.md) · Next: [Phase 4](../phase-4-capstone/README.md)
