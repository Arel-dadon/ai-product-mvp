# PRODUCT

## Product Name
TBD

---

# Vision

Build a reliable, developer-first automation platform that allows users to create, execute, monitor, and debug workflows visually and programmatically.

The platform combines strengths from tools like:
- n8n
- Zapier
- Power Automate
- Make
- Temporal

while focusing heavily on:
- reliability
- observability
- retry safety
- execution visibility
- developer control

---

# Problem

Existing automation platforms often suffer from:
- weak debugging visibility
- unreliable execution behavior
- poor retry handling
- difficult scaling
- hidden failures
- poor developer experience
- limited workflow observability

Users need:
- clear execution history
- reliable retries
- transparent logs
- workflow recovery
- execution guarantees
- easier debugging

---

# Target Users

## Initial Users
- Developers
- DevOps engineers
- IT automation engineers
- SRE teams
- Internal operations teams

---

# MVP Goal

Create a minimal but production-grade workflow engine capable of:

- Creating workflows
- Running workflows
- Scheduling workflows
- Retrying failed steps
- Viewing execution logs
- Tracking workflow state
- Executing trigger/action nodes
- Persisting execution history

---

# MVP Features

## Workflow Builder
- Basic node-based editor
- Trigger nodes
- Action nodes
- Conditional logic

## Workflow Engine
- Queue-based execution
- Step execution state
- Retry support
- Failure handling
- Timeout handling

## Observability
- Execution logs
- Step status
- Failure tracking
- Retry visibility

## Authentication
- Basic user accounts
- API keys

## Infrastructure
- PostgreSQL
- Redis queue
- Docker support

---

# Non-Goals (Phase 1)

- Hundreds of integrations
- Marketplace
- AI agents
- Kubernetes
- Enterprise RBAC
- Multi-region scaling
- Complex billing
- Mobile app

---

# Initial Tech Stack

## Frontend
- React
- TypeScript

## Backend
- FastAPI or NestJS

## Infrastructure
- PostgreSQL
- Redis
- Docker

---

# Core Engineering Principles

- Reliability first
- Idempotent execution
- Clear observability
- Strong retry semantics
- Simplicity over premature scale
- Explicit failure visibility
