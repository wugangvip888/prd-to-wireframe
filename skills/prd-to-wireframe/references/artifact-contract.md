# Artifact Contract

## Inputs

```text
workspace/PRD/{prd_file}.md
workspace/figma_targets.md
```

`workspace/figma_targets.md` stores:

```text
Figma address
Figma internal layer name
```

## Outputs

```text
workspace/intents/{page_id}.md
workspace/priority_maps/{page_id}.md
workspace/layout_specs/{page_id}.md
workspace/records/run_xxx.md
```

Figma output is a set of frames in the target Figma file. The default mobile page frame size is `360 x 780` unless the PRD requires a different device or container.

## Run Record Required Fields

```text
run_id:
execution time:
PRD input:
page scope:
generation mode:
Figma address:
Figma internal layer name:
Intent output:
Priority Map output:
Layout Spec output:
Gate result:
Figma Frame ID:
Frame name:
wireframe post-change notes:
manual confirmation points:
```

## Resume Fields

```text
execution status: running / blocked / completed
last successful stage:
generated artifacts:
unfinished stages:
blocker:
resume entrypoint:
whether generated artifacts can be reused:
scope requiring rerun:
```

## Overwrite Rules

- Intent, Priority Map, and Layout Spec: overwrite same-name `{page_id}.md` as the latest artifact.
- Figma wireframe: replace target layer content by default.
- Run Record: always create a new `run_xxx.md`; never overwrite an old run record.
