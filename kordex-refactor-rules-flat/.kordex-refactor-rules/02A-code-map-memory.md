---
description: "Graphify, Serena, and Codebase-Memory usage rules for Kordex repo understanding"
globs: "**/*"
alwaysApply: false
version: "1.0.0"
model_target: "universal-router-hybrid"
protocol_compat: "mcp: 2026-05"
last_updated: "2026-06-13"
priority_schema: "critical > strong > guideline"
dependencies: ["graphify", "serena", "codebase-memory-mcp"]
---

# Code Map And Memory Contract

<meta-instruction>
You have been routed here because the task involves Graphify, Serena, Codebase-Memory MCP, repo maps, call graphs, or “what every function is for.” Use repo-memory tools as context providers, not authorities.
</meta-instruction>

## Why

Kordex has conceptual layers that are easy to confuse: ontology types, profile composition, checker runtime, proposal mapping, branch-local patches, persistence, and future operation algebra. A code graph helps, but function purpose should be made explicit with comments and rules.

<positive-directives>
- Use Graphify for conceptual architecture and doc-aware maps.
- Use Serena first when the agent must inspect or edit symbols precisely.
- Use Codebase-Memory MCP when persistent graph memory and repeated call-path questions become valuable.
- Ask tools for callers, callees, reads, writes, side effects, and layer ownership.
</positive-directives>

<absolute-constraints>
- DO NOT assume a function’s domain purpose from its name alone.
- DO NOT allow code-memory output to override accepted Kordex design decisions.
- DO NOT use both Serena and Codebase-Memory at the same time unless their roles are explicitly separated.
- DO NOT index secrets, credentials, or private external URLs into graph tools.
</absolute-constraints>

<conditional-logic>
IF the question is “what does this feature mean architecturally?”:
THEN prefer Graphify plus Kordex docs.

IF the question is “where is this symbol used and how do I edit it?”:
THEN prefer Serena or Codebase-Memory.
</conditional-logic>

<context>
Target Directory Scope: whole repo, especially `src/features/ontology` and `ONTOLOGY_PROFILE_REFACTOR`.
Key Tool Split: Graphify = architecture map; Serena = refactor hands; Codebase-Memory = persistent repo memory.

<example>
// Good: ask for specific ownership map
Find every function that writes profile proposals, its callers, and whether it bypasses the operation layer.
</example>

<example>
// Bad: ask a graph tool to invent a new architecture from summaries only
Design the new system based only on graph centrality.
</example>
</context>

<pre-flight-checklist>
Before relying on code memory, internally verify:
1. [ ] Did I distinguish conceptual map from symbol graph?
2. [ ] Did I cross-check with source files and tests?
3. [ ] Did I document true function intent where the tool had to infer it?
</pre-flight-checklist>
