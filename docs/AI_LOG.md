# AI Log — crane-api

Machine-oriented log. Every edit and decision is recorded here, newest at the bottom.
Read **Current State** first, then the most recent entries.

## Current State
<!-- Keep this section short and always up to date. Overwrite it (do not append). -->

- **Phase:** Setup
- **Last entry:** AI-008
- **Stack:** Python 3.15 + Flask 3.1.3, venv at `.venv/` (rebuilt 2026-11-04 from `C:\Users\liewp\AppData\Local\Python\pythoncore-3.15-64\python.exe`)
- **Code written:** `api.py` (Flask-RESTful + Flask-SQLAlchemy, `UserModel`, `/api/users/` GET+POST; written by user), `create_db.py`
- **Env tip:** prefer `.venv\Scripts\python.exe -m pip` / `-m flask` over the `.exe` launchers
- **Open questions:** see "Open Questions" below
- **Next step:** wait for user to add project brief to `project-details/`, then plan

## Open Questions
<!-- Remove an item once answered; record the answer as a log entry. -->

- Q1: What is the project brief / what should the crane API do? (awaiting `project-details/`)

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

### AI-003 | 2026-11-04 | NOTE
- summary: Diagnosed install failure: `.venv\Scripts\pip.exe` launcher pointed at old venv path `C:\Users\liewp\Documents\crane-api\.venv` (venv had been moved); `python -m pip` worked. Advised Flask-RESTful is optional (plain Flask + jsonify is enough); not installed.
- files: -
- reason: User could not install Flask / Flask-RESTful
- decided_by: ai
- related: -
- human_log: no

### AI-004 | 2026-11-04 | ANSWER
- summary: Q3 answered: re-saved `requirements.txt` from UTF-16 to UTF-8 (no BOM); contents unchanged
- files: requirements.txt
- reason: User approved; `pip install -r` now reads it reliably
- decided_by: user
- related: Q3
- human_log: yes

### AI-005 | 2026-11-04 | FIX
- summary: Deleted and recreated `.venv` with base Python 3.15, reinstalled from requirements.txt; verified pip.exe, flask.exe and `GET /` returns 200
- files: .venv/
- reason: Moved venv had broken launchers with hard-coded old paths; user approved rebuild
- decided_by: user
- related: AI-003, Q2 (.venv still tracked in git, so the rebuild shows as many git changes)
- human_log: yes

### AI-006 | 2026-11-04 | FIX
- summary: Checked the folder move. Old folder `C:\Users\liewp\Documents\crane-api` no longer exists; git root is the new folder; no project file references the old path. Deleted stale `__pycache__/` (compiled at old path); regenerated cleanly on re-run.
- files: __pycache__/
- reason: User asked to verify everything lives in the new folder after moving it
- decided_by: ai
- related: AI-005
- human_log: no

### AI-007 | 2026-11-04 | FIX
- summary: `/api/users/` returned 500 `no such table: user_model`. DB had been created when the model was named `User` (table `user`); class later renamed to `UserModel` (table `user_model`). Re-ran `create_db.py` to create the missing table. Verified GET 200, POST 201; removed the test row. Old empty `user` table is left in the DB. Duplicate name/email on POST still gives 500 (IntegrityError, not handled); reported to user, not changed.
- files: instance/database.db
- reason: User asked to debug the SQLAlchemy traceback
- decided_by: ai
- related: -
- human_log: no

### AI-008 | 2026-11-04 | FIX
- summary: `api.py`, `create_db.py` and `.gitignore` were never pushed to GitHub. `.gitignore` (auto-written by venv) had a `*` rule ignoring every file, so commit 9d638ca only removed `.venv/` and added nothing. Removed the `#` comment and `*` lines; kept `.venv/`, `__pycache__/`, `instance/`, `*.db`, `desktop.ini`. Q2 resolved: `.venv/` is untracked (9d638ca) and ignored.
- files: .gitignore
- reason: User asked whether everything had been deleted from GitHub
- decided_by: ai
- related: Q2, AI-005
- human_log: no
