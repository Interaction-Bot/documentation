---
description: Configure the live transcription of voice channels.
---

# Speech to text

<figure><img src="../../.gitbook/assets/dash-speech-to-text.png" alt="Speech to text page"><figcaption><p>Speech to text page</p></figcaption></figure>

## Localization

Navbar > category _**Audio & AI**_ > _**Speech to text**_.

## Transcription

The bot transcribes the speech of voice channels and posts the transcriptions in a text channel, a forum or the chat of the voice channel. The spoken language is detected automatically. You can also use [`/transcribe`](../../commands/voice.md#transcription-speech-to-text).

Use the _**Enabled / Disabled**_ toggle to enable the transcription on the server, then click _**Add a configuration**_. For each configuration:

* **Voice channel**: listen to a specific voice channel, or to _All voice channels_ (default).
* **Text channel**: where the transcriptions are posted: a text channel, a forum, or the chat of a voice channel. Default: _Chat of the voice channel being transcribed_.
* **Translate to** (**premium**): translate each transcription into this language. Only the translation is posted. Default: _No translation_. On a free server, the field reads _No translation (premium only)_.
* **Style**:
  * _Embed_: a card with the speaker's name and avatar, and the transcription (or its translation). Needs *Embed Links*.
  * _Message_: a plain message, speaker name followed by the text. Needs no embed permission.
  * _Webhook_ (default): sent under the speaker's name and avatar. Needs the *Manage Webhooks* permission, otherwise a plain message is used.

Click _**Remove**_ on a configuration to delete it. When there are unsaved changes, a bar at the bottom of the page says _You made changes, save them!_ with _Save_ and _Cancel_ buttons: _Save_ applies them, _Cancel_ restores the last saved configurations. The message _Configuration saved._ confirms the save.

Changes to the style, the language, the translation and the text channel apply live to a running session. A change of voice channel applies to the next session.

## Limits

| Free                       | Premium                                  |
| -------------------------- | ---------------------------------------- |
| 1 configuration            | Unlimited configurations                 |
| 30 minutes per day         | 2 hours per day                          |
| Needs a recent top.gg vote | No vote needed                           |
| No translation             | Translation of the transcription         |

At most 3 configurations can listen to the same voice channel. _All voice channels_ counts as one voice channel in this rule.

Voice features need a premium server, or a [top.gg vote](https://top.gg/bot/893494390142697493/vote) in the last 24 hours. The session stops after its limit, and the bot leaves the voice channel.

## Messages of the page

| Message | Meaning |
| --- | --- |
| _Too many configurations for this server._ | Free servers have one configuration. Get premium to add more. |
| _Too many configurations listen to the same voice channel._ | More than 3 configurations use the same voice channel. |
| _The translation of the transcription is reserved for premium servers._ | Remove the translation, or get premium. |
| _One of the output channels is not available on this server._ | The channel was deleted, or it is not a text channel, forum or voice channel chat. Choose another one. |
| _One of the voice channels is not available on this server._ | The voice channel was deleted. Choose another one. |
| _The configuration could not be saved._ | Try again. |

{% hint style="info" %}
The page only saves the configuration. For the permissions the bot needs and the messages posted during a session, see [Voice](../../commands/voice.md#transcription-speech-to-text) and [Voice troubleshooting](../../commands/voice-troubleshooting.md). A step by step setup is in [Voice guides](../../commands/voice-guides.md#4-transcribe-automatically-when-someone-joins-transcribe-auto).
{% endhint %}
