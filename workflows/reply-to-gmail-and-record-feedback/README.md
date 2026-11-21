# Reply to Gmail and Record Feedback

Generate a reply to an incoming email, log it and record linked feedback.

<!-- template-actions:start -->
[![View in Open Flow](../../assets/view-in-openflow.svg)](https://openflow.run/templates/reply-to-gmail-and-record-feedback/) [![n8n JSON](../../assets/n8n-json.svg)](templates/reply-to-gmail-and-record-feedback.n8n.json)
<!-- template-actions:end -->

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

## Setup

Connect Gmail and Google Sheets, and configure an AI model. Prepare a Google Sheet with `Sheet1` headers `ID`, `Initial message`, `Generated reply`, and `Good response?`, and set the spreadsheet ID in **Append reply log**, **Read reply IDs**, and **Record feedback**. Set the allowed sender filter in **Choose next email**, publish the workflow, and copy the **Receive feedback click** Webhook URL into **Format linked reply**.

## Behavior

For allowed unread messages, the workflow generates a reply, logs the UUID, original text, and reply to Google Sheets, and sends an HTML Gmail reply containing Yes/No feedback links. Clicking a link calls the feedback Webhook and records the response in the matching row. Email content is shared with the model. Lost Gmail or Sheets responses can mean a write succeeded; inspect the destination before retrying.

<details>
<summary>In n8n</summary>

Import the n8n workflow, configure Gmail and OpenAI credentials, set the allowed senders in **Configure**, and set a public feedback webhook URL on **On feedback given**.

</details>

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Send a ChatGPT email reply and save responses to Google Sheets](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/Gmail_and_Email_Automation/Send%20a%20ChatGPT%20email%20reply%20and%20save%20responses%20to%20Google%20Sheets.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The n8n parser follows [ikbelkirasan’s gist](https://gist.github.com/ikbelkirasan/2462073f6c7c760faa6fad7c6a0c4dc3), and includes [node-email-reply-parser](https://github.com/t2bot/node-email-reply-parser), [lodash](https://github.com/lodash/lodash) and [esrever](https://github.com/mathiasbynens/esrever), distributed under the MIT License. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

Copyright (c) GitHub, William Durand, Travis Ralston. Copyright OpenJS Foundation and other contributors; based on Underscore.js, copyright Jeremy Ashkenas, DocumentCloud and Investigative Reporters & Editors. Copyright Mathias Bynens.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

</details>
