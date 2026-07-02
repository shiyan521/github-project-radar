# GitHub Project Radar

A lightweight Codex skill for people who collect too many GitHub repos and need a durable review workflow.

It turns repo links into a small decision record:

- Is this a duplicate?
- Is it worth using?
- Is it worth publishing or teaching?
- Does it need installation testing?
- Should it be archived?

## Files

- `SKILL.md`: the reusable skill.
- `assets/candidate-table-template.md`: starter candidate table.
- `references/review-checklist.md`: review and install-test checklist.

## Recommended Workflow

1. Paste repo links into a thread.
2. Normalize each link to `owner/repo`.
3. Check the local candidate table.
4. Assign one tier: `use`, `publish`, `test`, or `archive`.
5. Only install-test repos that truly need verification.
6. Write the decision back to the table.

## Repository Strategy

This package is designed to live in its own GitHub repository.

Do not mix it into an unrelated repo unless it is part of a larger skill library.

## License

MIT.

