# Receive New IMAP Email

Listen for incoming mail in an IMAP mailbox and expose each unread message with its headers and text bodies.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/receive-imap-inbox-mail.n8n.json)
<!-- template-actions:end -->

## Setup

1. Import the workflow and select an IMAP credential in **Email Trigger (IMAP)**. Use the mailbox provider's hostname, port, and password or app password. Enable SSL/TLS and keep certificate validation on. [IMAP credentials](https://docs.n8n.io/integrations/builtin/credentials/imap/)
2. Leave **Mailbox Name** as `INBOX` or enter the exact folder name to watch. Activate the workflow and deliver a test message to a mailbox where you can safely mark messages as read. Inspect the trigger output in the execution. [Email Trigger (IMAP)](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.emailimap/)

## Behavior

While active, the trigger keeps an IMAP connection open. When the server reports new mail, it checks for unread messages. A delivery notification can collect several unread messages, including unread messages already in the folder. Each is a separate item within the execution.

The default **Simple** format exposes `textPlain`, `textHtml`, common fields such as `from` and `subject`, and other headers in `metadata`. Attachment files are omitted from the output by default. The trigger marks the fetched messages as read after retrieval, then emits the message items. This workflow only receives mail and has no downstream steps.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

The portable export keeps the single IMAP trigger and its original defaults. It leaves account details for you to configure.

Adapted from [IMAP Email Trigger](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Emailreadimap/1050_Emailreadimap_Send.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Zie619 / n8n-workflows.

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
