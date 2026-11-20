# Capture Job Applications

Receive application details and save a CV link for human review.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/capture-job-applications.n8n.json)
<!-- template-actions:end -->

## Setup and use

Set the Drive folder, Airtable base and table. Create Airtable columns Name, Email address, Phone, CV Link and Applied On as text, and Years of experience as a number. Customize the form job description.

## Behavior

Each submission uploads the PDF and records the supplied details and Drive link. People review applications; this component does not score or shortlist candidates. Personal data and CVs are stored in Drive and Airtable. Avoid overlapping runs and inspect the destination before clearing a pending checkpoint after an uncertain write.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [HR Job Posting and Evaluation with AI](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/HR_and_Recruitment/HR%20Job%20Posting%20and%20Evaluation%20with%20AI.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

Changes from source: Isolate form intake, remove automated scoring and hiring decisions, add Open Flow relay and write checkpoints, and preserve phone numbers as text.

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
