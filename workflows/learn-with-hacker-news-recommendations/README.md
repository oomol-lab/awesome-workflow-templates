# Learn with Hacker News Recommendations

Find learning resources in Ask HN comments and email a categorized summary.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/learn-with-hacker-news-recommendations.n8n.json)
<!-- template-actions:end -->

## Setup

Configure SMTP, Gemini, the sender address.

Submit a topic and email address. The topic is optional. Up to 150 Ask HN results are selected in relevance order; direct comments are read and summarized into learning resource categories. No email is sent when no comment text is available. Comment content is sent to the model; review its recommendations and links.

Reuse the same submission ID for retries; a new form submission has a new ID. Avoid overlapping retries.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

Retrieve each search hit’s Firebase story to obtain its direct comment IDs; search hits do not include the children array. Update the model and use the submitted topic throughout.

Adapted from [Learn Anything from HN](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/AI_Research_RAG_and_Data_Analysis/Learn%20Anything%20from%20HN%20-%20Get%20Top%20Resource%20Recommendations%20from%20Hacker%20News.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
