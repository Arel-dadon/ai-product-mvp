# ARCHITECTURE

# High-Level System Design

The platform consists of:

- Frontend Application
- API Backend
- Workflow Engine
- Queue System
- Database
- Execution Workers
- Scheduler
- Logging/Observability Layer

---

# Core Components

## Frontend
Responsibilities:
- Workflow builder UI
- Execution monitoring
- Logs visualization
- Workflow management

Tech:
- React
- TypeScript

---

## API Backend
Responsibilities:
- Authentication
- Workflow CRUD
- Execution APIs
- Trigger management
- User management

Tech:
- FastAPI or NestJS

---

## Workflow Engine
Responsibilities:
- Parse workflow definitions
- Execute workflow steps
- Track workflow state
- Handle retries
- Handle failures

Core Requirements:
- Idempotent execution
- Retry-safe execution
- Persistent execution state

---

## Queue System
Responsibilities:
- Async execution
- Retry scheduling
- Delayed jobs
- Worker coordination

Tech:
- Redis Queue

---

## Database
Responsibilities:
- Store workflows
- Store executions
- Store logs
- Store step states

Tech:
- PostgreSQL

---

## Execution Workers
Responsibilities:
- Execute workflow steps
- Process queued jobs
- Handle retries
- Update execution state

---

## Scheduler
Responsibilities:
- Cron triggers
- Delayed execution
- Recurring workflows

---

# Core Engineering Principles

- Reliability over features
- Explicit failure handling
- Strong observability
- Idempotent workflow execution
- Queue-based execution
- Simple architecture initially

---

# Initial Constraints

- Monolith architecture
- Single database
- Single Redis instance
- Docker-based deployment
- Minimal integrations initially

---

# Initial Workflow Flow

1. User creates workflow
2. Workflow stored in database
3. Trigger fires
4. Execution record created
5. Job added to queue
6. Worker processes step
7. State updated after each step
8. Logs persisted
9. Retry on failure
10. Final workflow state stored
