# Review CV for a Full-Stack Role

Collect PDF resumes, summarize candidate information, and record a role-fit assessment for human review.

<!-- template-actions:start -->
[![View in Open Flow](../../assets/view-in-openflow.svg)](https://openflow.run/templates/review-cv-for-full-stack-role/) [![n8n JSON](../../assets/n8n-json.svg)](templates/review-cv-for-full-stack-role.n8n.json)
<!-- template-actions:end -->

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

## Setup

Connect Google Drive and configure **Upload CV** with a destination folder. The form accepts a name, email and PDF. Configure a Google Sheet with columns DATA, NAME, PHONE, CITY, EMAIL, DATA NASCITA, EDUCATIONAL, JOB HISTORY, SKILLS, SUMMARIZE, VOTE and CONSIDERATION in that order. Prevent overlapping executions.

Configure **Forward application to Open Flow** with the deployed webhook URL, connect Google Sheets, select an AI model, and set the spreadsheet ID and range in **Prepare candidate row**. Restrict access to the Open Flow webhook at the deployment boundary; it has no built-in authentication. Enable persistent State.

## Behavior

Each submission stores the original PDF in Drive, extracts readable text, summarizes education, work history and skills, and compares the resume with the configurable job profile. The resulting candidate details, summary, suggested 1–10 score and explanation are appended to the sheet. Review the result and make hiring decisions with human judgment; the model can omit or misinterpret details. The PDF must contain extractable text; scanned images need OCR. In Open Flow, the extracted text and its enclosing data must fit the host’s 1 MiB limit for each Code input and output. Personal data and resume text are sent to the configured model and stored in Drive, Sheets and execution histories. Protect access and apply your retention rules.

If Drive upload or forwarding is uncertain, inspect Drive and the downstream execution before replaying. If the Open Flow sheet append is uncertain, inspect the sheet, replay the same submission with the pending key in **Prepare candidate row** and resolution confirmed if appended or absent if not, then clear both fields.

<details>
<summary>In n8n</summary>

Import the n8n workflow, connect Google Drive and configure **Upload CV** with a destination folder. Select a Data Table with text columns item_key and status in all checkpoint nodes. For Open Flow, set **Choose processing mode** to relay, configure **Forward application to Open Flow** with the deployed webhook URL, connect Google Sheets, select an AI model, and set the spreadsheet ID and range in **Prepare candidate row**. For direct n8n, leave processing mode as direct and connect OpenAI and Google Sheets. In n8n, inspect the pending Data Table row, complete any missing work manually, then mark it done; delete it only if no external write occurred.

</details>

<details>
<summary>Inspiration &amp; credits</summary>

Add a form/PDF relay and write checkpoints; replace private destinations and repair the form name and phone column mapping.

Adapted from [HR-focused automation pipeline with AI](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Extractfromfile/1981_Extractfromfile_Form_Automate_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

The collection’s [MIT notice](https://github.com/Zie619/n8n-workflows/blob/94007c1445d9258a7da116646b79473e7c7c3282/LICENSE) is pinned at a later revision. This is the collection notice at that revision; it does not establish a separate original template author's license. Our changes are listed above; see [repository licensing](../../README.md#licensing).

> MIT License
>
> Copyright (c) 2025 Zie619
>
> Permission is hereby granted, free of charge, to any person obtaining a copy
> of this software and associated documentation files (the "Software"), to deal
> in the Software without restriction, including without limitation the rights
> to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
> copies of the Software, and to permit persons to whom the Software is
> furnished to do so, subject to the following conditions:
>
> The above copyright notice and this permission notice shall be included in all
> copies or substantial portions of the Software.
>
> THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
> IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
> FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
> AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
> LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
> OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
> SOFTWARE.

</details>
