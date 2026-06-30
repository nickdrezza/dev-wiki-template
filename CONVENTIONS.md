# Conventions

How to work in this wiki. The audience is your team; treat the repo as private to the team
unless you've decided otherwise. The one rule that drives everything else: **file a doc by
what it _is_, not by what it's _about_.**

## Where things go

Pick the folder by document type, not topic:

| If the doc… | → folder |
|---|---|
| states a **rule we must follow** | `policies/` |
| **teaches a task** (incl. onboarding) | `guides/` |
| **describes a system we run** | `systems/` |
| says what to do **when something breaks / routine ops** | `runbooks/` |
| is a **quick lookup** (glossary, conventions, links) | `references/` |
| records **why we decided something** (ADR) | `decisions/` |
| is a **post-mortem / investigation** of something that broke | `incidents/` |
| is about the **wiki's own tooling** | `meta/` |

Tie-breakers:

- **policy vs guide** — a policy is *the rule*; a guide is *the steps to comply*.
- **guide vs runbook** — a guide is to *build or learn*; a runbook is to *operate or recover
  under pressure*.
- **guide vs incident** — an incident is the retrospective written *after* something broke.

## Source of truth for repo-specific docs

**Repo-specific docs live in the repo. This wiki links to them; it never copies them.** The
wiki owns only what *spans* repos or has *no single repo home* (how systems connect, shared
data flows, team-wide policies/guides, decisions).

Litmus when filing: **does this fact belong to exactly one repo?**

- **Yes** → it belongs in that repo's `README` / `docs/`. Link out from here; don't duplicate.
- **No** → the wiki owns it.

How it's encoded:

- [`systems/registry.yml`](systems/registry.yml) is the canonical catalog of the most-used
  systems — one entry per repo with a `docs:` link to the repo's own documentation (the
  source of truth). Add a system there rather than re-documenting it here.
- A `systems/<name>.md` page is written *only* when a system needs cross-repo prose. It must
  open with a "source of truth" banner pointing back to the repo, and cover only what spans
  repos — never setup/config/run instructions (those live in the repo).

## File conventions

- Name files `kebab-case.md`. A simple topic is one file; a system with sub-pages is a folder
  with an `index.md`.
- Every doc starts from [`_template.md`](_template.md). Required frontmatter:
  `title`, `description`, `owner`, `updated` (`YYYY-MM-DD`). `owner` is a person or team —
  **a doc with no owner rots.**
- ADRs are numbered `NNNN-slug.md`; incidents are dated `YYYY-MM-DD-slug.md`.
- Add a one-line entry to the folder's `README.md` index when you add a doc.

## Always update the changelog

When you add or meaningfully change content (or repo tooling/structure), add a dated bullet
to the **top** of [`CHANGELOG.md`](CHANGELOG.md) in the same change:

```
- **YYYY-MM-DD** — <what changed, in plain high-signal prose>
```

Most recent first. This is **curated prose, not an auto-generated commit log** — keep entries
high-signal and readable. The optional [chat merge notification](meta/chat-merge-notifications.md)
surfaces new changelog bullets on every push to `main`, so a good entry pays off twice.

If `main` moved while a pull request was open, the conflict is almost always in
[`CHANGELOG.md`](CHANGELOG.md) — resolve by keeping **both** bullets in date order (newest on
top), never by dropping one.

## Immutability

Never rewrite an existing ADR or incident to reflect a new reality. ADRs are superseded by a
new ADR; incidents are point-in-time history — link forward instead of editing.

## Writing style

- Open with the one thing a reader needs, then the detail.
- Prefer short, high-signal prose over exhaustive coverage. Link rather than repeat.
- Use tables for lookups and Mermaid for flows, as the example docs do.
