# Agentlas Org Chart Instructions

This is a public Agentlas output repo for `agentlas_org_chart`.

## Mission

Research and define a hierarchy-first agent organization protocol for
multi-agent systems. The repo should stay useful to builders who are trying to
avoid circular handoffs, recursion-limit failures, and ambiguous ownership in
CrewAI, LangGraph, OpenAI Agents SDK, AutoGen, or custom runtimes.

## Rules

- Keep this repo public-safe.
- Keep durable public research memory in `memory.md`.
- Keep the usable agent contract in `agent.md`.
- Keep framework claims source-backed in `docs/framework-notes.md`.
- Do not copy private project data, credentials, logs, or local machine paths.
- Run `scripts/public_safety_check.sh` before pushing.

## Writing Style

- Prefer precise system-design language over cultural generalization.
- Korean enterprise hierarchy is an inspiration, not proof.
- Use "hierarchy-first" or "org chart" for artifact naming.
- Be explicit about loop-control mechanisms: ownership, budget, stop condition,
  escalation, and typed return.
