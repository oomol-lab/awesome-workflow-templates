# Delete n8n Executions Older Than Ten Days

Delete n8n execution records older than ten days on a schedule or manually.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/delete-n8n-executions-older-than-ten-days.openflow.json) · [n8n JSON](templates/delete-n8n-executions-older-than-ten-days.n8n.json)

## Setup and use

Set your n8n HTTPS base URL in Select execution page and Select old execution, and bind an API key with execution list and deletion permissions as secret Variable N8N_API_KEY in both HTTP nodes. The schedule defaults to 04:44 UTC; set the timezone to your n8n instance timezone. In n8n configure the n8n credential. Use one format.

## Behavior

The workflow collects execution IDs from every page, then permanently deletes those started over ten days ago. Manual and scheduled runs both delete records. If a delete outcome is unknown, inspect the execution in n8n before retrying.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Open Flow collects pages before deletion and uses the n8n REST API to list and delete executions.

Adapted from [Delete n8n executions older than ten days](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Manual/0662_Manual_Schedule_Automation_Scheduled.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
