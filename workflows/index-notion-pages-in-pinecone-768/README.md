# Index Notion Pages in Pinecone 768

Embed new Notion page text and store the vectors and page metadata in Pinecone.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/index-notion-pages-in-pinecone-768.n8n.json)
<!-- template-actions:end -->

## Setup

Create a new Pinecone dense index with 768 dimensions. Configure Notion database access and name its title property Name, or adjust **Prepare page text**. Prevent overlapping runs.

## Behavior

Each new page is processed separately. Direct page blocks are read, images and video excluded, and text split into 1,000-character windows with 120-character overlap, up to 20 chunks per page. Gemini Embedding 2 generates 768-dimensional vectors; Pinecone records contain the page ID, creation time, title and chunk text. Existing vectors from other embedding models cannot be compared with these vectors; re-embed into a fresh index. Page content is sent to Gemini and Pinecone and may appear in execution history. Code input and output ports must each fit 1 MiB. No vector search is included.

Reconcile partial writes manually.

The source model text-embedding-004 was retired. The replacement changes the embedding space; both formats explicitly request 768 dimensions. See [Google's embedding documentation](https://ai.google.dev/gemini-api/docs/embeddings) and [Pinecone's upsert API](https://docs.pinecone.io/reference/api/2025-10/data-plane/upsert).

<details>
<summary>Inspiration &amp; credits</summary>

Use a supported Gemini model and process pages separately.

Adapted from [Notion to Vector Store - Dimension 768](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Filter/1570_Filter_Summarize_Automation_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
