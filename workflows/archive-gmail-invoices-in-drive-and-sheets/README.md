# Archive Gmail Invoices in Drive and Sheets

Save unread email PDF invoices to Drive and append extracted invoice details to a reconciliation sheet.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/archive-gmail-invoices-in-drive-and-sheets.openflow.json) · [n8n JSON](templates/archive-gmail-invoices-in-drive-and-sheets.n8n.json)

## Setup

Import the n8n workflow and connect Gmail and Google Drive. Configure the destination folder, a Google Sheet with Invoice date, Invoice Description, Total price and Fichero columns, and a Data Table with item_key and status text columns. Prevent overlapping runs.

For direct n8n, connect the OpenAI model and Google Sheets and leave processing mode direct. For Open Flow, select relay mode, set the Open Flow webhook URL, connect Sheets and a model, configure its spreadsheet ID and range, and enable persistent State. Protect the webhook at your deployment boundary. Activate one mode.

## Behavior

Each unread message with a PDF saves its first PDF to Drive, extracts readable text, records the date, saved filename, total and Drive link, then marks the message read. Messages with no PDF are marked read without creating a row. Review extracted values; model output can be wrong. Scanned PDFs need OCR. The extracted text and surrounding data must fit the Open Flow 1 MiB per-Code input/output limit. Invoice text goes to the model; execution histories and Drive/Sheets contain sensitive data. Restrict access and apply retention rules.

If a write has an unknown outcome, inspect Drive, Sheets and Gmail before retrying. The n8n Data Table retains a pending message; finish missing work manually and mark it done, or delete it only when no external write occurred. For an uncertain Open Flow row append, inspect the sheet and replay the same message with its pending key in **Prepare reconciliation row** and resolution confirmed if present or absent if not, then clear the fields. Do not overlap executions.

<details>
<summary>Inspiration &amp; credits</summary>

Save the original PDF into the configured folder directly, keep its Drive link and message association, and mark read only after processing succeeds.

Adapted from [Attachments Gmail to drive and google sheets](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Extractfromfile/1764_Extractfromfile_HTTP_Automation_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
