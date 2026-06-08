---
name: prograph
description: Use this skill to analyze a software project before or after implementation. In Preflight Mode, build a project mind map, optimize token usage, plan multi-agent work, assign skills/tools, and produce a confirmed execution plan before coding. In Audit Mode, inspect an existing project for structure, goal coverage, architecture risks, redundant complexity, validation gaps, and follow-up improvements. Trigger when the user wants structured project planning, implementation preparation, project review, project audit, delivery check, task decomposition, or a ProGraph-style plan.
---

# ProGraph

ProGraph is a project analysis workflow with two modes:

- **Preflight Mode**: Use before implementation to plan the work.
- **Audit Mode**: Use after implementation to inspect what was built.

Choose the mode from the user's request. If they describe an idea, brief, or future build, use Preflight Mode. If they point to an existing repository, finished project, branch, PR, or deliverable, use Audit Mode. If the mode is unclear, ask one short clarifying question.

Match the user's language throughout.

## Preflight Mode

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

### Preflight Final Output

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

## Audit Mode

Use Audit Mode to inspect an existing project. Read the repository or artifact first, then produce one concise audit report. Do not modify files unless the user explicitly asks for fixes.

### 1. Actual Structure Map

Inspect the project layout, README/docs, package/build files, source folders, tests, and configuration. Identify:

- what the project appears to be
- major modules and responsibilities
- dependency and execution flow
- complexity hotspots

Use this text format:

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

### 2. Goal Coverage

Compare the implementation against the original goal when available. If no original brief is available, infer the goal from README, docs, file names, tests, and public interfaces, and clearly mark that inference.

Classify each major area:

- `covered`: implemented and supported by evidence
- `partial`: present but incomplete or unclear
- `missing`: expected but absent
- `unknown`: cannot be judged from available context

### 3. Architecture and Dependency Risks

Look for risks such as:

- unclear ownership boundaries
- duplicated or overly complex logic
- hidden coupling between modules
- fragile configuration or installation steps
- stale docs or docs-code mismatch
- security, privacy, or dependency concerns when relevant

Prioritize concrete, evidence-backed risks over generic advice.

### 4. Validation Gaps

Review tests, scripts, CI, manual verification notes, and expected runtime behavior. Identify what is already validated and what still needs proof.

Include the most relevant commands to run when they are discoverable. If tests cannot be run, explain the blocker.

### 5. Improvement Plan

Produce a ranked follow-up plan:

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

## Guardrails

- This skill is for analysis, planning, and auditing only.
- Do not begin implementation or fixes until the user explicitly asks to start.
- Keep outputs concise but complete.
- In Preflight Mode, if the mind map changes, revisit later dimensions that depend on it.
- In Audit Mode, separate evidence from inference.
