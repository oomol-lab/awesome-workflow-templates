# Back Up Zigbee2MQTT to SFTP

Request a weekly Zigbee2MQTT backup and save the resulting ZIP on an SFTP server.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/back-up-zigbee2mqtt-to-sftp.n8n.json)
<!-- template-actions:end -->

## Setup

1. Select MQTT credentials for the same broker in **Request a Zigbee2MQTT backup** and **Receive backup responses**. Leave the client ID blank so the two connections get separate IDs. Grant the publisher access to `zigbee2mqtt/bridge/request/backup` and the subscriber access to `zigbee2mqtt/bridge/response/backup`. Use a trusted broker with a private connection or TLS.
2. In **Upload the ZIP to SFTP**, select an SFTP credential with permission to write to the remote backup folder. The default folder is `zigbee_backups`. To change it, edit `backupDirectory` in **Validate the ZIP and choose its destination**. Limit access to the folder because backups can contain Zigbee network credentials.
3. Activate the workflow so MQTT listens continuously. The schedule defaults to Monday at 02:45 UTC. Set the workflow time zone if you want Monday at 02:45 local time. If your Zigbee2MQTT instance uses a custom base topic, change both MQTT nodes and the expected response topic in **Validate the ZIP and choose its destination**. [Zigbee2MQTT backup topics](https://www.zigbee2mqtt.io/guide/usage/mqtt_topics_and_messages.html#zigbee2mqtt-bridge-request-backup)

## Behavior

The schedule sends an empty, non-retained backup request at MQTT QoS 0. The independent listener also uses QoS 0 and accepts successful responses from its configured topic, including responses requested by another authorized client. Use non-retained responses. The listener must be connected when the broker delivers the response.

A successful response with a complete ZIP is uploaded unchanged. The filename starts with `zigbee_backup_` and includes the UTC receive time and workflow execution ID. An error response, invalid Base64 or incomplete ZIP stops before SFTP. The workflow disables saving execution data. If SFTP reports an error, check the destination before repeating the backup request.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

Use the empty backup request documented by current Zigbee2MQTT. Validate the reply before writing and include the execution ID in the filename to distinguish simultaneous arrivals.

Adapted from [Weekly Zigbee2MQTT backups to SFTP](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Code/0553_Code_Schedule_Send_Scheduled.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Zie619 / n8n-workflows.

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
