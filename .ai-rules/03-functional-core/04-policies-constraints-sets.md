# Policies, Constraints, and Sets

<meta-instruction>
Use this file for authorization, feature flags, eligibility, matching, route access, scheduling, booking limits, scopes, tags, and set-shaped domains.
</meta-instruction>

## Policy rules

<positive-directives>
- Name policies with domain verbs: decideAccess, decideLimit, authorizeScopes, findEligibleOptions.
- Use sets for membership, overlap, missing values, scopes, tags, and allowed transitions.
- Use named constraints when the problem is "find values satisfying these rules".
- Return failed constraint names or missing values when useful.
- Keep side effects out of constraints.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT use arrays as sets when membership/overlap is central and order does not matter.
- DO NOT build a fake rule engine for two conditions.
- DO NOT hide database or network calls inside predicates named like pure constraints.
- DO NOT return only `false` for permission failures when support/debug/UI needs the reason.
</absolute-constraints>

<context>
<example>
// Good: missing permissions are explicit.
function authorize(required: ReadonlySet<Scope>, granted: ReadonlySet<Scope>): AccessDecision {
  const missing = difference(required, granted);
  return missing.size === 0 ? { kind: "allow" } : { kind: "deny", missing };
}
</example>

<example>
// Bad: boolean hides missing scope.
return required.every(scope => granted.includes(scope));
</example>
</context>

<pre-flight-checklist>
1. [ ] Is this membership, eligibility, or matching?
2. [ ] Would a set or named constraint reveal the domain?
3. [ ] Are failure reasons useful?
</pre-flight-checklist>
