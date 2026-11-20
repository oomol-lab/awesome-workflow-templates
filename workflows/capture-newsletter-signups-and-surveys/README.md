# Capture Newsletter Signups and Surveys

Record newsletter signups, notify Slack and save an optional survey to the same row.

<!-- template-actions:start -->
[![View in Open Flow](../../assets/view-in-openflow.svg)](https://openflow.run/templates/capture-newsletter-signups-and-surveys/) [![n8n JSON](../../assets/n8n-json.svg)](templates/capture-newsletter-signups-and-surveys.n8n.json)
<!-- template-actions:end -->

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

## Setup

Create a Sheet1 tab with columns execution_id, date, email, first_name, last_name, job_level, job_function, country_region, product_experience, product_goals, enrol_betatesters in that order. Connect Google Sheets and Slack. Select a Data Table with item_key and status text columns for n8n checkpoints and prevent overlapping sheet writes.

For Open Flow set **Prepare signup** to relay, configure the webhook URL, spreadsheet IDs and Slack channel, connect Sheets and Slack, and enable persistent State. Restrict webhook access to trusted n8n. Direct mode runs in n8n; use one mode.

## Behavior

The first form saves the email and date and sends a Slack notification. A three-page survey follows; if the visitor leaves it unfinished, the original signup remains. Completing it updates the same execution ID with the person's name, role, country, product interests and beta preference. The workflow records newsletter consent through the signup form; it does not send a newsletter or manage unsubscribe requests. Personal data can appear in execution history and the Slack channel.

If a sheet write, Slack send or relay result is uncertain, inspect the corresponding records before replaying. Open Flow uses separate pending keys in **Reserve signup row** and **Reserve Slack notification**; enter the key and confirmed or absent, replay the same stage, then clear the fields. In n8n awaiting_survey means the initial signup completed and the optional form is still open. Reconcile a pending submission and finish any missing steps manually before marking it done; remove it only if no external write occurred.

<details>
<summary>Inspiration &amp; credits</summary>

Checkpoint writes and retain the execution ID across the survey.

Adapted from [Newsletter signup and optional survey](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Form/0648_Form_GoogleSheets_Create_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
