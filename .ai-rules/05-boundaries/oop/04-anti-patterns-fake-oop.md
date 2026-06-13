# Fake OOP and Class Ceremony

<meta-instruction>
Use this file to detect class-based overengineering. Refactor toward functions/modules when ownership is fake.
</meta-instruction>

## Fake OOP signs

<absolute-constraints>
- DO NOT create classes with one method and no state/dependencies.
- DO NOT create class hierarchies for simple variants.
- DO NOT make mutable entity objects that secretly perform side effects.
- DO NOT create god services that validate, calculate, persist, notify, log, and integrate providers in one method.
- DO NOT use inheritance where composition or a discriminated union is clearer.
- DO NOT use singleton classes for ordinary stateless helpers.
</absolute-constraints>

## Recovery moves

<positive-directives>
- Move pure rules into functions.
- Keep the class as a dependency owner if it is still useful.
- Replace class variants with discriminated unions when behavior is operation-centric.
- Split adapters by external capability.
- Use module functions for single use cases in module-style repos.
</positive-directives>

<context>
<example>
// Good recovery: class shells delegate policy.
class ReturnService {
  async requestReturn(input: ReturnInput) {
    const decision = decideReturn(order, input);
  }
}
</example>

<example>
// Bad: business policy trapped in giant service method.
class ReturnService { async requestReturn(...) { /* everything */ } }
</example>
</context>

<pre-flight-checklist>
1. [ ] Does the class own something real?
2. [ ] Is business meaning extractable?
3. [ ] Is inheritance avoidable?
</pre-flight-checklist>
