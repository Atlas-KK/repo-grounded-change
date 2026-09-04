# Options and clarification

## Option quality

Provide 2 or 3 mutually exclusive options when genuine alternatives exist. For each option state:

- behavior and user experience;
- implementation shape and major code areas;
- preserved and changed behavior;
- compatibility and migration consequences;
- testing implications;
- risks, effort, and rollback difficulty.

Recommend the option with the best overall fit for the user's stated outcome and repository constraints, not merely the smallest diff.

Do not present obviously inferior or unsafe choices as equal alternatives. If only one option is feasible, document the rejected approaches and their blocking reasons.

## Clarification rules

- One requirement theme per round.
- At most 3 questions in a round; prefer 1 question when it unlocks the solution.
- Each question has 2 or 3 mutually exclusive choices.
- Put the recommended choice first, mark it `（推荐）`, and explain its impact.
- Ask only about product behavior, material risk, scope, or acceptance—not low-level details Codex can determine from the repository.
- Use structured input controls when available. Otherwise accept responses such as `A`, `Q1-A`, `按建议执行`, or a user-written modification.

After each answer, report:

- confirmed decisions;
- user modifications;
- unresolved items;
- conflicts;
- impact on later recommendations.

Do not interpret discussion or praise as implementation approval.
