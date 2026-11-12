# Fetch Bible Passages by Reference

Fetch Bible passages for one or more references using the GetBible API.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/fetch-bible-passages-by-reference.openflow.json) · [n8n JSON](templates/fetch-bible-passages-by-reference.n8n.json)

## Setup

Provide `references` as an array of Bible references, such as `["John 3:16", "Romans 3:16"]`, and optionally set a translation and API version. If references are omitted, the workflow uses `John 3:16`; the defaults for translation and version are `kjv` and `v2`. The n8n version is a sub-workflow called by another workflow. In Open Flow, run it with Start inputs or call it as a workflow. Network access to `query.getbible.net` is required.

## Behavior

The references are joined into one GetBible query and the API's JSON is returned under `result`. Ranges and comma-separated verses are passed to GetBible for interpretation. A failed request stops the run. The external service determines available translations and returned text.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Encode URL path components so spaces and punctuation in references are transmitted safely.

Adapted from [GetBible Query](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Http/1871_HTTP_Executeworkflow_Import_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
