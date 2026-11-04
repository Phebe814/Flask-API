# AI Log — crane-api

Machine-oriented log. Every edit and decision is recorded here, newest at the bottom.
Read **Current State** first, then the most recent entries.

## Current State
<!-- Keep this section short and always up to date. Overwrite it (do not append). -->

- **Phase:** Setup
- **Last entry:** AI-002
- **Stack:** Python + Flask 3.1.3, venv at `.venv/`
- **Code written:** none yet
- **Open questions:** see "Open Questions" below
- **Next step:** wait for user to add project brief to `project-details/`, then plan

## Open Questions
<!-- Remove an item once answered; record the answer as a log entry. -->

- Q1: What is the project brief / what should the crane API do? (awaiting `project-details/`)
- Q2: Should `.venv/` be removed from git and added to `.gitignore`? (currently staged)
- Q3: `requirements.txt` is saved as UTF-16 (from PowerShell `>`); re-save as UTF-8 so `pip install -r` works reliably?

---

## Entry Template

```
### AI-NNN | YYYY-MM-DD | <type: EDIT | DECISION | QUESTION | ANSWER | FIX | NOTE>
- summary: <one line>
- files: <paths touched, or "-">
- reason: <why>
- decided_by: <user | ai | ai+user>
- related: <AI-xxx ids, or "-">
- human_log: <yes | no>   # yes = also written to DECISION_LOG.md
```

---

## Entries

### AI-001 | 2026-11-03 | EDIT
- summary: Created logging system and passdown file
- files: CLAUDE.md, docs/AI_LOG.md, docs/DECISION_LOG.md, project-details/README.md
- reason: User requested an AI log, a human-readable decision log, a project-details folder, and a passdown file read at every session start
- decided_by: user
- related: -
- human_log: yes

### AI-002 | 2026-11-03 | DECISION
- summary: Use CLAUDE.md as the passdown file; logs live in docs/; folder named `project-details` (hyphen, no space)
- files: CLAUDE.md
- reason: Claude Code auto-loads CLAUDE.md every session, guaranteeing logs are read before work; hyphenated folder name avoids path-quoting issues on Windows/shell
- decided_by: ai
- related: AI-001
- human_log: yes
