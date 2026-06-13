# File Splitting

<meta-instruction>
Split files when the split improves understanding, testability, reuse, or boundary ownership. Do not split because architecture diagrams look cleaner.
</meta-instruction>

## Split triggers

<positive-directives>
- Split when pure policy logic is dense and testable separately.
- Split when a file contains multiple stable responsibilities.
- Split when helpers are reused by several files.
- Split when boundary code and domain code obscure each other.
- Split when comments would be clearer as file headers for separate modules.
- Keep one file when a feature is small and cohesive.
</positive-directives>

## Split constraints

<absolute-constraints>
- DO NOT split by "types/errors/helpers" automatically.
- DO NOT create index barrel files that hide ownership unless repo convention requires them.
- DO NOT move local helper functions global without reuse or domain value.
- DO NOT split generated code manually.
</absolute-constraints>

<context>
<example>
// Good: service stays shell-like.
asset-edit.domain.ts   // decideAssetEdit
asset-edit.errors.ts   // map errors to framework exceptions
asset.service.ts       // load asset, call decision, save, queue job
</example>

<example>
// Bad: every helper becomes a file.
applyMaxCount.ts
shouldEmitChange.ts
beforeUploadDecision.ts
uploadTypes.ts
</example>
</context>

<pre-flight-checklist>
1. [ ] Does this split reduce cognitive load?
2. [ ] Would a reader know where to look?
3. [ ] Is the split still local to the feature?
</pre-flight-checklist>
