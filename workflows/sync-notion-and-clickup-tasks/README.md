# Sync Notion and ClickUp Tasks

Synchronize Notion page details to ClickUp and ClickUp status changes back to Notion.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/sync-notion-and-clickup-tasks.n8n.json)
<!-- template-actions:end -->

## Setup and use

The Notion data source needs a rich text **ClickUp ID**, title **Task name**, select **Status** and date **Deadline**.

## Behavior

A changed Notion page updates the matching ClickUp task’s name, status and deadline when they differ. A ClickUp status event queries every matching Notion page by ClickUp ID and updates its Status select when it differs. Keep status names consistent and monitor both directions for repeated updates. Inspect both systems before retrying an uncertain write.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Notion and ClickUp task sync](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Clickup/0282_Clickup_Notion_Update_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
