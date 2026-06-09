# T001 Matrix Preflight

## Decision

`ready_for_build12_matrix_rerun`

## Rows To Rerun

Build 12 has passed TestFlight upload and physical onboarding smoke, so the
matrix rerun can use physical `iPhone-preview` evidence only.

Rows in scope:

- Notes sterile editor: pass only if Notes opens to a blank/sterile editor or a
  known sterile note, not a private notes list.
- Safari local normal field: use the local sterile fixture from
  `docs/goals/ios-v0.26-apple-host-app-matrix-rerun/notes/fixture/index.html`.
- Safari local secure field: expected rejection; Foil Keyboard and Insert
  latest should be absent and the staged transcript should remain in App Group
  until cleanup.
- Messages fake-recipient compose: draft-only through a redacted fake-recipient
  `sms:` payload; prove no send and cleanup.

Rows out of scope:

- Mail remains deferred under issue #12.
- Real Messages delivery and existing private threads remain out of scope.
- Arbitrary iPhone app support remains out of scope.

## Reusable Fixtures And Commands

Physical automation:

- WDA direct URL: `http://192.168.1.40:8100`
- current known session: `181D521D-E0EC-4606-AEA7-3FF20B055610`
- harness status: `scripts/ios-physical-harness.py status --wda-url http://192.168.1.40:8100`
- source fetch: `scripts/ios-physical-harness.py fetch-source ... --wda-url http://192.168.1.40:8100 --output /tmp/...`
- evidence helper: `scripts/ios-physical-harness.py receipt ... --write-json notes/receipts/...`

Sterile transcript pattern:

- stage with `scripts/ios-physical-harness.py stage-transcript --transcript-file /tmp/...`
- use a unique, non-private phrase per row
- commit only hashes/counts from receipts, not transcript bodies
- after insertion or rejection, prove App Group state is idle/no transcript or
  deliberately still staged before cleanup

Safari fixture:

- serve the fixture from a local host/port reachable by the phone
- open Safari with `devicectl ... --payload-url http://<mac-ip>:<port>/`
- prior passing Insert latest tap used full-screen coordinate near `{x:207,y:615}`

Messages fixture:

- open with `devicectl ... com.apple.MobileSMS --payload-url <redacted fake-recipient sms URL>`
- do not navigate thread lists
- do not tap send
- cleanup must prove the draft no longer contains the sterile transcript and
  App Group returns to idle/no transcript

## Stop Conditions

Stop and record an exact blocker if:

- Notes or Messages exposes private content before a sterile input is focused.
- WDA becomes unavailable and cannot be restarted without device/account action.
- TestFlight/device metadata no longer reports Foil iOS build `12`.
- Any receipt would require committing raw WDA source, screenshots, contacts,
  phone numbers, thread content, provider keys, or transcript bodies.

## Receipt Contract

For pass rows, receipts must prove:

- pre-insert keyboard readiness when insertion is expected
- intended field receives the sterile value exactly once
- Insert latest becomes disabled after insertion
- secure field rejects Foil Keyboard and preserves staged App Group state
- cleanup returns App Group to `idle` with `hasTranscript=false`
- all raw WDA sources remain under `/tmp`
