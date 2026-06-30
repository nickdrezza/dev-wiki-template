# Team Wiki Template

A lightweight, plain-Markdown knowledge base for an engineering or data team — the
"how we build and operate" handbook. It's just Markdown files in a Git repo, filed by
**what a document is**, with a small set of conventions that keep it findable and current.

This is an open-source **template**. Use it as the starting point for your team's wiki:
generate a repo from it, delete the example docs, and start writing your own.

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
[`notebooks/`](notebooks/) is personal scratch space — one folder per person, no template or review bar.
[`GAPS.md`](GAPS.md) tracks open questions and knowledge gaps not yet documented.

**Not sure where something goes?** policy = the rule, guide = the steps to comply.
guide = build/learn, runbook = operate/recover under pressure.

## Contributing

1. Put the doc in the right folder (table above) and name it `kebab-case.md`.
   A system with sub-pages gets its own folder with an `index.md`.
2. Start from [`_template.md`](_template.md) — every doc needs frontmatter
   (`title`, `description`, `owner`, `updated`).
3. Add a dated bullet to the top of [`CHANGELOG.md`](CHANGELOG.md) in the same change.
4. Add a one-line entry to the folder's `README.md` index.

Full conventions live in [`CLAUDE.md`](CLAUDE.md).

## Automation

An optional GitHub Action posts to a team chat space on every push to `main` — the merge
headline, new changelog bullets, and changed files. See
[`meta/chat-merge-notifications.md`](meta/chat-merge-notifications.md) to wire it up.

## Editing in Obsidian (optional)

The repo is plain Markdown, so any editor works. [Obsidian](https://obsidian.md) is a nice
fit — open the repo as a vault for fast search, backlinks, and a file tree. The vault config
(`.obsidian/`) is intentionally **not** committed; keep your editor setup local.

## License

[MIT](LICENSE). Free to use, adapt, and share.
