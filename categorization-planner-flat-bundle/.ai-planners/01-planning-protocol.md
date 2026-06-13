---
title: "Categorization Planning Protocol"
description: "Interrogation and approval loop for categorization planning before schema compilation."
globs: "**/*"
alwaysApply: false
version: "1.0.0"
schema_version: "1.0.0"
model_target: "universal-planner-hybrid"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Categorization Planning Protocol

<meta-instruction>
Use this file to run the planning loop. Your job is to extract the user's category intent, project boundaries, module boundaries, and approval decisions before any final schema files are generated.
</meta-instruction>

## 1. Planning Directives

<positive-directives>
- You MUST inventory the project before naming final categories.
- You MUST ask only questions that unblock categorization decisions.
- You MUST distinguish current reality from proposed architecture.
- You MUST place unresolved choices in a `Needs Decision` table.
- You MUST repeat the blueprint loop until the user gives `APPROVED`.
</positive-directives>

## 2. Planning Prohibitions

<absolute-constraints>
- DO NOT ask broad abstract questions before reading supplied folders, files, or module names.
- DO NOT treat category names as final until the user approves them.
- DO NOT collapse project areas, modules, and logic roles into one flat taxonomy.
- DO NOT generate final `.ai-rules` files from a draft blueprint.
</absolute-constraints>

## 3. Required Planning Phases

<context>
Phase 1: Inventory the app, project areas, modules, artifacts, and unknowns.
Phase 2: Propose the draft categorization blueprint and explicit boundary rules.
Phase 3: Let the user re-decide, merge, split, rename, or tighten categories.
Phase 4: After `APPROVED`, map categories to a flat schema file plan.
Phase 5: After `COMPILE`, generate the final schema files.
</context>

## 4. Why This File Exists

<context>
Planning must be separated from compilation because category systems are design decisions. If the LLM compiles too early, it freezes bad boundaries into rules and globs.
</context>

<pre-flight-checklist>
Before finalizing a planning response, verify:
1. [ ] Did I extract inventory before proposing final categories?
2. [ ] Did I identify unresolved decisions?
3. [ ] Did I ask for approval at the correct gate?
4. [ ] Did I avoid generating final schema files too early?
</pre-flight-checklist>
