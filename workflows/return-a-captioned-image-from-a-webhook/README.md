# Return a Captioned Image from a Webhook

Draw a supplied name over a configured image and return the edited JPEG in the same GET response.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/return-a-captioned-image-from-a-webhook.n8n.json)
<!-- template-actions:end -->

## Setup

1. In **Download the configured background**, enter a direct public HTTPS URL to a JPEG or PNG you are authorized to use. Choose an image at least 640 × 400 pixels to leave room for the caption. The template does not include a background image.
2. Make sure n8n's **Edit Image** node can run GraphicsMagick. The official Docker image includes it. On other installations, install GraphicsMagick and point the node's font option to an installed font if Arial is unavailable. [Edit Image requirements](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.editimage/)
3. Activate the workflow. Open its production GET webhook URL with `?name=Casey%20Redwood`. The default path is `test`. Use fictional names for the demonstration caption.

## Behavior

The request reads one name of up to 40 characters and uses it in the caption. The **Edit Image** node draws the caption at x=150 and y=180 using font size 25 and an 18-character line setting. The response contains the edited JPEG as `image/jpeg`, so a browser can display it directly.

The image URL comes from the workflow configuration. Redirects, an invalid name, a failed download, or a failed render stop the request. The source image is fetched once per request and may be up to 6 MiB.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Caption a newspaper image using a webhook query](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Http/0937_HTTP_Editimage_Update_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Zie619 / n8n-workflows.

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
