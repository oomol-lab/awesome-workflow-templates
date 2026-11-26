# Look Up ServiceNow Incidents from Slack

Use a Slack slash command to look up a ServiceNow incident and share its details in an approved channel.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/slack-servicenow-incident-lookup.n8n.json)
<!-- template-actions:end -->

## Setup

1. Create a slash command in a Slack app and name it `/incident`. Obtain the app’s signing secret. Supply it to the **Compute the Slack request signature** node through the `SLACK_SIGNING_SECRET` environment variable on your self-hosted n8n instance. Allow node environment access only on a deployment with trusted workflow editors. If you use an n8n external secret store, replace both references to the environment variable in the node’s Secret expression with that secret. [Slack request verification](https://docs.slack.dev/authentication/verifying-requests-from-slack/)
2. In **Verify Slack and approve the incident lookup**, set the Slack workspace ID, approved channel IDs and approved user IDs. Add your ServiceNow instance subdomain. Both allowlists start empty. Use channels authorized to see incident details and caller names.
3. In **Read the matching ServiceNow incident**, connect a ServiceNow Basic Auth credential for that instance with read-only access to the incident fields. Publish the workflow and set the slash command’s Request URL to the production HTTPS webhook shown in **Receive the Slack command**. [ServiceNow Table API](https://www.servicenow.com/docs/r/api-reference/rest-apis/c_TableAPI.html)
4. Run `/incident INC0012345` in an approved channel. If you chose another command name, update it in the verification node.

## Behavior

The workflow verifies Slack’s signature over the original form body and checks the request timestamp. It acknowledges a valid request before it contacts ServiceNow so Slack’s three-second deadline applies only to admission. It then sends the result to the response URL provided by the signed command. The workflow accepts only Slack’s commercial command response host and checks any workspace ID in the response URL. [Slack slash command responses](https://docs.slack.dev/interactivity/implementing-slash-commands/)

A matching incident is shown in the channel with the incident number, description, severity, caller, priority, state, category, opened date and a link to ServiceNow. A missing incident, malformed number or lookup error produces a private reply. The workflow looks up one exact `INC` number and rejects ambiguous results. It ignores requests Slack marks as retries and never retries its own Slack reply automatically.

Keep the signing key and response URL private. Workflow execution data saving is disabled. Restrict access to live execution inspection and avoid production request tracing that records raw webhook bodies or destinations.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [ServiceNow incident lookups from Slack](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Stickynote/0684_Stickynote_Respondtowebhook_Send_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Angel Menendez (djangelic, original workflow) and Zie619 (collection). See the [original n8n gallery template](https://n8n.io/workflows/2727-display-servicenow-incident-details-in-slack-using-slash-commands/).

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

## Changes to the source

The workflow verifies Slack’s signed request and approved workspace, channel and user. It uses a fast acknowledgment and a separate Slack response for the exact incident lookup. The successful result remains visible in the channel and error messages stay private.

</details>
