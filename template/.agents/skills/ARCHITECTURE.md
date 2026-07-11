# Agent Skills Architecture

`.agents/skills/` contains repository-scoped Agent Skills and their bundled
resources.

## Invariants

- Each direct child skill directory that is meant to be discoverable by Codex
  must contain `SKILL.md`.
- Skill-specific deterministic helpers belong in the owning skill's `scripts/`
  directory.
- Long reusable guidance belongs in the owning skill's `references/` directory.
- Output templates or reusable artifacts belong in the owning skill's `assets/`
  directory when needed.
- This directory is a shared uv and pnpm workspace member. Python helper
  dependencies belong in `pyproject.toml`; JavaScript helper dependencies
  belong in `package.json`.

## Adding a skill

Create one directory per skill directly under `.agents/skills/`. Keep the
workflow in `SKILL.md`, and place supporting resources in the directories
described above. This keeps each skill self-describing and its dependencies
local to the workflow that uses them.
