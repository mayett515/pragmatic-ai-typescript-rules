# Policy Extraction Template

## Hidden Policy

```txt
[name the policy]
```

## Current Problem

```txt
[where the policy is currently hidden]
```

## Decision Type

```ts
type [Policy]Decision =
  | { kind: "allow" }
  | { kind: "deny"; reason: [Reason] };
```

## Pure Decision Function

```ts
function decide[Policy](input: [Input]): [Policy]Decision {
  // no DB, no framework, no logging, no external API
}
```

## Boundary Mapping

```ts
function toFrameworkResult(decision: [Policy]Decision) {
  // map at the edge
}
```

## Checklist

```txt
- Does the policy name reveal meaning?
- Is the function pure?
- Are side effects still in the shell?
- Is the boundary mapping explicit?
```
