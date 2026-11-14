# Send Customer Posts With Delay

Post customer IDs and names one at a time with a four-second delay.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/send-customer-posts-with-delay.openflow.json) · [n8n JSON](templates/send-customer-posts-with-delay.n8n.json)

## Setup and use

In Open Flow provide a customers array with id and name fields and set the target URL in **Post customer**. The default JSONPlaceholder endpoint is a public demonstration service. In n8n the original training datastore supplies fictional customers; replace it with your customer source and configure the HTTP destination. Use one format.

## Behavior

The workflow sends one JSON object with id and name per customer, waits four seconds after each successful POST, then processes the next customer. A failed or unknown request stops the run; earlier requests may have succeeded. Inspect the destination before retrying to avoid duplicate writes. Customer data is sent to the configured endpoint.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Open Flow accepts customer data directly instead of relying on the n8n training datastore.

Adapted from [Sequential customer posts](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Wait/0101_Wait_Manual_Automation_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
