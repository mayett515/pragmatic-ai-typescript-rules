---
title: "Categorization Planner Flat Bundle"
description: "Machine-optimized flat planner system for categorizing projects, modules, and internal module logic before schema generation."
version: "1.0.0"
schema_version: "1.0.0"
model_target: "universal-planner-hybrid"
protocol_compat: "mcp: 2026-05"
dependencies: ["mcp-filesystem"]
priority_schema: "critical > strong > guideline"
---

# Categorization Planner Flat Bundle

<meta-instruction>
Use this README only as the directory guide. The executable planner entrypoint is `.ai-planners/00-categorization.planner.md`.
</meta-instruction>

## File Tree

```text
categorization-planner-flat-bundle/
  README.md
  .ai-planners/
    00-categorization.planner.md
    01-planning-protocol.md
    02-category-vocabulary.md
    03-logic-intent-matrix.md
    04-output-compilation.md
    05-research-capture.md
```

## Why This Structure Exists

This bundle uses one hidden planner folder and a flat set of routed files. It avoids deep nesting, orphan notes, and tiny scattered files. Every planner file has YAML frontmatter, XML control tags, and a pre-flight checklist.

## Usage

1. Give the full folder to the LLM.
2. Start with `.ai-planners/00-categorization.planner.md`.
3. Provide the project idea, app goal, module list, folder tree, or codebase artifact.
4. Let the planner produce a categorization blueprint.
5. Only after explicit approval should the planner map categories into final `.ai-rules` schema files.

<pre-flight-checklist>
Before using this bundle, verify:
1. [ ] The LLM starts at `.ai-planners/00-categorization.planner.md`.
2. [ ] No planner files are placed in nested subfolders.
3. [ ] Every planner file inside `.ai-planners/` has YAML frontmatter.
</pre-flight-checklist>
