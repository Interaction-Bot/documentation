---
description: The audio changes of the next update of Interaction Bot, not yet released.
---

# Unreleased

The audio changes below are being prepared. They are listed here as they are in the bot, the website and the translation API. Limits are given as **Free / Premium**.

## Daily limits

* Transcription and text to speech: **30 minutes per day** (Free) / **3 hours per day** (Premium), per server.
* Recording: **1 hour per day** (Free) / **6 hours per day** (Premium), per server.
* The day starts at **midnight UTC**. Notices at 80 % and 100 % of the day, and [`/limits`](../audio/limits.md) shows the time used and left.
* See [Daily limits](../audio/limits.md).

## Text to speech

* `/tts start` makes the bot join your voice channel and read the messages of the chat and of the voice channel, for as long as you want. `/tts stop` ends it.
* Automatic reading of the messages during a session, with the name of the author said when it changes.
* `/tts say` reads one text (up to 500 characters). `/tts-stop` is replaced by `/tts stop`, and `/tts <text>` by `/tts say`.
* Each person gets **their own voice** in a session. `/tts voice` lets members choose it. The server sets the order of the voices, switches them off and chooses the default voice, on the dashboard.
* **Text to speech settings** page: reading settings, prefix, and who can start and stop, read automatically, or choose a voice. `/tts settings` shows the same settings with buttons.
* See [Text to speech commands](../commands/tts.md).

## Recording

* `/record start`, `/record stop` and `/record list`: one track per speaker and a mix, encrypted, aligned in time.
* Continuous recording for premium servers (24 hours at most).
* Announcement to each member who joins a recording, in the text channel and out loud. The announcement is not part of the recording.
* The link is sent in private messages. Recordings are kept **7 days** (Free) / **30 days** (Premium) and downloaded from the website after logging in with Discord.
* A recording can also be started from the live transcription Activity, with the **Record the audio** button.
* See [Recording commands](../commands/record.md) and the [Voice recording](../website/dashboard/voice-recording.md) page.

## Speech to text

* Live transcription in the Discord Activity with `/transcribe live`, and its settings on the [Speech to text](../website/dashboard/speech-to-text.md) page.
* Transcript recording (text only) with `/transcribe record start` and `stop`.

## Temporary voice channels

* `/tempvoice setup` creates a **Join to create** channel. Each member who joins it gets a voice channel of their own, with a control panel of 15 buttons.
* 21 `/voice` subcommands for the owner, `/find`, `/join`, context menus, a vote kick between the members of the channel, and a moderation log.
* Settings on the [Temp voice](../website/dashboard/temp-voice.md) page. No top.gg vote is needed.
* See [Temporary voice channels](../commands/tempvoice.md).

## Commands page

* The website has a [Commands](https://interaction-bot.com/commands) page with every slash command, grouped by feature, with search, copy and the permissions of each command.
