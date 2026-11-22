---
description: Text to speech and speech to text in voice channels, and which one to choose.
---

# Audio overview

Interaction Bot can **speak** in a voice channel (text to speech, TTS) and **write down** what members say in a voice channel (speech to text, STT, also called transcription). Both can be combined with [translation](../translation/overview.md): a text can be translated before it is read aloud, and a transcription can be translated before it is posted.

## Choose your feature

| I want to... | Use | Where it is set |
| --- | --- | --- |
| Have the bot read a text aloud, once | [`/tts say`](voice.md#tts-say) | No setting needed |
| Have the bot read the messages of a text channel, a forum or a server | [TTS rules](voice.md#tts-channels) | Dashboard, [Text to speech](../website/dashboard/tts-channels.md) |
| Read the messages of a voice channel session, without a command for each message | [`/tts start`](voice.md#tts-start-session) | Dashboard, [Text to speech](../website/dashboard/tts-channels.md#settings) (reading options) |
| Choose a voice, or use my own cloned voice | [`/tts voice`](voices-and-cloning.md#choose-your-voice-tts-voice), [`/tts clone`](voices-and-cloning.md#create-a-cloned-voice-tts-clone-create) | Dashboard, [My voice](../website/my-voice.md) for the clone |
| Transcribe a voice channel on demand | [`/transcribe start`](voice.md#transcribe-start) | No setting needed |
| Transcribe automatically when someone joins a voice channel | [Automatic transcription](voice.md#automatic-transcription) | Dashboard, [Transcription](../website/dashboard/speech-to-text.md) |
| See the transcription live, line by line, in a Discord Activity | [Live transcription](live-transcription.md) (`/transcribe live`) | Dashboard, [Transcription](../website/dashboard/speech-to-text.md#live-transcription-activity) |
| Read the transcription in another language | [Transcription with translation](voice.md#translation) | Dashboard, [Transcription](../website/dashboard/speech-to-text.md) (premium) |
| Transcribe a voice message | [Voice messages](voice-messages.md) | Right-click menu, or automatic on the dashboard |

## Before you start

* Voice features need a **premium server** or a **vote on top.gg**. The exact rule depends on the command, see [Access](voice.md#access).
* The bot needs **Connect** and **Speak** in the voice channel, and permission to post in the text channel of a transcription, see [Permissions](voice.md#permissions).
* Speech to text: a free server can transcribe 30 minutes per day, a premium server 3 hours. Text to speech has the same daily time. The day starts again at midnight UTC. See [Daily time and stop](voice.md#daily-time-and-stop) and [Limits and privacy](limits-and-privacy.md#daily-limits).

## Where to configure

* On the dashboard, in the category **Audio & AI**:
  * [Transcription](../website/dashboard/speech-to-text.md): the rules that say which voice channels are transcribed and where the text goes, and the live transcription settings.
  * [Text to speech](../website/dashboard/tts-channels.md): the rules that say which messages are read, the reading options, the voices and who can use the feature.
  * [Voice recording](../website/dashboard/voice-recording.md) and [Temp voice](../website/dashboard/temp-voice.md).
* In the translation category, [Voice messages](../website/dashboard/voice-messages.md) sets how voice messages are transcribed and translated.
* With commands: the full reference is [Voice (TTS and transcription)](voice.md). The bot has no command for the rules: they are set on the dashboard, or with the assistant `/ai setup`.

## Learn more

* [Voices and cloning](voices-and-cloning.md): the voices of the reading, and your own cloned voice (Premium).
* [Voice recording](recording.md): `/record`, one track per speaker.
* [Temporary voice channels](tempvoice.md): members who get their own voice channel.
* [Voice guides](voice-guides.md): step-by-step examples.
* [Voice troubleshooting](voice-troubleshooting.md): messages and fixes.
