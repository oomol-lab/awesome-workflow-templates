# Sync Google Sheets Contacts to PostgreSQL

Sync contact names, towns and ages from Google Sheets into an existing PostgreSQL table every hour.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/sync-google-sheets-contacts-to-postgres.n8n.json)
<!-- template-actions:end -->

## Setup

1. Put `first_name`, `last_name`, `town`, and `age` in the first row of the source tab. In **Set the source sheet and target table**, set the spreadsheet ID, tab name, and PostgreSQL schema and table names.
2. Bind a Google Sheets OAuth2 credential with permission to read the source in **Read the Google Sheets contact rows**.
3. Use a PostgreSQL table with text name and town columns, an integer age column, and a non-deferrable unique constraint on `(first_name, last_name)`. Both names must be non-null and the key must compare them case-sensitively. The town and age columns must allow nulls if the sheet leaves them blank. Resolve any duplicate names before enabling the workflow.
4. Bind a PostgreSQL credential in **Apply changes in PostgreSQL** with `SELECT`, `INSERT`, and `UPDATE` permission on the target columns. Enable TLS when connecting to a remote server. Activate the schedule. It runs at the start of each hour in the workflow's time zone, which defaults to UTC.

## Behavior

Each row matches the complete first name and last name, including case and spaces. Different last names are different keys. A repeated full name in the sheet stops the batch before it writes. Use a source where the name pair identifies one contact.

The workflow inserts new contacts and updates changed town and age values. Blank town or age cells become null. Contacts absent from the sheet stay in PostgreSQL. Each run returns the number of source rows and the number changed. A repeated run with the same source data changes zero rows.

One transaction applies the batch. If its outcome is unknown, check PostgreSQL before running the workflow again. Keep imports serial when the source may change. The workflow reads columns A through AZ, and accepts up to 10,000 data rows and 1 MiB of validated JSON per batch.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

Use the complete key already used for updates to identify both new and changed contacts. Apply only insertions and changed values in a single PostgreSQL transaction. [Original workflow by Bela](https://n8n.io/workflows/2081-synchronize-your-google-sheets-with-postgres/).

Adapted from [Synchronize your Google Sheets with Postgres](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Splitout/1998_Splitout_Postgres_Sync_Scheduled.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Bela (original workflow); Zie619 / n8n-workflows (collection).

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
