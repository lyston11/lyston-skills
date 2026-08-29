# Project Textbook / Deep-Learning Mode

Use this mode for requests such as “深入研究这个项目”, “让我能完整学习这个项目”, “从原理到源码”, “一步步解构”, “源码级教材”, or “通过一份文档掌握它”. The deliverable is a teaching artifact, not a repository report, feature catalog, or prettified table of contents.

## Outcome Contract

The document should enable a motivated reader to:

- explain the problem the project solves and the design beliefs behind it;
- build a stable mental model of the system and its boundaries;
- trace representative end-to-end control, data, and state flows;
- locate and read the most important source entry points independently;
- distinguish current production paths from compatibility, deprecated, experimental, and planned paths;
- reason about trade-offs, failure modes, security, reliability, and evaluation;
- run meaningful experiments that turn passive reading into working knowledge.

“Complete” means covering the concepts and relationships required to reason about the project. It does not mean listing every directory, endpoint, class, option, or release note.

## Research Contract

Before writing:

1. Fix the evidence boundary: repository path, branch or tag, commit, inspection date, and relevant release. State it near the beginning of the document.
2. Read foundational material directly and completely when it defines project intent or architecture: the primary README, architecture/design documents, contributor instructions, current release notes, and official roadmap when relevant. Do not outsource these documents to summaries.
3. Trace the representative source paths. Cover the real runtime entry points, state transitions, data model, storage boundaries, configuration, tests, and failure handling—not only interface definitions.
4. For wide repositories, use bounded parallel exploration to reduce context pollution. Require `file:line`, symbol names, and key quotations. Verify consequential claims by sampling the cited locations rather than repeating the whole search.
5. Separate evidence classes explicitly:
   - current implemented behavior;
   - compatibility or legacy behavior;
   - experimental or partially migrated behavior;
   - official roadmap/backlog;
   - the author's inference or recommended exercise.
6. Prefer repository-relative `file:line` citations so the study document remains portable. When exact lines are unstable or the important contract is a file-level scope comment, cite the file and symbol and say so.
7. Treat documentation and code disagreement as a finding. Explain which source governs the current runtime and why; do not silently select the easier narrative.

## Teaching Design

Build the explanation in layers. The exact headings and chapter count are project-dependent; do not mechanically reproduce a universal template.

### Self-contained learner contract

The document must teach the stated learner without requiring them to open source code, official documentation, or a glossary merely to understand the main prose. Source code strengthens and verifies the lesson; it must not carry the explanation on the author's behalf.

Before writing, choose the lowest reasonable learner baseline from the request. If the user says they want to learn the project completely and does not claim prior expertise, assume no project-specific knowledge and no unexplained RAG, distributed-systems, database, model, or framework terminology. General computer literacy is not permission to assume BM25, tokenization, embeddings, message acknowledgements, schema mappings, checkpoints, or vector dimensions.

Apply a **first-use gate**:

- define an unfamiliar term in plain language before using it to explain another term;
- say what concrete problem caused the concept to exist;
- connect the English/source identifier to a stable Chinese meaning;
- show one concrete instance before relying on the abstraction later;
- do not defer essential understanding to an end-of-document glossary.

A later glossary is a review aid, not a substitute for first-use teaching.

### Minimum teaching unit for an important concept

For every concept that controls the main data flow, behavior, configuration, failure mode, or design choice, make the section answer the following in a natural teaching order:

1. **What is it?** Give a plain-language definition that does not depend on another unexplained term.
2. **Why does it exist?** Name the specific problem the system had without it.
3. **What goes in and comes out?** Show a small realistic input and output.
4. **What happens in the middle?** Walk through the transformation or decision step by step.
5. **How does this project implement it?** Only now introduce project fields, components, configuration, and source symbols.
6. **What changes when a parameter changes?** Use a comparison, worked example, or counterexample.
7. **How does it fail and how can the learner observe that?** Show a symptom and a diagnostic checkpoint.

Do not render these seven questions as a fixed template in every subsection. They are a completeness test. Shorten only when the answer is genuinely obvious from the surrounding lesson.

