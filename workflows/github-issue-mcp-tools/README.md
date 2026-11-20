# GitHub Issue MCP Tools

Expose latest issues, issue comments and comment creation as repository-scoped MCP tools.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/github-issue-mcp-tools.n8n.json)
<!-- template-actions:end -->

## Setup

Configure Bearer Auth on **Github MCP Server**. Set the same owner/repository in each of its three tool nodes and in **Validate MCP request**. Connect a GitHub account with issue read and comment access. Connect a compatible MCP client to the authenticated server endpoint.

## Behavior

The server exposes getLatestIssues, getIssueComments and addIssueComment for the configured repository. Latest issues returns at most ten open issues ordered by creation; comments returns the first page of up to 30. Posting requires an issue number and text. Caller inputs and returned issue content can appear in execution history.

Each comment is reserved before creation. If the result is unknown, inspect the GitHub issue before replay. The key includes repository, issue and text; an intentional identical repeat requires clearing its confirmed checkpoint after verifying the prior comment.

<details>
<summary>Inspiration &amp; credits</summary>

Add repository validation, authenticated relay and a comment checkpoint.

Adapted from [Build a GitHub MCP server](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Github/0876_GitHub_Aggregate_Create_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
