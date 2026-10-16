---
description: "Step-by-step guides for the voice features: read the chat aloud, read one text, TTS channels, transcription, transcription with translation and recording."
---

# Voice guides

Each guide starts from a server where the bot is installed, with the permissions of [Voice](voice.md#permissions). Check the [access rules](voice.md#access) first: most voice features need a premium server or a vote on [top.gg](https://top.gg/bot/893494390142697493/vote).

## 1. Read the chat aloud for a while (`/tts start`)

1. Join a voice channel of the server.
2. In the text channel you want to be read, run `/tts start`. The bot joins your voice channel and answers *I joined #channel. The messages written in this chat are read aloud there.*
3. Write a message in the chat. It is read aloud, and the name of its author is said first when the author changes.
4. The messages of the chat of the voice channel are read too. To turn that off, see *Read the chat of voice channels* on the [Text to speech settings](../website/dashboard/tts-settings.md) page.
5. Run `/tts stop` when you are done. The bot leaves the voice channel and cuts the speech in progress. It also leaves 30 seconds after the last human left.

{% hint style="info" %}
`/tts start` needs a premium server, or a vote on top.gg from a member of the server in the last 24 hours. The permission *Start and stop* of the [Text to speech settings](../website/dashboard/tts-settings.md#permissions) decides who can run it.
{% endhint %}

## 2. Read one text once (`/tts say`)

1. Join a voice channel of the server.
2. Run `/tts say` and type the text in `query`. The text can have up to 500 characters.
3. Optional: in `language`, start typing a language name and pick it from the suggestions. Leave it empty to detect the language automatically.
4. The bot joins your voice channel and reads the text.

{% hint style="info" %}
`/tts say` needs **your own** vote on top.gg in the last 24 hours, even on a premium server. Otherwise the bot answers *You need to vote for the bot to use this command.*
{% endhint %}

## 3. Give each person their own voice

1. Open the page **Text to speech settings** (category *Audio & AI*) and look at the **Voices** card. Switch off the voices you do not want, and drag the others to set their order: the first voices are given first.
2. Choose the **default voice**, used by `/tts say`.
3. Members who want a particular voice run `/tts voice` and pick it from the suggestions. `/tts voice reset:true` removes the choice.

Each person who writes during a session keeps the same voice until the session ends. See [Voices](../commands/tts.md#voices).

## 4. Read a text channel aloud (TTS channel)

Every message of the channel is read in the voice channel of its author, for the members who are in a voice channel.

**With the command**

1. Make sure you have the *Manage Server* permission.
2. Run `/tts-channel set channel:#chat`. Optional: `language` (detected for each message if empty) and `translate-to` (translate each message before reading it, premium).
3. Check the list with `/tts-channel list`. To stop reading the channel, run `/tts-channel remove channel:#chat`.

**On the dashboard**

1. Open the dashboard of the server, then the page **Text to speech** (category *Audio & AI*).
2. Click *Add a channel*, choose the text channel, then set the language and the translation if needed.
3. Click *Save*.

<figure><img src="../.gitbook/assets/dash-text-to-speech.png" alt="Text to speech page"><figcaption><p>Text to speech page</p></figcaption></figure>

{% hint style="info" %}
A message is read only if it is 200 characters or less, has text, does not start with `/`, `!`, `.` or `$`, and its author is in a voice channel. Limits and anti-spam rules are in [TTS channels](../commands/tts.md#tts-channels).
{% endhint %}

## 5. Transcribe a voice channel manually (`/transcribe start`)

1. Join the voice channel you want to transcribe. If the bot is already connected to another voice channel of the server, it transcribes that channel instead.
2. Go to the text channel where the transcriptions must appear. Without the `channel` option, the transcriptions are posted in the channel where you run the command.
3. Run `/transcribe start`. Optional options:
   * `channel`: another text channel for the transcriptions;
   * `language`: the spoken language (detected automatically if empty);
   * `style`: `webhook` (default, under the speaker's name), `message` or `embed`.
4. Speak. The transcriptions appear in the text channel.
5. Run `/transcribe stop` when you are done. The transcription also stops when the daily time of the server is used up: 30 minutes on a free server, 3 hours on a premium server, counted from midnight UTC (see [Daily time and stop](voice.md#daily-time-and-stop)).

{% hint style="info" %}
`/transcribe start` needs a premium server, or a vote in the last 24 hours from the member who runs it. Only one transcription runs per server at a time.
{% endhint %}

## 6. Transcribe automatically when someone joins (`/transcribe auto`)

1. Make sure you have the *Manage Server* permission.
2. Check the permissions: the bot must be able to **Connect** and **Speak** in the voice channel, and to **Send Messages** in the text channel. The `embed` style also needs **Embed Links**. The `webhook` style (the default) needs **Manage Webhooks**; without it, plain messages are posted.
3. Run `/transcribe auto enable`. Optional options:
   * `voice_channel`: the voice channel that starts the transcription (any voice channel if empty);
   * `text_channel`: where the transcriptions are posted (this channel if empty);
   * `language`, `translate_to` and `style`, as in guide 5.
4. When a member joins the voice channel, the bot posts *The bot start transcribing in the voice channel #channel.* and transcribes the channel.
5. The bot leaves 30 seconds after the last human left. To turn the feature off, run `/transcribe auto disable`.

The same settings are on the dashboard page **Speech to text**: switch on *Enabled*, click *Add a configuration*, set the fields, then *Save*.

<figure><img src="../.gitbook/assets/dash-speech-to-text.png" alt="Speech to text page"><figcaption><p>Speech to text page</p></figcaption></figure>

{% hint style="info" %}
If the bot does not start, the permissions of the channels are the first thing to check: when a permission is missing, nothing is posted. See [Voice troubleshooting](voice-troubleshooting.md).
{% endhint %}

## 7. Transcribe with a translation (premium)

The translation of a transcription is a **premium** feature. Only the translation is posted.

1. Make sure the server is premium.
2. For a one-time transcription, run `/transcribe start` with the option `translate_to`, and pick the target language from the suggestions.
3. For an automatic transcription, run `/transcribe auto enable` with the same option. You can also set *Translate to* on the dashboard page **Speech to text**.
4. What is said in the target language is not translated again. If the translation fails, the original text is posted.

{% hint style="info" %}
On a free server, `/transcribe start translate_to:...` answers *The translation of the transcription is reserved for premium servers.* Start the transcription without the option, or get [premium](../premium/premium.md).
{% endhint %}

## 8. Record a voice channel (`/record`)

1. Join the voice channel you want to record. Stage channels cannot be recorded.
2. Run `/record start` in a text channel. The bot joins, and tells the members of the channel that it records. Anyone who joins later is told too.
3. Run `/record stop` when you are done, or wait for the end of the recording: 30 seconds after the last member left, or the daily time of the server.
4. The link to the recording is sent to you in private messages. Open it on the website, and log in with Discord to download the tracks and the mix.

{% hint style="info" %}
Recording needs a vote in the last 24 hours from a member of the server, or a premium server. The recording is kept 7 days on a free server and 30 days on a premium server. See [Recording commands](../commands/record.md).
{% endhint %}

## Next steps

* [Voice](voice.md): the rules of access, permissions and transcription.
* [Text to speech commands](../commands/tts.md): every text to speech command and setting.
* [Recording commands](../commands/record.md) and [Daily limits](limits.md).
* [Voice troubleshooting](voice-troubleshooting.md): messages and fixes.
