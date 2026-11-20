# Render Branded Markdown PDF

Render Markdown as a branded PDF with a cover and numbered contents.

<!-- template-actions:start -->
[![View in Open Flow](../../assets/view-in-openflow.svg)](https://openflow.run/templates/render-branded-markdown-pdf/) [![n8n JSON](../../assets/n8n-json.svg)](templates/render-branded-markdown-pdf.n8n.json)
<!-- template-actions:end -->

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

## Setup

Set the branding and page settings in **Build cover and contents**. Bind PDFMINT_API_KEY as a secret Variable and deploy the Open Flow webhook. Install the PDFMint community node and configure its credential. Set the Open Flow URL in **Prepare document with Open Flow**, then activate the Open Flow frontend webhook. Restrict access to both webhooks.

## Behavior

POST JSON containing title and markdown, with optional author. The workflow checks quota, numbers headings outside fenced code blocks, creates a cover and contents, and returns a PDF in the same HTTP response. Invalid input or an unsuccessful render returns JSON. A lost response can follow a completed render; inspect service usage before retrying. Markdown is sent to PDFMint.

<details>
<summary>In n8n</summary>

Import the n8n workflow, install the PDFMint community node and configure its credential. For direct n8n mode configure branding and credentials in the original nodes and activate its separate webhook.

</details>

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

Add an n8n synchronous PDF frontend for Open Flow, and replace the example brand.

Adapted from [Convert Markdown into a branded PDF with a table of contents using PDFMint](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/PDF_and_Document_Processing/Convert%20Markdown%20into%20a%20branded%20PDF%20with%20a%20table%20of%20contents%20using%20PDFMint.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source states that its author builds PDFMint. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
