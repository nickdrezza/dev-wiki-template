---
title: Local development setup
description: Get a working local dev environment from a clean machine.
owner: Platform team
updated: 2026-01-08
---

# Local development setup

**Get one service running locally end-to-end.** This guide is intentionally generic — the
exact commands for each service live in that repo's own `README`. This covers the shared
toolchain every repo assumes.

## Prerequisites

- A POSIX shell (macOS/Linux, or WSL on Windows).
- Git, configured with your name and email.
- A recent language runtime for the service you're working on (see the repo's `README`).
- A container runtime, if the service uses one.

## Steps

1. **Clone the repo** and read its `README` — it's the source of truth for that service.
2. **Install dependencies** with the project's package manager.
3. **Create your local config** by copying the committed `*.example` file and filling in
   values. Real secrets come from the password manager — never commit them
   (see [secrets management](../policies/secrets-management.md)).
4. **Run the service** with the documented start command and confirm it's healthy
   (a health endpoint, a log line, or a passing smoke test).
5. **Run the tests** to confirm your environment matches CI.

## Troubleshooting

| Symptom | Likely cause | Fix |
|---|---|---|
| Dependency install fails | Wrong runtime version | Match the version pinned in the repo |
| Service won't start | Missing local config value | Re-check your copied `*.example` file |
| Tests pass locally, fail in CI | Uncommitted local state | Run against a clean checkout |
