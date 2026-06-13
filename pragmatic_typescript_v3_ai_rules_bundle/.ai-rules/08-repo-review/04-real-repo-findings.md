# Real Repo Findings

<meta-instruction>
This file summarizes what repeated repo stress tests taught the schema. Use these findings as heuristics, not absolute laws.
</meta-instruction>

## Strongest fits

<positive-directives>
- Product workflows: booking, checkout, returns, subscriptions, asset editing.
- Parser boundaries: clipboard, protocol records, config files, webhooks.
- Hidden policies: MIME rules, plugin applicability, snapshot update policy, route access.
- Lifecycle systems: uploads, hydration, sessions, returns, workers.
- Permissions/entitlements: scopes, feature flags, roles, access decisions.
</positive-directives>

## Weakest fits

<positive-directives>
- Tiny pure utilities.
- Framework registration wrappers.
- Generated code.
- Highly optimized core algorithms.
- Type-level library internals.
</positive-directives>

## Stable lessons

<context>
```txt
Name the policy.
Keep the procedure.
Choose the smallest honest boundary.
```

```txt
Schema strength applies to a target responsibility, not automatically to the whole file.
```

```txt
The schema is strongest when it extracts meaning.
It is weakest when it creates structure without meaning.
```
</context>

<pre-flight-checklist>
1. [ ] Which finding does this case resemble?
2. [ ] Is this a strong-fit or weak-fit target?
3. [ ] Am I applying the schema with restraint?
</pre-flight-checklist>
