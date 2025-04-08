# resume.md — Workflow Resumption Protocol

## Purpose

This file defines the **standardized protocol for resuming development** on the Axovia AI Website project using the Cursor AI Coding Assistant Framework.

This ensures consistency, continuity, and accuracy across all sessions — especially after interruptions, context loss, or switching environments.

> ⚠️ **ABSOLUTE RULE:** NEVER RESUME WORK WITHOUT COMPLETING THIS FILE IN ORDER.
> ⚠️ **NEVER GUESS — Always ask the human if unsure.**

---

## 1. Session Resumption Procedure

### A. Load Project Memory

- Open and review `axovia-flow/memory/context-memory.md`
- Understand the overall architecture, recent updates, and ongoing design decisions
- Reconstruct the mental model of current app structure and purpose

### B. Load Current Task

- Read the latest state in `axovia-flow/memory/current-task.md`
- Ensure it includes description, task name, and status (in-progress or blocked)
- Confirm it’s the same task you are about to resume

### C. Verify Project Plan

- Open `axovia-flow/planning/implementation-plan.md`
- Confirm the current task is the next valid task in the sequence
- Cross-reference that no required predecessor tasks are marked incomplete

### D. Load Technical Files

- Open `component-registry.md` to avoid duplication
- Review `codebase-structure.md` for the latest architecture
- Open `design-system.md` for UI/UX styling and class references
- Validate `.env` structure using `env-template.md`

### E. Load Communications

- Check `requests-to-human.md` for unresolved questions
- Review any new decisions or replies in `answers-to-agent.md`
- Record any additional clarifications needed as new REQs

---

## 2. Verification Procedure

### A. Context Summary

- Write a 3–5 sentence summary in `current-task.md` describing:
  - What task is being resumed
  - What was completed before the pause
  - What remains to be done and dependencies

### B. Uncertainty Handling

- If anything is unclear:
  - Document the gap in `development-notes.md`
  - File a REQ in `requests-to-human.md`
  - Label `current-task.md` as `blocked` until resolved

### C. Alignment Confirmation

- Confirm:
  - Task name matches the file in `implementation-plan.md`
  - There are no uncommitted or out-of-sync changes
  - Necessary credentials are present in the environment

---

## 3. Re-Establishing Workflow

### A. Complete Pre-Task Checklist

Before continuing:

- Load and complete `pre-task.md` fully for the current task
- Confirm all prerequisites and anti-duplication checks are done

### B. Activate IDE and Environment

- Open the project in Cursor
- Confirm Flutter version is 3.19.5+
- Activate Python environment for Firebase Cloud Functions
- Run Firebase emulators or connect to live Firebase project as configured

### C. Log Session Start

- Add to `context-memory.md`:

```markdown
## Session Resumed — [Date/Time]
- Task: [Current Task Name]
- Description: [Short summary]
- Human guidance applied: [If any]
```

---

## 4. Decision History Review

### A. Review Guidance Archive

- Open `answers-to-agent.md`
- Skim for recent human decisions or overrides
- Reconfirm rationale for key implementation choices

### B. Review Development Log

- Read the latest entries in `development-notes.md`
- Look for relevant workarounds, blockers, or pivot points

### C. Update Notes if Needed

- If changes were made since last session:
  - Document what changed and why
  - Link to any approvals or REQs used

---

## Final Reminder to Cursor Assistant

> NEVER BEGIN IMPLEMENTATION until this protocol is completed.
> ❌ Skipping this file leads to duplication, missing memory, and architectural drift.

Once complete, load `pre-task.md` and begin pre-task checklist for your assigned task.

---

