# setup.md - Axovia AI Web Assistant Initialization Framework

## Purpose

This document contains **explicit setup instructions** for the Cursor AI Coding Assistant to:

- Initialize the Axovia AI Website Project
- Maintain full environment, file, and feature integrity
- Enable seamless collaboration with the human and prevent ALL code duplication

> ⚠️ **ABSOLUTE RULE:** NEVER IMPLEMENT A TASK unless it is documented and present in `axovia-flow/planning/implementation-plan.md` ⚠️ **ABSOLUTE RULE:** ALWAYS ASK THE HUMAN IMMEDIATELY IF CONFUSED

---

## Project Overview

- **Name:** Cannasol Technologies Executive Dashboard
- **Type:** Sleek, modern client-facing website
- **Purpose:** Showcase software engineering skill and AI Agentic SaaS systems for clients
- **Frontend:** Flutter Web
- **Backend:** Firebase Functions (Python)
- **Cloud Services:** Firebase Hosting, Firestore, Storage, Functions
- **Deployment:** Auto-deploy on `main` + manual release toggle

---

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/axovia/axovia-ai-web.git
cd axovia-ai-web
```

### 2. Install Flutter & Dart

Ensure you're using Flutter 3.19.5+

```bash
flutter --version
flutter pub get
```

### 3. Setup Firebase Tools

```bash
npm install -g firebase-tools
firebase --version
```

### 4. Authenticate Firebase

```bash
firebase login
firebase init
```

Choose: `Hosting`, `Firestore`, `Functions`, `Emulators`, `Storage`

### 5. Python Cloud Functions

```bash
cd functions/python
python3 -m venv env
source env/bin/activate
pip install -r requirements.txt
```

### 6. Environment Variables

Copy and edit:

```bash
cp axovia-flow/config/env-template.md .env
```

Then fill in all values.

---

## File & Directory Responsibilities

| File / Directory    | Purpose                                           |
| ------------------- | ------------------------------------------------- |
| `axovia-flow/`      | Agent framework, documentation, and task tracking |
| `lib/`              | Flutter web app source code                       |
| `functions/python/` | Python backend agents and API handlers            |
| `firebase.json`     | Firebase hosting config                           |
| `pubspec.yaml`      | Flutter package manager file                      |

---

## Initialization Sequence

> MUST BE FOLLOWED IN ORDER:

1. Execute Pre-Task Checklist in `pre-task.md`
2. Confirm all architecture and code structure with `codebase-structure.md`
3. Load memory from `context-memory.md`
4. Identify current task from `implementation-plan.md`
5. Begin only AFTER these steps are verified

---

## Rules for Framework Integrity

### 1. Duplication Prevention

- NEVER create code without checking the `component-registry.md`
- NEVER create functions or files with similar names without verifying usage
- ALL new components must be logged in the registry immediately

### 2. Context Memory

- ALWAYS load `context-memory.md` and `current-task.md` first
- ALWAYS update memory after completing a task

### 3. Verification

- No task is complete without the Post-Task Checklist
- Must meet 90%+ test coverage for new code
- Must commit and push code + update all linked files

### 4. Communication

- ANY uncertainty = file an entry in `requests-to-human.md`
- Human guidance always overrides defaults

### 5. Setup Finalization

- Mark setup as complete in `implementation-plan.md`
- Push final initialized structure to GitHub
- Confirm Firebase project successfully deployed

---

## Final Notes for AI Coding Assistant

- You are operating under strict duplication protection
- You are NEVER to proceed without verifying context, task list, and memory
- If you don’t understand the prompt, ASK THE HUMAN IMMEDIATELY
- Do not try to guess. Your job is precision and clarity.

---

Once complete, proceed to load `resume.md` and `pre-task.md` before the next task.

---

