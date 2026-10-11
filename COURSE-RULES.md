# Course Rules

These rules keep the course fair and predictable. They work together with [ASSESSMENT.md](ASSESSMENT.md) (how you are graded) and [docs/onboarding/github-workflow.md](docs/onboarding/github-workflow.md) (how you use Git).

---

## 1. Attendance

- Attendance is expected at every scheduled session. The four **offline anchor days** (Sessions 1, 9, 17 and 25) and the final presentation day require in-person attendance.
- Sessions may be recorded.
- If you miss a session, complete these **before the next session**: slides and tutorial, recording (if available), the lab, and the pre-reading for the next session.

## 2. Preparation and the Knowledge Check

- Every session has about 15 minutes of pre-reading. The session opens with a **Knowledge Check**: 3 questions, asked **by name**, not by volunteers.
- If you did not read, you still answer honestly with what you understood. There is no penalty — the point is the discipline.

## 3. Labs

- Every session has a mandatory lab with unit tests (20 % of the lab grade).
- A lab is complete only when it meets its **Definition of Done**:
  - the code builds and `mvn test` is green;
  - every acceptance criterion in the session handout is satisfied;
  - the checkpoint commit (correct format) is **pushed to your own repository**.
- A lab that is not committed and pushed is not graded.
- Bonus tasks are optional (+5 each) and never lift a grade above 100 %.

## 4. Homework and late work

- Homework is recommended, never graded, but later sessions assume you did it.
- Finish an unfinished lab as homework and push it **before the next session starts**.
- Work pushed after the next session has started receives feedback only, unless the trainer approved an extension in advance.

## 5. Git workflow

Sessions 1–24 — **your own private copy** of `microservices-pro-platform`, created with *Use this template*. You push to your own `main`; nobody else writes to it.

```
Use template → Clone → (add upstream) → Implement → mvn test → Commit → Push to your main
```

- The instructor's `reference` branch is for **reading and comparing only**. Never merge, rebase or cherry-pick it. It is closed during the Mid-Course Exam.
- Capstone (Sessions 25–29) — one **team repository**, protected `main`, short-lived branches, Pull Requests with one teammate review (answered within 24 hours).

Full details and commands: [docs/onboarding/github-workflow.md](docs/onboarding/github-workflow.md).

## 6. Commit messages

Use lowercase and hyphens. Three formats only:

```
session-NN: short-description-of-what-was-done      # Sessions 1–24
capstone-Lx: short-description                      # Capstone
exam-session-09: mid-course-exam                    # Mid-Course Exam
```

Example: `session-07: add-choreography-saga-order-inventory-payment`. A wrong format means you will be asked to re-commit before grading.

## 7. Code quality

- Follow Clean Code, meaningful names and REST naming conventions.
- Prefer **constructor injection** in the code you write. Some slides use `@Autowired` fields to keep live-coding short — that is a teaching shortcut, not a recommendation.
- Dev-only configuration must be labelled `# DEV ONLY` (see [docs/standards](docs/standards/COURSE-STANDARDS.md)).
- **Never commit secrets** (passwords, tokens, keys). If one is pushed, rotate it immediately and tell the trainer — deleting the file does not remove it from Git history.

## 8. Daily quizzes and the Mid-Course Exam

- The daily quiz is individual and taken at the end of the session.
- The Mid-Course Exam (Session 9) is individual and supervised. **Not allowed:** AI assistants, forums, classmates, and the `reference` branch. Sharing code during the exam gives zero to **both** trainees.

## 9. Academic integrity

- Discussing ideas is encouraged. **Code submission is individual** (labs, exam).
- Copying a solution defeats the purpose of the lab and shows in the Knowledge Check and the Capstone oral Q&A, where you must explain every line you claim.
- AI assistants may help you *understand* a concept. Do not use them to generate the lab solution you submit.
- In the Capstone, every team member must be able to explain **every** service, not only the one they wrote.

## 10. Respect and communication

- Be respectful in sessions, chats and pull requests — see [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).
- Questions are encouraged in every session. Discussion is part of learning.
- If you are blocked or behind, tell the trainer **early**. A 30-minute catch-up conversation is always better than a silent gap.

## 11. Certification

| Score | Result |
|---|---|
| 90–100 % | Certificate of Distinction |
| 75–89 % | Certificate of Completion (Merit) |
| 60–74 % | Certificate of Completion |
| below 60 % | Retake: resubmit failed labs before certification |
