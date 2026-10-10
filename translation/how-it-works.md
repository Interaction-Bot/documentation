---
description: What happens between the moment a message is sent and the moment its translation appears.
---

# How translation works

Understanding the steps makes it much easier to configure the bot and to find why a message was not translated.

## Automatic translation, step by step

When a message is posted, the bot goes through these steps. At any step, the bot can stop and **nothing is translated**.

1. **The message is eligible.** Direct messages, the bot's own messages, messages made only of a link and messages that repeat the same character (`hhhhhh`) are ignored.
2. **The rules of the channel are loaded.** The bot looks for [channel](../website/dashboard/channel-translation.md), [category](../website/dashboard/category-translation.md), [role](../website/dashboard/role-translation.md) rules and [translation groups](../website/dashboard/translation-groups.md) that apply to this message. If there is none, nothing happens.
3. **Filters.**
   * The channel is in the [blacklist](../website/dashboard/blacklist.md) (premium).
   * The author has a blacklisted role (premium).
   * The message is shorter than the *minimum characters* set in [Language identification](../website/dashboard/language-identification.md) for this channel.
   * The message comes from a bot and *Translate bot* is off (messages of bots are translated on premium servers only).
4. **Language detection.** The language of the message is detected automatically. If the bot is not sure (very short message, only emojis, mixed languages), the message is skipped, except for rules with *Always send*. If the language is in the blacklisted languages (premium), the message is skipped.
5. **For each rule**, the bot checks that the message is not already in the target language (unless *Always send* is on), then translates it. If the translation is almost identical to the original (similarity of 60 % or more) it is considered "already translated" and is not sent.
6. **Sending.** The translation is sent in the target channel with the chosen [style](styles-and-options.md). *Delete message* and *Delete translation* are applied.

{% hint style="info" %}
The bot shows **"Interaction Bot is typing…"** in the target channels while a translation is prepared, so members know that a translation is coming.
{% endhint %}

## Limits that protect your server

| Limit                                 | Free  | Premium |
| ------------------------------------- | ----- | ------- |
| Translations produced by one message  | 3     | 20      |
| Configurations of each type           | 20    | 500     |

When a message needs more translations than the limit allows, the bot sends the translations in the order of the rules (channels, then groups, then categories, then roles) and stops at the limit, then posts a short notice. This notice can be turned off in the dashboard with the *Simultaneous translation warning* option of the [Overview](../website/dashboard/overview.md) page.

To avoid floods, the bot also protects itself against servers that send an abnormal number of messages or reactions: translations are then paused for a short time. A normal community never reaches these protections.

## Flag translation, step by step

1. A member adds a flag emoji (🇫🇷, 🇪🇸, 🇯🇵…) under a message. The flag decides the target language ([171 flags](languages.md) are supported).
2. The bot checks the [flag translation](../website/dashboard/flag-translation.md) configuration of the channel. Without any configuration, the flags **work by default**.
3. Bots are ignored, and messages written by bots are translated on premium servers only.
4. In **Once** mode, a message is translated only the first time a flag is added. In **Every time** mode, every flag added produces a translation.
5. The translation is posted as a **reply** to the message, in an embed that shows the source and target languages. It is deleted after a while unless *Auto delete* is turned off (about 0.13 s per character, at least 25 seconds).

{% hint style="info" %}
🏴‍☠️ the pirate flag translates the message in English and then in pirate speech.
{% endhint %}

## Commands and menus, step by step

* **`/translate`** and **Apps > Translate** detect the language of the message, translate it into the language you choose (or your Discord language) and answer privately (ephemeral message: only you see it, and you can dismiss it).
* **`/detect`** and **Apps > Detect** only tell you the detected language.
* They are limited to one use every few seconds per member.

## What is kept intact

The translation keeps the message readable:

| Element                                                  | Behaviour |
| -------------------------------------------------------- | --------- |
| Bold, italic, underline, strikethrough, spoiler          | Kept around the corresponding words |
| Quotes, lists, titles                                    | Kept (the prefix is not translated) |
| Code blocks and inline code                              | Never translated |
| Links                                                    | Kept as they are |
| Mentions (`@user`, `@role`, `#channel`) and emojis       | Kept as they are; the bot **never pings** anyone in a translation |
| Attachments (smaller than 1 MB)                          | Copied with the translation |
| Embeds, buttons and select menus                         | Translated on premium servers |

## Translation quality

Interaction Bot uses neural translation models. Short messages, slang, abbreviations and words that exist in several languages are the hardest cases. The detection of the language is generally right from about ten characters. Premium servers always get the best model and a priority when the service is busy.
