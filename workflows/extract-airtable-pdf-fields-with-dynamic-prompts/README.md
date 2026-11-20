# Extract Airtable PDF Fields with Dynamic Prompts

Extract Airtable field values from record PDFs using field descriptions as prompts.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/extract-airtable-pdf-fields-with-dynamic-prompts.n8n.json)
<!-- template-actions:end -->

## Setup

Configure an Airtable personal access token for schema, records and webhook management. Set your base, table and notification URL in **Set Airtable Vars** and run the manual registration flow once; it creates separate File-change and field-change webhooks. Airtable webhooks expire and must be refreshed before expiration. Protect incoming notifications using a private network or authenticated gateway.

The table needs a File attachment column and described output fields. Prevent overlapping runs and use one mode.

## Behavior

Notifications are read using the saved cursor and all available pages, then each changed table, field and record is matched to its own table schema. Field events process records with a File; record events process described fields whose values are falsy. Model answers may not satisfy the field type and require review. PDF contents and prompts are sent to the selected model provider; input size limits apply.

The cursor advances only after its events are handled. A write with an unknown outcome may have succeeded: inspect Airtable before clearing the pending record. Registration attempts have separate checkpoints; inspect Airtable before retrying an uncertain registration to avoid duplicate webhooks. Manage the existing webhook before clearing a completed registration checkpoint for a replacement. A successfully completed event and record is recorded to prevent duplicate writes on a cursor replay.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [AI Data Extraction with Dynamic Prompts and Airtable](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/OpenAI_and_LLMs/AI%20Data%20Extraction%20with%20Dynamic%20Prompts%20and%20Airtable.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
