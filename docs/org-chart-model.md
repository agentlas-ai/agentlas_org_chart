# Org Chart Model

Agentlas Org Chart is a coordination model for multi-agent systems. It treats
agents as an organization with authority and reporting lines rather than a set
of equal peers.

## Problem

Flat or peer-first networks can be useful when agents need to collaborate
freely. They are risky when the task is ambiguous, the state is shared, or
several agents can ask each other for more work without a single owner deciding
that the job is finished.

The typical symptom is not dramatic failure. It is slow drift:

- repeated handoffs;
- repeated tool calls with weak new evidence;
- reviewers asking for more polish without acceptance criteria;
- state changing faster than any agent can summarize it;
- final answer delayed because no agent owns closure.

## Core Pattern

```text
Mission Owner
  owns: goal, constraints, final stop condition

Strategy Office
  owns: decomposition, acceptance criteria, routing plan

Workstream Manager
  owns: domain state, blockers, revision budget, evidence merge

Team Lead
  owns: bounded worker task, local task plan, worker acceptance

Specialist Worker
  owns: one focused execution task

QA / Evidence Office
  owns: verification, contradictions, citation/test quality

Risk / Policy Office
  owns: privacy, secrets, security, cost, human approval

Final Synthesis Office
  owns: final artifact after workstream acceptance
```

## Authority Rules

### Mission Owner

- May redefine scope.
- May extend the global budget.
- May accept final output.
- May stop or escalate the run.

### Strategy Office

- May split work into workstreams.
- May define acceptance criteria.
- May recommend which managers are needed.
- May not perform specialist execution.

### Workstream Manager

- May delegate to team leads.
- May accept or reject team output.
- May escalate unresolved ambiguity.
- May not create new mission scope.

### Team Lead

- May assign bounded tasks to workers.
- May perform local synthesis.
- Must return to the manager after each worker attempt.
- May not call unrelated teams directly.

### Specialist Worker

- May use approved tools for a bounded task.
- Must return structured output.
- Must declare blocked after retry budget is exhausted.
- May not hand off to another worker.

### QA / Evidence Office

- May verify, reject, or request one revision.
- Must cite concrete acceptance gaps.
- Must escalate after repeated rejection.
- May not create infinite polish cycles.

## State Model

Each workstream should maintain a compact state object:

```yaml
workstream_id: string
owner: string
goal: string
status: open | done | blocked | escalated
accepted_outputs:
  - id: string
    summary: string
    evidence_refs:
      - string
open_questions:
  - question: string
    owner: string
    due: string
budgets:
  max_worker_attempts: 2
  max_qa_rejections: 1
  max_tool_retries_per_worker: 2
```

## Loop-Control Rules

- No unapproved lateral worker handoffs.
- No worker gets full project memory by default.
- Every loop edge must have a counter.
- Every reject path must include a maximum.
- Every tool retry must record what changed.
- Every manager must choose one of: accept, revise, escalate, stop.
- Every unresolved contradiction moves upward.

## When To Use

Use this model when:

- the workflow has more than two specialist domains;
- tool cost matters;
- final output needs evidence and QA;
- previous runs showed repeated handoffs;
- the user wants a durable operating system for agent teams.

Do not use this model when:

- a single agent with tools is enough;
- the task is tiny;
- creativity benefits from loose peer exploration;
- all agents need direct user interaction;
- deterministic code can replace agent routing entirely.
