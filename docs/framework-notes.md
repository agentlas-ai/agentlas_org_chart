# Framework Notes

These notes ground the research in current public framework documentation. They
are not exhaustive and should be rechecked before publishing benchmark claims.

## CrewAI

CrewAI supports sequential and hierarchical processes. Its hierarchical process
uses a manager agent or manager LLM to coordinate workflow, delegate tasks, and
validate outcomes.

Implication for Agentlas Org Chart: CrewAI already has a native hook for the
top half of the org chart. The research opportunity is to add stricter role
contracts below the manager: who can reopen work, how revisions are bounded,
and what structured evidence workers must return.

Sources:

- https://docs.crewai.com/en/learn/hierarchical-process
- https://docs.crewai.com/en/concepts/processes
- https://docs.crewai.com/en/learn/sequential-process

## LangChain and LangGraph

LangChain documents several multi-agent patterns: subagents, handoffs, skills,
router, and custom workflows. The subagents pattern uses a central main agent
or supervisor that calls subagents as tools. LangGraph supplies the lower-level
stateful orchestration runtime for durable, long-running workflows.

LangGraph also documents `GRAPH_RECURSION_LIMIT`, where a graph reaches a
maximum step count before hitting a stop condition. The docs explicitly connect
this to likely cycles or infinite loops when many iterations were not expected.

Implication for Agentlas Org Chart: LangGraph is flexible enough to represent
flat, cyclic, or hierarchical systems. The org chart should be encoded as graph
topology plus state contracts: only managers route downward, workers return
upward, and every cycle has a typed exit condition.

Sources:

- https://docs.langchain.com/oss/python/langchain/multi-agent/index
- https://docs.langchain.com/oss/python/langchain/multi-agent/subagents
- https://docs.langchain.com/oss/python/langgraph
- https://docs.langchain.com/oss/python/langgraph/GRAPH_RECURSION_LIMIT

## OpenAI Agents SDK

The OpenAI Agents SDK documents multi-agent orchestration with agents as tools,
manager-style orchestration, and handoffs. Handoffs let one agent delegate part
of a conversation to another specialist agent.

Implication for Agentlas Org Chart: use manager-style orchestration for
accountability and use handoffs only when a specialist should truly take over
the user interaction. Peer handoffs are useful, but they need owner-level stop
rules.

Sources:

- https://openai.github.io/openai-agents-python/multi_agent/
- https://openai.github.io/openai-agents-js/guides/handoffs/

## Anthropic Multi-Agent Research System

Anthropic describes a production research feature using an
orchestrator-worker pattern: a lead agent plans, spawns specialized subagents
in parallel, and synthesizes their findings.

Implication for Agentlas Org Chart: strong multi-agent systems in production
often look less like peer chat and more like workstream decomposition under a
lead owner.

Source:

- https://www.anthropic.com/engineering/multi-agent-research-system

## AutoGen

AutoGen's group chat reference describes a `GroupChatManager` that mediates
messages in a group-chat style agent setup.

Implication for Agentlas Org Chart: a manager object is not enough by itself.
The manager needs explicit authority, budget, termination, and escalation
policy; otherwise it may only moderate a flat room.

Source:

- https://autogenhub.github.io/autogen/docs/reference/agentchat/groupchat/

## Working Synthesis

The frameworks are not the enemy. They already provide useful primitives. The
research target is the missing organizational contract across those primitives:

- Authority: who may decide?
- Delegation: who may assign work?
- Reporting: where does output return?
- Memory: who owns durable state?
- Revision: how many attempts are allowed?
- Stop: who can declare done, blocked, or escalated?
