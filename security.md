---
description: What the bot can see, what it stores, and how the dashboard is protected.
---

# Security and privacy

## What the bot can see

The bot asks Discord for the minimum it needs:

* **Servers and channels**, to know where to translate;
* **Messages and their content**, to translate them, detect their language, answer the FAQ;
* **Reactions**, for the [flag translation](translation/flags.md);
* **Voice states**, to join voice channels for [text to speech, transcription and recording](audio/overview.md).

## What it keeps

The bot keeps **your configuration** (channels, roles, languages, options, FAQ entries, premium state) so it can apply it. Messages are processed to be translated, they are not a part of your configuration. For the details and your rights, read the [Privacy Policy](https://interaction-bot.com/privacy) and the [Terms of Use](https://interaction-bot.com/tou).

## The dashboard

* You log in with your **Discord account** (OAuth). The bot never sees your Discord password.
* You can only configure the servers where you have the *Administrator* permission and where the bot is present.
* The bot only posts in channels **of the server** that owns the configuration.

## Voice features

* The bot listens to a voice channel **only while a transcription or a recording is running** (started by a command, by the automatic mode you enabled, or by a member with the permission you gave). Text to speech plays the messages it is given; it does not listen to the voice channel.
* Transcription time is limited per server and per day, from midnight UTC (30 minutes on a free server, 3 hours on premium), and the bot leaves when no human remains. See [Daily limits](audio/limits.md).
* A **recording** is announced: the bot posts a message in the text channel, and says it out loud, each time someone joins. The bot does not record its own announcements.
* The audio of a recording is **encrypted** on the server, with a key of its own for each recording. It is kept 7 days on a free server and 30 days on premium, then deleted. Only the member who started the recording can download it, after logging in with Discord.
* A transcription can also keep a **text** transcript, only if the server turned it on. No audio is kept with it.

## Report a problem

If you found a security problem, please contact the [support](https://support.interaction-bot.com) privately and do not publish it.
