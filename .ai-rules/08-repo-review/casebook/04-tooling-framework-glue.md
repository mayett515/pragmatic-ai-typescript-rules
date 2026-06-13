---
description: "Tooling, config resolver, framework registration, and library-core cases"
globs: "**/*.{ts,tsx,js,jsx}"
alwaysApply: false
version: "3.0.0"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Casebook: Tooling and Framework Glue

<meta-instruction>
These cases show how the schema behaves in tooling/framework code: it helps at policy seams but should not disturb good procedural glue.
</meta-instruction>

## Vitest config resolver

<context>
Target responsibility: snapshot update policy.

Key helper:
```ts
function decideSnapshotUpdateMode(input: SnapshotUpdateInput): SnapshotUpdateMode
```

Schema lesson:
- Config resolvers should stay procedural.
- Extract hidden precedence/policy decisions from nested ternaries.
- Do not rewrite the whole resolver.
</context>

## Astro create-vite

<context>
Target responsibility: Vite plugin application policy.

Key type:
```ts
type PluginApplyDecision =
  | { kind: "keep" }
  | { kind: "drop"; reason: "empty_plugin" }
  | { kind: "drop"; reason: "opposite_command" }
  | { kind: "drop"; reason: "apply_function_rejected" };
```

Schema lesson:
- Comments can be good, but typed decisions make policy executable/testable.
- Keep Vite config merging procedural.
</context>

## Playwright config

<context>
Target responsibilities:
- worker-source precedence
- web-server normalization

Key types:
```ts
type WorkerSource =
  | { kind: "forced_single_worker"; reason: "debug" | "pause" }
  | { kind: "cli_override"; value: string | number }
  | { kind: "user_config"; value: string | number }
  | { kind: "default_percentage"; value: "50%" };
```

Schema lesson:
- Config bugs are often precedence bugs.
- Name precedence origins.
- Classes are defensible when they aggregate resolved config/project internals.
</context>

## Monaco TypeScript mode

<context>
Target responsibility: provider registration table.

Key concept:
```txt
configuration flag → provider registration
```

Schema lesson:
- A typed executable registry can reveal repeated if-block structure.
- OOP adapters in Monaco are already boundary objects.
- Do not add a fake service class.
</context>

## XState spawn

<context>
Target responsibility: spawn source resolution.

Key type:
```ts
type ResolvedSpawnSource =
  | { kind: "referenced"; src: string; logic: AnyActorLogic }
  | { kind: "inline"; logic: AnyActorLogic };
```

Schema lesson:
- XState is already deeply schema-native: type strategy and actor boundaries are the product.
- Maybe extract source resolution if it grows.
- Do not split or class-wrap core library functions unnecessarily.
</context>

## Zustand persist

<context>
Target responsibility: hydration decision.

Key type:
```ts
type HydrationDecision<S> =
  | { kind: "empty_storage" }
  | { kind: "use_stored_state"; state: S }
  | { kind: "migrate"; state: unknown; fromVersion: number }
  | { kind: "migration_missing"; fromVersion: number };
```

Schema lesson:
- Middleware can be a boundary.
- No class needed.
- Extract hidden lifecycle decisions when dense.
</context>

<pre-flight-checklist>
1. [ ] Is this framework glue or a real policy seam?
2. [ ] Did I preserve procedural setup/registration when it is already clear?
3. [ ] Did I avoid turning tooling code into enterprise architecture?
</pre-flight-checklist>
