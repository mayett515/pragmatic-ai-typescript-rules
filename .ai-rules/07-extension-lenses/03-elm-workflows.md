# Elm Lens: Model, Message, Update, Command

<meta-instruction>
Use this lens only when the problem shape matches: UI workflows, multi-step forms, client state, command descriptions.
</meta-instruction>

## Guidance

<positive-directives>
- Use discriminated model/msg/update when workflow state is meaningful. Keep commands as descriptions interpreted by the shell.
- Keep the result idiomatic TypeScript.
- Map the lens back to Type Strategy, Functional Core, Procedural Shell, or Boundary.
- Apply the smallest useful form of the idea.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT apply this lens for novelty.
- DO NOT create abstractions that hide simple code.
- DO NOT violate existing repository conventions.
</absolute-constraints>

<context>
<example>
// Good: lens applied lightly.
type Msg = { type: "submit_clicked" } | { type: "submit_succeeded"; id: string };
</example>

<example>
// Bad: lens turned into framework ceremony without real need.
// Overengineered abstraction omitted intentionally.
</example>
</context>

<pre-flight-checklist>
1. [ ] Does the task actually match this lens?
2. [ ] Did the lens reveal meaning?
3. [ ] Did the code remain ordinary TypeScript?
</pre-flight-checklist>
