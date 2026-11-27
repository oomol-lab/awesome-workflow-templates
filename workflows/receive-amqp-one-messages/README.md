# Receive AMQP 1.0 Messages

Listen for messages on an AMQP 1.0 queue or topic and inspect the original broker message.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/receive-amqp-one-messages.n8n.json)
<!-- template-actions:end -->

## Setup

1. In **AMQP Trigger**, select an AMQP credential with your broker host, port, username and password. For an encrypted listener, set Transport Type to `tls` and use the broker’s TLS port. Check that the listener accepts AMQP 1.0. An AMQP 0-9-1-only listener is incompatible. [n8n AMQP credentials](https://docs.n8n.io/integrations/builtin/credentials/amqp/) · [n8n AMQP Trigger](https://docs.n8n.io/integrations/builtin/trigger-nodes/n8n-nodes-base.amqptrigger/)
2. Enter the broker’s **source address** in **Queue / Topic**. For example, on RabbitMQ 4.x use `/queues/my-queue` for an existing queue. Other brokers use their own source address formats and access rules. Test with a dedicated queue, then publish to listen continuously. [RabbitMQ AMQP 1.0 source addresses](https://www.rabbitmq.com/docs/amqp#source-address-v2)

## Behavior

The trigger exposes the broker message in the execution output, including its body and any supplied message ID or application properties. Its body stays in the format returned by the native decoder. This workflow only listens. It contains no publishing step or downstream action.

The trigger is exported inactive and leaves the connection and source address for you to configure. Use a test queue when checking the output because receiving from a queue consumes its messages.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

The original single trigger and default output are preserved. The portable export omits connection references and run data.

Adapted from [AMQP Trigger](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Amqp/0138_Amqp_Send_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Zie619 / n8n-workflows.

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
