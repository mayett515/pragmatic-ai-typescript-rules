---
description: "OOP ownership, class usage, GoF patterns, and SOLID at boundaries"
globs: "**/*.{ts,tsx}"
alwaysApply: false
version: "3.0.0"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# OOP Boundary Index

<meta-instruction>
OOP is not where business rules live by default. OOP is where capabilities, resources, dependencies, lifecycle, and framework integration are owned.
</meta-instruction>

<routing-logic>
IF deciding whether something should be a class:
THEN load `.ai-rules/05-boundaries/oop/01-when-to-use-classes.md`.

IF the task mentions design patterns or resembles Adapter/Facade/Proxy/Decorator/Factory/Command/State/Strategy/Observer:
THEN load `.ai-rules/05-boundaries/oop/02-gof-patterns-at-boundaries.md`.

IF the task asks about SOLID in class-based code:
THEN load `.ai-rules/05-boundaries/oop/03-solid-in-oop.md`.

IF code smells like fake OOP, god service, or class ceremony:
THEN load `.ai-rules/05-boundaries/oop/04-anti-patterns-fake-oop.md`.
</routing-logic>

## OOP core rule

```txt
Use FP for meaning.
Use procedural code for execution.
Use OOP for ownership.
```

<positive-directives>
- Use classes for adapters, repositories, service boundaries, workers, clients, stateful resources, and framework DI.
- Keep business decisions extractable as functions even when a class owns dependencies.
- Prefer composition over inheritance.
- Keep interfaces narrow and behaviorally consistent.
</positive-directives>

<absolute-constraints>
- DO NOT create a class for a pure calculation.
- DO NOT trap business policy inside giant mutable objects.
- DO NOT use inheritance when a union/function/composition is clearer.
- DO NOT create service classes with no owned capability.
</absolute-constraints>

<pre-flight-checklist>
1. [ ] What does the class own?
2. [ ] Can the policy remain functional?
3. [ ] Is OOP reducing or adding ceremony?
</pre-flight-checklist>
