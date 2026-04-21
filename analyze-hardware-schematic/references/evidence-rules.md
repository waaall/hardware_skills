# Evidence Rules

Use this file when claims, labels, or sources disagree.

## Source Priority

### For topology and connection claims

1. screenshot-visible topology
2. user-provided auxiliary mapping files
3. full schematic PDF point checks, only if allowed

### For part identity and parameters

1. BOM
2. screenshot-visible designator and text
3. auxiliary notes

## Conflict Handling

### Screenshot vs BOM

- Treat the screenshot as authoritative for visible connectivity.
- Treat the BOM as authoritative for part identity only after the `RefDes` mapping is trusted.
- If the same `RefDes` appears to disagree on model or function, record a conflict and avoid a hard conclusion.

### Screenshot vs Architecture Notes

- Use the screenshot for actual visible connectivity.
- Record the architecture note as design intent when relevant.
- If the intent and visible evidence diverge, do not silently merge them.

### Auxiliary Sources vs Primary Evidence

- Auxiliary maps can help close ownership and naming.
- They cannot replace missing topology evidence.

## Confidence Labels

Use exactly these labels:

- `已确认`
  Visible and sufficiently closed by evidence.
- `推断`
  Strongly suggested by evidence, but not fully closed.
- `待确认`
  Mentioned or partially visible, but insufficient to trust.
- `冲突`
  Sources disagree in a way that affects interpretation.

## Writing Rules

- Say what is visible before saying what is inferred.
- Do not present inference in the same tone as confirmation.
- If a claim matters to power flow, reference flow, reset, clocking, or MCU resource ownership, be more conservative.
