# Personal Second Brain

Personal vault: `~/SecondBrain`

## Default context

At the start of work in any project other than the vault itself, silently read
`~/SecondBrain/wiki/hot.md`. Use it only when it is relevant to
the request; do not crawl the vault or repeat its contents to the user.

For work related to an existing project, then read
`wiki/index.md` and the matching page under `wiki/projects/`, plus only the
directly relevant area or resource pages.

## Keep the brain current

When the user begins or creates a real, durable project (not an experiment,
throwaway folder, or one-off question), ensure it has a page in
`~/SecondBrain/wiki/projects/`. Create or update that page with
the goal, repository/path, current state, key decisions, risks, and next steps.
Then update `wiki/projects/_index.md`, `wiki/index.md`, `wiki/hot.md`, and
`wiki/log.md` as appropriate.

Before writing to the vault, read its local `AGENTS.md` and follow its locking,
frontmatter, privacy, and address-allocation rules. Never record secrets,
credentials, private keys, access tokens, or personal data not needed for the
project summary.

When a project gains a reusable lesson, add or update a concise page under
`wiki/resources/` and link it from the relevant project pages.

## 与 Claude Code 的 Code Review 分工

当你（Codex）被 Claude Code 通过 MCP 或 `codex exec` 调用做 code review 时：

- **只审不改**：只输出问题清单和修改建议，不要修改任何文件、不要执行写操作。
- 建议格式：每条给出 `文件:行号`、问题描述、建议改法、严重级（CRITICAL / HIGH / MEDIUM / LOW）。
- 改文件由 Claude Code 逐条复核确认后执行；之后 Claude Code 会把修改结果发回给你**二审**——二审时对照你上一轮的清单，逐条确认已修复/未修复/新引入问题。
- 不确定是不是真问题的，标注「存疑」并说明验证方法，不要硬凑数量。

**唯一例外**：用户本人直接让你改文件时，不受此限。
