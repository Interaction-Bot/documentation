---
description: Configure the live transcription of voice channels.
---

# Speech to text

## Localization

Navbar > category _**Audio & AI**_ > _**Speech to text**_.

## Transcription

The bot transcribes the speech of voice channels and posts the transcriptions in a text channel, a forum or the chat of the voice channel. The spoken language is detected automatically. You can also use [`/transcribe`](../../commands/voice.md).

Use the _**Enabled / Disabled**_ toggle to enable the transcription on the server, then click _**Add a configuration**_. For each configuration:

* **Voice channel**: listen to a specific voice channel, or to _All voice channels_ (default).
* **Text channel**: where the transcriptions are posted: a text channel, a forum, or a voice channel chat. By default, the chat of the voice channel being transcribed.
* **Translate to** (**premium**): translate each transcription into this language. Only the translation is posted.
* **Style**:
  * _Embed_: a card with the transcription (and its translation).
  * _Message_: a plain message, speaker name followed by the text. Needs no embed permission.
  * _Webhook_ (default): sent under the speaker's name and avatar. Needs the *Manage Webhooks* permission, otherwise a plain message is used.

Changes apply live to a running session.

## Limits

| Free                       | Premium                                  |
| -------------------------- | ---------------------------------------- |
| 1 configuration            | Unlimited configurations                 |
| Session of 30 minutes      | Session of 2 hours                       |
| Needs a recent top.gg vote | No vote needed                           |
| No translation             | Translation of the transcription         |

At most 3 configurations can listen to the same voice channel.
