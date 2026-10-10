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

## Step by step

### Read a text aloud (`/tts`)

1. Join a voice channel (the bot joins it for you).
2. Type `/tts query:<text>`. The language is detected, or choose `language`.
3. The bot reads the text. Several `/tts` are queued (up to 5 waiting). Use `/tts-stop` to cut the speech and empty the queue.

### Read a text channel aloud (TTS channel)

1. Run `/tts-channel set channel:#chat` (or use the [dashboard](../website/dashboard/tts-channels.md)). Optionally set `language` and `translate_to`.
2. Join a voice channel and write in `#chat`: the bot joins **your** voice channel and reads your message.
3. `/tts-channel list` shows the channels, `/tts-channel remove` stops one.

{% hint style="info" %}
Messages longer than 200 characters are not read. A member who sends many messages in a few seconds is ignored for a moment, and a channel that receives a burst of messages is slowed down too.
{% endhint %}

### Transcribe a voice channel

1. Join the voice channel.
2. In the text channel where the text must appear, type `/transcribe start`. Optionally set `language` (the language spoken), `translate_to` (premium) and `style`.
3. Speak: the bot posts what is said, under the name of the speaker (webhook style).
4. End with `/transcribe stop`, or wait for the end of the session (30 minutes free, 2 hours premium).

To start it **automatically** when someone joins a voice channel, use `/transcribe auto enable` or the [Speech to text](../website/dashboard/speech-to-text.md) page.

## Good to know

| Topic                | Behaviour |
| -------------------- | --------- |
| Who can use TTS     | Premium servers, or any member who voted on top.gg in the last 24 hours. |
| Who can transcribe  | Premium servers, or a member who voted. Premium servers do not need a vote. |
| Several people speak | Each speaker is transcribed separately, with their own name. |
| The bot leaves       | 30 seconds after the last human left, after 5 minutes without speech (TTS), or at the end of the session time. |
| Service busy         | The number of simultaneous transcriptions is limited; retry a bit later. After 5 consecutive failures of the service the session stops by itself. |
| Commands cooldown   | `/tts` once every 5 seconds per member, `/tts-stop` every 3 seconds. |

## Troubleshooting

| Symptom                                              | What to check |
| ---------------------------------------------------- | ------------- |
| The bot does not join                                | *Connect* and *Speak* permissions in the voice channel, and that the channel is not full. |
| Nothing is read in a TTS channel                     | You must be in a voice channel; the message must be 200 characters or fewer and contain readable text. Check the vote or premium. |
| "You need to vote" message                           | Vote on [top.gg](https://top.gg/bot/893494390142697493/vote); you can vote every 12 hours, `/reminder enable` notifies you. |
| The transcription is empty or in the wrong language  | Set the `language` of the speakers; check that the bot has *View Channel* and *Send Messages* (and *Manage Webhooks* for the webhook style). |
| The transcription stops after a while                | The session reached its limit (30 min free, 2 h premium): start it again. |
