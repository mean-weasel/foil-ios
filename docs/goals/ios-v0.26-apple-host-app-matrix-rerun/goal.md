# Foil iOS v0.26 Apple Host-App Matrix Rerun

## Original Request

Now that WDA works on the preview iPhone through the direct device URL, rerun
the Apple host-app keyboard insertion matrix.

## Outcome

Prove Foil Keyboard insertion and secure-field rejection on physical
`iPhone-preview` with sanitized receipts, while blocking rows that would expose
private host-app content.

## Oracle

This board is complete when each required row is either proven with sanitized
WDA/App Group receipts or blocked with a precise privacy/operator reason:

- Notes sterile editor
- Messages/iMessage sterile thread
- Mail sterile compose
- Safari normal text field
- Safari secure/password field rejection

## Non-Goals

- Do not inspect private Messages, Mail, Notes, Safari history, contacts,
  accounts, URLs, or raw host-app trees.
- Do not claim closed-beta readiness from app-side command-mailbox proof alone.
- Do not commit raw WDA source, screenshots, transcript bodies, provider keys,
  App Store Connect keys, JWTs, contacts, or private phone content.

## Starter Command

`/goal Follow docs/goals/ios-v0.26-apple-host-app-matrix-rerun/goal.md.`
