# Environment Setup — Step by Step

This is the detailed installation guide. The checklist, the required versions and the "install later" tools are in [SETUP.md](../../SETUP.md). Do everything here **at least 24 hours before Session 1**, so the trainer has time to help if something fails.

Estimated time: 1.5–2 hours.

## 0. What you need

| Tool | Version |
|---|---|
| JDK | 21 (LTS) |
| Maven | 3.9+ |
| Docker Desktop | 4.x+ (running) |
| Git | 2.x+ |
| IDE | IntelliJ IDEA (Community is enough) or VS Code + Spring Boot Extension Pack |
| Postman | latest |

Hardware: 16 GB RAM recommended, ≈ 20 GB free disk. Docker needs at least **6 GB** (see step 3).

## 1. JDK 21

Install **Eclipse Temurin 21** from <https://adoptium.net>, or:

| OS | Command |
|---|---|
| Windows | Download the `.msi` from adoptium.net and tick *Set JAVA_HOME* and *Add to PATH* |
| macOS | `brew install --cask temurin@21` |
| Linux | `curl -s "https://get.sdkman.io" \| bash` then `sdk install java 21-tem` |

Open a **new** terminal and verify:

```bash
java -version      # openjdk version "21.0.x"
javac -version     # javac 21.0.x
```

**Wrong Java version?**

- Windows: set `JAVA_HOME` to the JDK 21 folder (System Properties → Environment Variables) and move `%JAVA_HOME%\bin` to the top of `Path`.
- macOS/Linux: add to `~/.zshrc` or `~/.bashrc`, then `source` it:
  ```bash
  export JAVA_HOME=$(/usr/libexec/java_home -v 21)     # macOS
  export PATH=$JAVA_HOME/bin:$PATH
  ```

## 2. Maven

| OS | Command |
|---|---|
| Windows | Download the binary zip from maven.apache.org, extract it, add its `bin` folder to `Path` |
| macOS | `brew install maven` |
| Linux | `sdk install maven` |

```bash
mvn -version       # Apache Maven 3.9.x … Java version: 21.0.x
```

If Maven reports a different Java version, fix `JAVA_HOME` (step 1).

## 3. Docker Desktop

Install from <https://www.docker.com/products/docker-desktop> and **start it** — the whale icon must be active before every session.

- **Windows:** enable the WSL2 backend when asked. To give Docker 6 GB, create `%UserProfile%\.wslconfig`:
  ```ini
  [wsl2]
  memory=6GB
  ```
  then run `wsl --shutdown` and restart Docker Desktop.
- **macOS / Windows (Hyper-V):** Docker Desktop → Settings → Resources → Memory ≥ 6 GB.
- **Linux:** install Docker Engine + the Compose plugin, then allow your user to run it: `sudo usermod -aG docker $USER` and log in again.

```bash
docker --version
docker compose version
docker run hello-world      # "Hello from Docker!"
```

## 4. Git

Install from <https://git-scm.com> (Windows) or `brew install git` / your package manager.

```bash
git config --global user.name  "Your Name"
git config --global user.email "you@example.com"
git --version
```

Create a GitHub account if you do not have one. You will need to create a **private** repository from a template.

## 5. IDE and Postman

- **IntelliJ IDEA** (Community): set JDK 21 as the project SDK (File → Project Structure → SDK). Useful plugins: Spring Boot, Docker, Kubernetes (later), SonarLint.
- **VS Code:** install *Extension Pack for Java* and *Spring Boot Extension Pack*.
- **Postman:** install and create a free account to save collections.

## 6. Verify everything

```bash
java -version
mvn -version
docker --version
git --version
```

All four must print without errors, and `java -version` / `mvn -version` must show Java **21**.

## 7. Platform repository and infrastructure

Follow [github-workflow.md](github-workflow.md) §2 to create your private copy of `microservices-pro-platform`, then:

```bash
cd microservices-pro-platform
docker compose up -d
docker compose ps
docker exec -it postgres psql -U postgres -c "SELECT 1"
```

Seeing extra containers (Kafka, Redis, Zipkin…) is expected — each is taught in its own session. See [SETUP.md](../../SETUP.md) §4.

## 8. Spring Boot smoke test

1. In your IDE create a Spring Initializr project: Java 21 · Maven · Spring Boot 3.x · dependencies *Spring Web* and *Actuator*.
2. Run it and open `http://localhost:8080/actuator/health` → `{"status":"UP"}`.
3. Stop it — port 8080 is needed later by the API Gateway.

## Common problems

| Problem | Fix |
|---|---|
| `java -version` shows 11 or 17 | Fix `JAVA_HOME` and `Path` order (step 1), then open a **new** terminal |
| `mvn -version` shows the wrong Java | Same as above — Maven uses `JAVA_HOME` |
| `Cannot connect to the Docker daemon` | Docker Desktop is not running — start it and wait for the whale icon |
| `docker compose` is not recognised | Update Docker Desktop (Compose v2 is built in); on Linux install the compose plugin |
| Containers restart or are killed | Docker has too little memory — give it 6 GB (step 3) |
| `port is already allocated` | Another process uses the port: `lsof -i :<port>` (macOS/Linux) or `netstat -ano \| findstr :<port>` (Windows) |
| WSL2 error on Windows | Enable virtualisation in BIOS; run `wsl --update` |

Still stuck? Contact the trainer **before** Session 1, not during it.
