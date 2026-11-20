# Extract Invoices with LlamaParse

Parse emailed invoice PDFs and record structured invoice details in Google Sheets.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/extract-invoices-with-llamaparse.n8n.json)
<!-- template-actions:end -->

## Setup and use

Connect Gmail, Google Sheets, an AI model and LlamaCloud. Set LLAMA_AUTHORIZATION to the full Bearer token and bind it to both LlamaParse HTTP nodes. Use an invoice-synced label and configure the Gmail search to exclude that label. Run one mode at a time and avoid overlapping runs.

LlamaParse processes the PDF asynchronously; the workflow polls for completed Markdown, extracts invoice fields, appends JSON to the sheet and labels the original email. Check AI results against the invoice. If a job, sheet append or label operation has an uncertain result, inspect the service before clearing the corresponding pending state.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Invoice data extraction with LlamaParse and OpenAI](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/PDF_and_Document_Processing/Invoice%20data%20extraction%20with%20LlamaParse%20and%20OpenAI.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

Original n8n tutorial: https://blog.n8n.io/how-to-extract-data-from-pdf-to-excel-spreadsheet-advance-parsing-with-n8n-io-and-llamaparse/. Changes: use current LlamaParse v2 and a current model, and guard external writes.

```text
Creative Commons Attribution 4.0 International License

Copyright (c) 2024-2026 Enes Cingoz

You are free to:

  Share - copy and redistribute the material in any medium or format
  Adapt - remix, transform, and build upon the material for any purpose,
  even commercially.

Under the following terms:

  Attribution - You must give appropriate credit, provide a link to the
  license, and indicate if changes were made. You may do so in any
  reasonable manner, but not in any way that suggests the licensor
  endorses you or your use.

  No additional restrictions - You may not apply legal terms or
  technological measures that legally restrict others from doing
  anything the license permits.

Notices:

  You do not have to comply with the license for elements of the
  material in the public domain or where your use is permitted by an
  applicable exception or limitation.

  No warranties are given. The license may not give you all of the
  permissions necessary for your intended use. For example, other rights
  such as publicity, privacy, or moral rights may limit how you use the
  material.

For the full license text, see:
https://creativecommons.org/licenses/by/4.0/legalcode
```

</details>
