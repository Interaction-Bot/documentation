---
description: "Voice messages: transcribe a Discord voice message from the menu, transcribe them automatically, translate them with the translation features (Premium), and read the translation aloud (Premium). Limits, quotas, opt-out and privacy."
---

# Voice messages

A **voice message** is a voice note sent in a Discord channel (the recording with a waveform). The bot can:

* **transcribe** a voice message, privately, with the menu _**Transcribe voice message**_;
* **transcribe every voice message** of the server automatically, under the message;
* **translate** the voice messages with the translation features (flag, channel, mirror, category and role), **Premium**;
* **read the translation aloud** as a new voice message, **Premium**.

Settings: [Voice messages](../website/dashboard/voice-messages.md) on the dashboard.

Only voice notes sent in Discord are read. Audio files uploaded as attachments are not.

## Transcribe a voice message

1. Right-click the voice message.
2. Open **Apps**, then choose **Transcribe voice message**.
3. The bot answers **privately**, with only you able to see it. The answer shows:
   * the transcript, with the name and the picture of the author;
   * in the footer, the length of the voice message in seconds and the detected language.
4. Press _**Translate to my language**_ to translate the transcript into the language of your Discord client. If the transcript is already in your language, the bot says so. The translation is also private.

The button works for 5 minutes after the answer.

| Requirement | Detail |
| --- | --- |
| Transcription on | The transcription feature of the server must be on. |
| Vote or Premium | Premium servers need no vote. Other servers need a [top.gg vote](https://top.gg/bot/893494390142697493/vote) in the last 24 hours, like the other voice features (see [Transcription](../website/dashboard/speech-to-text.md#limits)). |
| Cooldown | One use every 5 seconds for each person. |
| Length | See [Limits](#limits). |

## Automatic transcription

The option _**Transcribe voice messages**_ on the dashboard transcribes **every** voice message sent in the server.

* The bot posts the transcript as a reply under the voice message, in the same channel.
* The transcript is **not translated**.
* The bot posts nothing when a voice message cannot be transcribed (too long, quota used up, no speech, opt-out). No error message is shown in the channel.

The transcription feature of the server must be on for this option to work.

## Translate voice messages (Premium)

On a Premium server, a voice message is translated like a written message, through its transcript, by these translation features:

| Feature | Where to set it |
| --- | --- |
| Flag translation (reaction with a flag) | [Flag translation](../website/dashboard/flag-translation.md) |
| Channel translation | [Channel translation](../website/dashboard/channel-translation.md) |
| Mirror (group of channels) | [Translation groups](../website/dashboard/translation-groups.md) |
| Category translation | [Category translation](../website/dashboard/category-translation.md) |
| Role translation | [Role translation](../website/dashboard/role-translation.md) |

A voice message is translated from its transcript, and the translation is posted like the translation of a written message. A voice message that has written text is not transcribed: only its text is translated.

On a free server, voice messages are not translated. The option _**Translate voice messages**_ cannot be turned on for a free server.

## Voice dubbing (Premium)

**Dubbing** reads the translated text of a voice message aloud, and posts it as a new voice message in the channel of the translation. It is a Premium option (_**Generate translated voice messages**_ on the dashboard).

The text is not read aloud when one of these is true:

* the text to speech feature (`tts`) is off on the server;
* the server is not Premium;
* the daily text to speech quota of the server is used up;
* the translated text is longer than **600 characters**;
* the target language has no voice on the server.

Other rules:

* **Voice:** the default voice of the server is used when it speaks the target language. Otherwise the first voice of the server that speaks it is used.
* **Maximum 3 voices per voice message**, one for each target language.
* Dubbing uses the **text to speech quota** of the server, see [Text to speech](../website/dashboard/tts-channels.md).

## Limits

| | Free | Premium |
| --- | --- | --- |
| Length of one voice message | 2 minutes | 15 minutes |
| Daily speech to text quota of the server | Same quota as the transcription of voice channels, see [Transcription](../website/dashboard/speech-to-text.md#limits) | Same quota as the transcription of voice channels |
| Translation of voice messages | No | Yes |
| Voice dubbing | No | Yes |

* A voice message longer than the limit is refused, with the length limit shown.
* Each transcription uses the speech to text quota of the server, for the length of the audio. When the quota is used up, the message says so, and the quota resets at midnight UTC.
* A voice message that is transcribed once is kept for 10 minutes in memory. A new use of the same voice message in those 10 minutes does not use the quota again.

## Opt-out

A member who opted out of message processing on the **Account** page of the dashboard (see [Limits and privacy](limits-and-privacy.md#privacy-opt-outs)) is not transcribed:

* the menu answers that the author of the message refused that the bot processes their messages;
* the translations and the automatic transcription do not process the messages of that member.

## Privacy

* **The audio is not stored.** The bot downloads the voice message in memory, converts it, sends it to the speech to text service, and forgets it.
* **The transcript is kept in memory for 10 minutes** (by message), so that the menu, the translations and the automatic transcription do not transcribe the same message twice. Then it is dropped. The bot does not keep it in its database.
* **The quota** keeps only the length of the audio, per server and per day.

## Commands and menus

| Name | Type | Description |
| --- | --- | --- |
| _Transcribe voice message_ (in **Apps**) | Message context menu | Transcribes a voice message, shown privately, with a translation button. |
| _Translate to my language_ | Button of the transcript | Translates the transcript into the language of your Discord client. Shown privately. |

There is no slash command for voice messages. The settings are on the dashboard.
