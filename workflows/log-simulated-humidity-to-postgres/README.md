# Log Simulated Humidity to PostgreSQL

Generate a simulated humidity reading every minute and insert it into your PostgreSQL table.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/log-simulated-humidity-to-postgres.n8n.json)
<!-- template-actions:end -->

## Setup

1. Use an existing readings table or create a dedicated demo table.

   ```sql
   CREATE TABLE public.humidity_readings (
     sensor_id text NOT NULL,
     value integer NOT NULL CHECK (value BETWEEN 1 AND 100),
     time_stamp timestamptz NOT NULL,
     notification boolean NOT NULL
   );
   ```

2. In **Insert the reading into PostgreSQL**, select the schema and table you want to use. The imported node starts with the source table name, `public.n8n`. Select `public.humidity_readings` if you used the example. Bind a [PostgreSQL credential](https://docs.n8n.io/integrations/builtin/credentials/postgres/) with schema access and `INSERT` and `SELECT` on the four columns. Use TLS for a remote database.
3. Activate the workflow to start the minute schedule. The workflow time zone is UTC.

## Behavior

Each minute creates one row for the simulated sensor `humidity01`, with a random integer from 1 to 100, the UTC trigger time, and `notification = false`. The Postgres node returns the inserted fields. No sensor connection or notification service is required.

If a connection drops during an insert, check the table for that minute before retrying the failed execution.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Postgres Data Ingestion](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Cron/0822_Cron_Postgres_Automation_Scheduled.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Zie619 / n8n-workflows.

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
