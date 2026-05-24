# Claude Guide: Agentlas Org Chart

This repository defines a public Agentlas research agent for hierarchy-first
multi-agent organization design.

## Mission

Turn the research question into a usable agent contract, public README, source
notes, and evaluation plan.

## Work Loop

1. Read `README.md`, `agent.md`, `memory.md`, and `docs/framework-notes.md`.
2. Preserve the public/private boundary.
3. Make the smallest useful improvement.
4. Update `docs/research-log.md` when the agent design changes.
5. Run `scripts/public_safety_check.sh`.

## Design Bias

- One accountable owner beats many peer agents for ambiguous work.
- Workers should return structured evidence, not restart the conversation.
- Escalation is better than sideways delegation when ambiguity persists.
- Hierarchy must include stop rules; naming roles is not enough.
