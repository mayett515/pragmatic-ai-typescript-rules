---
description: "Human and AI guide for the flat Kordex refactor rules add-on"
globs: ".kordex-refactor-rules/**/*.md"
alwaysApply: false
version: "1.0.0"
model_target: "universal-router-hybrid"
protocol_compat: "mcp: 2026-05"
last_updated: "2026-06-13"
priority_schema: "critical > strong > guideline"
dependencies: ["pragmatic-ai-typescript-rules-v3-flat"]
---

# Kordex Refactor Rules — Flat Add-On

<meta-instruction>
This directory is a Kordex-specific add-on to the separate Pragmatic TypeScript v3 flat rules bundle. Use it only for the Kordex ontology/profile/proposal/checker refactor; do not treat it as a replacement for the generic TypeScript scheme.
</meta-instruction>

## Why This Folder Exists

This bundle captures the extra things discovered in the Kordex refactor discussion: operation/type-system design, proposal safety, Effect evaluation, invariant testing, refactor tooling, function cataloging, and AI-agent repository context.

## Relationship To The TypeScript Bundle

The base TypeScript scheme lives here:

- https://github.com/mayett515/pragmatic-ai-typescript-rules
- Flat bundle path: `pragmatic_typescript_v3_ai_rules_bundle_flat/.ai-rules/`

That bundle should continue to govern general TypeScript style. This folder governs the Kordex-specific refactor path.

## Why Flat

<positive-directives>
- Keep this directory flat so `00-system-index.md` can route directly to every active rule file.
- Split large domains horizontally with `01A`, `01B`, `02A`, and similar prefixes instead of nested folders.
- Keep examples, tool prompts, and package notes as routed markdown files with YAML frontmatter.
</positive-directives>

<absolute-constraints>
- DO NOT create nested rule folders below `.kordex-refactor-rules/`.
- DO NOT place active rules in orphan files that are not referenced from `00-system-index.md`.
- DO NOT duplicate broad TypeScript style rules already owned by the Pragmatic TypeScript bundle.
</absolute-constraints>

<context>
Target Directory Scope: `.kordex-refactor-rules/`
Key Libraries Discussed: `ts-pattern`, `fast-check`, `effect`, Graphify, Serena, Codebase-Memory MCP, dependency-cruiser, ast-grep, Knip, TypeDoc.

<example>
// Good: flat, directly routed rule file
.kordex-refactor-rules/01B-effect-runtime-spike.md
</example>

<example>
// Bad: nested, likely orphaned by routing
.kordex-refactor-rules/runtime/effect/spike.md
</example>
</context>

<pre-flight-checklist>
Before using this bundle, internally verify:
1. [ ] Did I load the general TypeScript rules first when editing generic TS code?
2. [ ] Did I load `00-system-index.md` before using any Kordex-specific subfile?
3. [ ] Did I keep active rule files flat and directly routable?
</pre-flight-checklist>
