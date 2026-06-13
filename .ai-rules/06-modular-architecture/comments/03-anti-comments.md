# Anti-Comments

<meta-instruction>
Detect comments that create noise, lie over time, or hide bad code. Remove or replace with better names/structure.
</meta-instruction>

## Banned comment patterns

<absolute-constraints>
- DO NOT write comments that restate the next line.
- DO NOT write vague comments like "handle stuff" or "business logic".
- DO NOT write file headers that claim broad ownership without May/May NOT boundaries.
- DO NOT use comments to explain confusing code that can be made clear by naming a helper or type.
- DO NOT keep stale architecture comments after responsibility moves.
</absolute-constraints>

## Better replacements

<positive-directives>
- Replace narration with better function names.
- Replace vague comments with domain types.
- Replace stale file headers with May/May NOT responsibility contracts.
- Replace long inline explanations with a small pure helper if the concept deserves a name.
</positive-directives>

<context>
<example>
// Good replacement: name the concept.
const decision = decideMimePolicy(...);
</example>

<example>
// Bad comment: tells the reader nothing durable.
// Check MIME stuff.
</example>
</context>

<pre-flight-checklist>
1. [ ] Could a better name remove this comment?
2. [ ] Is the comment durable?
3. [ ] Does it define responsibility?
</pre-flight-checklist>
