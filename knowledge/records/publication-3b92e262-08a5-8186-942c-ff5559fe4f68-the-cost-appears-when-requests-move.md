# The cost appears when requests move

Here is a hypothetical deployment with two workers:

```text
Initialization -> worker A -> context in A's memory
Next tool call -> worker B -> no matching local context
```

Sticky routing can keep a client on worker A. Shared storage can make the context available to both workers. Both approaches may be appropriate. Each also creates something to reason about during scaling, restarts, and incident recovery.

The point is not that sessions make production impossible. They add a dependency that is easy to overlook when a local demo has only one process.

Now change the request boundary:

```text
Request -> authenticated identity + required protocol context
        -> durable document/review identifiers
        -> any eligible worker
        -> current permission check
```

The service still has state. Its dependencies are easier to see, test, and recover independently.

## Source and context

- Record: `publication-3b92e262-08a5-8186-942c-ff5559fe4f68-the-cost-appears-when-requests-move`
- Kind: `note`
- Topics: [Agents & trust](concept-agents.md), [Reliable infrastructure](concept-infrastructure.md), [Product thinking](concept-product.md)
- Source: [MCP Is Moving Beyond Sessions. Here’s Why That Matters.](https://github.com/ashwinrachhavt/AR-Portfolio/blob/e4530a35d356b690ea1c7ecfb544376797569302/src/content/writing/mcp-sessions.md)
- Passage: The cost appears when requests move
- Source revision: `09b0274dfe4f3edc`
- Record updated: 2026-09-22

## Connections

- `part-of` → [MCP Is Moving Beyond Sessions. Here’s Why That Matters.](publication-3b92e262-08a5-8186-942c-ff5559fe4f68.md)
- `about` → [Agents & trust](concept-agents.md)
- `about` → [Reliable infrastructure](concept-infrastructure.md)
- `about` → [Product thinking](concept-product.md)

[Browse the collection](../README.md) · [Agent reading guide](../for-agents.md)
