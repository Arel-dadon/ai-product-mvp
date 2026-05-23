# WORKFLOW DEFINITION

# Purpose

A workflow definition describes what the automation should do.

It must be:
- readable
- versioned
- executable by the engine
- safe to validate before running

---

# Initial Workflow Structure

```json
{
  "name": "Example Workflow",
  "trigger": {
    "type": "webhook",
    "config": {
      "path": "/webhooks/example"
    }
  },
  "steps": [
    {
      "id": "step_1",
      "type": "condition",
      "name": "Check status",
      "config": {
        "field": "status",
        "operator": "equals",
        "value": "approved"
      },
      "next": {
        "true": "step_2",
        "false": "step_3"
      }
    },
    {
      "id": "step_2",
      "type": "http_request",
      "name": "Call external API",
      "config": {
        "method": "POST",
        "url": "https://example.com/api",
        "body": {
          "message": "{{trigger.body.message}}"
        }
      },
      "retry": {
        "max_attempts": 3,
        "backoff_seconds": 10
      }
    }
  ]
}
