# Knowledge from work, writing, and reading

A collection of useful ideas, project experience, and references from Ashwin Rachha. Follow a topic, read a note, and inspect its sources. Each record is available as ordinary Markdown and in the [structured catalog](public.json).

Reviewed September 23, 2026. This edition contains **51 public records**: six topics, seven projects, fourteen experience records, six reading takeaways, three publication records, fourteen essay passages, and one external reference. The reading takeaways are selected paraphrases from the 12-Factor Agents section of the public Notion *AI Engineering* notes, attributed to Dex Horthy / HumanLayer. This is a curated selection, not a complete Notion export.

## Start with a question

| If you are exploring… | Start here |
| --- | --- |
| How should an agent handle permissions? | [A tool call is a proposal](records/note-tools-structured-actions.md), [permissions in Lois](records/experience-loan-labs-permissions.md) |
| Where should workflow state live? | [Recoverable state](records/note-recoverable-state.md), [state still needs an owner](records/publication-3b92e262-08a5-8186-942c-ff5559fe4f68-state-still-needs-an-owner.md) |
| What makes retrieval useful in a product? | [Context ownership](records/note-own-context.md), [Classify AI](records/project-classify-ai.md) |
| How do banking workflows connect? | [Bank Connections](records/project-bank-connections.md), [Cash Underwriting](records/project-cash-underwriting.md) |
| How can AI support learning and access? | [Gurukul](records/project-gurukul.md), [UNAR Labs](records/project-unar-labs.md) |
| How can an agent read or reuse this collection? | [Agent reading guide](for-agents.md), [catalog](public.json) |

## Topics

- [Agents & trust](records/concept-agents.md) — Design agents around explicit identity, permissions, and recoverable work.
- [Financial systems](records/concept-fintech.md) — Trace financial workflows from ingestion to reviewed decisions.
- [Reliable infrastructure](records/concept-infrastructure.md) — Make system boundaries and failure behavior understandable.
- [Learning & access](records/concept-learning.md) — Use technology to help people understand and participate.
- [Product thinking](records/concept-product.md) — Connect system behavior to a useful human experience.
- [Retrieval & context](records/concept-retrieval.md) — Find relevant evidence before deciding what to do.

## Projects

- [Bank Connections](records/project-bank-connections.md) — Reusable Plaid and Teller infrastructure for account linking, secure token lifecycles, webhooks, and transaction synchronization.
- [Cash Underwriting](records/project-cash-underwriting.md) — Cash-based underwriting using 90-day bank data, reconstructed daily balances, and reviewable decision history.
- [Classify AI](records/project-classify-ai.md) — Transaction classification that combines transaction history, merchant enrichment, and custom charts of accounts.
- [Gurukul](records/project-gurukul.md) — Built an adaptive learning environment using RAG and guardrails; research at IEEE FIE 2024 and IEEE SouthEastCon 2023.
- [Lois](records/project-lois.md) — Mortgage-document classification, lender-specific renaming, and policy validation through a permission-aware agent in LoanOS.
- [Outreach Template Project](records/project-outreach-template-project.md) — Reusable NLP inference and deployment infrastructure using model-serving tools, Go/Python microservices, and GKE.
- [UNAR Labs](records/project-unar-labs.md) — Accessibility-focused backend and data pipelines for visually impaired users, deployed on GCP with Docker.

## Reading notes

- [Prefer focused agents with bounded responsibilities](records/note-focused-agents.md) — A small agent is easier to inspect than a universal assistant.
- [Own the context you give an agent](records/note-own-context.md) — An agent can only reason over the context it receives.
- [Keep the control flow inspectable](records/note-own-control-flow.md) — Pauses, retries, and human review belong in the application design.
- [Version prompts like other application code](records/note-prompt-ownership.md) — Prompt changes deserve tests and an inspectable history.
- [Give resumable work an explicit state](records/note-recoverable-state.md) — A paused task needs enough information to resume and explain itself.
- [A tool call is a proposal for deterministic code](records/note-tools-structured-actions.md) — Separate model output from permission to execute it.

