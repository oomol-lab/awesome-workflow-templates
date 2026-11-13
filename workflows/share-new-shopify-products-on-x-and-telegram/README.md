# Share New Shopify Products on X and Telegram

Announce a new Shopify product on X and in a Telegram chat.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/share-new-shopify-products-on-x-and-telegram.openflow.json) · [n8n JSON](templates/share-new-shopify-products-on-x-and-telegram.n8n.json)

## Setup

Connect X and Telegram, and replace `@YOUR_TELEGRAM_CHANNEL` with your Telegram chat ID or channel username. Deploy the Open Flow webhook and register it for Shopify's products/create topic with the full product payload. In n8n connect Shopify, X and Telegram, and replace `@YOUR_TELEGRAM_CHANNEL` with your Telegram chat ID or channel username. Use one workflow format.

## Behavior

Each new product supplies the vendor, title and product type for two announcements. The webhook does not verify the sender; restrict access appropriately. Its acknowledgment confirms receipt, not delivery to either service. Each message is a separate external write, so check both destinations before retrying a failed or uncertain run. Execution history can include product data.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Register the Shopify webhook separately for Open Flow.

Adapted from [Announce new Shopify products on X and Telegram](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Shopify/0085_Shopify_Twitter_Create_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
