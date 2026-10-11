# Contributing

Thank you for helping improve this course. This repository holds **learning materials only** (slides, tutorials, guides). The platform source code lives in [`microservices-pro-platform`](https://github.com/SayedBaladoh/microservices-pro-platform).

## Reporting a mistake or unclear content

Open an **Issue** and include:

- **Session** (e.g. Session 7) and **file name** (e.g. `Session_07_Saga_Kafka.pdf`, slide or page number)
- **Lab** (if the problem is in a lab, e.g. Lab 5A)
- **Expected behaviour** vs **actual behaviour**
- Your environment if it is a setup problem: OS, `java -version`, `docker --version`
- A short error message or log excerpt (never paste secrets, tokens or passwords)

Problems in the platform code (a service that does not start, a failing test) belong in the platform repository, or go to the trainer directly.

## Suggesting an improvement

- Typos, broken links, clearer wording, a missing explanation → open an Issue or a Pull Request.
- New topics or changes to the course structure → open an Issue first and describe the *problem* the change solves (the course teaches problem-first).

## Pull Requests

- Keep every PR focused on **one topic**.
- Describe what changed and why, and link the related Issue.
- Documents are Markdown or PDF. Follow the file naming used in `sessions/`:
  - slides: `Session_NN_<Topic>.pdf`
  - extended tutorial: `Session_NN_<Topic>_Tutorial.pdf`
  - no spaces, no `&`, no special characters in file names.
- Do **not** add trainer-only material (solutions, answer keys, grading sheets) or any secret.
- By contributing you agree that your contribution is released under the repository [LICENSE](LICENSE).

## Review

The trainer reviews Issues and PRs. Small fixes are usually merged within a few days; larger changes may be scheduled for the next cohort.

## Conduct

Be respectful and constructive. See [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).
