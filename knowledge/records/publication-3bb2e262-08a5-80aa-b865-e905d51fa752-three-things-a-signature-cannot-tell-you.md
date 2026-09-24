# Three things a signature cannot tell you

The [Nostr event format](https://github.com/nostr-protocol/nips/blob/master/01.md) includes an event identifier, public key, timestamp, kind, tags, content, and signature. That structure makes attribution and integrity inspectable. It does not make every downstream statement true.

For a product built around agent work, I would keep three distinctions visible:

| Question | Why it matters |
| --- | --- |
| Is the event authentic? | A changed or forged message must not borrow someone’s identity. |
| Is the action authorized? | A legitimate member can still lack access to a channel, repository, or operation. |
| Did the work actually complete? | An accepted request can outlive a failed worker or a denied tool call. |

These are my design criteria for evaluating such a system. They are not a claim that the current UI exposes every state exactly this way.

## Source and context

- Record: `publication-3bb2e262-08a5-80aa-b865-e905d51fa752-three-things-a-signature-cannot-tell-you`
- Kind: `note`
- Topics: [Agents & trust](concept-agents.md), [Reliable infrastructure](concept-infrastructure.md), [Product thinking](concept-product.md)
- Source: [Inside Buzz: How One Signed Message Becomes Work by an AI Agent](https://github.com/ashwinrachhavt/AR-Portfolio/blob/e4530a35d356b690ea1c7ecfb544376797569302/src/content/writing/inside-buzz.md)
- Passage: Three things a signature cannot tell you
- Source revision: `00a7ed0a648cd004`
- Record updated: 2026-09-22

## Connections

- `part-of` → [Inside Buzz: How One Signed Message Becomes Work by an AI Agent](publication-3bb2e262-08a5-80aa-b865-e905d51fa752.md)
- `about` → [Agents & trust](concept-agents.md)
- `about` → [Reliable infrastructure](concept-infrastructure.md)
- `about` → [Product thinking](concept-product.md)

[Browse the collection](../README.md) · [Agent reading guide](../for-agents.md)
