# What the earlier HTTP design allowed

Under the 2025-11-25 transport specification, a server can return an `MCP-Session-Id` during initialization. A client that receives it includes that ID on subsequent requests. If the session expires and the server returns the specified not-found response, the client initializes again.

That is a protocol mechanism. It does not require every deployment to store sessions in one worker's memory. A server can make different storage and routing choices. But once correct handling depends on recovering session context, those choices become part of operating the service.

## Source and context

- Record: `publication-3b92e262-08a5-8186-942c-ff5559fe4f68-what-the-earlier-http-design-allowed`
- Kind: `note`
- Topics: [Agents & trust](concept-agents.md), [Reliable infrastructure](concept-infrastructure.md), [Product thinking](concept-product.md)
- Source: [MCP Is Moving Beyond Sessions. Here’s Why That Matters.](https://github.com/ashwinrachhavt/AR-Portfolio/blob/e4530a35d356b690ea1c7ecfb544376797569302/src/content/writing/mcp-sessions.md)
- Passage: What the earlier HTTP design allowed
- Source revision: `09b0274dfe4f3edc`
- Record updated: 2026-09-22

## Connections

- `part-of` → [MCP Is Moving Beyond Sessions. Here’s Why That Matters.](publication-3b92e262-08a5-8186-942c-ff5559fe4f68.md)
- `about` → [Agents & trust](concept-agents.md)
- `about` → [Reliable infrastructure](concept-infrastructure.md)
- `about` → [Product thinking](concept-product.md)

[Browse the collection](../README.md) · [Agent reading guide](../for-agents.md)
