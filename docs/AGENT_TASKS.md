# AGENT TASKS

# Purpose

This file defines how AI agents should work on this repository without creating chaos.

---

# Global Rules For All Agents

- Do not change architecture without approval.
- Do not introduce new frameworks without approval.
- Do not touch unrelated files.
- Keep PRs small and focused.
- Add tests for engine-critical logic.
- Prefer simple, readable code over clever abstractions.
- Preserve existing docs and decisions.
- Explain tradeoffs in PR descriptions.

---

# Codex Role — Implementation Engineer

Codex should handle:
- backend scaffolding
- frontend scaffolding
- API endpoints
- database models
- migrations
- tests
- worker implementation
- queue wiring

Codex should NOT:
- redesign architecture
- choose new stack
- add unnecessary integrations
- rewrite unrelated files

---

# Claude Code Role — Senior Reviewer / Reliability Engineer

Claude should handle:
- architecture review
- failure-mode review
- retry/idempotency review
- security review
- concurrency analysis
- refactor review

Claude should NOT:
- generate massive rewrites without approval
- add scope
- optimize prematurely

---

# Jules Role — GitHub Automation / Maintenance

Jules should handle:
- small PRs
- CI setup
- linting
- formatting
- issue cleanup
- documentation updates
- dependency hygiene

Jules should NOT:
- own product architecture
- make large feature decisions
- merge without review

---

# First Implementation Order

## Task 1 — Backend Skeleton
Owner: Codex

Create backend foundation with:
- FastAPI or NestJS
- health check route
- project structure
- config loading
- basic test setup

No workflow logic yet.

---

## Task 2 — Database Schema
Owner: Codex

Implement initial schema for:
- users
- workflows
- workflow_versions
- executions
- execution_steps
- execution_logs
- credentials

---

## Task 3 — Execution Engine Design Review
Owner: Claude Code

Review:
- EXECUTION_ENGINE.md
- DATABASE.md
- WORKFLOW_DEFINITION.md

Focus:
- failure modes
- retries
- idempotency
- persistence
- worker crash scenarios

---

## Task 4 — CI Pipeline
Owner: Jules

Create GitHub Actions for:
- backend tests
- frontend tests later
- linting later
