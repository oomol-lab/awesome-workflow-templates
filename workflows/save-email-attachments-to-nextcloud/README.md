# Save Email Attachments to Nextcloud

Archive attachments received in an IMAP folder to a Nextcloud folder.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/save-email-attachments-to-nextcloud.n8n.json)
<!-- template-actions:end -->

## Setup

1. Import the JSON into n8n. In **Watch the invoices mailbox**, select an IMAP credential and enter the folder to monitor. The default is `Invoices`.
2. In **Upload to Nextcloud**, select a Nextcloud API credential with your username, app password and WebDAV URL such as `https://cloud.example.com/remote.php/webdav`. Create a destination folder and edit the path prefix if you use a folder other than `Documents/Invoices/`. Use a dedicated destination per IMAP folder.
3. Activate the workflow. The trigger searches all matching mail in the chosen folder when it checks for new arrivals. Start with a dedicated mailbox folder if you want to control which existing messages it can see.

## Behavior

Each attachment is uploaded as its own file. Names include the email's UTC date, the sender, the attachment filename, the IMAP message UID and the attachment number. The sender and attachment filename are sanitized for the destination path. A message with no attachments creates no file. The trigger marks fetched messages as read before upload.

An upload error stops the execution. Check the execution and destination folder before retrying, since uploads that completed before the error may already be present. A replay of the same email with its original attachment order uses the same paths and replaces any existing files at those paths. Choose a fresh destination if the monitored mailbox is recreated or its IMAP UIDs are reset. [Nextcloud WebDAV uploads](https://docs.nextcloud.com/server/stable/developer_manual/client_apis/WebDAV/basic.html#uploading-files).

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Replace the Function node and its Lodash dependency with a Code node that preserves each binary attachment and adds the message UID and attachment number to the filename.
- Use the native resolved IMAP trigger with UID tracking and explicit Nextcloud binary upload settings.

Adapted from [IMAP attachment archive to Nextcloud](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Emailreadimap/0134_Emailreadimap_Nextcloud_Send.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Zie619 / n8n-workflows.

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
