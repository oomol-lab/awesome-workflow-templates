# Reply to LINE Texts and Send a Manual Push

Echo signed LINE text messages and send a separate manual push to one configured user.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/reply-and-push-line-text-messages.n8n.json)
<!-- template-actions:end -->

## Setup

1. Enable the Messaging API for your LINE Official Account. Set the **Secret** expression in **Sign the request with the LINE channel secret** to your channel secret. Use an External Secrets expression if your instance supports it, or enter the value privately in the node and keep populated exports private. Bind a Bearer Auth credential with the channel access token in **Reply using the event token** and **Push text to the configured LINE user**. [LINE webhook signature](https://developers.line.biz/en/docs/messaging-api/verify-webhook-signature/)
2. Create a dedicated Data Table with text columns `request_key`, `status`, and `receipt`. Select it in the two lookup nodes, both reservation nodes, and both record nodes. Run one active copy in self-hosted regular mode with `N8N_CONCURRENCY_PRODUCTION_LIMIT=1`. Publish and add the production HTTPS URL from **Receive LINE webhook deliveries** to your LINE channel. Click **Verify**, then enable webhooks.
3. To send a manual push, edit **Set one push user, message and retry key**. Enter one LINE user ID, message text, and a new UUIDv4 retry key for that specific message. Set `enabled` to true and run **Start a manual LINE push**. Use a new retry key only for a new push, and avoid overlapping manual runs. [LINE push eligibility and API](https://developers.line.biz/en/reference/messaging-api/#send-push-message)

## Behavior

Valid LINE deliveries receive an empty HTTP 200 before any Messaging API calls, including the empty event list sent by **Verify**. Every eligible text event receives the original reply prefix followed by its own text. Inactive and non-text events are skipped. The workflow skips events too old to reply to, missing a token, or too long for LINE's 5,000-character text limit after the prefix.

The Data Table records accepted, rejected or indeterminate requests by event ID or push key. A repeated webhook or manual push key does not send again. If LINE may have received a request, check the table and your LINE account before attempting recovery. Acceptance confirms LINE queued the request. Keep successful, failed and manual execution data saving off to avoid retaining channel payloads and reply tokens. Check the Data Table for message outcomes.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

Verify the original request bytes, acknowledge before sending, and handle every eligible event in a batch. Keep manual pushes scoped to one configured LINE user and record attempts before sending. [Original workflow by darrell_tw](https://n8n.io/workflows/2733-line-message-api-push-message-and-reply/).

Adapted from [LINE Messaging API reply and push example](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Http/1799_HTTP_Manual_Send_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: darrell_tw (original workflow); Zie619 / n8n-workflows (collection).

The collection’s [MIT notice](https://github.com/Zie619/n8n-workflows/blob/94007c1445d9258a7da116646b79473e7c7c3282/LICENSE) is pinned at a later revision. This is the collection notice at that revision; it does not establish a separate original template author's license. Our changes are listed above; see [repository licensing](../../README.md#licensing).

> MIT License
>
> Copyright (c) 2025 Zie619
>
> Permission is hereby granted, free of charge, to any person obtaining a copy
> of this software and associated documentation files (the "Software"), to deal
> in the Software without restriction, including without limitation the rights
> to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
> copies of the Software, and to permit persons to whom the Software is
> furnished to do so, subject to the following conditions:
>
> The above copyright notice and this permission notice shall be included in all
> copies or substantial portions of the Software.
>
> THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
> IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
> FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
> AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
> LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
> OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
> SOFTWARE.

</details>
