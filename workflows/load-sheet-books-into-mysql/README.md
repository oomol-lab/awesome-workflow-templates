# Load Google Sheets Book Rows into MySQL

Insert book titles and prices from a Google Sheets range into an existing MySQL table each Monday.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/load-sheet-books-into-mysql.n8n.json)
<!-- template-actions:end -->

## Setup

1. Select the Google Sheets OAuth2 credential in **Read title and price from Google Sheets**. Set the spreadsheet ID and an A1 range containing the `title` and `price` headers followed by the data. For example, use `'Books'!A1:B100`.
2. Select the MySQL credential in **Insert rows into MySQL**. The credential's default database must contain the target table with compatible `title` and `price` columns. Use the existing `books` table or enter another simple table name. Make sure the MySQL session has `NO_BACKSLASH_ESCAPES` disabled. The native insert driver uses backslash escaping for string values. [MySQL client string escaping](https://github.com/mysqljs/sqlstring)
3. Set the workflow time zone if it should differ from the n8n instance. Enable the workflow to run on Mondays at 05:00 in that time zone. A manual execution also runs the insert.

## Behavior

The workflow reads the selected range and validates all returned rows before writing. It preserves titles, numeric prices, and decimal price text. An empty range produces no insert. For a nonempty range, the workflow uses one native `INSERT LOW_PRIORITY IGNORE` statement. Whether low priority affects scheduling depends on the storage engine.

MySQL's existing unique constraints determine what counts as a duplicate. Existing rows are left as-is. A table without a relevant unique constraint can receive another copy on a later run. MySQL can also downgrade some other errors to warnings under `IGNORE`. Check the insert result and database warnings when rows are missing or changed by the server. [MySQL INSERT modifiers](https://dev.mysql.com/doc/refman/8.4/en/insert.html)

The workflow does not automatically retry the write. If the connection drops during the insert, check the target table before running again.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Weekly Google Sheets to MySQL workflow](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Googlesheets/0234_GoogleSheets_Cron_Create_Scheduled.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Zie619 / n8n-workflows.

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

This adaptation makes the original Monday default explicit, removes instance-specific configuration, and checks title and price before the insert.

</details>
