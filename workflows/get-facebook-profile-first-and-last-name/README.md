# Get a Facebook Profile First and Last Name

Read the first and last name available to a Facebook user access token.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/get-facebook-profile-first-and-last-name.openflow.json) · [n8n JSON](templates/get-facebook-profile-first-and-last-name.n8n.json)

## Setup and use

Connect Meta using a Facebook user access token authorized to read the user's profile. In Open Flow, allow Provider API Request on the connection. In n8n, configure the Facebook Graph API credential with a user access token. Run manually. The token determines which user is queried; a Page or system-user token represents a different identity.

## Behavior

The workflow requests `last_name,first_name` from the token's `/me` profile and returns the response object. Availability depends on the token, account and API permissions. Open Flow uses the Meta connection's Graph API version; n8n uses its default Graph API version.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Open Flow uses the Meta Provider API Request to request the source fields, checks the response and exposes it as a profile object.

Adapted from [Read a Facebook profile](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Manual/0987_Manual_Facebookgraphapi_Automation_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
