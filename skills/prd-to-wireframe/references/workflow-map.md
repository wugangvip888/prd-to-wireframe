# Workflow Map

This skill wraps the repository's existing workflow documents instead of duplicating them.

## Stage Entrypoints

```text
Full pipeline: prompts/00_run_full_pipeline.md
PRD to Intent: prompts/01_prd_to_intent.md
Intent to Priority Map: prompts/02_intent_to_priority_map.md
Priority Map to Layout Spec: prompts/03_priority_map_to_layout_spec.md
Layout Spec to Wireframe: prompts/04_layout_spec_to_wireframe.md
```

Execution details live in:

```text
execution/00_run_full_pipeline.md
execution/01_prd_to_intent.md
execution/02_intent_to_priority_map.md
execution/03_priority_map_to_layout_spec.md
execution/04_layout_spec_to_wireframe.md
execution/wireframe_construction_method.md
```

## Rule Files

```text
rules/intent_rules.md
rules/priority_rules.md
rules/layout_spec_rules.md
rules/wireframe_rules.md
rules/structure_preparation_rules.md
rules/harness_rules.md
```

## Standard Flow

```text
workspace/PRD/{prd_file}.md
-> workspace/intents/{page_id}.md
-> Intent Harness Check
-> workspace/priority_maps/{page_id}.md
-> Priority Harness Check
-> workspace/layout_specs/{page_id}.md
-> Layout Harness Check
-> Wireframe Preflight Check
-> Figma Wireframe
-> workspace/records/run_xxx.md
```

Default to full pipeline execution unless the user asks for staged review.

## Page Scope

If the user does not specify a page range, identify all pages/states from the PRD and process all of them. If the user specifies pages, keep all generated files limited to that scope and record the scope in the run record.
