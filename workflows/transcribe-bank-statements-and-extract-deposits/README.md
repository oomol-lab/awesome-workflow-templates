# Transcribe Bank Statements and Extract Deposits

Transcribe a bank statement PDF and extract deposit rows.

<!-- template-actions:start -->
[![View in Open Flow](../../assets/view-in-openflow.svg)](https://openflow.run/templates/transcribe-bank-statements-and-extract-deposits/) [![n8n JSON](../../assets/n8n-json.svg)](templates/transcribe-bank-statements-and-extract-deposits.n8n.json)
<!-- template-actions:end -->

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

## Setup

Connect Google Drive and Gemini, and set the connector transit hostname in **Prepare PDF transcription**. Enter a Drive file ID at the start.

## Behavior

The PDF is sent to Gemini for visual transcription, including scanned pages. A second call extracts deposit rows from the transcript. Review both outputs against the statement; models can omit or misread amounts. Entire PDF bytes and encoded request must fit Open Flow's 1 MiB HTTP and Code limits. Transcription can stop on long documents. The complete statement is sent to Gemini; restrict execution history and transit URL access.

<details>
<summary>In n8n</summary>

In n8n select the Drive file and connect Gemini credentials.

</details>

<details>
<summary>Inspiration &amp; credits</summary>

The source rendered each PDF page to an image. Gemini now accepts PDF visual input directly; this version sends the complete PDF and checks both model outputs.

Adapted from [Transcribe and extract data from scanned bank statements](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Code/1699_Code_Editimage_Automation_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Zie619 / n8n-workflows.

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
