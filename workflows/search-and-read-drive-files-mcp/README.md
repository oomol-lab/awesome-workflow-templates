# Search and Read Drive Files with MCP

Search Drive files and read supported file contents through MCP tools.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/search-and-read-drive-files-mcp.n8n.json)
<!-- template-actions:end -->

## Setup

Set Bearer Auth on the MCP trigger and Header Auth on the binary extraction webhook with Authorization: Bearer followed by a secret token, and configure the Google Drive and OpenAI credentials. The MCP server exposes SearchFiles and ReadFile. Configure the client with the authenticated MCP endpoint. Restrict both endpoints to trusted callers.

Search matches file names in My Drive and returns up to ten files. ReadFile downloads the requested file and extracts PDF text or CSV rows, describes an image or transcribes audio. The original folderId input did not constrain the read. Video and Google Docs exported as plain text had no result branch in the source and are reported as unsupported. CSV aggregates all rows and escapes quotes; the original single-execution setting could drop rows. Images and audio are sent to the configured AI service. Use searchable PDFs.

See the [MCP reference](https://github.com/modelcontextprotocol/servers/tree/main/src/gdrive).

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Google Drive MCP Server](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Googledrivetool/0875_Googledrivetool_Extractfromfile_Import_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
