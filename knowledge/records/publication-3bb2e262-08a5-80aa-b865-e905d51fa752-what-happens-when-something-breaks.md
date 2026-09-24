# What happens when something breaks?

Consider four failures in our hypothetical patch review.

**The message is modified after signing.** Verification should fail. The product should not turn that into an ordinary agent task.

**The author is real but lacks access.** Identity verification can succeed while authorization fails. “Authenticated” should never be treated as a synonym for “allowed.”

**The agent starts, then loses its process.** The person's request has not magically become a completed review. A useful experience needs a visible failure or recovery state, and retry behavior that does not accidentally duplicate consequential actions.

**A tool returns an error.** The agent should report what it could and could not inspect. A confident summary is not evidence that a repository was read or a test was run.

This is where I would spend time evaluating an agent workspace. A happy-path demo shows that the parts connect. Failure paths show whether people can trust the product while doing actual work.

## Source and context

- Record: `publication-3bb2e262-08a5-80aa-b865-e905d51fa752-what-happens-when-something-breaks`
- Kind: `note`
- Topics: [Agents & trust](concept-agents.md), [Reliable infrastructure](concept-infrastructure.md), [Product thinking](concept-product.md)
- Source: [Inside Buzz: How One Signed Message Becomes Work by an AI Agent](https://github.com/ashwinrachhavt/AR-Portfolio/blob/e4530a35d356b690ea1c7ecfb544376797569302/src/content/writing/inside-buzz.md)
- Passage: What happens when something breaks?
- Source revision: `00a7ed0a648cd004`
- Record updated: 2026-09-22

## Connections

- `part-of` → [Inside Buzz: How One Signed Message Becomes Work by an AI Agent](publication-3bb2e262-08a5-80aa-b865-e905d51fa752.md)
- `about` → [Agents & trust](concept-agents.md)
- `about` → [Reliable infrastructure](concept-infrastructure.md)
- `about` → [Product thinking](concept-product.md)

[Browse the collection](../README.md) · [Agent reading guide](../for-agents.md)
