---
description: "Strict prohibition gates preventing historical bugs for [DOMAIN]"
globs: "[INSERT RELEVANT GLOBS]"
alwaysApply: false
version: "1.0.0"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Anti-Regression Contract: [DOMAIN]

<meta-instruction>
This file bans historical drift patterns. Use Via Negativa. Do not include positive-directives unless explicitly required.
</meta-instruction>

## 1. Historical Context

<incident-reports>
- Incident [ID]: [DESCRIBE PAST BUG OR ARCHITECTURAL FAILURE].
</incident-reports>

## 2. Hard Regression Bans

<absolute-constraints>
- REGRESSION BAN [ID]: DO NOT [EXPLICIT ACTION THAT CAUSED INCIDENT].
</absolute-constraints>

## 3. Conditional Gates

<conditional-logic>
IF you alter [SYSTEM]:
THEN verify [PREVIOUS FIX] remains intact.
</conditional-logic>

## 4. Verification

<pre-flight-checklist>
1. [ ] Did I avoid every regression ban?
2. [ ] Did I preserve stable architectural boundaries?
</pre-flight-checklist>
