# `.ai-rules` Directory Guide

<meta-instruction>
This folder is an architecture-rule ecosystem. Always begin with `00-system-index.md`, then load the relevant subfiles based on the task. Do not treat this folder as one giant prompt; use the hierarchy.
</meta-instruction>

## Folder purpose

```txt
01-core/                 Core schema and decision algorithm
02-type-strategy/        How to create and use TypeScript types
03-functional-core/      Pure rules, decisions, parsing, policies
04-procedural-shell/     Workflows, side effects, orchestration
05-boundaries/           Boundary ladder, OOP, GoF, SOLID ownership
06-modular-architecture/ File splitting, folder layout, comments
07-extension-lenses/     Language-inspired lenses integrated into the schema
08-repo-review/          Real-repo evaluation and rating framework
09-anti-regression/      Historical bug prevention and hard bans
90-specs/                Meta-specs for editing/generating rules
91-templates/            Reusable markdown templates
```

## Reading order

For most architecture work, read:

1. `00-system-index.md`
2. `01-core/00-core-index.md`
3. The specific domain folder for the task
4. `08-repo-review/01-review-format.md` if reviewing/refactoring existing code

## Core principle

The schema is a meaning-extraction system, not a universal refactoring machine.
