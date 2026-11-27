# Save Discord Links to Notion

Use a Discord slash command to save a webpage’s title and URL in Notion.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/save-discord-link-to-notion.n8n.json)
<!-- template-actions:end -->

## Setup

1. On self-hosted n8n 2.12 or later, set `N8N_SSRF_PROTECTION_ENABLED=true` and restrict network egress to public endpoints. In the Code task runner, allow only the Node built-ins this workflow uses with `NODE_FUNCTION_ALLOW_BUILTIN=crypto,url`. Apply the module setting to the external task runner if you use one. [n8n outbound request protection](https://docs.n8n.io/deploy/host-n8n/configure-n8n/security/enable-ssrf-protection.md)
2. In **Verify Discord and approve the URL**, enter the Discord application ID, its public key and the server ID. Set `allowedHosts` to the exact hostnames of approved public sites. The list starts empty. Do not add private hostnames to the n8n SSRF allowlist.
3. Register a server chat-input command named `/save-link` with one required string option named `url`. Activate the workflow and paste the production HTTPS URL from **Receive the Discord interaction** into the app's Interactions Endpoint URL. [Discord application commands](https://docs.discord.com/developers/interactions/application-commands) · [Discord HTTP interactions](https://docs.discord.com/developers/interactions/receiving-and-responding)
4. In **Verify Discord and approve the URL**, set the Notion data source ID for your bookmarks database. The data source ID is distinct from the database ID. Add a title property named `Name` and a URL property named `Link`. Share the data source with a Notion integration that can insert pages. Select its Notion API credential in **Create the Notion page**. [Notion page creation](https://developers.notion.com/reference/post-page)

## Behavior

The workflow verifies Discord's Ed25519 signature against the original body and rejects stale requests. Discord PING receives PONG without fetching or writing anything. An approved command gets a deferred response and the workflow fetches the HTTPS page without following redirects. It parses the text in the HTML title and saves that title and the canonical HTTPS URL without its fragment in Notion.

The workflow edits the original Discord reply after Notion confirms the title, URL and data source. Missing titles or unconfirmed writes produce an error message. If the Notion result is uncertain, check the data source before running again. Another invocation can create another bookmark. Automatic retries and execution-data saving are disabled. Keep request logging off for the webhook and the Discord edit URL because they contain private interaction tokens.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

Verify Discord requests before accepting them. Defer slash commands while fetching the title and writing to Notion. Set up a public-host list and use the destination's Notion data source ID.

Adapted from [Discord link capture in Notion](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Http/0048_HTTP_Htmlextract_Create_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Zie619 / n8n-workflows.

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
