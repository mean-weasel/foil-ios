# T004 Messages And Mail Rows

## Result

`blocked_operator_sterile_fields_needed`

## Messages

Messages requires an operator-opened sterile self/test thread with the draft
field focused. This run did not launch or inspect Messages because thread lists,
contacts, phone numbers, or message text could be exposed.

## Mail

Mail requires an operator-opened blank compose window with sterile recipient and
body state. This run did not inspect Mail because inbox/account surfaces could
be exposed.

## Exact Unblock

Open the desired sterile field on the preview phone, leave the cursor focused,
and rerun the row using WDA direct URL `http://192.168.1.40:8100`.
