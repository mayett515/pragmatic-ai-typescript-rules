# Global Architectural Regression Bans

<meta-instruction>
These are hard bans against patterns that repeatedly caused drift during schema stress tests.
</meta-instruction>

<absolute-constraints>
- REGRESSION BAN: DO NOT turn pure decisions into framework exception throwers.
- REGRESSION BAN: DO NOT move external API calls into domain helpers.
- REGRESSION BAN: DO NOT replace explicit decision unions with magic booleans/strings.
- REGRESSION BAN: DO NOT create service classes that own no capability.
- REGRESSION BAN: DO NOT split tiny coherent features into multi-file architecture.
- REGRESSION BAN: DO NOT hand-edit generated code.
- REGRESSION BAN: DO NOT let raw `unknown`/`any` cross into persistence code.
- REGRESSION BAN: DO NOT silently swallow parser/schema/migration failures.
- REGRESSION BAN: DO NOT use comments to justify unclear code instead of naming the concept.
</absolute-constraints>

<conditional-logic>
IF you are changing a parser boundary:
THEN verify malformed input is handled explicitly.

IF you are changing a workflow with side effects:
THEN verify irreversible effects happen after validation and policy decisions.

IF you are changing a class boundary:
THEN verify the class still owns a real capability/resource/lifecycle.
</conditional-logic>

<pre-flight-checklist>
1. [ ] Did I avoid every regression ban?
2. [ ] Did any conditional gate apply?
3. [ ] Did I preserve established boundaries?
</pre-flight-checklist>
