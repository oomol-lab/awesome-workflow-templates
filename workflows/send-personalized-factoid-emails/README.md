# Send Personalized Factoid Emails

Manage subscribers and send illustrated facts about their chosen topics.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/send-personalized-factoid-emails.n8n.json)
<!-- template-actions:end -->

## Setup

Create an Airtable table with Email, Topic, Status, Interval, Start Day and Last Sent fields. Status uses active and inactive; Interval uses daily, weekly and surprise. Connect Airtable, Gmail and OpenAI. Set the Airtable base and table IDs in **Save subscriber and confirm**, **Deactivate subscriber**, **List active subscribers** and **Record Last Sent**.

Configure **Subscribe Form** and **Unsubscribe Form**, and set each **Choose...

## Behavior

A subscription saves the email, topic and requested daily, weekly or surprise schedule and sends a confirmation. Unsubscribe marks the given record inactive. Each day at 09:00 UTC the workflow checks active subscriptions. Daily subscribers are selected daily, weekly subscribers when no prior send exists or seven days have elapsed, and surprise subscribers with a one-in-ten chance each day. It searches Wikipedia, asks Groq for a fact avoiding the last five facts for that subscriber, creates an illustration, resizes it to 480×360 and emails both. A successful send is followed by an Airtable Last Sent update.

Earlier writes may have succeeded. The source uses publicly reachable forms without authentication; restrict access to trusted callers. Workflow state and execution history can contain subscriber information.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Correct the surprise interval, use the actual send time and remove the original copied recipient and private Airtable IDs.

Adapted from [Learn something every day](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Code/0658_Code_Schedule_Create_Scheduled.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
