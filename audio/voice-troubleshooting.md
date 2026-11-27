---
description: The bot does not join, does not speak, or does not transcribe? Check these points.
---

# Voice troubleshooting

## Quick checklist

1. **Does the bot have *Connect* and *Speak*** in the voice channel? See [Permissions](voice.md#permissions).
2. **Is the feature allowed?** `/tts say`, `/tts start`, `/connect`, `/transcribe start`, `/transcribe live`, the TTS rules and the automatic transcription need a premium server or a vote from a member of the server (valid 24 hours). Starting the live transcription from the Activity also needs *Manage Server*. `/tts voice` and `/tts clone` need no vote. See [Access](voice.md#access).
3. **Is the bot already busy?** It can be connected to another voice channel of the server, or already transcribing.
4. **Is the text short enough?** `/tts say` refuses texts over 500 characters.
5. **Is the bot still in the channel?** It leaves when no feature uses it any more, and when nobody is left in the channel for the delay of the server (30 seconds by default, see [Leave the voice channel](../website/dashboard/overview.md#leave-the-voice-channel)).
6. **Is the daily time used up?** `/limits` shows the time left for transcription, text to speech and recording, and when it resets (midnight UTC).

## Permissions

| Where | Needed for | Permissions |
| --- | --- | --- |
| Voice channel | `/tts say`, `/tts start`, `/connect`, TTS rules, transcription | **Connect**, **Speak** |
| Voice channel | Automatic transcription (checked before it starts) | **Connect**, **Speak** |
| Text channel of the transcription | Transcription output | **Send Messages**; **Embed Links** for the *embed* style; **Manage Webhooks** for the *webhook* style |
| Text channel of a TTS rule | Reading the messages | **View Channel**, **Read Message History** |

The members need the server permission *Start and stop* for `/tts start` and `/tts stop` (dashboard, tab *Permissions*), otherwise the bot answers *⛔ You are not allowed to use this on this server.*

{% hint style="info" %}
The bot does not warn you when automatic transcription cannot start because of a missing permission: it simply does not start. Check the permissions of the voice channel and of the text channel first.
{% endhint %}

## Messages and fixes

These are the messages the bot shows, with the exact text.

| Message | Cause and fix |
| --- | --- |
| *⛔ You are not connected to a voice channel.* | Join a voice channel first (or give the channel in the command). |
| *⛔ I'm not able to connect to the voice channel.* | The bot could not connect: check that it has **Connect** in that channel, then try again. The message is also shown when the connection times out. |
| *⛔ I'm already connected to a voice channel.* | `/connect` was run for the channel where the bot already is. |
| *⛔ I'm not connected to a voice channel.* | `/disconnect` or `/transcribe stop` was run while the bot is not connected. |
| *⛔ I'm not connected to this voice channel.* | `/disconnect` was run with a channel the bot is not in. |
| *⛔ Nobody is in that voice channel. Join it yourself, or choose a channel where other members are.* | `/connect` was given an empty channel. |
| *⛔ I can't join a voice channel that you can't join yourself.* | `/connect` was given a channel you cannot join. |
| *⛔ You need to vote for the bot to use this command.* | Vote on [top.gg](https://top.gg/bot/893494390142697493/vote) (valid 24 hours), or ask for a premium server. Shown for the commands that need a vote. |
| *Reading aloud needs your own vote on top.gg (valid 24 hours), or a premium server.* | Shown by `/tts start`. Vote, or get a premium server. |
| *Vote to unlock speech to text, text to speech and recording* (a message in a text channel) | An automatic feature is blocked: one vote from a member of the server unlocks it for 24 hours. The message is posted at most once a day. Admins can turn it off on the dashboard (Overview). |
| *🗳️ Vote for the bot on top.gg (or use a premium server) to transcribe voice messages.* | The menu *Transcribe voice message* needs a vote or a premium server. |
| *⛔ You are on cooldown. Try again in {time} seconds.* | The voice commands have a short cooldown per member: 5 seconds for `/tts say` and `/tts start`, 3 seconds for `/tts stop` and `/tts voice`. Wait and run the command again. |
| *⛔ The text is too long (maximum 500 characters).* | `/tts say` accepts 500 characters at most. Split the text. |
| *⛔ Too many texts are waiting to be read, please wait a moment.* | The queue of 5 texts is full. Wait, or use `/tts stop`. |
| *There is nothing to stop.* | `/tts stop` was run with no session and nothing to read. |
| *The translation api seems to be inaccessible. Please try again later.* | The speech or translation service could not answer. Try again later. |
| *⛔ This language is currently not supported by the bot.* | The language name was not recognised. Pick it from the suggestions of the option. |
| *⛔ I'm already transcribing a voice channel.* | A transcription is already running on the server. Stop it with `/transcribe stop`. |
| *⛔ Too many voice channels are being transcribed right now, please try again in a few minutes.* | The bot is at its limit of simultaneous transcriptions. Try again later. |
| *⛔ You do not have permission to execute this command.* | `/transcribe stop` was run by a member who may not stop it. See [Daily time and stop](voice.md#daily-time-and-stop). |
| *⛔ I am missing permissions in #channel: I need to send messages there (and to embed links in the embed style). Please give them to me or choose another style.* | The bot cannot post in the chosen channel. Fix the permissions or change the style. |
| *⛔ The translation of the transcription is reserved for premium servers. Get premium or start the transcription without `translate-to`.* | `translate-to` needs a premium server. Start the transcription without it. |
| *✅ The transcription has been stopped.* | The transcription ended: stopped by a member, or the bot left the channel. |
| *⏱️ This server has used all its daily Transcription time (30 min). It resets ...* | Free servers: the 30 minutes of the day are used. The time adds up across sessions, and the counter starts again at midnight UTC. Premium raises the limit to 3 hours. |
| *⏱️ This server has used all its daily Transcription time (3 h). It resets ...* | Premium servers: the 3 hours of the day are used. The countdown gives the reset, at midnight UTC. |
| *⏹️ The transcription has stopped: the daily limit is reached.* | The daily time of the server was used up during the transcription. The bot leaves the voice channel. |
| *⏱️ This server has used all its daily Text to speech time (...). It resets ...* | The limit is 30 minutes free, 3 hours premium, reset at midnight UTC. A warning is posted once at 80 % of the day. `/limits` shows the usage of the server. |
| *⛔ I'm not able to use the speech recognition api.* | The speech service failed 5 times in a row, so the transcription stopped. Try again later. |
| *⛔ I am already reading in another voice channel.* | The bot is connected to another voice channel of the server and you are in a different one. Use `/tts stop` first, or join its channel. |
| *⛔ You are not allowed to use this on this server.* | The member lacks the *Start and stop* permission (or *Choose a voice*, for `/tts voice`). |
| *This voice does not exist on this server, or it is switched off.* | Use the suggestions of `/tts voice`; the server may have switched the voice off. |
| *Choosing a voice is turned off on this server.* | The server did not allow members to choose their voice. |
| Messages about a cloned voice | See [Voices and cloning: Troubleshooting](voices-and-cloning.md#troubleshooting). |

## Typical problems

| Symptom | Cause and fix |
| --- | --- |
| The bot does not join | The member is not in a voice channel (see the messages above), or the bot lacks **Connect** in that channel. |
| The bot joins but says nothing | Missing **Speak**, or the text was refused (see above). `/tts stop` empties the queue. |
| `/tts say` speaks in another voice channel | `/tts say` reads in the voice channel where the bot already is, when you are not in a voice channel. If you are in another one, the command refuses (*I am already reading in another voice channel.*). Use `/tts stop` (or `/disconnect`) first, then `/tts say`. |
| The bot does not read a TTS rule message | Check that the author is in a voice channel (unless the rule has a destination), that the message has text, and that it does not start with `/`, `!`, `.` or `$`. Check that the rule is not paused, and that the **Only members whose mic is muted** option does not hide the author. The bot also ignores a member who posts 5 messages with an average gap under 1.5 seconds (for 10 seconds). Check the **voice channel for reading** of the rule: the message is read there, and only when someone is in that channel. |
| A TTS message is read in the wrong language | Set the **Language** of the rule on the dashboard. Automatic detection is used when none is set. |
| Automatic transcription does not start | A permission is missing (nothing is posted), the server has no vote, the bot is busy in another voice channel or already transcribing, or the member joined a voice channel that no rule covers. |
| Only some words are transcribed | Very short sounds, quiet sounds and noise are ignored. Speak closer to the microphone, and avoid overlapping voices. The speech service may also skip unclear parts. |
| Transcriptions are plain messages, not webhooks | The bot lacks **Manage Webhooks** in that channel. Give it the permission, or choose the *message* style. |
| The translation is not posted | Translation is premium only. On a premium server, the original text is posted when the translation fails. |
| The transcription stops by itself | The daily time of the server was used up (30 minutes free, 3 hours premium, counted per UTC day), the bot was disconnected, or the speech service failed 5 times in a row. |
| The language of the speech is wrong | Set the **Language** of the rule on the [Transcription](../website/dashboard/speech-to-text.md) page, or leave it on automatic detection. |
| The live view (`/transcribe live`) does not open, or says *Connecting to Discord…* forever | See [Live transcription: Troubleshooting](live-transcription.md#troubleshooting). |
| My cloned voice is not used | Creating and using a cloned voice need Premium. The server may refuse them (*Cloned voices allowed*). See [Voices and cloning](voices-and-cloning.md#who-can-create-and-use-a-cloned-voice). |
| My voice changed, or I have the default voice | Your voice is used from your next message when no one else in the channel has it. Otherwise you keep your current voice until you rejoin the channel. A voice given to someone else is not taken away. |

Still stuck? Join the [support server](https://discord.gg/wjWjf6mCjf). To check a working setup step by step, see the [Voice guides](voice-guides.md).
