---
description: "Human guide for the flat Pragmatic TypeScript v3 AI rules bundle"
globs: "README.md"
alwaysApply: false
version: "3.0.0"
model_target: "gpt-5.5-plus"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Pragmatic TypeScript v3 — Flat AI Rules Bundle

This bundle is optimized for **machine routing**, not visual folder browsing.

The `.ai-rules/` directory is intentionally flat. Rule domains are split horizontally with numbered files such as `01-core.md`, `02-type-strategy.md`, and `05A-oop-classes-gof-solid.md`.

## Why flat?

- Every rule file can be referenced directly from `00-system-index.md`.
- No file is hidden inside nested folders that an agent may never load.
- Horizontal splitting preserves the 15-rule ceiling without deep navigation.
- A human viewer can build a tree UI later; the rule files themselves should favor LLM routing.

## Core formula

```txt
Type Strategy
↓
Functional Core
↓
Procedural Shell
↓
Smallest Honest Boundary
```

Plus integrated extension lenses, SOLID/FP, GoF at boundaries, modern TypeScript when justified, repo-review evidence, and anti-regression rules.
