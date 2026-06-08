# T002 Safari Rows

## Result

`pass`

## Normal Field

The first two taps exposed a coordinate-origin issue in WDA keyboard-extension
source: keyboard element coordinates are local to the extension, not full-screen
coordinates. The visible screenshot showed the actual Insert latest button
around logical `y=615`.

The corrected retry passed:

- `safari-retry-stage-transcript.json` staged a sterile complete transcript.
- `safari-retry-before-insert.json` proved Foil Keyboard root and Insert latest
  enabled before insertion.
- WDA tap at `{x: 207, y: 615}` hit the visible Insert latest button.
- `safari-retry-after-insert.json` proved the sterile value appeared exactly
  once and Insert latest became disabled.
- `safari-retry-app-group-after-insert.json` proved App Group returned to
  `idle` with no transcript.

## Secure Field

The secure-field row passed:

- `safari-secure-stage-transcript.json` staged a sterile transcript.
- Focusing the sterile password field succeeded.
- `safari-secure-focused.json` proved Foil Keyboard root and Insert latest were
  absent while the secure field was focused, and the secure field length stayed
  `0`.
- `safari-secure-app-group-after-focus.json` proved the transcript remained
  staged rather than being inserted.
- `safari-secure-cleanup.json` returned App Group to `idle` with no transcript.

## Privacy Boundary

Raw Safari WDA source and screenshots stayed in `/tmp`. Committed receipts use
hashes, identifier checks, text counts, and App Group summaries only.
