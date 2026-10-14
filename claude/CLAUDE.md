# CLAUDE.md

## 语言（最高优先）

**始终用中文回复我**，包括进度更新、总结、提问和思考过程里给用户看的部分；不要说英文。英文只用于代码、命令、提交信息，以及必须用英文写的信件正文（正文后附中文大意）。

Behavioral guidelines to reduce common LLM coding mistakes. Merge with project-specific instructions as needed.

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment.

## 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

## 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

## 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:
- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.

When your changes create orphans:
- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: Every changed line should trace directly to the user's request.

## 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:
```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

---

**These guidelines are working if:** fewer unnecessary changes in diffs, fewer rewrites due to overcomplication, and clarifying questions come before implementation rather than after mistakes.

---

## 第二大脑 / Wiki Knowledge Base

我有一个持久知识库(Obsidian + claude-obsidian 插件,PARA 模式):**`~/SecondBrain`**。
它存着所有项目的"记忆"(目标、决策、踩坑)和蒸馏出的知识。

**当本项目里缺少你需要的上下文时,按这个顺序读(省 token):**
1. 先读 `~/SecondBrain/wiki/hot.md`(最近上下文,~500 字)
2. 不够再读 `~/SecondBrain/wiki/index.md`(全量目录)
3. 要项目/领域细节,读对应页:`wiki/projects/<名>.md`、`wiki/areas/<名>.md`
4. 最后才读具体 wiki 页面

**在某个项目里干活时**,优先读该项目对应的 `wiki/projects/<项目名>.md`。

**完成有价值的工作后**,可主动把新决策/踩坑/结论更新进对应项目页,并刷新 `hot.md`,让记忆复利累积。

**写库纪律(防增生)**:
- `hot.md` 是**覆盖式缓存**(≤500字),只留最近 1-2 条;历史一律进 `log.md`(新条目在最上)。
- **项目页只留参考信息**(目标/架构/命令/踩坑/当前状态/待办),**不堆逐日进展**;日记式内容直接写进 `log.md`。项目页超 ~300 行就该压缩归档。
- 更新页面时同步改 frontmatter 的 `updated:`;通用经验(跨项目可复用的坑)抽成 `resources/` 知识卡并从项目页双链。
- 改动后 `git add -A && git commit && git push`(远程建议用私有仓库，如 `<你的GitHub用户名>/SecondBrain`)。

**不要为这些去读知识库**:通用编程/语法问题、本项目文件或对话里已有的信息、与该项目领域无关的任务。

> 读写优先用 `mcp-obsidian`(需 Obsidian 开着);连不上就直接用文件读写 `~/SecondBrain/`。

## 浏览器

- 打开网址一律用 **Chrome**（Claude in Chrome，`mcp__claude-in-chrome__*` 工具，我的登录态都在那），**不要用右边的内置浏览器**（`mcp__Claude_Browser__*`）。
- 例外：预览本机 dev server（localhost）仍可用内置浏览器的 preview_start。
