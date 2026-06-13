# File Header Comments

<meta-instruction>
Use file headers when they clarify responsibility boundaries. Do not add headers to obvious tiny files.
</meta-instruction>

## Header schema

```ts
/**
 * Functional Core | Procedural Shell | Boundary | Adapter | Worker | Parser | Policy
 *
 * Purpose:
 * [one or two sentences]
 *
 * May:
 * - [allowed responsibility]
 * - [allowed responsibility]
 *
 * May NOT:
 * - [forbidden responsibility]
 * - [forbidden responsibility]
 */
```

## Rules

<positive-directives>
- Use `Purpose` to define why the file exists.
- Use `May` to define allowed responsibilities.
- Use `May NOT` to prevent architectural drift.
- Keep lists short and concrete.
- Add headers mainly to domain, shell, boundary, adapter, worker, parser, and policy files.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT add file headers to every tiny helper file.
- DO NOT list every function in the file header.
- DO NOT include stale "Used by" sections unless actively maintained.
- DO NOT write headers that repeat the filename only.
</absolute-constraints>

<pre-flight-checklist>
1. [ ] Does the header prevent drift?
2. [ ] Are May/May NOT concrete?
3. [ ] Is the file large/important enough to deserve it?
</pre-flight-checklist>
