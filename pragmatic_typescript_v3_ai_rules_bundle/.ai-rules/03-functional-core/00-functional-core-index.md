---
description: "Functional core rules for pure decisions, parsing, validation, policies, and transformations"
globs: "**/*.{ts,tsx}"
alwaysApply: false
version: "3.0.0"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Functional Core Index

<meta-instruction>
The functional core contains pure or pure-adjacent meaning: decisions, validation, parsing, transformations, calculations, state transitions, policies, constraints, and lifecycle rules.
</meta-instruction>

<routing-logic>
IF the task extracts a business decision or policy:
THEN load `.ai-rules/03-functional-core/01-pure-decisions.md`.

IF the task parses text, JSON, config, clipboard, protocol records, webhooks, or external input:
THEN load `.ai-rules/03-functional-core/02-validation-parsing.md`.

IF the task models lifecycle, UI workflow, async request state, uploads, returns, jobs, subscriptions, or hydration:
THEN load `.ai-rules/03-functional-core/03-state-transitions-lifecycle.md`.

IF the task involves permissions, matching, eligibility, scopes, sets, constraints, or feature flags:
THEN load `.ai-rules/03-functional-core/04-policies-constraints-sets.md`.

IF the task involves arrays, DTO mappings, normalization, pipelines, reports, or display derivation:
THEN load `.ai-rules/03-functional-core/05-transformations-pipelines.md`.
</routing-logic>

## Functional Core Rules

<positive-directives>
- Make hidden rules explicit with named pure functions.
- Pass time, random generators, and environment values in as inputs when needed.
- Return values instead of mutating inputs.
- Return typed decisions for meaningful outcomes.
- Keep framework response mapping outside the core.
</positive-directives>

## Hard Constraints

<absolute-constraints>
- DO NOT call databases from functional-core functions.
- DO NOT call network APIs from functional-core functions.
- DO NOT send emails, logs, analytics, payments, or jobs from functional-core functions.
- DO NOT read `Date.now()` or randomness inside pure functions unless explicitly passed in.
- DO NOT mutate input objects to express a decision.
</absolute-constraints>

<context>
<example>
// Good: rule is pure and named.
function decideBookingLimit(existing: Booking[], candidates: Candidate[], limit: Limit): LimitDecision {
  return existing.length + candidates.length > limit.max
    ? { kind: "deny", reason: "booking_limit_exceeded" }
    : { kind: "allow" };
}
</example>

<example>
// Bad: rule hides DB access and side effects.
async function decideBookingLimit(...) {
  const existing = await db.bookings.findMany(...);
  logger.info("checking limit");
}
</example>
</context>

<pre-flight-checklist>
1. [ ] Is this function pure or intentionally pure-adjacent?
2. [ ] Are all dependencies inputs?
3. [ ] Is side-effect execution left to the shell?
</pre-flight-checklist>
