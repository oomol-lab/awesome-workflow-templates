# Extract Drive Statements to CSV

Extract and categorize statement transactions from new PDFs or images into Drive CSV files.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/extract-drive-statements-to-csv.n8n.json)
<!-- template-actions:end -->

## Setup and use

Use separate Google Drive input and output folders. Configure Google Drive, OpenAI and Gemini connections.

The workflow processes each new PDF or PNG, JPEG, WebP, HEIC or HEIF image, extracts transaction rows and a category column, validates the CSV, and uploads a CSV file. PDF text extraction requires selectable text. Review results against the original statement; model output can omit or misread transactions. Statement content is sent to the configured model, and images are temporarily uploaded to Gemini Files. Other image formats stop with an explicit error. An uncertain upload leaves a pending file ID; inspect the output folder before clearing the checkpoint and retrying. Avoid overlapping runs.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Extract text from PDF and image using Vertex AI (Gemini) into CSV](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/PDF_and_Document_Processing/Extract%20text%20from%20PDF%20and%20image%20using%20Vertex%20AI%20(Gemini)%20into%20CSV.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

Changes: update retired models, remove the download-once behavior, process each source file independently, validate CSV and guard uncertain uploads.

Collection license notice:

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
