# Score and Route Demo Leads

Score inbound demo leads, record their context, and route follow-up alerts.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/score-and-route-demo-leads.openflow.json) · [n8n JSON](templates/score-and-route-demo-leads.n8n.json)

## Setup and use

Connect Gmail and Google Sheets, set the spreadsheet ID and create a Leads sheet with columns received_at, priority, lead_score, sla_minutes, owner_team, intent_tags, page_signal_tags, dedupe_key, email, company, message, name, phone, role, budget, timeline, page_url, source, utm_campaign, needs_exec_escalation, missing_contact, page_title and page_description. Set the four recipient addresses in Prepare audit and routing. Import the n8n workflow and configure its Gmail and Sheets credentials.

Choose one intake: enable Lead Intake Webhook for n8n mode, or disable it and enable Open Flow relay webhook for Open Flow mode. In relay mode set the deployed Open Flow webhook URL in Forward lead, set the Page context relay URL in Open Flow and activate n8n. Neither intake nor the page context relay authenticates callers; restrict access to trusted senders.

## Behavior

Missing contact information returns HTTP 400. A valid submission is scored and optionally enriched with its submitted page title and description; page fetch failures continue without page signals. The workflow writes an audit row and sends a priority email. Hot leads with the source's executive escalation flag also send a leadership alert. It returns priority, score, SLA, owner and dedupe key. The key is descriptive and does not deduplicate submissions.

If an audit append or Gmail send loses its response, the write may have happened. Inspect the sheet and mailbox before retrying the same submission. Open Flow's webhook waits up to 60 seconds for its response. Page URLs and lead data are processed by the workflow and retained according to your execution-history settings.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Add a complete-payload n8n relay and preserve request data after Gmail sends. The page context relay preserves the source HTTP timeout and continues with empty page context on fetch failure.

Adapted from [B2B Demo Lead Rescue Desk - Enrich Score Route and Escalate](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/Google_Drive_and_Google_Sheets/B2B%20Demo%20Lead%20Rescue%20Desk%20-%20Enrich%20Score%20Route%20and%20Escalate.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
