# Workers, Concurrency, Retries, and Message Ownership

<meta-instruction>
Use message-based thinking for concurrent work, background jobs, retries, queues, cancellation, and shared mutable state.
</meta-instruction>

## Worker rules

<positive-directives>
- Use typed message/job unions for queue or worker inputs.
- Give mutable processing state one owner.
- Use explicit retry/backoff/cancellation policies near the shell.
- Use `AbortSignal` when cancellation matters.
- Use worker/actor classes when they own queue lifecycle, state, retries, or resources.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT modify shared mutable maps/sets from unrelated modules.
- DO NOT fire-and-forget promises without failure handling.
- DO NOT create actor/worker abstractions for direct calls.
- DO NOT hide retries inside pure-looking helpers.
</absolute-constraints>

<context>
<example>
// Good: typed job and owned worker boundary.
type EmailJob =
  | { type: "send_welcome"; email: string }
  | { type: "send_receipt"; orderId: string; email: string };

class EmailWorker { async handle(job: EmailJob) { /* side effects */ } }
</example>

<example>
// Bad: global mutable set modified by many callers.
const processing = new Set<string>();
</example>
</context>

<pre-flight-checklist>
1. [ ] Is there real concurrency or background work?
2. [ ] Who owns mutable state?
3. [ ] What is the failure/retry/cancel strategy?
</pre-flight-checklist>
