# Team Wiki Template

> A lightweight, plain-Markdown knowledge base for engineering and data teams — the
> "how we build and operate" handbook, kept in Git.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![PRs welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![Docs: Markdown](https://img.shields.io/badge/docs-Markdown-blue.svg)](#how-its-organized)

It's just Markdown files in a Git repo, filed by **what a document is**, with a small set of
conventions that keep the knowledge findable, owned, and current. No database, no hosted
service, no lock-in — your wiki lives next to your code and travels with it.

This repository is a **template**. Generate your own wiki from it, delete the example docs,
and start writing.

## Why a wiki like this

- **Lives next to the work.** Same tools as code — branches, pull requests, review, history.
- **Filing by document type scales.** "Where does this go?" has one answer, so the wiki stays
  navigable as it grows past a handful of pages.
- **Ownership fights decay.** Every doc names an `owner` and an `updated` date, so staleness
  is visible instead of silent.
- **Durable and portable.** Plain text outlives any single tool.
- **Optional, not required, automation.** A built-in GitHub Action announces every merge to
  your team chat — turn it on with one secret, or ignore it.

## Quickstart — use this template

1. **Create your repo.** Click **“Use this template”** on GitHub (or clone this repo and point
   it at a new remote).
2. **Make it yours.**
   - Set the copyright holder in [`LICENSE`](LICENSE) (or swap the license).
   - Edit this `README.md` to describe *your* team's wiki.
   - Adjust the folder set and tie-breakers in [`CONVENTIONS.md`](CONVENTIONS.md) if your team
     files things differently — the structure is a strong default, not a cage.
3. **Clear the examples.** Delete the sample docs in each folder (keep each folder's
   `README.md` index), reset [`CHANGELOG.md`](CHANGELOG.md), and empty [`GAPS.md`](GAPS.md).
4. **Write your first real doc.** Copy [`_template.md`](_template.md) into the right folder,
   fill in the frontmatter, add it to the folder index, and add a `CHANGELOG.md` bullet.
5. **(Optional) Turn on merge notifications.** Add a `CHAT_WEBHOOK_URL` secret — see
   [`meta/chat-merge-notifications.md`](meta/chat-merge-notifications.md).

## How it's organized

Documents are filed by **what they are**, not by topic. Pick the folder that matches:

| Folder | What lives here | Read it to… |
|---|---|---|
| [`policies/`](policies/) | The rules — standards the team must follow | know the rule |
| [`guides/`](guides/) | How-to instructions & onboarding | learn to do a task |
| [`systems/`](systems/) | Reference docs for the systems you run | understand how something works |
| [`runbooks/`](runbooks/) | What to do when something breaks, and routine ops | operate / recover |
| [`references/`](references/) | Glossary, conventions, cheat-sheets, links | look something up |
| [`decisions/`](decisions/) | ADRs — why you chose what you chose | understand a past decision |
| [`incidents/`](incidents/) | Post-mortems & investigations — what broke and what you learned | learn from a past incident |

[`meta/`](meta/) documents the wiki itself (tooling, conventions).
[`notebooks/`](notebooks/) is personal scratch space — one folder per person, no template or
review bar. [`GAPS.md`](GAPS.md) tracks open questions not yet documented.

**Not sure where something goes?** policy = the rule, guide = the steps to comply.
guide = build/learn, runbook = operate/recover under pressure.

## Contributing

The short version: put the doc in the right folder, start from [`_template.md`](_template.md),
add it to the folder's `README.md` index, and add a dated bullet to the top of
[`CHANGELOG.md`](CHANGELOG.md) — all in one pull request. Full conventions are in
[`CONVENTIONS.md`](CONVENTIONS.md); the contribution workflow is in
[`CONTRIBUTING.md`](CONTRIBUTING.md).

## Automation

An optional GitHub Action ([`.github/workflows/notify-chat-on-merge.yml`](.github/workflows/notify-chat-on-merge.yml))
posts to a team chat space on every push to `main` — the merge headline, new changelog
bullets, and changed files. It works with any chat provider that accepts an incoming webhook;
set up is one repository secret. See [`meta/chat-merge-notifications.md`](meta/chat-merge-notifications.md).

## Editing in Obsidian (optional)

The repo is plain Markdown, so any editor works. [Obsidian](https://obsidian.md) is a nice
fit — open the repo as a vault for fast search, backlinks, and a file tree. The vault config
(`.obsidian/`) is intentionally **not** committed (see [`.gitignore`](.gitignore)); keep your
editor setup local.

## License

[MIT](LICENSE) — free to use, adapt, and share.
