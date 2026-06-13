---
title: "Blueprint Output & Schema Compilation Routing"
description: "Output contracts for categorization blueprints and final flat schema file plans."
globs: "**/*"
alwaysApply: false
version: "1.0.0"
schema_version: "1.0.0"
model_target: "universal-planner-hybrid"
protocol_compat: "mcp: 2026-05"
dependencies: ["mcp-filesystem"]
priority_schema: "critical > strong > guideline"
---

# Blueprint Output & Schema Compilation Routing

<meta-instruction>
Use this file only when producing blueprint outputs or mapping approved categories into final schema/rule files. Keep the final rule tree flat and directly routed.
</meta-instruction>

## 1. Output Directives

<positive-directives>
- You MUST output the categorized inventory before the final file plan.
- You MUST include a boundary decision matrix for disputed categories.
- You MUST show the proposed codebase tree separately from the proposed AI rules tree.
- You MUST verify that every final rule file has YAML frontmatter.
- You MUST split horizontally in the same folder when one file would exceed 15 rules.
</positive-directives>

## 2. Compilation Prohibitions

<absolute-constraints>
- DO NOT create folders below the central rules folder.
- DO NOT create final rule files without a router pointer.
- DO NOT create final rule files without YAML frontmatter.
- DO NOT exceed 15 total rules or constraints in a generated rule file.
- DO NOT use research notes as executable rules unless they are compiled into routed schema files.
</absolute-constraints>

## 3. Required Blueprint Shape

<context>
The approved blueprint must include:

```text
1. Project Area Inventory
2. Module Inventory
3. Logic Intent Inventory
4. Category Vocabulary Table
5. Boundary Decision Matrix
6. Proposed Codebase Tree
7. Proposed Flat AI Rules Tree
8. Router Pointer Table
9. Glob Verification Table
10. Compile-Ready File Plan
```
</context>

## 4. Final Schema Tree Pattern

<context>
Use this shape when compiling final `.ai-rules` files:

```text
.ai-rules/
  00-system-index.md
  01-project-areas.md
  02-module-boundaries.md
  03-logic-intent.md
  04-data-and-translation.md
  05-infrastructure-boundaries.md
  06-anti-regression.md
```

If a domain exceeds the 15-rule ceiling, split it horizontally:

```text
.ai-rules/
  03A-logic-intent-domain.md
  03B-logic-intent-orchestration.md
```
</context>

<pre-flight-checklist>
Before producing a final file plan, verify:
1. [ ] Is every final file directly routed?
2. [ ] Is the rules directory flat?
3. [ ] Does every final file have YAML frontmatter?
4. [ ] Are globs aligned with the proposed codebase tree?
</pre-flight-checklist>
