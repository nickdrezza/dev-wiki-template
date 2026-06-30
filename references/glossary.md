---
title: Glossary
description: Shared terms and acronyms used across the team's docs and systems, defined once.
owner: the team
updated: 2026-01-08
---

# Glossary

Define a term here once and link to it rather than re-explaining it. Keep entries short.

- **ADR** — Architecture Decision Record. A short doc capturing *why* a decision was made.
  Lives in [`decisions/`](../decisions/).
- **Analytics tables** — the published, consumer-facing tables in the warehouse, derived from
  raw data by transforms. Downstream tools read these, never the raw layer.
- **Idempotent** — an operation that can be run multiple times with the same result. Important
  for safely retrying jobs (see [Restart a stuck job](../runbooks/restart-a-stuck-job.md)).
- **Raw layer** — the unprocessed tables a loader writes first, before transforms run.
- **Runbook** — a terse, step-by-step procedure for operating or recovering a system under
  pressure. Lives in [`runbooks/`](../runbooks/).
- **Source of truth** — the single place a fact authoritatively lives. For repo-specific
  facts, that's the repo; the wiki links to it rather than copying it.
