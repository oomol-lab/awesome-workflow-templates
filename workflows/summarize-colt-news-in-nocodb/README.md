# Summarize Colt News in NocoDB

Summarize recent Colt news and save summaries and keywords to NocoDB.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/summarize-colt-news-in-nocodb.n8n.json)
<!-- template-actions:end -->

## Setup

Create the fields News_Source, Title, Date, Link, Summary and Keywords. Use one format and prevent overlapping runs.

## Behavior

Each Wednesday at 04:32 UTC, fetch the Colt news index, pair dates and links by position, select posts dated within the preceding 70 days, read each article, produce a summary under 70 words and three technical keywords, and create a NocoDB record. The source code uses 70 days although its node name says seven. Previously selected articles can be written again on a later weekly run, as in the source. The original site-specific CSS selectors may need updating if the site changes. Article text is sent to the model.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Scrape and summarize posts of a news site without RSS feed](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/AI_Research_RAG_and_Data_Analysis/Scrape%20and%20summarize%20posts%20of%20a%20news%20site%20without%20RSS%20feed%20using%20AI%20and%20save%20them%20to%20a%20NocoDB.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
