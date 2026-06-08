# T999 Final Audit

## Decision

`partial_pass_with_operator_blockers`

## Matrix Result

| Row | Result | Evidence |
| --- | --- | --- |
| Safari normal field | Pass | `safari-retry-before-insert.json`, `safari-retry-after-insert.json`, `safari-retry-app-group-after-insert.json` |
| Safari secure field | Pass | `safari-secure-focused.json`, `safari-secure-app-group-after-focus.json`, `safari-secure-cleanup.json` |
| Notes sterile editor | Blocked | `notes/T003-notes.md` |
| Messages/iMessage sterile thread | Blocked | `notes/T004-messages-mail.md` |
| Mail sterile compose | Blocked | `notes/T004-messages-mail.md` |

## Strongest Realistic Failure Modes

1. The Safari normal row might look like it passed because Insert latest was
   tapped, while the target field did not change.
   - Evidence: the first failed receipts are preserved; the passing retry uses
     the corrected visible coordinate and `safari-retry-after-insert.json`
     proves the sterile text value count is exactly `1`.
2. The keyboard might insert once but leave a stale transcript available.
   - Evidence: `safari-retry-app-group-after-insert.json` proves App Group
     returned to `idle` with no transcript after insertion.
3. Secure fields might allow Foil custom-keyboard insertion.
   - Evidence: `safari-secure-focused.json` proves Foil Keyboard root and
     Insert latest are absent while the sterile password field is focused, and
     the secure length remains `0`.
4. The board might claim Apple host-app coverage while private rows remain
   untested.
   - Evidence: Notes, Messages, and Mail are explicitly blocked with operator
     setup requirements and no raw/private host-app source was inspected.

## Final Cleanup

`safari-secure-cleanup.json` proves App Group is idle with no transcript at the
end of the matrix slice.

## Next Action

Operator opens a fresh blank Notes editor, a sterile Messages self/test thread,
or a blank Mail compose field with the cursor focused. Then rerun the matching
row with WDA direct URL `http://192.168.1.40:8100`.
