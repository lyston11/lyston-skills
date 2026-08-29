# Links And Discoverability

Rules for cross-references inside the vault. They apply whenever a route creates, updates, moves, splits, or repairs links — including a top-of-document "相关文档" / "相关阅读" / "See also" line.

## Every Link Is A Content Claim

A wiki link like `[[Pi 插件用途与使用指南]]` claims the target note actually discusses this subject. Do not add a related-document link merely because the target exists, shares a category, is a sibling subject, or would "be nice to cross-reference". A link whose target never mentions the current subject is a **dangling related-link** — it wastes the reader's click and signals a relationship the target note does not confirm.

Before writing any `[[...]]` link to another note:

1. **Verify the link is warranted.** Open or grep the target note and confirm it contains substantive content about the *current* subject — not just a passing keyword, a category match, or nothing at all. A sibling subject under the same category (e.g. another `Pi/` note) is **not** by itself a reason to link.
2. **Two valid outcomes, choose one per link:**
   - **The target genuinely discusses this subject** → the link may stay. If the discussion is thin, prefer to add a one-line clarification to the target's matching section first so the link pays off.
   - **The target does not discuss this subject** → either (a) add a concise, substantive section about this subject to the target note (one that earns the link, not a stub), or (b) **omit the link entirely**. Do not leave a link whose target has no relevant content.
3. **No speculative link lists.** Do not write a `相关文档: [[A]] [[B]] [[C]]` line and plan to "fill in later". Each link must be justified at write time by real target content; if you have not checked the target, do not add the link.
4. **A bare "related documents" block is optional, not required.** If no existing note genuinely covers the subject, the new document simply has no related-document links. Silence is correct; a dangling link is not.
5. **Re-check on material updates.** When materially updating a note, re-verify any existing outbound `[[...]]` links against current target content. If the target no longer (or never did) discuss the subject, remove the link or repair the target — same two-outcome rule.

This applies to Obsidian wiki links `[[note]]`, relative Markdown links, and "related documents" sections alike. The principle: every cross-reference must be backed by real content at the destination, or it must not exist.

## Link Syntax

- Prefer Obsidian wiki links for vault-internal references. Use relative Markdown links only when they are clearer for a specific path.
- Use clear headings and related-document links inside the actual notes, not in separate navigation files.

## After Moves And Splits

- Update all affected Obsidian wiki links across the vault after moves, renames, splits, merges, or numbering changes, and verify every changed link target exists.
- Link repairs stay inside the Codex root (see SKILL.md writable boundary): if a link points to a note outside the root, leave the link or report it — do not open or rewrite the outside file.

## Report-Back Self-Check

When the report-back step mentions links, each listed link must have been verified against real target content during this task. If a link could not be verified (e.g. target note not opened), report it as omitted rather than listing it as if it were safe.

## No Navigation Junk

- Do not add or update folder `README.md` files, separate catalogs, summary entry pages, or artificial navigation folders.
- Do not create catch-all locations (`其他`, `杂项`, `综合`, `基础设施`) to hold unclassifiable links or notes.
- For sensitive content, record the sensitive boundary inside the relevant subject document itself ([rules/sensitive-records.md](sensitive-records.md)).
