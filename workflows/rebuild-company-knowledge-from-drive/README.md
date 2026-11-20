# Rebuild Company Knowledge from Drive

Clear and rebuild a Qdrant knowledge collection from a Google Drive folder.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/rebuild-company-knowledge-from-drive.n8n.json)
<!-- template-actions:end -->

## Setup

The collection is cleared completely on each new rebuild. Use a dedicated collection and keep a backup. Restrict the webhook using an authenticated gateway or private network. The EPUB parser needs a writable temporary directory.

## Use

Drive is listed before deletion; an empty folder clears the collection and indexes nothing. Do not overlap rebuilds. A pending record means the deletion or insertion outcome may be unknown; inspect Qdrant and reconcile before retrying, reusing the same rebuild ID. Rebuilding is not transactional and searches can see a partial collection until completion.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [AI-Powered Email Automation for Business: Summarize & Respond with RAG](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/OpenAI_and_LLMs/AI-Powered%20Email%20Automation%20for%20Business_%20Summarize%20%26%20Respond%20with%20RAG.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

Changes: isolate Drive rebuild, list all pages before clearing, align model and dimensions with inquiry retrieval, and add rebuild checkpoints.

Collection license notice:

```text
Creative Commons Attribution 4.0 International License

Copyright (c) 2024-2026 Enes Cingoz

You are free to:

  Share - copy and redistribute the material in any medium or format
  Adapt - remix, transform, and build upon the material for any purpose,
  even commercially.

Under the following terms:

  Attribution - You must give appropriate credit, provide a link to the
  license, and indicate if changes were made. You may do so in any
  reasonable manner, but not in any way that suggests the licensor
  endorses you or your use.

  No additional restrictions - You may not apply legal terms or
  technological measures that legally restrict others from doing
  anything the license permits.

Notices:

  You do not have to comply with the license for elements of the
  material in the public domain or where your use is permitted by an
  applicable exception or limitation.

  No warranties are given. The license may not give you all of the
  permissions necessary for your intended use. For example, other rights
  such as publicity, privacy, or moral rights may limit how you use the
  material.

For the full license text, see:
https://creativecommons.org/licenses/by/4.0/legalcode
```

</details>
