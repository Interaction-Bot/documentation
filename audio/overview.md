---
description: Text to speech and speech to text in voice channels, and which one to choose.
---

# Audio overview

Interaction Bot can **speak** in a voice channel (text to speech, TTS) and **write down** what members say in a voice channel (speech to text, STT, also called transcription). Both can be combined with [translation](../translation/overview.md): a text can be translated before it is read aloud, and a transcription can be translated before it is posted.

## Choose your feature

| I want to...                                                          | Use                                                                 | Needs the dashboard |
| --------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------- |
| Have the bot read a text aloud, once                                  | [`/tts say`](voice.md#tts-say)                                      | No                  |
| Have the bot read every message of a text channel to the members in voice | [TTS channels](voice.md#tts-channels)                           | Optional            |
| Read the messages of a voice channel session, without a command for each message | [`/tts start`](voice.md#tts-start-session)                | Optional (`/tts settings`) |
| Choose a voice, or use my own cloned voice                            | [`/tts voice`](voices-and-cloning.md#choose-your-voice-tts-voice), [`/tts clone`](voices-and-cloning.md#cloned-voices) | Optional ([My voice](../website/my-voice.md) for the clone) |
| Transcribe a voice channel on demand                                  | [`/transcribe start`](voice.md#transcription-speech-to-text)        | No                  |
| Transcribe automatically when someone joins a voice channel           | [Automatic transcription](voice.md#automatic-transcription)         | Optional            |
| See the transcription live, line by line, in a Discord Activity       | [Live transcription](live-transcription.md) (`/transcribe live`)    | Optional (the live view can be turned off) |
| Manage the automatic transcription with a panel                       | `/transcribe auto manage`                                           | Optional            |
| Read the transcription in another language                            | [Transcription with translation](voice.md#translation)              | Optional            |

## Before you start

* Voice features need a **premium server** or a **vote on top.gg**. The exact rule depends on the command, see [Access](voice.md#access).
* The bot needs **Connect** and **Speak** in the voice channel, and permission to post in the text channel of a transcription, see [Permissions](voice.md#permissions).
* A free server can transcribe 30 minutes per day, a premium server 3 hours. The day starts again at midnight UTC. See [Daily time and stop](voice.md#daily-time-and-stop) and [Limits and privacy](limits-and-privacy.md).
* Text to speech counts towards a daily time per server: 30 minutes free, 3 hours premium, reset every day at midnight UTC.

## Where to configure

* On the dashboard: [Text to speech](../website/dashboard/tts-channels.md) (tabs *Reading channels*, *Settings* and *Permissions*) and [Speech to text](../website/dashboard/speech-to-text.md), including the settings of the live view.
* On Discord: `/tts settings` for the text to speech settings of the server, and `/tts-channel manage` for the TTS channels.
* With commands: the full reference is [Voice (TTS and transcription)](voice.md).

## Learn more

* [Voice guides](voice-guides.md): step-by-step examples.
* [Voice troubleshooting](voice-troubleshooting.md): messages and fixes.
