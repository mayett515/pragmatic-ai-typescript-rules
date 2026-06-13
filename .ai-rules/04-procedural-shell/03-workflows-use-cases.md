# Workflows and Use Cases

<meta-instruction>
Use this file for checkout, booking, returns, subscription changes, asset edits, imports, exports, and multi-step product workflows.
</meta-instruction>

## Workflow rules

<positive-directives>
- Identify the central hidden decision or lifecycle in each workflow.
- Keep the shell responsible for sequencing, not calculating policy inline.
- Use narrow dependency objects or service classes based on repo style.
- Keep long workflow methods readable by extracting policies, not arbitrary helpers.
- Prefer one use-case file before splitting into a full folder.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT extract every line into a helper.
- DO NOT pass raw request bodies through the whole workflow.
- DO NOT let framework exceptions become the only domain model.
- DO NOT force a class boundary when a module use-case function is the repo convention.
</absolute-constraints>

<context>
<example>
// Good: core policy extracted.
const decision = decideAssetEdit(asset, edits);
if (!decision.ok) throw toBadRequest(decision.error);
await assetEditRepository.replaceAll(id, decision.value.edits);
</example>

<example>
// Bad: 12 inline checks and job queueing mixed without named policy.
</example>
</context>

<pre-flight-checklist>
1. [ ] What is the workflow’s central decision?
2. [ ] What belongs to the shell?
3. [ ] Is extraction based on meaning, not line count alone?
</pre-flight-checklist>
