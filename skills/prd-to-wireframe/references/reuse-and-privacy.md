# Reuse and Privacy

Before committing or sharing this workflow:

- Do not commit real PRDs.
- Do not commit real Figma URLs, file keys, node IDs, or target layer names from private projects.
- Do not commit generated artifacts derived from confidential PRDs unless they are explicitly approved for sharing.
- Keep local project data under `workspace/` ignored by Git.
- Use small, fictional fixture data when examples are needed.

Recommended ignored paths:

```gitignore
workspace/PRD/*
workspace/figma_targets.md
workspace/intents/*
workspace/layout_specs/*
workspace/priority_maps/*
workspace/records/run_*.md
```

Keep `.gitkeep` files and `workspace/README.md` so teammates get the expected directory structure.
