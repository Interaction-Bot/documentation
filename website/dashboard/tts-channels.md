---
description: Read aloud the messages of text channels in voice channels.
---

# Text to speech

<figure><img src="../../.gitbook/assets/dash-text-to-speech.png" alt="Text to speech page"><figcaption><p>Text to speech page</p></figcaption></figure>

## Localization

Navbar > category _**Audio & AI**_ > _**Text to speech**_.

## TTS channels

Each message posted in a TTS channel is **read aloud in the voice channel of its author** (the bot joins the member's voice channel). The same can be done with [`/tts-channel`](../../commands/voice.md).

Click on _**Add a channel**_ and set:

* **Channel**: a text channel of the server.
* **Language of the messages**: _Auto-detect_ (default) or a language.
* **Translate to** (optional): translate each message into this language before reading it. Default: _No translation_.

Click _**Remove this channel**_ to stop reading it, then _**Save**_.

## Limits

| Free       | Premium     |
| ---------- | ----------- |
| 5 channels | 25 channels |

Messages are read up to 200 characters, and a member who posts many messages very quickly is temporarily ignored. Voice features need a premium server or a recent [top.gg vote](https://top.gg/bot/893494390142697493/vote).
