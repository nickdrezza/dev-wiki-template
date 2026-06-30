# Using this wiki in Obsidian

This wiki is plain Markdown, so **any** editor works — VS Code, vim, GitHub's web UI, or just
a text editor. But [Obsidian](https://obsidian.md) is an especially nice fit: it turns the
repo into a fast, linked, searchable knowledge base without changing a single file or adding
any dependency. This guide covers a comfortable setup.

> Obsidian is optional. Nothing here is required to use the wiki, and none of it changes how
> the docs render on GitHub.

## Open the repo as a vault

A "vault" is just a folder Obsidian manages. To open this repo as one:

1. Install Obsidian.
2. **Open folder as vault** → pick this repository's folder.
3. That's it — every Markdown file shows up in the left-hand file explorer.

Obsidian stores its per-vault settings in a `.obsidian/` folder. **This repo intentionally
git-ignores `.obsidian/`** (see [`.gitignore`](.gitignore)), so your editor setup stays local
and personal — it never lands in commits or affects teammates.

## Why it's a good fit

- **Instant search** — `Ctrl/Cmd+Shift+F` searches the full text of every doc.
- **Quick switcher** — `Ctrl/Cmd+O` jumps to any doc by name.
- **Backlinks & graph** — see which docs link to the one you're reading, and visualize how the
  wiki connects.
- **Properties view** — the frontmatter (`title`, `description`, `owner`, `updated`) shows up
  as editable properties at the top of each note.
- **Mermaid built in** — the diagrams in docs like
  [`systems/example-data-pipeline.md`](systems/example-data-pipeline.md) render automatically.
- **Outline** — the heading outline of long docs, for quick navigation.

Most of these are **core plugins** (built in). Enable them under
**Settings → Core plugins**: *Quick switcher, Search, Backlinks, Outgoing links, Outline,
Tags view, Properties view, Templates*.

## Keep links GitHub-compatible

This is the one setting that matters. The wiki uses **standard Markdown links**
(`[label](path/to/doc.md)`) so docs render correctly on GitHub. Obsidian can instead insert
its own `[[wikilinks]]`, which **do not render on GitHub**. To keep everything portable:

- **Settings → Files & Links**
  - **Use [[Wikilinks]]** → **off**
  - **New link format** → **Relative path to file**

Now any link you create in Obsidian also works on GitHub and in every other Markdown viewer.

## Use the doc template

Wire up [`_template.md`](_template.md) so new docs start with the right frontmatter:

1. **Settings → Core plugins → Templates** → enable it.
2. **Settings → Templates → Template folder location** → set it to the repo root (or move
   `_template.md` into a folder you point at).
3. When creating a doc, run **Insert template** (command palette: `Ctrl/Cmd+P` → "Insert
   template") and fill in the frontmatter.

Then file it per [`CONVENTIONS.md`](CONVENTIONS.md): put it in the folder matching its type,
add it to that folder's `README.md` index, and add a bullet to [`CHANGELOG.md`](CHANGELOG.md).

## Saving your changes (Git)

Obsidian edits files on disk but doesn't do Git. Commit your work the normal way:

- **From a terminal** — `git add`, `git commit`, and open a pull request (see
  [`CONTRIBUTING.md`](CONTRIBUTING.md)). This is the recommended path.
- **From inside Obsidian (optional)** — the community **Obsidian Git** plugin can stage and
  commit on a schedule or with a hotkey, if you'd rather not leave the app. It's a personal
  convenience and, like the rest of `.obsidian/`, isn't part of this repo.

## Tips

- Treat [`notebooks/`](notebooks/) as your Obsidian scratch space — drafts and working notes
  with no template or review bar. Promote anything durable into the right folder later.
- Use the **graph view** filtered to a folder to spot orphaned docs (nothing links to them).
- The **Tags view** works if you add `tags:` to frontmatter, though this template keeps
  frontmatter minimal by default.
