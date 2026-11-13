# Update Rank Math SEO Metadata

Update a WordPress post’s Rank Math SEO title, description and canonical URL.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/update-rank-math-seo-metadata.openflow.json) · [n8n JSON](templates/update-rank-math-seo-metadata.n8n.json)

## Setup and use

Install and enable Rank Math and [Rank Math API Manager](https://github.com/Devora-AS/rank-math-api-manager). Configure a WordPress user with permission to edit the target post and an application password. In Open Flow replace the example HTTPS URL with your site's endpoint and bind secret Variables **WORDPRESS_USERNAME** and **WORDPRESS_APP_PASSWORD**. In n8n set the site URL in **Settings** and connect the WordPress credential. Edit the post ID and SEO fields in the HTTP node before running manually.

## Behavior

The sample updates post ID 246 with a demo SEO title, description and canonical URL. Verify the destination and values before running. If the result is unknown, inspect the post before retrying; the update may already have occurred. The example endpoint and values do not identify a real site.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Use the endpoint provided by Rank Math API Manager and avoid automatic retry of an uncertain write.

Adapted from [Update Rank Math metadata](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Manual/0713_Manual_HTTP_Update_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
