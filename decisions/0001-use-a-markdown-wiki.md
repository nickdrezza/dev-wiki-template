---
title: 0001 — Use a plain-Markdown, Git-backed wiki
description: Why the team's knowledge base is Markdown files in a Git repo, filed by document type.
owner: the team lead
updated: 2026-01-10
---

# 0001 — Use a plain-Markdown, Git-backed wiki

**Status:** accepted · **Date:** 2026-01-10

## Context

The team needed a knowledge base for "how we build and operate." We wanted something durable,
searchable, easy to contribute to, and resistant to going stale. We considered a hosted wiki
product, a shared-docs folder, and a Markdown repo.

## Decision

Use **plain Markdown files in a Git repo**, filed by **what a document is**
(policy / guide / system / runbook / reference / decision / incident) rather than by topic.
Each doc carries frontmatter (`title`, `description`, `owner`, `updated`); each change updates
a folder index and a curated `CHANGELOG.md`.

## Why

- **Lives next to the work.** Same tools as code — branches, pull requests, review, history.
- **Durable and portable.** Plain text outlives any single tool; no vendor lock-in.
- **Filing by document type scales.** "Where does this go?" has one answer, so the base stays
  navigable as it grows.
- **Ownership fights decay.** A required `owner` and `updated` make staleness visible.

## Trade-offs

- Contributors need a little Git fluency (mitigated by reviews and templates).
- Rich media and real-time co-editing are weaker than in a hosted wiki — acceptable for a
  text-first knowledge base.

## Consequences

- The folder taxonomy and frontmatter are conventions everyone follows (see
  [`CLAUDE.md`](../CLAUDE.md)).
- Repo-specific detail stays in its repo; the wiki owns only cross-repo, durable knowledge.
