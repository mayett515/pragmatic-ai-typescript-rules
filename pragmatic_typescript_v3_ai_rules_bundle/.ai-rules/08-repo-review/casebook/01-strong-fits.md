---
description: "Strong-fit repo cases: business workflows, hidden policies, lifecycle decisions"
globs: "**/*.{ts,tsx}"
alwaysApply: false
version: "3.0.0"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Casebook: Strong Fits

<meta-instruction>
These cases show where the schema is strongest: hidden business meaning, lifecycle decisions, and policies mixed with side effects.
</meta-instruction>

## Cal.com booking limits

<context>
Target responsibility: booking-limit evaluation for recurring booking candidates.

Key discovery:
```txt
Evaluate limits against the complete candidate set,
not one booking occurrence in isolation.
```

Key type:
```ts
type BookingLimitDecision =
  | { kind: "allow" }
  | { kind: "deny"; reason: "booking_limit_exceeded"; window: BookingLimitWindow };
```

Schema lesson:
- Fetch existing bookings in the shell.
- Build candidate bookings as data.
- Decide limit violation in the functional core.
- Insert bookings only after the decision succeeds.
</context>

## Medusa order items / custom line items

<context>
Target responsibility: preparing order line items.

Key discovery:
```txt
The bug was not length; the type model was lying.
```

Key type:
```ts
type OrderItemInput =
  | { kind: "variant_item"; variantId: string; quantity: number }
  | { kind: "custom_item"; title: string; quantity: number; unitPrice: number };
```

Schema lesson:
- Replace unsafe non-null assumptions with honest variants.
- Use `Result` for expected missing variant failures.
- Keep the transformation as plain data in / plain data out.
</context>

## Immich asset editing

<context>
Target responsibility: `editAsset` eligibility and crop validation.

Key win:
```ts
function decideAssetEdit(asset, edits): Result<AssetEditDecision, AssetEditEligibilityError>
```

Rules extracted:
- asset must exist
- asset must be image
- live photo / panorama / GIF / SVG not supported
- dimensions must exist
- crop must be first
- crop must be in bounds

Schema lesson:
- Keep `AssetService` as NestJS boundary/shell.
- Extract asset-edit decision logic into pure core.
- Map domain errors to framework exceptions at the boundary.
</context>

## Directus file import

<context>
Target responsibility: imported-file candidate and MIME policy.

Key type:
```ts
type MimePolicyDecision =
  | { kind: "allowed" }
  | { kind: "denied"; reason: "global_mime_type_denied" | "interface_mime_type_denied"; mimeType: string };
```

Schema lesson:
- Do not rewrite the whole `FilesService`.
- Extract MIME policy and candidate derivation only.
- Keep HTTP fetch and upload delegation in the procedural shell.
</context>

## Supabase Auth session initialization

<context>
Target responsibility: session initialization plan inside `GoTrueClient`.

Key type:
```ts
type InitializeSessionPlan =
  | { kind: "recover_from_url"; callbackUrlType: "implicit" | "pkce" }
  | { kind: "recover_from_storage" };
```

Schema lesson:
- `GoTrueClient` is a real OOP boundary because it owns storage, locks, fetch, BroadcastChannel, session lifecycle, subscribers, and auto-refresh.
- Do not fight justified OOP.
- Extract the hidden initialization policy into a typed plan.
</context>

## Firecrawl crawl controller

<context>
Target responsibilities:
- prompt-generated option merge
- crawl limit by credits
- zero-data-retention decision
- path regex validation

Key types:
```ts
type PromptOptionMergeDecision =
  | { kind: "keep_user_value"; key: string }
  | { kind: "apply_prompt_value"; key: string; value: unknown };

type CrawlLimitDecision =
  | { kind: "auth_disabled"; limit: number }
  | { kind: "clamped_by_credits"; requested: number; remainingCredits: number; limit: number };
```

Schema lesson:
- Product API controllers often hide multiple policies.
- Extract policy decisions, not the whole controller.
- The controller remains the Express shell.
</context>

<pre-flight-checklist>
1. [ ] Did I identify the specific hidden policy/lifecycle decision?
2. [ ] Did I avoid claiming the whole service/controller must be rewritten?
3. [ ] Did I keep effects in the shell and decisions in the core?
</pre-flight-checklist>
