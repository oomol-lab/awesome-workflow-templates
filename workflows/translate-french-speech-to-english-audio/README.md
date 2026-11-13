# Translate French Speech to English Audio

Generate French speech from text, transcribe it, translate the transcript into English and generate English speech in the same voice.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/translate-french-speech-to-english-audio.openflow.json) · [n8n JSON](templates/translate-french-speech-to-english-audio.n8n.json)

## Setup and use

Use only text and audio that can be public. In Open Flow, both generated recordings are uploaded to Connector storage with public-read download URLs. Anyone with a URL can download that recording. Automatic expiry has not been verified; retention depends on the storage deployment. A later failure can leave the earlier French recording hosted. n8n keeps the recordings as execution binary files.

Connect ElevenLabs in **Generate French speech** and **Generate English speech**. Your voice must support French and English, with allowance for `eleven_multilingual_v2`. The Open Flow Connector deployment must have file transit enabled. Connect OpenAI in **Transcribe the French audio**, and select a configured `gpt-4o-mini-2024-07-18` model in **Translate into English**.

Use Run and supply:

```json
{
  "french_text": "Bonjour. Notre équipe prépare un guide public pour expliquer son travail.",
  "voice_id": "YOUR_ELEVENLABS_VOICE_ID"
}
```

Replace the voice ID with one available to your ElevenLabs account. French text must be nonempty and fit 10,000 characters. The original text is synthesized without trimming; the translated English text is trimmed and must also fit 10,000 characters. Both speech steps use the same voice, stability `0.5`, similarity boost `0.5` and MP3 format `mp3_44100_128`. The source's latency optimization level `1` is retained; ElevenLabs currently marks this option deprecated.

For n8n, edit **Configure French Text and Voice**. Select Header Auth credentials on both ElevenLabs HTTP nodes with header name `xi-api-key` and your API key as its value. Select OpenAI credentials in **Transcribe Audio** and **English Translation Model**. Use Execute Workflow. Keep keys in credentials.

## Behavior

The workflow generates French audio, transcribes that generated recording with `whisper-1`, translates the transcript into English at temperature `0`, and generates English audio in the same voice. It does not skip the French synthesis or transcription. Quotes and line breaks remain valid in both speech requests.

Open Flow returns `frenchTranscript`, `englishText`, `frenchAudio` and `englishAudio`. Each audio object contains `name`, `mimetype` and its public download `url`. Download the files you need while your storage deployment retains them. n8n returns the transcript and translation with English audio in binary `data` and French audio in binary `french`.

Two speech generations, one transcription and one translation step consume the selected services' allowances. No workflow-level retries are configured. n8n's model adapter can retry transient translation requests internally; a configured model service may have its own request behavior. A failed speech, transcription or translation step stops later work. There is no rollback of generated or hosted audio. Service request limits still apply; Whisper accepts files up to 25 MB, and long text can reach generation or transfer limits. The workflow checks returned file references and audio MIME types; it does not verify speech or translation accuracy. Review the text and listen before sharing a recording, and disclose that its voice is AI-generated.

OpenAI has announced shutdown of the default [translator snapshot on January 14, 2027](https://developers.openai.com/api/docs/deprecations/) and [`whisper-1` on February 26, 2027](https://developers.openai.com/api/docs/guides/speech-to-text). Configure compatible replacements in both formats before those dates and verify their request and response formats. This template retains the source transcription endpoint; it uses a separate text translation step.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Make French text and voice ID reusable inputs, with a neutral example in n8n.
- Build speech requests as JSON objects so quotes, newlines and Unicode remain valid.
- Replace the source's omitted translator choice with the explicit snapshot above, which supports its configured temperature. The source currently imports with n8n's `gpt-5-mini` default; this model change can change translation wording.
- Validate empty transcripts and translations before later generation, and make MP3 output explicit.
- Return both recordings and the intermediate texts. Open Flow uses public-read hosted downloads instead of n8n execution binary storage; only use material that can be public, with no verified automatic expiry.

Adapted from [Translate French speech to English audio](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Manual/0400_Manual_Code_Create_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
