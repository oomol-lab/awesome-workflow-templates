# Awesome Workflow Templates

[![Awesome](https://awesome.re/badge.svg)](https://github.com/sindresorhus/awesome)
[![n8n workflows](https://img.shields.io/badge/n8n-workflows-EA4B71?logo=n8n&logoColor=white)](#contents)
[![Open Flow workflows](https://img.shields.io/badge/Open_Flow-workflows-356DF3)](https://openflow.run/templates/)
[![Star on GitHub](https://img.shields.io/badge/GitHub-Star_this_repo-181717?logo=github)](https://github.com/oomol-lab/awesome-workflow-templates)

**Handpicked workflow templates and AI automations for n8n and Open Flow.**

A growing collection of automation workflows for connecting apps and getting repetitive work done. We review the logic, fix issues we find, and maintain matching **n8n** and **[Open Flow](https://openflow.run/templates/)** versions.

**[Star this repo](https://github.com/oomol-lab/awesome-workflow-templates) for new workflows and improvements to the ones you already use.**

[Browse all workflows](#contents) · [Browse online](https://openflow.run/templates/) · [Suggest a workflow](https://github.com/oomol-lab/awesome-workflow-templates/issues/new)

## Contents

- [Sales](#sales)
- [Operations](#operations)
- [Marketing](#marketing)
- [Support](#support)
- [Development](#development)
- [Contribute](#contribute)
- [Licensing](#licensing)

## Sales

- [Website Lead Capture](workflows/website-lead-capture/) - Save website enquiries to Google Sheets, alert your team on Telegram, and send a Gmail reply.
- [Client Onboarding](workflows/client-onboarding/) - Welcome a new client by Gmail, record their project in Google Sheets, and return the client ID to your form or CRM.

## Operations

- [Unread Email Digest](workflows/unread-email-digest/) - Summarize unread Gmail messages with AI and send a prioritized weekday morning digest to Telegram.
- [Invoice Payment Reminders](workflows/invoice-payment-reminders/) - Email Italian payment reminders for unpaid invoices that are overdue or due within three days, every weekday morning.
- [Event Feedback Report](workflows/event-feedback-report/) - Summarize Google Sheets event feedback into an AI report covering sentiment and improvement ideas, and email it with Gmail.
- [Morning Brief to LINE](workflows/morning-brief-to-line/) - Turn your configured daily tasks into a concise AI morning brief and send it to LINE at 08:00.
- [Transport Request Intake](workflows/transport-request-intake/) - Normalize a transport request and return missing fields, readiness status, and a JSON request with numeric weight.
- [GitHub Release Slack Alerts](workflows/github-release-slack-alerts/) - Check configured GitHub repositories daily and notify Slack when their latest release was published within the last 24 hours.
- [Calendar Event Creator](workflows/calendar-event-creator/) - Create one Google Calendar event with the calendar, title, and start/end times you configure.
- [Google Task Creator](workflows/google-task-creator/) - Create one Google Tasks item in the task list you select.
- [Todoist Task Creator](workflows/todoist-task-creator/) - Create one Todoist task in the project you select.
- [Trello Card Creator](workflows/trello-card-creator/) - Create one Trello card with a name and description in the list you select.
- [Coda Table Row Creator](workflows/coda-table-row-creator/) - Submit one new Coda table row containing three configured column values.
- [Gmail Label Switcher](workflows/gmail-label-switcher/) - Move a batch of Gmail messages from one label to another.

## Marketing

- [GitHub & Dev.to Engagement](workflows/github-devto-engagement-monitor/) - Collect GitHub stars, forks and open issues alongside Dev.to reactions and comments every 12 hours.
- [Airtable Tweet Drafts](workflows/airtable-tweet-drafts/) - Generate a tweet draft for a randomly selected hashtag and save the draft and hashtag in Airtable for review.
- [AI Content to Slack](workflows/ai-content-to-slack/) - Generate a blog, newsletter, or social posts from a webhook request, notify Slack, and return the complete draft as JSON.
- [Blog Writing Pipeline](workflows/blog-writing-pipeline/) - Generate research notes, an outline, a Markdown blog draft, and an edited post with four separate model steps.
- [Social Content Review](workflows/social-content-review/) - Generate X, LinkedIn, Reddit, and Instagram drafts, review them with a second model call, and return the complete content set.
- [Article to Social Posts](workflows/article-to-social-posts/) - Repurpose your article or transcript into an X thread and LinkedIn post while instructing the model to use only source material.

## Support

- [Phone Call Log](workflows/phone-call-log/) - Record caller details, duration, supplied summary, and the first 500 transcript characters in Google Sheets from a webhook.
- [Webhook Request Classifier](workflows/webhook-request-classifier/) - Classify an incoming request as support, sales, technical, or general and return its priority and summary as JSON.
- [Customer Feedback Sentiment](workflows/customer-feedback-sentiment/) - Classify submitted customer feedback with AI and save the feedback, contact information, and sentiment in Google Sheets.

## Development

- [n8n Execution Diagnostics](workflows/n8n-execution-diagnostics/) - Classify structured n8n execution errors and return affected nodes, error counts, and suggested investigation steps.
- [n8n Silent Workflow Check](workflows/n8n-silent-workflow-check/) - Check active n8n workflows for missing or stale executions and return a report with the inspected page limits.

## Contribute

Share a workflow that saves you time. [Suggest a template](https://github.com/oomol-lab/awesome-workflow-templates/issues/new) or [open a pull request](https://github.com/oomol-lab/awesome-workflow-templates/compare).

## Licensing

Original OOMOL contributions to this collection are licensed under [CC BY 4.0](LICENSE).

Third-party material retains its original licenses. See each workflow's README for source attribution, available license information, and our changes.
