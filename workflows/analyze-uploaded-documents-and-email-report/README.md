# Analyze Uploaded Documents and Email a Report

Parse uploaded documents, translate and analyze them, and email the report.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/analyze-uploaded-documents-and-email-report.n8n.json)
<!-- template-actions:end -->

## Behavior

A form accepts one required and one optional file, an email address, and a caller-generated Request ID of 16 to 128 letters, digits, underscores or hyphens. Use a unique random ID for each new submission and reuse it when retrying the same submission. LlamaCloud parses each file; Gemini translates and analyzes their combined text, and Gmail sends a text attachment to the submitted address. Review AI output against the source documents. Files and text are sent to LlamaCloud and Gemini. The separate conversational retrieval and knowledge-indexing branches of the original are not part of this component.

Unknown parse creation or email outcomes stop before retry; inspect the destination, enter the pending key and confirmed or absent in **Choose document processing step**, and replay the same submission. For a confirmed parse creation, enter its job ID. Clear the recovery fields afterward.

<details>
<summary>Inspiration &amp; credits</summary>

Extract the form analysis component; replace the former external chat link and use the current LlamaCloud Parse API.

Adapted from [My workflow 3](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Code/1818_Code_Converttofile_Automate_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Zie619 / n8n-workflows.

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
