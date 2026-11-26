# Generate Stock Image Metadata from a Webhook

Send a PNG or JPEG to a webhook and get a stock title, description, keywords, and a CSV row in the HTTP response.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/generate-stock-image-metadata-with-a-webhook.n8n.json)
<!-- template-actions:end -->

## Setup

1. Attach a **Header Auth** credential to **Receive an image** with the name `X-Stock-Metadata-Key` and a secret value. Connect an OpenAI API credential in **Generate stock metadata with OpenAI**.
2. For URL submissions, set your Google Cloud Storage bucket in **Validate the image and configure the bucket**. Use a direct public or signed HTTPS object URL in that bucket, such as `https://storage.googleapis.com/BUCKET/photo.jpg`. The object must identify its content as `image/jpeg` or `image/png`. Inline submissions require no bucket.
3. Activate the workflow and send a POST to the production webhook URL with your secret header and `Content-Type: application/json`.

## Behavior

Send one image in `imageUrl`, `image_url`, `image`, or `imageBase64`. The first three accept the configured bucket URL or a PNG or JPEG data URL. Use `imageBase64` for raw base64 or a data URL. Each image can be up to 2 MiB after decoding. URL downloads use HTTPS without redirects. The workflow checks the image bytes before sending them to OpenAI.

The same HTTP request returns a one-item JSON array with `title`, `description`, `keywords`, `keyword_count`, `csv_row`, and `csv`. The CSV holds a header and one row, with keywords separated by semicolons. Formula-like cells are prefixed with an apostrophe in CSV. The JSON fields retain their text.

A successful response includes 20–40 distinct lowercase keywords. Invalid inputs get an error response. Failed downloads, image validation, and unusable model replies also fail the request.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [AI Stock Image Metadata Generator](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/OpenAI_and_LLMs/AI%20Stock%20Image%20Metadata%20Generator.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The source export does not identify a separate template author or license. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

## Changes to the source

The workflow validates the image before using an OpenAI structured response, confines downloads to the configured bucket, and protects exported CSV cells from spreadsheet formulas.

</details>
