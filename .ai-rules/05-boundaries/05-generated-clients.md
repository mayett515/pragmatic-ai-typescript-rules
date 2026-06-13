# Generated Clients as Boundaries

<meta-instruction>
Generated clients are boundary artifacts. They should be boring, reproducible, and treated as external-schema integration points.
</meta-instruction>

## Rules

<positive-directives>
- Use generated clients where external schemas are source of truth.
- Keep generated files marked and reproducible.
- Wrap generated clients only when app-level semantics differ from client semantics.
- Map generated API errors to app errors at the shell/boundary.
- Prefer schema-native generation over manual sync of repeated endpoint/client code.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT hand-edit generated clients.
- DO NOT hide manual business logic in generation templates.
- DO NOT expose generated protocol records as domain types when app semantics differ.
- DO NOT generate code when explicit code is clearer and repetition is small.
</absolute-constraints>

<context>
<example>
// Good: generated client is called from boundary shell.
const record = await atprotoClient.getRecord(uri);
const parsed = parseSupportedRecord(record);
</example>

<example>
// Bad: generated protocol shape is persisted everywhere without classification.
await db.insert(record as any);
</example>
</context>

<pre-flight-checklist>
1. [ ] Is codegen justified by repetition/schema source of truth?
2. [ ] Is generated output untouched?
3. [ ] Is mapping needed into internal domain language?
</pre-flight-checklist>
