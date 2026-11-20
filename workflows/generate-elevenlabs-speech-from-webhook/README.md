# Generate Speech with ElevenLabs

Generate speech from text and return the audio bytes.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/generate-elevenlabs-speech-from-webhook.n8n.json)
<!-- template-actions:end -->

## Setup

Configure an ElevenLabs connection with access to eleven_multilingual_v2 and the selected voice. Restrict webhook access; requests use your ElevenLabs account.

## Use

POST JSON with voice_id, text and a unique request_id. Text is sent to ElevenLabs. The model supports up to 10,000 characters per request.

Prevent overlapping requests with the same ID.

<details>
<summary>Inspiration &amp; credits</summary>

Original workflow by The n8Ninja.

Adapted from [Generate Text-to-Speech Using Elevenlabs via API](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/OpenAI_and_LLMs/Generate%20Text-to-Speech%20Using%20Elevenlabs%20via%20API.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
