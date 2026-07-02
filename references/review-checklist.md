# Review Checklist

## Deduplication

- Normalize to `owner/repo`.
- Remove `.git`.
- Remove `/tree/...`, `/blob/...`, and README subpaths.
- Ignore query strings for identity.

## Tiering

Use `use` when the repo could improve the user's own workflow.

Use `publish` when the repo has a clear story, demo, or audience pain.

Use `test` when the repo is promising but needs install or runtime verification.

Use `archive` when the repo is duplicate, stale, too narrow, or not relevant.

## Install-Test Gate

Only test one repo at a time.

Before testing, record:

- why the test is needed
- expected visible result
- install command source
- rollback or cleanup notes

Stop after two repeated failures with the same error.

