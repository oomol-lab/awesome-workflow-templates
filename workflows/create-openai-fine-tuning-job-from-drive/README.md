# Create an OpenAI Fine-Tuning Job from Drive

Upload a JSONL training file from Google Drive and create an OpenAI fine-tuning job.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/create-openai-fine-tuning-job-from-drive.n8n.json)
<!-- template-actions:end -->

## Setup and use

OpenAI is winding down fine-tuning and no longer accepts new users. Eligible existing organizations must also have used a fine-tuned model for inference in the prior 60 days. They can create training jobs until January 6, 2027, unless the selected base model shuts down sooner. The source model gpt-4o-mini-2024-07-18 is scheduled to shut down on January 14, 2027. Check [OpenAI fine-tuning availability](https://developers.openai.com/api/docs/guides/supervised-fine-tuning) and select a model supported by your account.

For the direct job node, configure HTTP Header Auth with the name Authorization and value Bearer followed by your OpenAI API key.

## Behavior

Training runs asynchronously. If either upload or job creation has an unknown result, inspect OpenAI files or jobs before retrying; a repeated run may create another file or job.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Automated End-to-End Fine-Tuning of OpenAI Models with Google Drive Integration](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/Google_Drive_and_Google_Sheets/Automated%20End-to-End%20Fine-Tuning%20of%20OpenAI%20Models%20with%20Google%20Drive%20Integration.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
