# Summarize Three Essays

Read the first three essay links from Paul Graham’s article index and summarize each page.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/summarize-three-essays.n8n.json)
<!-- template-actions:end -->

## Setup

Configure an AI model.

## Behavior

Fetch the index, take its first three nested-table links, fetch each essay and return its title, URL and summary. The workflow sends page content to the model. Summaries can differ and require review. Very large pages must fit workflow input and model limits.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

Use HTTPS, process essays independently and preserve each title and URL with its summary.

Adapted from [Scrape and summarize webpages with AI](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/AI_Research_RAG_and_Data_Analysis/Scrape%20and%20summarize%20webpages%20with%20AI.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
