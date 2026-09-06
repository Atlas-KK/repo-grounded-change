# Change specification and acceptance

Use for full proposals or changes involving persisted state, interfaces, or migrations. For a bounded change, keep only the applicable outcome and verification details.

## Executable specification

Give enough detail to implement and review the recommendation:

- Observable outcome and relevant interaction or execution states.
- Owning modules, interfaces, state, data, and tests affected.
- Compatibility, migration, fallback, degradation, and rollback where relevant.
- Existing behavior and data that must be preserved.
- Scope boundaries where adjacent work could otherwise be mistaken for authorization.
- Proportionate verification and observable acceptance criteria.

Omit irrelevant categories instead of filling a template. Label inferred file touchpoints and verify them before editing. Avoid success criteria such as "looks better" or "works normally" without describing what observable change demonstrates success. Inspect code, tests, or runtime and propose a check before treating missing acceptance evidence as a user blocker.

## Authorization baseline

For a complex change, briefly capture the selected outcome, consequential assumptions, scope, and acceptance criteria when needed to prevent ambiguity. Reuse the user's direct instructions and prior confirmed decisions.

If that baseline is already authorized and no consequential decision remains, implement immediately. If authorization is missing, present the concrete recommendation and ask only for the missing decision or execution approval. If the user requested only an assessment deliverable, completing that deliverable does not require converting it into an implementation request.

Reopen only the portion materially changed by new evidence. Ordinary implementation details do not invalidate approval.

## Execution evidence

Connect acceptance to appropriate evidence: focused behavioral tests, static analysis, build, runtime interaction, visual inspection, or manual checks. Use a full acceptance-to-evidence mapping only when complexity warrants it; otherwise summarize the outcome and checks.

Distinguish source-level inference from executed verification. Identify unavailable required checks and their impact. Do not claim tests or full acceptance passed when evidence is incomplete, and do not add a new test for every reversible low-impact edit just to fill this list.
