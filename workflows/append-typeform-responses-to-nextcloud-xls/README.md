# Append Typeform Responses to a Nextcloud Workbook

Add each signed Typeform response to an existing Excel 97–2003 workbook in Nextcloud.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/append-typeform-responses-to-nextcloud-xls.n8n.json)
<!-- template-actions:end -->

## Setup

1. Install [SheetJS xlsx 0.20.3](https://docs.sheetjs.com/docs/getting-started/installation/nodejs/) in the [self-hosted n8n JavaScript task runner](https://docs.n8n.io/deploy/host-n8n/configure-n8n/set-up-task-runners.md). Set `NODE_FUNCTION_ALLOW_EXTERNAL=xlsx` for the runner.
2. Prepare an existing Excel 97–2003 `.xls` file up to 2 MiB, with one visible sheet dedicated to plain response data. Put `response_token` and the answer column names in row 1. In **Verify and map the response**, enter the Typeform form ID, the full Nextcloud WebDAV HTTPS URL for this file, and each column's Typeform field ID.
3. Assign the same **Basic Auth** credential with the Nextcloud username and app password in **Download the Nextcloud workbook** and **Save the updated workbook**. Configure one production execution at a time for this workbook. Use a dedicated file that no other automated process writes.
4. In **Compute the Typeform signature**, set **Secret** to the secret you configure for this webhook in Typeform. Activate the workflow and point Typeform's completed-response webhook to the production URL. Use your deployment's secret storage for this value. [Typeform webhook signatures](https://www.typeform.com/developers/webhooks/secure-your-webhooks/)

## Behavior

Each completed, signed submission adds one row. Existing cell values and column order are checked after the workbook is rebuilt. The answer columns accept text, dates as text, numbers, booleans, choices, and URLs. Missing answers leave cells blank.

Use a plain data workbook. Formulas, merged cells, special number formats, macros, and additional sheets are outside this workflow's scope. Keep a backup before connecting your workbook.

The save uses the downloaded file's strong ETag. A changed file or unconfirmed save returns an error, allowing Typeform to retry. A delivery whose response token is already in the workbook returns success without another upload. Keep the endpoint responsive within Typeform's 30-second delivery timeout.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Typeform to Nextcloud spreadsheet](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Typeform/0262_Typeform_Spreadsheetfile_Automate_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Zie619 / n8n-workflows.

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

## Changes to the source

Read the workbook on each signed form submission. Preserve existing rows, validate the resulting XLS and write it back to the same WebDAV URL. Store the response token in the worksheet to recognize redeliveries.

</details>