## Writing

- [MCP Is Moving Beyond Sessions. Here’s Why That Matters.](records/publication-3b92e262-08a5-8186-942c-ff5559fe4f68.md) — Where protocol state belongs, why request boundaries matter, and what to check before migrating an MCP server.
- [Inside Buzz: How One Signed Message Becomes Work by an AI Agent](records/publication-3bb2e262-08a5-80aa-b865-e905d51fa752.md) — Follow a message through identity, permissions, an ACP bridge, and agent tools. What Buzz teaches us about building products where people and agents work together.
- [AI Engineering](records/publication-ai-engineering.md) — A collection of reading notes on context, tools, control flow, and focused agents.

## Essay passages

- [A migration should begin with an inventory](records/publication-3b92e262-08a5-8186-942c-ff5559fe4f68-a-migration-should-begin-with-an-inventory.md)
- [A session is not a connection](records/publication-3b92e262-08a5-8186-942c-ff5559fe4f68-a-session-is-not-a-connection.md)
- [State still needs an owner](records/publication-3b92e262-08a5-8186-942c-ff5559fe4f68-state-still-needs-an-owner.md)
- [The cost appears when requests move](records/publication-3b92e262-08a5-8186-942c-ff5559fe4f68-the-cost-appears-when-requests-move.md)
- [The product lesson](records/publication-3b92e262-08a5-8186-942c-ff5559fe4f68-the-product-lesson.md)
- [What I like about the draft direction](records/publication-3b92e262-08a5-8186-942c-ff5559fe4f68-what-i-like-about-the-draft-direction.md)
- [What the earlier HTTP design allowed](records/publication-3b92e262-08a5-8186-942c-ff5559fe4f68-what-the-earlier-http-design-allowed.md)
- [Follow one request](records/publication-3bb2e262-08a5-80aa-b865-e905d51fa752-follow-one-request.md)
- [Start with the relay](records/publication-3bb2e262-08a5-80aa-b865-e905d51fa752-start-with-the-relay.md)
- [The bridge has a real job](records/publication-3bb2e262-08a5-80aa-b865-e905d51fa752-the-bridge-has-a-real-job.md)
- [Three things a signature cannot tell you](records/publication-3bb2e262-08a5-80aa-b865-e905d51fa752-three-things-a-signature-cannot-tell-you.md)
- [What happens when something breaks?](records/publication-3bb2e262-08a5-80aa-b865-e905d51fa752-what-happens-when-something-breaks.md)
- [What I take from Buzz](records/publication-3bb2e262-08a5-80aa-b865-e905d51fa752-what-i-take-from-buzz.md)
- [Why the interface matters as much as the architecture](records/publication-3bb2e262-08a5-80aa-b865-e905d51fa752-why-the-interface-matters-as-much-as-the-architecture.md)

## Experience

