# Control Spotify With an MQTT Remote

Use an IKEA-style MQTT remote to control a configured Spotify Connect device and run two playback shortcuts.

<!-- template-actions:start -->
[![n8n JSON](../../assets/n8n-json.svg)](templates/control-spotify-with-an-mqtt-remote.n8n.json)
<!-- template-actions:end -->

## Setup

1. In **Receive MQTT remote actions**, select credentials for your MQTT broker and enter one authorized remote action topic, for example `zigbee2mqtt/living-room-remote/action`. Use a topic whose publishers you trust and configure the remote to send fresh, non-retained actions. The trigger supports plain text or JSON strings.
2. Set the exact Spotify Connect device name in **Set the Spotify device and shortcuts**. To use both long-press shortcuts, set a Spotify track URI such as `spotify:track:YOUR_TRACK_ID` and the exact name of an accessible playlist.
3. Use the same Spotify OAuth2 credential in **Read Spotify playback state**, **List Spotify Connect devices**, **Read the Spotify playlist pages**, and **Send the targeted Spotify command**. Use a Spotify Premium account. The required scopes are `user-read-playback-state`, `user-modify-playback-state`, and `playlist-read-private` or `playlist-read-collaborative` for an applicable playlist. In a shared instance, serialize this workflow's production executions so closely spaced volume changes can read the previous playback state. [Spotify Player API](https://developer.spotify.com/documentation/web-api/reference/get-information-about-the-users-current-playback)
4. Activate the workflow and press the remote. The target device must be online, controllable, and visible to that Spotify account.

## Remote actions

| MQTT message | Action |
| --- | --- |
| `arrow_left_click` / `arrow_right_click` | Previous or next track on the active Spotify device |
| `brightness_up_click` | Raise volume by 5 percentage points, capped at 100% |
| `brightness_down_click` | Reduce volume by 5 percentage points with the source's 20% floor |
| `toggle` | Pause if the configured device is playing, or start or resume playback there |
| `brightness_up_hold` | Set volume to 80%, queue the configured track, then skip to the next track |
| `brightness_down_hold` | Find a unique playlist with the configured name and start it |

Unknown messages do not call Spotify. The arrow buttons use the active Spotify device directly. For volume, toggle and shortcuts, the workflow identifies one matching configured device, transfers playback to it when needed, and targets subsequent commands to it. A missing or ambiguous device or playlist stops the run before changing playback. The playlist shortcut checks up to 20 pages of 50 entries.

Spotify accepts each command separately. If a command fails or its outcome is uncertain, the run stops without retrying it. Check the player before pressing the button again. The MQTT Trigger does not expose retained or duplicate packet flags, so use a non-retained action topic and avoid replaying old commands.

<details>
<summary>Inspiration &amp; credits</summary>

Adapted from [Spotify control from an IKEA-style MQTT remote](https://github.com/Zie619/n8n-workflows/blob/ae8cf6dc5b873cbb4f74587aa9180ed3a9f70682/workflows/Splitout/0560_Splitout_Filter_Import_Webhook.json) in [Zie619/n8n-workflows](https://github.com/Zie619/n8n-workflows). Attribution: Zie619 / n8n-workflows.

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
