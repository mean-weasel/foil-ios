# T001 Messages Fake Recipient Row

## Result

`passed_fake_recipient_draft`

## Evidence

- WDA opened Messages through `sms:5555555555`, landing in a New Message
  compose view with a fake recipient and body field.
- One keyboard switch exposed Foil Keyboard.
- `messages-fake-stage-transcript.json` staged a sterile transcript and records
  only hashes and length.
- `messages-fake-before-insert.json` proves Foil Keyboard and enabled Insert
  latest before insertion.
- `messages-fake-after-insert.json` proves the transcript appeared exactly once
  in the message body field and the fake recipient was still present.
- `messages-fake-draft-cleanup.json` proves the unsent draft body no longer
  contained the transcript after cleanup.
- `messages-fake-app-group-cleanup.json` proves App Group state returned to
  idle/no transcript.

## Privacy Boundary

No message was sent. No raw WDA source, screenshots, private message text,
contacts, real phone numbers, or thread-list content were committed.

## Limitation

This proves Messages draft insertion through a fake-recipient compose surface.
It does not prove successful delivery, real-recipient behavior, or insertion
into an existing private conversation.
