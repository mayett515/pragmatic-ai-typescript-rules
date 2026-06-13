---
description: "File tree for the flat Kordex refactor rules bundle"
globs: ".kordex-refactor-rules/**/*.md"
alwaysApply: false
version: "1.0.0"
model_target: "universal-router-hybrid"
protocol_compat: "mcp: 2026-05"
last_updated: "2026-06-13"
priority_schema: "critical > strong > guideline"
dependencies: []
---

# File Tree

<meta-instruction>
This file exists so humans and agents can verify the bundle structure without scanning the ZIP manually. It is informational, but still has YAML frontmatter so it is not an orphan-style document.
</meta-instruction>

## Flat Directory

```text
.kordex-refactor-rules/
  README.md
  00-system-index.md
  01-operation-type-system.md
  01A-proposal-events.md
  01B-effect-runtime-spike.md
  01C-testing-invariants.md
  02-refactor-toolchain.md
  02A-code-map-memory.md
  02B-boundaries-codemods.md
  02C-function-catalog.md
  03-agent-checker-safety.md
  04-package-policy.md
  05-anti-regression.md
  98-install-and-use.md
  99-file-tree.md
```

## Why This Matches The Scheme

<positive-directives>
- The bundle uses one hidden folder.
- Every markdown file has YAML frontmatter.
- `00-system-index.md` directly routes to active rule files.
- The operation/type-system files and refactor/toolchain files are separated by prefixes, not nested folders.
</positive-directives>

<absolute-constraints>
- DO NOT add `tooling-examples/` below this folder.
- DO NOT add `codex-prompts/` below this folder.
- DO NOT add `operation/`, `runtime/`, `invariants/`, or `policies/` subfolders until the schema itself changes.
</absolute-constraints>

<context>
Target Directory Scope: `.kordex-refactor-rules/`
Key Design: flat machine routing.

<example>
// Good: horizontal split
01-operation-type-system.md
01A-proposal-events.md
01B-effect-runtime-spike.md
</example>

<example>
// Bad: deep human-readable folder tree
operation/type-system/events/errors.md
</example>
</context>

<pre-flight-checklist>
Before changing the file tree, internally verify:
1. [ ] Does the router point to every active rule file?
2. [ ] Did I avoid nested folders?
3. [ ] Did every markdown file keep YAML frontmatter?
</pre-flight-checklist>
