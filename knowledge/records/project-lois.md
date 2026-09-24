# Lois

Mortgage-document classification, lender-specific renaming, and policy validation through a permission-aware agent in LoanOS.

Agentic mortgage workflows · Internal & pilot workflows

Bring document intake, agent actions, and lender policies into the same mortgage workflow.

Re-architected Lois from one-off Ruby LLM calls into a LangGraph agentic system on Amazon Bedrock AgentCore for mortgage-document classification, lender-specific renaming, and policy validation.

Built agent-facing Rails APIs, borrower email intake, and an in-product conversational interface so users could handle loan documents and initiate agent actions in LoanOS.

Designed fail-closed authorization for Composio integrations: tenant/owner scoping, separate write/send/merge/archive permissions, reviewed tool allowlists, and execution-time checks that invalidate revoked access.

Connected CRM and document workflows across Google Drive, Box, Salesforce, HubSpot, Pipedrive, OneDrive, and SharePoint with fine-grained access controls and blocked delete actions.

## Source and context

- Record: `project-lois`
- Kind: `project`
- Topics: [Agents & trust](concept-agents.md), [Reliable infrastructure](concept-infrastructure.md)
- Source: [Approved career facts · Lois](https://github.com/ashwinrachhavt/AR-Portfolio/blob/e4530a35d356b690ea1c7ecfb544376797569302/src/content/resume.json)
- Passage: See derived-from relations for exact résumé fields.
- Source revision: `2026-09-20`
- Record updated: 2026-09-20

Project summaries describe the approved scope of the work. Credit, throughput, and close-time figures describe the documented team or system outcomes.

## Connections

- `derived-from` → [Loan Labs · architecture](experience-loan-labs-architecture.md)
- `derived-from` → [Loan Labs · surfaces](experience-loan-labs-surfaces.md)
- `derived-from` → [Loan Labs · permissions](experience-loan-labs-permissions.md)
- `derived-from` → [Loan Labs · integrations](experience-loan-labs-integrations.md)
- `about` → [Agents & trust](concept-agents.md)
- `about` → [Reliable infrastructure](concept-infrastructure.md)

[Browse the collection](../README.md) · [Agent reading guide](../for-agents.md)
