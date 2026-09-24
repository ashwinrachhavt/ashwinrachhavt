# A session is not a connection

A network connection is a channel over which bytes move. A protocol session is a relationship spanning interactions. Authentication establishes an identity. Application state records the work being done. These ideas can overlap in an implementation, but they solve different problems.

Consider an assistant reviewing an invoice. It may need an authenticated user, a document ID, and a review record. It does not follow that it also needs a particular server process to remember an earlier handshake before it can inspect that document.

```text
Connection:       How does this request reach the service?
Authentication:   Who is making it?
Authorization:    What may they do right now?
Application state: Which document or review are they working on?
```

The useful design question is not “can we remove all state?” It is “which state does this request depend on, and who owns it?”

## Source and context

- Record: `publication-3b92e262-08a5-8186-942c-ff5559fe4f68-a-session-is-not-a-connection`
- Kind: `note`
- Topics: [Agents & trust](concept-agents.md), [Reliable infrastructure](concept-infrastructure.md), [Product thinking](concept-product.md)
- Source: [MCP Is Moving Beyond Sessions. Here’s Why That Matters.](https://github.com/ashwinrachhavt/AR-Portfolio/blob/e4530a35d356b690ea1c7ecfb544376797569302/src/content/writing/mcp-sessions.md)
- Passage: A session is not a connection
- Source revision: `09b0274dfe4f3edc`
- Record updated: 2026-09-22

## Connections

- `part-of` → [MCP Is Moving Beyond Sessions. Here’s Why That Matters.](publication-3b92e262-08a5-8186-942c-ff5559fe4f68.md)
- `about` → [Agents & trust](concept-agents.md)
- `about` → [Reliable infrastructure](concept-infrastructure.md)
- `about` → [Product thinking](concept-product.md)

[Browse the collection](../README.md) · [Agent reading guide](../for-agents.md)
