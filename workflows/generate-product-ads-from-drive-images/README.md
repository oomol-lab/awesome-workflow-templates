# Generate Product Ads from Drive Images

Analyze product images and ad examples, then generate and save image ads.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/generate-product-ads-from-drive-images.n8n.json)
<!-- template-actions:end -->

## Setup

Configure the style-example, product-image and output folder IDs. Bind OPENAI_API_KEY and N8N_RELAY_TOKEN as secrets and connect Google Drive. The two input folders should contain images.

## Behavior

The workflow analyzes every style example with every product image, creates ten square ad prompts per pair and saves generated PNGs in Drive. It passes image data and descriptions to OpenAI. The original wait defaults to **15 hours before each image**; adjust the delay in the format you use if a different interval is intended. Generated ads may not accurately reproduce a product and need human review.

Use a unique run ID for each batch. Generation and Drive uploads are reserved separately. A generated image is kept only for the current execution; after an interruption inspect the pending state before deciding how to finish the item. A timeout can occur after a provider has completed an action.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [AI product Images](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/AI%20product%20imagines.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
