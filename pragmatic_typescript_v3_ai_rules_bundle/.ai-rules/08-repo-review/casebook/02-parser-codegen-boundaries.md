---
description: "Parser, protocol, generated type, schema, and external-data boundary cases"
globs: "**/*.{ts,tsx}"
alwaysApply: false
version: "3.0.0"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Casebook: Parser and Codegen Boundaries

<meta-instruction>
These cases show how the schema handles unknown external data, generated types, parser boundaries, schema libraries, and source-of-truth codegen.
</meta-instruction>

## Bluesky / ATProto record ingestion

<context>
Target responsibility: unknown ATProto record classification.

Key type:
```ts
type SupportedRecord =
  | { kind: "post"; uri: string; text: string; createdAt: string }
  | { kind: "follow"; subject: string; createdAt: string }
  | { kind: "like"; subjectUri: string; createdAt: string }
  | { kind: "ignored"; type: string };
```

Schema lesson:
- Lexicon-generated types are source-of-truth boundary types.
- Unknown protocol data must become validated internal variants before persistence.
- Use generated schemas/types; do not duplicate them blindly.
</context>

## Prisma generated client examples

<context>
Target responsibility: generated persistence shape vs domain input.

Key lesson:
```txt
Prisma schema
→ generated Prisma types
→ domain mapping function
→ Prisma create call
```

Recommended helper:
```ts
function toPrismaUserCreateData(input: CreateUserInput): Prisma.UserCreateInput
```

Schema lesson:
- Generated types are boundaries.
- Use them at persistence edges.
- Do not over-refactor tutorial/demo files.
</context>

## Payload JSON validation

<context>
Target responsibility: JSON validation plan inside field validator.

Key type:
```ts
type JsonValidationPlan =
  | { kind: "empty_allowed" }
  | { kind: "required_missing" }
  | { kind: "already_invalid" }
  | { kind: "validate_schema"; value: unknown; schemaConfig: JSONField["jsonSchema"] };
```

Schema lesson:
- Zod/Ajv/schema libraries are tools for the type strategy, not the whole architecture.
- Separate validation plan from effectful schema fetching and framework translation.
</context>

## Excalidraw clipboard parsing

<context>
Target responsibility: clipboard content classification.

Key type:
```ts
type ClipboardParseDecision =
  | { kind: "mixed_content"; value: PastedMixedContent }
  | { kind: "excalidraw_elements"; elements: readonly ExcalidrawElement[]; files?: BinaryFiles; programmaticAPI: boolean }
  | { kind: "plain_text"; value: string };
```

Schema lesson:
- Browser clipboard is an external-data boundary.
- Text/HTML/JSON parsing should produce named parse decisions.
- Do not let raw parsed JSON leak further than the parser boundary.
</context>

## tldraw external content

<context>
Target responsibility: external content and asset utility configuration.

Finding:
```txt
tldraw already looked schema-native.
```

It already uses:
- typed external content variants
- handler registration
- plugin-style extension points
- component/provider boundaries
- asset utility classes where behavior ownership is real

Schema lesson:
- Sometimes the correct review result is confirmation, not refactor.
</context>

<pre-flight-checklist>
1. [ ] Did unknown data become a validated internal type or parse decision?
2. [ ] Did I preserve generated types as source of truth?
3. [ ] Did I avoid introducing fake parsers when a schema library already handles the boundary?
</pre-flight-checklist>
