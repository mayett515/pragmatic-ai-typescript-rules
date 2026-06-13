---
description: "Specification for multi-file hierarchy and nested routing inside `.ai-rules`"
globs: ".ai-rules/**/*.md"
alwaysApply: false
version: "1.0.0"
model_target: "universal-router-hybrid"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Engineering Specification: Multi-File Hierarchy & Nested Routing

<meta-instruction>
Use this file when creating, moving, or routing AI rule files. The hierarchy should make responsibilities discoverable without creating deep folder mazes.
</meta-instruction>

## 1. Cascade Architecture

```txt
Level 0: 00-system-index.md
  Master router and global constraints.

Level 1: 01-pragmatic-typescript.md, 02-repo-review-framework.md, 04-anti-regression.md
  Domain or cross-cutting rule files.

Level 2: 01A-type-strategy.md, 01B-functional-core-shell.md, 01C-boundaries-oop-patterns.md, 01D-modular-architecture-comments.md
  Specific leaves for focused concerns.
```

## 2. Routing Rules

<positive-directives>
- You MUST route from broad files to more specific files.
- You MUST keep all rule files directly inside `.ai-rules` unless a future bundle explicitly introduces one nested folder.
- You MUST use XML `<routing-logic>` blocks for routing instructions.
- You MUST keep Level 2 files terminal unless the user explicitly changes the hierarchy.
</positive-directives>

## 3. Hard Hierarchy Constraints

<absolute-constraints>
- DO NOT route from Level 2 files back to `00-system-index.md`.
- DO NOT nest rule folders deeper than one level inside `.ai-rules`.
- DO NOT duplicate the same rule across many files when one routed source of truth is enough.
- DO NOT split a rule file only because it became long; split when a separate responsibility emerges.
</absolute-constraints>

## 4. Sub-Routing Syntax

<context>
Use this exact syntax when a rule file routes to another file:

<example>
// Good: explicit trigger and direct file path.
<routing-logic>
IF the task touches parser boundaries or external unknown input:
THEN you MUST load and comply with: `.ai-rules/01A-type-strategy.md`.
</routing-logic>
</example>

<example>
// Bad: vague routing without a specific file.
<routing-logic>
IF the task looks complex:
THEN read some other architecture files.
</routing-logic>
</example>
</context>

## 5. Hierarchy Pre-Flight Verification

<pre-flight-checklist>
Before finalizing hierarchy changes, verify:
1. [ ] Did I keep routing downward or sideways only?
2. [ ] Did I avoid deep nesting?
3. [ ] Did I avoid duplicate rules?
4. [ ] Did I choose file splits by responsibility instead of size alone?
</pre-flight-checklist>
