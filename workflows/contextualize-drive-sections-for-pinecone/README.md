# Contextualize Drive Sections for Pinecone

Add whole-document context to each Google Doc section and index its embedding in Pinecone.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/contextualize-drive-sections-for-pinecone.n8n.json)
<!-- template-actions:end -->

## Setup and use

Connect Google Drive, Gemini and Pinecone and configure its OpenRouter credentials and model. Use a Pinecone index with 3072 dimensions and the default namespace. Use the same index and embedding model when querying.

## Behavior

Run the workflow manually. The Google Doc is exported as text and split at the source's explicit SECTIONEND separator. For each section the workflow asks OpenRouter to place it in the context of the full document, embeds the resulting context plus section, and stores a vector with the combined text. Each section must fit the selected model's input limits and the full document must fit the context model and workflow limits. Gemini 001 output is configured for 3072 dimensions; create a matching index and re-embed documents when changing models.

Pinecone inserts use new IDs on each run. If a write response is lost, inspect the index before retrying because a vector may already exist.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [RAG_Context-Aware Chunking _ Google Drive to Pinecone via OpenRouter & Gemini](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/Google_Drive_and_Google_Sheets/RAG_Context-Aware%20Chunking%20_%20Google%20Drive%20to%20Pinecone%20via%20OpenRouter%20%26%20Gemini.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
