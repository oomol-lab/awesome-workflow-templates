# Create and Enrich a Humantic Profile

Create a profile, enrich it with a resume, and retrieve its hiring persona for review.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/create-and-enrich-humantic-profile.n8n.json)
<!-- template-actions:end -->

## Setup

Connect a Humantic API subscription and provide its API key as HUMANTIC_API_KEY. Use one mode and prevent overlapping runs.

## Behavior

One manual run creates a profile for the supplied LinkedIn URL, uploads the matching resume, then requests the hiring persona for that same identifier. Humantic processes updates asynchronously, so an immediate fetch may report in progress; retrieve it later rather than repeating writes. The resume and inferred personality profile are sensitive, and are sent to Humantic. Review the result with appropriate safeguards and make any employment decision independently.

A pending create or update may have succeeded. The workflow does not automatically repeat writes.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Create, update, and get a profile in Humantic AI](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/Other_Integrations_and_Use_Cases/Create%2C%20update%2C%20and%20get%20a%20profile%20in%20Humantic%20AI.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
