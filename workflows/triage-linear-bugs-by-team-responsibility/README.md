# Route Linear Bugs to Teams

Classify eligible Linear bugs and route them to a responsible team or notify Slack.

<!-- template-actions:start -->
[![View in Open Flow](../../assets/view-in-openflow.svg)](https://openflow.run/templates/triage-linear-bugs-by-team-responsibility/) [![n8n JSON](../../assets/n8n-json.svg)](templates/triage-linear-bugs-by-team-responsibility.n8n.json)
<!-- template-actions:end -->

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

## Setup

Connect Linear in **Watch Linear issues**, **Read Linear issue**, and **Update issue team**, and set **teamId** in **Watch Linear issues**. Configure `stateId`, `labelId`, and `teams` in **Check issue eligibility**, bind a Secret Variable for your Linear API key to **Find Linear teams**, connect an LLM to **Choose responsible team**, and connect Slack in **Notify Slack**.

## Behavior

Every minute, **Watch Linear issues** polls for changed issues. For each issue, **Read Linear issue** retrieves full details, **Check issue eligibility** filters by state, label, and non-template description, **Choose responsible team** selects the owning Linear team, and the workflow updates the issue team or notifies Slack with idempotent state checkpoints.

<details>
<summary>In n8n</summary>

Import the n8n workflow, connect Linear, OpenAI, and Slack credentials, and configure the trigger team and target filters.

</details>

<details>
<summary>Inspiration &amp; credits</summary>

Validate team names and reserve each external write.

Adapted from [Assign Linear bugs to the appropriate team](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Filter/1383_Filter_Slack_Create_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
