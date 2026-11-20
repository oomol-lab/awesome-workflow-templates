# Qualify and Approve Appointment Requests

Qualify an enquiry, request an administrator decision and create an appointment or send a rejection.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/qualify-and-approve-appointment-requests.n8n.json)
<!-- template-actions:end -->

## Setup and use

Connect its OpenAI and Gmail credentials, set the administrator email and calendar, and configure the form and terms for your use.

## Behavior

The form qualifies the enquiry, collects terms acceptance and a requested time, and emails an acknowledgement. A separate Gmail approval waits for an administrator. Approval creates a 30-minute calendar event with the requester and a Google Meet request; rejection emails the requester. It does not authenticate callers; restrict access to trusted senders. Review available dates and possible conflicts before approving; the workflow does not check availability.

Enquiries are shared with the model. A lost email or calendar response may represent a completed write; inspect the relevant account before retrying.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Qualifying Appointment Requests with AI & n8n Forms](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/Forms_and_Surveys/Qualifying%20Appointment%20Requests%20with%20AI%20%26%20n8n%20Forms.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source notes link to [Jim Le](https://www.linkedin.com/in/jimleuk/) and his [showcase](https://community.n8n.io/). No separate original template license was identified. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
