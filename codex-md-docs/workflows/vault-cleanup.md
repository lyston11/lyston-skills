# Organize And Clean Up The Vault

Route: the user asks to organize, archive, split, clean up, or says the vault is confusing. This operates on whole folders and the vault structure, not a single note.

Load [rules/placement.md](../rules/placement.md) before classifying anything; load [rules/links.md](../rules/links.md) before any move, merge, or delete.

## Procedure

1. Inventory Markdown files, first-level folders, second-level folders, headings, wiki links, document sizes, and large mixed documents.
2. Decide whether the task is ordinary note maintenance or **architecture decomposition mode**. Use [workflows/architecture-split.md](architecture-split.md) when the user identifies multiple important subsystems, asks for clearer reading logic, or rejects link-only summaries.
3. Classify every legacy root-level subject into one fixed category using the precedence rules.
4. For a mixed architecture document, build a section-to-target migration map before editing. Each substantive section must be retained, merged into a named target, or explicitly reported as intentionally removed.
5. Move the entire subject folder to `<category>/<subject>/` when its contents share one owner.
6. Split a mixed subject folder only when its contents have genuinely different owners or independent architectural boundaries. Do not split by document type, date, or implementation keyword alone.
7. Keep project-specific deployment, database, tunnel, plugin, and server records with the project. Do not scatter one project's operational history across technical categories.
8. Move device-first or server-first material under the closest stable subject, and keep the device/environment in the filename suffix.
9. Detect subjects placed under Codex, Pi, an agent, a tool, or a server solely because that system authored, hosted, installed, or mentioned them; move them to the real owner.
10. Update all affected Obsidian wiki links across the vault after moves, renames, splits, merges, or numbering changes. Verify every changed link target exists.
11. Remove duplicate or superseded files only after their unique substantive content has been migrated, all links are repaired, and the task scope authorizes cleanup. Do not leave empty legacy documents whose only purpose is to point elsewhere.
12. Do not create `README.md`, catalog folders, separate summary entry pages, `其他`, `杂项`, `综合`, or `基础设施` catch-alls. A requested overview may combine a real architecture overview with a reading map; it must not be link-only.
13. Verify the final root contains only the fixed categories, unless the user explicitly approved an exception.
14. Verify there are no stale links, device-only root folders, duplicate subject folders across categories, unrelated documents merged only because they share a host, old numbering references, or important source sections lost during migration.
15. Report the final file sequence and titles, substantive merge/split decisions, deletions, link repairs, and any unresolved ambiguity.
