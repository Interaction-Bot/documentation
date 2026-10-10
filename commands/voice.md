---
description: Text to speech and speech to text (transcription) in voice channels.
---

# Voice (TTS and transcription)

{% hint style="info" %}
Voice features work on a **premium** server, or when a member voted for the bot on [top.gg](https://top.gg/bot/893494390142697493/vote) during the last 24 hours (a vote can be done every 12 hours, `/reminder` notifies you). For `/transcribe start`, premium servers do not need the vote.
{% endhint %}

The bot needs the permissions *Connect* and *Speak* in the voice channel (and *View Channel*, *Send Messages* in the text channel for the transcription).

## Commands

| Command                    | Description                                                                                                                                                                                       |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `/connect [channel]`       | Connect the bot to a voice or stage channel (your channel by default). If it is already connected elsewhere, members vote (60 seconds) to move it; administrators do not need the vote.     |
| `/disconnect [channel]`    | Disconnect the bot (with a vote when several members are in the channel). The bot also leaves 30 seconds after the last human left the channel, and after 5 minutes without speech.             |
| `/tts <query> [language]`  | Text to speech. The bot reads the text (maximum 500 characters) in your voice channel and joins it if needed. Messages are queued (up to 5 waiting). The language is detected automatically if empty. |
| `/tts-stop`                | Stop the speech in progress and empty the queue.                                                                                                                                                  |
| `/tts-channel set <channel> [language] [translate_to]` | Read aloud the messages of a text channel, in the voice channel of their author. The language is detected for each message if empty; `translate_to` translates each message before reading it. Requires *Manage Server*. |
| `/tts-channel remove <channel>` | Stop reading a channel.                                                                                                                                                                      |
| `/tts-channel list`        | List the channels read aloud.                                                                                                                                                                     |
| `/transcribe start [channel] [language] [translate_to] [style]` | Transcribe the voice channel you are in into a text channel. See below.                                                                                                      |
| `/transcribe stop`         | Stop the transcription (vote needed when several members are in the channel).                                                                                                                     |
| `/transcribe auto enable [voice_channel] [text_channel]` | Start the transcription automatically when someone joins the voice channel (any voice channel if empty). Requires *Manage Server*.                                          |
| `/transcribe auto disable` | Disable the automatic transcription.                                                                                                                                                              |

## Text to speech (TTS)

* Supports 52 languages, the language of the text is detected automatically.
* Links, mentions, code blocks and markdown are cleaned before reading.
* In a **TTS channel**, messages are read up to 200 characters. Free servers: up to 5 TTS channels, premium: up to 25. A member who sends many messages very quickly is temporarily ignored (anti-spam).
* TTS channels and their language can also be configured on the dashboard ([TTS channels](../website/dashboard/tts-channels.md)).

## Transcription (speech to text)

* Multilingual: the spoken language is detected automatically, or you can set `language`.
* `translate_to` also translates what is said (**premium only**). With a translation, only the translation is shown.
* `style`: how the transcription is posted: `webhook` (default, as if the speaker wrote it), `message` or `embed`.
* Session length: **30 minutes** on free servers, **2 hours** on premium servers. Sessions are limited per cluster; if the service is busy, retry later.
* Settings made on the dashboard ([Speech to text](../website/dashboard/speech-to-text.md)) apply live to the running session.
* The bot leaves an automatic session 30 seconds after the last human left.
