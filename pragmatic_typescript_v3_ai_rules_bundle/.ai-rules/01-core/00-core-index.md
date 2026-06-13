---
description: "Core Pragmatic TypeScript v3 schema index"
globs: "**/*.{ts,tsx,js,jsx}"
alwaysApply: true
version: "3.0.0"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Core Schema Index

<meta-instruction>
This is the root conceptual model. Every other rule folder specializes one part of this model. Start here for architecture, refactoring, or code-review tasks.
</meta-instruction>

<routing-logic>
IF the task asks "where should this code live" or "should this be a class/function/module":
THEN load `.ai-rules/05-boundaries/00-boundary-index.md` and `.ai-rules/06-modular-architecture/00-modular-index.md`.

IF the task asks "what type should represent this" or involves Zod/Effect/generated schemas:
THEN load `.ai-rules/02-type-strategy/00-type-strategy-index.md`.

IF the task asks for before/after repo analysis:
THEN load `.ai-rules/08-repo-review/00-review-index.md`.
</routing-logic>

<routing-logic>
IF the task asks for the full compact schema summary:
THEN load `.ai-rules/01-core/05-integrated-summary.md`.
</routing-logic>

## The Four-Layer Model

<positive-directives>
- Type Strategy names domain concepts, states, decisions, failures, and validated values.
- Functional Core contains pure rules, decisions, parsing, transitions, and transformations.
- Procedural Shell coordinates side effects and workflows in readable order.
- Smallest Honest Boundary owns capabilities, resources, dependencies, framework integration, or lifecycle.
- Extension lenses are now part of the schema; use them as problem-shape detectors, not as novelty.
</positive-directives>

## Core Prohibitions

<absolute-constraints>
- DO NOT put DB/API/email/payment/filesystem calls inside functional-core helpers.
- DO NOT create a class solely to wrap one pure calculation.
- DO NOT return vague booleans when the reason matters.
- DO NOT let `unknown` or `any` external data leak into persistence or domain decisions.
- DO NOT split files until density, reuse, testability, or boundary clarity earns it.
</absolute-constraints>

## Core Mental Model

<context>
Good architecture usually reads as:

```txt
external input
→ parse/validate into honest types
→ pure decision / transition / policy
→ procedural shell executes effects
→ boundary owns dependencies/resources
```

<example>
// Good: policy is named and side effects stay outside.
type AccessDecision =
  | { kind: "allow" }
  | { kind: "deny"; reason: "missing_scope" };

function decideAccess(required: ScopeSet, granted: ScopeSet): AccessDecision {
  return isSubset(required, granted)
    ? { kind: "allow" }
    : { kind: "deny", reason: "missing_scope" };
}
</example>

<example>
// Bad: policy, framework response, and implementation details are mixed.
if (!granted.includes("admin:read")) {
  return NextResponse.redirect("/403");
}
</example>
</context>

## Core Checklist

<pre-flight-checklist>
1. [ ] What is the type strategy?
2. [ ] What is the functional core?
3. [ ] What side effects belong in the shell?
4. [ ] What boundary shape is smallest and honest?
5. [ ] Is this revealing meaning or adding ceremony?
</pre-flight-checklist>
