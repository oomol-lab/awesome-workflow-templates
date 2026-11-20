# Email MediaMarkt Deals by Category

Find MediaMarkt Spain deals in selected categories and email the source links.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/email-mediamarkt-deals-by-category.n8n.json)
<!-- template-actions:end -->

## Setup

Configure a Bright Data Web Unlocker zone and API token, and connect an AI model.

## Behavior

A form collects categories and an email address. Bright Data retrieves the MediaMarkt Spain offers page; the model extracts matching products. Only MediaMarkt paths, product names and price strings that appear in the returned page are included, and links use the MediaMarkt domain. The checks do not prove that a price belongs to a product. If none can be verified, the message says so. Prices and availability can change, and model output may be incomplete or inaccurate; check each offer on the retailer's site. The page and form details may appear in execution history. Code inputs and outputs must each fit 1 MiB.

<details>
<summary>Inspiration &amp; credits</summary>

Replace community nodes with native requests, verify links and fix the source’s incorrect retailer domain.

Adapted from [Top deals by category](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Form/0805_Form_Html_Create_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
