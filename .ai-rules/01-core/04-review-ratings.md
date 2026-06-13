# Schema Strength Ratings

<meta-instruction>
Use ratings to communicate schema fit honestly. Ratings apply to target responsibilities, not automatically to whole files.
</meta-instruction>

## Rating scale

```txt
10/10  Transformational. Hidden domain/lifecycle/policy becomes obvious.
9/10   Strong. Clear meaning extraction with little downside.
8/10   Useful. Improves readability/testability at specific seams.
6-7/10 Mixed. Some improvement, but ceremony risk exists.
4-5/10 Weak. Mostly confirms existing design or helps only lightly.
1-3/10 Do not apply. Code is already tiny, generated, glue, or algorithmic.
```

## Required rating fields

<positive-directives>
- Rate the original code for its actual purpose.
- Rate the schema-applied target responsibility.
- State whether a whole-file rewrite is recommended.
- State the key win in one sentence.
- State the ceremony risk.
</positive-directives>

## Rating constraints

<absolute-constraints>
- DO NOT rate a whole repository based on one extracted helper.
- DO NOT imply the entire file should be rewritten when only one policy seam was targeted.
- DO NOT overrate refactors that only rename obvious code.
</absolute-constraints>

<context>
Example:

```txt
Target: MIME policy inside FilesService
Original: 7.5/10
Our schema: 8.7/10
Whole-file rewrite: No
Key win: MIME allow-list logic becomes a testable decision.
Ceremony risk: extracting every file-service helper would be too much.
```
</context>

<pre-flight-checklist>
1. [ ] Did I rate the target responsibility?
2. [ ] Did I avoid inflated scores?
3. [ ] Did I state the key win clearly?
</pre-flight-checklist>
