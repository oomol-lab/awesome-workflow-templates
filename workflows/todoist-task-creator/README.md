# Todoist Task Creator

Create one task in a Todoist project. Run the workflow manually after setting the content and project.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/todoist-task-creator.openflow.json) · [n8n JSON](templates/todoist-task-creator.n8n.json)

## Setup

For Open Flow, import the JSON, connect Todoist in **Create Todoist task**, replace `YOUR_TODOIST_PROJECT_ID`, and edit Content. The default priority is 1, Todoist’s normal priority.

For n8n, connect Todoist in **Todoist**, select a project, and edit Content. This template uses Todoist node version 2.2.

Run once to create the task. The workflow returns the created task record. Every run creates a new task with the configured content; no due date, labels, section, parent task, or assignee is configured.

## Changes to the source

- Provide an editable example task and an explicit project placeholder.
- Update the n8n Todoist node to version 2.2 and keep normal priority.
- Expose the created task record in Open Flow.

## Source and license

Adapted from [Create a new task in Todoist](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Manual/0007_Manual_Todoist_Create_Triggered.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
