# Strength Ratings

<meta-instruction>
Ratings measure how strongly the integrated schema improves the target responsibility. "Our schema" means base + extension lenses.
</meta-instruction>

## Rating guidance

```txt
9-10: Strong hidden meaning/lifecycle/policy becomes explicit.
8-9: Good seam extraction; useful but not revolutionary.
6-8: Mixed; improvement possible but ceremony risk.
4-6: Weak; mostly confirms existing design.
1-4: Do not apply beyond tiny cleanup.
```

## Required rating context

<positive-directives>
- Name the exact target being rated.
- Include original score when useful.
- Include schema score.
- State whether whole-file rewrite is recommended.
- State over-refactor risk.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT rate the entire repository from one file.
- DO NOT score generated code as if it should be manually refactored.
- DO NOT give 9+ unless there is a real key win.
</absolute-constraints>

<context>
<example>
Target: parseClipboard classification logic
Original: 7.5/10
Our schema: 9/10
Whole-file rewrite: No
Key win: clipboard content outcomes become a typed decision union.
</example>
</context>

<pre-flight-checklist>
1. [ ] Did I rate the target?
2. [ ] Did I justify 9+ scores?
3. [ ] Did I mention ceremony risk?
</pre-flight-checklist>
