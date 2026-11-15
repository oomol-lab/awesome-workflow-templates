# Draft a Website-Grounded Cold Email

Draft a personalized cold email grounded in a lead’s website.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/draft-website-grounded-cold-email.openflow.json) · [n8n JSON](templates/draft-website-grounded-cold-email.n8n.json)

## Setup and use

Import n8n, enable the alternate Open Flow form and authenticated website relay, configure Header Auth and set its URL and matching N8N_SITE_RELAY_TOKEN in Open Flow. Configure a model and deploy the Open Flow webhook. For direct n8n mode configure the model. Restrict the relay and entry points to trusted callers because they can fetch supplied URLs. Use one mode.

Enter the lead’s first name, company, website URL and your offer. The workflow reads the page body, compresses whitespace and sends up to 6,000 characters to the model. It returns a single draft for review and does not send email. If the page is unavailable or has fewer than 40 words it requests human review; the model also flags error pages or insufficient evidence. Verify all generated claims before use.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Website-Grounded Cold Email Writer](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/Gmail_and_Email_Automation/Website-Grounded%20Cold%20Email%20Writer.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