### Show transformations, not inventories

A list of components, parameters, fields, states, source files, or pipeline stages is a map; it is not yet an explanation. For the central paths, show representative artifacts changing through the system, for example:

```text
raw paragraph
  -> parsed blocks with coordinates
  -> chunks with inherited title and metadata
  -> token fields and embedding vector
  -> indexed record
  -> lexical/vector candidates with scores
  -> reranked evidence
  -> final prompt
  -> answer with citation
```

Use one small but realistic record at each important boundary. Keep field values consistent with the running example so the reader can see what was added, removed, split, scored, filtered, or persisted.

Do not claim that a flow is explained when the document only names its arrows.

### Start with the learner

State assumed prerequisites, learning outcomes, how to read the document, and what can be skipped on a first pass. Separate mandatory prerequisites from concepts the document itself will teach. Never list an unfamiliar concept as a prerequisite merely to avoid teaching it when that concept is central to the requested subject.

### Move from intuition to mechanism

For each major idea, prefer this teaching progression where useful:

1. the concrete problem or tension;
2. an intuitive model;
3. the project's chosen design;
4. the end-to-end runtime behavior;
5. the source implementation and data structures;
6. trade-offs, edge cases, and failure modes;
7. an observation, experiment, or exercise.

This is a reasoning pattern, not a required seven-subheading template. Combine steps when that reads better.

### Use a running example

Choose one realistic example that can travel through the system—from input through transformation, storage, retrieval/execution, output, and observability. Revisit it whenever a new subsystem changes its state. A good running example prevents chapters from becoming disconnected component summaries.

### Teach the system twice

First give the reader a compact whole-system mental model. Then descend into mechanisms and source code. Finally reconstruct the whole flow with the added detail. The repeated model is deliberate learning reinforcement; chapter-level prose should otherwise avoid duplication.

### Explain code as contracts

Do not dump filenames. For each important source location, explain:

- why this is an entry point or boundary;
- what inputs, outputs, state, and invariants it owns;
- who calls it and what it calls next;
- where errors, retries, cancellation, authorization, and persistence occur;
- what a learner should notice when opening it.

Use short excerpts or pseudocode only when they expose a contract more clearly than prose. Avoid copying large source blocks.

Place source citations after the learner can already explain the mechanism in plain language. A paragraph that becomes meaningless when its file path, symbol, or field name is removed has failed the self-contained learner contract.

### Equations, scores, fields, and configuration

Never present an important formula as self-explanatory.

- define every symbol and its unit or range;
- explain what a larger or smaller value means;
- substitute concrete numbers and calculate at least one result step by step;
- compare at least two settings when the formula controls a design trade-off;
- state implementation qualifications such as normalization, truncation, backend differences, or whether the formula is conceptual rather than byte-for-byte source behavior.

For storage fields or schemas, show a small sample record and explain each important field by its consumer:

- who writes it;
- who reads it;
- what behavior changes if it is absent or wrong;
- whether it is source data, derived data, metadata, an index-only field, or runtime state.

For configuration, explain the default only after explaining the unit and behavior. “Default 512”, “weight 0.3”, or “dimension 1024” is not useful until the reader understands 512 of what, 0.3 applied where, and why 1024 must match another object.

### Control jargon density

Do not let prose collapse into English nouns and source identifiers. When a paragraph contains several terms such as tokenizer, delimiter, overlap, dense KNN, reranker, schema, checkpoint, ACK/NACK, or contextvars, either teach them in sequence or split the paragraph. Inline code formatting distinguishes an identifier; it does not explain it.

Translate implementation language into domain behavior. Prefer “任务处理完成后向消息系统确认，防止同一任务再次投递” before introducing `ACK`; prefer “把文本切成模型处理的最小计数单位” before introducing tokenization.

### Definition is not mastery

Do not treat a one-sentence definition as sufficient teaching for a concept the learner must use to reason about the project. “Embedding is a vector representation”, “overlap repeats adjacent text”, or “idempotency means repeated execution is safe” merely renames the idea. The learner still needs to see the situation before the mechanism exists, the concrete data before and after it acts, and the consequence of changing or removing it.

For every central mechanism, provide a **complete learning episode** before compressing it into a summary table:

1. begin with a concrete situation and a question the learner can understand without the term;
2. show the raw input or initial state;
3. perform the transformation or decision in visible steps, keeping values consistent;
4. show the resulting output or state and explain why it is better or different;
5. change one condition or parameter and compare the result;
6. only then give the compact definition, field table, formula, component name, or source location.

A central mechanism must not consist only of a definition, bullets, a table, a diagram, pseudocode, a formula, defaults, and source citations—even if all of those are accurate. Those artifacts summarize an explanation; they do not replace the explanatory narrative.

### Tables and lists may summarize, not silently teach

Do not introduce several unfamiliar ideas for the first time inside a component table, parameter table, schema table, checklist, or bullet list. Before or immediately after the table, walk through at least one row as a concrete story and explain the relationships among the rows. If a table can be removed without losing any narrative because the prose never used its contents, the section is probably an inventory rather than a lesson.

Likewise, a numbered pipeline such as “parse → chunk → tokenize → embed → index” is not an end-to-end explanation until the document follows one artifact through every arrow and shows what each arrow changes. A failure checklist is not troubleshooting instruction until it connects one visible symptom to observations, interpretations, and next actions.

A troubleshooting tree must give the learner a way to inspect each important branch: what signal, field, log event, query, command, or UI state to observe; one normal or abnormal example; and how that evidence changes the next step. Questions such as “is the message in the queue?” or “was the task claimed?” are not actionable unless the document teaches how to answer them or clearly marks the check as environment-dependent.

### Progressive depth, not premature compression

Teach difficult project-specific chapters in three passes when the learner baseline is low:

- **Intuition pass:** a familiar scenario, ordinary language, and the smallest useful mental model;
- **Mechanism pass:** concrete inputs, intermediate states, outputs, alternatives, and failure behavior;
- **Project pass:** actual components, fields, source contracts, configuration, and migration caveats.

Do not begin with the project pass and add a short analogy afterward. The analogy must prepare the mechanism; the mechanism must prepare the code.

Avoid chains in which an unknown term is defined only through more unknown terms. Recursively explain the dependency or replace it with concrete behavior. For example, teaching JWT via “serializer + middleware + tenant context” fails unless those ideas were already taught.

### Repair mode after learner feedback

When a learner says a document is too simplified, too code-like, or still requires opening source code:

1. treat the quoted passage as a symptom, not the entire scope;
2. identify the failure pattern—undefined terms, compressed mechanism, missing worked example, fields without records, formula without arithmetic, or source citation carrying the explanation;
3. scan every major chapter for the same pattern;
4. rewrite representative and central occurrences in progressive depth;
5. rerun the cold-reader and citation-removal tests across early, middle, and late chapters.

Do not “repair” such feedback by adding more definitions, more bullet points, more source paths, or a larger glossary. The repair must add causal explanation and visible transformations.

## Coverage Model

Select what exists in the project, but actively audit these dimensions before declaring a textbook complete:

| Dimension | Learner question |
|---|---|
| Purpose and philosophy | What problem is being solved, and what does the project believe matters? |
| Product and scope | What is included, excluded, deprecated, experimental, or planned? |
| Architecture and runtime topology | What processes and services exist, and how do they communicate? |
| State and data model | What durable and ephemeral state exists, who owns it, and how does it change? |
| Primary input path | How does information or work enter, transform, persist, and become usable? |
| Primary output path | How does a request become retrieval/execution/generation and a returned result? |
| Algorithms and policies | Which ranking, chunking, scheduling, caching, memory, or planning decisions matter? |
| Interfaces | How do UI, API, SDK, CLI, events, and integrations expose the system? |
| Security and tenancy | Where are trust boundaries, authorization checks, secrets, and execution risks? |
| Reliability | How are idempotency, retry, cancellation, checkpoint, consistency, and recovery handled? |
| Operations | How is the system configured, deployed, observed, upgraded, and debugged? |
| Testing and evaluation | What behavior is tested, what quality is measured, and what gaps remain? |
| Evolution | What is the migration state, technical debt, release direction, and official roadmap? |
| Source reading map | In what order should a learner read the code, and what question does each stop answer? |
| Practice | What can the learner run, modify, measure, and explain to prove mastery? |

Omit dimensions that genuinely do not exist, and say so when the absence is itself informative. Add project-specific dimensions whenever they are central.

## Document Shape

Choose a structure that follows the project's causal logic. A useful long-form shape often includes:

- version boundary and learning guide;
- prerequisite concepts and first mental model;
- project philosophy and system overview;
- one end-to-end running example;
- deep mechanism chapters ordered by that example's lifecycle;
- cross-cutting security, reliability, deployment, and evaluation;
- evolution, migration, and roadmap;
- source-reading itinerary;
- staged labs, review questions, and glossary.

This list is a design aid, not a mandatory heading template. Prefer explanatory prose between tables and lists. Use diagrams only when they materially clarify a multi-step flow, hierarchy, or boundary.

## Single Document Versus Series

- If the user asks for one document, create one coherent, substantive textbook. Use an internal reading map and progressive chapters.
- Split into a series only when the user asks, or when genuinely independent volumes are necessary and the user accepts that structure.
- Do not create link-only index pages. Any overview must teach the system in its own right.
- A long document is acceptable when the learning outcome requires it. Reduce redundant prose, not necessary explanation.

## Practice and Mastery

End passive explanation with a staged learning path appropriate to the project:

1. observe a working happy path;
2. trace it in logs, storage, and source;
3. change one controlled input or policy and predict the result;
4. inject a failure and explain recovery behavior;
5. measure quality, latency, resource use, or correctness;
6. implement or design a bounded extension;
7. teach the system back using review questions or a capstone.

Commands must be clearly labeled as verified from the repository, inferred examples, or environment-dependent. Never imply that a destructive or costly experiment is safe by default.

Self-tests must be self-correcting. Provide answer keys, required answer elements, scoring rubrics, observable expected results, or another concrete way for the learner to detect misunderstanding. A page of questions without expected reasoning is a review prompt, not mastery verification. For capstones, define the evidence that constitutes a pass and common false positives.

## Quality Gate

Before reporting completion, verify:

- version/commit/date and evidence conventions are explicit;
- the document begins with a whole-system mental model and later reconstructs the flow;
- major concepts are explained before their implementation details;
- a beginner can understand the main lesson without opening the cited code or jumping to the glossary;
- every central term passes the first-use gate and every central mechanism shows a concrete input, intermediate change, and output;
- parameter lists, field tables, diagrams, and source maps are followed by explanation rather than standing in for it;
- each important formula defines its symbols and includes a worked numerical example;
- important storage/index fields are demonstrated in a sample record and connected to their writers and readers;
- at least one example crosses the important system boundaries;
- source citations explain symbols and responsibilities rather than forming a file dump;
- current, legacy, experimental, roadmap, and inference claims are distinguishable;
- security, reliability, operations, tests, evaluation gaps, and trade-offs are not hidden behind the happy path;
- practice work progresses from observation to modification and evaluation;
- the reader is given a source-reading order and a way to self-assess mastery;
- headings, diagrams, code fences, and internal links are valid;
- no dangling related-document links or empty catalog sections were introduced.

Perform a **citation-removal test** on representative sections: mentally remove repository paths, symbol names, and code-formatted identifiers. If the reader can no longer say what the mechanism is, why it exists, what data changes, and how to recognize failure, rewrite the section before completion.

Perform a **cold-reader sample** on at least five central sections from different layers. For each, verify that a reader with the declared prerequisites can answer: “What went in? What happened? What came out? Why was this design needed? What would I observe if it failed?” Do not mark a document complete if the answer depends on reading source code.

If a dimension could not be verified, mark the limitation inside the document rather than filling the gap with plausible prose.
