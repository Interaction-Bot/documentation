---
description: Configure the voice recording of your server - who can record, the bot's voice, transcription, export defaults and automatic recording.
---

# Voice recording

The Voice recording page controls the [`/record`](../../audio/recording.md) command of your server: whether members can record, who can start a recording, what the default downloads and video exports look like, and the automatic recording.

## Localization

Navbar > category _**Audio & AI**_ > _**Voice recording**_.

The switch next to the title of the page turns recording on or off for the server. It is on by default. When it is off, `/record start` is refused with *Recording is disabled on this server.* A recording that is already running goes on.

## Settings

The settings are saved with the _**Save**_ button of the bar at the bottom of the page. _**Cancel**_ restores the last saved values.

### Recording

* **Record the bot's voice**: the text to speech of the bot is added as a separate track. Off by default. The announcements of the recording itself are never recorded.
* **Allow transcription of recordings**: members who started a recording can have it transcribed (see [Transcription of a recording](../../audio/recording.md#transcription-of-a-recording)). On by default. Turn it off to refuse all transcriptions on the server.
* **Default download format**: the format selected on the page of each recording. FLAC by default. The choices are FLAC, M4A, MP3, OGG and WAV.
* **Consent notice**: a reminder of what the bot does when a recording starts (the members are warned in the text channel and out loud). Nothing to set.

### Video export defaults

The starting values of the video export of each recording. They can still be changed before each export, on the recording's page.

| Setting | Choices | Default |
| --- | --- | --- |
| Layout | Call grid, Vertical list | Call grid |
| Theme | Dark, Light | Dark |
| Resolution | 720p, 1080p | 720p |
| Show names | On, Off | On |
| Border colour | Any colour (colour picker) | `#23A559` (green) |

### Who can start a recording

The rule of `/record start`:

* **Everyone** (default): any member can start a recording.
* **Only the roles and members below**: only members who have one of the **allowed roles**, or whose Discord ID is in the **allowed members** list, can start one.

Members with *Manage Server* can always start a recording. To add a member to the list, enter their Discord ID (Developer Mode, right-click on the member, Copy ID), then click _**Add**_. The list holds up to 100 members.

### Automatic recording

*Premium only.* The bot starts a recording when members join a voice channel. See [Automatic recording](../../audio/recording.md#automatic-recording) for how it behaves.

| Setting | Meaning | Default |
| --- | --- | --- |
| Automatic recording enabled | Turns the feature on. | Off |
| Watched voice channels | The channels that trigger a recording. Empty: every voice channel of the server. | Every voice channel |
| Minimum members | Members needed in the channel to start, bots excluded (1 to 25). | 1 |
| Trigger roles | A member with one of these roles starts a recording alone, whatever the minimum. | None |
| Panel channel | Where the recording panel is posted. _Automatic_: the first text channel where the bot can write. | Automatic |

On a free server the switch cannot be turned on: the page shows *Automatic recording is a premium feature.* with a link to [Premium](../../premium/premium.md).

## Limits

| | Free | Premium |
| --- | --- | --- |
| Voice recording, `/record start` | Yes, with a top.gg vote or premium | Yes |
| Settings of this page | All | All |
| Automatic recording | No | Yes |
| Daily recording time | 1 h 45 min per server | 6 h per server |

The daily time, the length and the retention of the recordings are set by the bot, not by this page. See [Voice recording](../../audio/recording.md#limits).

## Messages of the page

| Message | Meaning |
| --- | --- |
| *Settings saved.* | The settings are saved. |
| *The settings could not be saved. Try again.* | The save failed. Try again. |
| *The page could not be loaded. Try again.* | The settings could not be read. Use _**Try again**_. |
| *One of the roles no longer exists on this server. Choose the roles again.* | A role was deleted. Choose the roles again. |
| *One of the channels is not valid on this server. Choose them again.* | A channel of the automatic recording was deleted, or is not the right kind. |
| *Automatic recording needs a premium server.* | The server is not premium. |
| *Enter a Discord ID (digits only).* | The member ID is not a number. |

{% hint style="info" %}
The page only saves the settings. For the permissions the bot needs, see [Voice recording](../../audio/recording.md#permissions). To use the recordings of a member, see [My recordings](../recordings.md).
{% endhint %}
