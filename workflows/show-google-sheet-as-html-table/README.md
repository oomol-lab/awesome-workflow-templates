# Show a Google Sheet as an HTML Table

Open a webhook URL to view the rows of a configured Google Sheets range as a browser table.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/show-google-sheet-as-html-table.n8n.json)
<!-- template-actions:end -->

## Setup

1. In **Read the configured sheet range**, select a Google Sheets OAuth2 credential, enter the spreadsheet ID, and set the A1 range to include a header row followed by data. For example, use `'Report'!A1:D100`. The webhook always reads this configured range.
2. In **Receive the table request**, select a Basic Auth credential. Keep authentication enabled for private sheet data. Set Authentication to None only if anyone who reaches the webhook may see the selected cells.
3. Enable the workflow and open its production HTTPS GET URL in a browser. Keep n8n's HTML response sandbox enabled.

## Behavior

The first row supplies column headings. Remaining rows appear in sheet order, with blank cells where a row is short. Empty ranges show an empty-state message. Cell values and headings are escaped as text. The table contains no scripts or external resources.

The browser receives `text/html` in the same HTTP request under n8n's sandbox. Responses disable caching. Each request reads the configured range so the browser can display the latest values. Use a range that completes within your deployment's webhook timeout.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Google Sheets to HTML table workflow](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Googlesheets/0238_GoogleSheets_Respondtowebhook_Automate_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Zie619 / n8n-workflows.

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

This adaptation escapes cell text, uses built-in styles, and enables Basic Auth by default.

</details>
