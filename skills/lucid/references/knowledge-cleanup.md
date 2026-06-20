# Knowledge Cleanup Rules

Use these rules when Lucid needs to update project docs, agent memory, or handoff notes.

## Audience Split

Keep each knowledge layer focused:

| Layer | Audience | Belongs here |
| --- | --- | --- |
| `AGENTS.md` / `CLAUDE.md` | Future coding agents in this repo | Hard rules, project boundaries, commands, pitfalls |
| `README.md` | New human or agent visitors | What the project is, how to install/run/use it |
| `docs/` | Maintainers and integrators | Architecture, integration details, operations, handoff |
| Agent memory | The current agent across sessions | User preferences, cross-project facts, non-obvious lessons |

Do not use `AGENTS.md` or `CLAUDE.md` as a changelog. If a note is only "what happened last session", prefer Git history, a changelog, or no persistent note.

## Cleanup Rules

- Prefer editing existing content over appending a new section.
- Prefer deleting or merging obsolete notes over preserving them as history.
- Keep rule files short enough to obey; long narratives reduce adherence.
- Use absolute dates when dates matter.
- Do not invent docs for an empty or experimental directory with no durable project facts.
- If a memory or note has become stable project knowledge, promote it into README/docs and shrink or remove the memory note.

## What To Add

Add or update persistent knowledge when missing it would cause a future agent or maintainer to make a wrong decision:

- Required commands or environment setup.
- Real project boundaries, such as "only write database queries in this layer".
- Supported public interfaces and integration points.
- Known footguns with concrete prevention rules.
- Current architecture or operational facts that are visible in the code.

## What Not To Add

Avoid adding:

- Session diary entries.
- One-off bug narratives.
- "Recently", "today", or "now" phrasing.
- Pointers that duplicate an existing docs index.
- Speculative future plans unless the user asked for a roadmap.

## Minimal Verification

After editing docs or memory:

- Check that mentioned paths exist.
- Check that referenced commands still match the repo.
- Search touched files for stale relative time words.
- Re-read the edited section for audience fit.
