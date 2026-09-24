# Knowledge organization for visitors and authoring agents

Research date: September 23, 2026.

**Status: archived design research, September 23, 2026.** The website implementation was subsequently reverted at the owner’s request. This repository preserves the [public knowledge text](../../knowledge/README.md); the search service, Eve integration, and interactive-blog proposals below are not current website features. References to local drafts or source line numbers describe the workspace inspected on that date.

## Recommendation

Organize the collection around identifiable concepts, reusable knowledge notes, original sources, and explicit relationships. Keep each note's evidence and qualifications attached. Produce a reviewed public edition that the website and publishing agents can both query. An interactive article becomes a presentation of that knowledge, and can contribute new reviewed explanations back into the collection.

For this project, the strongest starting combination is:

- Notion for capture and editorial work; reviewed Markdown and structured metadata for the public edition.
- A small typed graph for meaning, source attribution, and related reading.
- Hybrid retrieval, combining exact-term and semantic search, with bounded navigation through explicit relationships.
- A shared search/get/related contract, accessible locally to authoring agents and through the website's server interface. MCP can expose that same contract to compatible clients.
- Markdown articles with validated interactive blocks; reviewed repository code for bespoke experiences.

This is an engineering recommendation based on the inspected repositories and primary sources below. No retrieval benchmark on the full collection or reader-engagement experiment has been run. The full eligible corpus size is still unknown.

## What the research establishes

