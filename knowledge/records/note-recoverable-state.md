# Give resumable work an explicit state

A paused task needs enough information to resume and explain itself.

The notes discuss serializable execution context and simple launch, pause, and resume interfaces. For a real workflow, identify what must survive a process restart and what cannot safely be reconstructed from conversation alone.

## Source and context

- Record: `note-recoverable-state`
- Kind: `note`
- Topics: [Agents & trust](concept-agents.md), [Reliable infrastructure](concept-infrastructure.md)
- Source: [AI Engineering — reading notes](https://ashwinrachha.vercel.app/blog/2572e262-08a5-8067-9928-ed6aba063cf5)
- Passage: Unify Execution State
- Source revision: `2025-11-06`
- Record updated: 2026-09-23

## Connections

- `derived-from` → [AI Engineering](publication-ai-engineering.md)
- `references` → [12-Factor Agents · HumanLayer](reference-12-factor-agents.md)
- `about` → [Agents & trust](concept-agents.md)
- `about` → [Reliable infrastructure](concept-infrastructure.md)

[Browse the collection](../README.md) · [Agent reading guide](../for-agents.md)
