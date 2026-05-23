# DATABASE

# Purpose

The database stores the source of truth for:
- users
- workflows
- workflow versions
- executions
- execution steps
- logs
- credentials metadata

---

# Core Tables

## users
Stores platform users.

Fields:
- id
- email
- name
- created_at
- updated_at

---

## workflows
Stores workflow ownership and metadata.

Fields:
- id
- user_id
- name
- description
- is_active
- created_at
- updated_at

---

## workflow_versions
Stores immutable workflow definitions.

Fields:
- id
- workflow_id
- version_number
- definition_json
- created_at

Rule:
- executions should always reference a specific workflow version.

---

## executions
Stores each workflow run.

Fields:
- id
- workflow_id
- workflow_version_id
- status
- trigger_type
- started_at
- finished_at
- created_at

Statuses:
- pending
- running
- completed
- failed
- cancelled
- timed_out

---

## execution_steps
Stores each step inside an execution.

Fields:
- id
- execution_id
- step_id
- step_type
- status
- attempt_count
- max_attempts
- input_json
- output_json
- error_message
- started_at
- finished_at
- created_at

Statuses:
- pending
- running
- completed
- failed
- skipped
- retrying

---

## execution_logs
Stores detailed logs for observability.

Fields:
- id
- execution_id
- execution_step_id
- level
- message
- metadata_json
- created_at

Levels:
- info
- warning
- error
- debug

---

## credentials
Stores encrypted credential references.

Fields:
- id
- user_id
- provider
- name
- encrypted_secret
- created_at
- updated_at

Rule:
- never store plaintext secrets.
