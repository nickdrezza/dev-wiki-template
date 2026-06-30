---
title: Restart a stuck job
description: Diagnose and safely restart a scheduled job that is hung, failed, or late.
owner: Platform team
updated: 2026-01-11
---

# Restart a stuck job

**Use when** a scheduled job (e.g. the [example data pipeline](../systems/example-data-pipeline.md))
is failed, hung, or hasn't finished by its expected time.

## 1. Confirm it's actually stuck

- Check the job's status in the scheduler/dashboard. Is it running, failed, or queued?
- Check the run logs for the last message. A job still emitting progress is slow, not stuck —
  give it time before intervening.

## 2. Find the cause before restarting

- **Failed with an error** → read the error. Upstream/source outage? Bad input? Permissions?
- **Hung with no progress** → likely a stuck connection or a lock. Note the start time.
- **Late but healthy** → a dependency upstream is probably late; check it first.

## 3. Restart safely

1. Confirm the job is **idempotent** for the affected run (re-running won't double-write). If
   it isn't, clean up the partial output first.
2. Cancel the stuck run so it doesn't conflict with the retry.
3. Re-trigger the run for the affected date/window.
4. Watch the logs through the first checkpoint to confirm it's making progress.

## 4. After recovery

- Confirm downstream consumers got the expected data.
- If this wasn't a one-off (recurring hang, unclear root cause, customer impact), write it up
  in [`incidents/`](../incidents/) so the fix outlives the memory of it.
