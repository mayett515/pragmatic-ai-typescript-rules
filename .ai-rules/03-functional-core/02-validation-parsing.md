# Validation and Parsing

<meta-instruction>
Parsing turns unknown outside data into trusted inside data. Treat important parsers as domain boundaries, not as incidental string manipulation.
</meta-instruction>

## Parser rules

<positive-directives>
- Use `unknown` for untrusted external input.
- Return typed parse results for expected malformed input.
- Name parse outcomes when several content types are possible.
- Keep schema/library parsing separate from business policy when the policy deserves a name.
- Keep raw external records out of persistence code.
</positive-directives>

## Parser constraints

<absolute-constraints>
- DO NOT cast `unknown` directly to a domain type and continue.
- DO NOT silently swallow malformed structured data.
- DO NOT use unnamed regex fragments for business-relevant text parsing.
- DO NOT parse and persist in the same function when the parsed meaning is important.
</absolute-constraints>

<context>
<example>
// Good: clipboard content is classified.
type ClipboardDecision =
  | { kind: "mixed_content"; value: MixedContent }
  | { kind: "app_elements"; elements: readonly Element[] }
  | { kind: "plain_text"; value: string };
</example>

<example>
// Bad: JSON parse result is used blindly.
const data = JSON.parse(text);
await db.insert(data as any);
</example>
</context>

<pre-flight-checklist>
1. [ ] What external format is being parsed?
2. [ ] What are the valid outcomes?
3. [ ] Are malformed inputs expected and typed?
</pre-flight-checklist>
