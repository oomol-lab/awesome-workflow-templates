# Draft Fastmail Replies from IMAP

Draft a reply to each eligible unread IMAP email with OpenAI and save it in Fastmail for review.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/draft-fastmail-replies-from-imap.n8n.json)
<!-- template-actions:end -->

## Setup

1. In **Watch the IMAP inbox**, select an IMAP credential and the folder to watch. In **Set the inbox and Fastmail account**, set `sourceAccount` to a stable label for that IMAP login and `fastmailUser` to the Fastmail login address that will own the drafts. Bind an OpenAI credential to **Write the reply**.
2. Create a Fastmail JMAP API token with the **Email** scope. Leave **Email submission** unchecked. In n8n, create one Header Auth credential named `Authorization` with the value `Bearer YOUR_TOKEN`. Attach it to **Read the Fastmail session**, **Find the Drafts mailbox**, and **Create the Fastmail draft**. [Fastmail API tokens](https://www.fastmail.help/hc/en-us/articles/5254602856719-API-tokens)
3. Use one production execution slot and a dedicated Data Table with text columns `request_key`, `status`, and `receipt`. Select it in **Look for a draft attempt**, **Reserve the draft attempt**, and **Record the draft ID**. Activate the workflow after configuring the accounts and table.

## Behavior

The IMAP trigger may include unread messages from the day you activate it. It leaves their read status unchanged. The workflow uses the original Reply-To when present, or the From address otherwise. It skips ambiguous addresses and messages without a usable Message-ID or text body. OpenAI receives the subject and body. Use authorized mailboxes and review the output before sending it yourself.

Fastmail saves the reply in the verified account's Drafts mailbox with the original message ID as its reply reference. The draft uses the Fastmail login address and the original subject with a single `Re:` prefix. The workflow handles messages one at a time and creates drafts only.

The table keeps one draft attempt per IMAP account, folder, and UID for the selected Fastmail account. Keep the account label and table stable. If your IMAP server rebuilds a folder or reports a new UIDVALIDITY, pause the workflow, reconcile pending attempts in Fastmail, and use a new workflow instance and Data Table for that folder. Retain the previous table for reconciliation. The trigger does not expose UIDVALIDITY.

If Fastmail does not confirm the draft ID, inspect Drafts before recovering the pending attempt. A regular replay skips that attempt. Retrying directly at **Create the Fastmail draft** bypasses the attempt check.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Create e-mail responses with Fastmail and OpenAI](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/Gmail_and_Email_Automation/create%20e-mail%20responses%20with%20fastmail%20and%20OpenAI.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The original workflow is credited to Vitali. The collection notice does not establish a separate license for the original workflow. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

[Original n8n workflow by Vitali](https://n8n.io/workflows/2441-create-e-mail-responses-with-fastmail-and-openai/).

## Changes to the source

Use the authenticated JMAP session's API URL, select one writable Drafts mailbox, and serialize the entire request as JSON. Keep the source email and reply address paired across a batch. Reserve each attempt before asking Fastmail to create a draft.

</details>
