# Start with the relay

The [project architecture](https://github.com/block/buzz/blob/main/ARCHITECTURE.md) describes the relay as the authority through which clients read and write. It handles authentication, signature verification, persistence, and distribution to subscribers. Community context matters too: a request must be resolved into the right workspace before it can operate there.

That makes a message more than text on a screen. It is an event attributed to an identity, interpreted inside an authority boundary.

The distinction I care about is simple: **a valid signature establishes who signed an event. It does not establish that the requested action is permitted, sensible, or complete.**

## Source and context

- Record: `publication-3bb2e262-08a5-80aa-b865-e905d51fa752-start-with-the-relay`
- Kind: `note`
- Topics: [Agents & trust](concept-agents.md), [Reliable infrastructure](concept-infrastructure.md), [Product thinking](concept-product.md)
- Source: [Inside Buzz: How One Signed Message Becomes Work by an AI Agent](https://github.com/ashwinrachhavt/AR-Portfolio/blob/e4530a35d356b690ea1c7ecfb544376797569302/src/content/writing/inside-buzz.md)
- Passage: Start with the relay
- Source revision: `00a7ed0a648cd004`
- Record updated: 2026-09-22

## Connections

- `part-of` → [Inside Buzz: How One Signed Message Becomes Work by an AI Agent](publication-3bb2e262-08a5-80aa-b865-e905d51fa752.md)
- `about` → [Agents & trust](concept-agents.md)
- `about` → [Reliable infrastructure](concept-infrastructure.md)
- `about` → [Product thinking](concept-product.md)

[Browse the collection](../README.md) · [Agent reading guide](../for-agents.md)
