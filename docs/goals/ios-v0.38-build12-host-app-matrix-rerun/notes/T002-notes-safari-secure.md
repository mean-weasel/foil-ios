# T002 Notes, Safari Normal, Safari Secure

## Decision

`safari_pass_notes_privacy_blocked`

## Safari Normal Field

Result: `passed`

Build 12 Safari normal-field proof used the sterile local fixture at
`http://192.168.1.34:8945/`.

Evidence:

- `build12-safari-normal-stage-transcript.json` staged a unique sterile
  transcript in App Group.
- `build12-safari-normal-before.json` proved Foil Keyboard root was present,
  Insert latest was enabled, and the Safari field contained zero copies of the
  sterile phrase before insertion.
- WDA clicked `foil-keyboard-insert-latest`.
- `build12-safari-normal-after.json` proved the Safari field contained exactly
  one copy of the sterile phrase and Insert latest became disabled.
- `build12-safari-normal-app-group-after.json` proved App Group returned to
  `idle` with `hasTranscript=false`.

## Safari Secure Field

Result: `passed_expected_rejection`

Evidence:

- `build12-safari-secure-stage-transcript.json` staged a unique sterile
  transcript in App Group.
- WDA focused the local fixture password field.
- `build12-safari-secure-focused.json` proved Foil Keyboard root and Insert
  latest were absent, secure length stayed `0`, and the sterile phrase appeared
  zero times in value attributes.
- `build12-safari-secure-app-group-after-focus.json` proved the transcript
  remained staged after secure-field focus.
- `build12-safari-secure-cleanup.json` reset App Group to `idle` with
  `hasTranscript=false`.

## Notes

Result: `privacy_blocked`

Notes opened directly to an editor, not a list, but the editor had an existing
unknown value of length `21`. The `mobilenotes://new` payload did not change the
screen or create a blank editor. Because the existing note was not known to be
sterile, this row stopped before staging a transcript, clearing content, or
inserting text.

Evidence:

- WDA source stayed in `/tmp` only.
- Structural precheck showed one visible Notes text view and zero list cells.
- The value was not one of the known sterile phrases.
- `build12-notes-blocker-app-group.json` proved App Group remained idle/no
  transcript after the blocker decision.

## Privacy Boundary

No raw WDA sources, screenshots, note contents, transcript bodies, or private
host-app content were committed.
