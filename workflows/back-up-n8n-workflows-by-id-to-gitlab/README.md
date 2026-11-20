# Back Up n8n Workflows by ID to GitLab

Back up n8n workflows as JSON files in a GitLab repository.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/back-up-n8n-workflows-by-id-to-gitlab.n8n.json)
<!-- template-actions:end -->

## Setup

Connect n8n and GitLab, set owner, project, branch and path in **Configure the backup**, and enable persistent State. Prevent concurrent runs. In n8n connect the corresponding credentials, configure the same repository and a Data Table with item_key and status text columns; the path must end in / when nonempty. Run manually and use one format.

## Behavior

Each workflow is saved as its ID plus .json. Existing JSON is compared recursively while ignoring updatedAt and global fields, including when the keys differ. The source compared object key counts before ignoring these fields. Unchanged files are skipped. Backups may contain sensitive configuration; restrict access to the repository and execution history. Open Flow Code inputs, outputs and accumulated list must fit 1 MiB.

If a write has an unknown result, inspect GitLab. In **Resolve pending backup**, enter its pending key and either confirmed or absent, rerun, and clear these fields. In n8n inspect the pending Data Table row; mark done only when confirmed or delete only when absent. Earlier successful files are not rolled back. Open Flow stops on a read error; n8n reports the affected item and continues.

<details>
<summary>Inspiration &amp; credits</summary>

Use workflow IDs for paths and checkpoint writes.

Adapted from [n8n workflow backup to GitLab](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Gitlab/0561_Gitlab_Code_Create_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
