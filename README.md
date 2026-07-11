# AI Agent Workspace Template

A [Copier](https://copier.readthedocs.io/) template for generic, AI-agent-ready Python and JavaScript workspaces.

## Usage

Install Copier and Git. Install mise, uv, and pnpm when selecting the related
optional steps.

```sh
# Create a repository from the published template.
# Copier prompts for the project name, slug, and description.
# Git initialization is enabled by default. Toolchain installation and lockfile
# generation are disabled by default; neither lockfile is stored in the template.
# --trust permits the template's explicitly declared tasks.
copier copy --trust https://github.com/japboy/agent-workspace-template.git /path/to/new-repository

# From the generated repository, after committing or otherwise resolving local
# changes, update from the template recorded in .copier-answers.yml.
copier update --trust
```

When both optional toolchain installation and lockfile generation are selected,
Copier runs lock generation through `mise exec`; otherwise it uses compatible
`uv` and `pnpm` already on `PATH`.

## Generated baseline

The generated repository includes agent instructions (`AGENTS.md`, with
`CLAUDE.md` linked to it), repository architecture, and shared uv/pnpm workspace
members in `.agents/skills`, `apps/*`, and `packages/*`. Public Python and npm
packages use anonymous Takumi Guard proxies, dependency resolution has a
three-day maturity window, and JavaScript dependency build scripts require
explicit approval.

No agent-memory database or configuration is included.

For Copier installation and advanced options, see the official [Copier documentation](https://copier.readthedocs.io/).
