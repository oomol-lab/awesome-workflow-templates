# Upload Multiple Files to a Named Drive Folder

Upload multiple form files to a named Google Drive folder, creating it when needed.

<!-- template-actions:start -->
[![View in Open Flow](../../assets/view-in-openflow.svg)](https://openflow.run/templates/upload-multiple-files-to-named-drive-folder/) [![n8n JSON](../../assets/n8n-json.svg)](templates/upload-multiple-files-to-named-drive-folder.n8n.json)
<!-- template-actions:end -->

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

## Setup

Allow uploads through the form and prevent overlapping submissions targeting the same new folder.

For Open Flow set mode to relay in **Prepare folder request**, configure its webhook URL, connect the same Google Drive account and enable persistent State. Restrict webhook access. File bytes are not sent to Open Flow.

## Behavior

Submit a folder name and multiple files. The workflow finds exactly one matching folder directly under the configured parent, or creates it, then uploads each file with its original name to that folder. Multiple same-name folders stop the run for manual selection. Folder contents and filenames may appear in execution history; protect access.

If folder creation is uncertain, inspect the parent before retrying. In Open Flow set **Reserve folder creation** to applied when the folder exists or absent when it does not, replay the same request, then clear the field.

<details>
<summary>In n8n</summary>

Import the n8n workflow, connect Google Drive, set the parent folder ID in **Prepare folder request**, and select a Data Table with item_key and status text columns in all checkpoint nodes. Direct mode runs in n8n; use one mode. In both modes n8n retains and uploads the original binary files. In n8n inspect the folder checkpoint and Drive before marking it done or deleting it. If an upload is uncertain, inspect that file in the destination before retrying; reconcile its pending Data Table row and any remaining files manually.

</details>

<details>
<summary>Inspiration &amp; credits</summary>

Keep binary uploads in n8n, match the parent folder and stop on ambiguous writes.

Adapted from [Bulk File Upload to Google Drive with Folder Management](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Form/0733_Form_Code_Create_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
