# Make Social Event Banners for Discord

Generate an event poster from a prompt and share it as a Discord attachment.

<!-- template-actions:start -->
[![View in Open Flow](../../assets/view-in-openflow.svg)](https://openflow.run/templates/make-social-event-banners-for-discord/) [![n8n JSON](../../assets/n8n-json.svg)](templates/make-social-event-banners-for-discord.n8n.json)
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

## Changes to the source

Added hosted form intake, Run Artifact poster download, multipart Discord upload, configurable account settings, and write checkpoints.

Adapted from [Speed Up Social Media Banners With BannerBear.com](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/Instagram_Twitter_Social_Media/Speed%20Up%20Social%20Media%20Banners%20With%20BannerBear.com.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
