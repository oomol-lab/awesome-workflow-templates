# Publish Notion Posts to LinkedIn

Format scheduled Notion posts, publish their images on LinkedIn and mark the matching page done.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/publish-notion-posts-to-linkedin.openflow.json) · [n8n JSON](templates/publish-notion-posts-to-linkedin.n8n.json)

## Setup

Connect Notion, LinkedIn and a text model. Configure the Notion data source, its Date and Status properties, and the LinkedIn personal URN. Enable persistent State. Import the n8n workflow, configure LinkedIn, a Data Table with text columns item_key and status, and the upload relay Header Auth credential. Enable **Binary upload relay**, disable the n8n schedule when using Open Flow, set the relay URL in **Upload image via n8n** and bind N8N_RELAY_TOKEN. For direct n8n mode configure the Notion database and LinkedIn account. Use only one format and prevent overlapping runs.

## Behavior

Daily at 15:00 UTC, read pages scheduled for that date and not marked Done. Read each page's direct text blocks and first image, format the text, publish the image post and update the same Notion page. Text is sent to the model; formatted text and images are sent to LinkedIn. Protect the relay and execution history, which can contain image URLs. The model can alter meaning; review source material and outputs.

If a publish or status update has an unknown result, inspect LinkedIn or Notion. Enter its pending key in **Resolve prior post**, set resolution to confirmed or absent, rerun, and clear the fields. In n8n inspect the pending-post or pending-status Data Table row. Complete a missing status update manually and mark the row done; delete a pending-post row only after confirming no post was created.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

Process pages individually, replace the private assistant, skip completed pages and checkpoint publication and status updates.

Adapted from [Automate LinkedIn Outreach with Notion and OpenAI](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/Notion/Automate%20LinkedIn%20Outreach%20with%20Notion%20and%20OpenAI.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
