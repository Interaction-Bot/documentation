---
description: The voice features of Interaction Bot, text to speech, transcription, recording and temporary voice channels, and which one to choose.
---

# Audio overview

Interaction Bot works with voice channels in several ways:

* **Text to speech** (TTS): the bot **reads text aloud** in a voice channel.
* **Speech to text** (STT, also called transcription): the bot **writes down** what members say.
* **Recording**: the bot **records** a voice channel, one track per speaker.
* **Temporary voice channels**: each member who wants one gets **a voice channel of their own**.

Text to speech and transcription can be combined with [translation](../translation/overview.md): a text can be translated before it is read aloud, and a transcription can be translated before it is posted.

## Choose your feature

| I want to... | Use | Needs the dashboard |
| --- | --- | --- |
| Have the bot read a text aloud, once | [`/tts say`](../commands/tts.md) | No |
| Have the bot read the messages of a chat, for as long as I want | [`/tts start`](../commands/tts.md#start-a-session-tts-start) | Optional |
| Have the bot read every message of a text channel | [TTS channels](../commands/tts.md#tts-channels) | Optional |
| Choose the voice that reads my messages | [`/tts voice`](../commands/tts.md#voices) | Optional |
| Transcribe a voice channel on demand | [`/transcribe start`](voice.md#transcription-speech-to-text) | No |
| Transcribe automatically when someone joins a voice channel | [Automatic transcription](voice.md#automatic-transcription) | Optional |
| Read the transcription in another language | [Transcription with translation](voice.md#translation) | Optional |
| Record a voice channel, with one track per speaker | [`/record start`](../commands/record.md), or the **Record the audio** button of the Activity | Optional |
| Give each member a temporary voice channel | [Temporary voice channels](../commands/tempvoice.md) | Optional (`/tempvoice setup` does the same) |
| Know how much audio time the server has left today | [`/limits`](limits.md) | No |

## Before you start

* Voice features need a **premium server** or a **vote on top.gg**. The exact rule depends on the command, see [Access](voice.md#access).
* The bot needs **Connect** and **Speak** in the voice channel, and permission to post in the text channel of a transcription, see [Permissions](voice.md#permissions).
* Each feature has a **daily time limit per server**: 30 minutes of transcription and of text to speech, 1 hour of recording on a free server, and 3 hours, 3 hours and 6 hours on a premium server. The limits restart every day at midnight UTC, see [Daily limits](limits.md).
* Recording and transcription cannot run at the same time on the same server: while one runs, the other is refused.

## Where to configure

* On the dashboard, in the category **Audio & AI**: [Text to speech](../website/dashboard/tts-channels.md), [Text to speech settings](../website/dashboard/tts-settings.md), [Speech to text](../website/dashboard/speech-to-text.md), [Voice recording](../website/dashboard/voice-recording.md) and [Temp voice](../website/dashboard/temp-voice.md).
* With commands: the full references are [Text to speech commands](../commands/tts.md), [Voice](voice.md), [Recording commands](../commands/record.md) and [Temporary voice channels](../commands/tempvoice.md).
* The list of every command is on the [Commands](../commands/all-commands.md) page and on the website's [Commands page](https://interaction-bot.com/commands), which has a search.

## Learn more

* [Voice guides](voice-guides.md): step-by-step examples.
* [Voice troubleshooting](voice-troubleshooting.md): messages and fixes.
* [Daily limits](limits.md): the time limits and the `/limits` command.
