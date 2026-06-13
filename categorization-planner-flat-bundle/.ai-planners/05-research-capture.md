---
title: "Categorization Research Capture"
description: "Structured research capture for unknown ontology terms, taxonomy options, and categorization tradeoffs without creating orphan research folders."
globs: "**/*"
alwaysApply: false
version: "1.0.0"
schema_version: "1.0.0"
model_target: "universal-planner-hybrid"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Categorization Research Capture

<meta-instruction>
Use this file only when categorization requires researching or comparing concepts before the blueprint is finalized. Capture research as structured decision input, not as scattered notes.
</meta-instruction>

## 1. Research Directives

<positive-directives>
- You MUST state the research question before collecting options.
- You MUST compare candidate category systems by usefulness for routing and boundary clarity.
- You MUST convert research findings into decision candidates.
- You MUST mark unresolved tradeoffs as `Needs Decision`.
- You MUST merge approved research outcomes back into the categorization blueprint.
</positive-directives>

## 2. Research Prohibitions

<absolute-constraints>
- DO NOT create a `/research` folder for executable planner logic.
- DO NOT leave research findings outside the approval loop.
- DO NOT treat researched terminology as final without user approval.
- DO NOT add a new category only because a source or framework uses the term.
</absolute-constraints>

## 3. Research Output Shape

<context>
Use this compact shape:

```text
Research Question:
Candidate Terms / Models:
Boundary Impact:
Routing Impact:
Risks:
Recommended Decision:
Needs Decision:
```
</context>

## 4. Why This File Exists

<context>
Research is useful, but scattered research files become orphan context. This file keeps research inside the routed planner system and forces it to become a categorization decision.
</context>

<pre-flight-checklist>
Before using research in the blueprint, verify:
1. [ ] Did I convert findings into a concrete decision option?
2. [ ] Did I avoid creating orphan notes?
3. [ ] Did I preserve unresolved issues as `Needs Decision`?
4. [ ] Did I merge approved findings back into the main blueprint?
</pre-flight-checklist>
