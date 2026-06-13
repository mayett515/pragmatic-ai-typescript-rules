---
description: "Modular architecture, file splitting, schema-native layout, and comments"
globs: "**/*.{ts,tsx,md}"
alwaysApply: false
version: "3.0.0"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Modular Architecture Index

<meta-instruction>
Modular architecture answers where code lives. Comment architecture explains why a module exists and what belongs there. They are related but not the same.
</meta-instruction>

<routing-logic>
IF deciding whether to split files:
THEN load `.ai-rules/06-modular-architecture/01-file-splitting.md`.

IF designing folder layout:
THEN load `.ai-rules/06-modular-architecture/02-folder-architecture.md`.

IF comparing direct refactor vs schema-native repo design:
THEN load `.ai-rules/06-modular-architecture/03-schema-native-vs-direct-refactor.md`.

IF writing or evaluating comments:
THEN load `.ai-rules/06-modular-architecture/comments/00-comment-index.md`.
</routing-logic>

## Modular rules

<positive-directives>
- Extract concepts before extracting files.
- Keep related feature logic local until reuse, density, or boundary clarity earns a split.
- Split files by responsibility, not by paradigm label alone.
- Keep folder depth meaningful and navigable.
- Let comments define module intent, allowed responsibilities, and forbidden responsibilities.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT create file splits that force readers to jump for tiny concepts.
- DO NOT create folders named after patterns if the domain name is clearer.
- DO NOT split types/errors/helpers into separate files by default.
- DO NOT mix comment architecture with obvious line narration.
</absolute-constraints>

<context>
<example>
// Good split when feature grows.
returns/
  return.domain.ts
  request-return.ts
  return.service.ts
</example>

<example>
// Bad split for 80 lines.
return-types.ts
return-errors.ts
return-policy.ts
return-service.ts
return-factory.ts
</example>
</context>

<pre-flight-checklist>
1. [ ] What concept earned the split?
2. [ ] Is navigation improved?
3. [ ] Are comments explaining boundaries instead of syntax?
</pre-flight-checklist>
