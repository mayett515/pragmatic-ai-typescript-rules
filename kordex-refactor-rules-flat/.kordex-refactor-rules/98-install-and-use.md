---
description: "Installation and usage guide for the flat Kordex refactor rules add-on"
globs: "**/*"
alwaysApply: false
version: "1.0.0"
model_target: "universal-router-hybrid"
protocol_compat: "mcp: 2026-05"
last_updated: "2026-06-13"
priority_schema: "critical > strong > guideline"
dependencies: ["mcp-filesystem"]
---

# Install And Use

<meta-instruction>
You have been routed here because the user wants to install or use the Kordex refactor rules bundle. Keep the instructions flat, simple, and compatible with the existing Pragmatic TypeScript rules scheme.
</meta-instruction>

## Install

Place this hidden folder at the root of the Kordex repo or inside `codelens-rn`, depending on where the coding agent starts:

```bash
cp -R .kordex-refactor-rules /path/to/codelens-rn/
```

Keep the generic TypeScript rules separate:

```text
.ai-rules/                  # Pragmatic TypeScript v3 flat bundle
.kordex-refactor-rules/     # Kordex-specific ontology/refactor add-on
```

## Use With Codex Or Another Agent

<positive-directives>
- Load `.ai-rules/00-system-index.md` first for generic TypeScript style.
- Load `.kordex-refactor-rules/00-system-index.md` second for Kordex-specific refactor rules.
- Ask the agent to state which routed files it loaded before editing.
- Work in small slices: map, inspect symbols, change one layer, run tests, update graph/docs.
</positive-directives>

<absolute-constraints>
- DO NOT merge this folder into the generic TypeScript `.ai-rules/` unless you intentionally want one combined ecosystem.
- DO NOT rename routed files without updating `00-system-index.md`.
- DO NOT treat this add-on as mandatory law if the user only wants loose brainstorming.
</absolute-constraints>

<context>
Target Directory Scope: repo root or `codelens-rn` root.
Key Loading Order: generic TypeScript rules first, Kordex rules second.

<example>
// Good: explicit session start
Read `.ai-rules/00-system-index.md`, then `.kordex-refactor-rules/00-system-index.md`, then plan the operation-algebra refactor.
</example>

<example>
// Bad: generic rules and Kordex-specific rules mixed into one unclear folder with orphan docs
.ai-rules/random-kordex-notes/tooling/memory.md
</example>
</context>

<pre-flight-checklist>
Before using the bundle, internally verify:
1. [ ] Is the folder flat?
2. [ ] Did the agent load both routers in the correct order?
3. [ ] Are generic TypeScript rules and Kordex-specific rules still separate?
</pre-flight-checklist>
