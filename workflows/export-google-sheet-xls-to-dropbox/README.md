# Back Up a Google Sheet to Dropbox as XLS

Every 15 minutes, export the rows of a Google Sheets range as a legacy Excel workbook and replace a Dropbox file.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/export-google-sheet-xls-to-dropbox.n8n.json)
<!-- template-actions:end -->

## Setup

1. Attach your Google Sheets OAuth2 credential to **Read the Google Sheets range**. Enter the spreadsheet ID and an A1 range starting with a header row, such as `'Prices'!A1:D200`. Use unique text headings.
2. Attach a Dropbox OAuth2 credential with write access in **Overwrite the Dropbox file**. Set the destination path to the `.xls` file you intend to replace. The default is `/my-sheets/prices.xls`. Create the folder in Dropbox before running.
3. Enable the workflow to back up the selected range every 15 minutes. A manual execution also replaces that file.

## Behavior

The workflow exports cell values into one legacy Excel XLS worksheet named `Sheet`. Numeric cells remain numeric, and text such as `001` stays text. The workbook contains a header row and the requested data rows. Formulas contribute evaluated values. Formatting, comments and other tabs stay in the source spreadsheet.

Each successful upload overwrites the same Dropbox path. An empty range leaves the existing file in place. A failed read or conversion stops before upload. The workflow makes no automatic upload retries within a run. If an upload result is uncertain, check Dropbox before running manually again. The next scheduled run reads a fresh snapshot.

Legacy XLS supports up to 65,535 data rows and a header row, 256 columns, and 32,767 characters per cell.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Google Sheets XLS export to Dropbox](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Googlesheets/0082_GoogleSheets_Interval_Process_Scheduled.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Zie619 / n8n-workflows.

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

This adaptation makes the original XLS format and Dropbox overwrite behavior explicit and checks workbook limits before conversion.

</details>
