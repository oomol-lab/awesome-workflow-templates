# Respond to an HMAC CRC Challenge

Answer a CRC webhook challenge with a signed response token.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/respond-to-hmac-crc-challenge.openflow.json) · [n8n JSON](templates/respond-to-hmac-crc-challenge.n8n.json)

## Setup

Bind a secret Variable containing the shared API key secret to **Sign challenge** and deploy the webhook. In n8n enter the same secret in **Crypto**, set the webhook path and activate the workflow. Configure your calling service to send its GET challenge to the deployed URL.

## Behavior

For a GET request with a nonempty crc_token query parameter, the endpoint returns JSON containing response_token, formed by prefixing sha256= to the Base64 HMAC-SHA256 of the token using the configured secret. Missing input or secret stops the run. This endpoint implements the challenge response only.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Replace the example secret with a secret Variable in Open Flow.

Adapted from [CRC webhook challenge response](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Crypto/0164_Crypto_Webhook_Automate_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
