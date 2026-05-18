---
name: prd-to-wireframe
description: Use this skill when converting a product requirements document (PRD) into structured wireframe artifacts and Figma wireframes. Trigger for requests to run or reuse the PRD -> Intent -> Priority Map -> Layout Spec -> Figma Wireframe workflow, validate generated artifacts with gates, resume interrupted runs, or package this repository's wireframe workflow for a teammate.
---

# PRD to Wireframe

Use this skill to run the repository workflow that converts a PRD into page-level planning artifacts and Figma wireframes.

## Required Inputs

Check these before generating anything:

```text
workspace/PRD/{prd_file}.md
workspace/figma_targets.md
page scope: all pages or named pages
generation mode: typical_state or full_state
```

`workspace/figma_targets.md` must contain a Figma file URL and target layer name. If either is missing, stop and ask for the missing input.

## Core Workflow

1. Read `docs/workflow.md` and `execution/00_run_full_pipeline.md`.
2. Read the rules needed for the requested stage:
   - Intent: `rules/intent_rules.md`
   - Priority Map: `rules/priority_rules.md`
   - Layout Spec: `rules/layout_spec_rules.md`
   - Harness gates: `rules/harness_rules.md`
   - Wireframe: `rules/wireframe_rules.md` and `rules/structure_preparation_rules.md`
3. Generate artifacts in this order:
   - `workspace/intents/{page_id}.md`
   - `workspace/priority_maps/{page_id}.md`
   - `workspace/layout_specs/{page_id}.md`
   - Figma wireframe frames
   - `workspace/records/run_xxx.md`
4. Run the matching gate after each artifact. Do not continue a page when its gate fails.
5. Before writing to Figma, run Wireframe Preflight against PRD, Intent, Priority Map, and Layout Spec.
6. After Figma changes, add a new run record. Never overwrite prior `run_xxx.md` records.

## Priority Order

Use this source-of-truth order when resolving conflicts:

```text
PRD > rules > Intent > Priority Map > Layout Spec > Wireframe
```

Rules constrain how to generate artifacts; they do not change PRD business requirements.

## Figma Work

When the task requires writing frames to Figma:

- Use the Figma skill/tooling available in the current environment.
- Default to replacing the target layer content named in `workspace/figma_targets.md`.
- Create copies or extra versions only when the user explicitly asks to preserve old wireframes.
- Follow `execution/wireframe_construction_method.md` for frame construction.

## Resuming Runs

For interrupted or rerun work:

1. Read the latest related `workspace/records/run_xxx.md`.
2. Inspect existing files under `workspace/intents/`, `workspace/priority_maps/`, and `workspace/layout_specs/`.
3. Reuse artifacts only if their upstream inputs have not changed and their gates already passed.
4. Re-run Wireframe Preflight before any Figma update.

## Stop Conditions

Stop and report the blocker when:

- PRD file is missing.
- Figma URL or target layer name is missing.
- PRD conflicts with downstream artifacts.
- A required page, state, or PRD hard constraint is missing.
- A downstream artifact adds core business capability not present in the PRD.
- Layout Spec is not sufficient to produce one page state per Figma frame.

## References

- Read `references/workflow-map.md` for the complete file map and stage commands.
- Read `references/artifact-contract.md` when creating or validating output files.
- Read `references/reuse-and-privacy.md` before committing workflow changes or sharing the skill.
