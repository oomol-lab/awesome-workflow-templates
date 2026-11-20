# Route Matching Gmail PDFs to Drive

Classify PDF attachments from Gmail by their content and upload matching files to Google Drive.

<!-- template-actions:start -->
[![View in Open Flow](../../assets/view-in-openflow.svg)](https://openflow.run/templates/route-matching-gmail-pdfs-to-drive/) [![n8n JSON](../../assets/n8n-json.svg)](templates/route-matching-gmail-pdfs-to-drive.n8n.json)
<!-- template-actions:end -->

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

## Setup

Connect Gmail, Encodian, Gemini and Google Drive. Set the destination folder ID in **Choose the next attachment** and the matching term in **Prepare PDF classification**. Configure Gmail file transit and replace the example hostname in **Verify complete attachment** with your transit hostname. Enable persistent State.

## Behavior

The workflow polls Gmail every minute, downloads each PDF attachment, extracts its text layer via Encodian, classifies it with Gemini, and uploads matching original PDFs to Google Drive. Non-PDF attachments are skipped.

<details>
<summary>In n8n</summary>

Import the n8n workflow, connect Gmail, OpenAI and Google Drive, set the matching term and Drive folder ID in **Configure**, and activate the trigger.

</details>

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Send specific PDF attachments from Gmail to Google Drive using OpenAI](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/Gmail_and_Email_Automation/Send%20specific%20PDF%20attachments%20from%20Gmail%20to%20Google%20Drive%20using%20OpenAI.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source credits [David Sha](https://davidsha.me). See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
