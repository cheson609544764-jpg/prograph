---
description: Project pre-analysis — map structure, optimize tokens, plan multi-agent strategy, and assign skills before implementation
argument-hint: Paste your project description or brief here
---

# ProGraph — Project Pre-Analysis Framework

You are helping a developer fully understand and prepare for a project BEFORE implementation begins. Your goal is to produce a clear mental map, optimize execution efficiency, and pre-configure the right tools.

## Core Principles

- **Deep understanding first**: Don't rush to solutions. Fully comprehend what the developer wants to build.
- **Ask before assuming**: If the project description is vague or incomplete, ask targeted questions to fill gaps.
- **Developer confirms each dimension**: Never proceed to the next dimension without explicit developer confirmation.
- **Output in developer's language**: Match the language the developer uses (Chinese/English/etc).

---

## Input

Developer's project description: $ARGUMENTS

---

## Dimension 1: Project Mind Map (思维导图)

**Goal**: Build a complete, layered understanding of the project's structure, logic flow, and dependencies.

**Actions**:

1. Read and deeply analyze the developer's project description
2. Identify the core goal, sub-goals, logical layers, and execution order
3. If the description is unclear or missing critical details, ask targeted questions:
   - What is the final deliverable?
   - What are the key constraints (tech stack, timeline, dependencies)?
   - Are there parts you're unsure about or want suggestions on?
   - What's the expected input/output for each major part?
4. Once all gaps are filled, produce a **text-based mind map** using this format:

```
📋 Project: [Name]
├── Part 1: [Name] — [simple/medium/complex]
│   ├── 1.1 [Sub-task]
│   ├── 1.2 [Sub-task]
│   └── Dependencies: [what it needs from other parts]
├── Part 2: [Name] — [simple/medium/complex]
│   ├── 2.1 [Sub-task]
│   └── 2.2 [Sub-task]
└── Part 3: [Name] — [simple/medium/complex]
    └── ...
```

5. Mark each part's complexity level: **simple** / **medium** / **complex**
6. Show dependencies and execution order between parts
7. **Ask developer to confirm**: "Does this mind map accurately represent your project? Any adjustments?"

**Wait for confirmation before proceeding to Dimension 2.**

---

## Dimension 2: Token Optimization Analysis (Token优化)

**Goal**: Identify opportunities to reduce token consumption without sacrificing project quality.

**Actions**:

1. For each part in the mind map, analyze:
   - Can boilerplate/repetitive code be generated with templates instead of full LLM generation?
   - Are there parts that can use shorter prompts with clear examples?
   - Can any parts reuse existing code/libraries instead of generating from scratch?
   - Are there parts where a smaller/faster model (like Haiku) is sufficient?
   - Can context be scoped more tightly for certain parts to avoid loading unnecessary files?

2. Present findings in a table:

| Part | Optimization Strategy | Estimated Token Savings | Quality Impact |
|------|----------------------|------------------------|----------------|
| Part 1 | [strategy] | ~X% reduction | None / Minimal |
| Part 2 | [strategy] | ~X% reduction | None / Minimal |

3. Provide total estimated savings
4. **Ask developer**: "Would you like to apply these optimizations? Which ones do you approve?"

**Wait for confirmation before proceeding to Dimension 3.**

---

## Dimension 3: Multi-Agent Strategy (多Agent协同)

**Goal**: Identify complex parts that benefit from parallel multi-agent execution to improve accuracy and coverage.

**Actions**:

1. Review all parts marked as **complex** in the mind map
2. For each complex part, evaluate:
   - Is there risk of a single agent missing important details?
   - Can the work be split into parallel perspectives (e.g., architecture + implementation + testing)?
   - Would adversarial verification (one agent builds, another reviews) improve quality?
   - Are there independent sub-tasks that can run simultaneously?

3. Present multi-agent recommendations:

| Complex Part | Recommended Agents | Agent Roles | Why Multi-Agent |
|-------------|-------------------|-------------|-----------------|
| Part X | 2-3 agents | Agent A: [role], Agent B: [role] | [reason] |

4. Explain trade-offs: more agents = better coverage but higher token cost
5. **Ask developer**: "Do you want to use multi-agent mode for these parts? Which ones?"

**Wait for confirmation before proceeding to Dimension 4.**

---

## Dimension 4: Skill/Tool Assignment (工具配备)

**Goal**: Pre-assign the most suitable skills and tools for each part of the project.

**Actions**:

1. For each part in the mind map, consider available skills:
   - `/feature-dev` — for structured feature development with codebase exploration
   - `/code-review` — for reviewing code quality after implementation
   - `/security-review` — for security-sensitive parts
   - `/deep-research` — for parts requiring external knowledge or research
   - `/verify` — for confirming features work correctly
   - `/simplify` — for post-implementation cleanup
   - `/init` — for new project setup
   - Custom workflows — for parts needing complex orchestration

2. Present skill assignments:

| Part | Recommended Skill/Tool | Reason |
|------|----------------------|--------|
| Part 1 | /feature-dev | Structured approach needed for complex feature |
| Part 2 | /deep-research + implementation | Requires external knowledge first |
| Part 3 | Basic implementation + /verify | Simple enough for direct coding |

3. For parts with no matching skill, suggest whether a custom approach or workflow is needed
4. **Ask developer**: "Do you approve these tool assignments? Any changes?"

---

## Final Output: Execution Plan

After all 4 dimensions are confirmed, produce a final execution plan:

```
=== ProGraph Execution Plan ===

Project: [Name]
Total Parts: [N]
Estimated Complexity: [Simple/Medium/Complex]

Execution Order:
1. [Part] — [skill] — [single/multi-agent] — [token optimization applied?]
2. [Part] — [skill] — [single/multi-agent] — [token optimization applied?]
...

Token Optimization: ~X% savings approved
Multi-Agent Parts: [list]
Skills Pre-loaded: [list]

Ready to begin implementation? (Y/N)
```

---

## Notes

- This skill is for ANALYSIS ONLY. Do not begin implementation until the developer explicitly says to start.
- If the developer changes their mind on any dimension, re-run that dimension.
- Keep all outputs concise but comprehensive.
- The mind map is the foundation — if it's wrong, everything else will be wrong. Get it right first.
