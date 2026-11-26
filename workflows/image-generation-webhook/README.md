# Generate an Inline PNG from a Webhook

Open an authenticated URL with an image prompt and view the generated PNG in your browser.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/image-generation-webhook.n8n.json)
<!-- template-actions:end -->

## Setup

1. Import the workflow. In **Receive the image prompt**, select a Basic Auth credential with a unique username and strong password. Use HTTPS for the webhook.
2. Connect an OpenAI API credential in **Generate the PNG**. Your OpenAI project needs access to `gpt-image-2.5-flare`. [OpenAI image generation API](https://developers.openai.com/api/reference/resources/images/methods/generate)
3. Publish the workflow. Open the production webhook URL in your browser with `?input=` followed by one URL-encoded prompt, for example `?input=A%20woodcut%20of%20a%20heron`. Enter your webhook credentials at the browser prompt.

## Behavior

Each accepted request makes one billable OpenAI call and waits for the 1024 × 1024 PNG to display in the same browser tab. The workflow accepts one prompt of up to 4,000 characters. It rejects requests that the browser marks as coming from another site. Failed model calls are never retried automatically. Allow up to 75 seconds for the OpenAI request and check your hosting provider’s webhook timeout. OpenAI receives the prompt, which also appears in the URL and may be saved in browser history or server access logs.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Configure your own Image Creation API Using OpenAI DALLE-3](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/OpenAI_and_LLMs/Configure%20your%20own%20Image%20Creation%20API%20Using%20OpenAI%20DALLE-3.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The [original n8n gallery template](https://n8n.io/workflows/2217-configure-your-own-image-creation-api-using-openai-dalle-3/) credits Bela. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

## Changes to the source

GPT Image 2.5 Flare replaces the retired DALL·E 3 model. The workflow validates the returned PNG and requires webhook authentication. It keeps the original GET query parameter and inline image response. [OpenAI model deprecations](https://developers.openai.com/api/docs/deprecations)

</details>
