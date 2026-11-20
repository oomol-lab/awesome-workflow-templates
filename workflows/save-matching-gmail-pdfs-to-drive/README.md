# Save Matching Gmail PDFs to Drive

Classify email PDF attachments by text and save matching originals to Google Drive.

<!-- template-actions:start -->
[![View in Open Flow](../../assets/view-in-openflow.svg)](https://openflow.run/templates/save-matching-gmail-pdfs-to-drive/) [![n8n JSON](../../assets/n8n-json.svg)](templates/save-matching-gmail-pdfs-to-drive.n8n.json)
<!-- template-actions:end -->

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

## Setup

Connect Gmail, Encodian, Gemini and Google Drive. Set the destination folder ID in **Choose the next attachment** and the document type in **Prepare PDF classification**. Configure Gmail file transit and replace the example hostname in **Verify complete attachment** with your transit hostname. Enable persistent State.

## Behavior

The workflow checks Gmail every minute, examines each PDF attachment separately, extracts its text layer via Encodian, and uploads the original file to Google Drive when Gemini matches the configured document type. Non-PDF attachments are skipped.

<details>
<summary>In n8n</summary>

Import the n8n workflow, connect Gmail, OpenAI and Google Drive, select the destination folder, and set the document type in **Configure PDF matching**.

</details>

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Send specific PDF attachments from Gmail to Google Drive using OpenAI](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Code/0298_Code_Readpdf_Send_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
