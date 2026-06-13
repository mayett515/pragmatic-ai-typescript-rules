# Generated Types and Codegen Boundaries

<meta-instruction>
Use generated types as source-of-truth boundaries. Do not edit generated code. Map generated protocol/persistence types into internal domain types when meaning differs.
</meta-instruction>

## Good uses

<positive-directives>
- Use Prisma, GraphQL, OpenAPI, ATProto Lexicon, or SDK-generated types at the integration edge.
- Use small mapping functions when generated shapes differ from internal domain language.
- Treat generated code as boring output from a clear schema.
- Keep the source schema obvious and reproducible.
- Use generated clients as boundaries, not as the functional core.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT hand-edit generated files.
- DO NOT duplicate generated types by copying their full shape manually.
- DO NOT let raw generated protocol data leak deep into business logic if the app needs internal variants.
- DO NOT hide business decisions inside code generators.
</absolute-constraints>

<context>
<example>
// Good: generated persistence shape is used at the edge.
function toPrismaUserCreateData(input: CreateUserInput): Prisma.UserCreateInput {
  return { email: input.email, name: input.name, role: input.role };
}
</example>

<example>
// Bad: protocol data goes directly into side effects everywhere.
await db.records.insert(rawLexiconRecord as any);
</example>
</context>

<pre-flight-checklist>
1. [ ] What schema generates this type?
2. [ ] Is mapping needed between generated and domain language?
3. [ ] Is generated code untouched and reproducible?
</pre-flight-checklist>
