# Convert Webhook XML to JSON

Send raw XML or upload an XML file to one POST webhook and receive a JSON response.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/convert-webhook-xml-to-json.n8n.json)
<!-- template-actions:end -->

## Setup

1. In **Set the Slack error channel**, set the ID of the Slack channel that should receive conversion errors. On **Notify Slack of the conversion error**, choose an n8n Header Auth credential with the header `Authorization` and a value of `Bearer YOUR_SLACK_BOT_TOKEN`. Give the Slack app `chat:write` and access to the channel. [Slack message API](https://docs.slack.dev/reference/methods/chat.postMessage/)
2. The webhook imports inactive. To restrict callers, configure native Basic Auth or Header Auth in **Receive XML or a file upload**. Activate the workflow and copy the production HTTPS URL for `tool/xml-to-json`. [n8n Webhook configuration](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.webhook/)

## Request and response

Send one uncompressed UTF-8 XML document, up to 1 MiB. Use one of these request formats.

- Send XML in the body with `Content-Type: application/xml` or `text/xml`. The workflow returns the native webhook XML conversion, which lowercases element names, normalizes text whitespace and groups attributes under `$`.
- Send XML in the body with `Content-Type: text/plain`, or upload one `.xml` file under the multipart field `file`. The XML node preserves element case and merges attributes into their element. Use the same request format for repeat calls if exact key casing or attribute placement matters.

Success returns HTTP 200 and `{"status":"OK","data":{...}}` with JSON content type. The original route is for XML conversion. The workflow rejects `application/json` with the same error behavior as other unsupported inputs.

A conversion error handled by the workflow returns HTTP 500 and `{"status":"error","data":"There was a problem converting your XML. Please refresh the page and try again."}`. The workflow sends one Slack alert after responding. The alert includes a reason category, UTC time and execution ID. It omits the document, headers, upload name and parser details. If Slack fails to confirm delivery, check that channel before resending a notification.

The XML parser uses no external resource resolver. The workflow rejects DOCTYPE, entity declarations, XML processing instructions other than the XML declaration, and XInclude. Malformed XML and multipart requests that reach the workflow receive the same conversion-error response. Your HTTPS proxy should reject requests larger than 1 MiB for raw XML or 1 MiB plus 8 KiB for multipart before forwarding them. Requests rejected before the workflow starts do not send Slack alerts.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

The webhook keeps each request as its own binary input. The workflow extracts one ordinary multipart file or uses the raw body, validates the XML and applies the original media-specific conversion style. It preserves the response fields and sends only operational error information to Slack. [Multipart form requirements](https://www.rfc-editor.org/rfc/rfc7578)

Adapted from [XML to JSON webhook](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Webhook/0483_Webhook_Extractfromfile_Update_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Zie619 / n8n-workflows.

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
