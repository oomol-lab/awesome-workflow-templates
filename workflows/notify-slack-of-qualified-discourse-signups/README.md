# Notify Slack About Qualified Discourse Signups

Match new Discourse members to their employers and alert a private Slack channel when the employer meets your size and traffic criteria.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/notify-slack-of-qualified-discourse-signups.n8n.json)
<!-- template-actions:end -->

## Setup

1. In **Verify event and authorize the signup**, enter your Discourse HTTPS base URL without a trailing slash and the ID of a private Slack channel where members may view the matched professional information. The default thresholds are 30 employees and a worldwide rank of 100,000 or better. Change `minEmployees` and `maxGlobalRank` there.
2. In Discourse, create a dedicated JSON webhook for `user_created`. Set a distinct random signing secret of at least 24 characters and copy the HTTPS production endpoint from **Receive signed Discourse user events**. Use the same secret in **Compute Discourse HMAC** through the `DISCOURSE_SIGNING_SECRET` expression. The environment-variable expression requires `N8N_BLOCK_ENV_ACCESS_IN_NODE=false` on a trusted self-hosted deployment. You can use a managed external secret instead. Use a hook whose signed payload includes the new user’s primary email. [Discourse webhooks](https://meta.discourse.org/t/configure-webhooks-that-trigger-on-discourse-events-to-integrate-with-external-services/49045)
3. Select Header Auth with header `X-API-KEY` in **Match the email and organization with Hunter** for Hunter. In **Read Similarweb worldwide ranking**, select a different Header Auth credential with `api-key` for Similarweb API V5 Website Ranking. In **Post to the private Slack channel**, select the same Slack OAuth2 connection as **Read the configured Slack channel**, with `groups:read` and `chat:write`. Grant the app access to the configured private channel. Confirm your forum privacy notice and provider agreements permit sending a member’s work email to Hunter and publishing matched details to that channel. [Hunter enrichment](https://hunter.io/api-documentation/v2#combined-enrichment) · [Similarweb Website Ranking](https://docs.similarweb.com/api-v5/api-reference/website-analysis-api/website-performance/website-ranking)
4. Create an n8n Data Table with a string column named `signup_key`. Select it in **Skip signup already reserved for Slack** and **Reserve the qualified signup**. Run in regular mode with `N8N_CONCURRENCY_PRODUCTION_LIMIT=1` and avoid overlapping manual runs so the reservation cannot race. Publish after entering the credentials, channel and forum. [n8n concurrency control](https://docs.n8n.io/hosting/scaling/concurrency-control/)

## Behavior

The workflow verifies the signature over the original request bytes before processing a new-user event. It uses the email from the signed Discourse payload. An absent work email, staged account, or common personal address stops processing. Hunter must return the same work email and the exact same domain for the person’s employment and the company. It also checks the numeric employee count and skips profiles marked unavailable or opted out.

Only the qualified employer’s domain goes to Similarweb. The workflow uses the latest returned worldwide rank from the last three complete UTC months. The original threshold used Alexa Global Rank, which Clearbit retired. Similarweb estimates worldwide website traffic with its own methodology, so the same numeric cutoff can qualify a different set of employers. The alert includes the matched name, role, company, industry and work email, plus the measured rank and any verified-format LinkedIn profile link. It disables link previews and omits remote profile images. [Clearbit API changes](https://help.clearbit.com/hc/en-us/articles/115015797408-Clearbit-API-Version-Change-Logs) · [Similarweb rank data](https://docs.similarweb.com/api-v5/guides/available-data)

The workflow verifies that Slack reports an active, private and unshared destination. It reserves the forum and user ID before sending to that channel. Keep receipt rows to suppress repeated deliveries. If Slack’s reply is unavailable, inspect the private channel before posting manually. The workflow never automatically repeats an unconfirmed send. Execution saving is disabled in the template. Keep access to live execution data and provider logs limited.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

The personal-address checks now reject any of the listed providers. Hunter replaces Clearbit’s person and company lookup, and Similarweb replaces its retired numerical Alexa field. Industry describes the employer in Slack. Eligibility uses employee count and worldwide rank.

Adapted from [Enrich new Discourse members and notify Slack](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Webhook/0414_Webhook_Filter_Create_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Max Tkacz (original n8n template), Zie619 (collection). [Original n8n template](https://n8n.io/workflows/2109-enrich-new-discourse-members-with-clearbit-then-notify-in-slack/)

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
