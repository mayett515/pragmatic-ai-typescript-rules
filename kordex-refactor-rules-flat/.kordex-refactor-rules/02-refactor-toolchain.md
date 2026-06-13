---
description: "Kordex refactor toolchain workflow for AI-assisted codebase work"
globs: "**/*"
alwaysApply: false
version: "1.0.0"
model_target: "universal-router-hybrid"
protocol_compat: "mcp: 2026-05"
last_updated: "2026-06-13"
priority_schema: "critical > strong > guideline"
dependencies: ["graphify", "serena", "codebase-memory-mcp", "dependency-cruiser", "ast-grep", "knip", "typedoc"]
---

# Kordex Refactor Toolchain Contract

<meta-instruction>
You have been routed here because the task involves tools for refactoring, understanding, mapping, or documenting the Kordex codebase. Use tools by role; do not let tools make architecture decisions blindly.
</meta-instruction>

## Tool Roles

Graphify maps architecture/docs/concepts. Serena or Codebase-Memory handles symbol-level code memory. dependency-cruiser enforces import boundaries. ast-grep performs structural searches and codemods. Knip finds dead code. TypeDoc/JSDoc captures human intent.

<positive-directives>
- Run concept mapping before large refactors and symbol search before editing specific functions.
- Add architecture boundary checks before or during the operation-algebra migration.
- Use ast-grep for structural rewrite candidates instead of raw text grep when syntax matters.
- Run tests, typecheck, lint, and Knip after each meaningful slice.
</positive-directives>

<absolute-constraints>
- DO NOT let Graphify, Serena, Codebase-Memory, or Codex infer domain intent without checking Kordex docs and rule files.
- DO NOT perform broad codemods without inspecting representative matches first.
- DO NOT create tool-specific nested folders inside `.kordex-refactor-rules/`.
- DO NOT treat a generated graph as proof that a mutation path is safe.
</absolute-constraints>

<conditional-logic>
IF Codex repeatedly rereads files or loses context:
THEN add Serena or Codebase-Memory MCP before continuing the refactor.

IF tool output conflicts with existing tests or Kordex docs:
THEN trust tests/docs first and update the tool prompt or graph.
</conditional-logic>

<context>
Target Directory Scope: whole repo during refactor sessions.
Key Tools: Graphify, Serena, Codebase-Memory MCP, dependency-cruiser, ast-grep, Knip, TypeDoc.

<example>
// Good: map -> inspect symbols -> refactor slice -> enforce boundaries -> test
Graphify summary; Serena references; ast-grep candidates; dependency-cruiser rule; Vitest.
</example>

<example>
// Bad: ask an AI agent to “clean architecture” without a graph, symbol map, boundary rules, or tests
codex "refactor everything"
</example>
</context>

<pre-flight-checklist>
Before a tool-assisted refactor, internally verify:
1. [ ] Did I choose the tool for its specific role?
2. [ ] Did I inspect matches before applying changes?
3. [ ] Did I re-run validation after each slice?
</pre-flight-checklist>
