---
description: What happens between the moment a message is sent and the moment its translation appears, and why a message is sometimes not translated.
---

# How translation works

Understanding the steps makes it much easier to configure the bot and to find why a message was not translated.

## Automatic translation, step by step

When a message is posted in a server, the bot goes through these steps. At any step, the bot can stop, and **nothing is translated**.

1. **The message is eligible.** Direct messages, the bot's own messages and messages made only of a link are ignored, and so are messages that repeat the same character (`hhhhhh`) for the rules that do not have _Send even if the text seems already translated_.
2. **The server has a translation feature on.** Each feature (translation, flags, voice messages...) has its own switch on the dashboard. If none is on, nothing happens.
3. **The rules are loaded.** The bot looks for the [translation rules](automatic.md) that apply to this channel, its category, the roles of the author and the server. If none applies and the channel is not linked to others, nothing happens.
4. **The exceptions.** The minimum size of the message is checked; on Premium, the channel and the author's roles too, then the language (see [Exceptions](../website/dashboard/exceptions.md)). A message that matches one of them is skipped.
5. **Bots.** A message from a bot is ignored on a server without Premium. On Premium, it is translated only by the rules with the _Translate bots_ option.
6. **Language detection.** The language of the message is detected (see [language detection](language-detection.md)). If the bot is not sure (a very short message, only emojis, mixed languages), the message is skipped, unless the rule has _Send even if the text seems already translated_.
7. **For each rule**, the bot checks that the message is not already in the target language (unless the rule says otherwise), then translates it. If the translation is almost identical to the original (a similarity of 60 % or more), it is considered already translated and is not sent.
8. **Sending.** The translation is sent in the target channel with the chosen [style](styles-and-options.md). _Delete the original message_ and _Delete the translation after_ are applied.

{% hint style="info" %}
While a translation is prepared, the bot shows **"Interaction Bot is typing…"** in the target channel, so members know that a translation is coming.
{% endhint %}

## Limits that protect your server

| Limit                                                  | Free  | Premium |
| ------------------------------------------------------ | ----- | ------- |
| Translations produced by one message                   | 3     | 20      |
| Translation rules per server                           | 30    | 200     |
| Languages in one rule                                  | 5     | 20      |
| Linked channels (links per server, channels per link)  | 1, 3 channels | 5, 5 channels |

When a message needs more translations than the limit allows, the bot sends the translations in the order of the rules (the two languages of a channel, the channel, the category, the server, then the roles) and stops at the limit. It then posts a short notice, at most once a day per server. The notice can be turned off with the *Simultaneous Translation Warning* option of the [Overview](../website/dashboard/overview.md) page.

To avoid floods, the bot also protects itself against servers that send an abnormal number of messages or reactions: translations are then paused for a short time. A normal community never reaches these protections.

## Flag translation, step by step

1. A member adds a flag emoji (🇫🇷, 🇪🇸, 🇯🇵…) under a message. The flag decides the target language ([175 flags](languages.md) are known).
2. The bot checks the [Flags](../website/dashboard/flag-translation.md) settings of the channel. Without settings, the flags **work by default**.
3. A reaction by a bot is ignored. A message written by a bot is translated on Premium servers only.
4. In **Once per message** mode, a message is translated only the first time a flag is added. In **Each time someone reacts** mode, every flag added makes a translation.
5. The translation is posted as a **reply** to the message, in an embed by default, with the source and target languages in its footer. It is deleted after a while if _Delete the translation automatically_ is on (0.13 second per character, at least 25 seconds).

Flag translations do not follow the exceptions of the server, nor the translation rules.

{% hint style="info" %}
🏴‍☠️ The pirate flag translates the message into English, then into pirate speech.
{% endhint %}

## Commands and menus, step by step

* **`/translate`** detects the language of a text and translates it into the language you choose (or your personal language, or your Discord language). Its answer is **public**.
* **Apps > Translate** does the same for a message, with a **private** answer (only you see it).
* **`/detect`** (posted in the channel) and **Apps > Detect** (private) only tell you the detected language.
* They are limited to one use every few seconds per member.

## What is kept intact

The translation keeps the message readable:

| Element                                            | Behaviour                                                          |
| -------------------------------------------------- | ------------------------------------------------------------------ |
| Bold, italic, underline, strikethrough, spoiler    | Kept around the corresponding words                                |
| Quotes, lists, titles                              | Kept (the prefix is not translated)                                |
| Code blocks and inline code                        | Never translated                                                   |
| Links                                              | Kept as they are                                                   |
| Mentions (`@user`, `@role`, `#channel`) and emojis | Kept as they are                                                   |
| Pings                                              | Never: the bot does not ping anyone in a translation               |
| Pictures and files                                 | Copied with the translation (8 MB at most in total)                 |
| Embeds, buttons and select menus                   | Translated on Premium servers only                                 |

## Translation quality

Interaction Bot uses neural translation models. Short messages, slang, abbreviations and words that exist in several languages are the hardest cases. The language is generally detected right from about ten characters. Premium servers always get the best model and a priority when the service is busy.
