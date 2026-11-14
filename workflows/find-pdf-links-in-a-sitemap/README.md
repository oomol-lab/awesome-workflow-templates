# Find PDF Links in a Sitemap

Fetch a sitemap and return entries whose URL ends in .pdf.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/find-pdf-links-in-a-sitemap.openflow.json) · [n8n JSON](templates/find-pdf-links-in-a-sitemap.n8n.json)

## Setup and use

Set **Fetch sitemap** to the URL of the XML sitemap to inspect and run manually. In n8n set **Set sitemap URL** to the same URL and run the workflow. The default is the source's example sitemap.

## Behavior

The workflow parses sitemap entries and returns those whose loc ends in lowercase .pdf, retaining the other entry fields. It does not traverse sitemap indexes.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Open Flow returns matching entries as an array.

Adapted from [Sitemap.xml reader](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Splitout/1143_Splitout_Filter_Automation_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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

Open Flow bundles [fast-xml-parser 4.4.1](https://github.com/NaturalIntelligence/fast-xml-parser) and strnum 1.0.5 under MIT; their notices are included in the workflow code.

</details>
