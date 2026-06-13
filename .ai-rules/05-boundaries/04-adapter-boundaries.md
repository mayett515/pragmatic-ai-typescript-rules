# Adapter, Client, and Repository Boundaries

<meta-instruction>
Use adapters to hide external systems and persistence weirdness. This is one of the strongest justified OOP zones.
</meta-instruction>

## Adapter rules

<positive-directives>
- Use adapter/client classes for Stripe, SendGrid, S3, Redis, OpenAI, external HTTP APIs, and SDKs.
- Use repositories/adapters to hide persistence implementation details.
- Keep external request/response mapping inside the adapter.
- Expose narrow application-facing ports.
- Add logging/retry/metrics wrappers at boundary level when needed.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT let provider-specific SDK shapes spread through use cases.
- DO NOT put business eligibility rules inside adapters.
- DO NOT make repositories god services with unrelated methods.
- DO NOT wrap a stable internal function as an adapter.
</absolute-constraints>

<context>
<example>
// Good: app uses a clean port.
type PaymentProvider = { refund(input: RefundInput): Promise<void> };
class StripePaymentProvider implements PaymentProvider { /* Stripe mapping */ }
</example>

<example>
// Bad: Stripe SDK shape leaks into return use case.
await stripe.refunds.create({ payment_intent: order.payment.id, amount });
</example>
</context>

<pre-flight-checklist>
1. [ ] What external weirdness is hidden?
2. [ ] Is the exposed port narrow?
3. [ ] Are business rules outside the adapter?
</pre-flight-checklist>
