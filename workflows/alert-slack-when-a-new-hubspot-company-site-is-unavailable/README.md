# Alert Slack When a New HubSpot Company Site Is Unavailable

Check the HTTPS domain on each new HubSpot company and notify one Slack channel if the check fails.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/alert-slack-when-a-new-hubspot-company-site-is-unavailable.n8n.json)
<!-- template-actions:end -->

## Setup

1. Deploy n8n 2.12 or later with `N8N_SSRF_PROTECTION_ENABLED=true` and network egress rules that block private destinations and cloud metadata endpoints. Keep the default blocked ranges and leave website hosts out of infrastructure allowlists that override those checks. [n8n SSRF protection](https://docs.n8n.io/hosting/securing/ssrf-protection/)
2. In **Set the account, webhook URL and channel**, set the HubSpot account ID, the production HTTPS webhook URL with no query or fragment, and the Slack channel ID. In **Verify v3 signatures**, set **Secret** to your HubSpot app's client secret. If you use classic v1-signed deliveries, use the same secret in the **Value** expression in **Verify classic signatures**, before the concatenation with `$json.rawText`. Use a secret expression where available or keep the populated workflow private.
3. Configure a HubSpot project app with OAuth and a webhook with a `crmObjects` subscription for `object.creation` and `objectType: company`, targeting that production URL. Classic `company.creation` subscriptions are also accepted. Install the app on the same account. In **Read the same HubSpot company**, attach a Bearer Auth credential for a HubSpot Service Key or another token from that account with `crm.objects.companies.read`. In **Send the availability alert**, attach a Bearer Auth credential for a Slack bot with `chat:write` and access to the selected channel. [HubSpot webhook subscriptions](https://developers.hubspot.com/docs/apps/developer-platform/add-features/configure-webhooks)
4. Create a dedicated Data Table with text columns `company_key`, `status`, and `receipt`. Select it in **Skip companies already checked**, **Reserve this company check**, and **Record the result**. Activate one regular-mode production copy with `N8N_CONCURRENCY_PRODUCTION_LIMIT=1`.

## Behavior

The webhook verifies HubSpot's signature against the original request bytes before acknowledging delivery. It checks creation events from the configured HubSpot account. For each event it reads that same company by ID and checks the root of its public HTTPS domain with GET. It skips missing or invalid domains, mismatched CRM records, and replays of a recorded company check.

HTTP 200 is silent. Any other HTTP status or no response produces a Slack availability alert with that company's name, CRM website, and record ID. Redirects are reported without following them. No-response alerts can reflect DNS, TLS, timeouts, or blocked egress. The check measures availability from the workflow runtime.

The Data Table reserves each company check before contacting the website. Review `pending` and `alert_unconfirmed` rows before clearing them for a retry. A webhook acknowledgment confirms receipt. Keep execution history off if you do not need to store payloads or company data.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Check a new HubSpot company domain and notify Slack](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Http/0167_HTTP_Slack_Create_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Zie619 / n8n-workflows.

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
