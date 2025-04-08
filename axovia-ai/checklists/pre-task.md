# pre-task.md — Task Initialization Checklist

## Purpose
This file contains the **mandatory pre-task checklist** for the Cursor AI Coding Assistant.

It prevents context loss, implementation drift, and duplication.

> ⚠️ DO NOT START ANY TASK until EVERY STEP in this file is completed.
> ⚠️ ASK THE HUMAN IMMEDIATELY if you are unsure about any requirement.

---

## Task Details
- [ ] **Task Name:** [MUST match task name in `implementation-plan.md`]
- [ ] **Feature Prompt:** [MUST match prompt file assigned to task]
- [ ] **Priority:** [High / Medium / Low — as defined in `implementation-plan.md`]

---

## 1. Memory Loading
- [ ] Load `context-memory.md`
- [ ] Load `current-task.md`
- [ ] Understand prior tasks and current scope
- [ ] Confirm this task is next in sequence

## 2. Architecture Validation
- [ ] Read `component-registry.md`
- [ ] Read `codebase-structure.md`
- [ ] Check if similar components already exist
- [ ] Check if this feature modifies shared or core components

## 3. Duplication Prevention
- [ ] Search for duplicate functionality across all files
- [ ] Review related feature prompts for overlap
- [ ] Confirm no other task has implemented this functionality
- [ ] Confirm new components will be logged in `component-registry.md`

## 4. Dependency Check
- [ ] Verify all prerequisite tasks are marked complete in `implementation-plan.md`
- [ ] Check that all required components already exist
- [ ] Check that this task does not break downstream tasks

## 5. Implementation Planning
- [ ] Identify applicable agent pattern (if relevant)
- [ ] Determine UI layout or data flow changes
- [ ] Define internal component interfaces (input/output)
- [ ] Estimate testing coverage areas
- [ ] Identify potential edge cases or user states

## 6. Technical Validation
- [ ] Confirm access to required Firebase credentials
- [ ] Confirm access to required social API credentials
- [ ] Confirm Firebase emulators or project are active
- [ ] Confirm correct Python + Flutter versions

## 7. Communication Check
- [ ] Check `requests-to-human.md` for unresolved blockers
- [ ] Check `answers-to-agent.md` for new approvals or decisions
- [ ] If anything is unclear, create a REQ ticket immediately

## 8. Final Verification
- [ ] Confirm task matches prompt file
- [ ] Confirm no unresolved dependencies exist
- [ ] Confirm readiness to begin work
- [ ] Update `current-task.md` with Pre-Task START status

---

Once all items are verified and checked, implementation may begin. You must update memory and reference documentation during and after development.

> ⚠️ DO NOT SKIP ANY STEPS.
> ⚠️ DO NOT GUESS — Always confirm unclear requirements with the human.

When finished with the task, proceed to `post-task.md` to complete delivery and verification.

