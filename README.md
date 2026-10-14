# Claude Code + Codex 配置模板

一套可以直接抄的 Claude Code 个人配置：中文回复、写代码的行为准则、分层编码规范、Obsidian「第二大脑」记忆、Claude 写代码 + Codex 交叉审查。

## 目录

```
claude/
  CLAUDE.md                  → 放到 ~/.claude/CLAUDE.md（全局指令，所有项目生效）
  settings.example.json      → 参考着合并进 ~/.claude/settings.json
  rules/                     → 放到 ~/.claude/rules/（编码规范，自动加载）
    common/                  通用：代码风格、git、测试、安全、性能、开发流程
    typescript/ python/ golang/ kotlin/ php/ perl/   各语言补充
    codex-review.md          Claude ↔ Codex 交叉审查流程
codex/
  AGENTS.md                  → 放到 ~/.codex/AGENTS.md（Codex 的全局指令）
```

## 安装

```bash
mkdir -p ~/.claude ~/.codex
cp claude/CLAUDE.md ~/.claude/CLAUDE.md
cp -R claude/rules ~/.claude/rules
cp codex/AGENTS.md ~/.codex/AGENTS.md
```

已经有这些文件的话，**先备份再合并**，别直接覆盖。`settings.example.json` 不要整个替换 `~/.claude/settings.json`，挑需要的段落合并进去。

只用某几种语言的话，`rules/` 下不用的语言目录可以删掉；`common/` 必须保留（各语言规则会引用它）。

## 装完要改的地方

1. **不用 Obsidian 第二大脑**：删掉 CLAUDE.md 里「第二大脑」那一节，以及 codex/AGENTS.md 的前半部分。要用的话，先装插件 `claude-obsidian`（已在 settings 示例里），在 `~/SecondBrain` 建库。
2. **不用 Codex**：删掉 `rules/codex-review.md` 和 settings 里的 `codex@openai-codex`。要用的话先装 Codex CLI 并登录，然后在 Claude Code 里跑 `/codex:setup`。
3. **浏览器那一节**：默认让 Claude 用 Chrome 扩展（Claude in Chrome）开网页。没装扩展就删掉这一节。
4. **语言**：不想要中文回复就改「语言」那一节。

## 注意

- **权限**：`settings.example.json` 里的 `permissions.allow` 是**全部放行**（`Bash(*)` 等），Claude 执行命令不再逐条询问。效率高，但风险自担；新手建议删掉这一段，用默认的逐条确认。
- `rules/common/` 和各语言目录来自开源项目 everything-claude-code，可以去原仓库拿最新版。
- 这份模板不含任何账号、密钥、记忆文件和本机路径；MCP 服务器配置因为和本机路径绑定，也没放进来。
