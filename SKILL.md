---
name: prograph
description: Use this skill to pre-analyze a software project before implementation by building a project mind map, identifying token optimizations, planning multi-agent work, assigning skills/tools, and producing a confirmed execution plan. Trigger when the user wants structured project planning, implementation preparation, preflight analysis, task decomposition, or a ProGraph-style plan before coding.
---

# ProGraph

ProGraph is a pre-implementation analysis workflow. Use it before writing code when the user wants a clear project map, execution strategy, token budget plan, and skill/tool assignments.

## Workflow

Work through the four dimensions in order. Match the user's language. Do not move to the next dimension until the user explicitly confirms the current one.

### 1. Project Mind Map

Analyze the project description and identify:

- core goal and final deliverable
- major parts, sub-tasks, and dependencies
- complexity for each part: `simple`, `medium`, or `complex`
- recommended execution order

If key information is missing, ask targeted questions before producing the map.

Use this text format:

```text
Project: [Name]
|-- Part 1: [Name] - [simple/medium/complex]
|   |-- 1.1 [Sub-task]
|   |-- 1.2 [Sub-task]
|   `-- Dependencies: [what it needs]
|-- Part 2: [Name] - [simple/medium/complex]
|   |-- 2.1 [Sub-task]
|   `-- 2.2 [Sub-task]
`-- Execution Order: [ordered parts]
```

Ask: "Does this mind map accurately represent your project? Any adjustments?"

### 2. Token Optimization

For each part, identify ways to reduce token usage without reducing quality:

- reusable templates or existing code
- smaller scoped prompts
- libraries instead of generated-from-scratch logic
- smaller/faster models for low-risk parts
- tighter context loading

Present a concise table with part, strategy, estimated savings, and quality impact. Ask which optimizations the user approves.

### 3. Multi-Agent Strategy

Review complex parts and decide whether parallel or adversarial agents would improve coverage.

Recommend agents only when they add real value. Include roles, why multiple agents help, and the token cost trade-off. Ask which multi-agent recommendations the user approves.

### 4. Skill/Tool Assignment

Assign the best available skill, tool, or workflow to each part. Explain why each assignment fits. For parts without a matching skill, propose a direct custom workflow.

Ask the user to approve or adjust the assignments.

## Final Output

After all four dimensions are confirmed, produce:

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

## Guardrails

- This skill is for analysis and planning only.
- Do not begin implementation until the user explicitly asks to start.
- Keep outputs concise but complete.
- If the mind map changes, revisit later dimensions that depend on it.
