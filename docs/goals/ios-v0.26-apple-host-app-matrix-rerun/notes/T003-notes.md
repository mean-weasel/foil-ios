# T003 Notes Row

## Result

`blocked_operator_sterile_editor_needed`

## Reason

The Notes row requires a fresh sterile editor. Launching Notes from automation
may expose a notes list or an existing private note before a blank editor is
focused. This board did not inspect Notes source or screenshots.

## Exact Unblock

On `iPhone-preview`, open Notes to a fresh blank note, focus the note body, and
switch to Foil Keyboard. Then rerun the Notes row using WDA direct URL
`http://192.168.1.40:8100`.
