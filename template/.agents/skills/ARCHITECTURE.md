# Agent Skills and Plugin Architecture

`.agents/` is a self-contained Codex and Claude Code plugin directory.
`.agents/skills/` is its canonical source for repository-scoped Agent Skills
and bundled resources. `.claude/skills` is a relative symbolic link to this
directory for Claude Code development-time discovery.

Both manifests live under `.agents/` and package `./skills/` relative to that
plugin root. Parent marketplaces distribute this directory with a Git
subdirectory source, so installed plugins remain self-contained and do not
depend on a parent repository's submodules or any path outside the copied
plugin.

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
