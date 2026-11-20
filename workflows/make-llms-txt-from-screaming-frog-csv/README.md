# Make llms.txt from Screaming Frog CSV

Turn a Screaming Frog crawl export into a downloadable llms.txt index.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/make-llms-txt-from-screaming-frog-csv.n8n.json)
<!-- template-actions:end -->

## Setup

Export internal_html.csv or internal_all.csv from Screaming Frog. Open its form to provide the website name, description and CSV.

## Behavior

Rows with status 200, an indexable value and a content type containing text/html become Markdown links, using each row's title, URL and optional meta description. The output starts with the submitted website name and description. The workflow recognizes the source's English, French, Italian, German and Spanish column labels; indexability values are Indexable, Indicizzabile or Indexierbar. The optional source classifier remains disabled. If no rows match, the file contains only the heading and description.

<details>
<summary>Inspiration &amp; credits</summary>

Correct CSV extraction and preserve each submission when generating the file.

Adapted from [Generate AI-Ready llms.txt Files from Screaming Frog Website Crawls](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Filter/1791_Filter_Summarize_Create_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
