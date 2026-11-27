# Receive MQTT Topic Messages

Keep an MQTT subscription open and inspect each incoming message with its original topic.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/receive-mqtt-topic-messages.n8n.json)
<!-- template-actions:end -->

## Setup

1. In **MQTT Trigger**, select an MQTT credential for your broker. Set its protocol, host, port and any required authentication. For a secure broker, use its TLS listener and validate its certificate. [n8n MQTT credentials](https://docs.n8n.io/integrations/builtin/credentials/mqtt/)
2. Enter the **Topics** to subscribe to. Use comma-separated filters without spaces, such as `sensors/+/temperature,alerts/#:1`. The suffix `:1` requests QoS 1 for that filter. A filter without a suffix requests QoS 0. Test by sending a sample publication to an approved test topic, then publish the workflow. [n8n MQTT Trigger](https://docs.n8n.io/integrations/builtin/trigger-nodes/n8n-nodes-base.mqtttrigger/)

## Behavior

While active, the trigger stays subscribed and exposes each matching publication as an execution with `topic` and `message`. The default output decodes the payload as UTF-8 text. Broker settings, the publishing QoS and the session policy determine whether a publication can be redelivered or queued while disconnected. The workflow only listens. It contains no publishing step or downstream action.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

The original single trigger and default text output are preserved. The portable export leaves the broker and topic filters for you to configure.

Adapted from [MQTT Trigger](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Mqtt/0992_Mqtt_Send_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Zie619 / n8n-workflows.

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
