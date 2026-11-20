# Check Drive Passport Photo Guidance

Check Google Drive portraits against digital passport photo guidance and review the results.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/check-drive-passport-photo-guidance.n8n.json)
<!-- template-actions:end -->

## Setup

Connect Google Drive and Gemini, and configure a current vision-capable Gemini model.

## Behavior

It returns those measurements, whether the digital size requirements pass, and the model's assessment of visible features. Review each result against the original image and current official guidance; a model cannot establish all requirements or guarantee acceptance. Images are sent to Gemini.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

Measure original pixel dimensions and byte length before resizing; return separate objective and visual checks. Add an n8n relay and replace private photo IDs and the retired model.

Adapted from [Automate Image Validation Tasks using AI Vision](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/OpenAI_and_LLMs/Automate%20Image%20Validation%20Tasks%20using%20AI%20Vision.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
