# ProGraph

A standard AI skill and Claude Code slash command for project planning before implementation and project auditing after implementation.

## Repository Structure

```text
prograph/
├── SKILL.md              # Standard skill entrypoint
├── agents/
│   └── openai.yaml       # Optional UI metadata for skill lists
├── prograph.md           # Claude Code slash command version
└── README.md             # Repository documentation
```

---

## English

### What it does

ProGraph has two modes:

1. **Preflight Mode** — Analyzes a project before coding with a mind map, token optimization plan, multi-agent strategy, and skill/tool assignments
2. **Audit Mode** — Reviews an existing project for actual structure, goal coverage, architecture risks, validation gaps, and next-step improvements

### Installation as a Skill

Copy this repository folder into your skills directory:

```bash
cp -R prograph ~/.codex/skills/prograph
```

### Installation as a Slash Command

Copy `prograph.md` to your Claude Code commands directory:

```bash
cp prograph.md ~/.claude/commands/prograph.md
```

### Usage

In any Claude Code conversation:

```
/prograph [your project description here]
```

For an existing project:

```
/prograph Audit this repository and tell me what is covered, risky, or missing
```

Preflight Mode is guided step by step. Audit Mode reads the project context first, then returns a concise report.

### Why use it

- Get a clear mental map before diving in
- Check whether a finished project actually matches its intended goal
- Save tokens by identifying optimizations upfront
- Avoid single-agent blind spots on complex tasks
- Pre-load or select the right tools for future work

---

## 中文

### 功能介绍

ProGraph 是一个标准 AI Skill，同时保留 Claude Code slash command 版本。它现在有两种模式：

1. **Preflight Mode / 开工前分析** — 在写代码前输出思维导图、Token 优化、多 Agent 策略和工具分配
2. **Audit Mode / 完成后检查** — 检查已有项目的实际结构、目标覆盖、架构风险、验证缺口和后续改进计划

### 作为 Skill 安装

将整个仓库目录复制到你的 skills 目录：

```bash
cp -R prograph ~/.codex/skills/prograph
```

### 作为 Slash Command 安装

将 `prograph.md` 复制到 Claude Code 的 commands 目录：

```bash
cp prograph.md ~/.claude/commands/prograph.md
```

### 使用方法

在任何 Claude Code 对话中输入：

```
/prograph [在这里粘贴你的项目描述]
```

检查已有项目时可以输入：

```
/prograph 检查这个仓库，告诉我完成度、风险和缺失项
```

Preflight Mode 会逐步引导，每个维度确认后再继续。Audit Mode 会先读取项目上下文，再输出一份简洁检查报告。

### 为什么用它

- 动手前就看清项目全貌，避免做到一半才发现结构混乱
- 做完后检查项目是否真正覆盖目标
- 提前识别可以省 token 的地方，减少不必要的开销
- 复杂任务用多 Agent 协同，降低遗漏风险
- 预选或重新分配合适工具，避免后续修复时浪费时间
