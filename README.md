# Pragmatic TypeScript v3 AI Rules Bundle

This bundle is a full AI-rule ecosystem for a pragmatic TypeScript architecture style:

```txt
Type Strategy
→ Functional Core
→ Procedural Shell
→ Smallest Honest Boundary
```

The hidden `.ai-rules/` folder keeps the project root clean while remaining fully readable by CLIs, IDEs, LLMs, and automation tools.

## What this bundle contains

This is not a compressed one-file prompt. It is a modular rule system:

```txt
.ai-rules/
  00-system-index.md
  01-core/
  02-type-strategy/
  03-functional-core/
  04-procedural-shell/
  05-boundaries/
    oop/
  06-modular-architecture/
    comments/
  07-extension-lenses/
  08-repo-review/
  09-anti-regression/
  90-specs/
  91-templates/
```

## How to use it

Point your LLM or coding agent at `.ai-rules/00-system-index.md` first. The master index routes the agent into the correct subfiles.

For human review, start here:

1. `.ai-rules/01-core/00-core-index.md`
2. `.ai-rules/02-type-strategy/00-type-strategy-index.md`
3. `.ai-rules/05-boundaries/00-boundary-index.md`
4. `.ai-rules/06-modular-architecture/00-modular-index.md`
5. `.ai-rules/08-repo-review/00-review-index.md`

## Core sentence

```txt
Put meaning in types and pure functions.
Put execution in procedural shells.
Put ownership in boundaries.
```


## v3 Complete Addendum

This bundle includes a real-repo casebook preserving the stress tests that shaped the schema. The active schema is not only rules; it is calibrated by evidence from product workflows, UI components, parser boundaries, generated clients, config resolvers, and weak-fit restraint cases.
