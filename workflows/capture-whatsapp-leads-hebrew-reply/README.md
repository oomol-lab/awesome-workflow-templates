# Capture WhatsApp Leads and Reply in Hebrew

Record incoming WhatsApp messages in Google Sheets and send a Hebrew acknowledgement in the same chat.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/capture-whatsapp-leads-hebrew-reply.n8n.json)
<!-- template-actions:end -->

## Setup

1. Create a dedicated Google Sheet tab with these headers in A1:E1: `Timestamp`, `Name`, `Phone`, `Message` and `Source`. In **Select direct incoming leads**, set the spreadsheet ID and the destination tab’s numeric `gid`. Connect the same Google Sheets OAuth2 credential in **Read the metadata reservation** and **Atomically append the lead and reserve its message ID**.
2. Configure the provider you use. Use a trusted self-hosted n8n deployment with node access to the named secret environment variables, or replace the expressions with supported external secrets. Restrict access to workflow editing, execution history and ingress logs. Use the HTTPS production callback URL.
   - **WAHA**: In **Select direct incoming leads**, set the HTTPS origin without a trailing slash and the session name. In the session webhook set `events` to `["message"]` and `hmac.key` to a random secret of at least 24 characters. Set the same value in `WAHA_WEBHOOK_HMAC_KEY`. Use Header Auth named `X-Api-Key` in **Resolve the original WAHA linked ID** and **Send the Hebrew reply through WAHA**. For linked IDs, use a WAHA engine with access to its LID-to-phone lookup. [WAHA events](https://waha.devlike.pro/docs/how-to/events/) · [WAHA contacts](https://waha.devlike.pro/docs/how-to/contacts/)
   - **Meta Cloud API**: Set the business phone number ID in **Select direct incoming leads**. Set `META_WHATSAPP_APP_SECRET` to the app secret and `META_WHATSAPP_VERIFY_TOKEN` to your own random token of at least 24 characters. Attach a WhatsApp API credential with a token that has messaging access in **Send the Hebrew reply through Meta**. Configure the same production HTTPS callback for GET setup and POST notifications and subscribe the app to `messages`. [Meta webhook setup](https://developers.facebook.com/docs/graph-api/webhooks/getting-started/) · [WhatsApp service messages](https://developers.facebook.com/documentation/business-messaging/whatsapp/messages/send-messages)
3. Publish the workflow. If Meta is unused, its verification request is denied without its verify token. Incoming requests need their configured provider signature before the workflow accepts them.

## Behavior

A verified direct inbound message becomes a row with the sender, E.164 phone, message and receipt time. Israeli numbers with a domestic leading zero are converted to `+972`; valid international numbers keep their country code. Group, status, channel and outgoing events are ignored. For a WAHA linked ID, the workflow checks the matching phone lookup before writing and replies to the original linked chat. Meta contact names are matched to the message sender, and replies are sent only inside that message’s 24-hour service window.

The workflow acknowledges the webhook promptly. It uses one Google Sheets transaction to append the row and reserve the full provider message identity. The short spreadsheet metadata ID selects the reservation. A different message occupying that ID is reported as `metadata_slot_occupied`. Each recorded message uses one Sheets developer-metadata entry. Keep the metadata for as long as duplicates must be blocked. Sheets counts metadata keys and values against a 30,000-character allowance for the destination tab, separate from its 30,000-character spreadsheet-level allowance. When the tab’s allowance is exhausted, new rows and replies stop. [Sheets developer metadata](https://developers.google.com/workspace/sheets/api/guides/metadata) · [Atomic batch updates](https://developers.google.com/workspace/sheets/api/reference/rest/v4/spreadsheets/batchUpdate)

The Hebrew reply is attempted after Sheets confirms the append. A duplicate creates neither another row nor another reply. If the Sheets receipt is uncertain, check the recorded row before taking further action. If the send receipt is uncertain, check the original WhatsApp conversation before replying manually. Execution history can contain contact data and message contents.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Capture WhatsApp Leads to Google Sheets with Instant Hebrew Auto-Reply](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/WhatsApp/Capture%20WhatsApp%20Leads%20to%20Google%20Sheets%20with%20Instant%20Hebrew%20Auto-Reply.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source sticky note credits [Achiya Automation](https://achiya-automation.com). See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

## Changes to the source

The workflow verifies both webhook signatures and the Meta setup challenge. It processes every matching message in a Cloud API delivery and uses each provider’s own send API to reply to the original chat. The Sheets row keeps the original five fields and is protected against repeated events.

</details>
