# Research a Topic into HTML

Research a topic with Perplexity and return an HTML article.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/research-topic-to-html.n8n.json)
<!-- template-actions:end -->

## Setup

Restrict webhook access.

Send a GET request with URL-encoded topic, chatId and requestId query parameters. Use a unique requestId for each request and prevent overlapping requests with the same ID.

## Behavior

The workflow rewrites the topic, invokes a Perplexity research tool, sends the research topic and an excerpt to Telegram, and returns a generated HTML page. Research is limited to the source workflow's perplexity.ai domain and the preceding month. Both the topic and research are sent to external AI services. Generated HTML can contain inaccurate or unsafe content; inspect it and display it only in a sandboxed context.

A notification is reserved before sending. A repeated request ID is blocked; resolve the existing notification manually and use a new ID only after confirming whether the prior messages were sent. Never run both entry points for the same request.

The synchronous Sonar Chat Completions API remains operational through Perplexity's compatibility path, although its support ended on September 27, 2026. Check Perplexity's current API availability before use.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Perplexity Researcher to HTML Web Page](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/AI_Research_RAG_and_Data_Analysis/%F0%9F%94%8D%20Perplexity%20Research%20to%20HTML_%20AI-Powered%20Content%20Creation.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
