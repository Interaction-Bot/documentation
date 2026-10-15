---
description: Configure how the bot reads messages aloud on your server, and who can use the text to speech features.
---

# Text to speech settings

Navbar > category _**Audio & AI**_ > _**Text to speech settings**_.

This page holds the settings that apply to **every** reading on the server: a session started with `/tts start`, the automatic reading of messages, `/tts say`, and the [TTS channels](tts-channels.md). The commands are described in [Text to speech commands](../../commands/tts.md).

The reading settings and the permissions are saved with the _**Save**_ button at the bottom of the page, and _**Cancel**_ restores the last saved settings. The message _Settings saved._ confirms the save. The **Voices** card has its own _**Save**_ button, and confirms with _Voices saved._

## Reading

| Setting | Default | What it does |
| --- | --- | --- |
| Read messages automatically | On | Reads the messages of allowed members during a session, without a command for each one. |
| Say who wrote | On | When the author changes, the bot says the name before the message, for example *Alex said: ...*. |
| Read the chat of voice channels | On | Also reads the messages written in the chat of a voice channel the bot is in. |
| Ignore bots | On | Messages written by bots are not read. |
| Ignore the audience of stages | On | Messages of the audience of a stage channel are not read. |
| The author must be in the voice channel | On | Only the messages of members in the voice channel of the bot are read. |
| Skip emojis | Off | Emojis are removed before the message is read. |
| Members can choose their voice | On | Members can pick their own voice with `/tts voice`. |
| Prefix | Empty | Only the messages that start with this prefix are read. The prefix itself is not read. Up to 10 characters. Leave it empty to read every message. |

## Voices

The **Voices** card lists the voices available on the server. Each person who speaks in a session gets a voice of their own, so that the listeners can tell who is talking.

* **Use** (switch): a voice that is switched off is never given.
* **Order**: drag a voice to move it, or use the arrow buttons. The order is the order in which the voices are given. The first voices are given first.
* **Default voice**: the voice of `/tts say` and of the messages without author. A disabled voice cannot be the default one, and at least one voice must stay enabled.

A member's own choice (`/tts voice`) takes precedence over the order, when the member is allowed to choose.

## Permissions

Each permission decides who can use a feature. For each one, choose:

* **Everyone** (default), or
* **Only the chosen roles and members**: pick roles in the list, and add members by their Discord ID. To copy an ID, turn on developer mode in Discord, then right-click the member.

Members with the *Manage Server* permission can always use these features.

| Permission | Who it applies to |
| --- | --- |
| Start and stop | `/tts start` and `/tts stop`: who can make the bot join or leave a voice channel. |
| Automatic reading | Whose messages are read automatically during a session. |
| Choose a voice | Who can change the voice used for their messages with `/tts voice`. |

{% hint style="info" %}
The changes of permissions take effect within about 30 seconds.
{% endhint %}

## Messages of the page

| Message | Meaning |
| --- | --- |
| _One of the roles does not exist anymore. Remove it and save again._ | A role of a permission was deleted on Discord. Remove it from the list. |
| _This permission does not exist._ | The page was not up to date. Reload it and try again. |
| _The settings could not be saved._ | Try again in a moment. |

For the voice settings, see also the messages of the **Voices** card in [Text to speech commands](../../commands/tts.md#voices).

{% hint style="info" %}
To check how a session works step by step, see [Voice guides](../../audio/voice-guides.md#1-read-the-chat-aloud-for-a-while-tts-start). The bot must be able to view the channels and to connect and speak in the voice channels, see [Voice troubleshooting](../../audio/voice-troubleshooting.md).
{% endhint %}
