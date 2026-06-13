# Review Format

<meta-instruction>
Use this exact structure for comprehensive repo/file reviews unless the user requests otherwise.
</meta-instruction>

## Required sections

<positive-directives>
- Start with repo/file and why it is a useful target.
- Show original shape or condensed code.
- Give an honest read before criticizing.
- Identify problems as target-responsibility issues.
- Show the schema version focused on that target.
- State the key win.
- Discuss boundary/OOP/file split only if relevant.
- Provide final schema strength and whole-file rewrite recommendation.
</positive-directives>

## Review skeleton

```txt
1. Repo / file
2. Original shape
3. Honest read
4. Target responsibility
5. Our schema version
6. Key win
7. Boundary/OOP decision
8. File split decision
9. Schema strength
10. Verdict
```

## Constraints

<absolute-constraints>
- DO NOT skip the honest read.
- DO NOT make every review a success story.
- DO NOT create educational mega-code when the user asks for fair file-to-file comparison.
</absolute-constraints>

<pre-flight-checklist>
1. [ ] Did I show before and after?
2. [ ] Did I avoid overclaiming?
3. [ ] Did I include the key win?
</pre-flight-checklist>
