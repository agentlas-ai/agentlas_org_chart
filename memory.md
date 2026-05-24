# Agentlas Org Chart Memory

This is public memory for `agentlas_org_chart`.

## Stable Facts

- Agent name: Agentlas Org Chart
- Agent slug: org_chart
- Repository name: agentlas_org_chart
- Public site: `https://agentlas.cloud`
- Core research object: hierarchy-first multi-agent organization design.

## Current Hypothesis

Multi-agent infinite loops often appear when the system lacks explicit
authority, reporting lines, revision budgets, and termination ownership. A
vertical org chart can reduce loop risk by making delegation and escalation
asymmetric.

## Design Decisions

### 2026-05-24: Use `agentlas_org_chart` as the repo name

- The research folder follows the requested `agentlas_xxx` naming shape.
- The repo remains under `output/` as an independent public output repository.
- Avoid generic starter-template wording for the final research artifact.

### 2026-05-24: Frame culture as inspiration, not evidence

- Korean large-company hierarchy is a useful design analogy for reporting lines,
  approval gates, and escalation paths.
- The technical claim must be evaluated through loop metrics, not national or
  cultural essentialism.

### 2026-05-24: Hierarchy means authority plus stop rules

- A role name alone does not prevent loops.
- Every management layer needs explicit authority, budget, state ownership, and
  escalation behavior.

## Open Questions

- How much hierarchy is enough before manager bottlenecks dominate?
- Which work types benefit from peer handoffs despite higher loop risk?
- Can deterministic state machines enforce org chart rules while preserving
  useful agent autonomy?
- What metrics best separate "healthy iteration" from "looping"?
