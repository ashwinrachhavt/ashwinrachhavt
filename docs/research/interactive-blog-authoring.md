# Agent-authored interactive writing

**Status: archived design research, September 23, 2026.** The website implementation was subsequently reverted at the owner’s request. This repository preserves the [public knowledge text](../../knowledge/README.md); the search service, Eve integration, and interactive-blog proposals below are not current website features. References to local drafts or source line numbers describe the workspace inspected on that date.

## Recommendation

Keep reusable knowledge and evidence independent of the blog format. Have agents assemble an article from approved knowledge records, write Markdown, and select a small set of reviewed interactive components through validated data. Each interaction should teach one concrete idea and retain a readable explanation without JavaScript.

Use trusted, repository-reviewed React or MDX when an essay needs a genuinely new interaction. Treat such contributions as application code with preview and tests. Do not execute code found in Notion, retrieved documents, visitor prompts, or generated article payloads.

This is an engineering inference for this repository, not a measured claim that one publishing format increases engagement.

## Website baseline inspected during research

Evidence from `../AR-Portfolio`:

- `package.json:28`, `:31`, `:35`, `:37`: Next.js 16.3.5, React 19.2, react-markdown 10.1, remark-gfm 4. The dependency list has no MDX package.
- `src/app/blog/[id]/page.jsx:34` defines the existing Markdown component mapping; `:62` renders the article through `ReactMarkdown`. Extend this publishing surface instead of introducing a second blog engine.
- `src/lib/publishing.mjs:3` uses a strict Zod publication schema. `:14` validates imported Markdown, including size, links, expiring asset URLs, and possible credentials. These are useful validation patterns, not proof that all publication or privacy risks are covered.
- `src/lib/blog.server.ts:26` merges reviewed local writing with Notion articles; `:30` resolves reviewed local articles first. Preserve this existing content path.
- `src/app/tools/workflow-readiness/WorkflowBrief.tsx:11` already renders typed data as an interactive document with export and explicit error feedback. Reuse its design conventions where appropriate; it is not yet a generic blog-widget system.

## Authoring alternatives

