# Parse and Validate a Phone Number with Uproc

Parse and validate a phone number using Uproc.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/parse-and-validate-phone-with-uproc.openflow.json) · [n8n JSON](templates/parse-and-validate-phone-with-uproc.n8n.json)

## Setup

The workflow uses Uproc’s legacy v2 process API. In Open Flow, create secret Variables for the Uproc account email and API key and bind them to **Auth Username** and **Auth Password** in **Parse the phone number**. Run with a phone number, including its international prefix.

In n8n, connect a Uproc API credential and set the phone number in **Create Phone Item**. Run either format manually.

## Behavior

Each run submits a phone number for Uproc to parse and check its format and prefix. Each response item is marked valid when its `message.valid` value converted to text equals `true`, matching the source condition. Open Flow returns each item with a `valid` flag in the `results` array. n8n routes matching and nonmatching items to the true and false outputs of **Phone is Valid?**. An array response is treated as individual items in both formats. The response data is retained without filtering. Request failures stop the run. Open Flow has a 30-second HTTP timeout, a 4 MiB response limit, and a 1 MiB Code output limit.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Open Flow accepts the phone number as a run input and exposes the branch decision alongside each result.

Adapted from [Verify phone numbers](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Manual/0067_Manual_Uproc_Automation_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The matching [n8n community listing](https://n8n.io/workflows/863-verify-a-phone-number-with-uproc/) credits Miquel Colomer. The original template does not state a separate license.

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
