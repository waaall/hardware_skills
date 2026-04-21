# Stop Rules

Use this file when deciding whether to continue, pause, or stop.

## Continue

Continue when:

- uncertainty is local
- the main chain remains interpretable
- the unresolved item does not change module role or signal ownership

## Pause and Ask the User

Pause when:

- a critical chain cannot be closed
- a conflict changes likely function or behavior
- module ownership of a signal is ambiguous
- architecture notes and screenshots disagree on a key boundary

Critical chains include:

- power rails
- reset paths
- clocks
- reference-voltage and reference-ground paths
- MCU main communication buses
- critical external interfaces

## Stop the Round

Stop the current round when:

- many critical chains are unresolved
- image quality prevents reliable interpretation
- the minimum input set is not present
- cross-module closure is too weak to support a system-level document

## Output Behavior on Stop

If you pause or stop:

- summarize what is already solid
- list blocked items clearly
- state exactly what extra evidence is needed
- do not continue writing system-level conclusions that depend on the missing evidence
