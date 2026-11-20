# Route Matching Gmail PDFs to Drive

Classify PDF attachments from Gmail by their content and upload matching files to Google Drive.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/route-matching-gmail-pdfs-to-drive.n8n.json)
<!-- template-actions:end -->

## Behavior

The workflow polls Gmail every minute, iterates attachments, extracts PDF text, and classifies it using the configured term, filename and text. Matching original PDFs are uploaded to the configured Drive folder; non-PDF and nonmatching files are skipped. PDFs above the source's text-length limit are skipped. PDF contents are shared with the model. Neither webhook authenticates callers; restrict access to trusted senders. A lost Drive response may represent a completed upload; inspect the destination before retrying.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Send specific PDF attachments from Gmail to Google Drive using OpenAI](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/Gmail_and_Email_Automation/Send%20specific%20PDF%20attachments%20from%20Gmail%20to%20Google%20Drive%20using%20OpenAI.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source credits [David Sha](https://davidsha.me). See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
