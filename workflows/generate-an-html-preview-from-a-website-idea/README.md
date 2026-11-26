# Generate an HTML Preview from a Website Idea

Open a webhook URL with a website idea and get a static preview in the browser.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/generate-an-html-preview-from-a-website-idea.n8n.json)
<!-- template-actions:end -->

## Setup

1. Import the workflow and connect an OpenAI credential in **Design the website preview**.
2. Publish the workflow and open the production URL from **Receive a website idea**. Append `?query=` followed by the URL-encoded website idea. For example, append `?query=A%20signup%20page%20for%20a%20ceramics%20class`.

## Behavior

The GET request waits for the preview and returns UTF-8 HTML in the same response. A missing, repeated or oversized `query` returns HTTP 400. A request with a valid idea makes one OpenAI call. An unavailable model or invalid result returns HTTP 502.

The preview can include headings, links within the page, lists, tables and form layouts. Images appear as labeled placeholders, and form controls are disabled. The page uses a built-in stylesheet. It does not load scripts, fonts or media. The endpoint is public when the workflow is published without webhook authentication.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Dynamically generate HTML page from user request using OpenAI Structured Output](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Webhook/1415_Webhook_Respondtowebhook_Create_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Agent Studio (original workflow) / Zie619 (collection). See the [original n8n gallery template](https://n8n.io/workflows/2388-dynamically-generate-a-webpage-from-user-request-using-openai-structured-output/).

## Changes to the source

A deterministic renderer replaces the second model call and the external Tailwind script. It checks the structure, escapes text, and permits only approved elements and attributes. The response includes a restrictive document content security policy.

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
