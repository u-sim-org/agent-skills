# Validation and delivery

The archive contains a release-matched snapshot generated from the Suite contract and docs. `profile.json` identifies the schema and Suite version. For a different deployment, obtain its matching schema and references from `/docs/downloads/`; do not assume the newest profile matches an older scenario.

## Structural checks

Validate raw scenario content against `profile-schema.json` with a JSON Schema draft-07 validator. Disable coercion, default insertion, and removal of additional properties. The schema does not validate all reference relationships, graph behavior, image content, attachment limits, or package metadata. Report the actual validator and result; visual inspection alone is not a schema validation pass.

## Full Suite checks

When working inside the u-sim Suite repository, use the existing `assertScenario` export from `lib/workspace-store.ts` for shape and content checks, followed by `validateScenario` from `lib/workspace-types.ts` for semantic errors. Call semantic validation only after the shape check succeeds. Do not reimplement a weaker validator and label it equivalent. Repository dependencies must be available; these source modules are not bundled in the skill.

Outside the repository, use the target application's supported Builder validation workflow when available. If it is unavailable, report schema validation and manual reference review separately and leave Suite semantic/runtime validation unverified. These skills do not install a validator or supply an MCP server. Never invent a `validate_scenario` tool or public validation endpoint.

For runtime verification, use a disposable preview or test run within the user's scope. Exercise relevant choices and delays, and save/reload if persistence behavior matters. Record the profile/revision tested. A simulated trace or deterministic test fixture is not evidence of a live AI interaction.

## Baseline authoring checks

For newly authored flows, baseline is starting conditions only. No action or resource destination returns to baseline, including self-loops. A meaningful milestone advances to a distinct non-baseline phase even with unchanged physiology; routine resource requests need no new state. Check that splitting a phase preserves original deterioration deadlines and that cancellation covers effective treatment on every relevant branch, not recognition alone. Keep assessment references intact. These are authoring checks beyond schema validity: preserve explicit legacy/imported behavior on unrelated edits and report baseline loops for review rather than automatically migrating them.

## Packaging

`scenario-example.json` is inner scenario content. A published Suite export uses `format: "usim-suite-scenario"`, `formatVersion: 1`, and a revision envelope with a content digest. A portable document uses `format: "usim-scenario"` and a different contract. Renaming raw JSON to `.usim` does not make a published import package.

Use the application's supported export path for an authorized published revision. If only content authoring is requested or publication is unavailable, deliver raw JSON clearly labeled as scenario content and explain the remaining publication/export step. Do not invent a revision, verified digest, clinical approval, or successful import.
