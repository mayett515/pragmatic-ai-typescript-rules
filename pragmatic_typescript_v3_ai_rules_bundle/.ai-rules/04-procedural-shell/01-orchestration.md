# Orchestration

<meta-instruction>
Procedural orchestration is not bad. It is the correct style for workflows, routes, scripts, jobs, commands, and service methods that coordinate effects.
</meta-instruction>

## Orchestration rules

<positive-directives>
- Keep workflows top-to-bottom and readable.
- Name each meaningful step with a variable or helper.
- Ask pure functions to decide before executing irreversible effects.
- Return typed failures for expected business outcomes when the codebase supports them.
- Keep framework-specific response mapping near framework boundaries.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT force declarative chains onto ordered side effects.
- DO NOT mix multiple unrelated workflows into one function.
- DO NOT continue after a failed business decision.
- DO NOT let a use-case shell grow into a god method without extracting decisions.
</absolute-constraints>

<context>
<example>
// Good: recipe-like orchestration.
const candidate = deriveImportedFileCandidate(response);
const mimeDecision = decideMimePolicy(candidate);
if (mimeDecision.kind === "denied") throw toMimeError(mimeDecision);
return uploadFile(stream, candidate);
</example>

<example>
// Bad: external fetch, MIME policy, upload, and error messages tangled together.
</example>
</context>

<pre-flight-checklist>
1. [ ] Can a reader summarize the workflow from variable names?
2. [ ] Are irreversible effects after validation/decision?
3. [ ] Is this function still one use case?
</pre-flight-checklist>
