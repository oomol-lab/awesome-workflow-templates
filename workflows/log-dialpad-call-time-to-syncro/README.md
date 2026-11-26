# Log Dialpad Call Time on a Syncro Ticket

Look up the ticket for a finished Dialpad call in Google Sheets and log the call time in Syncro.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/log-dialpad-call-time-to-syncro.n8n.json)
<!-- template-actions:end -->

## Setup

1. In your mapping sheet, make columns A and B contain the headers `Call` and `Ticket` in row 1. Keep Call IDs as plain text. Ticket values are Syncro API Ticket IDs.
2. In **Read the ended call**, set your spreadsheet ID, tab, Syncro subdomain, and technician User ID. Connect Google Sheets OAuth2 in **Read the call mapping sheet**. In **Create the Syncro ticket timer**, attach a **Header Auth** credential named `Authorization` with value `Bearer YOUR_SYNCRO_API_TOKEN`. The token needs **Ticket Timers - Overview**. [Syncro API reference](https://api-docs.syncromsp.com/#/Ticket/post_tickets__id__timer_entry)
3. Use one dedicated n8n Data Table for this Dialpad webhook and Syncro account. Add four text columns, `call_key`, `ticket_id`, `status`, and `receipt`. Select the same table in **Read the call reservation**, **Reserve the call and ticket**, and **Save the timer receipt**. Use self-hosted n8n in regular mode with `N8N_CONCURRENCY_PRODUCTION_LIMIT=1` so lookup and reservation share one production slot. Keep a single active copy for this webhook and table. Pause deliveries and let active and queued runs finish before running manually or editing reservations. [n8n concurrency control](https://docs.n8n.io/hosting/scaling/concurrency-control/)
4. Give **Verify the Dialpad signature** a **JWT Auth** credential with key type **Passphrase**, algorithm **HS256**, and a secret you generate for Dialpad. Activate the workflow. Register the production URL from **Receive signed Dialpad events** as a Dialpad webhook with the same secret and subscribe it to the `hangup` state. [Create a signed webhook](https://developers.dialpad.com/reference/webhookscreate) · [Subscribe to call events](https://developers.dialpad.com/reference/webhook_call_event_subscriptioncreate)

## Behavior

The webhook verifies the signed Dialpad request before reading the mapping sheet. Only `hangup` events can create timers. It uses Dialpad's start and end timestamps in milliseconds and includes the contact name and phone number when available.

A unique Call ID with a Ticket ID is reserved before creating the timer. A missing match or blank Ticket returns HTTP 200 with an empty JSON array and leaves the call unreserved. Multiple rows for the same Call ID return HTTP 409. An invalid signature returns HTTP 401.

A confirmed call returns HTTP 200 with the saved timer ID, ticket ID, technician ID, and start and end times in a JSON array. Repeat deliveries return the same receipt. A repeat delivery for a pending call returns HTTP 202 with its reserved ticket ID and makes no new request to Syncro. Review that ticket if the original execution failed. Dialpad's default timeout is five seconds, so a slow execution can still be running when Dialpad retries. [Dialpad delivery retries](https://developers.dialpad.com/docs/webhook-delivery-failures)

Keep the reservations across runs. If an execution fails after reservation, check the reserved ticket against the original timestamps and technician. Remove a pending row for a deliberate retry only after confirming that Syncro created no timer. Keep confirmed rows to prevent later replays from creating another timer.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Update specific post-call information on Syncro](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Noop/0172_Noop_GoogleSheets_Create_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Jonathan / bionemesis (original workflow) and Zie619 (collection). See the [original n8n listing](https://n8n.io/workflows/1489-update-specific-post-call-information-on-syncro/).

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
