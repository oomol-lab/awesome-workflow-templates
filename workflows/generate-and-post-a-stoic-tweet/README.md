# Generate and Post a Stoic Tweet

Generate a tweet using an influencer profile and post it manually or every six hours.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/generate-and-post-a-stoic-tweet.openflow.json) · [n8n JSON](templates/generate-and-post-a-stoic-tweet.n8n.json)

## Setup and use

Connect OpenAI and X. Edit the niche, style and inspiration in Prepare influencer profile. The schedule defaults to every six hours in UTC; adjust the timezone and minute to suit your account. In n8n configure OpenAI and X credentials and edit Configure your influencer profile. Use one format.

## Behavior

The workflow generates a tweet, regenerates it when its text is longer than 280 characters, and posts the result. Each run can incur model charges and publishes publicly. If a post result is unknown, inspect the X account before retrying.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Open Flow uses an OpenAI Responses model and a fixed schedule minute; the source requests a random minute.

Adapted from [Generate and post an influencer tweet](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Manual/0439_Manual_Schedule_Create_Scheduled.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
