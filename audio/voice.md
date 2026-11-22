---
description: "Reference of the voice commands: text to speech (TTS) and speech to text (transcription) in voice channels."
---

# Voice (TTS and transcription)

The bot can read text aloud in a voice channel (**text to speech**, TTS) and write down what members say in a voice channel (**speech to text**, transcription).

* Step-by-step examples: [Voice guides](voice-guides.md).
* Something does not work: [Voice troubleshooting](voice-troubleshooting.md).
* Settings on the website: [Text to speech](../website/dashboard/tts-channels.md) and [Transcription](../website/dashboard/speech-to-text.md).

{% hint style="info" %}
The rules of the reading and of the transcription (which channels, which voice channel, which output) are set on the dashboard, not with commands. The commands below start, stop and check the voice features.
{% endhint %}

## Access

Voice features need a **premium server** or a **vote on [top.gg](https://top.gg/bot/893494390142697493/vote)**. A vote is valid for 24 hours, and one vote from a member of the server unlocks the feature for the whole server. The rule depends on the command:

| Feature | Who can use it |
| --- | --- |
| `/connect`, `/tts say`, `/tts start` | The server is premium, **or** a member of the server has voted in the last 24 hours. |
| `/transcribe start`, `/transcribe live` | The server is premium, **or** a member of the server has voted in the last 24 hours. |
| TTS rules and automatic transcription (set on the dashboard) | The server is premium, **or** a member of the server has voted in the last 24 hours. |
| `/tts voice`, `/tts clone create`, `/tts clone list`, `/tts clone delete` | No vote needed. Creating a cloned voice needs Premium, see [Voices and cloning](voices-and-cloning.md). |
| `/tts stop`, `/disconnect`, `/transcribe stop` | No vote needed. |

When a member runs a command that needs a vote, the bot replies (only to that member) that a vote is needed, with a *Top.gg* button. When an automatic feature is blocked by the rule, the bot asks for a vote in the text channel, at most once a day per server.

## Permissions

The bot needs these permissions. See also [Permissions](../permissions.md).

| Where | Permissions |
| --- | --- |
| Voice channel | **Connect**, **Speak** |
| Text channel of a transcription | **Send Messages**; **Embed Links** for the *embed* style; **Manage Webhooks** for the *webhook* style (without it, plain messages are posted) |
| Text channel of a TTS rule | **View Channel** and **Read Message History**, so that the bot reads the messages. The bot also needs **Connect** and **Speak** in the voice channel where the messages are read. |

Text to speech also has permissions set by the server (dashboard, tab **Permissions**): **Start and stop** (`/tts start`, `/tts stop`), **Automatic reading** (messages read without `/tts say`), and **Choose a voice** (`/tts voice`). Each one is open to everyone unless the server lists roles and members. Members with *Manage Server* are always allowed.

## Commands

| Command | Description |
| --- | --- |
| `/connect [channel]` | Connect the bot to a voice or stage channel (yours by default). If the bot is already connected to another channel, members vote to move it. Needs a vote, see [Access](#access). |
| `/disconnect` | Disconnect the bot from its voice channel. Members vote when enough of them are in the channel. |
| `/tts say query [language] [voice]` | Read a text aloud in your voice channel (the bot joins it). The text can have up to **500 characters**. `voice` chooses the voice for this message, see [Voices and cloning](voices-and-cloning.md). Needs a vote or a premium server. |
| `/tts start` | Join your voice channel and read the messages of this chat and of the chat of the voice channel. Needs a vote or a premium server. See [`/tts start` (session)](#tts-start-session). |
| `/tts stop` | Leave the voice channel, end the session and cut the speech in progress. |
| `/tts voice [voice] [reset]` | Show or choose your voice. See [Voices and cloning](voices-and-cloning.md#choose-your-voice-tts-voice). |
| `/tts clone create audio name` | Create a cloned voice from a recording of your voice (Premium). See [Voices and cloning](voices-and-cloning.md#create-a-cloned-voice-tts-clone-create). |
| `/tts clone list`, `/tts clone delete voice` | List your cloned voices, or delete one. |
| `/transcribe start [channel] [language] [translate-to] [style]` | Transcribe the voice channel you are in. The transcriptions are posted in `channel` (this channel by default). See [`/transcribe start`](#transcribe-start). |
| `/transcribe stop` | Stop the transcription. See [Daily time and stop](#daily-time-and-stop). |
| `/transcribe live` | Open the live transcription Activity of your voice channel. Starts the transcription if none runs, with the checks of `/transcribe start`. See [Live transcription](live-transcription.md). |

The commands that set the rules of the reading and of the transcription (`/tts settings`, `/tts-channel`, `/transcribe auto`) no longer exist. Their settings are on the dashboard: [Text to speech](../website/dashboard/tts-channels.md) and [Transcription](../website/dashboard/speech-to-text.md).

## Connecting and leaving

* `/connect` without channel uses the voice channel you are in. The bot answers *You are not connected to a voice channel.* if you are not in one and no channel is given.
* **Move vote**: if the bot is already in another channel of the server, `/connect` asks the members of that channel to vote (60 seconds). The vote is only needed when at least 4 members (not bots) are in the bot's channel: 2 votes are then required for 4 to 6 members, and the number grows with the members.
* **Disconnect vote**: `/disconnect` uses the same rule and the same number of votes.
* **Administrators** do not need a vote, for `/connect` and `/disconnect`.
* **Automatic leave**: the bot leaves its voice channel **30 seconds after the last human left it**. If someone comes back before that, it stays.
* **Text to speech**: the bot leaves the same way. It also leaves on `/tts stop`, and when the daily text to speech time of the server is used up (once the queue is read).

## Text to speech (TTS)

### `/tts say`

* The text can have up to **500 characters**. Longer texts are refused with *The text is too long (maximum 500 characters).*
* The language is **detected automatically** when you leave it empty. Otherwise, start typing the language name (or its code) and pick it from the suggestions.
* The voice is chosen in this order: the `voice` of the command, then your own voice (when the server lets members choose one, see [Voices and cloning](voices-and-cloning.md#who-can-do-what)), then the default voice of the server.
* If the chosen language has no voice, the text is read with the **speech service's default voice** for that language.
* The bot joins your voice channel if it is not connected. If it is already connected to another voice channel of the server, the command answers *I am already reading in another voice channel.*
* Texts are played **one after the other**. Up to **5 texts** can wait behind the one playing. Beyond that, the bot answers *Too many texts are waiting to be read, please wait a moment.*
* `/tts say` and `/tts start` can be used once every 5 seconds per member; `/tts stop` and `/tts voice` once every 3 seconds.
* The text read counts towards the **daily text to speech time** of the server: 30 minutes free, 3 hours premium, reset every day at midnight UTC.

### `/tts start` (session)

Joins your voice channel and reads the messages of **this chat** and of the **chat of the voice channel** aloud, without a command for each message. When the server lets members choose their voice, each member of the voice channel gets a voice of its own; otherwise everybody is read with the voice of the server. Use `/tts stop` to leave.

The reading options of a session (who is read, the prefix, the name of the author, the emojis, the notices, the length limit...) are on the [Settings tab](../website/dashboard/tts-channels.md#settings) of the dashboard. Who can start and stop a session is set on the [Permissions tab](../website/dashboard/tts-channels.md#permissions).

### Cleaning of the text

Before a message is read, links are removed (or said as the word *link* in a session, when the option is on) and mentions are read as names. The settings of the server can also skip the emojis, require a prefix (removed before reading), say the name of the author when it changes, and expand chat abbreviations such as *lol* or *idk* (see [Text to speech](../website/dashboard/tts-channels.md#settings)).

## TTS channels

A TTS rule reads the messages of a text channel, of a category, or of the whole server aloud. The rules are set on the dashboard, in the tab **Read-aloud rules** of [Text to speech](../website/dashboard/tts-channels.md). When several rules apply to a message, the most precise one wins: the rule of the channel, then the rule of its category, then the rule of the whole server.

* A **channel** rule can be a text channel, a forum (each post is read) or the chat of a voice channel.
* **Without destination**, the message is read in the voice channel of its author. The author must be connected to a voice channel: the bot joins it, or ignores the message if it is busy in another voice channel of the server.
* A channel rule can have a **destination** voice channel. The message is then read there, when someone is in that channel, whoever writes it.
* A **global rule** (the whole server) makes the bot join the voice channel of whoever writes, anywhere on the server.
* **Only muted members**: a rule can read only the members who are in a voice channel with their microphone off.
* **Translate to** translates each message before it is read. It is a premium feature.
* **Language**: detected for each message, unless a language is set.
* A rule can be switched off without being removed (*Enabled* on the dashboard).
* **Limits**: 5 rules per server, or **25 with premium**.
* Messages from bots, messages without text (attachments only), and messages starting with `/`, `!`, `.` or `$` are not read. Bots and webhooks are read only if the reading options of the server allow it.
* A long message is split into parts read one after the other. Only its first **4000 characters** are read.
* **Anti-spam**:
  * a member who sends 5 messages with an average gap under 1.5 seconds is ignored for 10 seconds;
  * a server that receives 10 messages with an average gap under 0.5 second is ignored for 5 seconds.
* Up to 40 parts of messages can wait to be read on the server. Beyond that, a new message is not read.

## Reading the translations aloud (Premium)

On a **Premium** server, text to speech also reads the **translations made by the bot**: in a session started with `/tts start` and in the TTS channels, each translation is read **after the original message**, with the voice of the server (not the voice of the author). Messages of other bots and webhooks stay ignored.

* The setting is **Read translations aloud**, **on by default**, in the **Settings** tab of [Text to speech](../website/dashboard/tts-channels.md#settings). Turn it off to read only the original messages.
* On a free server the translations are never read, whatever the setting.
* Links are removed from the text before reading, and a translation that starts with a command prefix is not read.

## Transcription (speech to text)

### `/transcribe start`

* You must be in a voice channel (*You are not connected to a voice channel.* otherwise).
* If the bot is already connected to a voice channel of the server, it transcribes **that** channel. Otherwise it joins the voice channel you are in.
* Only **one transcription runs per server** at a time (*I'm already transcribing a voice channel.* otherwise).
* Each bot cluster also limits the number of transcriptions running at the same time. When that limit is reached, the bot answers *Too many voice channels are being transcribed right now, please try again in a few minutes.*
* `channel`: where the transcriptions are posted. Default: the channel where you run the command.
* `language`: the spoken language. It is **detected automatically** when you leave it empty.
* `translate-to`: translates what is said. **Premium only**. See [Translation](#translation).
* `style`: how the transcriptions are posted, see [Posting styles](#posting-styles).

### Posting styles

| Style | What is posted |
| --- | --- |
| `webhook` (default) | The text under the **name and avatar of the speaker**. Needs *Manage Webhooks*; without it, a plain message is posted instead. |
| `message` | A plain message: the speaker name, then the text. Needs no embed permission. |
| `embed` | A card with the name and avatar of the speaker, and the text. Needs *Embed Links*. |

The voices of bots are ignored. The style of the automatic transcription is set on the dashboard, rule by rule.

### Translation

* `translate-to` is a **premium** feature.
* On the dashboard, each rule shows **Translation only** (default) or **Original + translation**.
* If what is said is already in the target language, nothing is translated. If the translation fails, the original text is posted.

### Daily time and stop

* Transcription time is limited **per server and per day**: **30 minutes** on a free server, **3 hours** on a premium server. The time of all the sessions (manual, automatic and live) adds up. The transcription of voice messages uses the same daily quota, see [Voice messages](voice-messages.md#limits).
* The day is the **UTC day**: the counter starts again from 0 at **midnight UTC**. The server is warned when 80 % of the day is used. When the limit is reached, the bot leaves the voice channel and posts *⏹️ The transcription has stopped: the daily limit is reached.* followed by the notice of the limit, which gives the time of the reset. Until then, `/transcribe start`, `/transcribe live` and the automatic transcription are refused.
* On a free server, the message suggests premium. A server that gets premium (or loses it) is measured against the limit of its current offer.
* `/transcribe stop` can be used by:
  * the member who started the transcription;
  * a member with *Manage Server* or *Move Members*;
  * a member who is in the voice channel, when that channel holds at most two members (the bot and this member).
* The transcription also stops when the bot is disconnected, and when the bot leaves after the last human left (see [Connecting and leaving](#connecting-and-leaving)).
* If the speech service fails **5 times in a row**, the transcription stops and the bot posts *I'm not able to use the speech recognition api.* When the service is only busy, the bot retries after 3 seconds, then skips that part of the speech. The transcription keeps running.

### Automatic transcription

The automatic transcription is set on the dashboard, in the tab **Transcribed channels** of [Transcription](../website/dashboard/speech-to-text.md). A rule says which voice channels to listen to:

* a **voice channel** rule: that voice channel;
* a **category** rule: every voice channel of the category;
* a **global** rule: every voice channel of the server.

The most precise rule applies: the rules of the voice channel, else those of its category, else the global rules.

* When a member joins a matching voice channel, the bot starts a transcription by itself, if the server is premium or a vote is valid. Without a vote, the bot asks for one in the text channel, at most once a day.
* A **free** server has **one** rule. A **premium** server can have up to **25 rules**. At most **3** rules can listen to the same voice channel, and a voice channel can be posted to up to 3 places at once on a premium server (1 on a free server).
* When a session starts, the bot says *Transcription started.* in the voice channel (spoken). It posts no start message in the text channel.
* It only starts when the bot can connect and speak in the voice channel, and can send messages in the text channel. **If a permission is missing, nothing is posted**: check the permissions first.
* The automatic transcription **leaves 30 seconds after the last human** left the channel, and stays if someone comes back.
* A change of style, language, translation or text channel applies to a running session at once. A change of voice channel applies to the next session.

## Live transcription (Activity)

`/transcribe live`, or **Start an Activity** in the voice channel and pick **Interaction Bot**, opens the transcription as a live view: the sentences appear line by line with the picture of each speaker. It uses the same transcription and the same daily time. Translation for each viewer is premium. Details, settings and troubleshooting: [Live transcription](live-transcription.md).

## Related

* [Voice guides](voice-guides.md): step-by-step examples.
* [Voice troubleshooting](voice-troubleshooting.md): messages and fixes.
* [Voices and cloning](voices-and-cloning.md): the voices used for reading.
* [Limits and privacy](limits-and-privacy.md): daily limits, `/limits` and `/privacy`.
* [Translation](../translation/overview.md): how translation works.
* [Premium](../premium/premium.md): what changes on a premium server.
