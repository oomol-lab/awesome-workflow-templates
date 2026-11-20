# Review Meeting Follow-up Suggestions

Find meetings without subsequent email, suggest available slots and book only after a human response.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/review-meeting-follow-up-suggestions.n8n.json)
<!-- template-actions:end -->

## Setup

Connect Google Calendar and Gmail and configure the calendar ID in **Set meeting window**, **Check whether follow-up is needed**, **Reserve approval request** and **Reserve calendar action**. Configure Gmail, Calendar, the AI model, the administrator address and timezone. Prevent overlapping executions.

## Behavior

At 06:00 UTC each day the workflow examines meetings from two to four days earlier; adjust the schedule and timezone for your calendar. It checks the first non-self attendee for later email and suggests available weekday slots when no thread is found. An administrator replies to the approval email. Only an explicit request with a start and end creates a calendar event; a dismissal creates nothing. Review model interpretations and ambiguous requests. The event does not invite attendees, matching the source.

For an uncertain approval request, enter its exact pending key and confirmed or absent in **Set meeting window**, run the schedule, then clear the fields. If the meeting is outside the search window, arrange any absent request manually. For an uncertain calendar creation, inspect Calendar, enter its pending key and confirmed or absent in **Reserve calendar action**, replay the same decision, then clear the fields. Mark it done only if the action happened, or delete it only if absent. Approval remains pending while waiting for the administrator. If the waiting execution was lost, obtain the decision and complete the remaining action manually.

<details>
<summary>Inspiration &amp; credits</summary>

Correct the empty-email filter, preserve human approval before booking and use the Calendar API response to retain the attendee self flag.

Adapted from [Meeting follow-up suggestions](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Googlecalendar/0783_GoogleCalendar_Schedule_Create_Scheduled.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
