# Record Analyzed Retell Calls

Log signed Retell call transcripts and analysis in Google Sheets, Airtable, or Notion.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/record-analyzed-retell-calls.n8n.json)
<!-- template-actions:end -->

## Setup

1. Import the template into n8n. In **Sign the Retell request bytes**, replace the placeholder expression with the Retell API key marked for webhooks. Add the production URL from **Receive Retell call events** to your Retell agent's webhook settings. [Retell signature setup](https://docs.retellai.com/features/secure-webhook)
2. In **Map the call and destinations**, enable any of the three destinations and enter its identifiers. Bind the corresponding credential in **Write the Google Sheets row**, **Write the Airtable record**, or **Write the Notion page**. Google Sheets uses a Google Sheets OAuth2 credential. Use an Airtable Personal Access Token with write access and a Notion integration that can create pages in the target data source.
3. Create an n8n Data Table with text columns `call_key` and `status`. Select the table in **Skip reserved calls**, **Reserve this call**, and **Record completion**. On self-hosted n8n in regular mode, set `N8N_CONCURRENCY_PRODUCTION_LIMIT=1`. Keep one active copy for this webhook and table, and avoid overlapping manual runs.

Use these headers in the Google Sheets tab, in this order. Use the same field names in Airtable, with date-time fields for the two dates, number fields for duration and cost, and text fields for the rest.

`Call ID`, `Start Datetime`, `End Datetime`, `Duration in seconds`, `Transcript`, `Call Summary`, `User Sentiment`, `Phone Number`, `Total Cost in Dollars`.

For Notion, use a data source ID and the same fields and types. Use a title property named `Name` for the call summary in place of a separate `Call Summary` property.

## Behavior

The webhook checks Retell's signature on the original request bytes and accepts timestamps within five minutes. It acknowledges correctly signed deliveries and ignores events other than `call_analyzed`. Acknowledgment confirms receipt. Check the execution for the write outcome.

Each analyzed call is saved only in enabled destinations. The record contains both timestamps in UTC, billed seconds, cost in US dollars, and the number on the other end of the call. An unavailable transcript, summary, sentiment or phone number is left blank. Sheets receives literal values, including phone numbers and text beginning with an equals sign. Sheets and Notion accept up to 50,000 characters per text field in this template.

The workflow checks each destination's response against the call ID. If a write fails, completed writes in earlier destinations may remain. The call stays reserved to prevent duplicate writes. Check the selected destinations before clearing a pending reservation for a deliberate retry.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Authenticate Retell's original request bytes before saving call data.
- Replace the sample accounts with configurable destinations. Preserve the source fields and use UTC timestamps.
- Record completion only after all enabled destinations return matching receipts. [Original workflow listing](https://n8n.io/workflows/3504-store-retell-transcripts-in-sheets-airtable-or-notion-from-webhook/)

Adapted from [Store Retell transcripts in Sheets, Airtable or Notion from webhook](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Webhook/0845_Webhook_Filter_Export_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Agent Studio (original workflow); Zie619 / n8n-workflows (collection).

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
