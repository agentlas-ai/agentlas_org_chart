# Research Log

## 2026-05-24: Initial Question

Claim type: hypothesis

### Claim

Peer-first multi-agent systems are prone to loops when no layer has explicit
authority to stop, escalate, or accept work. A hierarchy-first org chart may
reduce this risk by making delegation asymmetric and by giving each layer a
bounded revision budget.

### Evidence

- CrewAI documents a hierarchical process where a manager coordinates task
  delegation and validates outcomes.
- LangChain documents supervisor and subagent patterns where a main agent
  coordinates subagents and maintains context.
- LangGraph documents recursion-limit errors as often caused by cycles that do
  not hit a stop condition.
- OpenAI Agents SDK documents both manager-style orchestration and handoffs.
- Anthropic describes a production research system with an orchestrator-worker
  architecture.

### Interpretation

Frameworks already support hierarchy, but hierarchy is often treated as an
implementation option rather than an operating contract. The research should
focus on authority, reporting lines, budgets, memory ownership, and typed
worker returns.

### Next Experiment

Implement the same research-and-write workflow in two shapes:

1. Peer handoff graph.
2. Agentlas Org Chart hierarchy.

Compare completion rate, repeated handoff count, tool-call count, recursion or
iteration-limit hits, final answer quality, and human intervention count.
