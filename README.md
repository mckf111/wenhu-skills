# wenhu-skills

Wenhu 的 AI coding agent skills 合集。这个仓库用于收纳可复用的 Agent Skills，让不同 coding agent 在项目收尾、文档同步、代码审查等场景里有一致的工作方法。

## Skills

| Skill | 中文名 | 用途 | 路径 | 支持状态 |
| --- | --- | --- | --- | --- |
| `lucid` | 清爽 | 项目收尾检查：同步文档/记忆，并做 Git 只读安全审查 | `skills/lucid` | Codex、Claude Code、OpenCode |

## 安装

推荐使用自然语言安装。对支持从 GitHub 安装 skill 的 Agent，可以直接说：

```text
请从 https://github.com/mckf111/wenhu-skills/tree/main/skills/lucid 安装 lucid skill
```

如果需要手动安装，把 `skills/lucid` 整个目录复制到对应位置：

| Agent | 用户级安装路径 | 项目级安装路径 | 调用示例 |
| --- | --- | --- | --- |
| Codex | `~/.agents/skills/lucid` | `.agents/skills/lucid` | `用 $lucid 做项目收尾检查` |
| Claude Code | `~/.claude/skills/lucid` | `.claude/skills/lucid` | `/lucid` 或自然语言提到 `lucid` |
| OpenCode | `~/.config/opencode/skills/lucid`，也会读取 `~/.agents/skills/lucid` 和 `~/.claude/skills/lucid` | `.opencode/skills/lucid`，也会读取 `.agents/skills/lucid` 和 `.claude/skills/lucid` | `Use lucid to clean up this project handoff` |

其他 coding agent 如果不原生支持 Agent Skills，也可以把 `skills/lucid/SKILL.md` 作为项目规则、自定义命令或提示词引用。不要把这种手动引用当作正式兼容支持。

如果你的 Codex 环境仍使用旧的本地目录，也可以复制到 `~/.codex/skills/lucid` 或 `$CODEX_HOME/skills/lucid`；公开仓库文档优先写标准 Agent Skills 路径。

## lucid / 清爽

`lucid` 是一个项目收尾 skill，适合在一次开发结束、准备交接、准备提交前使用。它会帮助 Agent：

- 检查 README、docs、`AGENTS.md` / `CLAUDE.md` 是否与当前代码和会话事实一致。
- 清理过期、重复、膨胀的项目知识和 Agent 记忆。
- 做 Git 只读审查：工作区状态、diff 摘要、未跟踪文件、疑似敏感文件、建议提交分组和提交信息。
- 输出清爽报告：已处理、建议处理、风险、下一步。

`lucid` 默认不会执行 `commit`、`push`、`merge`、`rebase`、`reset`、删除分支、删除文件或开 PR。它只负责把项目收尾状态看清楚、说清楚，真正发布动作应由用户明确触发并交给专门的 Git/GitHub 工作流处理。

## 来源与许可

`lucid` 基于 [`neat-freak`](https://github.com/KKKKhazix/khazix-skills/tree/main/neat-freak) 的思路优化而来。主要变化是：

- 更保守的触发范围，避免普通“整理文件”误触发。
- 加入 Git 只读安全审查，但不自动提交或推送。
- README 面向公开仓库和多 Agent 安装方式重写。
- `SKILL.md` 与参考文件分层，便于后续扩展更多 skills。

本仓库使用 MIT License。

## 参考

- [Agent Skills specification](https://agentskills.io/specification)
- [Codex Agent Skills docs](https://developers.openai.com/codex/skills)
- [Claude Code skills docs](https://docs.anthropic.com/en/docs/claude-code/skills)
- [OpenCode skills docs](https://opencode.ai/docs/skills/)
