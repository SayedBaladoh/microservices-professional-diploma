# Phase 1 — Foundation & Core Patterns (Sessions 1–8)

**Question answered:** *How do independent services find, protect, call and trust each other?*

| S | Topic | Capability added | Lab | Checkpoint commit |
|---|---|---|---|---|
| 1 | Architecture & Spring Cloud *(offline)* | Service discovery & centralized config | Lab 1 | `session-01: add-product-service-eureka-config` |
| 2 | API Gateway — Core | Single entry point | Lab 2A | `session-02: add-api-gateway-with-product-route` |
| 3 | API Gateway — Advanced | JWT validation + rate limiting | Lab 2B | `session-03: add-jwt-auth-filter-and-rate-limiting` |
| 4 | Resilience — Circuit Breaker & Retry | Graceful degradation | Lab 3A | `session-04: add-circuit-breaker-and-retry-on-order-payment` |
| 5 | Resilience — Bulkhead & TimeLimiter | Complete resilience layer | Lab 3B | `session-05: add-bulkhead-and-timelimiter-to-order-payment` |
| 6 | Inter-Service Communication | OpenFeign synchronous calls | Lab 4A | `session-06: add-inventory-service-and-feign-client` |
| 7 | Saga + Kafka | Distributed business transactions | Lab 5A | `session-07: add-choreography-saga-order-inventory-payment` |
| 8 | Caching + Architecture Clinic #1 | Redis cache + architecture validation | Lab 6A | `session-08: add-redis-caching-to-product-service` |

Platform tags: `milestone-01` (S1) · `milestone-02` (S3) · `milestone-03` (S5) · `milestone-04` (S7) · `milestone-05` (S8).

## Materials

Slides are the session presentation. Extended tutorials explain the same topics step by step, with more detail than the slides — read them when a slide feels too compact.

| Session | Slides | Extended tutorial |
|---|---|---|
| Kickoff | [PDF](00-Course-Kickoff.pdf) | — |
| 1 | [PDF](Session_01_Architecture_SpringCloud.pdf) | — |
| 2 | [PDF](Session_02_API_Gateway_Routing.pdf) | [PDF](Session_02_API_Gateway_Routing_Tutorial.pdf) |
| 3 | [PDF](Session_03_Gateway_Advanced.pdf) | [PDF](Session_03_Gateway_Advanced_Tutorial.pdf) |
| 4 | [PDF](Session_04_Resilience_CircuitBreaker.pdf) | — |
| 5 | [PDF](Session_05_Resilience_Advanced.pdf) | — |
| 6 | [PDF](Session_06_InterService_Communication.pdf) | [PDF](Session_06_InterService_Communication_Tutorial.pdf) |
| 7 | [PDF](Session_07_Saga_Kafka.pdf) | [PDF](Session_07_Kafka_Async_Tutorial.pdf) |
| 8 | [PDF](Session_08_Caching_ArchClinic1.pdf) | [PDF](Session_08_Redis_Caching_Tutorial.pdf) |

## Phase 1 self-check (answer "yes" to at least 8 of 10 before Phase 2)

- [ ] I can run the full platform locally with `docker compose up -d`.
- [ ] I can explain why a Config Server beats per-service config.
- [ ] I can draw the Gateway chain: request → JWT check → rate limit → route.
- [ ] I can configure a Circuit Breaker with sensible thresholds.
- [ ] I can explain when to use `@Retry` — and when not (idempotency).
- [ ] I can draw the Order → Inventory → Payment Saga with **both** the happy and compensation paths.
- [ ] I can name two technical-debt items in the platform and their risks.
- [ ] I can apply `@Cacheable` and verify it with `redis-cli`.
- [ ] I can commit with the correct message format and push.
- [ ] I can explain Choreography vs Orchestration.

Next: [Phase 2](../phase-2-quality-deployment/README.md)
