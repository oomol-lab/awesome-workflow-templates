# Receive HubSpot App Events

Receive events from a HubSpot app subscription.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/receive-hubspot-app-events.openflow.json) · [n8n JSON](templates/receive-hubspot-app-events.n8n.json)

## Setup and use

Import and activate the n8n workflow. Configure your HubSpot app to deliver its selected legacy webhook subscriptions to the **Receive HubSpot events** production URL. Store the app client secret as HUBSPOT_CLIENT_SECRET in the n8n environment and allow the workflow to access it. For Open Flow, enter its webhook URL in **Forward to Open Flow** and enable that node; leave it disabled for n8n alone. Restrict access to the relay endpoint.

## Behavior

The n8n workflow checks the v1 SHA-256 signature over the original request bytes and emits each event from the batch. As in the source, contact, company, deal and ticket object IDs are mapped to their corresponding named ID field. Unsafe integers become decimal strings. The optional relay forwards each event to Open Flow. Inspect n8n execution history for forwarding failures. Events may contain personal information.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Replace the source app-wide registration with manual subscription configuration and validate the signature over raw bytes. The source did not select an event; choose subscriptions in HubSpot.

Adapted from [HubSpot app events](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Hubspot/1081_HubSpot_Automate_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
