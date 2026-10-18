---
description: Read aloud the messages of text channels in voice channels.
---

# Text to speech

<figure><img src="../../.gitbook/assets/dash-text-to-speech.png" alt="Text to speech page"><figcaption><p>Text to speech page</p></figcaption></figure>

## Localization

Navbar > category _**Audio & AI**_ > _**Text to speech**_.

## What it does

Each message posted in a TTS channel is **read aloud in the voice channel of its author**, or in the **destination** voice channel when one is set. The bot joins the channel when needed. Without destination, only the members who are in a voice channel are read. The same can be done with the command [`/tts-channel`](../../audio/voice.md#tts-channels).

The page lists the **TTS channels** of the server. The list is saved as a whole: each _Save_ replaces the previous list. The page has three tabs: *Reading channels* (this page), *Settings* and *Permissions*.

## Configure a TTS channel

Click on _**Add a channel**_ and set:

* **Channel**: a text channel of the server. A channel can be used only once.
* **Language of the messages**: _Auto-detect_ (default) or a language. With _Auto-detect_, the language is detected for each message.
* **Translate to** (optional): translate each message into this language before it is read. Default: _No translation_.
* **Destination** (optional): the voice channel where the messages are read. Default: the voice channel of the person who writes. The bot only joins a channel where someone is.
* **Enabled**: switch a channel off without removing it. A disabled channel is kept in the list but not read.

Click _**Remove**_ to stop reading a channel. When you are done, click _**Save**_. _**Cancel**_ restores the last saved list.

After a save, the bot reloads the channels at once: no restart is needed.

## Settings

The **Settings** tab holds the reading options. Each has a switch, saved with the *Save* bar:

| Option | Default | What it does |
| --- | --- | --- |
| Read messages automatically | On | Reads the messages of allowed members during a session (`/tts start`), without `/tts say` each time. |
| Say who wrote | On | Says "Alex said" when the author changes. |
| Read the chat of voice channels | On | Also reads the messages written in the chat of a voice channel the bot is in. |
| Ignore bots | On | Messages written by bots are not read. |
| Ignore the audience of stages | On | Messages from the audience of a stage channel are not read. |
| The author must be in the voice channel | On | Only reads the members who are in the bot's voice channel. |
| Skip emojis | Off | Emojis are removed before reading. |
| Members can choose their voice | On | `/tts voice` works on the server. |
| Cloned voices allowed | On | Premium members can read with their own cloned voice. |

Also the **Prefix** field (10 characters maximum): when set, only the messages that start with it are read, and the prefix is not said.

Also the **Voices** card: the voices of the server, in the order they are given to the members of a session. Each voice can be enabled, made the default, and moved up or down. At least one voice stays enabled, and the default voice cannot be disabled. Changes are saved with the same *Save* bar. See [Voices and cloning](../../audio/voices-and-cloning.md#the-voice-catalogue).

## Permissions

The **Permissions** tab has three rules, each one *Everyone* or *Only the chosen roles and members*:

* **Start and stop** (`/tts start`, `/tts stop`);
* **Automatic reading** (messages read during a session);
* **Choose a voice** (`/tts voice`).

Members with *Manage Server* are always allowed.

## Limits

| Free       | Premium     |
| ---------- | ----------- |
| 5 channels | 25 channels |

Adding a channel beyond the limit opens the premium window. The translation of messages is a premium feature: on a free server the *Translate to* field is locked.

## What is read

* Messages are read **up to 200 characters**. A longer message is not read.
* Messages from bots, messages without text (attachments only) and messages starting with `/`, `!`, `.` or `$` are not read.
* Links are removed and mentions are read as names.
* A member who posts many messages very quickly is **temporarily ignored**: 5 messages with an average gap under 1.5 seconds block this member for 10 seconds. A channel that receives 10 messages with an average gap under 0.5 second is paused for 5 seconds.
* Messages are read one after the other. Up to 5 messages can wait in the queue of the voice channel.

## Access

Voice features need a **premium server**, or a **[top.gg vote](https://top.gg/bot/893494390142697493/vote)** from a member of the server in the last 24 hours. When neither is true, the bot posts a message asking for a vote in the TTS channel, at most once a day.

{% hint style="info" %}
The bot must be able to view the channel and read its messages, and to connect and speak in the voice channels. See [Voice troubleshooting](../../audio/voice-troubleshooting.md) for the messages and fixes, and [Voice guides](../../audio/voice-guides.md#2-read-a-text-channel-aloud-tts-channel) for a step by step setup.
{% endhint %}
