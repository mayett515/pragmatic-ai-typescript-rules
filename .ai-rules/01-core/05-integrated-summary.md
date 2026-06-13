---
description: "Integrated summary of all learned Pragmatic TypeScript v3 principles"
globs: "**/*.{ts,tsx,js,jsx}"
alwaysApply: false
version: "3.0.0"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Integrated Summary

<meta-instruction>
Use this file when you need the whole schema in one concise mental model. It integrates Type Strategy, Functional Core, Procedural Shell, Boundary, extension lenses, SOLID, GoF, modular architecture, comments, modern TypeScript, and repo-review lessons.
</meta-instruction>

## Final sentence

<context>
```txt
Put meaning in types and pure functions.
Put execution in procedural shells.
Put ownership in boundaries.
```
</context>

## The working sequence

<positive-directives>
- First identify external data, domain concepts, decisions, policies, side effects, and ownership points.
- Use Type Strategy to make important states, decisions, failures, and validated values explicit.
- Use Functional Core for pure rules, transitions, parsing, validation, constraints, set logic, and transformations.
- Use Procedural Shell for ordered side effects, async workflows, database calls, API calls, logging, queues, and framework responses.
- Use the Smallest Honest Boundary: function, module, handler, service class, adapter class, worker, or generated client.
- Use classes when ownership is real; use functions when code only decides.
- Use extension lenses as ordinary TypeScript instincts, not as language cosplay.
- Use GoF/OOP patterns mostly at boundaries when collaboration/ownership requires them.
- Use SOLID as responsibility, substitution, interface size, extension, and dependency-direction guidance without forcing class-heavy design.
- Use modern TypeScript only when it clarifies real behavior or strengthens contracts.
- Split files only when density, reuse, testing, or boundary clarity earns the split.
- Comment intent and boundaries; do not narrate obvious code.
- Rate schema strength at the target responsibility, not the whole file.
- Reject ceremony when it does not reveal meaning.
</positive-directives>

## Hard bans

<absolute-constraints>
- DO NOT confuse dependency parameters with dependency ownership.
- DO NOT use OOP to hide pure business rules in giant mutable objects.
- DO NOT use FP to make straightforward procedures unreadable.
- DO NOT use type-level cleverness where a simple union or constructor works.
- DO NOT add folders/files/classes because the architecture diagram looks cleaner.
- DO NOT make the schema a universal refactoring machine.
</absolute-constraints>

## Schema strength heuristic

<context>
Strong fit:
```txt
hidden domain concepts
business policies
permissions
external data parsers
lifecycle transitions
workflows with side effects
configuration precedence
```

Weak fit:
```txt
tiny pure utilities
framework registration
generated code
high-performance algorithms
type-level library internals
tutorial examples
```
</context>

<pre-flight-checklist>
1. [ ] What meaning is currently hidden?
2. [ ] What policy, state, or decision deserves a name?
3. [ ] What should stay procedural?
4. [ ] What boundary owns capabilities?
5. [ ] What would be ceremony?
</pre-flight-checklist>
