# Extract Data from a Webpage

Extract requested fields and a structured summary from a webpage.

<!-- template-actions:start -->
[![View in Open Flow](../../assets/view-in-openflow.svg)](https://openflow.run/templates/extract-data-from-a-webpage/) [![n8n JSON](../../assets/n8n-json.svg)](templates/extract-data-from-a-webpage.n8n.json)
<!-- template-actions:end -->

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

## Setup

Configure an AI model and deploy the Open Flow webhook. Restrict the webhook to trusted callers and deploy with network controls that prevent access to private or internal hosts.

## Behavior

POST JSON with `url` and optional `extract_fields` and `name`. Fields default to `price,features,description`. The workflow fetches the webpage, strips scripts, styles and HTML tags, and sends the first 4,000 characters of text to the model. It returns `title`, `description`, `extractedData`, `statistics` and `sentiment` as JSON. Page text is sent to the model and the result should be checked against the source. Failed or empty fetches do not produce an extraction.

<details>
<summary>In n8n</summary>

Import the n8n workflow, configure the model credential, and restrict the **Scrape URL** webhook to trusted callers.

</details>

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [DataForge Lite — Single URL AI Scraper](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/AI_Research_RAG_and_Data_Analysis/DataForge%20Lite%20-%20AI%20URL%20Data%20Extractor.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
