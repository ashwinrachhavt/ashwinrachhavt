# What I like about the draft direction

The current draft describes transport-independent message patterns and per-request context, and explains compatibility with earlier initialization-based revisions. I read that as a useful separation: transport moves messages; the application owns durable work.

My engineering preference is to make a tool request intelligible at its boundary. When I inspect a failure, I want to know what operation was requested, which identity requested it, what resource it addressed, and why it was accepted or denied.

That preference is not proof that one architecture is always faster. It is a claim about what becomes easier to inspect. Throughput, latency, and operating cost still need measurement on the actual workload.

## Source and context

- Record: `publication-3b92e262-08a5-8186-942c-ff5559fe4f68-what-i-like-about-the-draft-direction`
- Kind: `note`
- Topics: [Agents & trust](concept-agents.md), [Reliable infrastructure](concept-infrastructure.md), [Product thinking](concept-product.md)
- Source: [MCP Is Moving Beyond Sessions. Here’s Why That Matters.](https://github.com/ashwinrachhavt/AR-Portfolio/blob/e4530a35d356b690ea1c7ecfb544376797569302/src/content/writing/mcp-sessions.md)
- Passage: What I like about the draft direction
- Source revision: `09b0274dfe4f3edc`
- Record updated: 2026-09-22

## Connections

- `part-of` → [MCP Is Moving Beyond Sessions. Here’s Why That Matters.](publication-3b92e262-08a5-8186-942c-ff5559fe4f68.md)
- `about` → [Agents & trust](concept-agents.md)
- `about` → [Reliable infrastructure](concept-infrastructure.md)
- `about` → [Product thinking](concept-product.md)

[Browse the collection](../README.md) · [Agent reading guide](../for-agents.md)
