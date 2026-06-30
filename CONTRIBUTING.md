# Contributing

Thanks for adding to the wiki. Good docs are a team effort — this guide covers the workflow.
The *conventions* themselves (where docs go, frontmatter, naming) live in
[`CONVENTIONS.md`](CONVENTIONS.md); read that first.

## The workflow

1. **Branch.** Create a branch off `main`; don't commit directly to `main`.
2. **Write the doc.**
   - Decide the document *type* and put it in the matching folder (see the table in
     [`CONVENTIONS.md`](CONVENTIONS.md)).
   - Copy [`_template.md`](_template.md) and fill in the frontmatter — `title`, `description`,
     `owner`, `updated` (today's date, `YYYY-MM-DD`). **Every doc needs an owner.**
   - Name the file `kebab-case.md`.
3. **Wire it in (same change):**
   - Add a one-line entry to the folder's `README.md` index (match the existing bullet style:
     link + em-dash + one-line description).
   - Add a dated bullet to the **top** of [`CHANGELOG.md`](CHANGELOG.md).
4. **Open a pull request.** Keep it focused; explain the *why* in the description. Get a
   review before merging.

## Quality bar

- **Open with the one thing a reader needs**, then the detail. High-signal prose beats
  exhaustive coverage.
- **Link, don't duplicate.** If a fact belongs to exactly one code repo, link to that repo
  rather than copying it here (see "source of truth" in [`CONVENTIONS.md`](CONVENTIONS.md)).
- **Check your links.** Use relative links between docs so they work on GitHub and in local
  editors alike.
- **Keep frontmatter honest.** When you meaningfully edit a doc, bump its `updated` date.

## Editing existing docs

- Updating a guide, system, policy, reference, or runbook? Edit it in place and bump `updated`.
- **ADRs and incidents are immutable.** Don't rewrite them to reflect a new reality — write a
  new ADR that supersedes the old one, or link an incident forward. They're history.

## Reporting gaps without writing the doc

Spotted something missing or out of date but can't fix it now? Add a bullet to
[`GAPS.md`](GAPS.md), or open an issue using one of the templates. That's a real contribution
too.

## Code of conduct

Participation is governed by our [Code of Conduct](CODE_OF_CONDUCT.md). Be kind and specific.
