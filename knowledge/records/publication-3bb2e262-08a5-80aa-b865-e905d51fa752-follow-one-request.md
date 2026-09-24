# Follow one request

Imagine a teammate writes, “Review this patch and tell me what could fail.” This is a hypothetical walkthrough; it is not a transcript of a production run.

```text
Person writes a message
  -> signed event reaches the relay
  -> identity, workspace, and access checks
  -> accepted event becomes available to subscribers
  -> buzz-acp receives an eligible mention
  -> ACP prompt reaches an agent process
  -> agent reasons and uses permitted tools
  -> results return to the workspace
```

Each arrow is a place to ask a different question. Was the event accepted? Was it delivered? Did the worker start? Did its tool succeed? Did the person get a useful result?

Treating all of those as “the AI responded” makes failures difficult to diagnose.

## Source and context

- Record: `publication-3bb2e262-08a5-80aa-b865-e905d51fa752-follow-one-request`
- Kind: `note`
- Topics: [Agents & trust](concept-agents.md), [Reliable infrastructure](concept-infrastructure.md), [Product thinking](concept-product.md)
- Source: [Inside Buzz: How One Signed Message Becomes Work by an AI Agent](https://github.com/ashwinrachhavt/AR-Portfolio/blob/e4530a35d356b690ea1c7ecfb544376797569302/src/content/writing/inside-buzz.md)
- Passage: Follow one request
- Source revision: `00a7ed0a648cd004`
- Record updated: 2026-09-22

## Connections

- `part-of` → [Inside Buzz: How One Signed Message Becomes Work by an AI Agent](publication-3bb2e262-08a5-80aa-b865-e905d51fa752.md)
- `about` → [Agents & trust](concept-agents.md)
- `about` → [Reliable infrastructure](concept-infrastructure.md)
- `about` → [Product thinking](concept-product.md)

[Browse the collection](../README.md) · [Agent reading guide](../for-agents.md)
