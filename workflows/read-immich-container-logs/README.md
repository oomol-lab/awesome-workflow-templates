# Read Immich Container Logs

Return the most recent 1,000 lines of container logs.

<!-- template-actions:start -->
[![View in Open Flow](../../assets/view-in-openflow.svg)](https://openflow.run/templates/read-immich-container-logs/) [![n8n JSON](../../assets/n8n-json.svg)](templates/read-immich-container-logs.n8n.json)
<!-- template-actions:end -->

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

## Setup

Provide a Docker Engine v1.44 endpoint behind an authenticated HTTPS gateway that permits container inspection and log reads. Set its URL and expected server domain in **Validate server and request**, and set the gateway hostname in the HTTP allowlist of **Read and decode Docker logs**. Bind INSPECTION_WEBHOOK_AUTH to the incoming Authorization header and DOCKER_GATEWAY_TOKEN to the gateway token. In n8n set the same server domain and gateway URL and connect Header Auth credentials on the webhook and Docker HTTP nodes.

## Use

POST server_domain, domain and command set to container_log. The workflow reads stdout and stderr for the container named domain followed by _immich, with tail 1000. Logs may contain secrets and personal data; restrict access to the endpoint and execution history. Docker logging driver must support reading logs.

<details>
<summary>Inspiration &amp; credits</summary>

Extract the log command; use the Docker Engine API and decode its non-TTY stream framing.

Adapted from [puq-docker-immich-deploy](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Code/1966_Code_Webhook_Automation_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Zie619 / n8n-workflows.

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
