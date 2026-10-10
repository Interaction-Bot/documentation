---
description: Commands that use the voice channels (text to speech and transcription).
---

# Voice (TTS and transcription)

{% hint style="info" %}
`/connect` and `/tts` require that you voted for the bot on [top.gg](https://top.gg/bot/893494390142697493/vote) in the last 24 hours.
{% endhint %}

| Command                 | Description                                                                                                                                  |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| `/connect [channel]`    | Connect the bot to a voice or stage channel. Without `channel`, the bot joins the channel you are in. If the bot is already connected somewhere, members vote (60 seconds) to move it. |
| `/disconnect [channel]` | Disconnect the bot from the voice channel. A vote is started if several members are in the channel. The bot also leaves when the channel is empty. |
| `/tts <query>`          | Text to speech: the bot reads the text (maximum 500 characters) in the voice channel. It joins your voice channel if it is not connected yet. |
| `/transcribe start [channel]` | Transcribe the voice channel into a text channel (English only, beta).                                                                 |
| `/transcribe stop`      | Stop the transcription (a vote is started if several members are in the channel).                                                            |

{% hint style="warning" %}
The transcription (speech to text, `/transcribe`) is **currently disabled** while it is being rebuilt. The command answers that the feature is disabled.
{% endhint %}

## Text to speech

1. Join a voice channel.
2. Run `/tts query: Hello everyone`.
3. The bot joins your channel and says the text.

The bot needs the permissions *Connect* and *Speak* in the voice channel.
