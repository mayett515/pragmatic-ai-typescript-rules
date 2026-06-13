---
description: "Strict prohibition gates preventing historical bugs for [DOMAIN]"
globs: "[INSERT RELEVANT GLOBS]"
alwaysApply: false
version: "1.0.0"
model_target: "[INSERT MODEL FAMILY]"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Anti-Regression Contract: [DOMAIN]

<meta-instruction>
You have been routed here because you are modifying stable systems, fixing bugs, or touching code with known regression risk. This file contains hard bans on historical anti-patterns.
</meta-instruction>

## 1. Historical Context

<incident-reports>
- Incident [ID]: [DESCRIBE THE PAST BUG OR ARCHITECTURAL FAILURE].
- Incident [ID]: [DESCRIBE ANOTHER PAST BUG].
</incident-reports>

## 2. Hard Regression Bans

<absolute-constraints>
- REGRESSION BAN [ID]: DO NOT [EXPLICITLY BAN THE ACTION THAT CAUSED INCIDENT 1].
- REGRESSION BAN [ID]: DO NOT [EXPLICITLY BAN THE ACTION THAT CAUSED INCIDENT 2].
- REGRESSION BAN [ID]: DO NOT [EXPLICITLY BAN A RELATED ARCHITECTURAL DRIFT].
</absolute-constraints>

## 3. Anti-Regression Conditional Gates

<conditional-logic>
IF you are altering an existing function that touches [SYSTEM]:
THEN you MUST explicitly verify that [PREVIOUS FIX] remains intact.
</conditional-logic>

## 4. Anti-Regression Pre-Flight Verification

<pre-flight-checklist>
Before finalizing the refactor or bug fix, verify:
1. [ ] Did I reintroduce any pattern listed in `<absolute-constraints>`?
2. [ ] Did I bypass any established architectural boundaries?
3. [ ] Did I preserve the previous fix's intent?
</pre-flight-checklist>
