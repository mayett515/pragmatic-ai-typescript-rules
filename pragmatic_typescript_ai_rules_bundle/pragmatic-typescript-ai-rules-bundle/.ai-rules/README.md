# `.ai-rules` Bundle: Pragmatic TypeScript Architecture

<meta-instruction>
You are an expert TypeScript architecture assistant. This folder is the source of truth for the user's preferred TypeScript style. Before generating or refactoring code, load `00-system-index.md`, follow its routing logic, and then load any referenced sub-files that match the task.
</meta-instruction>

## Hidden Folder Rule

This folder is named `.ai-rules` so it stays visually quiet in a project root. The leading dot makes it hidden on macOS, Linux, and Windows, but AI tools, CLIs, editors, and repository agents can read it normally.

## Ecosystem Inventory

Start with these files:

- `00-system-index.md` — master router and global execution contract.
- `01-pragmatic-typescript.md` — main TypeScript architecture contract.
- `01A-type-strategy.md` — domain types, validation, generated types, Zod/Effect guidance, modern TS features.
- `01B-functional-core-shell.md` — pure rules, procedural shell, workflows, Result usage.
- `01C-boundaries-oop-patterns.md` — smallest honest boundary, OOP, GoF patterns, adapters, workers.
- `01D-modular-architecture-comments.md` — file splitting, modular architecture, comments that explain intent.
- `02-repo-review-framework.md` — how to evaluate existing code, direct refactors, and schema-native designs.
- `04-anti-regression.md` — bans that prevent architectural drift.
- `SPEC-01-SCHEMA-GENERATION.md` — rules for generating more `.md` rule files.
- `SPEC-02-FILE-HIERARCHY.md` — hierarchy and routing rules.
- `TEMPLATE-DOMAIN.md` — template for new domain rule files.
- `TEMPLATE-ANTI-REGRESSION.md` — template for historical regression guard files.

## Core Mental Model

```txt
Type Strategy
↓
Functional Core
↓
Procedural / Imperative Shell
↓
Smallest Honest Boundary
```

The language lenses are integrated into the schema. Do not apply them by name for decoration. Use them to identify problem shapes: variants, parsers, workflows, constraints, sets, bulk transforms, plugins, workers, lifecycle, codegen, and validated values.

## Execution Protocol

1. Load `00-system-index.md`.
2. Follow routing into the relevant Level 1 or Level 2 rule files.
3. Identify the target responsibility, not necessarily the whole file.
4. Apply the smallest schema improvement that reveals meaning.
5. Avoid ceremony that adds structure without increasing meaning.
