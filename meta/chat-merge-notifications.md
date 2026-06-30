---
title: Chat merge notifications
description: How the GitHub Action posts a message to a team chat space on every push to main, plus setup and troubleshooting.
owner: Platform team
updated: 2026-01-08
---

# Chat merge notifications

When anything lands on `main`, a GitHub Actions workflow posts a message to a team chat
space. The point is to keep the team passively aware of what's shipping without anyone having
to announce it.

- **Workflow:** [`.github/workflows/notify-chat-on-merge.yml`](../.github/workflows/notify-chat-on-merge.yml)
- **Trigger:** `push` to `main` (catches squash-merges and direct pushes alike).
- **What it posts:**
  - Repo + branch + the merge headline (first line of the commit), linked to the commit.
  - **Changelog** — any bullets added to [`CHANGELOG.md`](../CHANGELOG.md) in this push (omitted if none).
  - **N files changed** — one line per file with a status emoji (added · modified · deleted · renamed), each linked to its blob.
  - A context line: who pushed it · "view full diff" compare link.

## Why push, not pull_request

The workflow fires on `push` to `main`, not on PR-merge events. A squash-merge lands as a
single commit on `main`, and `push` catches that plus any direct commit, so nothing slips by
unannounced. It checks out with full history and diffs `before..after` to compute the
changelog bullets and file list. (On the first push to a branch, `before` is all zeros, so it
falls back to diffing the commit itself.)

## The CHANGELOG.md convention

The **Changelog** section only appears when the push adds bullets to `CHANGELOG.md`. To get
value from it, add a dated bullet to the **top** of `CHANGELOG.md` in the same change:

```
- **YYYY-MM-DD** — <what changed, in plain high-signal prose>
```

Most recent first. Curated prose, not an auto-generated commit log. A good entry shows up in
the merge notification, so it pays off twice.

## One-time setup

This workflow is **generic over chat providers** that accept an incoming webhook posting JSON
(most do — e.g. a `{ "text": "..." }` payload). To wire it up:

1. **Create an incoming webhook** in your chat space and copy its URL. Treat the whole URL as
   a secret — anyone with it can post to the space.
2. **Add the URL as a repository secret** named `CHAT_WEBHOOK_URL`:
   - Settings → Secrets and variables → Actions → New repository secret, or
   - `gh secret set CHAT_WEBHOOK_URL` and paste the URL when prompted.

The next push to `main` posts a message. If your provider expects a different JSON shape than
`{ "text": ... }`, adjust the payload near the end of the workflow step.

## Testing it

Open a throwaway PR against `main` (include a `CHANGELOG.md` bullet to exercise that section)
and merge it — the message should appear within a few seconds. To inspect a run: the
**Actions** tab → this workflow → the latest run → the post step logs the HTTP status.

## Troubleshooting

| Symptom | Likely cause | Fix |
| --- | --- | --- |
| Job fails: secret not set | `CHAT_WEBHOOK_URL` missing or misnamed | Add the secret exactly as `CHAT_WEBHOOK_URL`. |
| `HTTP 404` from the webhook | Webhook deleted or space removed it | Recreate the webhook and update the secret. |
| `HTTP 400/403` from the webhook | Truncated URL or wrong payload shape | Re-copy the full URL; check the provider's expected JSON. |
| No Changelog section | Push didn't add a `- ` bullet to `CHANGELOG.md` | Expected — add a changelog bullet in the same change. |
