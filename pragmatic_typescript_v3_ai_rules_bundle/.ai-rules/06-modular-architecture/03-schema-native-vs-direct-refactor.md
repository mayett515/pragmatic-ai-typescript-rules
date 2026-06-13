# Direct Refactor vs Schema-Native Design

<meta-instruction>
Use two lenses for repo review: direct local refactor and schema-native architecture. Keep both fair and avoid inflating the schema-native version with invented features.
</meta-instruction>

## Lens definitions

```txt
Direct refactor:
  How would this exact file improve if we applied the schema locally?

Schema-native design:
  If the repo had this schema from the beginning, where would the same responsibilities live?
```

## Rules

<positive-directives>
- Use direct refactor to compare local before/after one-to-one.
- Use schema-native design to show fair file-to-file comparison without stuffing all helpers into one file.
- Include only responsibilities present in the original target.
- Keep schema-native splits minimal and earned.
- Rate both lenses when useful.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT invent richer domain behavior than the original file contains.
- DO NOT pretend a schema-native design would require dozens of files.
- DO NOT use schema-native design to avoid judging the original file fairly.
</absolute-constraints>

<context>
<example>
// Direct: extract local decidePluginApplication() in create-vite.ts.
// Schema-native: create-vite.ts + vite-plugin-policy.ts only if policy grows/reuses.
</example>

<example>
// Bad: turning one function into enterprise folder architecture.
feature/domain/application/infrastructure/adapters/usecases/factories
</example>
</context>

<pre-flight-checklist>
1. [ ] Did I compare the same responsibility?
2. [ ] Did schema-native avoid extra invented features?
3. [ ] Did I state which lens I am using?
</pre-flight-checklist>
