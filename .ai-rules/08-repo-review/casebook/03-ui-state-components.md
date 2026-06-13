---
description: "UI, React component, hook, upload, and workflow-state cases"
globs: "**/*.{tsx,ts}"
alwaysApply: false
version: "3.0.0"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Casebook: UI State and Components

<meta-instruction>
These cases show how the schema applies to frontend code without turning components into backend-style services.
</meta-instruction>

## Ant Design Upload

<context>
Target responsibilities:
- max-count policy
- change-emission policy
- `beforeUpload` magic return values

Key type:
```ts
type BeforeUploadDecision =
  | { kind: "upload"; file: RcFile }
  | { kind: "skip" }
  | { kind: "ignore" };
```

Key win:
```txt
Magic callback outcomes become explicit domain language.
```

Schema lesson:
- Keep `Upload.tsx` as React shell/boundary.
- Extract hidden policies as nearby pure helpers.
- Do not build a full lifecycle state machine unless upload status logic grows.
</context>

## Dify Agent node

<context>
Target responsibility: derived display models and tool icons.

Key win:
```txt
React component renders; pure helpers derive display data.
```

Recommended split:
```txt
nodes/agent/
  node.tsx
  derive-display-models.ts
  derive-tool-icons.ts
```

Schema lesson:
- UI transformation logic belongs in pure nearby helpers when meaningful/testable.
- No class, no `Result`, no framework-style service needed.
</context>

## VS Code multi-step input sample

<context>
Target responsibility: workflow draft state.

Key type:
```ts
type ResourceGroupSelection =
  | { kind: "existing"; item: QuickPickItem }
  | { kind: "new"; name: string };
```

Key win:
```txt
QuickPickItem | string becomes honest workflow state.
```

Schema lesson:
- `MultiStepInput` class is justified because it owns UI resources, step stack, disposal, and lifecycle.
- Draft state should use explicit variants.
- Samples may stay one file for teaching, but real extensions can split flow helpers.
</context>

## React Hook Form example

<context>
Finding:
```txt
Mostly leave it alone.
```

The example already has:
- small components
- clear generic form wrapper
- library-native boundary
- no hidden domain logic

Possible tiny improvement:
```ts
TFormValues extends FieldValues
```

Schema lesson:
- Component extension points can be good as-is.
- Do not add architecture to tutorial examples with no hidden meaning.
</context>

<pre-flight-checklist>
1. [ ] Is the component hiding a policy/state decision, or is it just rendering?
2. [ ] Can derived display data be tested without React?
3. [ ] Did I avoid backend-style services in UI code?
</pre-flight-checklist>
