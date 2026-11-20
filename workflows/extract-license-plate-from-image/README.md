# Extract a License Plate from an Image

Upload a vehicle image and extract the front-most license plate as text.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/extract-license-plate-from-image.n8n.json)
<!-- template-actions:end -->

## Setup

Connect a vision-capable OpenRouter model for direct use. Restrict access to trusted users.

## Behavior

Upload a JPG or PNG image on the selected form. The vision model reads the plate on the front-most car and displays its result on the completion page. Check the result against the image: recognition may be inaccurate. Images and uploaded files are sent to the model provider and retained according to its settings. If an upload outcome is uncertain, inspect the account before submitting again.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Extract license plate number from image uploaded via an n8n form](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/PDF_and_Document_Processing/Extract%20license%20plate%20number%20from%20image%20uploaded%20via%20an%20n8n%20form.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

</details>
