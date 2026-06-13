---
description: "Anti-regression rules preventing architectural drift"
globs: "**/*.{ts,tsx}"
alwaysApply: false
version: "3.0.0"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Anti-Regression Index

<meta-instruction>
Use this folder when modifying stable systems, fixing bugs, or refactoring code where historical drift can reappear. Prefer Via Negativa: explicitly ban known bad patterns.
</meta-instruction>

<routing-logic>
IF a task touches architectural boundaries, stable workflows, or bug-prone code:
THEN load `.ai-rules/09-anti-regression/01-global-bans.md`.

IF creating a new regression file:
THEN use `.ai-rules/09-anti-regression/02-regression-template.md` or `.ai-rules/91-templates/TEMPLATE-ANTI-REGRESSION.md`.
</routing-logic>

## Anti-regression rules

<positive-directives>
- Convert repeated bugs into explicit bans.
- Tie each ban to a known incident or failure pattern when possible.
- Keep bans atomic and enforceable.
- Use anti-regression files sideways from domain files.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT reintroduce silent failures.
- DO NOT bypass established boundaries for quick fixes.
- DO NOT fix a bug by hiding failure or returning fake success.
- DO NOT let raw external input skip validation because a previous layer "probably" handled it.
</absolute-constraints>

<pre-flight-checklist>
1. [ ] Is this a stable or historically bug-prone area?
2. [ ] Did I check anti-regression bans?
3. [ ] Did I avoid bypassing boundaries?
</pre-flight-checklist>
