---
title: "Module Logic Intent Matrix"
description: "Classification matrix for internal module logic by intent, side effects, and allowed behavior."
globs: "**/*"
alwaysApply: false
version: "1.0.0"
schema_version: "1.0.0"
model_target: "universal-planner-hybrid"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Module Logic Intent Matrix

<meta-instruction>
Use this file when categorizing internal logic inside modules. Classify by intent, responsibility, and side-effect boundary. Do not classify by code shape alone.
</meta-instruction>

## 1. Classification Directives

<positive-directives>
- You MUST classify domain rules separately from orchestration flow.
- You MUST classify mappers and translators as boundary logic unless they enforce business invariants.
- You MUST classify repositories, API clients, file access, queues, and event publishers as infrastructure.
- You MUST identify side effects before assigning the final logic category.
- You MUST record category violations as boundary risks.
</positive-directives>

## 2. Classification Prohibitions

<absolute-constraints>
- DO NOT classify two functions as the same category merely because their syntax looks similar.
- DO NOT place database writes inside domain logic.
- DO NOT place business invariants inside infrastructure adapters.
- DO NOT place external API payload shapes inside core domain objects.
- DO NOT hide orchestration decisions inside mappers.
</absolute-constraints>

## 3. Intent Matrix

<context>
| Logic Intent | Core Question | Allowed Behavior | Boundary Warning |
| :--- | :--- | :--- | :--- |
| Domain Logic | What rule must always hold? | Validate invariants, calculate business decisions, enforce value constraints | Must not depend on external systems |
| Orchestration Logic | What steps coordinate the use case? | Fetch, call domain logic, persist, publish, return result | Must not become the real business rule owner |
| Translation / Mapping Logic | How does one shape become another? | Convert DTOs, API payloads, persistence records, view models | Must not hide side effects or policy decisions |
| Infrastructure Logic | What touches the outside world? | Query DB, call APIs, send emails, read files, publish events | Must handle failures, retries, timeouts, and IO boundaries |
| Cross-Cutting Logic | What applies across many flows? | Logging, telemetry, auth guards, permissions, caching | Must not smuggle domain-specific decisions everywhere |
</context>

## 4. Why This File Exists

<context>
Logic can look identical while serving different architectural purposes. Categorizing by intent lets the schema decide where logic belongs, what it may depend on, and what it must never do.
</context>

<pre-flight-checklist>
Before assigning a logic category, verify:
1. [ ] Did I identify whether the logic has side effects?
2. [ ] Did I distinguish rule ownership from flow coordination?
3. [ ] Did I separate translation from policy decisions?
4. [ ] Did I flag any boundary risks?
</pre-flight-checklist>
