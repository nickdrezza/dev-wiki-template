---
title: 2026-01-15 — Nightly pipeline outage (example)
description: Fictional post-mortem demonstrating the incident format — the nightly pipeline silently produced stale analytics tables.
owner: Data team
updated: 2026-01-16
---

# 2026-01-15 — Nightly pipeline outage (example)

> This is a **fictional example** included to demonstrate the post-mortem format. Replace it
> with real incidents.

**Summary:** the nightly [example data pipeline](../systems/example-data-pipeline.md) appeared
to succeed but published **stale** analytics tables for one day. Dashboards showed the prior
day's numbers until it was caught mid-morning.

- **Impact:** ~10 hours of stale analytics; no data loss; no customer-facing outage.
- **Severity:** medium.
- **Detected by:** an analyst noticing a dashboard number hadn't moved.

## Timeline (all times UTC)

- **02:00** — Nightly run starts.
- **02:14** — Transform step reads the raw layer, but the loader had silently written **zero**
  new rows (upstream export was empty). The transform "succeeds" on stale data.
- **02:15** — Run reports success. No alert fires.
- **11:40** — Analyst reports a flat dashboard.
- **12:05** — On-call confirms the raw layer was empty for the run; re-runs the loader against
  a now-complete upstream export.
- **12:30** — Pipeline re-run completes; analytics tables refreshed; dashboards correct.

## Root cause

The pipeline treated an **empty load as success**. The transform had no freshness or
row-count check, so zero new rows flowed through as "valid," and success masked the problem.

## What went well

- Idempotent re-run made recovery a single clean retry.
- The analyst's instinct caught it before any external impact.

## What went wrong

- No freshness/row-count guard on the load.
- Success was reported without validating that data actually moved.

## Action items

- [ ] Add a **row-count / freshness check** after the load; fail the run if the raw layer is
      empty or unchanged. *(owner: Data team)*
- [ ] Alert on a failed or zero-row nightly run, not just on exceptions. *(owner: Platform team)*
- [ ] Add the freshness check to the [restart runbook](../runbooks/restart-a-stuck-job.md)'s
      "after recovery" step. *(owner: Data team)*
