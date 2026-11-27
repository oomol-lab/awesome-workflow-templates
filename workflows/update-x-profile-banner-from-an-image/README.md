# Update Your X Profile Banner from an Image

Download a PNG or JPEG and submit it as the profile banner for your connected X account.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/update-x-profile-banner-from-an-image.n8n.json)
<!-- template-actions:end -->

## Setup

1. In **Set the banner image URL**, replace the example URL with a direct HTTPS link to a PNG or JPEG you are authorized to use. Use a public image host and a file up to 2 MiB.
2. In **Upload to the connected X account**, attach an n8n OAuth1 API credential for your X app. Use HMAC-SHA1 and the app's consumer key and secret. Configure X's request-token, authorize, and access-token URLs and register the callback shown in n8n. Authorize the X account whose banner you want to replace. The app must have write access and permission to use the legacy banner endpoint. [X OAuth 1.0a setup](https://docs.x.com/fundamentals/authentication/oauth-1-0a/obtaining-user-access-tokens)
3. Run the workflow manually.

## Behavior

The workflow checks the file type and size and submits the downloaded bytes in the multipart `banner` field. It uses the account bound to the OAuth1 credential. Redirects and invalid images stop the workflow before the upload.

A status of 200, 201, or 202 means the endpoint accepted the request. Check your profile to confirm the banner is visible before retrying an uncertain upload. This template uses the original X API v1.1 endpoint. Its request was verified with synthetic responses, and live endpoint access depends on your app.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Update Twitter banner using HTTP request](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/Instagram_Twitter_Social_Media/Update%20Twitter%20banner%20using%20HTTP%20request.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). Original workflow by Harshil Agrawal. This adaptation validates the download and sets the multipart option explicitly. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

[Original n8n template by Harshil Agrawal](https://n8n.io/workflows/1338-update-twitter-banner-using-http-request/).

</details>
