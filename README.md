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
│   ├── agents/
│   └── references/
└── plans/
```

- `analyze-hardware-schematic/`: the main directory for the current hardware skill
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

## Expansion Convention

When adding more skills in the future, a similar structure is recommended:

- `SKILL.md`: defines the skill's purpose, inputs, workflow, and expected outputs
- `references/`: stores templates, rules, and review checklists
- `agents/`: stores agent configuration for the skill
- `plans/`: records design notes and iteration plans

The repository is still small, but it will continue to grow around the theme of hardware analysis and documentation automation.
