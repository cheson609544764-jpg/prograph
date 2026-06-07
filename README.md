# ProGraph

A Claude Code skill for comprehensive project pre-analysis before implementation.

## What it does

ProGraph analyzes your project from 4 dimensions before you start coding:

1. **Mind Map (思维导图)** — Breaks down the project into a layered structure with complexity ratings and dependencies
2. **Token Optimization (Token优化)** — Identifies ways to reduce token usage without sacrificing quality
3. **Multi-Agent Strategy (多Agent协同)** — Recommends parallel agent execution for complex parts
4. **Skill/Tool Assignment (工具配备)** — Pre-assigns the best available skills for each part

## Installation

Copy `prograph.md` to your Claude Code commands directory:

```bash
cp prograph.md ~/.claude/commands/prograph.md
```

## Usage

In any Claude Code conversation:

```
/prograph [your project description here]
```

Then follow the guided analysis — each dimension requires your confirmation before proceeding.

## Why use it

- Get a clear mental map of your project before diving in
- Save tokens by identifying optimizations upfront
- Avoid single-agent blind spots on complex tasks
- Pre-load the right tools so you don't waste time mid-project
