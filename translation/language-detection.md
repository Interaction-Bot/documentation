---
description: How the bot recognizes the language of a message, what it looks at for a short message, and how to improve it.
---

# Language detection

Before translating, the bot has to know **which language the message is written in**. It detects it automatically among 100 languages, and it also estimates how *reliable* the result is. If the bot is not confident enough, it does not translate: a message is never "translated" from a wrong language, unless the rule has _Send even if the text seems already translated_ on.

You never choose the source language. You only choose the **target** language of each rule.

## Messages used to detect the language

A short or ambiguous message ("ok", "Jajaja", "Son infumables") is often too short to be sure of its language, while its author usually writes in one language. To settle such a message, the bot also looks at the **previous messages of the same author**.

The setting **Messages used to detect the language** is on the [Overview](../website/dashboard/overview.md) page of the dashboard:

| Value        | What the bot does                                                                                                    |
| ------------ | -------------------------------------------------------------------------------------------------------------------- |
| **1**        | Each message is read alone. Nothing is remembered.                                                                   |
| **2 to 10**  | The message is read with the author's last messages (the default is **5**). The bot uses them only to settle an unclear message. |

The context is made of the author's messages:

* first, the messages of the author **in this channel**. When there are too few, the bot reads the recent history of the channel once;
* then, the author's messages **elsewhere on the server**.

Only the author counts: a French member writing in an English channel stays French.

### What the bot keeps

* The texts of the recent messages are kept in the **memory of the bot only**, for **10 minutes**. They are never written to the database, to a file or to the logs, and they are forgotten when the bot restarts.
* Messages of **bots** and **webhooks** are not kept, and neither are the messages of a member who opted out of the processing of their messages.
* With the setting at **1**, nothing is kept.

## Why a message can be detected wrongly

* The message is **very short** ("ok", "lol", "ça va"): too few words to be sure.
* It contains mostly **emojis, links, names, code** or numbers.
* The language is **close to another one** (Spanish and Portuguese, Indonesian and Malay...).
* The author switches language in the middle of a message.

## How to improve it

### Raise the number of messages used

If short messages of the same member are mistranslated, raise **Messages used to detect the language** on the [Overview](../website/dashboard/overview.md) page. The default is 5.

### Set a minimum message size

In the [Exceptions](../website/dashboard/exceptions.md) page (**Minimum message size**), set, per channel, the **number of characters** a message must have to be translated. A message shorter than this is not translated. Raise it if very short messages are often mistranslated.

### Exclude a language (Premium)

If a language is often confused with another one in your community, add it to the **Languages** of the [Exceptions](../website/dashboard/exceptions.md) page: messages detected in that language are never translated. This is a [Premium](../premium/premium.md) feature.

### Send even if the text seems translated

The option _Send even if the text seems already translated_ of a rule translates a message even when the detection is not sure, or when the message already looks like the target language. Use it carefully: it can produce translations of messages that are already fine. See [Automatic translation](automatic.md#options-of-the-rules).

## Check the language of a text

Use **Apps > Detect** on a message to see what the bot thinks of it, with the context of its author. [`/detect`](commands.md#detect) reads the text you type alone. The answer of Apps > Detect is private; the one of `/detect` is posted in the channel.
