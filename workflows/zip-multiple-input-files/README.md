# ZIP Multiple Input Files

Combine multiple input files into a single ZIP archive.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/zip-multiple-input-files.openflow.json) · [n8n JSON](templates/zip-multiple-input-files.n8n.json)

## Setup and use

In Open Flow provide an array of files, each with a name and base64-encoded content. In n8n call the sub-workflow with binary files in the **data** property of each item.

## Behavior

The workflow combines the inputs into one ZIP containing their filenames and bytes. Open Flow returns its name and base64 contents; n8n returns binary data. Inputs and output must fit the execution limits. Duplicate filenames resolve to the last file.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Open Flow uses fflate to compress base64 inputs and names the archive with the UTC date.

Adapted from [Combine binary items into a ZIP](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Code/1969_Code_Stickynote_Automation_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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



Open Flow bundles [fflate 0.7.4](https://github.com/101arrowz/fflate), copyright 2020 Arjun Barrett, under the MIT License. The complete notice is included in the Code node.

</details>
