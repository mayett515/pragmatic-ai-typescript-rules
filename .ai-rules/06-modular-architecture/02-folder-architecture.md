# Folder Architecture

<meta-instruction>
Folders should express domains, capabilities, or rule categories. Avoid deep trees unless the hierarchy prevents real confusion.
</meta-instruction>

## Folder rules

<positive-directives>
- Organize product code by domain/feature first when possible.
- Use subfolders for stable categories: domain, shell/use-case, adapters, workers, components, tests.
- Keep pure helpers near the feature until they become shared concepts.
- Use adapter folders for external systems.
- Use comments or README files only when a folder’s responsibilities are not obvious.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT create domain-less folders named only `utils`, `helpers`, or `misc` when a domain name exists.
- DO NOT create deep folder hierarchies to display architectural purity.
- DO NOT move framework files away from framework conventions without strong reason.
- DO NOT create shared folders that become dumping grounds.
</absolute-constraints>

<context>
<example>
// Good feature-centric layout.
asset-edit/
  asset-edit.domain.ts
  asset-edit.errors.ts
  asset-edit.test.ts
</example>

<example>
// Bad vague shared dump.
utils/
  thing1.ts
  thing2.ts
  helpers.ts
</example>
</context>

<pre-flight-checklist>
1. [ ] Is the folder name domain-specific?
2. [ ] Does the hierarchy help navigation?
3. [ ] Did I respect repo conventions?
</pre-flight-checklist>
