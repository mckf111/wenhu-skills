---
name: lucid
description: Project handoff and pre-commit cleanup for coding agents. Use when the user explicitly asks for "$lucid", "lucid", "清爽", "收尾", "整理一下", "同步一下", "commit 前整理", "交付前检查", "clean handoff", or a similar project-milestone cleanup where docs, agent memory, and Git working-tree status need to be reviewed together. Do not trigger for ordinary file organization, generic code optimization, publishing, CI fixing, or requests to commit/push unless the user also asks for cleanup review.
---

# Lucid / 清爽

Use this skill to make a project handoff clear before the next person or agent touches it. Keep the work grounded in evidence: inspect the repository, update only the knowledge that is stale or missing, and report Git risks without performing Git publishing actions.

Lucid is based on the cleanup philosophy of `neat-freak`, with a narrower trigger surface and an added Git hygiene review. It is a cleanup reviewer and knowledge editor, not a release bot.

## Non-Negotiable Safety Boundary

Never run mutating Git or destructive commands as part of this skill:

- No `git commit`, `git push`, `git merge`, `git rebase`, `git reset`, branch deletion, tag deletion, or PR creation.
- No deletion of files merely because they look stale. Report the candidate and ask for explicit user approval or leave it as "建议处理".
- No staging files. Do not run `git add`.
- No broad formatter or codegen commands that rewrite tracked files unless the user explicitly requested that separate work.

Allowed Git actions are read-only inspection: status, branch, remotes, diff summaries, file lists, and log snippets.

## Workflow

1. Define the cleanup scope.
   - Identify the current project root and whether the request is a docs/memory cleanup, a pre-commit review, or both.
   - If multiple repositories are involved, inspect each one separately and report cross-project dependencies.

2. Inventory the knowledge layer.
   - List project markdown files: `README.md`, `AGENTS.md`, `CLAUDE.md`, `docs/**/*.md`, and obvious equivalents.
   - Read the files that can be affected by the current work. Do not edit every markdown file by default.
   - For agent memory, use the platform's available mechanism. If no memory system exists, focus on project markdown and docs.
   - Read `references/knowledge-cleanup.md` for cleanup rules and `references/sync-matrix.md` when deciding which docs should change.

3. Reconcile docs and memory.
   - Prefer updating existing sections over appending new historical notes.
   - Remove or consolidate only content that is clearly made obsolete by current repository facts.
   - Use absolute dates when dates matter.
   - Keep project rules in `AGENTS.md` / `CLAUDE.md`; keep user-facing and operator-facing explanations in README or docs.

4. Run Git hygiene review.
   - Read `references/git-hygiene.md` before interpreting the working tree.
   - Inspect status, branch, remotes, tracked diff summary, untracked files, and likely sensitive files.
   - Group changes into suggested commit scopes, but do not stage or commit them.
   - If unrelated or user-owned changes are present, call them out instead of folding them into the suggested commit group.

5. Validate the cleanup.
   - Confirm edited links and paths exist when practical.
   - Search for relative time words such as "today", "recently", "最近", "今天", "昨天" in files you touched.
   - Re-check Git status after edits so the final report reflects the real state.

6. Report clearly.
   - Use the report format below.
   - Mention any skipped action and why.
   - If the user wants commit/push after the review, say that it is outside Lucid's default boundary and should be handled as a separate explicit Git workflow.

## Report Format

```markdown
## 清爽完成

### 已处理
- <file or area> — <what changed and why>

### Git 审查
- Branch: <branch>
- Changes: <tracked/untracked summary>
- Suggested commit group: <files or theme>
- Suggested commit message: <message>

### 风险
- <secret/untracked/unrelated/large-file/path risk, or "未发现明显风险">

### 建议下一步
- <next action, without performing commit/push>
```

If no files were changed, say so directly and still provide the Git review if requested.

## Reference Files

- `references/knowledge-cleanup.md`: docs and memory cleanup rules.
- `references/git-hygiene.md`: read-only Git review rules and sensitive-file checks.
- `references/sync-matrix.md`: map project changes to documentation updates.
