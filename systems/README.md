# Systems

Reference docs for the systems the team runs. The **source of truth for how each system
works is the system's own repo** — [`registry.yml`](registry.yml) is the canonical catalog
that links out to it. Only write a `systems/<name>.md` page when a system needs cross-repo
prose (how it connects to others); never copy a repo's setup/config here.

- [`registry.yml`](registry.yml) — catalog of the systems we run, one entry per repo.
- [Example data pipeline](example-data-pipeline.md) — how the nightly ingest connects source data, the warehouse, and downstream consumers.
