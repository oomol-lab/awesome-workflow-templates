# Process Pennylane Invoice Requests

Issue a finalized Pennylane invoice from a Basic-auth POST and optionally wait for confirmation that its email was accepted.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/process-pennylane-invoice-requests.n8n.json)
<!-- template-actions:end -->

## Setup

1. Bind **HTTP Basic Auth** to **Receive Invoice Request**. Share it only with callers authorized to issue invoices and choose whether to email them. Activate the workflow and use its production HTTPS POST URL ending in `/webhook/pennylane-invoice` for both modes. When replacing the original workflow on the same instance, deactivate it before activating this template to free the webhook path.
2. Bind the Pennylane company API token as **Header Auth** with header `Authorization` and value `Bearer <token>` in **Look Up the Invoice Reference**, **Find Customer by Email**, **Create Company Customer**, **Create Finalized Invoice**, and **Send to the Matched Customer Email**. Configure sequential invoice numbering in Pennylane. Use a sandbox company to configure and test. [Create a customer invoice](https://pennylane.readme.io/reference/postcustomerinvoices)
3. Create a dedicated Data Table with string columns `invoice_reference` and `idempotency_key`. Select the same table in **Check the Request Reservation** and **Reserve the Invoice Reference**. Use a separate table for each company and keep its rows across revisions. Run a single active copy in self-hosted n8n regular mode with `N8N_CONCURRENCY_PRODUCTION_LIMIT=1`. Avoid overlapping manual runs. [n8n concurrency control](https://docs.n8n.io/deploy/host-n8n/configure-n8n/scaling/control-concurrency.md)
4. Allow at least eight minutes plus queue time in the caller, proxy and execution timeouts to support up to five waits. Use email delivery only for documents authorized for email. Pennylane warns that emailing an invoice eligible for e-invoicing prevents later transmission through an approved platform. [Send a customer invoice by email](https://pennylane.readme.io/reference/sendbyemailcustomerinvoice)

## Request

POST JSON with `customer_name`, `customer_email`, and a nonempty `items` array. Each item requires a `label`, positive numeric `quantity`, and positive numeric `unit_price`. Optional fields are `customer_address`, `customer_postal_code`, `customer_city`, `customer_country`, `currency`, `due_date`, `reference`, `send_email`, and per-item `vat_rate`. Defaults are FR, EUR, due in 30 days (UTC), and VAT code `FR_200`. The legacy 5.5% French code `FR_055` is converted to Pennylane's current `FR_55`. The workflow uses two decimal places for unit prices and returns Pennylane's invoiced amount.

Set `send_email: true` as a JSON boolean to request email. An omitted value, `false`, or any other value confirms the invoice immediately after creation, without sending an email. The same URL and credential apply to both modes.

Supply a unique `reference`, an optional `Idempotency-Key` header with 1–128 letters, digits, periods, underscores, colons or hyphens and a leading letter or digit, or both. A reference is sent to Pennylane. The header stays in the workflow's reservation table. Reusing either identifier returns HTTP 409 before another financial write on this deployment. When both are omitted, separately submitted requests can create separate invoices even if their bodies match. After a timeout or a lost response, check the invoice and email history in Pennylane before submitting again, especially when the original request had neither identifier.

## Behavior

The workflow matches the customer by the exact email or creates a company customer if none exists. It stops on ambiguous matches. It issues one finalized invoice, then verifies the customer, currency and any supplied reference. The email route waits a minute before requesting delivery to the verified input address. A Pennylane 409 can trigger another wait and attempt, up to five total attempts. HTTP 204 confirms Pennylane accepted the email for sending.

The HTTP 200 response includes `success`, `invoice_id`, `invoice_number`, `amount`, `customer`, `public_url`, and `email_sent`. Direct confirmation uses `email_sent: false`. Accepted email uses `email_sent: true`. A known email rejection returns `success: false`, `invoice_created: true` and `email_sent: false`. An uncertain result uses `email_sent: null` with no automatic resend. If invoice creation cannot be confirmed, the request fails and any supplied identity stays reserved. A closed connection does not undo an accepted write. Keep the keys protected as operational records.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Create and send Pennylane invoices from webhook data](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/Other_Integrations_and_Use_Cases/Create%20and%20send%20Pennylane%20invoices%20from%20webhook%20data.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). Gauthier Huguenin provided the source under the MIT License. The collection notice is separate. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

## Changes to the source

Keep both modes on one webhook. Verify the customer and invoice receipts, reserve any supplied request identity, and distinguish a known email rejection from an uncertain result.

> MIT License
> Copyright (c) 2026 Gauthier Huguenin
>
> Permission is hereby granted, free of charge, to any person obtaining a copy
> of this software and associated documentation files (the "Software"), to deal
> in the Software without restriction, including without limitation the rights
> to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
> copies of the Software, and to permit persons to whom the Software is
> furnished to do so, subject to the following conditions:
>
> The above copyright notice and this permission notice shall be included in
> all copies or substantial portions of the Software.
>
> THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
> IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
> FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
> AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
> LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
> OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
> THE SOFTWARE.

</details>
