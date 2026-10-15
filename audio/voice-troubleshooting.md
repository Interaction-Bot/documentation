---
description: The bot does not join, does not speak, does not transcribe or does not record? Check these points.
---

# Voice troubleshooting

## Quick checklist

1. **Does the bot have *Connect* and *Speak*** in the voice channel? See [Permissions](voice.md#permissions).
2. **Is the feature allowed?** `/tts say` and `/connect` need **your own** vote (even on a premium server). `/tts start`, `/record start` and TTS channels need a premium server or a vote from a member of the server. `/transcribe start` needs a premium server or your vote. See [Access](voice.md#access).
3. **Are you allowed by the server?** Some text to speech actions can be limited to chosen roles and members. See [Text to speech settings](../website/dashboard/tts-settings.md#permissions).
4. **Is the bot already busy?** It can be connected to another voice channel of the server, already reading, transcribing or recording.
5. **Is the text short enough?** `/tts say` refuses texts over 500 characters, and TTS channels and sessions ignore messages over 200 characters.
6. **Is the bot still in the channel?** It leaves 30 seconds after the last human left. A text to speech session has no other timeout: it ends with `/tts stop`, the daily limit, or a disconnection.
7. **Is the daily time used up?** Check it with [`/limits`](limits.md).

## Permissions

| Where | Needed for | Permissions |
| --- | --- | --- |
| Voice channel | `/tts start`, `/tts say`, `/connect`, TTS channels, transcription, recording | **Connect**, **Speak** |
| Voice channel | Automatic transcription (checked before it starts) | **Connect**, **Speak** |
| Text channel of the transcription | Transcription output | **Send Messages**; **Embed Links** for the *embed* style; **Manage Webhooks** for the *webhook* style |
| Text channel of a TTS channel | Reading the messages | **View Channel**, **Read Message History** |

{% hint style="info" %}
The bot does not warn you when automatic transcription cannot start because of a missing permission: it simply does not start. Check the permissions of the voice channel and of the text channel first.
{% endhint %}

## Messages and fixes

These are the messages the bot shows, with the exact text.

### Connection

| Message | Cause and fix |
| --- | --- |
| *⛔ You are not connected to a voice channel.* | Join a voice channel first (or give the channel in the command). |
| *⛔ I'm not able to connect to the voice channel.* | The bot could not connect: check that it has **Connect** in that channel, then try again. The message is also shown when the connection times out. |
| *⛔ I'm already connected to a voice channel.* | `/connect` was run for the channel where the bot already is. |
| *⛔ I'm not connected to a voice channel.* | `/disconnect` was run while the bot is not connected. |
| *⛔ I'm not connected to this voice channel.* | `/disconnect` was run with a channel the bot is not in. |
| *⛔ I'm not able to disconnect from the voice channel.* | The bot could not leave. Try again. |
| *⛔ You need to vote for the bot to use this command.* | Vote on [top.gg](https://top.gg/bot/893494390142697493/vote) (valid 24 hours), or ask for a premium server. Shown for `/tts say`, `/connect` and `/transcribe start`. |
| *Vote to unlock speech to text and text to speech* (embed in a text channel) | Automatic transcription, a TTS channel or a session is blocked: one vote from a member of the server unlocks it for 24 hours. This message is posted at most once a day. |
| *⛔ You are on cooldown. Try again in {time} seconds.* | The voice commands have a short cooldown per member: 5 seconds for `/tts say` and `/tts start`, 3 seconds for `/tts stop`. Wait and run the command again. |

### Text to speech

| Message | Cause and fix |
| --- | --- |
| *⛔ You are not allowed to use this on this server.* | The server limits `/tts start` or `/tts stop` to chosen roles and members. Ask a member with *Manage Server*. |
| *⛔ I am already reading in another voice channel.* | `/tts start` was run while the bot reads in another voice channel of the server. Run `/tts stop` there first. |
| *⛔ The text is too long (maximum 500 characters).* | `/tts say` accepts 500 characters at most. Split the text. |
| *⛔ Too many texts are waiting to be read, please wait a moment.* | The queue of 5 texts is full. Wait, or run `/tts stop` to empty it. |
| *There is nothing to stop.* | `/tts stop` was run while the bot was not reading or connected. |
| *⛔ The voices are not available right now, try again later.* | The list of voices could not be loaded. Try again in a moment. |
| *⛔ You are not allowed to choose a voice on this server.* | `/tts voice` is limited by the permission *Choose a voice*. |
| *⛔ This voice does not exist on this server, or it is switched off.* | Pick a voice from the suggestions of `/tts voice`. |
| *The translation api seems to be inaccessible. Please try again later.* | The text could not get its speech from the service. It is also shown when the bot refuses the text for flood protection. Try again later. |
| *⛔ This language is not supported by the bot.* | The language name was not recognised. Pick it from the suggestions of the option. |
| *⛔ You reached the maximum number of TTS channels of this server (5, or 25 with premium).* | Remove a TTS channel with `/tts-channel remove`, or get premium. |
| *⏹️ Text to speech has stopped: the daily limit is reached, the bot leaves the voice channel.* | The daily text to speech time of the server is used up. The message says when it starts again. See [Daily limits](limits.md). |

### Transcription

| Message | Cause and fix |
| --- | --- |
| *⛔ I'm already transcribing a voice channel.* | A transcription is already running on the server. Stop it with `/transcribe stop`. |
| *⛔ Too many voice channels are being transcribed right now, please try again in a few minutes.* | The service is at its limit of simultaneous transcriptions. Try again later. |
| *⛔ You do not have permission to execute this command.* | `/transcribe stop` was run by a member who may not stop it. See [Daily time and stop](voice.md#daily-time-and-stop). |
| *⛔ I am missing permissions in #channel: I need to send messages there (and to embed links in the embed style). Please give them to me or choose another style.* | The bot cannot post in the chosen channel. Fix the permissions or change the style. |
| *⛔ The translation of the transcription is reserved for premium servers.* | `translate_to` needs a premium server. Start the transcription without it. |
| *✅ The transcription has been stopped.* | The transcription ended: stopped by a member, or the bot left the channel. |
| *⏱️ This server has used all its daily transcription time (3 h), the transcription has been stopped. It will be available again …* | Premium servers: the 3 hours of the day are used. The message gives the time when it is available again. |
| *⏱️ This server has used its 30 free minutes of transcription for today, the transcription has been stopped. … Premium servers can transcribe up to 3 hours per day.* | Free servers: the 30 minutes of the day are used. The time adds up across sessions and is available again at the time given in the message. |
| *⏱️ Sorry, this server has used all its daily transcription time. It will be available again …* | `/transcribe start` (or the automatic transcription) was refused because the time of the day is already used. Wait for the time given in the message. |
| *⛔ I'm not able to use the speech recognition api.* | The speech service failed 5 times in a row, so the transcription stopped. Try again later. |

### Recording

| Message | Cause and fix |
| --- | --- |
| *⛔ Join a voice channel first (stage channels cannot be recorded).* | Join a standard voice channel, then run `/record start`. |
| *⛔ Recording needs a vote on top.gg (for the whole server, valid 24 hours) or a premium server.* | Ask a member of the server to vote, or get premium. |
| *⛔ Keeping the recording when the channel is empty is a premium feature.* | `/record start continuous:true` needs a premium server. |
| *⛔ A recording is already running on this server.* | Only one recording runs per server. Use `/record stop` on the running one. |
| *⛔ The bot is busy on this server (another voice channel, or a transcription). Try again later.* | The bot is connected elsewhere on the server. Wait, or stop the other activity. |
| *⛔ Recording is disabled on this server.* | The server turned recording off on the dashboard. |
| *⛔ You are not allowed to record on this server.* | The server limits who can start a recording. Ask a member with *Manage Server*. |
| *⛔ The bot could not join the voice channel. Try again.* | Check the **Connect** permission, then try again. |
| *⏱️ This server has used all its daily Recording time (1 h). It resets …* | The daily recording time of a free server is used up. Premium servers have 6 hours. |

## Typical problems

| Symptom | Cause and fix |
| --- | --- |
| `/tts say` refuses on a premium server with the vote message | `/tts say` and `/connect` check the vote of **the member who runs them**. Vote, or ask a member who voted to run the command. `/tts start` only needs a vote from any member of the server, or a premium server. |
| The bot does not join | The member is not in a voice channel (see the messages above), or the bot lacks **Connect** in that channel. |
| The bot joins but says nothing | Missing **Speak**, or the text was refused (see above). Check the permission *Automatic reading* on the [Text to speech settings](../website/dashboard/tts-settings.md) page, and that the author is in the voice channel of the bot if *Author in voice only* is on. |
| The bot does not read the messages of a member | The member does not have *Automatic reading*, the message starts with the prefix setting that it does not have, it is longer than 200 characters, or the author is a bot while *Ignore bots* is on. |
| The bot does not say the name of the author | *Say the author* is off on the [Text to speech settings](../website/dashboard/tts-settings.md) page, or the same author wrote the previous message. |
| The bot reads the same person with the wrong voice | Each person keeps the voice given at the start of the session. Run `/tts stop` then `/tts start` to give the voices again. |
| The bot does not read a TTS channel message | Check that the author is in a voice channel, that the message has text and is not longer than 200 characters, and that it does not start with `/`, `!`, `.` or `$`. The bot also skips messages while it is connected to another voice channel of the server, and ignores a member who posts 5 messages with an average gap under 1.5 seconds (for 10 seconds). |
| A TTS channel is read in the wrong language | Set the **language** of the channel (`/tts-channel set`, or the dashboard). Automatic detection is used when none is set. |
| Automatic transcription does not start | A permission is missing (nothing is posted), the server has no vote, the bot is busy in another voice channel or already transcribing, or the member joined another voice channel than the one configured. |
| Only some words are transcribed | Very short sounds, quiet sounds and noise are ignored. Speak closer to the microphone, and avoid overlapping voices. The speech service may also skip unclear parts. |
| Transcriptions are plain messages, not webhooks | The bot lacks **Manage Webhooks** in that channel. Give it the permission, or choose the *message* style. |
| The translation is not posted | Translation is premium only. On a premium server, the original text is posted when the translation fails. |
| The transcription stops by itself | The daily time of the server was used up (30 minutes free, 3 hours premium, counted from midnight UTC), the bot was disconnected, or the speech service failed 5 times in a row. |
| A `/disconnect` vote never completes | When `/disconnect` is run without a channel, the vote buttons do not count the votes. Run `/disconnect` again with the `channel` option filled in, then vote. |
| The language of the speech is wrong | Set the **language** option (`/transcribe start` or `/transcribe auto enable`), or the language of the configuration on the dashboard. |
| I cannot find my recording | `/record list` shows your recordings on the server. Recordings are deleted after 7 days (free) or 30 days (premium). |

Still stuck? Join the [support server](https://discord.gg/wjWjf6mCjf). To check a working setup step by step, see the [Voice guides](voice-guides.md).
