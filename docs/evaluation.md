# Evaluation Plan

The research claim should be tested with comparable workflows, not asserted
from analogy alone.

## Main Metric

Loop reduction:

```text
loop_rate = repeated_agent_transition_count / total_agent_transition_count
```

A repeated transition is a transition that returns to the same agent pair or
same tool call without adding new accepted evidence.

## Secondary Metrics

| Metric | Why it matters |
|---|---|
| Completion rate | Did the workflow finish with an accepted artifact? |
| Human intervention count | Did a human need to rescue the run? |
| Tool-call count | Did hierarchy reduce redundant tool use? |
| Revision count | Did QA improve output without infinite polish? |
| Escalation count | Did ambiguity surface clearly? |
| Evidence acceptance rate | Did workers return verifiable material? |
| Final answer quality | Did loop control harm substance? |
| Wall-clock time | Did manager overhead slow the run too much? |
| Token or cost estimate | Did extra management pay for itself? |

## Baseline Experiment

Run the same task through two architectures:

1. Flat peer network: agents can hand off to each other freely.
2. Agentlas Org Chart: workers report upward and cannot call peers directly.

Suggested task:

```text
Research a new AI framework, compare it to two alternatives, produce a short
technical recommendation, verify claims with sources, and write a publishable
summary.
```

## Instrumentation

Record:

- agent transitions;
- tool calls;
- repeated transitions;
- state changes;
- accepted evidence references;
- rejections;
- escalations;
- final status;
- total cost estimate.

## Pass Criteria

Agentlas Org Chart is promising if it:

- reduces repeated transitions by at least 30%;
- does not reduce final quality below the flat-network baseline;
- makes blockers visible earlier;
- keeps total cost equal or lower on ambiguous tasks;
- produces clearer final ownership and evidence trails.

## Failure Criteria

The model needs revision if it:

- centralizes too much work in one manager;
- increases wall-clock time without reducing loops;
- blocks useful creative iteration too early;
- produces shallow worker outputs because context is too restricted;
- hides uncertainty behind manager summaries.

## Next Implementation Step

Build a minimal LangGraph version with:

- one supervisor node;
- two workstream manager nodes;
- two worker nodes;
- one QA node;
- explicit `accept`, `revise`, `blocked`, and `escalate` edges;
- counters in graph state for tool retry, QA rejection, and workstream revision.