| Approach | Evidence and tradeoff | Fit here |
| --- | --- | --- |
| Concepts, aliases, hierarchy, and related concepts | W3C SKOS supplies these vocabulary-building primitives, including concepts with more than one broader concept. | Borrow the semantics for a small JSON model. Full RDF infrastructure is not required by this proposal. [SKOS](https://www.w3.org/TR/skos-primer/) |
| Explicit provenance | W3C PROV models entities, the processes that derive them, attribution, and revisions. | Track which source passage informed a note, article, or chart and which revision was used. [PROV primer](https://www.w3.org/TR/prov-primer/) |
| Hybrid contextual retrieval | Anthropic describes combining lexical and embedding search, preserving chunk context, and optionally reranking. Its reported gains concern its datasets and setup. | Benchmark against this site's current keyword search; retain titles, headings, and source context with passages. [Contextual Retrieval](https://www.anthropic.com/engineering/contextual-retrieval) |
| Incremental agent retrieval | Anthropic describes loading relevant context through identifiers and targeted tools, while noting that runtime exploration can add latency. | Return concise search hits, then let agents fetch the relevant evidence. [Context engineering](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) |
| QMD | QMD supports local lexical/vector retrieval, reranking, document fetch, and CLI/MCP access. | Reuse it for local authoring over an explicitly selected public collection. Deployment of its local model stack inside this website has not been established. [QMD](https://github.com/tobi/qmd) |
| Full GraphRAG | Microsoft's system offers entity-focused local search and corpus-wide search over generated community reports; its documentation calls global search resource-intensive. | Evaluate if whole-library synthesis proves important and simpler retrieval fails. A navigable concept graph does not itself require this system. [GraphRAG query modes](https://microsoft.github.io/graphrag/query/overview/) |
| Postgres plus pgvector | pgvector documents combining vector search with PostgreSQL full-text search and merging results. PostgreSQL full-text search is not automatically BM25. | A viable shared runtime store if update frequency, concurrency, or measured index size justifies it. [pgvector hybrid search](https://github.com/pgvector/pgvector#hybrid-search) |

## A small ontology with clear distinctions

An ontology defines the kinds of things in the collection and what their links mean. These proposed types are project choices, not a verbatim implementation of an external standard.

| Type | What it represents | Example, illustrative rather than an approved claim |
| --- | --- | --- |
| Concept | A topic with a preferred name, aliases, definition, and related topics | Retrieval-augmented generation; alias: RAG |
| Source | An article, book section, paper, dataset, or original account used as evidence | A paper section with author, date, and URL |
| Knowledge note | One useful explanation, lesson, argument, method, or open question | When a deterministic workflow is appropriate |
| Experience | A reviewed account of a decision and its context | A project decision, its alternatives, and observed outcome |
| Publication | An essay or other public presentation assembled from knowledge | An interactive guide to retrieval |
| Exhibit | A reusable interactive explanation, with its data and assumptions | A retrieval comparison with inspectable example passages |

Collections and learning paths are views over these records. A note can belong to several concepts and curated paths without duplicating its body. Domains such as engineering, finance, literature, and philosophy are navigation facets; folder nesting should not force a note into only one of them.

Keep relationships specific and few: `about`, `derived_from`, `supports`, `challenges`, `applies_in`, `explains`, and `supersedes`; use `broader` and `related` between concepts. Each editorial assertion such as `supports` or `challenges` needs a rationale, source reference, and review state. Semantic similarity may suggest a relationship, but it does not establish that one claim supports another.

```text
Source passage <--- derived_from --- Knowledge note ---- about ----> Concept
                                         |                            |
Experience <-------- applies_in ---------+                         related
                                         ^                            |
Publication -------- explains -----------+                        Concept
    |
    +---- contains ----> Exhibit ---- uses ----> Data + assumptions

Every derived item retains links to the source revisions it used.
```

### The useful unit is an idea with context

Capture naturally first. Promote a passage into its own knowledge note when it can answer a useful question independently. Preserve the original document and paragraph context. A database row for every sentence would create avoidable editorial work and can detach caveats from claims.

Each note should answer: what is the idea, when is it useful, what supports it, what limits it, and how does it connect to other ideas? Distinguish `experience`, `source_summary`, `opinion`, `synthesis`, and `open_question`. Publication approval means it may be shared; it does not certify that a claim is objectively true. Express uncertainty in words and evidence, rather than assigning an unexplained confidence percentage.

### Minimum metadata

For each record, retain a stable ID independent of its title. Also retain its type, display title, short summary, concept IDs, body, authorship, editorial state, and revision. Keep publication permission separate from content type. Evidence references identify a source, its revision, and a passage locator. Source records carry public attribution, source date where known, access date, and reuse information when available.

For derived records, retain the source revision and content hash used for review. Keep private ingestion pointers and private source text in the private workspace; expose public citations or reviewed public excerpts in the published edition. Model-assisted extraction or rewriting is recorded as a transformation, not automatically attributed as Ashwin's own statement.

Resume-based career facts should remain generated references to `AR-Portfolio/src/content/resume.json`, as existing project guidance requires. This ontology should not create a second manually maintained resume.

## One public release, several useful views

The following is a candidate publication model, not an approved implementation plan:

```text
Notion capture + public originals + approved career source
                         |
              explicit selection and review
                         |
        versioned public Markdown + structured records
                         |
            validate IDs, evidence, relationships
                         |
                 one release manifest
                  /       |       \
         website pages  search     authoring-agent view
                        indexes
```

Notion remains the editable origin for Notion-authored material. Repository-authored records have their own declared origin. Avoid silently editing two homes for the same item. Record the upstream revision used for the last approved export and surface conflicts when both homes changed.

Proposed repository layout: keep existing `writing/` editorial guidance; place approved knowledge records under a shallow `knowledge/` directory with concept, source, note, and experience groupings. Publications refer to those IDs. Generated catalogs and search indexes share the same release identifier. The website consumes a pinned release artifact rather than assuming a sibling checkout exists on the deployment machine.

Index publication should be atomic: a failed refresh leaves the previous complete release available and reports the failure to the owner. Withdrawal needs a different policy from an ordinary refresh failure: revoked items and their derived snippets must stop being served, including from caches and historical-revision lookups. A public Git history cannot guarantee erasure of material already published; keeping raw private material out of the public repository is therefore part of the content design.

## How agents should query the collection

Use the same knowledge IDs and evidence format for visitor answers and authoring agents. Their access rights may differ; access must be enforced by the server or by physically separate exported collections, not by a caller-supplied `visibility` flag.

Start with three read operations:

| Operation | Input | Output |
| --- | --- | --- |
| `search_knowledge` | Question, optional concept/kind filters, bounded result count | Ranked summaries, matching passage IDs, source attribution, release ID, and retrieval mode |
| `get_knowledge` | Stable ID and an allowed revision or passage selection | Exact content, qualifications, evidence, public citation URL, and current publication state |
| `related_knowledge` | IDs, relationship types, bounded depth and result count | Explicit relationships with rationale and provenance |

These are proposed logical operations, not three new services. Reuse one implementation behind local tooling, HTTP, and any MCP adapter. MCP defines input schemas, optional output schemas, and structured result data, which supports such a contract. [MCP tools specification](https://modelcontextprotocol.io/specification/2025-11-25/server/tools)

Typical agent sequence:

1. Search the reader's actual question.
2. Retrieve a bounded set of exact supporting passages.
3. Follow relevant `challenges` or `applies_in` links where they improve the explanation.
4. Compose an answer or article using the retrieved evidence and disclosed assumptions.
5. Validate that cited IDs and passages exist in the allowed release. State gaps when the evidence cannot answer the question.

Return concise metadata before full bodies. Keep a small guide explaining available record types, access rules, and how to retrieve evidence; fetch topic-specific material on demand. This applies the incremental retrieval principle to this collection rather than adding every note to an agent's initial prompt. [Context engineering](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)

### Retrieval strategy

Compare an exact-term baseline with lexical plus semantic retrieval. Fuse rankings and deduplicate by canonical source and passage. Preserve title, heading path, note kind, dates where relevant, and necessary surrounding context. Respect code-block and table boundaries when making search passages. Add a limited number of explicitly connected notes only when relevant; their links are context, not automatic supporting evidence.

Evaluate reranking after the first comparison. Generated contextual summaries are optional derived metadata: retain the original passage separately and do not cite generated context as if it were source text. Anthropic's experiments motivate testing these techniques, but do not establish the best chunk size, model, or result count for this corpus. [Contextual Retrieval](https://www.anthropic.com/engineering/contextual-retrieval)

QMD is already installed locally, but the current project collection covers historical portfolio documentation, not this new knowledge collection. A dedicated collection over the reviewed export is the natural authoring-agent candidate. The public service can initially evaluate a prebuilt index; measure its memory, cold-start latency, and query latency before selecting an in-process runtime or a shared database. Keep embedding model/version/dimensions in the index manifest. Query and document vectors must use a compatible embedding space. Do not silently label keyword fallback as semantic search.

## Interactive blogs as reusable knowledge presentations

The accompanying [interactive-authoring research](interactive-blog-authoring.md) compares rendering options and cites their primary documentation. The recommendation is ordinary article text plus structured interactive block data, rendered by reviewed components. An agent can propose a bespoke component in repository code when a story needs it, followed by review and tests.

For example, an article explaining retrieval could contain a small comparison in which a reader changes a query, sees the retrieved passages, and inspects why each was selected. Its knowledge records supply the explanation and citations; its exhibit definition supplies allowed controls, example data, and a static explanation. Mark illustrative data and simulations clearly. Any empirical performance chart needs a dataset and measurement method, rather than invented numbers.

Each exhibit should declare its learning objective, relevant concept IDs, source references, input bounds, data or formula version, assumptions, explanatory fallback, and component version. Include important explanations and data descriptions in the searchable text edition. Otherwise an agent may find the article title but miss the knowledge inside its widget.

The public graph can offer concept pages, guided learning paths, related ideas, and a focused local neighborhood around the current topic. This is a proposed interface design. Usability and learning benefits need testing; a large node graph alone does not establish them.

## What would establish that this is the best fit

Create a small, human-reviewed evaluation set, initially about 30–50 questions spanning the actual collection. Include exact names, paraphrases, comparisons, cross-domain connections, conflicting notes, recent changes, and questions the collection cannot answer. Proposed checks:

- Retrieval: expected evidence appears near the top; compare keyword, hybrid, and hybrid plus limited relationship expansion on the same questions.
- Grounding: citations point to the precise supporting passage; source summaries, personal views, and measurements remain distinguishable.
- Boundaries: private, withdrawn, superseded, or inaccessible material is handled according to explicit policy; arbitrary source text cannot alter tool permissions.
- Authoring: an agent can produce a useful article brief, discover counterarguments, reuse an existing exhibit, and identify missing evidence.
- Operations: import failures, duplicate Notion trees, stale revisions, and partial indexing cannot silently publish an inconsistent release.
- Runtime: measure index size, cold and warm latency, query cost, provider failures, and cancelled requests on the intended deployment.
- Reader value: observe whether visitors find a useful answer, understand the example, follow its sources, or continue to a related article. Measure interaction completion and learning/task success; time on page alone is ambiguous.

The first three architecture choices to resolve in the engineering review are the authoritative export/publication contract, the record-and-evidence model, and the shared retrieval interface. Interactive rendering and storage can then be reviewed against those contracts. Research does not settle provider cost, update frequency, or the final approved content boundary.

## Repository evidence and research limits

Inspected existing interfaces:

- `writing/README.md:26–41`: explicit mirroring and public/private editorial boundaries.
- `writing/facts-and-stories.md:5–11`: approved career-source hierarchy.
- `writing/public-content.md:52–58`: stable work IDs and multiple publication links.
- `AR-Portfolio/src/lib/blog-model.mjs:23–28`: keyword filtering over title, description, and tags.
- `AR-Portfolio/src/lib/publishing.mjs:3–13`: strict article metadata and explicit publication. New ontology fields cannot simply be added to existing frontmatter without a schema change or a separate validated record format.
- `AR-Portfolio/src/lib/publication-files.mjs:11–24`: catalog persistence and rollback patterns worth reusing.
- `AR-Portfolio/src/lib/notion-blog.ts:28–55`: pagination and published database membership checks.
- `AR-Portfolio/src/app/blog/[id]/page.jsx:62`: the existing Markdown component renderer.

These are read-only observations, not a claim that any proposed implementation is tested. The initial research did not itself import Notion content or provision a model or database. The later reviewed text export is documented in the collection README; the application implementation was reverted.
