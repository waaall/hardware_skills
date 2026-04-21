# Using `analyze-hardware-schematic`

This document shows how to use `analyze-hardware-schematic` in practice.

It is written as a workflow example, not just a spec summary.

## What This Skill Is For

Use this skill when:

- the schematic is too large to review as one file
- the project has been split into module-level screenshot groups
- you want evidence-based hardware documentation instead of freeform interpretation

Typical goals:

- generate module-level design documents
- trace inter-module links
- identify unresolved or conflicting connections
- revise existing hardware documents against visible schematic evidence

## Minimum Inputs

Prepare these inputs before invoking the skill:

- an overall architecture description
- per-module schematic screenshot folders
- a BOM document, usually `bom.md`
- optional existing documents if you want revision mode

If the required inputs are incomplete or low quality, the skill should stop at intake and report the gaps first.

## Recommended Input Layout

One practical way to organize the project is:

```text
project-materials/
├── overview.md
├── bom.md
├── module-index.md
├── mcu-pin-map.md
├── interface-map.md
├── power/
│   ├── 01_acdc-input.png
│   ├── 02_24v-protection.png
│   └── 03_24v-to-5v.png
├── analog-input/
│   ├── 01_sensor-input.png
│   └── 02_signal-conditioning.png
├── mcu/
│   ├── 01_mcu-power-reset.png
│   └── 02_mcu-interfaces.png
└── existing-docs/
    ├── power.md
    └── inter-module-links.md
```

## Input Preparation Rules

Keep these points in mind:

- Screenshot filenames should be ordered and meaningful.
- Net labels, pin names, and designators must be readable.
- BOM `RefDes` values must be mappable to screenshot-visible designators.
- The architecture description should explain board purpose, major modules, and key module-to-module links.

Good screenshot names:

- `01_power-input.png`
- `02_24v-to-5v.png`
- `03_mcu-i2c-links.png`

Poor screenshot names:

- `image1.png`
- `test.png`
- `final-final.png`

## Example Prompt

Use a prompt that tells Codex exactly where the inputs are and what outputs you want.

Example:

```text
Use $analyze-hardware-schematic to analyze the materials under ./project-materials.

Read overview.md first, then inspect each module folder in filename order, and use bom.md as the source of part identity and parameters.

Work in fresh-document mode. Produce:
1. one module document per module
2. one inter-module relationship document
3. one project-level open issues document

Do not guess unclear links. If critical links are missing or unreadable, stop after the intake check and list the gaps.
```

## Revision Mode Example

If documents already exist, make that explicit:

```text
Use $analyze-hardware-schematic to revise the hardware design documents in ./project-materials/existing-docs based on the schematic screenshots and bom.md.

Preserve supported conclusions, replace unsupported statements with evidence-backed wording, and collect unresolved items separately.
```

## Expected Outputs

In a normal run, the skill should produce up to three output groups:

- module-level documents
- an inter-module relationship document
- a project-level open issues list

Each important conclusion should stay tied to evidence such as:

- screenshot filename
- key `RefDes`
- key net names
- confidence label

## When Not To Use It

Do not use this skill as the default approach for:

- PCB layout review
- SI/PI simulation tasks

## Practical Advice

- Start with one board and a small number of well-grouped modules.
- Keep module boundaries stable between the overview document and screenshot folders.
- Ask the skill to perform intake first if the materials were collected by someone else.
- If a cross-module link matters, make sure the relevant screenshots expose both the local chain and the cross-page or cross-module labels.
