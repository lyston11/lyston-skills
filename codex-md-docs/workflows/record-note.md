# Record A Note

Default route: create, append to, or update a Markdown note in the Codex vault. Load [rules/placement.md](../rules/placement.md) before choosing a destination; load [rules/links.md](../rules/links.md) when writing or repairing cross-references, and [rules/sensitive-records.md](../rules/sensitive-records.md) when the content includes credentials.

## Before Writing

1. If the user gives an exact file path, use that path.
2. If the user gives a folder path, choose or create the `.md` file inside that folder, using the filename suffix rule when relevant.
3. Identify the primary owner: what single project, service, product, agent, skill, plugin, application, tool, environment, network technology, cloud platform, or learning topic owns most of the document's durable value?
4. Apply the classification precedence ([rules/placement.md](../rules/placement.md)) to choose one fixed first-level category.
5. Inventory the chosen category's second-level folders before searching deeply. Evaluate candidate subject folders by ownership, not shared keywords.
6. Search filenames and headings inside the chosen subject folder for the topic, environment, hostname, date, service name, domain, or request keywords.
7. Prefer an existing note only when category, subject, topic, and device/environment all match.
8. Before creating a focused note, check whether an existing guide for the same subject already has a matching section that should be updated instead.
9. If the subject currently exists as a legacy root-level folder, migrate that subject folder into the correct category before adding new documentation. Update vault-internal links and remove the empty legacy folder. Do not reorganize unrelated subjects during a normal single-note task.
10. Identify the device/environment before choosing whether to append or create. Compare hostname, OS, cloud provider, public domain/IP, deployment root, path style, container runtime, and tunnel or reverse-proxy endpoint.
11. Never merge records across different subjects, projects, devices, or environments merely because integrations or names overlap.
12. Preserve existing Markdown structure, frontmatter, headings, Obsidian links, and unrelated content.
13. Do not create database backups, code backups, duplicate archival files, root landing pages, folder entry pages, or catalog documents unless the user explicitly asks.

## Create, Append, Or Update

Choose the smallest durable change that fits the request:

- **Create** a new second-level subject folder under a fixed category when no existing subject folder strongly owns the topic.
- **Create** a new file within the correct subject folder when the topic is new, the environment differs, the suffix differs, or the user asks for a standalone document.
- **Append** for deployment logs, operational history, incident notes, progress records, meeting notes, dated observations, command outputs, session handoffs, and continuing timelines that belong to the same subject and environment.
- **Update** an existing section for living guides, SOPs, runbooks, architecture notes, checklists, policies, configuration records, or summaries whose current content should be refined.

For dated append entries, prefer:

```markdown
## 2026-05-26
```

If updating risks overwriting important history, append a dated section instead. If environment cues are missing and multiple notes could match, ask one concise clarifying question.

## Merging Into An Existing Guide

Before creating a new focused document, check whether an existing note already covers the same subject as a guide, overview, or index. When one exists:

- Fold new clarifications, deeper usage notes, configuration snapshots, and troubleshooting refinements into the matching section of that existing document when the subject and boundary genuinely match.
- Split out a separate document when the new content is a distinct major subsystem, would make the parent document a mixed architecture dump, belongs to a different subject or environment, or the user explicitly asks for a standalone document.
- Do not create a near-duplicate focused document that merely restates the guide's overview.
- Do not reduce the original guide to a link-only shell after splitting. Either retain its own substantive scope, rewrite it as a substantive overview, or remove it after migrating its unique content and repairing links.

## Content Style

Record-mode notes should be concise and useful when reopened later:

- Include concrete paths, commands, service names, ports, config files, dates, and verification results when relevant.
- Keep facts separate from assumptions.
- Use fenced code blocks for commands, configuration, logs, and structured output.
- For operational records, include what changed, where it lives, how to verify it, and rollback or next steps when relevant.

## Report Back

After writing, briefly report:

- The exact file path.
- Whether content was created, appended, moved, split, or updated.
- The fixed first-level category and second-level subject selected.
- The device/environment suffix used when relevant.
- Any link repairs, legacy-folder migration, sensitive-content warning, or important caveat discovered while writing.
