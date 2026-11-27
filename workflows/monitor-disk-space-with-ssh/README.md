# Monitor Disk Space with SSH

Check one remote host every 30 minutes and send disk usage changes to Telegram, with email as a fallback.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/monitor-disk-space-with-ssh.n8n.json)
<!-- template-actions:end -->

## Setup

1. Connect an SSH credential for the host you administer in **Read remote disk usage**. Set the authentication method to match the credential. The host must return the English POSIX table for `df -P`. [SSH credentials](https://docs.n8n.io/integrations/builtin/credentials/ssh/)
2. Set the Telegram bot credential and chat ID in **Send the Telegram alert**. In **Email the same alert**, set the SMTP credential, sender and fallback recipient.
3. Adjust the percentage thresholds at the top of **Evaluate disk thresholds** if needed. Defaults are 80% for warning and 90% for critical. Publish and activate one workflow per host. Keep runs for that host serial so each run sees the last delivered level. The schedule runs on the half hour in UTC.

## Behavior

The workflow runs `df -P` over SSH. Each mount is checked independently. It alerts when usage enters warning or critical, moves between those levels, or returns below warning. A mount that stays at the same level produces no new alert. A failed command or invalid table fails the run and preserves prior levels.

Telegram displays the combined alert as text. If Telegram reports an error, SMTP sends the same text. A lost Telegram response can cause both channels to deliver. A failed fallback leaves the previous state eligible for the next scheduled check.

The workflow saves severity levels after a successful scheduled execution. Manual tests do not persist them. Review the execution history to monitor failed checks. [Workflow static data](https://docs.n8n.io/code/cookbook/builtin/get-workflow-static-data/)

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Disk space watchdog with tiered thresholds and Telegram alert](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/devops/disk-space-watchdog.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

This adaptation adds exit-code and table validation, keeps mount names with spaces intact, and passes the original alert text to the SMTP branch.

</details>
