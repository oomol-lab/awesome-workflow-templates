# Sync Notion and ClickUp Tasks

Synchronize Notion page details to ClickUp and ClickUp status changes back to Notion.

<!-- template-actions:start -->
[![View in Open Flow](../../assets/view-in-openflow.svg)](https://openflow.run/templates/sync-notion-and-clickup-tasks/) [![n8n JSON](../../assets/n8n-json.svg)](templates/sync-notion-and-clickup-tasks.n8n.json)
<!-- template-actions:end -->

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

## Setup

Connect Notion in **Watch Notion tasks**, **Find Notion pages**, and **Update Notion status**, and set **databaseId** in **Watch Notion tasks** and **dataSourceId** in **Find Notion pages**. Connect ClickUp in **Receive ClickUp status event**, **Read ClickUp task**, and **Update ClickUp task**, and set **workspaceId** (and optional **listId**) in **Receive ClickUp status event**.

## Behavior

Two independent triggers keep Notion and ClickUp in sync: **Watch Notion tasks** polls for updated Notion pages and updates matching ClickUp tasks when name, status, or deadline differ, while **Receive ClickUp status event** listens for `taskStatusUpdated` webhooks and updates matching Notion pages.

<details>
<summary>In n8n</summary>

Import the n8n workflow, connect Notion and ClickUp credentials, and configure the target Notion database and ClickUp team/workspace.

</details>

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
