# T003 Messages Fake-Recipient Draft

## Decision

`privacy_blocked_before_draft`

## What Happened

Messages was launched twice with redacted fake-recipient payloads:

- URL form 1 hash:
  `75c19565b84e1501b51f352ecba2d4a19e45949b1e377e555b5f2bd3971e291d`
- URL form 2 hash:
  `e7777cdaeb2878d6c865e400f10b6bc9001598e21c729fe7016954b50c62254a`

Both launches landed on the Messages thread-list surface instead of a New
Message compose view. The structural WDA summary showed:

- `New Message`: absent
- fake recipient: absent
- body text field/text view: absent
- send button: absent
- visible collection/list cells: `12`

Because the only available surface was the private/existing thread list, the row
stopped before staging a transcript, tapping compose, selecting a thread,
typing, inserting, or sending.

## Privacy Boundary

No raw Messages WDA source, screenshots, thread titles, contact names, phone
numbers, message bodies, or transcript text were committed. Raw WDA source files
remained in `/tmp` only.

## Exact Next Action

To rerun this row safely, provide one of:

- a reliable direct fake-recipient compose URL/path for iOS 26.5 Messages, or
- an operator-opened sterile New Message compose surface with the body field
  focused and no private thread list visible.

This row remains draft-only. It must not claim delivery or existing private
thread behavior.
