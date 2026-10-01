---
name: usim-scenario-authoring
description: Create or revise fictional u-sim Suite scenarios from a teaching brief or supplied case, using the bundled schema and behavior reference. Use for .usim scenario content and authoring; not application code changes or autonomous patient care.
---

# u-sim scenario authoring

Produce a Suite scenario object that preserves the user's teaching intent and existing authored behavior. Use fictional, non-identifying patient content.

## Choose the contract

Read [the profile manifest](references/profile.json) and [validation guidance](references/validation.md). The bundle targets the Suite implementation profile. The portable `usim-scenario` 2.0 format is a different contract; do not mix its arrays, fields, or extensions into Suite JSON. If the user requests portable content, consult the portable specification on their u-sim docs site and label execution support separately.

Use [the schema](references/profile-schema.json) for exact keys, required fields, bounds, and enums. Start a new case from [the fictional example](references/scenario-example.json), replacing its clinical content and decisions with the requested case. Do not copy the example's diagnosis or treatment as a default. Read [the field inventory](references/authoring-fields.json) when looking up a field and [Suite behavior](references/suite-behavior.md) when authoring events, resources, timing, or assessment. These files are a snapshot of the profile in the manifest; do not silently mix them with another release.

## Author the case

- Establish the audience, observable objectives, starting presentation, key decisions, and intended conclusions. Resolve routine detail from the supplied brief; ask when a missing clinical or educational decision materially changes the case.
- Connect stable state and action IDs. Preserve existing IDs and unrelated content when editing. Define learner decisions separately from scheduled transitions and delayed resource results.
- Baseline is starting conditions only. New milestones advance to a distinct non-baseline phase, even if vitals are unchanged; do not create baseline self-loops or returns (including resource destinations). Routine resource requests need no extra action or state. Preserve explicit source/legacy flows during unrelated edits.
- When adding a recognition phase, retain the original deterioration source and deadline. Recognition does not cancel or restart deterioration; include effective treatment actions from all relevant branches in cancellation references, and preserve assessment references.
- Use the actual resource types and diagnostic categories from the schema. Availability, disclosure, and physiological effects are separate authored choices. Do not infer a patient response solely from a medication name or dose.
- Keep optional values unspecified unless the brief or an explicit authoring choice supports them. Preserve zero and false. Do not invent assets, attachment bytes, provenance, review credentials, or source verification.
- Write assessment against observable authored actions. Check objective/action references and scoring; an unassessed objective is not a failed objective. Separate facilitator/debrief information from learner-facing cues to avoid disclosing the teaching answer.
- Ground clinical details in supplied sources or verified references when needed. Identify material assumptions and items requiring educator review; a schema pass does not certify clinical correctness.

## Verify and deliver

Follow [validation guidance](references/validation.md). Check both structural validity and the meaning of graph references, timing, results, and conclusions. If execution is available and within scope, exercise the intended path and a meaningful alternative; report what actually ran.

Deliver the scenario JSON, a concise change summary, and checks performed or still needed. Raw scenario JSON is not an importable published Suite package. Use the application's supported publication/export workflow when an importable package is requested; do not fabricate revision metadata or digests. Creating content does not itself authorize publishing it or changing a live run.
