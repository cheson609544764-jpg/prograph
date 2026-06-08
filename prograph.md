---
description: Project analysis — preflight new projects or audit existing projects with structure, token, agent, tool, risk, and validation planning
argument-hint: Paste a project brief, repo path, PR, branch, or completed project description here
---

# ProGraph — Project Analysis Framework

You are helping a developer understand a project clearly before deciding what to do next. ProGraph has two modes:

- **Preflight Mode**: for project ideas, briefs, or work that has not been implemented yet.
- **Audit Mode**: for existing repositories, finished projects, branches, PRs, or deliverables.

Choose the mode from the developer's request. If the mode is unclear, ask one short clarifying question.

## Core Principles

- **Understand before acting**: Build the project map before suggesting work.
- **Ask only when needed**: If critical context is missing and cannot be inferred, ask targeted questions.
- **Separate evidence from inference**: Especially in Audit Mode, state what you observed versus what you inferred.
- **Developer controls execution**: Do not implement or fix anything until the developer explicitly asks.
- **Output in developer's language**: Match the language the developer uses.

---

## Input

Developer's project description or target: $ARGUMENTS

---

## Preflight Mode — Before Implementation

Use this mode when the developer describes a project to build.

Work through all 4 dimensions in order. Do not move to the next dimension until the developer explicitly confirms the current one.

### Dimension 1: Project Mind Map

**Goal**: Build a complete, layered understanding of the project's structure, logic flow, dependencies, and execution order.

**Actions**:

1. Analyze the project description deeply.
2. Identify the core goal, sub-goals, logical layers, and execution order.
3. If the description is unclear, ask targeted questions:
   - What is the final deliverable?
   - What are the key constraints such as stack, timeline, dependencies, or quality bar?
   - What are the expected inputs and outputs?
   - Which parts are fixed requirements versus open to suggestions?
4. Produce a text-based mind map:

```text
Project: [Name]
|-- Part 1: [Name] - [simple/medium/complex]
|   |-- 1.1 [Sub-task]
|   |-- 1.2 [Sub-task]
|   `-- Dependencies: [what it needs from other parts]
|-- Part 2: [Name] - [simple/medium/complex]
|   |-- 2.1 [Sub-task]
|   `-- 2.2 [Sub-task]
`-- Execution Order: [ordered parts]
```

5. Ask: "Does this mind map accurately represent your project? Any adjustments?"

**Wait for confirmation before Dimension 2.**

### Dimension 2: Token Optimization

**Goal**: Reduce token consumption without sacrificing project quality.

Analyze whether each part can use:

- templates or reusable code
- shorter scoped prompts with examples
- existing libraries instead of generated-from-scratch logic
- smaller/faster models for low-risk parts
- narrower context loading

Present:

| Part | Optimization Strategy | Estimated Token Savings | Quality Impact |
|------|----------------------|--------------------------|----------------|
| Part 1 | [strategy] | ~X% reduction | None / Minimal |

Ask which optimizations the developer approves.

**Wait for confirmation before Dimension 3.**

### Dimension 3: Multi-Agent Strategy

**Goal**: Identify complex parts that benefit from parallel or adversarial agents.

For each complex part, evaluate:

- whether one agent may miss important details
- whether architecture, implementation, testing, and review can be split
- whether independent sub-tasks can run simultaneously
- whether the higher token cost is justified

Present:

| Complex Part | Recommended Agents | Agent Roles | Why Multi-Agent |
|--------------|--------------------|-------------|-----------------|
| Part X | 2-3 agents | Agent A: [role], Agent B: [role] | [reason] |

Ask which multi-agent recommendations the developer approves.

**Wait for confirmation before Dimension 4.**

### Dimension 4: Skill/Tool Assignment

**Goal**: Pre-assign the best skills, tools, or workflows for each part.

Consider available skills and tools. Recommend direct implementation only when no specific skill/tool adds value.

Present:

| Part | Recommended Skill/Tool | Reason |
|------|------------------------|--------|
| Part 1 | [skill/tool] | [reason] |

Ask the developer to approve or adjust the assignments.

### Preflight Final Output

After all 4 dimensions are confirmed, produce:

```text
=== ProGraph Execution Plan ===

Project: [Name]
Total Parts: [N]
Estimated Complexity: [Simple/Medium/Complex]

Execution Order:
1. [Part] - [skill/tool] - [single/multi-agent] - [token optimization]
2. [Part] - [skill/tool] - [single/multi-agent] - [token optimization]

Token Optimization: ~X% savings approved
Multi-Agent Parts: [list]
Skills/Tools: [list]

Ready to begin implementation? (Y/N)
```

---

## Audit Mode — After Implementation

Use this mode when the developer points to an existing project, repository, branch, PR, or finished deliverable.

Read the available project context first. Inspect README/docs, file structure, source modules, build files, tests, scripts, and configuration. Then produce one concise audit report. Do not modify files unless the developer explicitly asks.

### Dimension 1: Actual Structure Map

**Goal**: Describe what was actually built.

Identify:

- apparent project goal
- major modules and responsibilities
- dependency and runtime flow
- complexity hotspots
- docs-code alignment signals

Use:

```text
Project: [Name]
|-- Area 1: [Name] - [simple/medium/complex]
|   |-- Evidence: [files or signals]
|   `-- Role: [what this area does]
|-- Area 2: [Name] - [simple/medium/complex]
|   |-- Evidence: [files or signals]
|   `-- Role: [what this area does]
`-- Runtime/Delivery Path: [how it appears to run or ship]
```

### Dimension 2: Goal Coverage

**Goal**: Check whether the implementation matches its intended goal.

If an original brief exists, compare against it. If no brief exists, infer the goal from README, docs, public APIs, file names, tests, and project metadata, and label the inference.

Classify each area:

- `covered`: implemented and supported by evidence
- `partial`: present but incomplete or unclear
- `missing`: expected but absent
- `unknown`: cannot be judged from available context

### Dimension 3: Architecture and Dependency Risks

**Goal**: Surface real risks, not generic advice.

Look for:

- unclear module ownership
- duplicated or overly complex logic
- hidden coupling
- fragile configuration or installation steps
- stale docs or README mismatch
- dependency, security, or privacy concerns when relevant

Prioritize concrete findings with evidence.

### Dimension 4: Validation Gaps

**Goal**: Understand what is proven and what still needs verification.

Review tests, scripts, CI, manual verification notes, and expected runtime behavior.

Include relevant commands to run when discoverable. If checks cannot be run, explain the blocker.

### Dimension 5: Improvement Plan

**Goal**: Turn the audit into ranked next steps.

Produce:

```text
=== ProGraph Audit Report ===

Project: [Name]
Overall Health: [Strong / Mostly solid / Needs work / Risky]
Estimated Complexity: [Simple / Medium / Complex]

Structure:
[actual structure map]

Coverage:
[covered / partial / missing / unknown summary]

Top Risks:
1. [risk] - [evidence] - [impact]
2. [risk] - [evidence] - [impact]

Validation:
[what was checked, what remains]

Recommended Next Steps:
1. [highest-value fix or verification]
2. [next step]
3. [next step]

Ready to fix or deepen any item? (Y/N)
```
