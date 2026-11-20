# Turn a PDF into a Ghost Blog Post

Turn an uploaded PDF into a structured HTML blog article and create it in Ghost.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/turn-pdf-into-ghost-blog-post.n8n.json)
<!-- template-actions:end -->

## Setup

Protect execution history and both endpoints.

## Behavior

Upload a PDF and supply a unique random Request ID of 16–128 letters, digits, underscores or hyphens. Reuse that ID only for a retry of the same submission. Text is sent to Gemini, which drafts a structured HTML article; Ghost creates the article. Review the result and source citations before publishing.

A pending checkpoint stops a repeated uncertain Ghost write. Avoid overlapping runs for the same Request ID.

<details>
<summary>Inspiration &amp; credits</summary>

Add stable submission IDs and write checkpoints, provide a protected Open Flow relay, and use Gemini for article generation.

Adapted from [📄🛠️PDF2Blog](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Code/1837_Code_Ghost_Automation_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Zie619 / n8n-workflows.

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
