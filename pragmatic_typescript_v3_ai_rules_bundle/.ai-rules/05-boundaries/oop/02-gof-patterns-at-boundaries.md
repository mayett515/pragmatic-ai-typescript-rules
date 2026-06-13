# GoF Patterns at Boundaries

<meta-instruction>
Use GoF patterns as names for boundary problem shapes, not as instructions to create class hierarchies.
</meta-instruction>

## Boundary pattern mapping

<positive-directives>
- Adapter hides external provider or SDK shapes.
- Facade simplifies several capabilities behind one boundary.
- Proxy wraps access, cache, auth, retry, or lazy initialization.
- Decorator adds logging, metrics, retry, tracing, or caching around a port.
- Factory creates clients/adapters from config.
- Command models jobs, actions, queue messages, and command runners.
- State models lifecycle only when union transitions are insufficient.
- Strategy models swappable policies when variation is real.
- Observer models subscriptions/events/notifications.
- Composite models trees such as AST, UI, workflow graphs, or shape hierarchies.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT apply GoF patterns for their own sake.
- DO NOT replace a simple discriminated union with a class hierarchy unless ownership or extensibility is real.
- DO NOT use Strategy when a switch over a small union is clearer.
- DO NOT use Factory when direct construction is stable and obvious.
</absolute-constraints>

<context>
<example>
// Good: Adapter-shaped boundary.
class SendGridEmailClient implements EmailClient { /* maps app email to SendGrid */ }
</example>

<example>
// Bad: Strategy ceremony for two simple cases.
class SeniorTierStrategy {}
class StandardTierStrategy {}
</example>
</context>

<pre-flight-checklist>
1. [ ] What problem shape does the pattern solve?
2. [ ] Is ownership/collaboration real?
3. [ ] Would a union/function be simpler?
</pre-flight-checklist>
