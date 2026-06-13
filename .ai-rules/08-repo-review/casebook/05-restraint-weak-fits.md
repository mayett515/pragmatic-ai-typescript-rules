---
description: "Weak-fit and restraint cases where the schema should mostly confirm existing design"
globs: "**/*.{ts,tsx,js,jsx}"
alwaysApply: false
version: "3.0.0"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Casebook: Restraint and Weak Fits

<meta-instruction>
Use this file to avoid over-applying the schema. A strong schema has failure domains. If the code already expresses its intent directly, do not add structure.
</meta-instruction>

## MUI `createFilterOptions`

<context>
Finding:
```txt
Already pure, small, configurable, and readable.
```

Possible improvement:
```ts
function normalizeFilterText(...)
```

But the original may still be better.

Schema lesson:
- Tiny pure utilities rarely need more structure.
- Extracting helpers can lower readability when it adds ceremony without meaning.
</context>

## n8n HTTP Request wrapper

<context>
Finding:
```txt
Version registration glue is already correct.
```

The class is justified because n8n expects a `VersionedNodeType`.

Schema lesson:
- Framework registration is a weak-fit target.
- Maybe use `satisfies` for typed config, but do not split or refactor heavily.
</context>

## TypeScript ESLint AST utilities

<context>
Finding:
```txt
Already small, pure predicates over AST variants.
```

Possible tiny improvement:
```txt
make return types proper type predicates when useful to callers.
```

Schema lesson:
- Pattern-matching utility code is often already functional core.
- Do not abstract obvious predicates into a fake rules engine.
</context>

## TanStack Query `matchQuery` and `hashKey`

<context>
Finding:
```txt
`matchQuery` is a matcher where named predicates could help only if logic grows.
`hashKey` is a tiny pure utility and should be left alone.
```

Schema lesson:
- miniKanren-like constraints are useful only when matching logic is complex enough.
- Do not turn every predicate into a constraint object.
</context>

## Prisma tutorial example

<context>
Finding:
```txt
Tutorial/demo code may be better inline.
```

Schema lesson:
- Do not split simple teaching examples into domain/shell files.
- A pure data-builder helper is optional only if reused/tested.
</context>

## Generated code

<context>
Finding:
```txt
Generated code should usually be left alone.
```

Schema lesson:
- The schema applies to the generator/source-of-truth and consumption boundaries.
- Do not manually refactor generated output.
</context>

<pre-flight-checklist>
1. [ ] Is the code already pure, small, obvious, or generated?
2. [ ] Would a refactor reveal meaning or just add navigation?
3. [ ] Am I respecting the code's purpose, such as demo/tutorial/framework glue?
</pre-flight-checklist>
