# Pure Decisions

<meta-instruction>
Use pure decisions to name policies and reasons. The strongest schema wins often come from turning inline `if` logic into an explicit decision.
</meta-instruction>

## Decision rules

<positive-directives>
- Use decision unions when multiple outcomes are meaningful.
- Include denial/failure reasons when useful for UI, logs, support, tests, or analytics.
- Keep decision functions small enough to test with table cases.
- Keep framework-specific error/response mapping outside the decision.
- Use exhaustive switches when consuming decision unions.
</positive-directives>

## Decision constraints

<absolute-constraints>
- DO NOT return bare booleans when the reason matters.
- DO NOT throw framework exceptions from pure decisions.
- DO NOT encode multiple decision states in optional fields.
- DO NOT name predicates vaguely as `check` or `validate` when a domain verb is available.
</absolute-constraints>

<context>
<example>
// Good: named policy and reason.
type AssetEditDecision =
  | { kind: "allow"; edits: readonly Edit[] }
  | { kind: "deny"; reason: "gif_not_supported" | "crop_out_of_bounds" };
</example>

<example>
// Bad: caller cannot know why.
function canEditAsset(asset: Asset): boolean {
  return asset.type === "image" && !asset.path.endsWith(".gif");
}
</example>
</context>

<pre-flight-checklist>
1. [ ] Is the policy name visible?
2. [ ] Does the return type explain all outcomes?
3. [ ] Can this be tested without mocks?
</pre-flight-checklist>
