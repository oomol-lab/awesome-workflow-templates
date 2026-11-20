# Route Contact Forms by Topic

Classify a contact request, email the matching department and log it to Google Sheets.

<!-- template-actions:start -->
[![View in Open Flow](../../assets/view-in-openflow.svg)](https://openflow.run/templates/route-contact-form-by-topic/) [![n8n JSON](../../assets/n8n-json.svg)](templates/route-contact-form-by-topic.n8n.json)
<!-- template-actions:end -->

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

## Setup and use

Configure the form, SMTP credentials, sender and department recipients, and Google Sheets credentials, spreadsheet and sheet in each database node. In Open Flow, edit the five department addresses in **Choose department**, set the spreadsheet ID and A:F worksheet range in **Append contact to Sheets**, and connect Google Sheets. For relay, deploy the Open Flow workflow, configure its model, and set its webhook URL in both Open Flow HTTP nodes. Activate only the chosen mode.

## Behavior

The form collects a name, email and message. The model selects quote, product information, general problem, order, or other. The matching department receives the request with the submitter as reply-to; the workflow appends its details and recipient to the sheet. Messages are shared with the configured model. The Open Flow webhook does not authenticate callers; restrict access to trusted senders. A lost email or sheet response can mean the write succeeded; inspect the destination before retrying.

<details>
<summary>In n8n</summary>

Import the n8n workflow and configure the form, SMTP credentials, sender and department recipients, and Google Sheets credentials, spreadsheet and sheet in each database node. Set **Choose mode** to direct for native n8n classification, or relay for Open Flow classification. The form and email delivery remain in n8n in both modes.

In relay mode Open Flow chooses the department and appends the row after SMTP returns successfully.

</details>

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Add an Open Flow classification mode and correct the classifier's quote and product output wiring. Replace private spreadsheet IDs and recipient addresses with placeholders, and log the actual category.

Adapted from [Modular & Customizable AI-Powered Email Routing: Text Classifier for eCommerce](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/Gmail_and_Email_Automation/Modular%20%26%20Customizable%20AI-Powered%20Email%20Routing_%20Text%20Classifier%20for%20eCommerce.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
