# Framework Boundaries

<meta-instruction>
Frameworks often provide the boundary already. Do not wrap a framework handler in unnecessary architecture unless the handler is hiding domain decisions.
</meta-instruction>

## Framework examples

```txt
Next middleware
Remix action/loader
React component/hook
tRPC procedure
NestJS service/controller
Payload hook/access callback
VS Code command
n8n execute function
Redux slice/thunk
TanStack Query hook/queryFn
```

## Rules

<positive-directives>
- Let framework handlers read/write framework objects.
- Extract pure decisions and transformations from handlers when they grow.
- Map typed decisions to framework responses at the boundary.
- Respect framework contracts for thrown errors or return shapes.
- Avoid adding classes when the framework function is already the boundary.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT let request/response objects leak into the functional core.
- DO NOT create a service class around every route/action/procedure.
- DO NOT bury business policy inside JSX, middleware redirects, or tRPC errors.
- DO NOT fight a framework’s established error/return contract without clear benefit.
</absolute-constraints>

<context>
<example>
// Good: middleware delegates access decision.
const decision = decideRouteAccess(area, user);
return toNextResponse(decision);
</example>

<example>
// Bad: route policy hidden in redirects.
if (path.startsWith("/admin") && user.role !== "admin") redirect("/403");
</example>
</context>

<pre-flight-checklist>
1. [ ] What framework boundary already exists?
2. [ ] What pure logic should be extracted?
3. [ ] Is response mapping kept at the edge?
</pre-flight-checklist>
