# Analyze Trading Chart Images

Analyze a submitted market chart image and return a plain-language explanation.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/analyze-trading-chart-images.openflow.json) · [n8n JSON](templates/analyze-trading-chart-images.n8n.json)

## Setup and use

Import the n8n workflow, connect OpenAI for direct use, and configure a Header Auth credential on **Open Flow chart frontend** for Open Flow mode. Deploy the Open Flow webhook, bind OPENAI_API_KEY from the same account as the n8n upload credential, and set the URL in **Analyze chart with Open Flow**. Configure a Data Table with item_key and status text columns for upload checkpoints. Use one entry point and restrict access. The source does not include the Chrome extension.

POST a chart image as multipart form-data in the **data** file field, or as a raw image body. For Open Flow mode send a unique **X-Request-ID** header for each image and reuse it only when checking an uncertain attempt; prevent overlapping requests with the same ID. The n8n frontend uploads the image to OpenAI Files with purpose vision, passes its file ID to Open Flow for visual analysis, and returns synchronous text. Uploaded files remain in the OpenAI account according to its retention settings. If upload or analysis completion is uncertain, inspect the account and execution before resolving the pending Data Table row.

## Behavior

The model describes a stock or cryptocurrency chart and possible direction in plain language. The image is sent to OpenAI. Analysis can be incorrect or omit important context; it is not binding financial advice. Review it before making trading decisions.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Analyze tradingview.com charts with Chrome extension, N8N and OpenAI](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/AI_Research_RAG_and_Data_Analysis/Analyze%20tradingview.com%20charts%20with%20Chrome%20extension%2C%20N8N%20and%20OpenAI.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
