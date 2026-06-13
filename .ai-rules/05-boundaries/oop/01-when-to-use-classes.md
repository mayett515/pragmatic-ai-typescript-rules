# When To Use Classes

<meta-instruction>
Use classes when ownership is real. Do not use classes because the code "has dependencies" unless dependency ownership itself is useful.
</meta-instruction>

## Strong class cases

<positive-directives>
- Use classes for external clients and adapters.
- Use classes for repositories and persistence adapters when repo style expects them.
- Use classes for stateful resources: caches, queues, rate limiters, connection pools, WebSocket managers.
- Use classes for workers/actors/schedulers with lifecycle or owned mutation.
- Use classes for framework DI boundaries such as NestJS/Angular services/controllers.
- Use classes for multiple related use cases sharing stable dependencies.
- Use classes for `start`, `stop`, `dispose`, `connect`, `close`, or lifecycle ownership.
</positive-directives>

## Weak class cases

<absolute-constraints>
- DO NOT use classes for one pure calculation.
- DO NOT use classes for one mapper.
- DO NOT use classes for one parser.
- DO NOT use classes for a single use case in a module-style codebase unless framework DI requires it.
- DO NOT use classes as naming decoration.
</absolute-constraints>

<context>
<example>
// Good: class owns a stateful/external capability.
class RedisRateLimiter {
  constructor(private readonly redis: RedisClient) {}
  async consume(key: string) { /* external state */ }
}
</example>

<example>
// Bad: class owns no capability.
class EmailNormalizer { normalize(email: string) { return email.trim().toLowerCase(); } }
</example>
</context>

<pre-flight-checklist>
1. [ ] Does this class own capability, resource, lifecycle, or framework role?
2. [ ] Would a function/module be simpler?
3. [ ] Does the class keep policy out of infrastructure?
</pre-flight-checklist>
