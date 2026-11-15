# Email Quiz Certificates from Slides

Create and email a personalized PDF certificate for each passing quiz response.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/email-quiz-certificates-from-slides.openflow.json) · [n8n JSON](templates/email-quiz-certificates-from-slides.n8n.json)

## Setup

Configure a Google Sheets form-response tab with unique Submission ID, Name, Email and numeric Score columns. Each response must have a unique immutable Submission ID. The template must contain [ NAME ] on page object ID p, and the destination Drive folder must exist. Configure the n8n trigger, Drive, Slides, Gmail and a private Data Table with item_key, status and payload text columns. In Open Flow mode set mode to relay in Prepare response, configure the webhook and Header Auth, bind CERTIFICATE_RELAY_AUTH to that Authorization header, connect Drive and Slides, select the Gmail connection for the Email certificate Code node, and enable persistent State. Configure Header Auth on Resume submission. Enter the template and folder IDs in Choose certificate step. Prevent concurrent handling of the same submission.

A score strictly greater than 3 creates a copy of the Slides template, replaces [ NAME ] on page p, exports that copy as PDF and sends it to the respondent. Scores of 3 or less do not create or send a certificate. The Gmail connector fetches the temporary PDF transit URL; it must be accessible to the connector, and attachments have a 25 MB decoded limit. n8n exports and attaches the original PDF bytes directly. A missing name placeholder stops before email is sent.

If a copy, replacement or email has an unknown result, inspect Drive, Slides or Gmail before retrying. In Open Flow enter the pending key and confirmed or absent in Choose certificate step; a confirmed copy also needs its ID. Clear recovery fields after replay. In n8n inspect the matching Data Table row; for an absent copy delete it, for a confirmed copy set payload.fileId and ready-replace, for an absent or confirmed replacement set ready-replace or ready-email, and for an absent or confirmed email set ready-email or done. Resume the same submission through the authenticated resume webhook.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Quiz certificate by email](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Googleslides/0754_Googleslides_Noop_Automation_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
