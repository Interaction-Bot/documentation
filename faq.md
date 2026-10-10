---
description: Get more frequent question asked by user of Interaction Bot.
---

# FAQ

## Why is the translation of a message wrong?

The bot translates for free on tens of thousands of servers, with automatic translation models. The quality depends on the languages and on the message (slang, abbreviations and very short texts are harder). We keep improving the translation models.

## Why is my message detected in the wrong language?

The bot supports more than 100 languages and must detect them in any message. A message that is too short, or full of emojis and other elements, can be mistaken. You can increase the minimum size of a message for the detection in [Language identification](website/dashboard/language-identification.md), or ban a language that is too often confused with another one in the [blacklist](website/dashboard/blacklist.md) (premium).

## The bot does not translate in a channel

Check that the bot has the permissions *View Channel*, *Send Messages* and *Embed Links* (and *Manage Webhooks* for the webhook style) in the source and target channels, that the configuration is saved on the [dashboard](website/dashboard/), and that the message is long enough for the detection.

## My server does not appear on the dashboard

You must have the *Administrator* permission on the server, be logged in with the right Discord account, and the bot must be on the server.

## How do I use `/tts` or `/connect`?

These commands require a [top.gg vote](https://top.gg/bot/893494390142697493/vote) in the last 24 hours. See [Voice](commands/voice.md).

## The transcription (`/transcribe`) does not work

The speech-to-text feature is currently disabled. See [Voice](commands/voice.md).

## How do I get premium?

See [Premium](premium/premium.md) and [Subscribe](premium/subscribe.md).
