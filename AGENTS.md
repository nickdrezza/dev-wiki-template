# Guidance for AI coding agents

This repository is a **Markdown knowledge base**, not application code. If you're an AI
assistant helping someone add to or edit this wiki, follow the same rules a human contributor
does:

- **Read [`CONVENTIONS.md`](CONVENTIONS.md) first** — it's the source of truth for how docs
  are filed and formatted. Re-read it each time; conventions can change.
- **File by document type.** Put the doc in the folder that matches *what it is* (policy,
  guide, system, runbook, reference, decision, incident), not what it's about.
- **Start from [`_template.md`](_template.md)** and fill in all frontmatter
  (`title`, `description`, `owner`, `updated`). Never leave `owner` blank.
- **Make one coherent change:** the new/edited doc **plus** its folder `README.md` index entry
  **plus** a dated bullet at the top of [`CHANGELOG.md`](CHANGELOG.md).
- **Don't copy repo-specific facts in.** If a fact belongs to exactly one code repo, link to
  that repo instead of duplicating it here.
- **Treat ADRs and incidents as immutable** — supersede or link forward; don't rewrite history.

This file is intentionally short; [`CONVENTIONS.md`](CONVENTIONS.md) and
[`CONTRIBUTING.md`](CONTRIBUTING.md) hold the detail.
