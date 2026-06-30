---
title: Secrets management
description: Where secrets live, how they're shared, and what must never be committed to Git.
owner: Platform team
updated: 2026-01-09
---

# Secrets management

**Secrets never go in Git.** Not in code, not in config, not in a doc, not in a commit
message — not even in a private repo. If a secret is committed, treat it as compromised and
rotate it.

## Where secrets live

- **Application secrets** (API keys, DB passwords, tokens) live in the team's secrets manager
  and are injected at runtime as environment variables. Code reads them from the environment;
  it never hard-codes them.
- **Personal/shared credentials** live in the team password manager, in the shared vault for
  the relevant system. Don't paste them into chat or tickets.
- **CI secrets** live in the CI provider's encrypted secret store (e.g. GitHub Actions
  repository secrets), referenced by name in the workflow.

## Rules

1. **No secrets in the repo.** Use `.gitignore` for any local secret/env file, and prefer
   committing a `*.example` template with placeholder values.
2. **Least privilege.** Scope each token to the minimum access it needs, and prefer
   short-lived credentials over long-lived ones.
3. **Rotate on exposure or departure.** Rotate any secret that may have leaked, and when
   someone with access leaves the team.
4. **One secret, one purpose.** Don't reuse the same key across unrelated systems — it makes
   rotation and revocation painful.

## If a secret leaks

1. Rotate it immediately at the source system.
2. Invalidate the old value.
3. Note what was exposed and for how long; if it warrants a retrospective, write it up in
   [`incidents/`](../incidents/).
