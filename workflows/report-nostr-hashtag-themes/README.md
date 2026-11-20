# Report Nostr Hashtag Themes

Summarize Nostr hashtag posts and send a themes overview and detailed report by email and Telegram.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/report-nostr-hashtag-themes.n8n.json)
<!-- template-actions:end -->

## Setup

Select an AI model, connect Gmail and Telegram, and set the email and chat ID in both corresponding nodes.

## Behavior

The workflow analyzes the fetched posts, extracts themes, prepares a detailed report, and delivers both summaries to Gmail and Telegram. AI results may be inaccurate.

If a delivery fails or its result is unknown, inspect both destinations and complete the report manually before entering the pending execution ID in **Prepare hashtag posts** to acknowledge it. Do not replay the report without checking each destination. Keep runs from overlapping.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Report Nostr hashtag themes](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Telegram/0001_Telegram_Schedule_Automation_Scheduled.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
