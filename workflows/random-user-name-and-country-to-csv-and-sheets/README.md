# Random User Name and Country to CSV and Sheets

Fetch a random user, create a CSV and append the same fields to Google Sheets.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/random-user-name-and-country-to-csv-and-sheets.openflow.json) · [n8n JSON](templates/random-user-name-and-country-to-csv-and-sheets.n8n.json)

## Setup and use

Connect Google Sheets and set the spreadsheet ID and range in **Append user to sheet**. Set the destination headers to name and country, in that order. In n8n connect Google Sheets, select its spreadsheet and sheet, and use the same headers. Run one format manually.

## Behavior

Each run requests one example user from Random User, creates a CSV containing the name and country, and appends those fields to the sheet. Open Flow returns the CSV artifact after the sheet write succeeds. Each run appends a new row. If the append result is unknown, inspect the sheet before retrying. Random User availability and returned data depend on the service.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Add a manual trigger, replace the source spreadsheet ID, and expose the CSV artifact in Open Flow.

Adapted from [JSON to Google Sheets and CSV](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Http/0223_HTTP_GoogleSheets_Automation_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
