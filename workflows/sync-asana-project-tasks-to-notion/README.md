# Sync Asana Project Tasks to Notion

Create or update the matching Notion page when a task changes in the configured Asana project.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/sync-asana-project-tasks-to-notion.n8n.json)
<!-- template-actions:end -->

## Setup

1. In **Set the project and data source**, set your Asana project GID and Notion data source ID. Connect the Asana API access token in **Read the exact Asana task** and a Notion API integration in both Notion request nodes. Share the data source with the integration.
2. In Notion, use a title property named `Task`, a date property named `Deadline` and a text property named `Asana GID`. If the old property was a number, rename it and create the new text property. Fill it with the exact GID from Asana for each matched page before enabling sync. When an old number may have rounded or is ambiguous, look up the task in Asana before filling it.
3. On your self-hosted n8n deployment, allow `NODE_FUNCTION_ALLOW_BUILTIN=crypto` in the Code task runner. Use a trusted instance that allows workflow access to the signing secret. Leave `ASANA_WEBHOOK_SECRET` unset during registration, or set your external secret expression in **Verify the raw Asana request**.
4. Activate the workflow and register the production HTTPS webhook as the target of `POST https://app.asana.com/api/1.0/webhooks`. Use your authorized Asana credential and send the following JSON with your real project GID and endpoint. The workflow can echo the registration challenge while the signing secret is unset. [Asana webhook handshake](https://developers.asana.com/docs/webhooks-guide#the-webhook-handshake)

```json
{"data":{"resource":"YOUR_ASANA_PROJECT_GID","target":"YOUR_N8N_PRODUCTION_WEBHOOK_URL"}}
```

5. Set `ASANA_WEBHOOK_SECRET` from `X-Hook-Secret` in the authenticated Asana creation response and reload your deployment configuration. Keep the webhook URL unchanged. A handshake never saves a secret or writes to Notion. Subsequent deliveries must carry the matching Asana signature.

## Behavior

The workflow acknowledges valid deliveries promptly. It handles each distinct task GID once per delivery and reads its current Asana title and due date. It processes tasks currently in the configured project. Deleted, removed and unavailable tasks are skipped. It does not delete Notion pages.

For each task, it queries the configured Notion data source by its exact text GID. One matching page is updated, and a task with no match creates a page. A duplicate or mismatched Notion match stops the run. The workflow clears the Notion deadline when Asana returns an explicitly empty due date. [Get an Asana task](https://developers.asana.com/reference/gettask) · [Query a Notion data source](https://developers.notion.com/reference/query-a-data-source)

Run deliveries serially to reduce races during create. Asana webhooks are notifications, so a delivery may contain several changes or arrive after a later change. The workflow always reads the current task. An error can leave earlier tasks already synced. Check the affected Notion page after an unconfirmed write before processing the task again. The template adds no write retries and disables saving execution data.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

Verify the original Asana request bytes. Match Notion pages by an exact text GID instead of row order or a numeric conversion. Derive both the title and the optional deadline from the same task.

Adapted from [Asana tasks synchronized to Notion](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Asana/0241_Asana_Notion_Create_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Zie619 / n8n-workflows.

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
