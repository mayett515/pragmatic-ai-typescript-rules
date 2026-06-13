---
description: "Comment architecture for intent, boundaries, and responsibility"
globs: "**/*.{ts,tsx}"
alwaysApply: false
version: "3.0.0"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Comment Architecture Index

<meta-instruction>
Comments should explain intent, ownership, and boundaries. They should not narrate obvious code. Use comments to reinforce modular architecture.
</meta-instruction>

<routing-logic>
IF writing module/file header comments:
THEN load `.ai-rules/06-modular-architecture/comments/01-file-header-comments.md`.

IF writing function comments:
THEN load `.ai-rules/06-modular-architecture/comments/02-function-comments.md`.

IF evaluating bad comments:
THEN load `.ai-rules/06-modular-architecture/comments/03-anti-comments.md`.
</routing-logic>

## Comment kinds

<positive-directives>
- Use file headers for purpose, may, may not.
- Use function comments for non-obvious policy, boundary, or failure model.
- Use inline comments only for surprising constraints or historical behavior.
- Keep comments short enough to stay maintained.
- Prefer comments that prevent architectural drift.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT comment obvious syntax.
- DO NOT write long stale module essays.
- DO NOT duplicate function names in prose.
- DO NOT use comments to justify bad structure that should be refactored.
</absolute-constraints>

<pre-flight-checklist>
1. [ ] Does this comment explain why, not what?
2. [ ] Does it define a boundary or policy?
3. [ ] Will it stay true as code evolves?
</pre-flight-checklist>
