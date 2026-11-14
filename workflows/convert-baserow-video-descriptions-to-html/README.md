# Convert Baserow Video Descriptions to HTML

Convert one or all Baserow video descriptions from Markdown to HTML.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/convert-baserow-video-descriptions-to-html.openflow.json) · [n8n JSON](templates/convert-baserow-video-descriptions-to-html.n8n.json)

## Setup

Connect Baserow and set the same table ID in **Read requested Baserow rows** and **Update same Baserow row**. The table needs a text field named `📥 Video Description` and a text field for HTML. Enter its name in **Convert next description**. In n8n connect Baserow and select the same database, table, and destination HTML field in each read and update node. Activate one format.

## Use

Send a GET request to the webhook. Add a positive row ID as the `rec` query parameter to update one row; omit it to update all rows. The single-row path enables emoji, simple line breaks and backslash escaping of HTML tags; the all-row path uses default conversion options. Raw HTML may remain in the result; sanitize it before displaying untrusted content.

The webhook triggers writes and its acknowledgment does not confirm completion. Unknown updates may have succeeded; inspect the affected row before retrying. Earlier updates are not rolled back. The public endpoint has no built-in authentication; restrict access if needed. Large tables may exceed execution limits.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Replace private Baserow IDs and retain row IDs through Markdown conversion. Open Flow reads all pages and bundles Showdown 2.1.0.

Adapted from [Baserow markdown to html](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Baserow/1822_Baserow_Stickynote_Automation_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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

Open Flow bundles [Showdown 2.1.0](https://github.com/showdownjs/showdown) under MIT; its license is included in the workflow code.

</details>
