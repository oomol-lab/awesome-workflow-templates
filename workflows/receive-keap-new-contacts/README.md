# Receive Keap New Contacts

Receive notifications when Keap contacts are added.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/receive-keap-new-contacts.openflow.json) · [n8n JSON](templates/receive-keap-new-contacts.n8n.json)

## Setup and use

Import the n8n workflow and connect Keap in **Keap Trigger**. Activate it to register the contact.add hook; its URL must be publicly reachable by Keap. Confirm the subscription is verified in Keap. For Open Flow enter its webhook URL in **Forward to Open Flow** and enable that node; leave it disabled for n8n alone. Restrict access to the webhook endpoints.

## Behavior

Keap batches changed contacts; the trigger emits each contact ID, event type, timestamp and optional API URL separately. It responds to the registration handshake but does not authenticate later events. The optional relay forwards each event to Open Flow. Restrict endpoint access and inspect n8n execution history for relay failures. Event details may appear in execution history.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Add an optional n8n relay.

Adapted from [Keap contact addition events](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Keap/1023_Keap_Automate_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
