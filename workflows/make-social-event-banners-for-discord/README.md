# Make Social Event Banners for Discord

Generate an event poster from a prompt and share it as a Discord attachment.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/make-social-event-banners-for-discord.n8n.json)
<!-- template-actions:end -->

## Setup

Connect OpenAI, Cloudinary and Bannerbear. Create a Bannerbear template with layers named placeholder_image, placeholder_text, placeholder_location and placeholder_date.

## Behavior

The workflow generates an image, uploads it to Cloudinary, renders the event details in Bannerbear, and sends the poster as a Discord file. Image generation and rendering may take time.

If an external write has an unknown result, inspect the corresponding service. In **Choose banner step**, enter the pending key and resolution confirmed or absent. For a confirmed image generation, upload or render enter its resulting HTTPS URL; then rerun with the same submission ID and details and clear the fields.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

Added an authenticated Discord attachment relay, configurable account settings, and write checkpoints.

Adapted from [Speed Up Social Media Banners With BannerBear.com](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/Instagram_Twitter_Social_Media/Speed%20Up%20Social%20Media%20Banners%20With%20BannerBear.com.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
