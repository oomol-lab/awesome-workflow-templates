# Index Updated Tech Radar Documents

Index text from updated documents in a Drive folder.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/index-updated-radar-documents.n8n.json)
<!-- template-actions:end -->

## Setup

Select the watched folder. Connect Google Drive, LlamaCloud, Gemini and Pinecone, and use a 3072-dimensional Pinecone index. Parsing is polled every two seconds with a bounded timeout.

## Use

Updated files in the folder are parsed to text, split into overlapping passages and indexed. Other file types follow text extraction. LlamaParse can truncate text beyond 64 KB per page; review unusually dense documents. Changes to a document create a new set of vectors; remove obsolete versions according to your index retention policy. Avoid overlapping executions for the same document.

For a confirmed upload also enter its parse job ID. Clear recovery fields afterward. The MySQL refresh and chat paths are separate from this component.

<details>
<summary>Inspiration &amp; credits</summary>

Extract the Drive ingestion path, use current Gemini embeddings and a LlamaParse relay for common document formats, and add write checkpoints.

Adapted from [Tech Radar](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Code/1836_Code_Googledocs_Automation_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Zie619 / n8n-workflows.

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
