# Extract Baserow PDF Fields with Dynamic Prompts

Extract Baserow field values from row PDFs using field descriptions as prompts.

<!-- template-actions:start -->
[![View in Open Flow](../../assets/view-in-openflow.svg)](https://openflow.run/templates/extract-baserow-pdf-fields-with-dynamic-prompts/) [![n8n JSON](../../assets/n8n-json.svg)](templates/extract-baserow-pdf-fields-with-dynamic-prompts.n8n.json)
<!-- template-actions:end -->

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

## Setup

Configure Baserow Header Auth with a token allowed to read schema and rows and update the target table. Create a Baserow webhook for rows.updated (only the File field), field.created and field.updated, using field names. The table needs a File column containing PDFs and described fields containing extraction prompts. Protect the incoming webhook and restrict access to trusted senders.

Choose direct or relay in both **Choose mode** nodes. Prevent overlapping runs and use one mode.

## Behavior

For a row update, read each affected row and extract each described field whose current value is falsy. For a described field creation or change, extract that field for each row with a PDF. This branch reads at most three pages of 20 rows, as configured in the source. Only the first PDF in File is used. The field-event row query includes File so it can fetch the PDF. Text must fit the workflow input limit. Model answers are not guaranteed to match Baserow field types and require review.

An uncertain row update may have succeeded. Inspect that row and reconcile it before retrying. Open Flow stores a pending key baserow-pdf:TABLE_ID:ROW_ID. Remove a pending record only after confirming the update did not occur. PDF contents and prompts are sent to the selected model provider.

<details>
<summary>In n8n</summary>

Import the n8n workflow and configure Baserow Header Auth with a token allowed to read schema and rows and update the target table. In direct mode configure the OpenAI model and Data Table with item_key and status columns. In relay mode deploy Open Flow, configure its model, bind BASEROW_AUTHORIZATION to a secret containing the word Token, a space, and then by the Baserow token, enable persistent State, set the Open Flow URL and authentication in the n8n forwarding nodes, and restrict the Open Flow webhook using a private network or an authenticated gateway; the workflow itself does not authenticate callers. PDFs are downloaded and parsed in n8n. N8n marks its Data Table attempt complete only after receiving a matching row ID.

In relay mode their text, table and row IDs and field prompts go to Open Flow, which generates values and updates that same row.

</details>

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [AI Data Extraction with Dynamic Prompts and Baserow](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/OpenAI_and_LLMs/AI%20Data%20Extraction%20with%20Dynamic%20Prompts%20and%20Baserow.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
