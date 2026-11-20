# Send Churn Risk Win-Back Offers

Generate Turkish win-back offers for high-risk customers and record confirmed emails.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/send-churn-risk-winback-offers.n8n.json)
<!-- template-actions:end -->

## Setup

Connect Google Sheets, Gmail and a model. Configure SYSTEM_LOG with customer_id, system_log, date columns. Prevent concurrent runs.

## Behavior

Each day customers with a numeric score above 0.7 and at most 1 receive a Turkish offer. Scores through 0.8 receive an informational message about a preferred category; scores through 0.9 receive 200 points on Books, and higher scores receive a 20% Books discount. Confirm your business can honor these offers and review AI-generated content. Customer preferences are sent to the selected model and may appear in execution history. The source's campaign-date note is not implemented in its filter.

The log is appended only after Gmail confirms the send. If delivery or logging is uncertain, inspect Gmail and SYSTEM_LOG before retrying.

<details>
<summary>Inspiration &amp; credits</summary>

Retain the score tiers and send the email before appending its log; preserve each customer ID.

Adapted from [Daily churn risk win-back offers](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Filter/0948_Filter_Schedule_Create_Scheduled.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
