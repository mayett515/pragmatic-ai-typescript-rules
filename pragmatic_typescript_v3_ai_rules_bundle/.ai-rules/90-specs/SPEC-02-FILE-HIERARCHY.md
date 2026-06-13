# SPEC-02: File Hierarchy and Routing

## Purpose

This document defines the rules-folder hierarchy. The v3 bundle allows concept folders and one nested subfolder where a concept genuinely owns a subdomain.

## Hierarchy Levels

```txt
Level 0:
  00-system-index.md

Level 1:
  concept folders such as 01-core, 02-type-strategy, 05-boundaries

Level 2:
  subdomain folders only when earned, such as boundaries/oop and modular-architecture/comments
```

## Routing Rules

<positive-directives>
- Route from broad concept indexes to specific rule files.
- Keep subfolder indexes as navigational hubs.
- Use paths relative to `.ai-rules/`.
- Keep active rule folders discoverable from `00-system-index.md` or a folder index.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT nest deeper than Level 2 without explicit user approval.
- DO NOT create orphan rule files not referenced by an index or manifest.
- DO NOT make terminal files route back upward.
- DO NOT split folders merely to mirror academic categories.
</absolute-constraints>

<pre-flight-checklist>
1. [ ] Is the file discoverable?
2. [ ] Is the nesting earned?
3. [ ] Does routing point downward or sideways?
</pre-flight-checklist>
