# Project Decision Log — crane-api

A readable record of the key decisions made during this project, why they were made, and how the project progressed.
Intended for review and for writing the final project summary.

---

## Summary at a Glance

| # | Date | Decision | Made by |
|---|---|---|---|
| D1 | 2026-11-03 | Set up a logging system to track all work and decisions | Student |
| D2 | 2026-11-03 | Use an automatically loaded handover file so the AI assistant always starts with full context | AI (approved by student) |

---

## Decisions

### D1 — Track all work and decisions in logs
**Date:** 2026-11-03 · **Made by:** Student

**Decision:** Keep two logs: a detailed technical log for the AI assistant (`docs/AI_LOG.md`) and this human-readable decision log.

**Why:** To keep a clear history of the project so it can be summarised and presented at the end.

---

### D2 — Handover file for the AI assistant
**Date:** 2026-11-03 · **Made by:** AI (approved by student)

**Decision:** A `CLAUDE.md` file is loaded automatically at the start of every AI session. It tells the assistant to read the logs and the `project-details/` folder before starting any work.

**Why:** Each AI session starts without memory of the last one. This file makes sure no context is lost between sessions.

**Alternatives considered:** Reminding the AI manually each session. Rejected because it's easy to forget.

---

<!-- Template for new decisions:

### Dn — <short title>
**Date:** YYYY-MM-DD · **Made by:** <Student | AI | AI (approved by student)>

**Decision:** <what was decided>

**Why:** <reasoning in plain language>

**Alternatives considered:** <optional>

**Impact:** <optional: what this changed in the project>

-->
