# Input Requirements

Use this file during intake.

## Required Inputs

### 1. Overall Architecture Description

The user should provide a document that states:

- board or system purpose
- major modules
- how modules connect to MCU, external interfaces, and each other
- important signal names, rail names, or pin names when known

### 2. Per-Module Screenshot Folders

Expected characteristics:

- one folder per module
- ordered screenshot filenames
- filenames describe function or flow direction

Recommended filename pattern:

- `01_acdc-to-24v.png`
- `02_24v-to-5v.png`
- `03_5v-to-3v3.png`

### 3. BOM Document

Preferred filename:

- `bom.md`

Legacy compatibility:

- `boom.md`

Minimum BOM table fields:

- `位号 / RefDes`
- `器件型号`
- `参数`
- `功能/器件类别名`
- `所属模块`

Optional but useful fields:

- `原理图编号 / Sheet ID`
- `Comment`
- `替代料`

The BOM should also include a section after the table for key-part notes such as electrical limits, variants, or original schematic comments.

## Recommended Inputs

These are recommended, not required:

- `module-index.md`
- `mcu-pin-map.md`
- `interface-map.md`
- `schematic-page-map.md`
- screenshot sidecar notes
- full schematic PDF export for point checks

## Intake Checklist

Before analysis, check:

- required files exist
- module folders are named clearly
- screenshot order is meaningful
- BOM `RefDes` values appear in screenshots
- architecture description and module folders roughly agree

If these checks fail, report the issue list before doing formal analysis.

## Image Quality Rules

Do not proceed with conclusions when:

- net labels are unreadable
- pin names are unreadable
- critical designators are unreadable
- key links are cropped
- multiple unrelated chains are mixed into one ambiguous screenshot

If quality is poor, ask for better screenshots or a point-check source before continuing.
