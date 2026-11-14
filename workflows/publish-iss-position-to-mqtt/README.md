# Publish ISS Position to MQTT

Publish the current International Space Station position to an MQTT topic every minute.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="preview-dark.png">
  <img alt="Open Flow workflow" src="preview-light.png">
</picture>

[Open Flow JSON](templates/publish-iss-position-to-mqtt.openflow.json) · [n8n JSON](templates/publish-iss-position-to-mqtt.n8n.json)

## Setup and use

Connect an MQTT broker in Open Flow using its MQTT-over-WebSocket URL and any required credentials. In n8n connect an MQTT credential. The default topic is iss-position; change it in the publish node if needed. Activate one format.

## Behavior

Every minute, the workflow reads the current ISS position from Where the ISS at? and publishes a JSON message with Name, Latitude, Longitude and Timestamp as strings. The default MQTT QoS is 0 and retain is false, matching the source. QoS 0 does not provide delivery acknowledgement. If a publish result is uncertain, a subscriber may already have received it.

<details>
<summary>Inspiration &amp; credits</summary>

## Changes to the source

- Request the current-position endpoint instead of passing a millisecond timestamp to the positions endpoint, and preserve the four output fields. Open Flow connects over MQTT WebSocket.

Adapted from [ISS position to MQTT](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Http/0033_HTTP_Mqtt_Automation_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). The source export does not identify a separate template author or license.

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
