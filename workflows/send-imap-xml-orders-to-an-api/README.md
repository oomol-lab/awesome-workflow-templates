# Send IMAP XML Orders to an API

Read the first XML attachment from each IMAP message and POST the parsed order to your HTTPS endpoint.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/send-imap-xml-orders-to-an-api.n8n.json)
<!-- template-actions:end -->

## Setup

1. Import the template into n8n. In **Watch for order emails**, select the IMAP credential and mailbox folder. The default is `INBOX`. Enable SSL/TLS in the credential and leave **Allow Self-Signed Certificates** off.
2. In **Decode the first XML attachment**, replace the sample URL with the HTTPS endpoint that receives your orders. It should accept the original form contract. The parsed XML appears under `orderRequest` using nested form keys such as `orderRequest[Order][Number]`.
3. Activate the workflow. It looks for unread mail received since the activation date, then tracks new message UIDs. Use a dedicated folder to control which messages it can see.

## Behavior

The workflow marks fetched mail as read and checks only the first attachment. It accepts an XML filename or XML media type. Inline message parts are ignored. A message whose first attachment is absent or another type is skipped.

The XML parser retains the document root, ignores attributes, and groups repeated elements into arrays. The workflow returns the API's text response in `status`. Each XML attachment must be valid UTF-8 and no larger than 1 MiB. Invalid XML, document type declarations, and entity declarations stop the batch before it sends anything.

POST requests verify TLS certificates and do not follow redirects or retry automatically. If a request times out or its outcome is unclear, check the destination before retrying any messages from that batch.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Retain the first attachment selection and original form-encoded `orderRequest` structure.
- Validate the XML input and replace the source API URL with configurable HTTPS. Remove the certificate bypasses.

Adapted from [IMAP XML attachment to order API](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Http/0350_HTTP_Emailreadimap_Send_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Zie619 / n8n-workflows.

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
