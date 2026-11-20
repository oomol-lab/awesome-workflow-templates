# Analyze CV and Record Candidate

Extract CV details for human review and record them in Google Sheets.

<!-- template-actions:start -->
[![View in Open Flow](../../assets/view-in-openflow.svg)](https://openflow.run/templates/analyze-cv-and-record-candidate/) [![n8n JSON](../../assets/n8n-json.svg)](templates/analyze-cv-and-record-candidate.n8n.json)
<!-- template-actions:end -->

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

## Setup and use

Import the n8n workflow to host the PDF form, extract text and upload the original CV to Google Drive. Configure its Drive folder and a Data Table with item_key and status text columns; for relay mode also set the Open Flow webhook URL. In n8n set the relay boolean in Choose mode to true for Open Flow or false for direct mode; in relay mode configure a model, spreadsheet and persistent State in Open Flow. For direct mode configure the n8n model and Sheets connection. Create sheet columns Date, Name, Email, Phone, City, Birthdate, Education, Job History, Skills, Summary in that order. Limit access to the webhook and candidate records. The webhook has no built-in caller authentication; restrict it with a trusted gateway or private network.

## Behavior

The form accepts a PDF and saves the original. Relay mode sends extracted text to Open Flow; direct mode analyzes and appends in n8n.  Human review is needed: AI output can be inaccurate and should not determine hiring decisions on its own. CVs and extracted personal data are sent to the configured services. Inspect Drive or Sheets before clearing pending checkpoints after an uncertain write; avoid overlapping executions.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [AI Automated HR Workflow for CV Analysis and Candidate Evaluation](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/OpenAI_and_LLMs/AI%20Automated%20HR%20Workflow%20for%20CV%20Analysis%20and%20Candidate%20Evaluation.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.



Changes from source: Fix the form name and candidate field mappings, consolidate factual extraction and summary, remove automated candidate scoring, update the model and add an Open Flow relay with write checkpoints.

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
