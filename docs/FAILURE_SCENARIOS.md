# FAILURE SCENARIOS

# Purpose

This document tracks dangerous failure scenarios in the automation platform and defines how the system should respond safely.

---

# Scenario 1 — Worker Crashes After External API Success

## Example

Worker:
1. Sends HTTP request successfully
2. External API completes action
3. Worker crashes BEFORE database save

Problem:
Retry may duplicate external side effect.

Risk:
- duplicate emails
- duplicate charges
- duplicate tickets
- duplicate messages

Potential Mitigations:
- idempotency keys
- external request tracking
- transactional outbox patterns
- deduplication logic

---

# Scenario 2 — Queue Job Runs Twice

Problem:
Redis/network issue causes duplicate execution pickup.

Risk:
Workflow step executes twice.

Potential Mitigations:
- execution locks
- step status validation
- idempotent actions

---

# Scenario 3 — Database Save Succeeds But Queue Push Fails

Problem:
Execution exists but worker never processes it.

Risk:
Workflow stuck forever.

Potential Mitigations:
- outbox pattern
- reconciliation jobs
- execution watchdogs

---

# Scenario 4 — External API Timeout

Problem:
Unknown whether action completed remotely.

Risk:
Unsafe retries.

Potential Mitigations:
- idempotency keys
- operation polling
- retry delay strategy
- compensating actions

---

# Scenario 5 — Scheduler Triggers Duplicate Jobs

Problem:
Multiple scheduler instances trigger same workflow.

Risk:
Duplicate executions.

Potential Mitigations:
- distributed locks
- unique execution constraints

---

# Scenario 6 — Partial Workflow Completion

Problem:
Workflow step 4 fails after steps 1-3 succeeded.

Risk:
System enters inconsistent business state.

Potential Mitigations:
- compensating workflows
- rollback strategy
- resumable execution

---

# Core Principle

Failures are normal.

The system must:
- expect failure
- persist state safely
- recover safely
- expose failures visibly
- avoid silent corruption
