---
description: "Reference of the voice commands: text to speech (TTS) and speech to text (transcription) in voice channels."
---

# Voice (TTS and transcription)

The bot can read text aloud in a voice channel (**text to speech**, TTS) and write down what members say in a voice channel (**speech to text**, transcription).

* Step-by-step examples: [Voice guides](voice-guides.md).
* Something does not work: [Voice troubleshooting](voice-troubleshooting.md).
* Settings on the website: [Text to speech](../website/dashboard/tts-channels.md) and [Speech to text](../website/dashboard/speech-to-text.md).

## Access

Voice features need a **premium server** or a **vote on [top.gg](https://top.gg/bot/893494390142697493/vote)**. A vote is valid for 24 hours. The rule depends on the command:

| Feature | Who can use it |
| --- | --- |
| `/connect`, `/tts say` | The member who runs the command must have voted in the last 24 hours. A premium server does **not** replace this vote. |
| `/tts start` | The server is premium, **or** a member of the server has voted in the last 24 hours (same rule as TTS channels). |
| `/tts voice`, `/tts clone`, `/tts settings`, `/tts stop` | No vote needed. |
| `/transcribe start` | The server is premium, **or** the member who runs the command has voted in the last 24 hours. |
| `/transcribe live` | The server is premium, **or** the member who runs the command has voted in the last 24 hours. Opens the [live transcription](live-transcription.md). |
| TTS channels (`/tts-channel`), automatic transcription (`/transcribe auto`) and starting the live transcription from the Activity | The server is premium, **or** a member of the server has voted in the last 24 hours. One vote unlocks the feature for the whole server. Starting from the Activity also needs *Manage Server*. |
| `/disconnect`, `/tts stop`, `/transcribe stop`, `/transcribe auto disable` | No vote needed. |

When a member runs a command that needs a vote, the bot replies (only to that member) with *You need to vote for the bot to use this command.* and a *Top.gg* button. When an automatic feature is blocked by the rule, the bot posts the message *Vote to unlock speech to text, text to speech and recording* in the text channel, at most once a day per server.

## Permissions

The bot needs these permissions. See also [Permissions](../permissions.md).

| Where | Permissions |
| --- | --- |
| Voice channel | **Connect**, **Speak** |
| Text channel of a transcription | **Send Messages**; **Embed Links** for the *embed* style; **Manage Webhooks** for the *webhook* style (without it, plain messages are posted) |

Text to speech also has permissions set by the server (dashboard, tab **Permissions**, or `/tts settings`): **Start and stop** (`/tts start`, `/tts stop`), **Automatic reading** (messages read without `/tts say`), and **Choose a voice** (`/tts voice`). Each one is open to everyone unless the server lists roles and members. Members with *Manage Server* are always allowed.

## Commands

| Command | Description |
| --- | --- |
| `/connect [channel]` | Connect the bot to a voice or stage channel (yours by default). If the bot is already connected to another channel, members vote to move it. Needs a vote, see [Access](#access). |
| `/disconnect [channel]` | Disconnect the bot from its voice channel. Members vote when enough of them are in the channel. |
| `/tts say query language voice` | Read a text aloud in your voice channel (the bot joins it). The text can have up to 500 characters. `voice` chooses the voice for this message, see [Voices and cloning](voices-and-cloning.md). Needs your own vote. |
| `/tts start` | Join your voice channel and read the messages of this chat and of the chat of the voice channel. Needs a premium server, or a vote from a member of the server. |
| `/tts stop` | Leave the voice channel, end the session and stop the speech in progress. |
| `/tts voice [voice] [reset]` | Show or choose your voice. See [Voices and cloning](voices-and-cloning.md#choose-your-voice-tts-voice). |
| `/tts settings` | The settings of the text to speech of the server, with buttons (*Manage Server*). |
| `/tts clone create`, `/tts clone list`, `/tts clone delete` | Create (Premium), list or delete your cloned voices. See [Voices and cloning](voices-and-cloning.md#cloned-voices). |
| `/tts-channel set channel [language] [translate-to] [voice-channel]` | Read the messages of a text channel, a forum or a voice channel's chat aloud. `voice-channel` sets where they are read (default: the voice channel of the author). Needs *Manage Server*. |
| `/tts-channel remove channel` | Stop reading a text channel aloud. |
| `/tts-channel list` | List the text channels read aloud. |
| `/tts-channel manage` | Manage the channels read aloud with buttons and menus. |
| `/transcribe start [channel] [language] [translate_to] [style]` | Transcribe a voice channel. The transcriptions are posted in `channel` (this channel by default). |
| `/transcribe stop` | Stop the transcription. See [Daily time and stop](#daily-time-and-stop). |
| `/transcribe live` | Open the live transcription Activity of your voice channel. Starts the transcription if none runs, with the checks of `/transcribe start`. See [Live transcription](live-transcription.md). |
| `/transcribe auto manage` | Manage the automatic transcription with a panel. Needs *Manage Server*. |
| `/transcribe auto enable [voice_channel] [text_channel] [language] [translate_to] [style]` | Start a transcription automatically when someone joins a voice channel. Needs *Manage Server*. |
| `/transcribe auto disable` | Disable the automatic transcription, and stop it if it is running. Needs *Manage Server*. |

## Connecting and leaving

* `/connect` without channel uses the voice channel you are in. The bot answers *You are not connected to a voice channel.* if you are not in one and no channel is given.
* **Move vote**: if the bot is already in another channel of the server, `/connect` asks the members of that channel to vote (60 seconds). The vote is only needed when at least 4 members (not bots) are in the bot's channel: 2 votes are then required for 4 to 6 members.
* **Disconnect vote**: `/disconnect` uses the same rule and the same number of votes.
* **Administrators** do not need a vote, for `/connect` and `/disconnect`.
* **Automatic leave**: the bot leaves its voice channel **30 seconds after the last human left it**. If someone comes back before that, it stays.
* **Text to speech**: the connection leaves as the rule above says (30 seconds after nobody but bots is left in its voice channel). It also leaves on `/tts stop`, and when the daily text to speech time of the server is used up (once the queue is read).

## Text to speech (TTS)

### `/tts say`

* The text can have up to **500 characters**. Longer texts are refused.
* The language is **detected automatically** when you leave it empty. Otherwise, start typing the language name (or its code) and pick it from the suggestions.
* If the chosen language has no voice, the text is read with the **speech service's default voice** for that language.
* The bot joins your voice channel if it is not connected. If it is already connected to a voice channel of the server, the text is read there, unless you are in another voice channel: then the command answers *⛔ I am already reading in another voice channel.*
* Texts are played **one after the other**. Up to **5 texts** can wait behind the one playing. Beyond that, the bot answers *Too many texts are waiting to be read, please wait a moment.*
* `/tts say` and `/tts start` can be used once every 5 seconds per member; `/tts stop` and `/tts voice` once every 3 seconds. `/tts stop` stops the speech and empties the queue.
* The text read counts towards the **daily text to speech time** of the server: 30 minutes free, 3 hours premium, reset every day at midnight UTC.

### `/tts start` (session)

Joins your voice channel and reads the messages of **this chat** and of the **chat of the voice channel** aloud, without a command for each message. Each member of the voice channel gets a voice of its own. Use `/tts stop` to leave. Settings: `/tts settings`. Details and voices: [Voices and cloning](voices-and-cloning.md).

### Cleaning of the text

Before a message is read, links are removed and mentions are read as names. The settings of the server can also skip the emojis, require a prefix (removed before reading), and say the name of the author when it changes (see [Text to speech](../website/dashboard/tts-channels.md#settings)).

## TTS channels

A TTS channel reads **every message** posted in it. By default the message is read in the voice channel of its author; with a **destination** voice channel, it is read there (see below). A channel can be a text channel, a forum (each post is read), or a voice channel (its chat). A channel can be switched off without being removed (*Enabled* on the dashboard).

* Without destination, the author must be connected to a voice channel: the bot joins it, or ignores the message if it is busy in another voice channel of the server. With a destination, the message is read there when someone is in that channel, whoever writes it.
* Messages are read when they are **200 characters or less** (after links are removed). Longer messages are ignored.
* Messages from bots, messages without text (attachments only) and messages starting with `/`, `!`, `.` or `$` are ignored.
* **Language**: detected for each message, unless a language is set. **Translate to** translates each message before it is read.
* **Limits**: 5 TTS channels per server, or **25 with premium**. Adding one more shows *You reached the maximum number of TTS channels of this server (5, or 25 with premium).*
* **Anti-spam**:
  * a member who sends 5 messages with an average gap under 1.5 seconds is ignored for 10 seconds;
  * a channel that receives 10 messages with an average gap under 0.5 second is ignored for 5 seconds.
* `/tts-channel list` shows one line per channel, with its language (`auto` when detected), its translation target if any, its destination (🔊 channel) if any, and *disabled* when it is switched off.
* The same settings are available on the dashboard page [Text to speech](../website/dashboard/tts-channels.md).

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

* Transcription time is limited **per server and per day**: **30 minutes** on a free server, **3 hours** on a premium server. The time of all the sessions (manual, automatic and live) adds up.
* The day is the **UTC day**: the counter starts again from 0 at **midnight UTC**. When the limit is reached, the bot leaves the voice channel and posts *⏹️ The transcription has stopped: the daily limit is reached.* followed by the notice of the limit, which gives the time of the reset (a Discord countdown such as *in 5 hours*). Until then, `/transcribe start`, `/transcribe live` and the automatic transcription are refused.
* On a free server, the message suggests premium. A server that gets premium (or loses it) is measured against the limit of its current offer.
* `/transcribe stop` can be used by:
  * the member who started the transcription;
  * a member with *Manage Server* or *Move Members*;
  * a member who is in the voice channel, when that channel holds at most two members (the bot and this member).
* The transcription also stops when the bot is disconnected, and when the bot leaves after the last human left (see [Connecting and leaving](#connecting-and-leaving)).
* If the speech service fails **5 times in a row**, the transcription stops and the bot posts *I'm not able to use the speech recognition api.* When the service is only busy, the bot retries once after 3 seconds, then skips that part of the speech. The transcription keeps running.

### Automatic transcription

* `/transcribe auto enable` starts a transcription **when a member joins** a voice channel. Without `voice_channel`, any voice channel of the server works. Without `text_channel`, the current channel is used.
* When a session starts, the bot says *Transcription started* in the voice channel (spoken). It posts no start message in the text channel.
* It only starts when the bot can connect and speak in the voice channel, and can send messages in the text channel. **If a permission is missing, nothing is posted**: check the permissions first.
* The automatic transcription **leaves 30 seconds after the last human** left the channel, and stays if someone comes back.
* `language`, `translate_to` and `style` work as for `/transcribe start`.
* The settings on the dashboard page [Speech to text](../website/dashboard/speech-to-text.md) apply to a running session. Style, language, translation and text channel change at once. The voice channel is used for the next session.

## Live transcription (Activity)

`/transcribe live`, or **Start an Activity** in the voice channel and pick **Interaction Bot**, opens the transcription as a live view: the sentences appear line by line with the picture of each speaker. It uses the same transcription and the same daily time. Translation for each viewer is premium. Details, settings and troubleshooting: [Live transcription](live-transcription.md).

## Related

* [Voice guides](voice-guides.md): step-by-step examples.
* [Voice troubleshooting](voice-troubleshooting.md): messages and fixes.
* [Translation](../translation/overview.md): how translation works.
* [Premium](../premium/premium.md): what changes on a premium server.
