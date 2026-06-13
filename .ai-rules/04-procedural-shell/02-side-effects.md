# Side Effects

<meta-instruction>
Side effects are allowed in the shell. They should be explicit, ordered, and separated from pure rules.
</meta-instruction>

## Side-effect rules

<positive-directives>
- Keep DB reads/writes, HTTP calls, email, payments, queues, logging, and file IO in shell or boundary code.
- Keep system failures distinct from expected business failures.
- Prefer explicit try/catch where the shell can add context or map errors.
- Push provider-specific details into adapters.
- Pass data into pure helpers instead of letting helpers read global state.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT catch and ignore errors unless idempotent "already exists" behavior is explicitly intended and commented.
- DO NOT log inside pure decision functions.
- DO NOT call payment/email/external API before eligibility decisions pass.
- DO NOT return fake success after a failed side effect.
</absolute-constraints>

<context>
<example>
// Good: side effect happens after decision.
if (decision.kind === "allow") {
  await payments.refund({ amount: decision.refundAmount });
}
</example>

<example>
// Bad: payment happens before return eligibility is known.
await payments.refund(...);
const decision = decideReturn(...);
</example>
</context>

<pre-flight-checklist>
1. [ ] Is each side effect intentional and ordered?
2. [ ] Is provider-specific behavior isolated?
3. [ ] Are failures handled honestly?
</pre-flight-checklist>
