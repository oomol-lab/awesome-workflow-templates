# Send an SMS with MessageBird

Send an SMS to one or more recipients using MessageBird.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/send-sms-with-messagebird.openflow.json) · [n8n JSON](templates/send-sms-with-messagebird.n8n.json)

## Setup

In Open Flow create a secret Variable named `MESSAGEBIRD_AUTHORIZATION` containing `AccessKey ` followed by your MessageBird API key, and bind it to **Send the SMS**. Run with the sender, message and comma-separated recipient numbers including country codes. In n8n connect MessageBird and enter the same values in **MessageBird**. Use one format per send.

## Behavior

A manual run sends one message request to up to 50 recipients and returns MessageBird's response. The response reports recipient statuses; acceptance does not guarantee delivery. Open Flow rejects malformed recipient numbers before sending. If a request fails or the outcome is uncertain, check MessageBird and recipient statuses before retrying; some or all messages may already have been sent.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Open Flow uses MessageBird's SMS API directly and validates recipient numbers before sending.

Adapted from [Sending an SMS with MessageBird](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Manual/1166_Manual_Messagebird_Send_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The matching [n8n community listing](https://n8n.io/workflows/455-sending-an-sms-with-messagebird/) credits tanaypant. The original template does not state a separate license.

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
