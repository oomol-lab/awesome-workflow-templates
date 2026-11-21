# Generate an Event Banner for Discord

Generate an event poster from a prompt and share it as a Discord attachment.

<!-- template-actions:start -->
[![View in Open Flow](../../assets/view-in-openflow.svg)](https://openflow.run/templates/generate-event-banner-for-discord/) [![n8n JSON](../../assets/n8n-json.svg)](templates/generate-event-banner-for-discord.n8n.json)
<!-- template-actions:end -->

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

## Setup

Connect OpenAI, Cloudinary and Bannerbear. Create a Bannerbear template with layers named `placeholder_image`, `placeholder_text`, `placeholder_location` and `placeholder_date`, and set your Bannerbear template IDs and Discord channel ID in **Choose banner step**. Bind `DISCORD_BOT_AUTH` as a secret variable (for example `Bot YOUR_DISCORD_BOT_TOKEN`), enable persistent State, and publish the workflow. Open the hosted Webhook form URL to submit event details.

## Behavior

The workflow generates an image, uploads it to Cloudinary, renders the event details in Bannerbear, downloads the rendered poster as a Run Artifact, and posts it to Discord as a multipart file attachment. Image generation and rendering may take time. Open Flow uses the synchronous endpoint.

If an external write has an unknown result, inspect the corresponding service. In **Choose banner step**, enter the pending key and resolution `confirmed` or `absent`. For a confirmed image generation, upload or render, enter its resulting HTTPS URL; then rerun with the same submission ID and details and clear the fields.

<details>
<summary>In n8n</summary>

Import the n8n workflow and configure the form's two template IDs, Cloudinary account and upload preset, Bannerbear and Discord. Select one Data Table with `item_key` and `status` text columns on all checkpoint nodes. If a pending row remains, inspect the affected service and complete any remaining actions manually before marking it `done`.

The source n8n workflow polls the asynchronous Bannerbear job.

</details>

<details>
<summary>Inspiration &amp; credits</summary>

Added hosted form intake, Run Artifact poster download, multipart Discord upload, configurable account settings, and write checkpoints.

Adapted from [Generate and share an event banner](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Bannerbear/0525_Bannerbear_Discord_Create_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
