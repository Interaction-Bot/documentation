---
description: "Step-by-step guides for the voice features: read a message aloud, TTS rules, manual and automatic transcription, and transcription with translation."
---

# Voice guides

Each guide starts from a server where the bot is installed, with the permissions of [Voice](voice.md#permissions). Check the [access rules](voice.md#access) first: most voice features need a premium server or a vote on [top.gg](https://top.gg/bot/893494390142697493/vote).

## 1. Read a message aloud (`/tts say`)

1. Join a voice channel of the server.
2. Run `/tts say` and type the text in `query`. The text can have up to 500 characters.
3. Optional: in `language`, start typing a language name and pick it from the suggestions. Leave it empty to detect the language automatically. Optional: `voice`, to pick a voice for this message.
4. The bot joins your voice channel and reads the text. It answers with the embed *The bot is saying `...` in the voice channel.*
5. To stop the speech and empty the queue, run `/tts stop`. To make the bot leave, run `/tts stop` or `/disconnect`, or wait: it leaves 30 seconds after nobody but bots is left in the channel.

{% hint style="info" %}
On a premium server, `/tts say` needs no vote. Otherwise, if no member of the server has voted in the last 24 hours, it answers *You need to vote for the bot to use this command.* One vote from any member unlocks it for the whole server.
{% endhint %}

## 2. Read a text channel aloud (TTS rule)

Every message of the channel is read in the voice channel of its author, for the members who are in a voice channel. A rule can also cover a whole category, or the whole server.

1. Make sure you have the *Manage Server* permission.
2. Open the dashboard of the server, then the page **Text to speech** (category *Audio & AI*). The tab **Read-aloud rules** is open.
3. Click **Add a channel** (or **Add a category**, or **Add** for the whole server). In the window, choose the channel.
4. Optional: set **Voice channel for reading** (where the messages are read; by default, the voice channel of the author), **Language** (automatic by default), and **Automatic translation** (premium).
5. Optional: turn on **Only members whose mic is muted** if only the members who cannot talk should be read.
6. Click **Add this rule**, then **Save** in the bar at the bottom of the page.

<figure><img src="../.gitbook/assets/tts-rule-window.png" alt="Adding a text to speech rule"><figcaption><p>Adding a text to speech rule</p></figcaption></figure>

{% hint style="info" %}
A message is read only if it has text, does not start with `/`, `!`, `.` or `$`, and either its author is in a voice channel, or the rule has a destination where someone is. Limits and anti-spam rules are in [Voice](voice.md#tts-channels).
{% endhint %}

## 3. Transcribe a voice channel manually (`/transcribe start`)

1. Join the voice channel you want to transcribe. If the bot is already connected to another voice channel of the server, it transcribes that channel instead.
2. Go to the text channel where the transcriptions must appear. Without the `channel` option, the transcriptions are posted in the channel where you run the command.
3. Run `/transcribe start`. Optional options:
   * `channel`: another text channel for the transcriptions;
   * `language`: the spoken language (detected automatically if empty);
   * `style`: `webhook` (default, under the speaker's name), `message` or `embed`.
4. Speak. The transcriptions appear in the text channel.
5. Run `/transcribe stop` when you are done. The transcription also stops when the daily time of the server is used up: 30 minutes on a free server, 3 hours on a premium server, counted per UTC day (the time starts again at midnight UTC; see [Daily time and stop](voice.md#daily-time-and-stop)).

{% hint style="info" %}
`/transcribe start` needs a premium server, or a vote in the last 24 hours from a member of the server. Only one transcription runs per server at a time.
{% endhint %}

## 4. Transcribe automatically when someone joins

1. Make sure you have the *Manage Server* permission.
2. Check the permissions: the bot must be able to **Connect** and **Speak** in the voice channel, and to **Send Messages** in the text channel. The `embed` style also needs **Embed Links**. The `webhook` style (the default) needs **Manage Webhooks**; without it, plain messages are posted.
3. Open the dashboard of the server, then the page **Transcription** (category *Audio & AI*). The tab **Transcribed channels** is open.
4. Click **Add a voice channel** (or **Add a category**, or **Add** for the whole server). Choose the voice channel to listen to, then the **Text channel** where the transcriptions are posted (the chat of the voice channel by default). Optional: **Translate to**, **Display** and **Style**.
5. Click **Add this rule**, then **Save** in the bar at the bottom of the page.
6. When a member joins the voice channel, the bot says *Transcription started.* in the voice channel (spoken) and transcribes the channel. Nothing is posted in the text channel for the start.
7. The bot leaves 30 seconds after the last human left.

A free server has **one** rule on this page; a premium server can have up to 25. The most precise rule of a voice channel wins: a rule of the voice channel, then of its category, then the rules of the whole server. Up to 3 rules can listen to the same voice channel.

<figure><img src="../.gitbook/assets/stt-page-overview.png" alt="The transcription rules of a server"><figcaption><p>The transcription rules of a server</p></figcaption></figure>

{% hint style="info" %}
If the bot does not start, the permissions of the channels are the first thing to check: when a permission is missing, nothing is posted. See [Voice troubleshooting](voice-troubleshooting.md).
{% endhint %}

## 5. Transcribe with a translation (premium)

The translation of a transcription is a **premium** feature. By default only the translation is posted; the *Display* option of a rule can post the original too.

1. Make sure the server is premium.
2. For a one-time transcription, run `/transcribe start` with the option `translate-to`, and pick the target language from the suggestions.
3. For an automatic transcription, open the page **Transcription**, and set **Translate to** in the rule (the field is locked on a free server).
4. What is said in the target language is not translated again. If the translation fails, the original text is posted.

{% hint style="info" %}
On a free server, `/transcribe start translate-to:...` answers *The translation of the transcription is reserved for premium servers.* Start the transcription without the option, or get [premium](../premium/premium.md).
{% endhint %}

## 6. Follow the transcription live (`/transcribe live`)

1. Join the voice channel. Make sure the server is premium, or that you have voted in the last 24 hours.
2. Run `/transcribe live`. If no transcription runs, the command starts one (same rules as `/transcribe start`). If one already runs in this channel, the view opens at once.
3. Click **Open the live transcription**. The Activity opens with the sentences as they are said.
4. On a premium server, choose the language you read in the **Translate** button. Only your view changes.
5. A member with *Manage Server* can stop the transcription from the Activity: click **Stop transcription**, then **Click again to stop** within 8 seconds.

{% hint style="info" %}
The live view can be turned off, or limited to members who can manage the server, on the dashboard page **Transcription**, in the tab **Live transcription (Activity)**. See [Live transcription](live-transcription.md).
{% endhint %}

## Next steps

* [Voice](voice.md): the full reference of the commands and limits.
* [Voice troubleshooting](voice-troubleshooting.md): messages and fixes.
