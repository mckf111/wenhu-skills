# Sync Matrix

Use this matrix when deciding which docs should change after project work.

## Code Or Project Change To Docs

| Change | Update |
| --- | --- |
| New public command or workflow | README usage section and project agent rules if agents must know it |
| New API, route, or protocol | Integration docs and architecture docs |
| New environment variable | README setup, operations/runbook docs, and agent rules if it affects development |
| New database table or schema concept | Architecture or data model docs |
| New deployment or infrastructure behavior | Operations/runbook docs |
| New cross-project contract | Both producer and consumer docs |
| Renamed concept | README/docs terminology and any quick-reference tables |
| Removed feature | Delete or update stale docs; do not leave "kept for history" notes unless the user asked |

## Anti-Bloat Checks

Before adding text to `AGENTS.md` or `CLAUDE.md`, ask:

- Would a future coding agent make a bad code change without this rule?
- Is this a durable rule rather than a one-session note?
- Does README or docs already explain this for humans?

If the answer is no, do not add it there.

## Cross-Project Checks

If a change affects consumers, SDKs, shared config, authentication, or deployment contracts, search dependent projects or docs before declaring cleanup done.

Report any dependent project that could not be inspected.
