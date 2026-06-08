# Foil iOS v0.29 Messages Fake Recipient Row

## Original Request

Try a fake-recipient Messages compose path instead of requiring a prior sterile
self thread.

## Outcome

Prove whether Messages can be opened directly into a sterile compose draft with
a fake recipient, then use Foil Keyboard to insert a staged transcript exactly
once without sending.

## Oracle

This board is complete when sanitized receipts prove:

- Messages opened to a new fake-recipient compose draft.
- Foil Keyboard inserted the staged transcript exactly once into the body.
- No send action occurred.
- The draft body and App Group state were cleaned up afterward.

## Non-Goals

- Do not send a message.
- Do not inspect private Messages threads, contacts, phone numbers, or thread
  lists.
- Do not commit screenshots, raw WDA source, or private Messages content.
- Do not claim delivery or real-recipient behavior.

## Starter Command

`/goal Follow docs/goals/ios-v0.29-messages-fake-recipient/goal.md.`
