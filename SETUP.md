# Setup Guide

Complete this **before Session 1** (≈ 1.5–2 hours). Session 1 assumes your machine already works.
Step-by-step installation help lives in [docs/onboarding/environment-setup.md](docs/onboarding/environment-setup.md); this page is the checklist and the verification.

## 1. Required now (Session 1)

| Tool | Version | Verify |
|---|---|---|
| JDK | 21 (LTS, e.g. Temurin) | `java -version` → `21.x` |
| Maven | 3.9+ | `mvn -version` → shows Java 21 |
| Docker Desktop | 4.x+, **running** | `docker --version` · `docker compose version` · `docker run hello-world` |
| Git | 2.x+ | `git --version` (name + email configured) |
| IDE | IntelliJ IDEA (Community is enough) or VS Code + Spring Boot Extension Pack | opens a Spring Initializr project |
| Postman | latest | opens |
| GitHub account | — | you can create a private repository |

**Hardware:** 16 GB RAM recommended; give Docker **at least 6 GB** (the Capstone needs it — Keycloak and Kafka are heavy). ≈ 20 GB free disk.

## 2. Install later (do not install early)

Each tool is taught in its own session. Install it the week it is needed.

| Tool | Needed from | Verify |
|---|---|---|
| `kubectl` 1.28+ | S14–S15 | `kubectl version --client` |
| minikube **or** kind (local cluster) | S14–S15 | `kubectl get nodes` |
| ArgoCD (provided by the trainer) | S14 | ArgoCD UI opens |
| Helm 3 | S16 | `helm version` |
| `istioctl` | S21 | `istioctl version` |
| k6 | S23 | `k6 version` (or run it via Docker) |

## 3. Get the platform repository

```bash
# 1. On GitHub: open microservices-pro-platform → "Use this template" → "Create a new repository"
#    Owner: you · Visibility: PRIVATE · Name: microservices-pro-platform
# 2. Add the trainer as a collaborator (Settings → Collaborators)
# 3. Clone YOUR copy
git clone https://github.com/<your-username>/microservices-pro-platform.git
cd microservices-pro-platform
# 4. Link the instructor's repository so you can read the reference branch
git remote add upstream https://github.com/SayedBaladoh/microservices-pro-platform.git
git fetch upstream
git branch -a        # you should see main and upstream/reference
```

Full workflow: [docs/onboarding/github-workflow.md](docs/onboarding/github-workflow.md).

## 4. Start the infrastructure

```bash
docker compose up -d
docker compose ps
```

Wait ~30 seconds. **Seeing extra containers running is expected** — the compose file starts infrastructure for the whole course. Only use what the current session teaches.

| Container | You first use it in | Taught in |
|---|---|---|
| PostgreSQL | S1 | S1 |
| Redis | S3 (Gateway rate limiting) | S8 (caching) |
| Kafka + Zookeeper | S7 | S7 |
| Zipkin | S17 | S17 |
| Prometheus, Grafana | S17 | S17 |
| Keycloak | S19 | S19 |

Do not explore the later containers early.

Verify PostgreSQL:

```bash
docker exec -it postgres psql -U postgres -c "SELECT 1"
```

## 5. Smoke-test your Java toolchain

1. In your IDE create a Spring Initializr project: Java 21 · Maven · Spring Boot 3.x · dependency *Spring Web* (+ Actuator).
2. Run it and open `http://localhost:8080/actuator/health` → `{"status":"UP"}`.
3. Stop it (the port is needed later by the API Gateway).

## 6. Ports used by the platform

| Service | Port |
|---|---|
| API Gateway | 8080 |
| Product Service | 8081 |
| Order Service | 8082 |
| Payment Service | 8083 |
| Inventory Service | 8084 |
| Notification Service | 8085 |
| Config Server | 8888 |
| Eureka Server | 8761 |
| PostgreSQL | 5432 |
| Redis | 6379 |
| Kafka | 9092 |
| Zipkin | 9411 |
| Prometheus | 9090 |
| Grafana | 3000 |
| Keycloak | 8180 |

If a port is busy, find the process: `lsof -i :<port>` (macOS/Linux) or `netstat -ano | findstr :<port>` (Windows).

## 7. Final checklist

- [ ] `java -version` shows 21 and `mvn -version` shows Java 21
- [ ] Docker is running; `docker run hello-world` works
- [ ] Your private copy of `microservices-pro-platform` is cloned; `git branch -a` shows `main` and `upstream/reference`
- [ ] `docker compose up -d` runs without errors; PostgreSQL answers
- [ ] The test Spring Boot project returns `UP` on `/actuator/health`
- [ ] Pre-Session 1 reading done (see the [Onboarding Guide](docs/Trainee_Onboarding_Guide.pdf))

**Problems?** Contact the trainer **before** Session 1, not during it.
