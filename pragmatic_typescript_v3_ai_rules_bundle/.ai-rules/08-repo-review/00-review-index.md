---
description: "Repo review and schema stress-testing framework"
globs: "**/*.{ts,tsx,js,jsx,md}"
alwaysApply: false
version: "3.0.0"
protocol_compat: "mcp: 2026-05"
dependencies: ["web-search-if-current", "github-source-if-available"]
priority_schema: "critical > strong > guideline"
---

# Repo Review Index

<meta-instruction>
Use this folder when evaluating real repositories, producing before/after refactors, or stress-testing the schema. Be honest: many files should be left mostly alone.
</meta-instruction>

<routing-logic>
IF producing a repo review:
THEN load `.ai-rules/08-repo-review/01-review-format.md`.

IF assigning numerical schema strength:
THEN load `.ai-rules/08-repo-review/02-strength-ratings.md`.

IF code appears to be tiny utility, glue, generated, algorithmic, or type-level library internals:
THEN load `.ai-rules/08-repo-review/03-weak-fit-categories.md`.

IF summarizing findings from stress tests:
THEN load `.ai-rules/08-repo-review/04-real-repo-findings.md`.
</routing-logic>

## Review directives

<positive-directives>
- Inspect actual file behavior before proposing refactors.
- Identify the target responsibility, not just the file name.
- Show original shape, problems, schema version, key win, and rating.
- State whether whole-file rewrite is recommended.
- Cite sources when reviewing public repos.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT invent a richer feature than the original file contains.
- DO NOT imply the whole file needs rewriting when only one seam was targeted.
- DO NOT force classes, Result types, or file splits by default.
- DO NOT ignore existing repo architecture and conventions.
</absolute-constraints>

<pre-flight-checklist>
1. [ ] Did I inspect the actual repo/file or state that the example is representative?
2. [ ] Did I identify a target responsibility?
3. [ ] Did I rate schema strength honestly?
</pre-flight-checklist>

## Casebook

<context>
For evidence from real repository stress tests, load `.ai-rules/08-repo-review/casebook/00-casebook-index.md`.
</context>
