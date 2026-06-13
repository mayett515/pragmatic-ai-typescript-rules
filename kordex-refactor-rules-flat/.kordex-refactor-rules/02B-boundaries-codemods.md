---
description: "dependency-cruiser and ast-grep rules for Kordex boundary enforcement and structural rewrites"
globs: "**/*.{ts,tsx,js,cjs,md}"
alwaysApply: false
version: "1.0.0"
model_target: "universal-router-hybrid"
protocol_compat: "mcp: 2026-05"
last_updated: "2026-06-13"
priority_schema: "critical > strong > guideline"
dependencies: ["dependency-cruiser", "ast-grep", "knip"]
---

# Boundaries And Codemods Contract

<meta-instruction>
You have been routed here because the task touches dependency boundaries, codemods, dead code, or structural search. Make architecture enforceable before and after refactors.
</meta-instruction>

## Why

The operation algebra is only meaningful if code paths cannot bypass it. dependency-cruiser can enforce layer imports, ast-grep can find unsafe patterns, and Knip can reveal dead exports after refactors.

<positive-directives>
- Use dependency-cruiser to ban UI -> low-level data mutation imports and checker -> direct durable mutation imports.
- Use ast-grep to find direct inserts, raw DB writes, `throw new Error`, and old proposal-shape patterns.
- Use Knip before and after major slices to remove dead exports and unused dependencies.
- Commit boundary rules separately from behavior changes when possible.
</positive-directives>

<absolute-constraints>
- DO NOT allow `operations` or `core` modules to import React Native UI.
- DO NOT allow checker code to write durable ontology/profile state except through proposal commands/services.
- DO NOT apply ast-grep rewrites without reviewing sample diffs.
- DO NOT delete code only because Knip flags it if it is generated, dynamic, or tool-referenced.
</absolute-constraints>

<conditional-logic>
IF dependency-cruiser flags a violation:
THEN either fix the import direction or explicitly document a temporary exception.

IF ast-grep finds a dangerous pattern:
THEN classify each match as migrate, safe existing use, or false positive before rewriting.
</conditional-logic>

<context>
Target Directory Scope: `src/features/ontology/**/*`, repo config files.
Key Tools: dependency-cruiser, ast-grep, Knip.

<example>
// Good: structural search before migration
ast-grep --lang ts -p 'throw new Error($MSG)'
</example>

<example>
// Bad: regex replacement across TypeScript for semantic code changes
sed -i 's/insertProposal/createCommand/g' **/*.ts
</example>
</context>

<pre-flight-checklist>
Before finalizing boundary/codemod work, internally verify:
1. [ ] Did I add or update boundary checks?
2. [ ] Did I inspect representative codemod diffs?
3. [ ] Did I run tests/typecheck after the rewrite?
</pre-flight-checklist>
