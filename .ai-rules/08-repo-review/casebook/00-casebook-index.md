---
description: "Casebook index for real-repo stress tests that shaped Pragmatic TypeScript v3"
globs: "**/*.{ts,tsx,js,jsx}"
alwaysApply: false
version: "3.0.0"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Real Repo Stress-Test Casebook

<meta-instruction>
Use this casebook as evidence and calibration. These are not rules by themselves. They show how the schema behaved against real TypeScript code: where it improved meaning, where it confirmed existing design, and where it would add ceremony.
</meta-instruction>

## Why this exists

<context>
The schema was not invented in isolation. It was shaped through repeated repo reviews across app code, UI libraries, tooling, generated clients, actor systems, config resolvers, and parser boundaries.

The purpose of the casebook is to preserve those lessons so future LLMs do not flatten the schema into generic advice.
</context>

## Case categories

<routing-logic>
IF the task involves product workflows, business policies, permissions, returns, uploads, sessions, or auth:
THEN inspect `.ai-rules/08-repo-review/casebook/01-strong-fits.md`.

IF the task involves parser boundaries, unknown external data, clipboard data, protocol records, config files, or generated schemas:
THEN inspect `.ai-rules/08-repo-review/casebook/02-parser-codegen-boundaries.md`.

IF the task involves UI components, hooks, upload widgets, workflow nodes, or derived display state:
THEN inspect `.ai-rules/08-repo-review/casebook/03-ui-state-components.md`.

IF the task involves tooling, config resolvers, provider registration, plugin application, or framework glue:
THEN inspect `.ai-rules/08-repo-review/casebook/04-tooling-framework-glue.md`.

IF the task involves already-excellent code, tiny utilities, generated code, or over-refactor temptation:
THEN inspect `.ai-rules/08-repo-review/casebook/05-restraint-weak-fits.md`.
</routing-logic>

## Stable result

<context>
```txt
Name the policy.
Keep the procedure.
Choose the smallest honest boundary.
```

```txt
A schema strength rating applies to a target responsibility,
not automatically to a whole file or whole repository.
```
</context>

<pre-flight-checklist>
1. [ ] Did I identify which case category this task resembles?
2. [ ] Did I avoid treating a whole file as bad when only one responsibility is the target?
3. [ ] Did I preserve the repo's existing architecture where it already fits the schema?
</pre-flight-checklist>
