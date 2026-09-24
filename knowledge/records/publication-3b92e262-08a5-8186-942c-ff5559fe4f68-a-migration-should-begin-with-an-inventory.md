# A migration should begin with an inventory

Before removing session-dependent code, list what it currently stores. Separate protocol negotiation from user identity, authorization, pending work, and caches. If you cannot explain where a value will live afterward, the migration is not ready.

Then test the failure paths:

1. Send the next request to a different worker.
2. Restart a worker between proposal and execution.
3. Revoke access while an operation is pending.
4. Retry after the client times out without knowing whether a write succeeded.
5. Connect a client that implements an older protocol revision.

Write down the expected result before running each test. “The second request returned 200” is weaker evidence than “the permitted operation completed once, and the revoked operation did not execute.”

## Source and context

- Record: `publication-3b92e262-08a5-8186-942c-ff5559fe4f68-a-migration-should-begin-with-an-inventory`
- Kind: `note`
- Topics: [Agents & trust](concept-agents.md), [Reliable infrastructure](concept-infrastructure.md), [Product thinking](concept-product.md)
- Source: [MCP Is Moving Beyond Sessions. Here’s Why That Matters.](https://github.com/ashwinrachhavt/AR-Portfolio/blob/e4530a35d356b690ea1c7ecfb544376797569302/src/content/writing/mcp-sessions.md)
- Passage: A migration should begin with an inventory
- Source revision: `09b0274dfe4f3edc`
- Record updated: 2026-09-22

## Connections

- `part-of` → [MCP Is Moving Beyond Sessions. Here’s Why That Matters.](publication-3b92e262-08a5-8186-942c-ff5559fe4f68.md)
- `about` → [Agents & trust](concept-agents.md)
- `about` → [Reliable infrastructure](concept-infrastructure.md)
- `about` → [Product thinking](concept-product.md)

[Browse the collection](../README.md) · [Agent reading guide](../for-agents.md)
