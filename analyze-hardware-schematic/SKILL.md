---
name: analyze-hardware-schematic
description: Analyze modular hardware schematic materials to create or revise hardware design documentation. Use when the user provides an overall architecture description, per-module schematic screenshots, and a BOM document such as bom.md, and the task is to understand module internals, confirm inter-module links, identify unresolved connections, and produce module-level documents plus an overall module-link document without guessing unclear relationships.
---

# Analyze Hardware Schematic

Use this skill when a hardware schematic is too large to analyze as one file and the user wants a modular, evidence-driven understanding based on screenshot groups, BOM data, and architecture notes.

## When to Use

Use this skill when:

- The user has split a hardware design into modules and screenshot sets.
- The task is to create or revise hardware design documents.
- The work must be based on visible evidence, not freeform guessing.
- The result should include both module-level analysis and an inter-module relationship document.

Do not use this skill as the default approach for:

- PCB layout review.
- SI/PI simulation work.
- Reading the full schematic project directly when the user has explicitly limited the evidence source.

## Required Inputs

The minimum working input set is:

1. An overall architecture description.
   It should describe board purpose, major modules, and key links to MCU or external I/O.
2. Per-module screenshot folders.
   Screenshots should be ordered and named to reflect function and signal/power flow.
3. A BOM document.
   Standard name is `bom.md`; legacy alias `boom.md` is acceptable.
4. Optional existing documents.
   If present, use revision mode. If absent, use fresh-document mode.

If required inputs are missing, do not proceed into formal analysis. Perform intake and report the gap first.

## Recommended Inputs

These inputs are not mandatory, but they materially improve closure:

- `module-index.md`
- `mcu-pin-map.md`
- `interface-map.md`
- `schematic-page-map.md`
- short sidecar notes for screenshots
- full schematic PDF export, only as auxiliary point-check evidence

If these are missing, continue only when the main chain can still be closed from the required inputs.

## Input Validation

Before analysis, perform an intake pass:

- Verify that all required inputs exist.
- Verify that screenshot naming is ordered and meaningful.
- Verify that BOM `RefDes` entries can be mapped to screenshot-visible designators.
- Verify that module boundaries in the architecture description roughly match the screenshot folders.
- Verify that critical text in screenshots is readable.

Flag image-quality issues early. At minimum, net labels, pin names, and component designators must be readable. If key links are cropped or blurred, output an input-quality issue list instead of writing conclusions.

## Evidence Rules

Follow these rules strictly:

- Screenshot-visible topology is the primary evidence for link and circuit-structure claims.
- BOM is the primary evidence for part identity, part parameters, and part category.
- Screenshot designators are the bridge between topology and BOM identity.
- Architecture notes and recommended-input files are auxiliary evidence, not replacements for visible topology.
- A full schematic PDF may be used only for point checks and only when the user allows it.
- Never use BOM part names to invent a connection that is not visible or otherwise evidenced.
- Never smooth over uncertainty just to make the document feel complete.

Classify important claims with one of these confidence labels:

- `已确认`
- `推断`
- `待确认`
- `冲突`

## Workflow

Follow this order:

1. Intake check.
   Validate inputs, readability, and cross-file consistency before analysis.
2. Build the module map.
   Read the overall description first. If `module-index.md` exists, use it to seed the map.
3. Identify priority chains.
   Prioritize power, reset, clock, reference, MCU main buses, and critical external interfaces.
4. Analyze each module folder in screenshot order.
   Use visible net names, designators, page connectors, and signal direction hints.
5. Reconcile key parts with BOM.
   Pull in model, parameters, and module ownership only after topology is understood.
6. Produce module documents.
   Each submodule starts with key parts, then relation analysis, then evidence-backed conclusions.
7. Produce the inter-module relationship document.
   Only summarize relationships already supported by module analysis.
8. Produce a project-level open issues list.
   Collect unresolved cross-module links, conflicts, missing evidence, and user action items.

## Revision Mode vs Fresh-Document Mode

In revision mode:

- Check each existing conclusion against screenshot and BOM evidence.
- Preserve correct structure when possible.
- Replace unsupported claims with evidence-backed wording or unresolved items.

In fresh-document mode:

- Generate documents directly from the standard templates.
- Do not invent history or prior assumptions.

## Stop Conditions

Pause and ask for user confirmation when:

- A critical link is unclear and affects the main chain.
- Screenshot evidence conflicts with BOM in a way that changes behavior or interpretation.
- Architecture notes and visible topology disagree on module boundaries or signal ownership.

Stop the current round when:

- Too many critical links are unresolved to trust the main analysis.
- Cross-module relationships cannot be closed reliably.
- Input quality is too poor for safe interpretation.

Continue only when uncertainty is local and does not distort the module's main chain.

## Output Requirements

Produce up to three outputs:

1. Module-level documents.
   One document per module, organized by submodule.
2. An inter-module relationship document.
   Power, references, control paths, data paths, and unresolved cross-module links.
3. A project-level open issues list.
   Conflicts, missing evidence, unresolved links, and required user confirmations.

Each important relationship should retain evidence references:

- screenshot filename
- key `RefDes`
- key net names
- closed/not-closed status
- cross-module or not
- confidence label

## Reference Files to Read

Read these files only when needed:

- [references/input-requirements.md](references/input-requirements.md)
  Use for intake rules, naming, and quality expectations.
- [references/module-doc-template.md](references/module-doc-template.md)
  Use when generating or normalizing module-level documents.
- [references/inter-module-links-template.md](references/inter-module-links-template.md)
  Use for the system-level relationship summary.
- [references/project-open-issues-template.md](references/project-open-issues-template.md)
  Use for unresolved-item and conflict tracking.
- [references/evidence-rules.md](references/evidence-rules.md)
  Use when evidence is ambiguous or conflicting.
- [references/stop-rules.md](references/stop-rules.md)
  Use when deciding whether to continue, pause, or stop.
- [references/review-checklist.md](references/review-checklist.md)
  Use before finalizing output.