- [Finally · banking](records/experience-finally-banking.md) — Architected reusable Plaid/Teller infrastructure for account linking, encrypted token storage, token lifecycle management, webhooks, transaction synchronization, and normalized account data.
- [Finally · classify](records/experience-finally-classify.md) — Joined as the first AI Product Engineer and led a three-engineer team from prototype to production on Classify AI; processed 50K+ transactions daily and reduced manual categorization by approximately 80%.
- [Finally · close](records/experience-finally-close.md) — Evolved bookkeeping from CSV upload to Plaid/Teller bank ingestion, OCR-supported statements, reconciliation, and QuickBooks push; helped reduce first-month close from 4+ months to approximately 2 weeks.
- [Finally · retrieval](records/experience-finally-retrieval.md) — Built retrieval-augmented classification with LangChain, Pinecone, Elasticsearch, Redis, Celery, and Django, combining transaction history, merchant enrichment, and custom charts of accounts.
- [Finally · underwriting](records/experience-finally-underwriting.md) — Built cash-based underwriting with 90-day bank data, daily-balance reconstruction, weekly recalculation, audit history, and manual overrides; supported $3M+ in credit for 50+ companies in approximately three months.
- [Virginia Tech · description](records/experience-gurukul-description.md) — Built an adaptive learning environment using RAG and guardrails; research at IEEE FIE 2024 and IEEE SouthEastCon 2023.
- [Loan Labs · architecture](records/experience-loan-labs-architecture.md) — Re-architected Lois from one-off Ruby LLM calls into a LangGraph agentic system on Amazon Bedrock AgentCore for mortgage-document classification, lender-specific renaming, and policy validation.
- [Loan Labs · integrations](records/experience-loan-labs-integrations.md) — Connected CRM and document workflows across Google Drive, Box, Salesforce, HubSpot, Pipedrive, OneDrive, and SharePoint with fine-grained access controls and blocked delete actions.
- [Loan Labs · leadership](records/experience-loan-labs-leadership.md) — Introduced an AI-assisted software delivery workflow linking Linear/Notion product context, technical specifications, shared company knowledge, and senior-engineer code review.
- [Loan Labs · permissions](records/experience-loan-labs-permissions.md) — Designed fail-closed authorization for Composio integrations: tenant/owner scoping, separate write/send/merge/archive permissions, reviewed tool allowlists, and execution-time checks that invalidate revoked access.
- [Loan Labs · surfaces](records/experience-loan-labs-surfaces.md) — Built agent-facing Rails APIs, borrower email intake, and an in-product conversational interface so users could handle loan documents and initiate agent actions in LoanOS.
- [Mindbowser Inc · vision](records/experience-mindbowser-vision.md) — Developed a facial-expression recognition system for CRM meeting analysis using VGG-19 transfer learning and MongoDB GridFS.
- [Outreach · platform](records/experience-outreach-platform.md) — Built reusable NLP inference and deployment infrastructure using PySpark, MLflow, ONNX, NVIDIA Triton, Go/Python microservices, Docker, CI/CD, and GKE.
- [UNAR Labs · accessibility](records/experience-unar-accessibility.md) — Built accessibility-focused backend and data pipelines for visually impaired users with OpenCV, PyTorch, Transformers, and FastAPI; deployed on GCP with Docker.

## References

- [12-Factor Agents · HumanLayer](records/reference-12-factor-agents.md) — A reference collected in Ashwin’s AI Engineering notes.

## Evidence and updates

Career evidence is derived from the [approved résumé](https://github.com/ashwinrachhavt/AR-Portfolio/blob/e4530a35d356b690ea1c7ecfb544376797569302/src/content/resume.json), dated September 20, 2026. Every experience record retains its exact field locator; project records link to the evidence they summarize. Metrics describe the documented scope and team or system outcomes, not independent verification of employer data.

Essay passages retain their article heading and source revision. Reading summaries remain attributed to their original authors. Topic descriptions are an editorial map, not evidence that two claims support one another. Dates and qualifications travel with the text so a historical statement does not become an unqualified current claim.

To update a record, compare its source revision, review the public wording, preserve its stable ID, and update both its Markdown file and `public.json`. Confirm that every relationship still resolves and that the source supports the claim. Add new notes deliberately; do not import an entire private workspace. The catalog revision is the first 16 characters of the SHA-256 of its `records` array serialized as UTF-8 JSON with sorted keys, no extra whitespace, and unescaped Unicode.

This repository publishes text and metadata. It does not deploy the website, expose a search API, or run an Eve service. The website redesign was reverted; these notes remain independently readable and reusable.

## Research on organizing and reusing knowledge

- [Knowledge organization for people and agents](../docs/research/knowledge-organization-for-agents.md)
- [Agent-assisted interactive writing](../docs/research/interactive-blog-authoring.md)

These dated research memos describe possible future approaches. They are not claims that the proposed website features are live.
