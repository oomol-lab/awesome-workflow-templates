# Summarize YouTube Videos on Discord

Summarize a channel’s new video captions and post the video to Discord.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/summarize-youtube-videos-on-discord.n8n.json)
<!-- template-actions:end -->

## Setup

Set the RSS feed channel ID. Configure YouTube OAuth with the owner of that channel; caption download requires appropriate access. Use one mode and avoid overlapping runs.

## Behavior

Every minute, the RSS feed checks for new channel videos. The first English caption track is downloaded and converted to text, summarized in three bullets and posted with that video’s title and link. Videos without an English track produce no post. Transcripts are sent to the model. Verify generated summaries.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Share YouTube Videos with AI Summaries on Discord](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/Discord/Share%20YouTube%20Videos%20with%20AI%20Summaries%20on%20Discord.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
