---
title: "Tasks: {Feature Name}"
date: YYYY-MM-DD
owner: ""
status: draft
---

# Tasks: {Feature Name}

> Copy this template. Rename to `{feature-slug}-tasks.md`.
> Or generate automatically: see `.github/agents/task-breakdown.agent.md`

## How to read this
- Tasks are ordered by dependency — do not reorder without checking blockers
- Each task = 1–2 engineer-days
- All acceptance criteria must pass before a task is closed
- Reference task ID in commit messages: `feat: TASK-001 set up project`

---

## Milestone 0 — Setup
> Unblocks all other work. Complete before any feature tasks start.

### TASK-001: Repository and environment setup
**Estimate:** 0.5 days
**Assigned to:** TBD
**Depends on:** nothing

Steps:
- [ ] Initialize repo with chosen framework
- [ ] Set up `.env.example` with all required variables from tech spec
- [ ] Configure linting and formatting
- [ ] Set up CI (GitHub Actions)

Acceptance criteria:
- [ ] `npm run dev` (or equivalent) runs without errors
- [ ] All env vars from tech spec are in `.env.example`
- [ ] CI passes on push

---

### TASK-002: Database setup and migrations
**Estimate:** 0.5 days
**Assigned to:** TBD
**Depends on:** TASK-001

Steps:
- [ ] Configure DB connection
- [ ] Write migration for {EntityName}

Acceptance criteria:
- [ ] Migration runs without errors
- [ ] Schema matches data models in tech spec

---

## Milestone 1 — {First component}
> Goal: {what this milestone delivers}

### TASK-003: {Task name}
**Estimate:** 1 day
**Assigned to:** TBD
**Depends on:** TASK-002

Steps:
- [ ]
- [ ]

Acceptance criteria:
- [ ]
- [ ]

---

## Milestone N — Integration & testing

### TASK-0XX: End-to-end test of core flow
**Estimate:** 1 day
**Depends on:** all previous milestones

Acceptance criteria:
- [ ] All API endpoints return correct responses
- [ ] Error cases return correct error codes
- [ ] No hardcoded secrets in codebase
- [ ] Test coverage ≥ 80% on new code

---

## Task summary table
| ID | Title | Estimate | Depends on | Milestone |
|----|-------|----------|-----------|-----------|
| TASK-001 | Setup | 0.5d | — | 0 |
| TASK-002 | DB migration | 0.5d | TASK-001 | 0 |

## Open Questions
- [ ] Question — owner: TBD

## Handoff Summary
> For engineers — this is your starting point.
- First task to pick up: TASK-001
- Critical path: TASK-001 → TASK-002 → ...
- Biggest risk / unknown:
- Who to ask if blocked:
