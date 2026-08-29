# Architecture Decomposition (专题拆分)

Route: the user says a large technical document is confusing, asks to split important subsystems into separate documents, asks to reorganize document order/titles, or explicitly says each subsystem deserves a full document. Do not interpret this as a request to create a set of link-only navigation pages.

Load [rules/placement.md](../rules/placement.md) for destinations and [rules/links.md](../rules/links.md) for link repairs before editing.

## Procedure

1. Identify the durable domains first: each candidate subsystem should have a distinct responsibility, source boundary, state/data model, execution path, security boundary, or failure/recovery semantics.
2. Split by meaningful architecture boundaries, not by arbitrary file names, document genres, or every small module. A major subsystem such as Memory, Context Builder, Agent Loop, Agent Tools, Skills/MCP, Graph/Evidence, Sandbox/Egress, Provider, Web/SSE, Mobile, or Auth/Files/Tasks may deserve its own document when its design can be understood independently.
3. Before creating files, inventory existing headings and map each substantive section to exactly one target document. Treat existing documents as source material to merge, rewrite, rename, or delete — not as immutable files that must all survive.
4. Every retained or newly created architecture document must carry real design value. At minimum, it should explain its scope and purpose, important source entry points, a control/data flow, implementation contracts or invariants, security/authorization boundaries where relevant, failure/recovery or consistency behavior where relevant, and meaningful trade-offs or limitations. A document whose body is only links, a short summary, or a table of contents is not a completed architecture document.
5. A top-level overview may contain the reading map, but it must also retain substantive project positioning, system layers, process topology, core data flow, architectural principles, and cross-domain relationships. Do not replace a valuable overview with an empty catalog page.
6. Merge documents when they have the same primary owner, answer the same reader question, share the same state/transaction boundary, and separating them would force duplication. Split documents when each has an independent reader question and at least one independent design boundary; link between them only after verifying that both sides contain substantive discussion.
7. When a new专题 absorbs an old document, preserve its valuable facts in the target before removing the source. Do not keep a legacy document merely as a link-only shell. If the old document has no distinct remaining purpose after migration, delete it only when cleanup is within the authorized writable root and the user has requested organization, deduplication, replacement, or has explicitly said old documents need not be retained.
8. If numbering or titles are reorganized, treat the change as one atomic migration: choose the complete final sequence and canonical titles first, rename/move files, update headings and all vault-internal links, then scan for old filenames, old numbers, duplicate titles, missing targets, and dangling links. Do not leave a mixed old/new numbering scheme.
9. Report the final information architecture, which content was merged into which document, which legacy files were removed, and any content that could not be placed without losing meaning.

## Prefer Merging Into An Existing Guide Over Splitting

Before creating a new focused document, check whether an existing note already covers the same subject as a guide, overview, or index. When one exists:

- Fold new clarifications, deeper usage notes, configuration snapshots, and troubleshooting refinements into the matching section of that existing document when the subject and boundary genuinely match.
- Split out a separate document when the new content is a distinct major subsystem, would make the parent document a mixed architecture dump, belongs to a different subject or environment, or the user explicitly asks for a standalone document.
- Do not create a near-duplicate focused document that merely restates the guide's overview.
- Do not reduce the original guide to a link-only shell after splitting. Either retain its own substantive scope, rewrite it as a substantive overview, or remove it after migrating its unique content and repairing links.

## Substantive-Document Self-Check

Before reporting completion, inspect every target document and verify:

- it has a clear single subject rather than a mixed subsystem inventory;
- it contains multiple substantive sections, not only navigation or related links;
- its source paths and implementation claims were checked against the relevant code or existing source-backed note;
- its outbound links point to notes that genuinely discuss the linked subject;
- no important section from the old document was silently discarded;
- the overview, numbering, filenames, headings, and links all describe the same final structure.
