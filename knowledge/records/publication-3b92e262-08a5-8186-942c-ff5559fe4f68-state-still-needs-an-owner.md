# State still needs an owner

Suppose a tool proposes changing an invoice category, then waits for a human to approve it. Removing protocol sessions does not eliminate the proposed change, approval status, or permission checks.

I would make those explicit application records:

| State | A useful owner | A question to test |
| --- | --- | --- |
| User identity | Authentication layer | Is this identity still valid? |
| Resource access | Authorization layer | Can this user act on this invoice now? |
| Proposed change | Durable application record | Which exact change is being approved? |
| Long-running work | Job/task record | Can a different worker resume or report it? |
| Duplicate submission | Application operation key | Will a retry repeat the side effect? |

These are design suggestions, not fields imposed by MCP. The important property is that approval refers to a specific action, and execution checks current authority. A remembered conversation should not grant permission forever.

## Source and context

- Record: `publication-3b92e262-08a5-8186-942c-ff5559fe4f68-state-still-needs-an-owner`
- Kind: `note`
- Topics: [Agents & trust](concept-agents.md), [Reliable infrastructure](concept-infrastructure.md), [Product thinking](concept-product.md)
- Source: [MCP Is Moving Beyond Sessions. Here’s Why That Matters.](https://github.com/ashwinrachhavt/AR-Portfolio/blob/e4530a35d356b690ea1c7ecfb544376797569302/src/content/writing/mcp-sessions.md)
- Passage: State still needs an owner
- Source revision: `09b0274dfe4f3edc`
- Record updated: 2026-09-22

## Connections

- `part-of` → [MCP Is Moving Beyond Sessions. Here’s Why That Matters.](publication-3b92e262-08a5-8186-942c-ff5559fe4f68.md)
- `about` → [Agents & trust](concept-agents.md)
- `about` → [Reliable infrastructure](concept-infrastructure.md)
- `about` → [Product thinking](concept-product.md)

[Browse the collection](../README.md) · [Agent reading guide](../for-agents.md)
