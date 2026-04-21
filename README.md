# hardware_skills

This repository is used to build and refine Codex skills for hardware-related workflows.

The goal is not to collect generic prompts, but to turn real hardware work such as schematic analysis, design understanding, and documentation into reusable, extensible skills with clear evidence boundaries.

## Current Status

At the moment, the repository contains one skill:

- `analyze-hardware-schematic`
  Used to perform conservative, evidence-driven hardware design analysis based on modular schematic screenshots, a BOM, and an overall architecture description. It produces module-level documents, an inter-module relationship document, and a list of open issues or conflicts.

## Repository Structure

```text
.
├── analyze-hardware-schematic/
│   ├── SKILL.md
│   ├── USAGE.md
│   ├── agents/
│   └── references/
└── plans/
```

- `analyze-hardware-schematic/`: the main directory for the current hardware skill
- `USAGE.md`: a practical tutorial showing how to use the skill with a real input layout
- `agents/`: agent configuration files associated with the skill
- `references/`: templates, evidence rules, stop conditions, and review checklists
- `plans/`: planning and design notes for skill development

## Direction

The intention is to gradually build a set of skills that support real hardware development workflows, for example:

- modular schematic analysis and document generation
- inter-module connection tracing
- BOM-to-schematic consistency checks
- pin and interface mapping
- design review assistance

## Design Principles

- Focus on real hardware workflows instead of generic chat-style prompting
- Prefer evidence-backed conclusions and avoid filling gaps by guessing
- Support both generating documentation from scratch and revising existing documents
- Keep each skill in its own directory so it can evolve independently

## How To Use

At the repository level, each skill should ideally provide two layers of documentation:

- a short summary in the root `README.md`
- a practical usage tutorial inside the skill directory

For the current skill, see [analyze-hardware-schematic/USAGE.md](analyze-hardware-schematic/USAGE.md).

## Installation

This repository is currently organized in a Codex-first skill format.

### Install In Codex

For local development, the most direct approach is to copy or symlink a skill folder into `~/.codex/skills/`.

Example:

```bash
mkdir -p ~/.codex/skills
ln -s /path/to/hardware_skills/analyze-hardware-schematic ~/.codex/skills/analyze-hardware-schematic
```

Then restart Codex so it can pick up the new skill.

If this repository is published on GitHub, you can also install a skill from inside Codex with the built-in skill installer. Official references:

- [Using skills in Codex](https://developers.openai.com/codex/skills)
- [Create custom skills in Codex](https://developers.openai.com/codex/skills/create-skill)

### Use With Claude Code

Claude Code should be documented a bit more carefully.

This repository's current structure is a direct fit for Codex. For Claude Code, the safest wording is to treat it as a compatibility path rather than claiming identical native installation behavior.

Recommended wording:

- if your Claude setup supports Agent Skills-style folders, place the skill under `~/.claude/skills/<skill-name>` or `<project>/.claude/skills/<skill-name>`
- if not, adapt the workflow into a project command or subagent under `.claude/commands/` or `.claude/agents/`

Official Claude Code references:

- [Set up Claude Code](https://docs.anthropic.com/en/docs/claude-code/getting-started)
- [Claude Code settings](https://docs.anthropic.com/en/docs/claude-code/settings)

## Expansion Convention

When adding more skills in the future, a similar structure is recommended:

- `SKILL.md`: defines the skill's purpose, inputs, workflow, and expected outputs
- `USAGE.md`: shows how to prepare inputs and invoke the skill in practice
- `references/`: stores templates, rules, and review checklists
- `agents/`: stores agent configuration for the skill
- `plans/`: records design notes and iteration plans

The repository is still small, but it will continue to grow around the theme of hardware analysis and documentation automation.
