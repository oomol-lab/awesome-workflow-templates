# Create and Email Pennylane Invoices

Create a finalized Pennylane invoice from an authenticated request and wait for Pennylane to accept its email.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/create-and-email-pennylane-invoices.n8n.json)
<!-- template-actions:end -->

## Setup

1. Bind **HTTP Basic Auth** in **Receive Invoice Request**. Give access only to trusted callers authorized to issue and email invoices for this company. Bind a Pennylane company API token as **Header Auth** with the header name `Authorization` and value `Bearer <token>` in **Look Up the Invoice Reference**, **Find Customer by Email**, **Create Company Customer**, **Create Finalized Invoice**, and **Send to the Matched Customer Email**. Configure sequential invoice numbering in Pennylane.
2. Create a dedicated Data Table with the text column `request_key` and select it in **Check the Request Reservation** and **Reserve the Invoice Reference**. Run a single active copy in self-hosted regular mode with `N8N_CONCURRENCY_PRODUCTION_LIMIT=1`. Keep the reservations. Use a separate table for each company and preserve it when updating the workflow.
3. Configure the HTTP client and every proxy to wait at least eight minutes for the synchronous response. Allow extra time for queued executions. Activate the workflow and use its production webhook URL. Use the company's sandbox for test requests. Pennylane warns that emailing an invoice eligible for electronic invoicing prevents later transmission through an approved platform. Use this endpoint only for documents approved for email delivery. [Pennylane email endpoint](https://pennylane.readme.io/reference/sendbyemailcustomerinvoice)

## Request

POST a JSON object with `send_email: true`, a stable unique `reference`, `customer_name`, `customer_email`, and a nonempty `items` array. Each item needs `label`, a positive numeric `quantity`, and a positive numeric `unit_price`. Optional fields are `customer_address`, `customer_postal_code`, `customer_city`, `customer_country`, `currency`, `due_date`, and per-item `vat_rate`. When omitted, country is FR, currency is EUR, the due date is 30 days ahead in UTC, and VAT code is `FR_200`. Supply the correct VAT code for every invoice. The original template’s 5.5% example code `FR_055` is sent using the current Pennylane code `FR_55`. The workflow rounds unit prices to two decimals and returns Pennylane's recorded invoice amount.

Use the same reference when checking or troubleshooting one invoice. A second request for a reserved or existing reference receives HTTP 409 before a new financial write. If a request times out, look up the reference in Pennylane and check the email history before taking action. A closed connection does not undo work already accepted by Pennylane.

## Behavior

The workflow looks up the customer by email and creates a company customer when there is no match. It stops on ambiguous matches. It creates a finalized invoice and verifies the customer and reference before sending to the matched address from the request. It waits one minute before the first send and repeats only on Pennylane HTTP 409, up to five total sends. A Pennylane HTTP 204 means the email was accepted for sending.

The final HTTP 200 body reports `success`, `invoice_id`, `invoice_number`, `amount`, `customer`, `public_url`, and `email_sent`. A known rejection or all five conflicts returns `success: false`, `invoice_created: true`, and `email_sent: false`. An indeterminate dispatch returns `email_sent: null`; the workflow does not resend it. If invoice creation itself cannot be confirmed, the caller receives an error and the reference stays reserved. Use Pennylane to verify the invoice and any dispatch before altering a reservation.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Create and send Pennylane invoices from webhook data](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/Other_Integrations_and_Use_Cases/Create%20and%20send%20Pennylane%20invoices%20from%20webhook%20data.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). Gauthier Huguenin provided the source under the MIT License. The collection notice is separate. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

## Changes to the source

Keep the email branch and add a stable reference reservation. Confirm the created invoice and send to the single verified address. Distinguish confirmed rejection from an unknown send result.

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
