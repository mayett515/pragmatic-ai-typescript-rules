---
description: "Anti-regression gates for the pragmatic TypeScript architecture schema"
globs: "**/*.{ts,tsx,js,jsx,mts,cts}"
alwaysApply: false
version: "1.0.0"
model_target: "gpt-5.5-family"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Anti-Regression Contract: Pragmatic TypeScript Architecture

<meta-instruction>
Use this file when modifying stable systems, refactoring existing code, or fixing bugs. These are hard bans against architectural drift we observed during schema stress testing.
</meta-instruction>

## 1. Historical Context

<incident-reports>
- Incident CEREMONY-001: Pure helpers were wrapped in classes, factories, or service objects without ownership.
- Incident FILESPLIT-001: Small features were split into many files before concepts were extracted.
- Incident EFFECTS-001: Business rules were hidden inside DB/API/framework shell code.
- Incident TYPES-001: Raw `any` or unchecked parsed data leaked past external boundaries.
- Incident EXTENSION-001: Language lenses were name-dropped without improving the code.
- Incident REWRITE-001: A whole file was implied to need rewriting when only one policy seam was the target.
</incident-reports>

## 2. Hard Regression Bans

<absolute-constraints>
- REGRESSION BAN CEREMONY-001: DO NOT add architectural layers that do not reveal meaning or ownership.
- REGRESSION BAN FILESPLIT-001: DO NOT split a small cohesive feature into many files before extracting concepts.
- REGRESSION BAN EFFECTS-001: DO NOT place database, network, email, payment, logging, or queue calls inside pure decision helpers.
- REGRESSION BAN TYPES-001: DO NOT pass unchecked `any` or raw parsed external data into persistence or domain decisions.
- REGRESSION BAN EXTENSION-001: DO NOT apply a language lens by name unless it changes the code shape or explanation meaningfully.
- REGRESSION BAN REWRITE-001: DO NOT rate or refactor an entire file when the schema target is only one responsibility.
</absolute-constraints>

## 3. Anti-Regression Gates

<conditional-logic>
IF a refactor introduces more files, classes, interfaces, or abstractions:
THEN you MUST explain what meaning, safety, testability, ownership, or extensibility is gained.

IF a function is already small, pure, obvious, and testable:
THEN treat it as a weak schema target unless a type/name improvement is clearly justified.

IF an external input parser is modified:
THEN verify unknown data becomes validated typed data before side effects.
</conditional-logic>

## 4. Anti-Regression Pre-Flight Verification

<pre-flight-checklist>
Before finalizing the refactor or bug fix, verify:
1. [ ] Did I avoid architecture ceremony?
2. [ ] Did I avoid premature file splitting?
3. [ ] Did I keep pure decisions free of side effects?
4. [ ] Did I validate external data before use?
5. [ ] Did I target the specific responsibility instead of the whole file by default?
</pre-flight-checklist>
