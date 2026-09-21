# SOP Forge

**Turn unfamiliar work into AI-executable SOPs and automatable workflows.**

SOP Forge is a methodology and reusable AI Skill for converting complex, unfamiliar-domain work into a process that can be researched, decomposed, verified, executed by agents, and continuously improved.

It is designed for people who do not want AI to merely "answer questions", but want AI to **discover how the work should be done, turn that method into an SOP, and then automate the SOP**.

## Core idea

```text
Unfamiliar domain
      ↓
AI research
      ↓
Expert workflow reconstruction
      ↓
Task decomposition
      ↓
Decision-rule extraction
      ↓
Human SOP
      ↓
AI-Executable SOP
      ↓
Simulation / verification
      ↓
Agent execution
      ↓
Automation
      ↓
Feedback
      ↓
SOP version update
      ↺
```

The key transformation is:

> **Tacit expert knowledge → explicit workflow → executable procedure → automated workflow**

## Why SOP Forge?

Using multiple AI agents does not automatically make complex work reliable.

The difficult part is usually upstream:

- What is the actual goal?
- What does an expert really do?
- Which steps are essential?
- Which decisions require judgment?
- What evidence is sufficient?
- What are the common failure modes?
- When should an AI continue, stop, verify, or ask a human?
- Which parts can safely be automated?

SOP Forge treats these questions as an engineering problem.

## Workflow

### 1. Goal Definition

Define:

- Objective
- Context
- Constraints
- Inputs
- Expected outputs
- Success criteria
- Non-goals

Do not start by asking AI to "solve the task". First define what a successful result means.

### 2. Domain Research

Research only the minimum domain knowledge required to perform the task.

Prioritize:

1. Primary sources
2. Official documentation
3. Expert workflows
4. High-quality examples
5. Failure cases and edge cases

The goal is not to become a domain expert. The goal is to build a **minimum viable domain model** that is sufficient to reconstruct the workflow.

### 3. Expert Workflow Reconstruction

Reverse-engineer how competent practitioners perform the work.

Capture:

- Trigger
- Inputs
- Preparation
- Actions
- Decisions
- Quality checks
- Outputs
- Exceptions
- Hidden dependencies
- Heuristics
- Red flags
- Quality signals

Represent the workflow as:

```text
Trigger
  → Input
  → Preparation
  → Step
  → Decision
  → Quality Check
  → Output
```

### 4. Task Decomposition

Break the workflow into atomic units.

Each task should define:

```text
Input
Process
Decision
Output
Verification
```

A task is too large if an agent cannot clearly determine what evidence proves it is complete.

### 5. Decision Rule Extraction

Convert fuzzy expert judgment into explicit rules whenever possible.

Examples:

```text
IF condition
THEN action

IF evidence is insufficient
THEN research more

IF confidence is below threshold
THEN escalate to human

IF output fails quality check
THEN revise and re-run
```

Record exceptions separately instead of hiding them inside vague instructions.

### 6. Human SOP

Create a readable SOP for humans.

A Human SOP should answer:

- What is the standard process?
- What tools are required?
- What should be checked?
- What can go wrong?
- What decisions require judgment?
- When should the operator escalate?

### 7. AI-Executable SOP

Translate the Human SOP into a machine-oriented procedure.

It should explicitly define:

- Inputs
- Preconditions
- Steps
- Decision rules
- Exceptions
- Verification
- Human checkpoints
- Stop conditions
- Output schema
- Evidence requirements

Example:

```yaml
task: research-and-compare
inputs:
  - user_goal
  - candidate_sources

preconditions:
  - goal_is_defined
  - required_sources_are_accessible

steps:
  - collect_primary_sources
  - extract_relevant_facts
  - normalize_information
  - compare_against_criteria

decision_rules:
  - if: evidence_conflicts
    then: flag_for_review
  - if: evidence_is_insufficient
    then: research_more

quality_checks:
  - every_major_claim_has_evidence
  - output_matches_requested_schema

human_checkpoints:
  - before_high_impact_action
```

See [examples/minimal-ai-sop.yaml](examples/minimal-ai-sop.yaml).

### 8. Simulation

Never move directly from SOP design to production automation.

Run dry-runs against:

- Normal cases
- Ambiguous cases
- Missing-input cases
- Adversarial cases
- Failure cases
- Boundary cases

Ask a separate critic process to attack the SOP.

### 9. Verification

Verification should focus on the claims and actions with the highest:

```text
Impact × Uncertainty
```

Do not waste the same verification budget on trivial and high-consequence steps.

### 10. Agentization

Split execution by responsibility rather than creating one giant agent.

A typical architecture:

```text
Orchestrator
├── Research Agent
├── Analysis Agent
├── Execution Agent
├── Verification Agent
├── Critic Agent
└── Human Escalation
```

Define permission boundaries explicitly:

```text
Can Read
Can Search
Can Create
Can Modify
Can Execute
Can Decide
Can Spend
Can Publish
Can Escalate
```

### 11. Automation

Move from manual operation to automation gradually:

| Level | Mode |
|---|---|
| L0 | Manual |
| L1 | AI-assisted |
| L2 | AI executes + human review |
| L3 | Conditional automation |
| L4 | Autonomous workflow |

Do not automate a process that has not yet become stable and verifiable.

### 12. Feedback and Versioning

Production execution should feed the SOP.

```text
Execution
  ↓
Failure / Exception
  ↓
Root-cause analysis
  ↓
Rule update
  ↓
SOP version
  ↓
Simulation
  ↓
Verification
  ↓
Production
```

An SOP is not a static document. It is a versioned operational artifact.

## Knowledge base structure

A practical knowledge base can use:

```text
Knowledge/
├── Domain Knowledge/
├── Workflows/
├── Human SOP/
├── AI SOP/
├── Decision Rules/
├── Examples/
├── Failure Cases/
├── Validation Records/
├── Agent Prompts/
├── Tool Configurations/
└── SOP Versions/
```

## SOP Forge output

For a new workflow, the final deliverable should contain:

1. Objective
2. Minimum domain model
3. Workflow map
4. Human SOP
5. AI-Executable SOP
6. Decision rules
7. Exceptions
8. Verification plan
9. Agent architecture
10. Human checkpoints
11. Automation level
12. Risks and unknowns
13. Failure cases
14. Next optimization
15. SOP version

## When to use SOP Forge

Use it when:

- The domain is unfamiliar.
- The work is multi-step.
- The work contains expert judgment.
- The process repeats.
- Multiple tools or agents are involved.
- Errors are costly.
- You eventually want automation.

It is less useful for:

- Simple factual questions
- One-off trivial tasks
- Tasks with no meaningful workflow
- Work where the desired output is purely creative and cannot be operationally evaluated

## Positioning

SOP Forge is not another prompt library.

It is a **workflow compiler**:

```text
Human intent
    ↓
Domain model
    ↓
Workflow
    ↓
Decision rules
    ↓
SOP
    ↓
Executable SOP
    ↓
Agents
    ↓
Automation
```

The long-term goal is to make complex human work progressively more **explicit, verifiable, executable, and automatable**.

## License

MIT. See [LICENSE](LICENSE).
