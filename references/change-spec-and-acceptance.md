# Change specification and acceptance

## Codex-ready modification specification

The recommended option should contain:

1. **Outcome** — the observable behavior after the change.
2. **Interaction or execution flow** — default, active, loading, empty, error, disabled, and responsive behavior where relevant.
3. **Code impact** — owning modules, components, state, interfaces, data, styles, and tests.
4. **Compatibility** — persisted values, migrations, fallbacks, feature flags, degradation, and rollback.
5. **Preservation rules** — existing behavior, data, permissions, audit records, and integrations that must remain.
6. **Exclusions** — adjacent cleanup or future work not authorized by this change.
7. **Verification plan** — focused tests and proportionate repository-wide checks.

File paths may be approximate before implementation, but clearly label inferred touchpoints and verify them before editing.

## Acceptance criteria

Acceptance criteria must be observable and testable. Cover the relevant categories:

- correct entry condition and default state;
- primary user action and resulting state;
- keyboard, focus, disabled, error, empty, and responsive behavior;
- correct data and state persistence or migration;
- preservation of unaffected workflows;
- absence of explicitly removed content or behavior;
- required tests, type checks, lint, build, and visual or interactive evidence.

Avoid criteria such as “code is elegant,” “UI looks better,” or “works normally” without a measurable condition.

## Approval baseline

Before implementation, summarize:

- selected option;
- approved modifications;
- acceptance criteria;
- assumptions;
- exclusions;
- unresolved blockers.

If there are no unresolved blockers, ask for explicit execution approval and stop.

## Execution evidence

After implementation, map each acceptance area to evidence:

- changed code or configuration;
- focused test result;
- full regression result;
- build or static analysis result;
- runtime, browser, screenshot, or manual verification result;
- disclosed validation gaps and their cause.
