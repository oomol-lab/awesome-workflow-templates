# Generate a Song Through a Tunova Webhook

Send an authenticated song prompt and receive the Tunova job status in the same HTTP request after a 150-second wait.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/return-tunova-song-from-webhook.n8n.json)
<!-- template-actions:end -->

## Setup

1. Import the workflow on a self-hosted instance using regular execution mode (`EXECUTIONS_MODE=regular`). Allow at least 240 seconds through the HTTP client, reverse proxy, load balancer and workflow execution settings. n8n Cloud times out after 100 seconds. [Webhook timeouts](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.webhook/common-issues#timeouts-on-n8n-cloud) · [Execution timeouts](https://docs.n8n.io/deploy/host-n8n/configure-n8n/basic-configuration/configuration-examples/configure-workflow-timeouts)
2. In **Receive an authenticated song request**, select a Header Auth credential with header name `Authorization` and value `Bearer <a-long-random-webhook-token>`. Use a separate Header Auth credential named `X-API-Key` with your Tunova API key in **Start the Tunova job** and **Check this Tunova job**. Use HTTPS and keep access to the webhook and execution data restricted. [Tunova quickstart](https://tunova.ai/quickstart)
3. Publish and use the production HTTPS webhook URL. POST a JSON body with a nonblank `prompt` of at most 2,000 characters and an optional boolean `instrumental`. Generate a random UUID v4 for the `Idempotency-Key` header and save it before sending. Do not put tokens in the URL.

```sh
curl --max-time 240 https://n8n.example.com/webhook/generate-song \
  -H "Authorization: Bearer $SONG_WEBHOOK_TOKEN" \
  -H "Idempotency-Key: $SONG_SUBMISSION_UUID" \
  -H 'Content-Type: application/json' \
  -d '{"prompt":"mellow piano by a rainy window","instrumental":true}'
```

## Behavior

The request stays open while the workflow waits 150 seconds after Tunova accepts the job. The workflow checks that same job once and responds with JSON fields `status`, `audio_url` and `title`. If the job is complete, the audio link and title describe the first finished track. If it is queued, processing, submitted or failed, the audio link and title are null. A finished track can also have a null title.

If the client disconnects, the request times out, or the workflow returns an upstream error, retry with the same key and identical inputs. During Tunova's retention period, normally around seven days, this preserves the existing job and waits before checking it again. Changed inputs with the same key return HTTP 409. Generate a new key only for a new song. Accepting a new job can spend credits. [Tunova idempotency](https://tunova.ai/security)

The original HTTP connection depends on the running n8n process. Keep the instance running during the wait. The waiting execution data can include the original request headers and prompt, so restrict access to the execution store and avoid logging those headers at ingress.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Tunova - Generate a song via webhook](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/Other_Integrations_and_Use_Cases/Tunova%20-%20Generate%20a%20song%20via%20webhook.json) in [enescingoz/awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates).

Source collection notice: © 2024–2026 Enes Cingoz, [CC BY 4.0](https://github.com/enescingoz/awesome-n8n-templates/blob/827110332c21cbe000ab13f6d292d5adb1f1f8db/LICENSE). The [source contribution](https://github.com/enescingoz/awesome-n8n-templates/commit/147dba292c4e2dd040a081b5579457a7fcab7c53) credits erliona. See [repository licensing](../../README.md#licensing) for the scope of OOMOL contributions and third-party material.

## Changes to the source

The request uses Tunova’s documented instrumental field and Suno v6. The webhook requires authentication and a submission key, checks the returned job ID, and preserves the original synchronous three-field JSON result. [Tunova versioning](https://tunova.ai/versioning)

</details>
