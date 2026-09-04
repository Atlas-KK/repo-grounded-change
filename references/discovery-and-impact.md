# Discovery and impact

Use this reference before proposing options.

## Repository discovery

Inspect the smallest relevant surface:

- repository instructions and dirty worktree;
- current UI, behavior, reproduction path, or failing test;
- owning components, services, state, persistence, routes, schemas, and APIs;
- related unit, integration, visual, and end-to-end tests;
- applicable approved product or design documents.

Capture the baseline before editing. If runtime reproduction is unavailable, distinguish source-level evidence from visually verified behavior.

## Pain-point statement

Summarize:

1. current behavior;
2. user pain or operational cost;
3. desired observable outcome;
4. constraints and behavior that must remain unchanged;
5. evidence gaps that could change the solution.

## Impact checklist

Evaluate only relevant categories:

- user flow, information hierarchy, discoverability, and cognitive load;
- click, keyboard, focus, selection, hover, loading, empty, and error states;
- component ownership and reuse semantics;
- state machines, cached or persisted UI state, URLs, schemas, and legacy values;
- domain data, API contracts, audit trails, and downstream consumers;
- permissions, privacy, accessibility, performance, responsiveness, and degradation;
- tests, build, deployment, observability, and rollback.

Removing a UI section does not automatically authorize deleting its backing data. Reusing a component does not automatically mean mounting the same interactive DOM in a second context; inspect whether a read-only or context-specific variant better preserves semantics.
