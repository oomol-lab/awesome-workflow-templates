# Parse Drive Invoices to Airtable

Parse new PDF invoices and save linked invoice and line item records in Airtable.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/parse-drive-invoices-to-airtable.n8n.json)
<!-- template-actions:end -->

## Setup and use

Connect Google Drive, Airtable and a model. Configure the watched folder, Airtable base and two tables. In Invoices create a Name text field; in Line Items create Description, Qty, Unit price, Amount and an Invoices linked-record field.

Each new PDF is uploaded and parsed by LlamaParse. The model extracts its line items; the workflow creates one invoice record and a linked record for each line. Verify AI output against the PDF. State keeps the parse job, parent ID and completed line index; inspect LlamaCloud or Airtable before clearing a pending checkpoint. Avoid overlapping runs.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Parse PDF with LlamaParse and save to Airtable](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/PDF_and_Document_Processing/Parse%20PDF%20with%20LlamaParse%20and%20save%20to%20Airtable.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source identifies Mark Shcherbakov / 5minAI; it does not state a separate template license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

Original workflow by Mark Shcherbakov / 5minAI. Changes: use LlamaParse v2 polling, current model and persistent write recovery; process each file independently.

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
