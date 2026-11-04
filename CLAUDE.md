# CLAUDE.md — Passdown File (read first, every session)

This file is loaded automatically at the start of every Claude Code session.
It is the handover point between sessions.

## Start-of-session checklist (MANDATORY, before any work)

1. Read `docs/AI_LOG.md` — at minimum the **Current State** section and the last 5 log entries.
2. Read everything in `project-details/` that is relevant to the task (start with `project-details/README.md` index). This folder is maintained by the user and is the source of truth for requirements.
3. If anything in the task is unclear or conflicts with `project-details/`, **ask the user before acting**. Do not guess requirements.

## During / end of work (MANDATORY)

After every change to code, config, or structure, and after every decision:

1. **Append an entry to `docs/AI_LOG.md`** using the entry template in that file. Update its **Current State** section if it changed.
2. **If a decision was made** (design choice, library choice, scope change, trade-off, user answer to a question), **also append to `docs/DECISION_LOG.md`** in plain, presentable language for humans.
3. Never delete or rewrite past log entries. Corrections go in a new entry that references the old one by ID.

## Project basics

- Project: `crane-api` — school project.
- Stack (so far): Python, Flask 3.1 (see `requirements.txt`), virtualenv in `.venv/`.
- Shell: Windows (PowerShell / Git Bash).
- Activate venv: `.venv\Scripts\Activate.ps1` (PowerShell) or `source .venv/Scripts/activate` (Git Bash).

## File map

| Path | Purpose | Audience |
|---|---|---|
| `CLAUDE.md` | Passdown / rules for AI | AI |
| `docs/AI_LOG.md` | Every edit & decision, structured | AI |
| `docs/DECISION_LOG.md` | Decisions & progress, presentable | Human (lecturer / team / final report) |
| `project-details/` | Brief, requirements, rubric, notes from user | Both |
