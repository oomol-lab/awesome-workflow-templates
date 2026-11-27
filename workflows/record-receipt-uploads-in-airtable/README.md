# Record Receipt Uploads in Airtable

Send a receipt file to a webhook and receive a summary after its extracted fields are saved in Airtable.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/record-receipt-uploads-in-airtable.n8n.json)
<!-- template-actions:end -->

## Setup

1. In **Receive an authenticated receipt**, select a Header Auth credential for the webhook caller. Use a dedicated secret. In all three Mindee HTTP nodes, select a separate Header Auth credential whose header name is `Authorization` and whose value is the Mindee V2 API key. [Mindee file uploads](https://docs.mindee.com/integrations/client-libraries-sdk/send-a-file-or-url)
2. In **Set destinations and check the file**, enter the Mindee model ID and Airtable base and table IDs. The model must expose single values for `purchase_category`, `date`, `currency`, `locale`, `supplier_name`, `time` and `total_amount`. Edit the model field names in `fieldNames` if needed. Configure ISO dates and three-letter uppercase currency codes.
3. In Airtable, create `category`, `currency`, `locale`, `merchant` and `time` as text fields, `date` as a date-only field, and `total` as a number field with sufficient precision. Connect an Airtable personal access token with access to create records in the configured base. [Airtable record creation](https://airtable.com/developers/web/api/create-records)
4. Activate the workflow and POST one supported receipt as raw bytes to its production HTTPS webhook. Include your webhook authentication header. Allow at least 65 seconds on the client and any reverse proxy. The template accepts PDF, JPEG, PNG, WebP, TIFF, HEIC and HEIF up to 10 MiB. [Mindee file limits](https://docs.mindee.com/integrations/technical-limitations)

## Behavior

The workflow sends the uploaded bytes to Mindee as a file, polls the same job up to eight times at three-second intervals, and checks the linked inference from the configured model. It creates one Airtable record with the seven validated values. When Airtable confirms those values, the original request receives HTTP 200 with a one-item JSON array containing `data` and a formatted expense `message`.

A missing or unreadable receipt field produces an error. The processing budget is 55 seconds, including the Airtable write. If Mindee takes too long, the original request receives HTTP 504 and no Airtable record is attempted. A failed or unconfirmed Airtable response returns an error. Before resending a timed-out request, check Mindee and Airtable because a previous submission may already have been accepted. The workflow performs no automatic write retries or deduplication.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

Set the webhook upload and Mindee file names to the same binary field. Use Mindee V2 and wait for its result within the synchronous request window. Return the confirmed record fields as a JSON object in `data`.

Adapted from [Receipt uploads to Mindee and Airtable](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Airtable/1120_Airtable_Mindee_Automate_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Zie619 / n8n-workflows.

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
