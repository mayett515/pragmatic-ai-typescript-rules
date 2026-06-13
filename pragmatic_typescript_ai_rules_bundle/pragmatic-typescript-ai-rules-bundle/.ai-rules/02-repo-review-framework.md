---
description: "Framework for stress-testing real repositories against the pragmatic TypeScript schema"
globs: "**/*.{ts,tsx,js,jsx,mts,cts,md}"
alwaysApply: false
version: "1.0.0"
model_target: "gpt-5.5-family"
protocol_compat: "mcp: 2026-05"
dependencies: ["web", "github"]
priority_schema: "critical > strong > guideline"
---

# Repository Review & Stress-Test Contract

<meta-instruction>
Use this file when reviewing existing code, comparing before/after architecture, or testing whether the schema actually helps a repository file. Be objective. The goal is truth, not proving the schema always wins.
</meta-instruction>

## 1. Review Directives

<positive-directives>
- You MUST identify the exact target responsibility before rating schema strength.
- You MUST distinguish direct local refactor from schema-native repo design.
- You MUST rate whether the schema improves the target, confirms existing design, or would add ceremony.
- You MUST include a key win when the schema helps.
- You MUST explicitly say when the whole file should not be rewritten.
</positive-directives>

## 2. Review Constraints

<absolute-constraints>
- DO NOT invent a richer domain than the inspected file contains.
- DO NOT imply a whole-file rewrite when only a policy seam is the target.
- DO NOT score generated code, tiny utilities, or registration glue as strong targets unless hidden meaning exists.
- DO NOT ignore existing repository conventions, helpers, validators, or framework boundaries.
- DO NOT call a refactor better merely because it is longer or more abstract.
</absolute-constraints>

## 3. Required Review Format

<conditional-logic>
IF reviewing a repository file:
THEN use this structure: Original shape, Honest read, Target responsibility, Schema version, Key win, Boundary decision, File split decision, Schema strength, Verdict.

IF the code already fits the schema:
THEN classify it as a confirmation case and avoid forced refactoring.

IF the schema is weak for the target:
THEN explain the failure domain.
</conditional-logic>

## 4. Context and Examples

<context>
Schema strength applies to the target responsibility, not automatically to the whole file.

<example>
// Good: target is precise.
Target: MIME policy inside FilesService.
Schema strength: 8.7/10.
Whole-service rewrite: No.
</example>

<example>
// Bad: target is too broad and implies a rewrite.
Target: Entire FilesService.
Schema strength: 9/10. Rewrite it all with our architecture.
</example>
</context>

## 5. Review Pre-Flight Verification

<pre-flight-checklist>
Before finalizing a repo review, verify:
1. [ ] Did I identify the target responsibility precisely?
2. [ ] Did I separate direct local refactor from schema-native design when useful?
3. [ ] Did I include the key win or say there is none?
4. [ ] Did I avoid whole-file rewrite implications?
5. [ ] Did I rate ceremony risk honestly?
</pre-flight-checklist>
