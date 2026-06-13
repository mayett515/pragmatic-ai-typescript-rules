# SPEC-01: Schema Generation Rules

## Purpose

This document governs how new `.md` rule files are created or edited.

## Format Selection Matrix

| Format | Use |
|---|---|
| YAML frontmatter | metadata, globs, versioning, dependencies |
| XML tags | behavioral control, constraints, routing, checklists |
| Markdown prose | explanation, headings, examples, navigation |

## Generation Rules

<absolute-constraints>
- DO NOT create more than 15 atomic rules inside one rule block.
- DO NOT combine multiple prohibitions in one bullet.
- DO NOT omit a bottom `<pre-flight-checklist>` from active rule files.
- DO NOT create rule files without version and protocol metadata.
- DO NOT generate vague placeholders in finalized files.
</absolute-constraints>

<positive-directives>
- Put routing and meta-instructions near the top.
- Put verification checklists at the bottom.
- Include one good and one bad example when a domain file teaches behavior.
- Use shallow files to avoid attention dilution.
- Prefer precise constraints over long essays.
</positive-directives>

<pre-flight-checklist>
1. [ ] Is the file focused?
2. [ ] Are constraints atomic?
3. [ ] Is routing clear?
</pre-flight-checklist>
