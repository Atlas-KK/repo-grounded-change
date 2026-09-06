---
name: repo-grounded-change
description: "Evaluate changes to an existing repository using code evidence, real tradeoffs, and observable acceptance criteria. Use when the user asks to assess first, compare options, or confirm before implementation, or when inspection reveals an unresolved choice with material product, compatibility, or scope consequences. Do not invoke for clear direct implementation requests without such a choice, PRD creation, review-only audits, or security-only assessment."
---

# Repo-grounded Change

Ground changes in repository facts, resolve only consequential decisions, and implement within the user's existing authorization. Scale the workflow to the task; a new confirmation is not a default prerequisite.

## Choose the lightest sufficient mode

- **Direct execution:** A clear implementation request already authorizes the requested work. Do not automatically invoke this skill for it. If explicitly invoked or already loaded, inspect the relevant code, implement, and verify without requiring options or a separate approval. Choose routine implementation details yourself.
- **Brief assessment:** A bounded change needs a small amount of investigation or one consequential decision. Explain the evidence and recommendation briefly. Proceed if the request already authorizes it; ask only for a missing decision. If the user requested assessment only, deliver the assessment without editing.
- **Full proposal:** The user requests alternatives or a plan before execution, or the change involves substantial unresolved behavior, compatibility, migration, or scope tradeoffs. Prepare a concrete recommendation and relevant acceptance criteria before seeking any missing authorization. Existing approval can authorize a complex implementation; complexity alone does not require another gate.

Mode selection is internal routing, not an extra question for the user. Load only the references needed for the selected mode.

## Authorization and scope

- Current explicit user instructions and confirmed decisions take precedence over this workflow. Track their scope across turns; do not ask again merely because implementation starts, a phase changes, or a reference mentions approval.
- A direct request to make a specific change authorizes that change. A request to evaluate or propose first authorizes investigation and a proposal, not implementation. Praise, discussion, or silence does not grant missing authorization.
- An approved outcome includes ordinary implementation choices needed to achieve it. It does not automatically authorize unrelated cleanup, destructive data changes, new external actions, or materially different behavior.
- When a new fact creates a consequential unresolved choice, pause only the dependent work. Complete independent, authorized investigation or implementation that will not prejudge that choice or require avoidable rework.
- Before asking, inspect available evidence, check prior authorization, and consider an in-scope alternative. Ask about the actual remaining decision, not generic permission to continue.

## Ground the decision

Inspect the smallest repository surface needed to explain the behavior and impact. Do not ask the user for facts discoverable from code, tests, configuration, or applicable product documents. For cross-module or compatibility-sensitive changes, read [references/discovery-and-impact.md](references/discovery-and-impact.md).

Keep user goals, code facts, approved document requirements, technical recommendations, and product assumptions distinct. Use explicit labels only where they prevent ambiguity; do not emit a fixed evidence taxonomy in every response. Source inspection is not runtime or visual verification.

Resolve conflicts using this order, exposing material contradictions:

1. Current explicit user instructions.
2. Decisions explicitly confirmed in the current task.
3. Applicable approved product specifications.
4. Current code and tests as evidence of existing behavior.
5. README files and historical documents.

Existing behavior is evidence, not automatically the desired product behavior.

## Recommend and resolve decisions

State the observable outcome, relevant code boundaries, and meaningful consequences. Present alternatives only when real tradeoffs require a decision; a single justified recommendation is sufficient otherwise. For genuine alternatives or unresolved choices, read [references/options-and-clarification.md](references/options-and-clarification.md).

Scale the specification to the change. A bounded fix may need one sentence of target behavior and a focused check. For full proposals or changes involving persisted state, interfaces, or migrations, read [references/change-spec-and-acceptance.md](references/change-spec-and-acceptance.md).

If authorization is missing, make the recommendation concrete and reviewable before asking the smallest necessary question. Wait for the answer before dependent edits. If already authorized, implement without an additional approval round. After a decision, report only new conclusions or changes that affect execution; do not repeat the entire baseline each turn.

## Implement and verify

- Recheck the dirty worktree before editing and preserve unrelated user changes. Make the smallest coherent implementation of the authorized outcome.
- Removing a UI presentation does not authorize deleting underlying domain data. Handle historical persisted values when repository evidence indicates they may exist.
- Derive observable acceptance from the requested behavior. If evidence is missing, first investigate or design an appropriate check; ask only when a user decision is needed to define success.
- Run focused checks and broaden proportionately to the affected contracts and regression risk. Tests should verify meaningful behavior, not mirror implementation. Small reversible changes do not require new tests solely to satisfy this workflow.
- If a check is unavailable, seek a suitable alternative and disclose its limits. Honor an explicitly required validation environment; do not silently substitute it or claim equivalent coverage. A validation gap does not by itself require another approval for independent authorized work.
- Report the result, relevant files, verification evidence, and material limitations. Completion requires implementing the authorized outcome and performing applicable checks; disclose any incomplete required validation instead of claiming full completion.

## When a user decision is necessary

Ask only when available evidence and existing authorization leave a consequential decision unresolved, such as:

- alternatives differ materially in product behavior, data compatibility, or scope;
- a dependency, integration, migration, or business-rule change introduces consequences outside the authorized baseline, such as recurring cost, external data transfer, a new service, breaking compatibility, or data loss;
- overlapping user edits cannot be preserved safely after inspection;
- new repository facts make the authorized outcome infeasible or require changing its acceptance criteria;
- completion requires a material expansion of scope or an undefined product success criterion.

A new helper, file, ordinary dependency within the authorized technical approach, longer duration, or implementation difficulty is not alone a reason to ask. These rules do not replace actual execution permissions or authorize destructive or external actions.

## Behavioral regression cases

When revising this skill or investigating over-triggering, use [references/behavioral-cases.md](references/behavioral-cases.md). These cases test routing and authorization decisions; do not load them during ordinary repository work.
