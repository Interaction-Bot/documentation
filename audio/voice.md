---
description: "Reference of the voice connection rules and of transcription (speech to text). Text to speech is in its own command page."
---

# Voice (connection and transcription)

The bot can join a voice channel to **read text aloud** (text to speech, TTS) and to **write down** what members say (speech to text, STT, also called transcription). This page covers the rules that apply to both, and the transcription. The text to speech commands are in [Text to speech commands](../commands/tts.md).

* Step-by-step examples: [Voice guides](voice-guides.md).
* Something does not work: [Voice troubleshooting](voice-troubleshooting.md).
* Daily time of each feature: [Daily limits](limits.md).
* Settings on the website: [Text to speech](../website/dashboard/tts-channels.md), [Text to speech settings](../website/dashboard/tts-settings.md) and [Speech to text](../website/dashboard/speech-to-text.md).

## Access

Voice features need a **premium server** or a **vote on [top.gg](https://top.gg/bot/893494390142697493/vote)**. A vote is valid for 24 hours. The rule depends on the command:

| Feature | Who can use it |
| --- | --- |
| `/connect`, `/tts say` | The member who runs the command must have voted in the last 24 hours. A premium server does **not** replace this vote for these two commands. |
| `/tts start` | The server is premium, **or** a member of the server has voted in the last 24 hours. One vote unlocks it for the whole server. |
| `/transcribe start`, `/transcribe live` | The server is premium, **or** the member who runs the command has voted in the last 24 hours. |
| TTS channels (`/tts-channel`) and automatic transcription (`/transcribe auto`) | The server is premium, **or** a member of the server has voted in the last 24 hours. One vote unlocks the feature for the whole server. |
| `/disconnect`, `/tts stop`, `/transcribe stop`, `/transcribe auto disable` | No vote needed. |

When a member runs a command that needs a vote, the bot replies (only to that member) with *You need to vote for the bot to use this command.* and a *Top.gg* button. When an automatic feature is blocked by the rule, the bot posts the message *Vote to unlock speech to text and text to speech* in the text channel, at most once a day per server.

Some text to speech actions can also be limited to chosen roles and members on the server: see [Text to speech settings](../website/dashboard/tts-settings.md#permissions).

## Permissions

The bot needs these permissions. See also [Permissions](../permissions.md).

| Where | Permissions |
| --- | --- |
| Voice channel | **Connect**, **Speak** |
| Text channel of a transcription | **Send Messages**; **Embed Links** for the *embed* style; **Manage Webhooks** for the *webhook* style (without it, plain messages are posted) |

## Commands

| Command | Description |
| --- | --- |
| `/connect [channel]` | Connect the bot to a voice or stage channel (yours by default). If the bot is already connected to another channel, members vote to move it. Needs a vote, see [Access](#access). |
| `/disconnect [channel]` | Disconnect the bot from its voice channel. Members vote when enough of them are in the channel. |
| `/tts start`, `/tts stop`, `/tts say`, `/tts voice`, `/tts settings` | Text to speech, see [Text to speech commands](../commands/tts.md). |
| `/tts-channel set\|remove\|list\|manage` | Read the messages of a text channel aloud, see [TTS channels](../commands/tts.md#tts-channels). |
| `/transcribe start [channel] [language] [translate_to] [style]` | Transcribe a voice channel. The transcriptions are posted in `channel` (this channel by default). |
| `/transcribe stop` | Stop the transcription. See [Daily time and stop](#daily-time-and-stop). |
| `/transcribe live` | Opens the live transcription (Activity) of your voice channel. |
| `/transcribe record start\|stop` | Records the transcript (text only) of the running transcription. See [Transcript recording](#transcript-recording). |
| `/transcribe auto enable [voice_channel] [text_channel] [language] [translate_to] [style]` | Start a transcription automatically when someone joins a voice channel. Needs *Manage Server*. |
| `/transcribe auto disable` | Disable the automatic transcription, and stop it if it is running. Needs *Manage Server*. |
| `/transcribe auto manage` | Manage the automatic transcription with a panel. Needs *Manage Server*. |

## Connecting and leaving

* `/connect` without channel uses the voice channel you are in. The bot answers *You are not connected to a voice channel.* if you are not in one and no channel is given.
* **Move vote**: if the bot is already in another channel of the server, `/connect` asks the members of that channel to vote (60 seconds). The vote is only needed when at least 4 members (not bots) are in the bot's channel: 2 votes are then required for 4 to 6 members.
* **Disconnect vote**: `/disconnect` uses the same rule and the same number of votes.
* **Administrators** do not need a vote, for `/connect` and `/disconnect`.
* **Automatic leave**: the bot leaves its voice channel **30 seconds after the last human left it**. If someone comes back before that, it stays.
* **No fixed duration**: a text to speech session does not end after a set time. The bot leaves when it is alone, when it is disconnected, or at the daily limit (see [Daily limits](limits.md)).

## Text to speech (TTS)

Everything about reading text aloud is in [Text to speech commands](../commands/tts.md): `/tts start` and `/tts stop` for a session, the automatic reading of the messages, `/tts say`, the voices, the settings and the TTS channels.

## Transcription (speech to text)

### `/transcribe start`

* You must be in a voice channel (*You are not connected to a voice channel.* otherwise).
* If the bot is already connected to a voice channel of the server, it transcribes **that** channel. Otherwise it joins the voice channel you are in.
* Only **one transcription runs per server** at a time (*I'm already transcribing a voice channel.* otherwise).
* Each bot cluster also limits the number of transcriptions running at the same time. When that limit is reached, the bot answers *Too many voice channels are being transcribed right now, please try again in a few minutes.*
* `language`: the spoken language. It is **detected automatically** when you leave it empty.
* `translate_to`: translates what is said. **Premium only**. See [Translation](#translation).
* `style`: how the transcriptions are posted, see below.

### Posting styles

| Style | What is posted |
| --- | --- |
| `webhook` (default) | The text under the **name and avatar of the speaker**. Needs *Manage Webhooks*; without it, a plain message is posted instead. |
| `message` | A plain message: the speaker name in bold, then the text. Needs no embed permission. |
| `embed` | An embed with the name and avatar of the speaker, and the text. Needs *Embed Links*. |

The voices of bots are ignored.

### Translation

* `translate_to` is a **premium** feature.
* With a translation, the translation is posted **instead of** the original text.
* If what is said is already in the target language, nothing is translated. If the translation fails, the original text is posted.

### Daily time and stop

* Transcription time is limited **per server and per day**, from **midnight UTC**: **30 minutes** on a free server, **3 hours** on a premium server. The time of all the sessions (manual and automatic) adds up. See [Daily limits](limits.md).
* When the limit is reached, the bot stops the transcription, leaves the voice channel, and posts a message saying when transcription is available again. Until then, `/transcribe start` and the automatic transcription are refused. At midnight UTC the counter starts again from 0.
* On a free server, the message suggests premium.
* `/transcribe stop` can be used by:
  * the member who started the transcription;
  * a member with *Manage Server* or *Move Members*;
  * a member who is in the voice channel, when that channel holds at most two members (the bot and this member).
* The transcription also stops when the bot is disconnected, and when the bot leaves after the last human left (see [Connecting and leaving](#connecting-and-leaving)).
* If the speech service fails **5 times in a row**, the transcription stops and the bot posts *I'm not able to use the speech recognition api.* When the service is only busy, the bot retries once after 3 seconds, then skips that part of the speech. The transcription keeps running.

### Automatic transcription

* `/transcribe auto enable` starts a transcription **when a member joins** a voice channel. Without `voice_channel`, any voice channel of the server works. Without `text_channel`, the current channel is used.
* The bot posts *The bot start transcribing in the voice channel #channel.* when it starts.
* It only starts when the bot can connect and speak in the voice channel, and can send messages in the text channel. **If a permission is missing, nothing is posted**: check the permissions first.
* The automatic transcription **leaves 30 seconds after the last human** left the channel, and stays if someone comes back.
* `language`, `translate_to` and `style` work as for `/transcribe start`.
* The settings on the dashboard page [Speech to text](../website/dashboard/speech-to-text.md) apply to a running session. Style, language, translation and text channel change at once. The voice channel is used for the next session.

### Live transcription (Activity)

`/transcribe live` opens the live transcription of your voice channel in the Discord Activity: the text appears line by line. It starts the transcription if it is not running, and needs the same access as `/transcribe start`.

From the same Activity, the **Record the audio** button starts an audio [recording](../commands/record.md#start-from-the-activity) of the voice channel, with one track per speaker. On a premium server, the continuous mode is offered too. Who can open the live view, and whether it shows the translation, is set on the [Speech to text](../website/dashboard/speech-to-text.md) page.

### Transcript recording

`/transcribe record start` and `/transcribe record stop` record **who said what, as text only** during a transcription. Nothing audio is kept. Everyone in the channel is warned in the text channel when it starts. It can also be started from the live view. On the [Speech to text](../website/dashboard/speech-to-text.md) page, the server chooses whether it is enabled, who can start it, and how long the transcripts are kept.

To record the **audio** of a voice channel instead, use [`/record`](../commands/record.md).

## Temporary voice channels

Temporary voice channels (`/tempvoice`, `/voice`) are described in [Temporary voice channels](../commands/tempvoice.md).

## Related

* [Voice guides](voice-guides.md): step-by-step examples.
* [Voice troubleshooting](voice-troubleshooting.md): messages and fixes.
* [Translation](../translation/overview.md): how translation works.
* [Premium](../premium/premium.md): what changes on a premium server.
