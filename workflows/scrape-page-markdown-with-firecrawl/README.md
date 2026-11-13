# Scrape Page Markdown with Firecrawl

Call Firecrawl to scrape one page and return its Markdown.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/scrape-page-markdown-with-firecrawl.openflow.json) · [n8n JSON](templates/scrape-page-markdown-with-firecrawl.n8n.json)

## Setup and use

Connect Firecrawl in Open Flow, then run or call the workflow with a page **url**. In n8n configure an HTTP Header Auth credential with `Authorization: Bearer YOUR_FIRECRAWL_API_KEY`, and call the subworkflow with `{"query":{"url":"https://example.org/page"}}`.

## Behavior

The workflow requests one page in Markdown and returns it as **response**. Firecrawl determines what it can access and extract. A successful API response may still contain an error page from the target site; inspect its content before relying on it. API failures stop the workflow.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Use Firecrawl v2 rather than v1 and set maxAge to 0 for a fresh scrape. Open Flow uses the Firecrawl action and takes a flat URL input; n8n retains the nested query input and uses a JSON expression.

Adapted from [get_a_web_page](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Http/1131_HTTP_Stickynote_Import_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
