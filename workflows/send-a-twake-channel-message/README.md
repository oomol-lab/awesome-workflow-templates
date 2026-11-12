# Send a Twake Channel Message

Send a formatted message to a Twake channel.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/send-a-twake-channel-message.openflow.json) · [n8n JSON](templates/send-a-twake-channel-message.n8n.json)

## Setup

Install the n8n integration in the Twake workspace and obtain its workspace key and destination channel ID. In Open Flow create a secret Variable named `TWAKE_WORKSPACE_KEY` and bind it to **Send to Twake**. Run with the channel ID and formatted message. In n8n configure Twake Cloud credentials and enter the channel ID and message in **Twake**. Use one format per message.

## Behavior

A manual run posts one formatted message. The message is configured so everyone can delete it, as in the source. Open Flow returns the full API response; n8n returns its `object` field. If a request fails or the outcome is uncertain, check the channel before retrying to avoid a duplicate.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Open Flow uses the Twake n8n integration API directly and accepts the channel and message as run inputs.

Adapted from [Send a message on Twake](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Manual/0355_Manual_Twake_Send_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The matching [n8n community listing](https://n8n.io/workflows/595-send-a-message-to-a-channel-on-twake/) credits Harshil Agrawal. The original template does not state a separate license.

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
