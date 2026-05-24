# Org Chart Contract Template

Use this template before implementing a multi-agent workflow.

## Mission

- Goal:
- Final artifact:
- User-facing success criteria:
- Global stop condition:
- Global budget:

## Org Chart

```text
Mission Owner:
  Strategy Office:
  Workstream Manager:
    Team Lead:
      Specialist Worker:
    QA / Evidence Office:
  Risk / Policy Office:
  Final Synthesis Office:
```

## Role Contracts

### Mission Owner

- Authority:
- Memory:
- Inputs:
- Outputs:
- Stop rules:

### Strategy Office

- Authority:
- Memory:
- Inputs:
- Outputs:
- Stop rules:

### Workstream Manager

- Authority:
- Memory:
- Inputs:
- Outputs:
- Stop rules:

### Team Lead

- Authority:
- Memory:
- Inputs:
- Outputs:
- Stop rules:

### Specialist Worker

- Authority:
- Memory:
- Inputs:
- Outputs:
- Stop rules:

### QA / Evidence Office

- Authority:
- Memory:
- Inputs:
- Outputs:
- Stop rules:

## Worker Return Schema

```yaml
task_id:
role:
status: done | needs_revision | blocked | escalate
summary:
output:
evidence:
  - type:
    reference:
risk:
  level:
  note:
next_action: accept | revise | escalate | stop
budget_used:
  turns:
  tool_calls:
  cost_estimate:
```

## Loop Guards

- Max worker attempts:
- Max tool retries per worker:
- Max QA rejections:
- Max manager replans:
- Escalation trigger:
- Human approval trigger:
