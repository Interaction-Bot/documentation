---
description: How the bot recognizes the language of a message, and how to improve it.
---

# Language detection

Before translating, the bot has to know **which language the message is written in**. It detects it automatically among 100 languages, and it also estimates how *reliable* the result is: if the bot is not confident enough, it does not translate (so a message is never "translated" from a wrong language) unless _Always send_ is on.

## Why a message can be detected wrongly

* The message is **very short** ("ok", "lol", "ça va"): too few words to be sure.
* It contains mostly **emojis, links, names, code** or numbers.
* The language is **close to another one** (Spanish and Portuguese, Indonesian and Malay...).

## How to improve it

### Minimum message size

On the dashboard, [Language identification](../website/dashboard/language-identification.md) lets you set, per channel, the **minimum number of characters** a message must have to be translated. Raise it if short messages are mistranslated.

### Blacklist a language (premium)

If a language is often confused with another one in your community, add it to the [blacklist](../website/dashboard/blacklist.md): messages detected in that language are ignored.

### Always send

The _Always send_ option of a configuration translates even if the detection is not confident, or if the message already looks like the target language. Use it carefully: it can produce translations of messages that are already fine.

## Check the language of a text

Use [`/detect`](commands.md) or **Apps > Detect** on a message to see what the bot thinks.
