# The bridge has a real job

The [buzz-acp documentation](https://github.com/block/buzz/blob/main/crates/buzz-acp/README.md) describes a harness that listens for mentions and connects the relay to agents speaking the Agent Client Protocol over standard input and output. The agent interacts with the workspace through Buzz tools. Agent identities have their own keys and membership.

ACP is the interface between the harness and the agent process here. It is distinct from MCP, which concerns tools and context exposed to an AI application.

The product implication is interesting: the workspace can provide the collaboration setting while the agent runtime provides reasoning. Those responsibilities can evolve separately, provided their interface stays explicit.

## Source and context

- Record: `publication-3bb2e262-08a5-80aa-b865-e905d51fa752-the-bridge-has-a-real-job`
- Kind: `note`
- Topics: [Agents & trust](concept-agents.md), [Reliable infrastructure](concept-infrastructure.md), [Product thinking](concept-product.md)
- Source: [Inside Buzz: How One Signed Message Becomes Work by an AI Agent](https://github.com/ashwinrachhavt/AR-Portfolio/blob/e4530a35d356b690ea1c7ecfb544376797569302/src/content/writing/inside-buzz.md)
- Passage: The bridge has a real job
- Source revision: `00a7ed0a648cd004`
- Record updated: 2026-09-22

## Connections

- `part-of` → [Inside Buzz: How One Signed Message Becomes Work by an AI Agent](publication-3bb2e262-08a5-80aa-b865-e905d51fa752.md)
- `about` → [Agents & trust](concept-agents.md)
- `about` → [Reliable infrastructure](concept-infrastructure.md)
- `about` → [Product thinking](concept-product.md)

[Browse the collection](../README.md) · [Agent reading guide](../for-agents.md)
