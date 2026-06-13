---
title: "Category Vocabulary & Ontology Boundaries"
description: "Controlled vocabulary for project, module, artifact, and ontology categorization."
globs: "**/*"
alwaysApply: false
version: "1.0.0"
schema_version: "1.0.0"
model_target: "universal-planner-hybrid"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Category Vocabulary & Ontology Boundaries

<meta-instruction>
Use this file to name categories consistently. The goal is not to invent many labels; the goal is to keep category boundaries stable, minimal, and useful for routing future schema files.
</meta-instruction>

## 1. Vocabulary Directives

<positive-directives>
- You MUST define every proposed category with a one-sentence boundary rule.
- You MUST assign each item to exactly one primary category before adding secondary tags.
- You MUST separate ontology categories from implementation folders.
- You MUST preserve the user's own domain language unless it conflicts with boundary clarity.
- You MUST mark ambiguous items as `Needs Decision` instead of guessing.
</positive-directives>

## 2. Vocabulary Prohibitions

<absolute-constraints>
- DO NOT create synonym categories that mean the same thing.
- DO NOT use framework folder names as ontology categories by default.
- DO NOT allow one item to have two primary categories.
- DO NOT create a category without a routing or decision purpose.
- DO NOT split categories only for human readability.
</absolute-constraints>

## 3. Controlled Category Layers

<context>
Use these layers when building the categorization blueprint:

| Layer | Meaning | Example |
| :--- | :--- | :--- |
| Project Area | A major product or app capability | Auth, Billing, Content, Analytics |
| Module Role | What a module is responsible for | Feature Module, Domain Module, Adapter Module |
| Logic Intent | What internal logic is doing | Domain, Orchestration, Mapping, Infrastructure |
| Data Shape | What kind of data artifact exists | DTO, Entity, Value Object, Persistence Record |
| Boundary Surface | Where systems meet or translate | API Boundary, Database Boundary, External Service Boundary |
| Rule Artifact | What schema file should govern it | Domain Rule, Anti-Regression Rule, Feature Rule |
</context>

## 4. Why This File Exists

<context>
Without a controlled vocabulary, categorization becomes aesthetic naming. The same module can be called a service, manager, controller, feature, or domain object, causing unstable schema routing.
</context>

<pre-flight-checklist>
Before using a category name, verify:
1. [ ] Does the category have a clear boundary rule?
2. [ ] Is there exactly one primary category per item?
3. [ ] Did I avoid synonym categories?
4. [ ] Does the category help future routing or decision-making?
</pre-flight-checklist>
