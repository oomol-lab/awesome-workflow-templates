# Extract Products from Page Screenshots

Read page URLs from Google Sheets, extract product details from screenshots and append the results.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/extract-products-from-page-screenshots.n8n.json)
<!-- template-actions:end -->

## Setup and use

Create a spreadsheet with **List of URLs** column A headed url and **Results** columns page URL, product title, price, brand, promotion and percentage.

Configure the ScrapingBee query-auth credential with key name api_key for both screenshot and HTML fallback requests, including the embedded tool workflow, and configure Gemini.

## Behavior

Each URL is rendered as a full-page ScrapingBee screenshot. The Gemini agent extracts product title, price, brand and promotion details, and can request the page HTML as Markdown when the image is incomplete. Page data is shared with ScrapingBee and Gemini. A lost Sheets append response may represent written rows; inspect the sheet before retrying.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Vision-Based AI Agent Scraper - with Google Sheets, ScrapingBee, and Gemini](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/Google_Drive_and_Google_Sheets/%E2%9C%A8%20Vision-Based%20AI%20Agent%20Scraper%20-%20with%20Google%20Sheets%2C%20ScrapingBee%2C%20and%20Gemini.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
