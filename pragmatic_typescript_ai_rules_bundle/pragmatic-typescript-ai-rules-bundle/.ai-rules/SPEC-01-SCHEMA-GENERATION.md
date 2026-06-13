---
description: "Specification for generating new AI rule markdown files in this ecosystem"
globs: ".ai-rules/**/*.md"
alwaysApply: false
version: "1.0.0"
model_target: "universal-router-hybrid"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Engineering Specification: Schema Generation & Anti-Regression Rules

<meta-instruction>
Use this file when generating or editing `.ai-rules` markdown files. The goal is compact, durable operational guidance that models behavior without flooding the target model with too many rules.
</meta-instruction>

## 1. Polyglot Format Selection Matrix

| Format Syntax | Functional Domain | Model Treatment |
| :--- | :--- | :--- |
| YAML Frontmatter | Metadata, globs, tools, protocol compatibility | Immutable schema memory |
| XML Body Tags | Constraints, gates, behavior rules | Hard operational fences |
| Markdown Prose | Explanations, examples, navigation | Section anchors and readable context |

## 2. Generation Rules

<positive-directives>
- You MUST keep each generated rule file focused on one domain or one cross-cutting concern.
- You MUST place routing and meta-instructions near the top.
- You MUST place the pre-flight checklist at the absolute bottom.
- You MUST include exactly one compliant example and one non-compliant example in domain files.
- You MUST write rules as operational instructions, not essays.
</positive-directives>

## 3. Hard Generation Constraints

<absolute-constraints>
- DO NOT exceed 15 total positive directives and absolute constraints in one generated rule file.
- DO NOT combine multiple unrelated prohibitions in one bullet.
- DO NOT create upward routing references from sub-files to the master router.
- DO NOT create hidden magic rules that are not visible in markdown.
- DO NOT use XML tags for long tutorials.
- DO NOT put implementation examples in YAML frontmatter.
</absolute-constraints>

## 4. Context and Examples

<context>
Target Directory Scope: `.ai-rules/**/*.md`
Key Principle: YAML for metadata, XML for gates, Markdown for explanation.

<example>
// Good: one atomic prohibition inside absolute constraints.
<absolute-constraints>
- DO NOT call external APIs from functional core helpers.
</absolute-constraints>
</example>

<example>
// Bad: compound conversational prohibition that mixes several behaviors.
<absolute-constraints>
- Don't call APIs or mutate things or use weird classes because that causes bad architecture and testing problems.
</absolute-constraints>
</example>
</context>

## 5. Schema Generation Pre-Flight Verification

<pre-flight-checklist>
Before finalizing a generated `.md` rule file, verify:
1. [ ] Did I keep the rule count under the limit?
2. [ ] Did I use YAML, XML, and Markdown for their intended purposes?
3. [ ] Did I include one good and one bad example for domain files?
4. [ ] Did I avoid upward routing references?
5. [ ] Did I keep the checklist at the bottom?
</pre-flight-checklist>
