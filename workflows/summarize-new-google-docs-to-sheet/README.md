# Summarize New Google Docs to a Sheet

Summarize each new Google Doc and append its last modifier and summary to a sheet.

<!-- template-actions:start -->
[![View in Open Flow](../../assets/view-in-openflow.svg)](https://openflow.run/templates/summarize-new-google-docs-to-sheet/) [![n8n JSON](../../assets/n8n-json.svg)](templates/summarize-new-google-docs-to-sheet.n8n.json)
<!-- template-actions:end -->

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

## Setup

Connect Google Drive, Google Docs, Google Sheets and an AI model, and enable persistent State. Configure the target Drive folder in **Watch Drive folder** and the spreadsheet ID in **Reserve summary append**. Create a `Summaries` sheet with `Name`, `Email` and `Summary` columns in that order, and prevent overlapping runs for the same document.

## Behavior

Each new Google Doc in the watched folder is read by ID, summarized, and appended with its last modifying user's name and email. If those fields are missing they are left blank. Content is sent to the model and can appear in execution history; review summaries before relying on them.

An unknown append is not replayed. Inspect the target sheet first. Enter the pending key and `confirmed` or `absent` in **Reserve summary append**, replay, and clear those fields. To intentionally summarize the same document again, remove its completed checkpoint.

<details>
<summary>In n8n</summary>

Import the n8n workflow, configure the Google Drive trigger folder, Google Docs, Google Sheets, the AI model, and a Data Table with `item_key` and `status` text columns.

</details>

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Google Doc Summarizer to Google Sheets](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Googledrive/1673_GoogleDrive_GoogleSheets_Automation_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
