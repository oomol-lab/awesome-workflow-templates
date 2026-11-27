# Reply to Fiwano Messages

Echo text and acknowledge attachments on the original WhatsApp, Instagram, or Messenger conversation.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/reply-to-fiwano-messages.n8n.json)
<!-- template-actions:end -->

## Setup

1. Install the verified `n8n-nodes-fiwano` community package, tested with version 1.11.0. Create a **Fiwano API** credential with your API key and a nonempty Webhook Secret. Attach it to **Receive Fiwano messages** and **Reply on the original channel**. In **Receive Fiwano messages**, replace the setup expression in **Webhook Secret** with that same secret using a secret expression or the masked field. Keep any configured export private. [Fiwano community nodes](https://github.com/fiwano-com/n8n-nodes-fiwano)
2. Use a single production execution slot and a dedicated Data Table with text columns `event_key`, `status` and `receipt`. Select it in **Skip messages already handled**, **Reserve this reply** and **Record the Fiwano receipt**.
3. Activate the workflow with the channel list in **Check the channel and compose the reply** still empty. In Fiwano, register the production HTTPS webhook URL only on channels you are authorized to operate. Enable **Message Received** and set the webhook secret to match the credential. Check that a request with no signature returns HTTP 401 before adding those channel IDs to the list. Repeat that check if you change the credential or rotate its secret. [Fiwano webhook setup](https://fiwano.com/documentation/webhooks)

## Behavior

The trigger verifies the Fiwano signature and acknowledges the incoming event. Text replies echo the received text. Attachments get a short acknowledgment with their type and MIME type when available. The workflow uses the incoming channel ID and sender to address the reply. It skips other events and messages from channels outside the configured list. It does not download attachments. Very long echoes are shortened to fit the channel's message limit.

The Data Table reserves one attempt per channel and incoming message ID. A retry of the webhook skips an existing reservation, including those whose outcome is still pending. The reply receipt records Fiwano's accepted or queued status. Check the Fiwano dashboard for delivery and reconcile a pending entry before retrying. Retrying directly at the send node bypasses the reservation.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Receive and Send Messages Across WhatsApp, Instagram and Facebook Messenger with Fiwano](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/WhatsApp/Receive%20and%20Send%20Messages%20Across%20WhatsApp%2C%20Instagram%20and%20Facebook%20Messenger%20with%20Fiwano.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). Fiwano maintains the official community nodes and the corresponding example. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

[Fiwano example and documentation](https://github.com/fiwano-com/n8n-nodes-fiwano/tree/main/workflows). This adaptation adds an explicit channel list, signature setup and one reply attempt per incoming message.

</details>
