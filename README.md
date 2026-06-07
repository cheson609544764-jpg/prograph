# ProGraph

A Claude Code skill for comprehensive project pre-analysis before implementation.

---

## English

### What it does

ProGraph analyzes your project from 4 dimensions before you start coding:

1. **Mind Map** — Breaks down the project into a layered structure with complexity ratings and dependencies
2. **Token Optimization** — Identifies ways to reduce token usage without sacrificing quality
3. **Multi-Agent Strategy** — Recommends parallel agent execution for complex parts
4. **Skill/Tool Assignment** — Pre-assigns the best available skills for each part

### Installation

Copy `prograph.md` to your Claude Code commands directory:

```bash
cp prograph.md ~/.claude/commands/prograph.md
```

### Usage

In any Claude Code conversation:

```
/prograph [your project description here]
```

Then follow the guided analysis — each dimension requires your confirmation before proceeding.

### Why use it

- Get a clear mental map of your project before diving in
- Save tokens by identifying optimizations upfront
- Avoid single-agent blind spots on complex tasks
- Pre-load the right tools so you don't waste time mid-project

---

## 中文

### 功能介绍

ProGraph 在你开始写代码之前，从 4 个维度对项目进行全面分析：

1. **思维导图** — 将项目拆解为分层结构，标注每个部分的复杂度和依赖关系
2. **Token 优化** — 找出可以节省 token 但不影响质量的方法，给出预估节省比例
3. **多 Agent 协同** — 对复杂部分推荐多个 Agent 并行执行，避免单 Agent 遗漏关键信息
4. **工具配备** — 为每个部分预先分配最合适的 skill/工具，附带推荐理由

### 安装

将 `prograph.md` 复制到 Claude Code 的 commands 目录：

```bash
cp prograph.md ~/.claude/commands/prograph.md
```

### 使用方法

在任何 Claude Code 对话中输入：

```
/prograph [在这里粘贴你的项目描述]
```

按照引导逐步分析，每个维度都需要你确认后才会进入下一步。

### 为什么用它

- 动手前就看清项目全貌，避免做到一半才发现结构混乱
- 提前识别可以省 token 的地方，减少不必要的开销
- 复杂任务用多 Agent 协同，降低遗漏风险
- 预装合适的工具，避免中途切换浪费时间
