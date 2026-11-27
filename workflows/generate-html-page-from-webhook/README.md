# Generate an HTML Page from a Webhook

Describe a page in a webhook query and preview the generated HTML in the same browser request.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/generate-html-page-from-webhook.n8n.json)
<!-- template-actions:end -->

## Setup

1. Attach an OpenAI credential to **Design the page**. By default, anyone who can reach the webhook can request a page using that connection. For a restricted audience, set **Authentication** to **Basic Auth** in **Receive the page brief** and select an n8n Basic Auth credential.
2. Activate the imported workflow. Open its production HTTPS webhook URL in a browser and add a URL-encoded `query` parameter. For example, append `?query=A%20signup%20page%20for%20a%20seed%20swap`.

## Behavior

A GET request accepts one `query` value of up to 2,000 characters and sends it to OpenAI. Keep private information out of the URL. The model proposes a title, copy, and a set of sections. The workflow renders that structure as an HTML page and returns it as `text/html` in the same request.

The page is a static mockup. It can show form fields and buttons in a disabled state. It uses built-in styling and escaped text, with no scripts, external resources, or form submissions. Keep n8n's HTML sandbox enabled.

Missing or malformed input returns HTTP 400. Model refusals return HTTP 422. A failed or malformed model response returns HTTP 502. The model request has a 45-second timeout. Use an n8n deployment and HTTPS proxy that allow the request to stay open for that long.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Dynamically generate a webpage from user request using OpenAI structured output](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Webhook/1416_Webhook_Respondtowebhook_Create_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Agent Studio (original workflow) / Zie619 (collection).

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

[Original n8n workflow by Agent Studio](https://n8n.io/workflows/2388-dynamically-generate-a-webpage-from-user-request-using-openai-structured-output/).

This adaptation replaces the source's HTML-writing model and external styling script with a constrained HTML renderer.

</details>
