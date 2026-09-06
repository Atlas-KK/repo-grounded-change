# Options and clarification

Read when genuine alternatives or an unresolved consequential choice exist.

## Option quality

Recommend the best fit for the user's outcome and repository constraints, not merely the smallest diff. Present two or three options only when they embody real product or engineering tradeoffs that the user needs to decide. Do not manufacture alternatives, include obviously inferior choices for balance, or ask the user to select routine implementation details.

For each meaningful option, cover only decision-relevant differences: behavior, affected code, preserved contracts, compatibility or migration, verification, cost, and rollback. If one option is clearly sufficient, give that recommendation and a concise reason. Explain rejected approaches only when that helps the decision.

## Clarification and authorization

Check the main skill's authorization contract before asking anything. An existing approved baseline or clear direct implementation request needs no second execution approval.

Ask the smallest set of questions that resolves missing product behavior, consequential risk, scope, or success criteria. Combine closely related questions if that avoids another round; do not impose one round per requirement theme. Use a suitable structured input tool only when its documented mode and purpose allow it. Otherwise ask a concise natural-language question. Suggested choices are optional; accept free-text answers and do not require option codes or magic approval phrases.

For assessment-only or plan-first requests, provide a concrete recommendation before seeking missing implementation approval. An answer resolving a product question does not automatically authorize execution if the user explicitly reserved a later approval step. Discussion, praise, and silence are not approval.

After an answer, incorporate it and proceed with authorized work. Mention only changed decisions, remaining blockers, or material downstream effects. Summarize a full baseline once when a complex plan is first approved or materially revised, not after every reply.
