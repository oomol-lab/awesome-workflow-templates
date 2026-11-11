# Awesome Workflow Templates

[![Awesome](https://awesome.re/badge.svg)](https://github.com/sindresorhus/awesome)
[![n8n workflows](https://img.shields.io/badge/n8n-workflows-EA4B71?logo=n8n&logoColor=white)](#contents)
[![Open Flow workflows](https://img.shields.io/badge/Open_Flow-workflows-F0F0F0.svg?logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAxMDAgMTAwIj48cGF0aCBmaWxsPSIjZTBlMmU2IiBkPSJNMzIgMTZINjhRODQgMTYgODQgMzJWMzZINjhDNDYgMzYgNTQgNTYgMzIgNTZIMTZWMzJRMTYgMTYgMzIgMTZaIi8%2BPHBhdGggZmlsbD0iIzhjOTE5YSIgZD0iTTE2IDY4SDMyQzU0IDY4IDQ2IDQ4IDY4IDQ4SDg0VjY4UTg0IDg0IDY4IDg0SDMyUTE2IDg0IDE2IDY4WiIvPjwvc3ZnPg%3D%3D)](https://openflow.run/templates/)
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
- [Research](#research)
- [Productivity](#productivity)
- [Content](#content)
- [Commerce](#commerce)
- [Utilities](#utilities)
- [Analytics](#analytics)
- [Lifestyle](#lifestyle)
- [Developer Tools](#developer-tools)
- [Communication](#communication)
- [Customer Support](#customer-support)
- [Finance](#finance)
- [Community](#community)
- [Content Creation](#content-creation)
- [Recruiting](#recruiting)
- [Content Review](#content-review)
- [Recruitment](#recruitment)
- [Data Sync](#data-sync)
- [Data Enrichment](#data-enrichment)
- [Contribute](#contribute)
- [Licensing](#licensing)

## Sales

- [Website Lead Capture](workflows/website-lead-capture/) - Save website enquiries to Google Sheets, alert your team on Telegram, and send a Gmail reply.
- [Client Onboarding](workflows/client-onboarding/) - Welcome a new client by Gmail, record their project in Google Sheets, and return the client ID to your form or CRM.
- [Pipedrive Deal Creator](workflows/pipedrive-deal-creator/) - Create one Pipedrive deal with a configured title using API v2.
- [Chargebee Customer Creator](workflows/chargebee-customer-creator/) - Create a Chargebee customer with a configured first and last name.
- [Salesmate Company Creator](workflows/salesmate-company-creator/) - Create a Salesmate company with a name and an existing owner.
- [Affinity Organization Creator](workflows/affinity-organization-creator/) - Create an Affinity organization with a name and domain.
- [Hunter Email Verifier](workflows/hunter-email-verifier/) - Request a Hunter deliverability assessment for one email address.
- [Keap Contact Reader](workflows/keap-contact-reader/) - Read the first Keap contacts page with the source limit of 100.
- [Calendly Booking to Mautic Contact](workflows/calendly-booking-to-mautic-contact/) - Create a Mautic contact or update its name when an invitee books a Calendly meeting.
- [Calendly Booking to Notion](workflows/calendly-booking-to-notion/) - Add each new Calendly booking to Notion with the invitee name, email and a configured status.
- [WooCommerce Customer to Mautic](workflows/woocommerce-customer-to-mautic/) - Create a missing Mautic contact or update its name when a WooCommerce customer changes.
- [LeadPilot Cold Email Drafts](workflows/leadpilot-cold-email-drafts/) - Write personalized cold-email and follow-up drafts for every supplied lead, then save the complete batch in Google Sheets for review.
- [Sheet Contacts through Dropcontact to Lemlist](workflows/sheet-contacts-dropcontact-lemlist/) - Read a sheet contact batch, enrich it with French company information, wait 45 seconds and create every returned contact as a Lemlist campaign lead.
- [Google Sheets Community Lead Rating](workflows/google-sheets-community-lead-rating/) - Rate newly appended community applications using the original responsibility and email-domain criteria, then update only the matching Timestamp row’s Rating.

## Operations

- [Unread Email Digest](workflows/unread-email-digest/) - Summarize unread Gmail messages with AI and send a prioritized weekday morning digest to Telegram.
- [Invoice Payment Reminders](workflows/invoice-payment-reminders/) - Email Italian payment reminders for unpaid invoices that are overdue or due within three days, every weekday morning.
- [Event Feedback Report](workflows/event-feedback-report/) - Summarize Google Sheets event feedback into an AI report covering sentiment and improvement ideas, and email it with Gmail.
- [Morning Brief to LINE](workflows/morning-brief-to-line/) - Turn your configured daily tasks into a concise AI morning brief and send it to LINE at 08:00.
- [Transport Request Intake](workflows/transport-request-intake/) - Normalize a transport request and return missing fields, readiness status, and a JSON request with numeric weight.
- [GitHub Release Slack Alerts](workflows/github-release-slack-alerts/) - Check configured GitHub repositories daily and notify Slack when their latest release was published within the last 24 hours.
- [Calendar Event Creator](workflows/calendar-event-creator/) - Create one Google Calendar event with the calendar, title, and start/end times you configure.
- [Google Task Creator](workflows/google-task-creator/) - Create one Google Tasks item in the task list you select.
- [Trello Card Creator](workflows/trello-card-creator/) - Create one Trello card with a name and description in the list you select.
- [Coda Table Row Creator](workflows/coda-table-row-creator/) - Submit one new Coda table row containing three configured column values.
- [Gmail Label Switcher](workflows/gmail-label-switcher/) - Move a batch of Gmail messages from one label to another.
- [Dropbox Public Image Archive](workflows/dropbox-public-image-archive/) - Create a Dropbox folder, save a public image into it, and list the folder after the file is saved.
- [Bitcoin Price Alert](workflows/bitcoin-price-alert/) - Check CoinPaprika every 15 minutes and send a Telegram alert when Bitcoin’s 24-hour USD change reaches +5% or −5%.
- [Exact-Match Quote Guard](workflows/exact-match-quote-guard/) - Validate extracted line items against a synthetic example catalog and return a calculated quote, review request, or rejection.
- [Communication Record Extractor](workflows/communication-record-extractor/) - Extract a communication record from supplied text, validate its fields, and allow one model correction when the output format is invalid.
- [JSON Feed Telegram Alert](workflows/json-feed-telegram-alert/) - Poll a JSON feed every five minutes and send matching new entries to Telegram, keeping a timestamp watermark after successful delivery.
- [Negative Feedback Alert](workflows/negative-feedback-alert/) - Analyze a Typeform feedback submission and post its text and score to Mattermost only when the score is negative.
- [Feedback Sentiment Routing](workflows/feedback-sentiment-routing/) - Save positive Typeform feedback in Notion and notify Slack, or create a Trello card for neutral and negative feedback.
- [Form Testimonial Capture](workflows/form-testimonial-capture/) - Analyze submitted feedback and create a Strapi entry only when its sentiment score is greater than 0.4.
- [Live Tennis Discord Alert](workflows/live-tennis-discord-alert/) - Check the first page of live tennis matches every five minutes and announce previously unseen match IDs in Discord.
- [Telegram Spotify Player](workflows/telegram-spotify-player/) - Turn a Telegram song description into a Spotify search, queue the first match, request next/resume playback and reply with the observed player status.
- [Resilient API Record Validator](workflows/resilient-api-record-validator/) - Fetch public JSON records with bounded retries, normalize names and emails, and report missing fields or a safe failure record.

## Marketing

- [GitHub & Dev.to Engagement](workflows/github-devto-engagement-monitor/) - Collect GitHub stars, forks and open issues alongside Dev.to reactions and comments every 12 hours.
- [Airtable Tweet Drafts](workflows/airtable-tweet-drafts/) - Generate a tweet draft for a randomly selected hashtag and save the draft and hashtag in Airtable for review.
- [AI Content to Slack](workflows/ai-content-to-slack/) - Generate a blog, newsletter, or social posts from a webhook request, notify Slack, and return the complete draft as JSON.
- [Blog Writing Pipeline](workflows/blog-writing-pipeline/) - Generate research notes, an outline, a Markdown blog draft, and an edited post with four separate model steps.
- [Social Content Review](workflows/social-content-review/) - Generate X, LinkedIn, Reddit, and Instagram drafts, review them with a second model call, and return the complete content set.
- [Article to Social Posts](workflows/article-to-social-posts/) - Repurpose your article or transcript into an X thread and LinkedIn post while instructing the model to use only source material.
- [Airtable SMS Broadcast](workflows/airtable-sms-broadcast/) - Read Airtable contacts and send each one a personalized SMS through Twilio.
- [Reddit Trend Log](workflows/reddit-trend-log/) - Rank a subreddit’s hot posts, ask AI for trends and content ideas, and record one daily analysis row in Google Sheets.
- [SEO Seed Keywords](workflows/seo-seed-keywords/) - Generate 15–20 SEO seed keywords from a B2B software customer profile, including its pain points, goals, and current solutions.
- [X Search Digest](workflows/x-search-digest/) - Search X once through Xquik and return normalized posts, a readable digest, and pagination information.
- [Typeform to Demio Registration](workflows/typeform-demio-registration/) - Register a Typeform respondent for a configured Demio event using their name and email.
- [WordPress Post Categorizer](workflows/wordpress-post-categorizer/) - Read WordPress post pages, classify every title into one configured category, validate the complete batch and replace each post’s category assignment.
- [ActiveCampaign Contact Upsert](workflows/activecampaign-contact-upsert/) - Create or update an ActiveCampaign contact by email with a first and last name.
- [Mailchimp Member Creator](workflows/mailchimp-member-creator/) - Add a subscribed Mailchimp audience member with an email address and first name.
- [Newsletter Unsubscribe](workflows/newsletter-unsubscribe/) - Mark one newsletter subscriber inactive in Airtable and confirm the update, using a record ID supplied through a form or JSON request.
- [Four Platform Content Repurposer](workflows/four-platform-content-repurposer/) - Analyze supplied content, write separate X, LinkedIn, Instagram and Facebook drafts, and log one complete set in Google Sheets.
- [Newsletter Subscriber Enrollment](workflows/newsletter-subscriber-enrollment/) - Create or reactivate an Airtable newsletter subscription by email, then send a plain-text Gmail confirmation.
- [Mautic Contact Reader](workflows/mautic-contact-reader/) - Read the first 30 contact records from a Mautic instance.
- [SERPBear Ranking Report](workflows/serpbear-ranking-report/) - Analyze one domain’s tracked SERPBear keyword rankings and save a dated SEO report in Baserow.
- [Bannerbear Template Image](workflows/bannerbear-template-image/) - Render a Bannerbear template with layer changes and return the completed image.
- [Umami Weekly SEO Report](workflows/umami-weekly-seo-report/) - Summarize self-hosted Umami traffic, compare two rolling weeks of page visitors, and save both analyses in one Baserow row.
- [Classify Software Keywords in Google Sheets](workflows/classify-software-keywords-in-google-sheets/) - Classify every keyword as containing a known IT software or service name, wait five seconds per six-row batch and update only matching Service? cells by Number.
- [Create and Update a WordPress Draft](workflows/create-and-update-wordpress-draft/) - Create a WordPress draft with a title, then update that same post with content.

## Support

- [Phone Call Log](workflows/phone-call-log/) - Record caller details, duration, supplied summary, and the first 500 transcript characters in Google Sheets from a webhook.
- [Webhook Request Classifier](workflows/webhook-request-classifier/) - Classify an incoming request as support, sales, technical, or general and return its priority and summary as JSON.
- [Customer Feedback Sentiment](workflows/customer-feedback-sentiment/) - Classify submitted customer feedback with AI and save the feedback, contact information, and sentiment in Google Sheets.
- [Discord Feedback Router](workflows/discord-feedback-router/) - Classify one feedback message and send its department instruction to the configured customer-success, IT, or support channel in Discord.
- [Zendesk Ticket Creator](workflows/zendesk-ticket-creator/) - Create one Zendesk support ticket with a subject and initial comment.
- [Human Support Escalation](workflows/human-support-escalation/) - Check a support request for an email address and notify a Slack support channel, or return a prompt asking for contact details.
- [Help Scout Inbox Reader](workflows/helpscout-inbox-reader/) - Read up to 50 Help Scout inboxes with their complete properties.

## Development

- [n8n Execution Diagnostics](workflows/n8n-execution-diagnostics/) - Classify structured n8n execution errors and return affected nodes, error counts, and suggested investigation steps.
- [n8n Silent Workflow Check](workflows/n8n-silent-workflow-check/) - Check active n8n workflows for missing or stale executions and return a report with the inspected page limits.
- [GitHub Issues to Telegram](workflows/github-low-comment-issues-telegram/) - Notify Telegram about recently updated open Bug issues with fewer than five comments.
- [Output Completion Check](workflows/output-completion-check/) - Check a completed-record batch for distinct nonempty IDs, invalid records, duplicates, and a configured minimum count.
- [GitHub Star Alerts in Slack](workflows/github-star-slack-alert/) - Post Slack alerts when a repository gains or loses a GitHub star.
- [PagerDuty Incident Create and Update](workflows/pagerduty-incident-create-and-update/) - Create a PagerDuty incident, change its title and retrieve the same incident.

## Research

- [Domain Filtered Research](workflows/domain-filtered-research/) - Ask Perplexity a research question with domain and one-month publication filters, and return the answer with citation URLs.
- [Web Search Results](workflows/web-search-results/) - Run one Tavily web search and return up to five ranked results with a title, URL and snippet.
- [Hacker News Popular Items](workflows/hacker-news-popular-items/) - Export up to fifty popular Hacker News search items as one JSON snapshot, with titles, points, URLs, timestamps and authors.

## Productivity

- [Shortcut Text Transformer](workflows/shortcut-text-transformer/) - Translate, correct grammar, shorten, or expand text from an Apple Shortcut and return the result as plain text.
- [Telegram Journal Reminder](workflows/telegram-journal-reminder/) - Send a daily Telegram journal prompt containing yesterday’s UTC date.
- [Telegram Weather Reply](workflows/telegram-weather-reply/) - Reply to each Telegram message with the current weather in a configured city.
- [Todoist to Notion Sync](workflows/todoist-to-notion-sync/) - Create Notion rows for labeled Todoist tasks, then add each Notion link to its task and replace the routing label.
- [Glasp Highlight Export](workflows/glasp-highlight-export/) - Collect new Glasp highlight documents every six hours, format text and Markdown, and track exported document IDs for 30 days.
- [Hacker News Yearly Lookback](workflows/hacker-news-yearly-lookback/) - Read the Hacker News front page for this UTC calendar day across past years, summarize selected headlines, and send one Telegram message.
- [ClickUp Task Creator](workflows/clickup-task-creator/) - Create one ClickUp task in a configured list and return its complete record.
- [Harvest Client Creator](workflows/harvest-client-creator/) - Create a Harvest client with a configured name and return its complete record.
- [Confluence Knowledge Search](workflows/confluence-knowledge-search/) - Search Confluence for supplied text and return the first result’s title, article link, and excerpt.
- [Google Sheet Record Lookup](workflows/google-sheet-record-lookup/) - List a Google Sheet’s columns, read one column with row numbers, or retrieve a record by its physical row number.
- [Box Folder Creator](workflows/box-folder-creator/) - Create a named folder in Box and return its metadata.
- [Asana Task Creator](workflows/asana-task-creator/) - Create an Asana task with a name in an existing workspace.
- [Gmail AI Labeler](workflows/gmail-ai-labeler/) - Poll incoming Gmail messages, classify each body into existing Inquiry, Partnership and Notification labels, and add each message’s own label IDs.
- [Google Books Add to Shelf](workflows/google-books-add-to-shelf/) - Get a Google Books volume, add it to My Library and list the first bookshelf page.
- [Zoom Meeting Creator](workflows/zoom-meeting-creator/) - Create a Zoom meeting for the connected user with a configurable topic.
- [Google Text Translator](workflows/google-text-translator/) - Translate one text or HTML input with Google Cloud Translation Basic.
- [Current City Weather](workflows/current-city-weather/) - Read the current OpenWeather conditions for one configured city in metric units.
- [Daily Gmail Summary Email](workflows/daily-gmail-summary-email/) - Summarize matching Gmail email snippets and send one HTML email with key points and named action items.
- [Typeform Request to ClickUp](workflows/typeform-request-to-clickup/) - Route four types of Typeform requests into ClickUp lists with the request details and priority.
- [Google Drive New Files to Notion](workflows/google-drive-new-files-to-notion/) - Record newly created Google Drive files in a Notion data source with their names and original viewer links.
- [Typeform Answers to Airtable](workflows/typeform-answers-to-airtable/) - Save the answers of each completed Typeform submission as one Airtable record using matching question and column names.
- [Typeform Contacts to Airtable and Slack](workflows/typeform-contacts-airtable-slack/) - Save the name and email from a completed Typeform submission in Airtable, then notify a Slack channel after the record is confirmed.
- [Typeform Invoice PDF](workflows/typeform-invoice-pdf/) - Build a two-item invoice from a completed Typeform response, generate its PDF with APITemplate.io and retain the complete PDF and generation response.
- [Create a Mattermost Channel and Welcome a Member](workflows/create-mattermost-channel-and-welcome-member/) - Create a new public Mattermost channel, add a specified user and post the welcome message in that same channel.
- [Gmail Message Snippets to Google Sheets](workflows/gmail-message-snippets-to-google-sheets/) - Append the sender, subject and Gmail snippet of each new message to a spreadsheet.
- [Urgent Gmail Subjects to Telegram](workflows/urgent-gmail-subject-to-telegram/) - Send a Telegram alert for incoming Gmail subjects containing Urgent or exactly matching Server Down.
- [Gmail To-Do Label to Google Tasks](workflows/gmail-todo-label-to-google-tasks/) - Create a Google Task for each new Gmail message matching label:To-Do, using its subject and snippet.
- [Telegram Documents to Google Drive](workflows/telegram-documents-to-google-drive/) - Save each document received by a Telegram bot to a Google Drive folder.

## Content

- [OpenAI Text to Speech](workflows/openai-text-to-speech/) - Convert supplied text into an MP3 with OpenAI tts-1 and return a downloadable audio file.
- [GitHub Prompt Runner](workflows/github-prompt-runner/) - Read a prompt file from GitHub, fill its variables, and return one text response from a configured model.
- [Webpage Markdown Extractor](workflows/webpage-markdown-extractor/) - Fetch one page through Firecrawl and return its Markdown content with the reported page status.
- [Batch Webpage Markdown and Links](workflows/batch-webpage-markdown-links/) - Convert up to 40 page URLs into Markdown, metadata and link arrays, pausing one minute between groups of ten.
- [Recent WordPress Posts](workflows/wordpress-recent-posts/) - Read the five most recent published posts from a WordPress site.
- [French to English Audio](workflows/french-to-english-audio/) - Generate French speech from text, transcribe it, translate the transcript into English and generate English speech in the same voice.

## Commerce

- [WooCommerce Product to Slack](workflows/woocommerce-product-slack-alert/) - Post new WooCommerce product names, prices, and links to Slack.
- [WooCommerce Large Order to Slack](workflows/woocommerce-large-order-slack-alert/) - Post a Slack alert when a new WooCommerce order total is at least 100.
- [WooCommerce Refunded Order to Slack](workflows/woocommerce-refund-slack-alert/) - Notify Slack when an updated WooCommerce order is refunded and its order total is at least 100.
- [WooCommerce Order to Mattermost](workflows/woocommerce-order-mattermost-alert/) - Notify a Mattermost channel when an order is created, using its billing first name and first line item name.
- [WooCommerce New Product to X and Telegram](workflows/woocommerce-product-to-x-and-telegram/) - Announce newly created WooCommerce products on X and Telegram using the product name and permalink.

## Utilities

- [Vector Centroid API](workflows/vector-centroid-api/) - Accept a GET request containing numeric vectors and return their coordinate-wise mean as JSON.
- [German Synonym Lookup](workflows/german-synonym-lookup/) - Look up German synonym groups in OpenThesaurus.
- [Text Hash Generator](workflows/text-hash-generator/) - Generate an MD5 checksum of UTF-8 text as a hexadecimal string.
- [DMY to MDY Date Converter](workflows/dmy-to-mdy-date-converter/) - Convert a valid DD/MM/YYYY calendar date to MM/DD/YYYY.
- [Current UTC Date and Weekday](workflows/current-utc-date-and-weekday/) - Return the current UTC timestamp and matching English weekday from one clock reading.
- [Rename JSON Key](workflows/rename-json-key/) - Rename the top-level JSON field key to newkey while keeping its value and other fields.

## Analytics

- [Segment Event Tracker](workflows/segment-event-tracker/) - Send one Segment Track event with an optional user ID or a fresh anonymous identity.

## Lifestyle

- [Daily Cocktail Photo in Telegram](workflows/daily-cocktail-telegram/) - Send Telegram one random cocktail photo and its available preparation instructions each evening.

## Developer Tools

- [API Operations Schema Export](workflows/api-operations-schema-export/) - Group a service’s API operation rows from Google Sheets into a custom JSON catalog and save the export in Google Drive.
- [GitHub Repository Profile](workflows/github-repository-profile/) - Read a GitHub repository’s community health score and community file metadata.
- [Jira Issue Creator](workflows/jira-issue-creator/) - Create a Jira Cloud issue with a project ID, issue type ID and summary.
- [CircleCI Pipeline Lookup](workflows/circleci-pipeline-lookup/) - Read a CircleCI pipeline by project and pipeline number.
- [Travis CI Build Request](workflows/travisci-build-request/) - Request a Travis CI Cloud build for a repository branch.
- [Rundeck Job Runner](workflows/rundeck-job-runner/) - Request execution of an existing Rundeck job and return its execution record.
- [Telegram Message JSON Debugger](workflows/telegram-message-json-debugger/) - Echo the complete Telegram update JSON privately to the message sender, using safe formatted parts for long updates.
- [GitHub Release Slack Notifications](workflows/github-release-slack-notifications/) - Post GitHub release events to Slack with the repository, tag, complete release notes and original release URL.
- [Send a Telegram Message from a Webhook](workflows/send-telegram-message-from-webhook/) - Send a GET query message to a configured Telegram private chat and return a confirmation using the recipient name from the saved message.
- [GitHub User Profile to Slack](workflows/github-user-profile-to-slack/) - Look up a GitHub profile and matching author emails from its last 25 pull requests, then post the bounded results and avatar to Slack.
- [GitHub Repository Alert Light](workflows/github-repository-alert-light/) - Turn a Home Assistant light red whenever GitHub delivers an event from a selected repository.
- [Google Sheet Table JSON API](workflows/google-sheet-table-json-api/) - Read a configured Google Sheet range and return every data row as a JSON object keyed by the first row.
- [Generate a Current TOTP Code](workflows/generate-current-totp-code/) - Manually generate the current six-digit SHA-1 TOTP code using an existing account secret and a 30-second period.
- [Capture a Public Page with Latchshot](workflows/capture-public-page-with-latchshot/) - Capture a public web page as a PNG with a configurable viewport and delay.

## Communication

- [Twilio SMS Sender](workflows/twilio-sms-sender/) - Submit one text message to Twilio with a sender and recipient number.
- [Mailjet Email Sender](workflows/mailjet-email-sender/) - Send one plain-text email through Mailjet and return its acceptance result.
- [Zulip Private Message Sender](workflows/zulip-private-message-sender/) - Send one Zulip private message to one person or a group.
- [Mailgun Email Sender](workflows/mailgun-email-sender/) - Send a plain-text email through Mailgun and return its queue acceptance result.
- [Rocket.Chat Message Sender](workflows/rocketchat-message-sender/) - Post one text message to a Rocket.Chat room or user.
- [Gmail AI Reply Draft](workflows/gmail-ai-reply-draft/) - Assess incoming Gmail messages, generate replies only when needed and save them as drafts in the original conversations.
- [Google Drive New File Email Alert](workflows/google-drive-new-file-email-alert/) - Watch a Google Drive folder for newly created files and send one plain-text email for each file.
- [Telegram Voice Language Translator](workflows/telegram-voice-language-translator/) - Transcribe a Telegram voice message, translate between two configured languages and reply to the same chat with both text and complete synthesized audio.

## Customer Support

- [Freshdesk Ticket Creator](workflows/freshdesk-ticket-creator/) - Create an open, low-priority Freshdesk ticket for a requester email.
- [Negative Event Feedback to Mattermost](workflows/negative-event-feedback-to-mattermost/) - Analyze Typeform event feedback with Amazon Comprehend and notify Mattermost only for negative sentiment.
- [Typeform Problem Report Routing](workflows/typeform-problem-report-routing/) - Log every completed Typeform problem report in Google Sheets, then send severe reports to Slack and other reports by email.
- [Slack Support Tickets to Linear](workflows/slack-support-tickets-to-linear/) - Find ticket-tagged Slack messages, check existing Linear issue hashes, generate structured support details and create the new tickets in order.
- [Linear Support Sentiment to Slack](workflows/linear-support-sentiment-to-slack/) - Track the sentiment of recently updated Linear issue conversations in Airtable and send aggregated Slack alerts when their sentiment turns negative.

## Finance

- [Pennylane Invoice Creator](workflows/pennylane-invoice-creator/) - Receive a protected invoice request, find or create its Pennylane customer, and return a finalized invoice without sending email.
- [Xero Invoice Reader](workflows/xero-invoice-reader/) - Read up to 100 invoice records from a Xero organization.
- [Invoice Ninja Client Reader](workflows/invoice-ninja-client-reader/) - Read the first 50 clients from an Invoice Ninja v5 instance.
- [Hebrew WhatsApp Invoice Reminders](workflows/hebrew-whatsapp-invoice-reminders/) - Send Hebrew WAHA reminders for open invoices exactly 7, 14 or 30 calendar days overdue, and record each accepted reminder in Google Sheets.

## Community

- [Disqus Forum Reader](workflows/disqus-forum-reader/) - Read public Disqus forum details by forum short name.

## Content Creation

- [Vancine Seedance Video](workflows/vancine-seedance-video/) - Submit one Seedance text-to-video task to Vancine, poll its status with a bounded wait loop and return the completed video URL.

## Recruiting

- [Hacker News Hiring to Airtable](workflows/hacker-news-hiring-to-airtable/) - Find recent Who is hiring threads, read their job comments and extract the first five into structured Airtable recruiting records.

## Content Review

- [Grounded Article MiniCheck](workflows/grounded-article-minicheck/) - Check article sentences against supplied reference facts with Bespoke-MiniCheck and summarize unsupported claims for editorial review.

## Recruitment

- [CV Job Match Report](workflows/cv-job-match-report/) - Extract the complete text of a linked PDF resume and compare it with a job description to produce a structured report for human review.

## Data Sync

- [Airtable Contacts to Google Sheets](workflows/airtable-contacts-to-google-sheets/) - Sync recently updated Airtable records into an existing Google Sheet, matching exact Email keys and using RAW values and the A1:E1000 lookup window.

## Data Enrichment

- [EU Company Register to Google Sheets](workflows/eu-company-register-to-google-sheets/) - Look up every company row across seven national registers with the original Apify Actor, wait for complete results, then update or append the selected registration fields in Google Sheets.

## Contribute

Share a workflow that saves you time. [Suggest a template](https://github.com/oomol-lab/awesome-workflow-templates/issues/new) or [open a pull request](https://github.com/oomol-lab/awesome-workflow-templates/compare).

## Licensing

Original OOMOL contributions to this collection are licensed under [CC BY 4.0](LICENSE).

Third-party material retains its original licenses. See each workflow's README for source attribution, available license information, and our changes.
