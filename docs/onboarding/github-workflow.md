# GitHub Workflow

How you work with Git during the course. Two phases, two models:

| Phase | Where you work | Branch model |
|---|---|---|
| Sessions 1–24 | **Your own private copy** of the platform | You push to *your* `main` |
| Capstone (25–29) | **Your team repository** | Protected `main`, short-lived branches, Pull Requests |

Nobody else pushes to your repository, so you never conflict with classmates.

## 1. The repositories

| Repository | Role |
|---|---|
| `microservices-pro-platform` (instructor) | Starting code on `main`; instructor solution on `reference`; milestone tags |
| **Your copy** of it | Your labs, Sessions 1–24 |
| Capstone team repo | Created from the Capstone Starter Repo in Session 25 |

## 2. One-time setup

1. Open `microservices-pro-platform` on GitHub → **Use this template** → **Create a new repository**.
2. Owner: you · Name: `microservices-pro-platform` · Visibility: **Private**.
3. In your copy: **Settings → Collaborators → add the trainer**.
4. Clone and link the instructor repository:

```bash
git clone https://github.com/<you>/microservices-pro-platform.git
cd microservices-pro-platform
git remote add upstream https://github.com/SayedBaladoh/microservices-pro-platform.git
git fetch upstream --tags
git remote -v        # origin = yours · upstream = instructor
```

## 3. Your loop in every session

```bash
git status
mvn test                                              # must be green
git add .
git commit -m "session-04: add-circuit-breaker-and-retry-on-order-payment"
git push origin main
```

- The message format is `session-NN: short-description`. Wrong format = re-commit before grading.
- Push **before the next session starts**. Unpushed work is not graded.
- Never commit secrets (passwords, tokens, real keys).

## 4. Using the `reference` branch

`reference` is the instructor's implementation, updated as the course progresses. It is a **lifeline for comparison**, not something to copy.

```bash
git fetch upstream

# See differences for one service
git diff main upstream/reference -- services/product-service/

# Read one file without switching branches
git show upstream/reference:services/product-service/src/main/java/.../ProductService.java

# Jump to the instructor's state at a milestone (read-only)
git tag -l 'milestone-*'
git show milestone-03:services/order-service/
```

**Never** merge, rebase or cherry-pick `reference` into your `main`. Your learning comes from writing the code. During the Mid-Course Exam the branch is closed.

## 5. If you fall behind

1. Finish the lab as homework and push before the next session.
2. If you are badly stuck, read the relevant files on `reference`, close them, and re-implement from memory.
3. Ask the trainer for a 30-minute catch-up. Do not wait until the end of the phase.

## 6. Capstone workflow (S25–S29)

- One repository per team, created from the Capstone Starter template; the trainer is added as a collaborator.
- **`main` is protected** after L0: no direct commits.
- Short-lived branches (max 1–2 days), merged by **Pull Request** with one teammate review (answered within 24 hours).
- Commit format: `capstone-Lx: short-description` — e.g. `capstone-L2: add-payment-idempotency`.
- Pair work: add `Co-authored-by: Name <email>`.
- Pull `main` daily. Never reformat shared files (parent POM, `docker-compose.yml`).
- Each member must commit in **at least 3 different services** — the trainer reads the git log at every gate.

```bash
git switch -c capstone-L2-payment-idempotency
# ... work, test ...
git push -u origin capstone-L2-payment-idempotency
# open a Pull Request into main, request a teammate's review
```

## 7. Common problems

| Problem | Fix |
|---|---|
| `git push` rejected | You edited on GitHub as well: `git pull --rebase origin main`, then push |
| Pushed a secret | Rotate it immediately, then tell the trainer — deleting the file does not remove it from history |
| `upstream/reference` not found | `git fetch upstream` (check `git remote -v`) |
| Accidentally merged `reference` | `git reset --hard origin/main` before pushing; ask for help if already pushed |
| Wrong commit message (not yet pushed) | `git commit --amend -m "session-NN: ..."` |