| Approach | Evidence | Assessment for this project |
|---|---|---|
| Markdown plus typed interactive blocks | react-markdown supports custom component mappings and plugins; its security guidance warns that custom components/plugins can undermine its safe defaults. [Official README](https://github.com/remarkjs/react-markdown#security) | **Recommended default.** Keep prose portable, validate the widget payload, and render through an explicit registry. Constraint: a new kind of interaction requires a code contribution. |
| Trusted MDX / repository React | MDX compiles Markdown with JSX into JavaScript; Next supports MDX integration. [MDX compiler](https://mdxjs.com/packages/mdx/), [Next MDX guide](https://nextjs.org/docs/app/guides/mdx) | Useful escape hatch for bespoke essays after code review. This is executable source code, even when compiled during build. An allowlist of visible JSX components alone does not make arbitrary MDX safe. |
| Runtime-generated JavaScript or remote MDX | MDX explicitly warns that `evaluate` and `run` evaluate JavaScript. [MDX API](https://mdxjs.com/packages/mdx/#evaluatefile-options) | Poor default for a public knowledge library. It creates a code-execution boundary and extra correctness/testing work for every generated post. If a future coding playground needs execution, review that as a separate sandbox feature. |
| Observable Framework / Idyll | Observable combines Markdown, reactive JavaScript, and build-time data snapshots. Idyll embeds React components and reactive variables in narrative text. [Observable introduction](https://observablehq.github.io/framework/), [data loaders](https://observablehq.github.io/framework/data-loaders), [Idyll docs](https://idyll-lang.org/docs) | Good prior art for explorable explanations. Borrow their separation of narrative, reusable components, and datasets. A wholesale renderer migration is not justified by the inspected site. Compatibility with this installed Next/React combination was not tested. |

## The contract between knowledge and presentation

The following is a proposed contract, not an existing API:

```text
approved source records + concepts + evidence passages
                         |
              bounded evidence bundle
                         |
                 authoring agent
                         |
        Markdown + typed blocks + dependency manifest
                         |
         schema / citation / public-access validation
                         |
                 preview and review
                         |
    article HTML + optional interactive React components
```

An authoring agent needs more than search snippets. Provide a bounded evidence bundle with stable record IDs, versions, relevant passages and locators, original public URLs, and explicit distinctions between external claims, personal experience, interpretation, and illustrative assumptions. A proposed `get_evidence_bundle(ids, purpose, max_tokens)` operation can reuse the same retrieval service as visitor search. Requesting a bundle must not expand the caller's access.

Keep interaction specifications separate from canonical claims. A widget should reference knowledge IDs, record its learning objective, and identify its data and assumptions. For example, an illustrative queue simulator should not make its generated wait times appear to be measured experience.

Proposed payload shape, intentionally illustrative:

```json
{
  "schemaVersion": 1,
  "type": "scenario-comparison",
  "id": "workflow-choice",
  "objective": "Explain when a fixed workflow is sufficient",
  "evidence": [{ "recordId": "lesson-example", "version": 3, "locator": "decision-criteria" }],
  "dataKind": "illustrative",
  "assumptions": ["The steps and acceptance criteria are known in advance"],
  "fallbackMarkdown": "Compare a fixed workflow with an adaptive agent using the criteria below.",
  "props": { "scenarioSetId": "workflow-choice-v1" }
}
```

Validate by a discriminated schema per widget type, not an unrestricted `props` object. Resolve dataset/scenario IDs from the approved build manifest. Do not let content select module imports, event-handler source, arbitrary fetch targets, or JavaScript expressions. Validate bounds, enum values, number finiteness, asset references, source versions, and required fallback content. Schema validity checks shape; editorial review still checks whether evidence supports the explanation.

Keep the dependency manifest so a corrected or withdrawn source can identify affected articles, widget datasets, rendered caches, and search documents. The exact withdrawal and invalidation mechanism needs the broader engineering review.

## Initial interaction vocabulary

Start with the smallest set justified by actual essays. Candidate types are a scenario comparison, a short quiz with explanation, a parameterized demonstration, and an evidence explorer. Treat this list as options, not approved scope. For each, the author supplies a learning question, an expected insight, source links, and a plain-text explanation.

Agents can compose existing types as content. Creating a new type goes through the regular code contribution path: typed interface, deterministic calculations, examples, tests, and preview. This preserves creative freedom without making each publication a new runtime program.

## Rendering, accessibility, and retrieval

Keep article prose server-rendered and make only the interactive leaf components client components. The installed Next documentation recommends small client boundaries to reduce JavaScript and requires serializable client props. Evidence: `node_modules/next/dist/docs/01-app/01-getting-started/05-server-and-client-components.md:188`, `:298`; [public guide](https://nextjs.org/docs/app/getting-started/server-and-client-components). Lazy loading can defer client components; `ssr: false` is not supported inside Server Components. Evidence: installed `01-app/02-guides/lazy-loading.md:13`, `:94`; [public guide](https://nextjs.org/docs/app/guides/lazy-loading).

Render the explanation, assumptions, citations, and a useful static state even if interaction code fails. For a chart, include a summary and accessible data representation. W3C describes short and long text alternatives for complex images and explicit header relationships in tables. [Complex images](https://www.w3.org/WAI/tutorials/images/complex/), [table guidance](https://www.w3.org/WAI/tutorials/tables/). For sliders, provide keyboard operation, labels, current values, and understandable units; WAI documents the expected keyboard and ARIA behavior. [Slider pattern](https://www.w3.org/WAI/ARIA/apg/patterns/slider/).

Index the explanation, learning objective, conclusions, and evidence relationships. Do not make search or an agent run a browser to discover knowledge hidden in an animation. This is a proposed retrieval design: the widget is another view of the knowledge, not the only place the knowledge exists.

## Validation and success measures

Proposed acceptance tests:

- Invalid type/version, missing source, private dependency, stale evidence, malformed parameters, and unsupported URLs fail publication with an actionable message.
- Numerical widgets have boundary and known-answer tests. Quiz answers and feedback reference the same reviewed evidence as the article.
- End-to-end tests cover keyboard and mobile use, reset, navigation away, failed JavaScript loading, static content, and working citations. A broken widget must not erase the article.
- Generated writing is checked against a fixed evidence set for unsupported claims, incorrect attribution, fabricated metrics, and disagreement between prose, widget, and fallback.
- Reuse existing publishing tests and add feature-specific tests; framework changes run the project-required `pnpm lint`, `pnpm typecheck`, and `pnpm build`.

For a pilot, compare a small number of interactive explanations against readable versions of the same material. Record interaction starts and completion, source opens, explicit usefulness feedback, and an optional concept question before/after. Treat these as proposed product signals; clicks, time on page, and quiz improvement alone do not establish that the interaction caused learning. Do not claim engagement gains until observed results support the claim. No comparative user study or site analytics was performed for this memo.

## Limits and next review step

This research checked primary documentation, Context7 passages for react-markdown, installed Next documentation, and the relevant current renderer/publisher source. It did not implement an interaction, benchmark bundle size, audit accessibility of the existing site, or validate a sample generated article. The engineering review should choose the publication contract, public-data boundary, first actual article/interaction, and evidence-version lifecycle before implementation.

This memo is retained as background for future authoring decisions. Publishing it does not enable interactive rendering or change the website.
