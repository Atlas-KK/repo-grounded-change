---
name: repo-grounded-change
description: "Evaluate and implement changes to an existing repository through a confirmation gate: inspect current behavior, clarify the user pain point, compare feasible options and impacts, produce a Codex-ready modification plan with acceptance criteria, and edit code only after explicit approval. Use for code, UI, interaction, refactoring, or architecture improvements when the user asks to assess first, propose alternatives, or confirm before execution. Do not use for direct implementation with no material design choice, PRD creation, review-only audits, or security-only assessment."
---

# Repo-grounded Change

Turn an optimization request for an existing project into a confirmed, implementation-ready change and then execute only the approved option.

## Interaction and authorization contract

- Inspect the current repository before recommending a solution. Do not ask the user for facts discoverable from code, tests, configuration, or applicable product documents.
- Remain read-only until the user explicitly approves an option or modification baseline. Diagnostics and repository inspection do not authorize edits.
- Do not force this workflow onto a direct, unambiguous implementation request. Use the gate when the user asks for evaluation first or when a choice materially affects behavior, compatibility, risk, or scope.
- Ask only decision-bearing questions. Use a structured user-input control when available; otherwise use concise option codes such as `Q1-A`.
- Normally provide 2 or 3 mutually exclusive feasible options. Put the recommended option first and explain why. If only one safe option exists, explain why the alternatives were rejected instead of inventing fake choices.
- After confirmation, implement the selected option without silently adding unrelated cleanup. If new repository facts would materially change the approved behavior, scope, migration, dependency, or acceptance criteria, stop and ask for a revised decision.

## Evidence and decision labels

Keep facts separate from interpretation:

- `用户目标`: the pain point and outcome stated by the user.
- `代码事实`: behavior observed in current source, tests, runtime, or configuration.
- `文档事实`: behavior required by the applicable approved product document.
- `技术建议`: an implementation recommendation that preserves the intended product behavior.
- `产品假设`: a reversible assumption that requires confirmation.
- `待确认`: an unresolved choice that prevents implementation.
- `已确认`: the option or baseline explicitly approved by the user.
- `本次不改`: behavior or code intentionally outside the approved change.

Unless the user specifies otherwise, use this authority order:

1. Current explicit user instructions.
2. Decisions explicitly confirmed in the current task.
3. The applicable approved product specification.
4. Current code and tests for existing behavior.
5. README files and historical documents.

Expose conflicts; do not silently choose one source.

## Workflow

### 1. Discover the current behavior

Read [references/discovery-and-impact.md](references/discovery-and-impact.md). Inspect only the repository areas needed to reproduce or explain the pain point. Protect existing user changes and establish the current test baseline when proportionate.

Report the current behavior, user impact, relevant code boundaries, and missing evidence before presenting the options.

### 2. Clarify the change objective

Translate the request into observable outcomes and constraints. Clarify only issues that can change the option, scope, compatibility strategy, or acceptance result.

Do not treat literal UI wording as a required implementation mechanism when it would introduce incorrect interaction semantics. Explain the distinction and offer a repository-compatible option.

### 3. Compare feasible options

Read [references/options-and-clarification.md](references/options-and-clarification.md). Compare product and engineering impact, including user experience, preserved behavior, state and data compatibility, accessibility, test impact, implementation effort, rollback difficulty, and meaningful risks.

### 4. Produce the recommended change specification

Read [references/change-spec-and-acceptance.md](references/change-spec-and-acceptance.md). The recommended option must be directly executable by Codex and include:

- target behavior and interaction;
- affected modules, components, files, interfaces, and state;
- compatibility, persistence, migration, degradation, and rollback handling where relevant;
- behavior and data that must be preserved;
- explicit exclusions;
- test plan and observable acceptance criteria.

Do not modify code in this step.

### 5. Obtain explicit approval

Present the recommendation and remaining choices. Stop after asking the user to select an option or answer the smallest necessary clarification round.

After the response, summarize the confirmed option, user modifications, unresolved matters, downstream impacts, and final acceptance baseline. Begin implementation only when the response clearly authorizes execution, such as `确认方案A` or `按推荐方案执行`.

### 6. Implement the approved option

Recheck the dirty worktree, preserve unrelated changes, and make the smallest coherent implementation. Comments should explain non-obvious invariants or compatibility decisions, not restate the code.

Do not delete underlying domain data merely because its UI presentation is removed unless deletion was explicitly approved. When changing persisted states, routes, schemas, or enums, handle legacy values when the repository indicates they may exist.

### 7. Verify and report

Run focused tests first, then proportionate repository-wide checks such as type checking, lint, full tests, build, and UI interaction or visual verification. Do not claim a check passed if it could not run.

Report the implemented outcome, main files, verification evidence, known limitations, and any unrelated pre-existing warnings. If a requested validation surface is unavailable, disclose it and do not bypass an explicitly selected tool or environment without approval.

## Mandatory stop conditions

Stop and request a decision when:

- two feasible options produce materially different user behavior;
- implementation requires an unapproved dependency, integration, credential, migration, destructive action, or business-rule change;
- current user changes overlap the required edit and cannot be preserved safely;
- repository facts contradict the approved option;
- acceptance criteria cannot be made observable;
- completing the change safely would require expanding the approved scope.

Difficulty, duration, or ordinary implementation details are not reasons to reopen a confirmed decision.

## Completion standard

The workflow is complete only when the selected option is implemented within scope, compatibility decisions are handled, acceptance criteria map to observable evidence, relevant checks have run, and limitations are reported honestly.
