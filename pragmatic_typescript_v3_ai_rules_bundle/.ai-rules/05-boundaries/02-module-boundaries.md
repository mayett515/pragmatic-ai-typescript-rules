# Module Boundaries and Dependency Objects

<meta-instruction>
Use module boundaries for use cases that need dependencies but do not need long-lived ownership or framework DI.
</meta-instruction>

## Module boundary rules

<positive-directives>
- Pass dependencies explicitly as a narrow object when a use case has side effects.
- Keep dependency types as ports/capabilities, not concrete implementations.
- Keep pure decisions imported from domain modules.
- Keep module use cases readable and procedural.
- Promote to service class only when ownership, grouping, or framework integration earns it.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT pass global app containers into use cases.
- DO NOT import concrete external clients directly into the functional core.
- DO NOT over-split one use case into many dependency-wrapper files.
- DO NOT create a class just to store a dependency object.
</absolute-constraints>

<context>
<example>
// Good: narrow dependency object.
type CreateUserDeps = { users: Pick<UserRepository, "exists" | "create"> };
export async function createUser(deps: CreateUserDeps, input: unknown) {}
</example>

<example>
// Bad: concrete dependency hardcoded.
import { prisma } from "../global";
export async function createUser(input: unknown) { await prisma.user.create(...); }
</example>
</context>

<pre-flight-checklist>
1. [ ] Are dependencies explicit and narrow?
2. [ ] Is a class unnecessary here?
3. [ ] Does the module function remain readable?
</pre-flight-checklist>
