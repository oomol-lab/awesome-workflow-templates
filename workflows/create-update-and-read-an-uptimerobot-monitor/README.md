# Create, Update, and Read an UptimeRobot Monitor

Create an HTTP monitor, rename it, and read its details.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/create-update-and-read-an-uptimerobot-monitor.openflow.json) · [n8n JSON](templates/create-update-and-read-an-uptimerobot-monitor.n8n.json)

## Setup and use

Connect UptimeRobot with an API key permitted to create and edit monitors. Run Open Flow with the monitored URL, an initial name and the new name. In n8n configure its UptimeRobot credential and replace the example URL and names before running manually. Use one workflow format.

## Behavior

Each run creates a real HTTP monitor, changes its name and reads back its details. The monitor remains in your account. If a create or rename result is uncertain, inspect the account before retrying to avoid duplicate monitors or unintended changes.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Add a manual trigger and configurable inputs in Open Flow.

Adapted from [Create, update and read an UptimeRobot monitor](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Uptimerobot/0050_Uptimerobot_Automate.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
