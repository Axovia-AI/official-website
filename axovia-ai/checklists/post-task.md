# post-task.md — Completion Verification Checklist

## Purpose
This document serves as an indispensable checkpoint for finalizing **every task** enumerated in `implementation-plan.md`. It ensures that test coverage is robust, project memory is properly updated, and the overarching system architecture remains consistent.

> ⚠️ Under no circumstances should a task be declared complete unless each section of this checklist has been fully addressed.
> ⚠️ Should ambiguities arise, consult the human stakeholder for clarification.

---

## ✅ Post-Task Checklist (Doctoral-Level Reading)

### 1. Test Coverage
- [ ] Conduct comprehensive unit testing:
  - [ ] Python Cloud Functions and LangGraph agents (via PyTest)
  - [ ] Flutter user interface and state management
- [ ] Employ emulator or mocking strategies:
  - [ ] Simulate Calendly, Firebase, or LLM endpoints
- [ ] Devise integration tests:
  - [ ] Validate data flow between UI and Firebase
  - [ ] Assess Cloud Function triggers, including both success and error conditions
- [ ] Execute the complete test suite:
  - [ ] Confirm zero regressions
  - [ ] Ensure inclusion of edge cases (e.g., null states, network latency, invalid inputs)
- [ ] ✅ Attain a minimum of 90% test coverage

---

### 2. Memory Update
- [ ] Update `context-memory.md` to reflect:
  - [ ] A concise feature summary
  - [ ] Notable decisions, exceptions, or trade-offs encountered
  - [ ] Documentation of newly introduced architectural patterns
- [ ] Update `current-task.md` to:
  - [ ] Register task status as ✅ complete
  - [ ] Provide a final implementation summary
  - [ ] Enumerate any residual issues or queries

---

### 3. Documentation Updates
- [ ] Amend `component-registry.md` to catalog:
  - [ ] Newly generated components
  - [ ] The nature of each component (UI, logic, API, agent, etc.)
- [ ] Modify `codebase-structure.md` to:
  - [ ] Reflect added folders or modules
  - [ ] Outline structural reorganizations
- [ ] Amend `api-guide.md` as warranted, should endpoints be altered or appended
- [ ] Adjust `workflow-diagrams.md` if you introduced modifications to agent orchestration

---

### 4. Project Plan
- [ ] In `implementation-plan.md`, mark the concluding task as completed
- [ ] Identify the next task in sequence
- [ ] Reevaluate and, if necessary, update dependencies or priority designations
- [ ] Notify the human that the task has reached fulfillment

---

### 5. Version Control
- [ ] Stage all changes via `git add .`
- [ ] Formulate commit messages according to standard conventions:
  ```
  feat: [task-name] — summary
  ```
- [ ] Push code to the designated branch
- [ ] Incorporate the commit hash into `version-history.md`
- [ ] Integrate updates into `CHANGELOG.md` under the appropriate version

---

### 6. CI/CD Pipeline Verification
- [ ] Confirm success of the CI build (Firebase and Flutter)
- [ ] Validate linting and test phases
- [ ] Verify the successful deployment of any previews
- [ ] Execute `pipeline-feedback-check.sh` for final pipeline feedback:
  - [ ] ✅ Pipeline passes, agent may proceed
  - [ ] ❌ Pipeline failure, must pause task completion and file a new REQ

---

### 7. Agentic System Evaluation (If Applicable)
- [ ] Run tests for agent functionality with relevant mocks
- [ ] Validate concurrency safeguards, loop prevention, and token usage
- [ ] Update `metrics.md` with performance outcomes
- [ ] Record known issues in `errors.md`

---

### 8. Memory Reinforcement
- [ ] Insert architectural commentary into `context-memory.md`
- [ ] Note prospective constraints or expansions for agent logic
- [ ] Log orchestrator-level revisions should the logic have evolved

---

### 9. Final Documentation Sync
- [ ] Confirm that all preceding sections are adequately completed
- [ ] Validate that the code compiles and deploys without anomalies
- [ ] Ensure the newly introduced feature operates as anticipated
- [ ] Reaffirm adherence to the 90%+ coverage benchmark
- [ ] Acknowledge the human regarding task closure

---

> ✅ Once these tasks are all checked off, you may legitimately declare the task as complete.
> ❌ Skipping any item means the task remains **incomplete** until rectified.

---

