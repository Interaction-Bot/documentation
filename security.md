---
description: What the bot can see, what it stores, and how the dashboard is protected.
---

# Security and privacy

## What the bot can see

The bot asks Discord for the minimum it needs:

* **Servers and channels**, to know where to translate;
* **Messages and their content**, to translate them, detect their language, answer the FAQ;
* **Reactions**, for the [flag translation](translation/flags.md);
* **Voice states**, to join voice channels for [text to speech and transcription](audio/voice.md).

## What it keeps

The bot keeps **your configuration** (channels, roles, languages, options, FAQ entries, premium state) so it can apply it. Messages are processed to be translated, they are not a part of your configuration. For the details and your rights, read the [Privacy Policy](https://interaction-bot.com/privacy) and the [Terms of Use](https://interaction-bot.com/tou).

## The dashboard

* You log in with your **Discord account** (OAuth). The bot never sees your Discord password.
* You can only configure the servers where you have the *Administrator* permission and where the bot is present.
* The bot only posts in channels **of the server** that owns the configuration.

## Voice features

* The bot listens to a voice channel **only while a transcription is running** (started by a command, or by the automatic mode you enabled).
* Transcription time is limited per server and per day (30 minutes on a free server, 2 hours on premium, over 24 hours from the first transcription) and the bot leaves when no human remains.

## Report a problem

If you found a security problem, please contact the [support](https://support.interaction-bot.com) privately and do not publish it.
