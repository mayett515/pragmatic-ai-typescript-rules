# Anti-Regression Template Notes

<meta-instruction>
Use this as a human guide. For actual generated files, use `91-templates/TEMPLATE-ANTI-REGRESSION.md`.
</meta-instruction>

## Required shape

```txt
1. Historical context
2. Hard regression bans
3. Conditional verification gates
4. Pre-flight checklist
```

## Rule

Each regression ban must be atomic:

```txt
REGRESSION BAN [ID]: DO NOT [exact bad behavior].
```

## Avoid

```txt
long narrative bans
multiple behaviors in one ban
positive advice in anti-regression files
untraceable vague incident IDs
```
