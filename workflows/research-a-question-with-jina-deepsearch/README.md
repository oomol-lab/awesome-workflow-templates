# Research a Question with Jina DeepSearch

Submit one research question in chat and receive a complete Markdown report with source citations.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/research-a-question-with-jina-deepsearch.n8n.json)
<!-- template-actions:end -->

## Setup

1. In **Research with Jina DeepSearch**, attach a **Bearer Auth** credential containing your Jina API key. [Jina DeepSearch API](https://jina.ai/en-US/deepsearch/)
2. Open the chat in the workflow editor and enter a research question. To deploy the hosted chat, make it available from **Enter a research question**, bind a Basic Auth credential for its intended users, and publish the workflow.

## Behavior

Each message starts a separate research request with low reasoning effort. Jina streams events to the workflow. The chat receives the complete report after the stream finishes. The workflow combines answer fragments, keeps inline Markdown citations, and adds source links supplied separately by Jina. It excludes reasoning events. An error or interrupted stream stops the run with no report.

The HTTP node is configured for 180 seconds. Keep the chat connection open while research runs. Hosting and reverse-proxy limits can end the browser request sooner. Questions are sent to Jina.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [AI-Powered Research with Jina AI Deep Search](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Http/1464_HTTP_Stickynote_Automation_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Leonard van Hemert (original workflow) / Zie619 (collection).

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

This adaptation uses authenticated requests and combines completed answer events while preserving Markdown citations.

</details>
