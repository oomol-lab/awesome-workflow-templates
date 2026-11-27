# Create Google Meet Links from Slack

Run /meet in Slack to create a Google Meet space and post the join link in the same conversation.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/create-google-meet-links-from-slack.n8n.json)
<!-- template-actions:end -->

## Setup

1. In the Slack app, add the `/meet` slash command and install the app in your workspace. Give its bot the `chat:write` scope. Invite it to each channel it should post in. For public channels where the bot is not a member, Slack also requires `chat:write.public`. Use that bot token in the Slack API credential on **Post the link to Slack**. [Slack slash commands](https://docs.slack.dev/interactivity/implementing-slash-commands/) · [Slack posting permissions](https://docs.slack.dev/reference/methods/chat.postMessage/)
2. Set the Slack workspace ID in **Verify Slack and select the conversation** and set `SLACK_SIGNING_SECRET` on your self-hosted n8n instance. Allow node environment access only on instances with trusted workflow editors. If you use an n8n external secret store, substitute its secret expression for both environment variable references in **Compute the Slack signature**. [Slack signing secrets](https://docs.slack.dev/authentication/verifying-requests-from-slack/)
3. Enable the Google Meet API in your Google Cloud project. Create a Web application OAuth client, set its redirect URI to the URL n8n shows for the credential, and connect the Google user who will own the meeting spaces. On **Create the Google Meet space**, create an OAuth2 API credential with Authorization Code grant, authorization URL `https://accounts.google.com/o/oauth2/v2/auth`, token URL `https://oauth2.googleapis.com/token`, scope `https://www.googleapis.com/auth/meetings.space.created`, and authentication set to Body. Add `access_type=offline&prompt=consent` in Auth URI Query Parameters for a refresh token. [Google Meet OAuth](https://developers.google.com/workspace/meet/api/guides/authenticate-authorize) · [Google OAuth web server flow](https://developers.google.com/identity/protocols/oauth2/web-server)
4. Activate the workflow. Set the Slack slash command's Request URL to the production HTTPS URL from **Receive the Slack command**.

## Behavior

The workflow verifies Slack’s signature over the original form body and checks that the timestamp is within five minutes. It acknowledges valid commands immediately, before calling Google Meet. The workspace must match your configuration. The Slack message goes to the conversation ID in the signed request and contains the actual Meet join link.

Meet spaces use the connected Google user’s default access policy. Slack channel membership does not grant access to the meeting. Google Meet creates the space directly, so there is no Calendar event or 15-minute appointment. [Google Meet space creation](https://developers.google.com/workspace/meet/api/reference/rest/v2/spaces/create)

If Google Meet fails or returns no usable link, the execution stops before posting. If Slack fails after Google creates the space, the space may already exist. Check the original conversation before running again. The workflow skips deliveries marked as Slack retries and performs no automatic create or post retries. A new command creates a new space.

The workflow disables execution-data saving because signed webhook payloads can contain Slack response URLs and verification tokens. It does not use those values.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

Verify the Slack request and send the acknowledgment before creating the link. Create the Google Meet space directly in place of creating and deleting a temporary Calendar event.

Adapted from [Generate instant Google Meet links with a Slack command](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Googlecalendar/1573_GoogleCalendar_Slack_Create_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Jonathan (original workflow) and Zie619 (collection). See the [original n8n gallery template](https://n8n.io/workflows/2156-generate-instant-google-meet-links-with-a-slack-command/).

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
