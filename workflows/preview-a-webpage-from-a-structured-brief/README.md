# Preview a Webpage from a Structured Brief

Describe a page in a webhook query and preview the generated mockup in the same browser request.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/preview-a-webpage-from-a-structured-brief.n8n.json)
<!-- template-actions:end -->

## Setup

1. In **Receive the webpage brief**, set up n8n Basic Auth before adding credentials if the deployment is publicly reachable. The default GET endpoint has no authentication and should be used only on a restricted network. Any authorized request can use your OpenAI quota.
2. Bind the same OpenAI API credential in **Design the recursive layout** and **Refine the title and page copy**. Activate the workflow and open its production HTTPS webhook URL in a browser. Add a URL-encoded brief such as `?query=Design%20a%20signup%20page%20for%20a%20seed%20swap`.

## Behavior

The workflow takes one `query` value of up to 2,000 characters. GPT-6 Luna proposes a recursive layout, then refines its title and text. The renderer builds a static HTML preview from those two results and returns it in the same GET response. Keep private information out of the query URL.

The preview uses built-in styles and escaped text. Form fields and buttons are disabled. It does not load external resources, execute generated code or send form data. Keep n8n's HTML sandbox enabled.

Invalid input returns HTTP 400. A model refusal returns 422. A failed or invalid model response returns 502. Each model request can take up to 30 seconds, so configure your deployment and HTTPS proxy to keep the browser connection open long enough for both calls.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Dynamically generate a webpage from user request using OpenAI Structured Output](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/OpenAI_and_LLMs/Dynamically%20generate%20a%20webpage%20from%20user%20request%20using%20OpenAI%20Structured%20Output.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). Original workflow by Agent Studio. This adaptation retains two model passes and builds the final document from a validated layout and text instead of executing generated markup. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

[Original n8n template by Agent Studio](https://n8n.io/workflows/2388-dynamically-generate-a-webpage-from-user-request-using-openai-structured-output/).

</details>
