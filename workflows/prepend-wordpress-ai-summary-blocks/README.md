# Add AI Summaries to WordPress Posts

Add a four-point summary to recent WordPress articles, log each update in Google Sheets, and notify Slack.

<!-- template-actions:start -->
[![View in Open Flow](../../assets/view-in-openflow.svg)](https://openflow.run/templates/prepend-wordpress-ai-summary-blocks/) [![n8n JSON](../../assets/n8n-json.svg)](templates/prepend-wordpress-ai-summary-blocks.n8n.json)
<!-- template-actions:end -->

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

## Setup

1. Set your WordPress HTTPS site URL, Google spreadsheet ID, worksheet name and Slack channel ID in **Set the site, worksheet and Slack channel**. Connect the same WordPress account to its list, read and update steps, and allow Provider API access. The account must be able to edit the selected published posts and save the Gutenberg HTML block. [WordPress REST API](https://developer.wordpress.org/rest-api/reference/posts/)
2. In a spreadsheet tab dedicated to this site, create the headers `post_id`, `summary`, `post_link`, `edit_link` and `summary_date`. Existing tabs can use `summarized_date` instead. You can add a sixth header, `title`. Use each header once. Bind Google Sheets to both worksheet steps, OpenAI to **Write four summary points** and Slack to **Notify Slack of the update**.
3. Enable persistent State. Run **Run on demand** while nobody is editing the same posts. Use one workflow in one mode for this site and worksheet. Draft and published runs have separate State, so check unresolved writes before switching.

## Behavior

Each manual run checks the five latest published posts by default. Set the limit between one and ten in **Set the site, worksheet and Slack channel**. The workflow skips logged post IDs, password-protected posts and posts that already contain a recognized AI summary, including the original template’s blue summary block. Empty articles and articles over 140,000 rendered characters or 400,000 raw characters are skipped.

OpenAI writes four points and a heading in the article’s language. The workflow escapes the text and inserts a Gutenberg summary block ahead of the existing content. The update sends only the content field, leaving the saved excerpt intact. A second editable read compares the article immediately before updating. If it detects a change, that post is skipped. WordPress’s core update endpoint has no atomic compare-and-swap. An edit made between the final read and write can still be overwritten, so pause other edits while running. [WordPress update endpoint](https://developer.wordpress.org/rest-api/reference/posts/#update-a-post)

A confirmed edit produces one Google Sheets row with the exact block and post links. A confirmed row triggers a Slack notice with the post’s title, ID and links. If a write or send lacks a matching confirmation, inspect WordPress, the worksheet and Slack before recovering that post. Its reservation prevents an automatic repeat in the same run mode. Match the exact post ID in all three services before you clear its `wordpress-summary:<site URL>:<post ID>` reservation. If WordPress shows the new block and a later step failed, complete the missing log or notice only after checking its destination. The workflow skips existing summaries on later runs.

<details>
<summary>In n8n</summary>

In **Set the site, worksheet and Slack channel**, set the same site and destinations. Use a Basic Auth credential with a WordPress username and Application Password on its four HTTP nodes, a Google Sheets OAuth credential on both Google requests, an OpenAI credential on the summary request, and a Header Auth credential with `Authorization: Bearer YOUR_SLACK_BOT_TOKEN` on the Slack request. Give the Slack app access to the channel and the `chat:write` scope.

Create a Data Table with one string column named `request_key`. Select the same table in **Check for a pending post update** and **Reserve the checked update**. Run only one manual execution at a time and keep the table’s reservation rows. If a run stops after a write, check the post, worksheet, and Slack before recovering it.

</details>

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

The original export’s Schedule and Webhook nodes are disabled and their read branches have no connection to the update steps. This version keeps the working Manual Trigger. It checks for a prior summary directly and formats the OpenAI response into the summary block.

Adapted from [AI-generated summary block for WordPress posts](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Datetime/1272_Datetime_Webhook_Create_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Dataki (original workflow) / Zie619 (collection). [Original n8n workflow](https://n8n.io/workflows/2822-ai-generated-summary-block-for-wordpress-posts/)

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
