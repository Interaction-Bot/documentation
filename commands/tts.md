---
description: Reference of the text to speech commands, the reading of the chat and the voices.
---

# Text to speech commands

The bot reads text aloud in a voice channel. The overview is in [Audio](../audio/overview.md), the access rules in [Voice](../audio/voice.md#access), and the daily time in [Daily limits](../audio/limits.md).

| Command | Description | Who |
| --- | --- | --- |
| `/tts start` | Makes the bot join your voice channel and read the messages of this chat and of that voice channel. | Members allowed by *Start and stop* (everyone by default) |
| `/tts stop` | Ends the session: the bot leaves the voice channel and cuts the speech in progress. | Same as `/tts start` |
| `/tts say <query> [language]` | Reads one text once, in your voice channel. | Everybody, with a vote |
| `/tts voice [voice] [reset]` | Chooses the voice that reads your messages. Without argument, shows your voice. | Members allowed by *Choose a voice* |
| `/tts settings` | Opens the settings panel, with buttons. The same settings as the dashboard. | Manage Server |
| `/tts-channel set\|remove\|list\|manage` | Reads every message of a text channel aloud. | Manage Server |
| `/connect` / `/disconnect` | Moves the bot to a voice channel, or makes it leave. | See [Voice](../audio/voice.md#connecting-and-leaving) |

{% hint style="info" %}
`/tts <text>` no longer exists: use `/tts say`. `/tts-stop` is replaced by `/tts stop`.
{% endhint %}

## Start a session: `/tts start`

* You must be in a voice channel, otherwise the bot answers *You are not connected to a voice channel.*
* The bot joins **your** voice channel. If it is already connected to another voice channel of the server, it refuses (*I am already reading in another voice channel.*).
* During the session, the bot reads the messages written in **the chat where you ran `/tts start`** and in **the chat of the voice channel**.
* The session has **no fixed duration**: the bot does not disconnect after a set time. It leaves when:
  * you run `/tts stop`;
  * nobody but bots is left in its voice channel for **30 seconds**;
  * the daily text to speech time of the server is used up. It first reads the clips already paid for, then leaves, and the chat says when the time starts again.
* Access: the server is premium, **or** a member of the server has voted on [top.gg](https://top.gg/bot/893494390142697493/vote) in the last 24 hours. One vote unlocks the feature for the whole server.

## Automatic reading

During a session, a message is read **without a command** when:

* its author is allowed by *Automatic reading* (everyone by default);
* the author is a member, not a bot, and is in the voice channel of the bot (unless *Author in voice only* is off);
* it is not from the audience of a stage channel (unless *Ignore the audience of stages* is off);
* it has text after the prefix, if a prefix is set, and it does not start with `/`, `!`, `.` or `$`.

Before reading:

* links are replaced by the word *link*;
* mentions are read as names;
* emojis are removed when *Skip emojis* is on;
* messages of more than **200 characters** are not read.

When the author of a message is not the author of the previous message read, the bot says the name first, then the message: for example *Alex said: hello*. The word *said* follows the language of the server (*Alex a dit* in French). This can be turned off with *Say the author*.

**Anti-spam**: a member who sends 5 messages with an average gap under 1.5 seconds is ignored for 10 seconds. A channel that receives 10 messages with an average gap under 0.5 second is paused for 5 seconds.

**Queue**: up to **5 texts** wait behind the one being read. Beyond that, the bot answers *Too many texts are waiting to be read, please wait a moment.*

## Read a text once: `/tts say`

* The text can have up to **500 characters**. Longer texts are refused.
* The language is detected automatically when you leave it empty.
* The text is read in your voice channel, or in the voice channel the bot is already in on this server.
* Requires **your own** top.gg vote in the last 24 hours, even on a premium server.
* One use every 5 seconds per member.

## Voices

Each person who writes during a session gets **a voice of their own**, kept until the session ends, so that listeners can tell who is talking.

The voice of a person is chosen in this order:

1. their own voice, if they chose one with `/tts voice` and are allowed to;
2. otherwise, the first free voice in the **order of the server** (set on the dashboard);
3. when there are more people than voices, the voices are given in turn.

Voices that the server switched off are never used. The voice of `/tts say` (texts with no author) is the **default voice** of the server, set on the dashboard.

### `/tts voice`

* `/tts voice` without argument shows your voice. `/tts voice <voice>` chooses one; the names are suggested as you type.
* With the `reset` option set to true, `/tts voice` removes your choice: you get an automatic voice again.
* Refused when the server turned off *Members choose their voice*, or when you are not allowed by *Choose a voice*.

## Settings

Open them with `/tts settings` (Manage Server) or on the dashboard page [Text to speech settings](../website/dashboard/tts-settings.md). Each change is saved at once in the panel.

| Setting | Default | What it does |
| --- | --- | --- |
| Read messages automatically | On | Reads the messages of allowed members without a command. |
| Say the author | On | Says the name when the author changes. |
| Read the chat of voice channels | On | Also reads the chat of the voice channel the bot is in. |
| Ignore bots | On | Messages written by bots are not read. |
| Ignore the audience of stages | On | Members of the audience of a stage are not read. |
| Author in voice only | On | Only the members in the voice channel of the bot are read. |
| Skip emojis | Off | Emojis are removed before reading. |
| Members choose their voice | On | Allows `/tts voice`. |
| Prefix | None | Only messages starting with this prefix are read; the prefix is not said. Up to 10 characters. |

### Permissions

Three permissions decide who can use the features. Each one is either **Everyone** (default) or **Only the chosen roles and members** (by role or by Discord ID). Members with *Manage Server* can always use them.

| Permission | Who it applies to |
| --- | --- |
| Start and stop | `/tts start` and `/tts stop` |
| Automatic reading | Whose messages are read automatically |
| Choose a voice | `/tts voice` |

## Voices of the server (dashboard)

On the dashboard page [Text to speech settings](../website/dashboard/tts-settings.md), the **Voices** card lists the voices of the server. An administrator can:

* switch a voice on or off (a switched off voice is never given);
* change the **order** of the voices, by dragging them or with the arrow buttons: the first voices are given first;
* choose the **default voice**, used by `/tts say`. A disabled voice cannot be the default one, and at least one voice must stay on.

## TTS channels

A TTS channel reads **every message** posted in it, for the members who are in a voice channel.

| Command | Description |
| --- | --- |
| `/tts-channel set channel [language] [translate-to] [voice-channel]` | Reads the messages of `channel`. `language` is detected for each message when empty. `translate-to` translates each message before reading it (**premium**). `voice-channel` chooses the voice channel where they are read (by default, the voice channel of the author). |
| `/tts-channel remove channel` | Stops reading the channel. |
| `/tts-channel list` | Lists the channels read aloud, with their language (`auto` when detected) and translation. |
| `/tts-channel manage` | Manages them with buttons and menus. |

* A message is read when its author is in a voice channel. The bot joins that channel, or ignores the message if it is busy in another voice channel of the server.
* Messages of more than **200 characters** (after links are removed) are ignored. Messages from bots, messages with no text, and messages starting with `/`, `!`, `.` or `$` are ignored.
* **Limit**: 5 TTS channels per server, **25 with premium**.
* The same anti-spam rules as in a session apply.
* The channels are also on the dashboard page [Text to speech](../website/dashboard/tts-channels.md).
