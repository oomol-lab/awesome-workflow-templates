# Reply to Unread Meeting Requests with Availability

Identify appointment requests, check calendar availability and reply with suggested times.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/reply-to-unread-meeting-requests-with-availability.n8n.json)
<!-- template-actions:end -->

## Setup

Connect Gmail, Google Calendar and an AI model. Configure the calendar. Prevent overlapping runs for the same message.

## Behavior

Unread email is classified by subject and snippet. Appointment requests use confirmed timed events from all calendar pages, from one day ago through one month ahead, to suggest a specific time with a 15-minute buffer after prior events. All-day events are excluded, as in the source, so check them separately before accepting a suggestion. The workflow replies to the original email and marks it read after the reply is confirmed. Other messages are left unread. It does not create calendar events. Review suggested times: model output may be wrong, and the workflow does not reserve a slot. Email content and calendar data are sent to the model; protect execution history.

If a reply or mark-read outcome is unknown, inspect Gmail before replaying.

<details>
<summary>Inspiration &amp; credits</summary>

Preserve each message identity, check every calendar page and mark read after the reply succeeds.

Adapted from [Email appointment scheduling assistant](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Googlecalendar/1668_GoogleCalendar_Filter_Automation_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
