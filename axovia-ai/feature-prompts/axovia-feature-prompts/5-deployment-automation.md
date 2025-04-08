# 5-deployment-automation.md — Firebase CI/CD + Feedback Enforcement

## Feature Title: CI/CD Automation + GitHub Feedback Loop (Early Enforcement)

## Objective
Establish a continuous integration + deployment (CI/CD) pipeline that:
- Deploys automatically to Firebase on push to `main`
- Deploys preview branches to staging
- **Blocks agent progress if pipeline fails**
- Includes feedback loop script to validate pipeline state before continuing

---

## CI/CD Goals
- Automate testing, building, and deploying
- Detect and log any errors early
- Prevent regressions
- Run feedback verification script after every push

---

## GitHub Workflows to Create

| File | Purpose |
|------|---------|
| `.github/workflows/firebase.yml` | Deploys app to Firebase Hosting on push/merge |
| `.github/workflows/lint-test.yml` | Runs format, lint, and unit tests for Dart + Python |
| `ci/pipeline-feedback-check.sh` | Feedback loop validator: blocks agent if failed |

---

## Agent Instructions

### Pre-Implementation
- [ ] Confirm Firebase CLI + project initialized (from Feature #1)
- [ ] Confirm GitHub repo is connected to Firebase via CI token
- [ ] Load `.env` and confirm `ENVIRONMENT=staging` or `production`

### Implementation
#### firebase.yml
- Trigger on push to `main` and PR to `main`
- Run:
  - Flutter build web
  - Firebase deploy (functions, hosting)

#### lint-test.yml
- Run Dart `flutter analyze` + `flutter test`
- Run Python `black` + `pytest`
- Fail CI if test coverage < 90%

#### pipeline-feedback-check.sh
- Uses GitHub API to:
  - Poll latest run status
  - Wait for all jobs to complete
  - Output ✅ or ❌ result
- **MUST BE CALLED at the end of post-task.md by the agent**
- If ❌, the agent is blocked from advancing to the next task

### Post-Implementation
- [ ] Test PR and push triggers
- [ ] Run pipeline check manually to verify behavior
- [ ] Add full test coverage to all jobs
- [ ] Register workflows and CI logic in `component-registry.md`
- [ ] Complete `post-task.md`

---

## Acceptance Criteria

As a **quality-first AI assistant**, I can:
- ✅ Trigger automated CI build on every push
- ✅ Deploy to Firebase hosting from `main` branch
- ✅ Deploy preview from PR branches
- ✅ Run full tests and linting for Dart and Python
- ✅ Block forward progress if CI pipeline fails

---

## Notes
This is **mission critical**. It guarantees:
- No broken pushes
- No incomplete implementations
- No regressions past CI

> ⚙️ From now on, quality is non-negotiable. No CI = no commit = no feature advance.
