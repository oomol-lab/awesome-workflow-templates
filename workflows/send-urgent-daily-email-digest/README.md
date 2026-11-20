# Send an Urgent Daily Email Digest

Summarize the past day of email and notify when a thread needs action.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/send-urgent-daily-email-digest.n8n.json)
<!-- template-actions:end -->

## Setup

Set NODE_FUNCTION_ALLOW_EXTERNAL=mailparser in that runner and install mailparser there. Configure IMAP, Telegram and ntfy credentials. Set a unique mailbox key and prevent concurrent runs.

## Behavior

A manual run or daily 23:59 UTC schedule reads INBOX from the preceding 24 hours without marking messages read. It groups references or subjects, mutes common promotional threads and summarizes the remainder. If the model fails or returns invalid JSON, heuristic fallback is used. Only urgent items produce a Telegram notification. ntfy is used only after a confirmed Telegram rejection. Review model judgments. Email contents are sent to the configured model.

A pending notification may have succeeded. An oversized input or an IMAP list reaching its configured limit stops rather than silently omitting messages.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Daily Email Notification](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/Gmail_and_Email_Automation/Daily%20Email%20Notification.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
