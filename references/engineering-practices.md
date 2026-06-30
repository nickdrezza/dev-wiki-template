---
title: Engineering practices
description: How the team writes, reviews, and ships code — the shared baseline expectations.
owner: the team lead
updated: 2026-01-08
---

# Engineering practices

The shared baseline for how we work. These are defaults, not dogma — when a situation calls
for an exception, make it deliberately and say why in the pull request.

## Version control

- **Work on a branch, open a pull request.** Don't push directly to `main`.
- Keep PRs small and focused — easier to review, safer to revert.
- Write commit messages that explain *why*, not just *what*.

## Code review

- Every change is reviewed before it merges.
- Review for correctness, clarity, and fit with existing patterns — match the surrounding code.
- Reviews are about the code, not the author. Be kind and specific.

## Testing

- New behavior comes with tests; bug fixes come with a test that would have caught the bug.
- CI must be green before merge.

## Documentation

- If a change alters how a system works or is operated, update the docs in the same PR.
- Durable, cross-repo knowledge goes in this wiki; repo-specific detail stays in the repo
  (see [`CONVENTIONS.md`](../CONVENTIONS.md) on source of truth).

## Operations

- Prefer idempotent, retry-safe jobs.
- Don't store secrets in code (see [secrets management](../policies/secrets-management.md)).
- When something breaks in a way worth remembering, write an [incident](../incidents/).
