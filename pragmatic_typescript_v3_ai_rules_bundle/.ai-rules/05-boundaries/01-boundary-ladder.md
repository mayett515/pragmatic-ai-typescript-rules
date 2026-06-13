# Boundary Ladder

<meta-instruction>
Choose the smallest honest boundary. Move up the ladder only when the lower level cannot express ownership, framework integration, or lifecycle clearly.
</meta-instruction>

## Ladder

```txt
1. Pure function
2. Module function with explicit dependencies
3. Framework handler/hook/procedure/action
4. Service class for constructor DI or grouped use cases
5. Adapter/client/repository class for external systems
6. Worker/actor/process class for lifecycle/concurrency/retries
7. Generated client for schema-shaped external APIs
```

## Rules

<positive-directives>
- Start with function/module unless the repo/framework demands a class.
- Promote to class when dependency ownership is useful.
- Promote to adapter when external API shape must be hidden.
- Promote to worker when time, retry, concurrency, or lifecycle matters.
- Keep generated clients at external-schema boundaries.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT jump to service class before checking module function.
- DO NOT add adapter classes around internal pure functions.
- DO NOT use generated clients as domain models.
- DO NOT create worker boundaries without real asynchronous/lifecycle pressure.
</absolute-constraints>

<context>
<example>
// Good: module use case first.
export async function requestReturn(deps: ReturnDeps, input: ReturnInput) {}
</example>

<example>
// Bad: service class with one method in a module-style codebase.
class RequestReturnService { async execute(...) {} }
</example>
</context>

<pre-flight-checklist>
1. [ ] Which ladder level is sufficient?
2. [ ] What forces the next level up?
3. [ ] Is the chosen boundary honest?
</pre-flight-checklist>
