# Email Quiz Certificates from Slides

Create and email a personalized PDF certificate for each passing quiz response.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/email-quiz-certificates-from-slides.n8n.json)
<!-- template-actions:end -->

## Setup

Configure a Google Sheets form-response tab with unique Submission ID, Name, Email and numeric Score columns. Each response must have a unique immutable Submission ID. The template must contain [ NAME ] on page object ID p, and the destination Drive folder must exist. Configure Header Auth on Resume submission. Enter the template and folder IDs in Choose certificate step. Prevent concurrent handling of the same submission.

A score strictly greater than 3 creates a copy of the Slides template, replaces [ NAME ] on page p, exports that copy as PDF and sends it to the respondent. Scores of 3 or less do not create or send a certificate. The Gmail connector fetches the temporary PDF transit URL; it must be accessible to the connector, and attachments have a 25 MB decoded limit. A missing name placeholder stops before email is sent.

If a copy, replacement or email has an unknown result, inspect Drive, Slides or Gmail before retrying. Clear recovery fields after replay. Resume the same submission through the authenticated resume webhook.

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
