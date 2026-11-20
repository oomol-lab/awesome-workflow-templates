# Summarize Google Search and Notify

Extract and summarize Google search results and send them to a webhook.

<!-- template-actions:start -->
[![View in Open Flow](../../assets/view-in-openflow.svg)](https://openflow.run/templates/summarize-google-search-and-notify/) [![n8n JSON](../../assets/n8n-json.svg)](templates/summarize-google-search-and-notify.n8n.json)
<!-- template-actions:end -->

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

## Setup and use

Set the search query and SERP zone in **Prepare search request**, bind secret Variable BRIGHT_DATA_TOKEN, configure the models, and set the destination URL in **Send search results**. In n8n configure Bright Data Header Auth as Authorization: Bearer followed by the API token, connect the Gemini models, and set the query, zone and webhook URL. Run one format manually.

## Behavior

The workflow requests the Google result page through Bright Data, extracts readable results, summarizes them and POSTs search_result and search_summary to the configured endpoint. Model results can be inaccurate; inspect cited sources. Provider and model usage may incur charges. If the notification result is uncertain, check the destination before retrying.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Use explicit notification routing rather than relying on a model tool call, and replace the example webhook URL with configuration.

Adapted from [Bright Data Google search summarization](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Manual/1467_Manual_Stickynote_Automation_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
