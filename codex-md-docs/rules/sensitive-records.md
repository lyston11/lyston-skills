# Sensitive And Credential Records

Load this file whenever a task saves, migrates, or documents credentials, tokens, keys, or other secret values.

This skill may save sensitive values in the Codex Obsidian vault when the user asks to record, save, preserve, migrate, document, or remember them.

Sensitive values may include API keys, passwords, admin credentials, bearer tokens, refresh tokens, session tokens, cookies, JWTs, SSH private keys, deploy keys, recovery codes, TOTP seeds, database passwords, `.env` secrets, account-pool entries, and proxy credentials.

When saving sensitive values:

- Keep the full value exactly as provided unless the user asks for redaction. Do not redact saved values unless asked.
- Put the note under the category and subject that own the credential; do not create a separate credential category.
- Include the device/environment suffix when applicable (see [placement.md](placement.md)).
- Mark the document near the top with `敏感级别：高` and a warning such as `不要同步到公开仓库或公开分享`.
- Prefer fenced code blocks for multiline private keys, `.env` files, cookies, JSON credentials, or command output.
- Do not create catalog, summary, README, or archive pages just to list secrets.
- Do not repeat secret values in the final chat response after writing them.

A credential record should also include, when known:

- Usage and the owning subject.
- Device/environment ownership.
- Creation or rotation date.
- Validity or expiry.
- A safe verification method that does not expose the value further.
