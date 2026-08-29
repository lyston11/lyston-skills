---
name: codex-md-docs
description: Route Markdown documentation work into the user's Codex Obsidian space using a fixed category-first, primary-subject-second hierarchy, with modes for concise records, architecture decomposition, and source-grounded project learning documents. Use when the user asks Codex to create, write, update, append, record, summarize, save, organize, archive, maintain, or deeply teach through any Markdown document unless the user explicitly gives a different destination.
---

# Codex Markdown Docs

Route every Markdown documentation request into the user's Codex Obsidian vault. This file owns the writable boundary and the task router; each route owns its procedure, and `rules/` owns invariants that apply across routes.

## Default Root

```text
/Users/lyston/Obsidian/lyston/Codex
```

Prefer this root even if older notes exist elsewhere, unless the user explicitly names another path. Create it if missing. Do not write documentation into project source trees, `/tmp`, `/root`, downloads, or ad hoc scratch folders.

## Writable Boundary

All operations that create, modify, move, rename, split, merge, append, update, link-repair, or delete files **must target paths inside `/Users/lyston/Obsidian/lyston/Codex`**. This is a trust boundary, not a preference.

- Reading outside the root for research is fine; mutating outside it is not.
- The only override is an exact path the user explicitly names for this task. One named exception never generalizes into a broader writable area, and no unlisted outside paths may be invented.
- Link repairs stay inside the root: if a `[[link]]` points outside, leave it or report it — do not open or rewrite the outside file.
- No cross-root moves or merges in either direction unless the user explicitly asks for that specific migration.
- If the request cannot be satisfied without writing outside the root and the user has not named that path, stop and ask for explicit permission.

## Task Router

Match exactly one route per task. Re-match on every new task, even in the same session — a second request may belong to a different route.

| Request | Route |
|---|---|
| Create, append, or update a note (default) | [workflows/record-note.md](workflows/record-note.md) |
| Deeply study a project; tutorial / textbook-style document | [references/project-learning-docs.md](references/project-learning-docs.md) |
| Split or reorganize a large document into subsystem topics | [workflows/architecture-split.md](workflows/architecture-split.md) |
| Organize, archive, clean up, or de-duplicate the vault | [workflows/vault-cleanup.md](workflows/vault-cleanup.md) |

Rule loading: every mutating route also reads [rules/placement.md](rules/placement.md) (categories, precedence, naming). Writing or repairing cross-references adds [rules/links.md](rules/links.md). Credential or secret values add [rules/sensitive-records.md](rules/sensitive-records.md).

If more than one mode applies, preserve the user's requested deliverable: one requested learning document stays one substantive textbook even when the repository has many subsystems — never silently turn it into a document series.

## Universal Invariants

1. **One owner per subject** — a document's durable value has exactly one category/subject owner. Never merge records across subjects, projects, devices, or environments merely because integrations or names overlap. ✓ Check: can you name the single owner after removing incidental hosts, authoring agents, and integrations?
2. **Fixed categories are closed** — no new first-level category without explicit user approval or proof every fixed category is semantically wrong. Never create catch-alls such as `其他`, `杂项`, `综合`, `基础设施`. ✓ Check: does the destination folder name appear in [rules/placement.md](rules/placement.md)?
3. **Environment lives in the filename, not the tree** — operational, deployment, access, and troubleshooting documents end with a device/environment suffix (`主题（设备或环境）.md`); devices and hostnames never determine the category. ✓ Check: does the file suffix identify the environment even when the title does?
4. **No navigation junk** — no folder `README.md`, catalog pages, entry pages, or link-only shells, and never reduce a real guide to a link-only shell after splitting. ✓ Check: would deleting the file lose real content? If not, do not create it.
5. **Every `[[link]]` is a content claim** — the target must genuinely discuss the subject, or the link must not exist ([rules/links.md](rules/links.md)).
6. **Preserve unrelated content** — existing frontmatter, headings, Obsidian links, and Markdown structure survive an edit unless the task explicitly reorganizes them.
7. **Report back after writing** — exact path; operation (created/appended/moved/split/updated); fixed category and subject; device suffix; link repairs, legacy-folder migrations, sensitive warnings, and unresolved caveats.

## Depth Discipline

Match depth to the route. Record-mode notes optimize for fast reopening and concrete actionability — concise, not thin. Textbook documents follow their dedicated reference and are as complete as the learning objective requires; never compress explanations to satisfy concision. If the learner reports a document as simplified or code-like, enter the reference's repair mode and audit the whole document for that failure pattern, not just the quoted paragraph.
