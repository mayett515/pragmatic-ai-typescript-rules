# Mental Model: Meaning, Execution, Ownership

<meta-instruction>
Use this file to explain the schema intuitively. Do not name-drop paradigms unless it clarifies a concrete design choice.
</meta-instruction>

## One Sentence

```txt
Put meaning in types and pure functions.
Put execution in procedural shells.
Put ownership in boundaries.
```

## What "meaning" means

Meaning is the part of code that answers:

```txt
What state is this?
What decision was made?
Why was this denied?
What policy applies?
What lifecycle transition occurred?
What external input has been validated?
```

Meaning should usually appear as:

```txt
domain-specific types
explicit decision unions
named pure functions
small parser outputs
state transition functions
policy helpers
```

## What "execution" means

Execution is the part that does real-world work:

```txt
load from DB
call API
send email
refund payment
queue job
write file
log output
return framework response
```

Execution is allowed to be procedural and step-by-step.

## What "ownership" means

Ownership appears when a thing owns:

```txt
external system
stateful resource
dependency group
framework lifecycle
queue/worker/retry loop
connection/client/cache
```

Ownership may justify a class, adapter, worker, or service boundary.

## Main warning

If the schema makes code longer without naming a hidden concept, it is probably ceremony.
