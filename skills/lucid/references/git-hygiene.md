# Git Hygiene Review

Lucid performs read-only Git review. It should make the working tree understandable without publishing it.

## Allowed Commands

Use read-only commands such as:

- `git status -sb`
- `git branch --show-current`
- `git remote -v`
- `git diff --stat`
- `git diff --name-status`
- `git diff -- <path>`
- `git ls-files --others --exclude-standard`
- `git log --oneline -5`

Do not stage, commit, push, reset, merge, rebase, delete branches, delete files, or create PRs.

## Review Checklist

Inspect and report:

- Current branch and whether it looks like a default branch.
- Tracked changed files and their rough purpose.
- Untracked files and whether they look intentional.
- Large generated artifacts that may not belong in source control.
- Possible secrets or local-only config files.
- Unrelated changes mixed into the same working tree.

## Sensitive Patterns

Treat these as risks to report, not things to fix silently:

- `.env`, `.env.*`, credentials, secrets, tokens, keys, private certificates.
- Files containing names like `token`, `secret`, `password`, `credential`, `private`.
- Local absolute paths that reveal machine details.
- Private repository URLs or internal hostnames.
- Large binaries, archives, database dumps, and build outputs.

## Commit Advice

When the tree is coherent, suggest:

- A commit group theme.
- The exact files that appear to belong in that group.
- A short commit message in imperative or conventional style.

When the tree is mixed, do not force a single commit. Recommend separate groups and identify which files need user confirmation.
