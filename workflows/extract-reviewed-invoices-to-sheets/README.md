# Extract Reviewed Invoices to Google Sheets

Extract and review emailed PDF invoices in Cradl AI, then record invoice lines in Google Sheets.

<!-- template-actions:start -->
[![View in Open Flow](../../assets/view-in-openflow.svg)](https://openflow.run/templates/extract-reviewed-invoices-to-sheets/) [![n8n JSON](../../assets/n8n-json.svg)](templates/extract-reviewed-invoices-to-sheets.n8n.json)
<!-- template-actions:end -->

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

## Setup and use

Connect Gmail, Google Sheets and a Cradl AI account with an invoice agent. Configure human review in Cradl AI. Configure the Open Flow webhook URL in the relay and protect it with an authenticated gateway or private network. Connect the same Gmail account and your sheet in Open Flow and enable persistent State.

Create an Invoices sheet with columns message ID, filename, line number and line JSON. The relay processes attachments sequentially; after each review Open Flow appends the invoice lines and marks the email read only after the final PDF. A pending spreadsheet or Gmail write requires inspection before clearing its checkpoint. The Gmail filter selects unread messages with invoice in the subject and PDF attachments. Avoid overlapping runs. Email attachments and extracted invoice data are sent to Cradl AI.

<details>
<summary>In n8n</summary>

Install its n8n community node and connect its OAuth credential; use the bundled n8n workflow for Gmail intake, PDF attachments and Cradl's authenticated completion callback. In n8n select Open Flow mode for the relay; for standalone n8n set the mode to false, connect Google Sheets and select a Data Table with item_key and status columns.

</details>

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Invoice data extraction with human-in-the-loop validation and auto-training using Cradl AI](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/PDF_and_Document_Processing/Invoice%20data%20extraction%20with%20human-in-the-loop%20validation%20and%20auto-training%20using%20Cradl%20AI.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.



Original workflow by Cradl AI. Process each PDF separately and mark mail read after successful exports.

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
