---
name: github-project-radar
description: Dedupe, tier, test, and record GitHub project candidates before deciding whether to use, publish, test, or archive them. Use when a user collects GitHub repositories and wants a lightweight review workflow instead of another bookmark pile.
---

# GitHub Project Radar

Use this skill when GitHub repositories are arriving faster than they can be judged.

The goal is not to summarize every README. The goal is to prevent duplicate collection, separate "useful" from "publishable", and keep a durable local record.

## Inputs

- One or more GitHub repository URLs.
- Optional notes about where the repo came from.
- Optional target audience or use case.
- A local candidate table, if one already exists.

## Workflow

1. Normalize the repository key.
   - Use `owner/repo` as the primary key.
   - Treat `.git`, `/tree/...`, `/blob/...`, query strings, and README links as the same repo.

2. Check for duplicates.
   - If the repo already exists, update `last_seen`.
   - Do not create a second candidate row.
   - Add a `revisit_note` only when there is a genuinely new angle.

3. Decide the tier.
   - `use`: worth trying in the user's own workflow.
   - `publish`: worth turning into content, demo, or teaching material.
   - `test`: promising but must be installed or verified first.
   - `archive`: low-value, duplicate, stale, too narrow, or not relevant.

4. Decide the next action.
   - `record-only`
   - `install-test`
   - `content-brief`
   - `revisit-later`
   - `archive`

5. Write the result back to the candidate table.

## Output

For each repo, output:

- `repo`
- `canonical_url`
- `duplicate?`
- `one_line_summary`
- `why_it_matters`
- `tier`
- `next_action`
- `review_notes`

Use the template in `assets/candidate-table-template.md` when no table exists.

## Review Rules

- Do not treat stars as proof of usefulness.
- Do not install a repo just because it looks interesting.
- Do not turn every repo into content.
- Do not let duplicate links occupy new candidate slots.
- If installation is needed, test one repo at a time.
- If installation fails twice in the same way, stop and diagnose before retrying.

## Evidence Bar

Before marking a repo as `use` or `publish`, check at least three of:

- README clearly explains the outcome.
- Recent commits or releases show maintenance.
- Installation path is plausible.
- The result can be demonstrated visually or with a short example.
- It maps to a real user pain.
- It is meaningfully different from existing tools in the user's stack.

## Safety

Do not run install scripts, remote commands, credential setup, or destructive commands without explicit confirmation.

