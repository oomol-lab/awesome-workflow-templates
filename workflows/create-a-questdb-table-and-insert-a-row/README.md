# Create a QuestDB Table and Insert a Row

Create a QuestDB table, insert a sample row, and read it back.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/create-a-questdb-table-and-insert-a-row.openflow.json) · [n8n JSON](templates/create-a-questdb-table-and-insert-a-row.n8n.json)

## Setup and use

Enable Basic Authentication on the QuestDB HTTP API and bind secret Variables QUESTDB_USER and QUESTDB_PASSWORD. Run with the QuestDB base URL. In n8n configure the QuestDB PostgreSQL connection and run manually. Use one format.

## Behavior

The workflow creates a table named test with id INT and name STRING, inserts the example row (0, Alex), then reads the table. It fails if test already exists. Both operations change the database; if a result is uncertain, inspect the table before retrying.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Use the QuestDB HTTP SQL API in Open Flow. Replace the n8n insert operation with explicit SQL and read the table afterwards.

Adapted from [Create a QuestDB table and insert a row](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Manual/0204_Manual_Questdb_Create_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
