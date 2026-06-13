# Decision Algorithm

<meta-instruction>
Use this algorithm before refactoring or designing. It prevents premature abstraction and forces target-responsibility analysis.
</meta-instruction>

## Algorithm

<positive-directives>
- Identify the target responsibility, not merely the containing file.
- Identify external inputs and whether they are trusted or unknown.
- Identify pure decisions, policies, validations, transformations, or state transitions.
- Identify side effects and their required order.
- Identify existing repo boundaries before creating new ones.
- Choose the smallest honest boundary.
- Apply extension lenses only after the code shape is known.
- Rate schema strength for the target responsibility, not the whole file by default.
</positive-directives>

## Stop Conditions

<absolute-constraints>
- DO NOT refactor tiny pure utilities merely to match the schema.
- DO NOT create local infrastructure if the repo already has a global helper or boundary.
- DO NOT introduce Result types when the framework already has a clear error contract and no expected failure model is improved.
- DO NOT replace a readable switch with a registry unless the registry reveals a real table or extension point.
</absolute-constraints>

## Output Decision

<context>
After analysis, choose one:

```txt
Confirm existing design
Light local helper extraction
Schema-native file split
Boundary class/adaptor/worker extraction
No change because ceremony would exceed meaning
```
</context>

<pre-flight-checklist>
1. [ ] Did I identify the hidden concept?
2. [ ] Did I check whether it is already represented elsewhere?
3. [ ] Did I avoid forcing the schema onto weak-fit code?
</pre-flight-checklist>
