---
name: sop-forge
description: Convert unfamiliar-domain work into standardized, verifiable, AI-executable, and automatable SOPs. Use when a task is complex, multi-step, repetitive, expert-driven, unfamiliar, or intended for eventual agent automation.
---

# SOP Forge

## Purpose

SOP Forge is a workflow-compilation process.

Given an unfamiliar or complex task, do not jump directly to execution. First reconstruct how competent practitioners perform the work, extract the decision logic, formalize the process as a Human SOP and AI-Executable SOP, test it, and only then agentize or automate it.

## Operating principle

```
Goal
→ Domain Research
→ Workflow Discovery
→ Expert Process Reconstruction
→ Task Decomposition
→ Decision Rule Extraction
→ Human SOP
→ AI-Executable SOP
→ Simulation
→ Verification
→ Agentization
→ Automation
→ Feedback
→ SOP Update
```

## Phase 1 — Goal Definition

Before research, define:

- Objective
- Context
- Constraints
- Inputs
- Expected output
- Success criteria
- Non-goals
- Risk level

If the goal or success criteria are ambiguous, resolve that ambiguity before building the SOP.

## Phase 2 — Minimum Viable Domain Model

Research enough domain knowledge to understand the task, not the entire field.

Prefer:

1. Primary sources
2. Official documentation
3. Expert procedures
4. High-quality worked examples
5. Failure cases

For important claims, preserve evidence and source provenance.

Output:

- Key concepts
- Important entities
- Required terminology
- Relevant standards
- Common workflows
- Known constraints
- Important exceptions

## Phase 3 — Expert Process Reconstruction

Reverse-engineer the process used by competent practitioners.

For every workflow, identify:

- Trigger
- Inputs
- Preparation
- Actions
- Decisions
- Quality checks
- Output
- Exceptions
- Dependencies
- Heuristics
- Red flags
- Quality signals

Use:

```
Trigger → Input → Preparation → Step → Decision → Quality Check → Output
```

Do not invent expert behavior when evidence is missing. Mark uncertain steps as assumptions and verify them.

## Phase 4 — Task Decomposition

Split the workflow into atomic tasks.

Every task should have:

```
Input
Process
Decision
Output
Verification
```

A task is too broad if its completion cannot be objectively checked.

## Phase 5 — Decision Rule Extraction

Translate tacit judgment into explicit rules.

Prefer:

```
IF <condition>
THEN <action>
BECAUSE <reason>
EVIDENCE <required evidence>
EXCEPT <exception>
```

Also define:

- Continue conditions
- Stop conditions
- Retry conditions
- Escalation conditions
- Confidence requirements

When a judgment cannot be safely formalized, create a human checkpoint rather than pretending it is deterministic.

## Phase 6 — Human SOP

Write the process so a competent human can execute it without reconstructing the method from scratch.

Include:

- Purpose
- Preconditions
- Required tools
- Inputs
- Procedure
- Decision points
- Quality checks
- Common failures
- Exceptions
- Escalation rules
- Output requirements

## Phase 7 — AI-Executable SOP

Convert the Human SOP into an explicit execution contract.

Minimum schema:

```yaml
task:
inputs:
preconditions:
steps:
decision_rules:
exceptions:
quality_checks:
human_checkpoints:
stop_conditions:
output:
evidence_requirements:
```

AI instructions must specify not only what to do, but also:

- What not to do
- When not to continue
- When to verify
- When to ask for clarification
- What evidence is required
- What constitutes completion

## Phase 8 — Simulation

Before production:

1. Run a normal case.
2. Run an ambiguous case.
3. Remove or corrupt an important input.
4. Test an exception.
5. Test a known failure mode.
6. Test an adversarial case.
7. Check whether the SOP produces a deterministic next action.

Record failures as test cases.

## Phase 9 — Verification

Use independent verification for high-impact or high-uncertainty outputs.

Recommended pattern:

```
Executor → Independent Verifier → Critic → Finalizer
```

The verifier should not simply repeat the executor's reasoning. It should independently check:

- Evidence
- Calculations
- Preconditions
- Decision rules
- Output format
- Safety / permission boundaries
- Whether the task actually reached its success criteria

## Phase 10 — Agentization

Use separate agents where responsibility boundaries are meaningful.

Suggested roles:

- Orchestrator
- Research Agent
- Analysis Agent
- Execution Agent
- Verification Agent
- Critic Agent
- Human Escalation

Define permissions explicitly:

```
Read
Search
Create
Modify
Execute
Decide
Spend
Publish
Escalate
```

High-impact actions should default to a human checkpoint until sufficient evidence exists that the workflow is stable.

## Phase 11 — Automation

Promote the workflow gradually:

- L0 — Manual
- L1 — AI Assisted
- L2 — AI Executes + Human Review
- L3 — Conditional Automation
- L4 — Autonomous Workflow

Only automate stable paths. Route exceptions to humans.

## Phase 12 — Feedback Loop

Every production failure should be classified:

- Missing knowledge
- Bad workflow decomposition
- Incorrect decision rule
- Missing exception
- Tool failure
- Verification failure
- Ambiguous requirement
- Permission boundary failure

Then:

```
Failure
→ Root Cause
→ Rule / SOP Change
→ Version
→ Simulation
→ Verification
→ Production
```

Never silently patch an execution prompt when the underlying SOP is wrong. Update the source-of-truth SOP.

## Final SOP Forge Report

Return:

```
# SOP Forge Report

## 1. Objective
## 2. Minimum Domain Model
## 3. Workflow Map
## 4. Human SOP
## 5. AI-Executable SOP
## 6. Decision Rules
## 7. Exceptions
## 8. Verification
## 9. Agent Architecture
## 10. Human Checkpoints
## 11. Automation Level
## 12. Risks / Unknowns
## 13. Failure Cases
## 14. Next Optimization
## 15. Version
```

## Quality gate

Do not declare a workflow automation-ready unless:

- The objective is testable.
- Inputs and outputs are defined.
- Major workflow steps are explicit.
- Important decisions have rules or human checkpoints.
- Exceptions are documented.
- Completion can be verified.
- At least one dry run has been performed.
- High-impact claims/actions have an appropriate verification path.
- Agent permissions are bounded.
- Failure feedback can update the SOP version.

## Core rule

**Do not ask AI to repeatedly solve the same complex task from scratch. Discover the process once, formalize it, verify it, and turn the stable process into an executable system.**
