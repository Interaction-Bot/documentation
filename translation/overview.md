---
description: Every way to translate with Interaction Bot, and which one to choose.
---

# Translation overview

Interaction Bot translates Discord messages between **100 languages**. It can translate **automatically**, with the translation rules of the dashboard (a channel, two languages in one channel, linked channels, a category, a role or the whole server), or **on demand**, with a flag reaction or a command. Everything is free to use; [Premium](../premium/premium.md) raises the limits and unlocks a few options.

Translation is configured on the [dashboard](../website/dashboard/) or with the [AI assistant](../management/ai-setup.md) (`/ai setup`). There is no configuration command: `/config` explains both ways.

## Choose your method

| I want to...                                                 | Use                                                                                  | Needs the dashboard |
| ------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------- |
| Translate a text I type                                      | [`/translate`](commands.md#translate) (the answer is public)                         | No                  |
| Translate a message someone else wrote, only for me          | Apps > Translate (right click or long press on the message): a private answer       | No                  |
| Know the language of a text                                  | [`/detect`](commands.md#detect) (public), or Apps > Detect (private)                         | No                  |
| Let members translate any message with one click             | [Flag reactions](flags.md) (members add a flag emoji under a message)               | Optional            |
| Add flag buttons under every new message of a channel        | [Automatically added flags](flags.md#automatically-added-flags)                      | Yes                 |
| Translate the messages of a channel into another language    | [Translation rules](automatic.md#channels) (a channel, or two languages in one channel) | Yes              |
| Translate everything a group of people (a role) writes       | [Translation rules](automatic.md#roles) (a role)                                     | Yes                 |
| Translate a whole category, or the whole server              | [Translation rules](automatic.md#categories-and-the-whole-server)                     | Yes                 |
| Link several channels, each in its own language              | [Translation rules](automatic.md#linked-channels) (linked channels)                  | Yes                 |

## Translation from the first minute

A new server gets one rule when the bot joins it: the whole server is translated into the language of the server on Discord. Change it or delete it in the [Translation rules](../website/dashboard/translation-rules.md#the-rule-of-a-new-server) page.

## How the bot translates a message

1. A message is posted in a channel that has a translation rule, or a member adds a flag, or someone runs a command or a menu.
2. The bot **detects the language** of the message (see [language detection](language-detection.md)).
3. The **exceptions** of the server are checked: the channels, roles and languages that are never translated, and the minimum size of a message (see [Exceptions](../website/dashboard/exceptions.md)).
4. The bot picks the rules that apply: the most precise one wins (see [which rule applies](automatic.md#which-rule-applies)).
5. It translates the text and sends the result with the style you chose: as the author, as a bot message, as a bot card, or in a thread (see [styles and options](styles-and-options.md)).

### When the bot does NOT translate

Automatic translation is skipped when:

* the message **only contains a link**, or a single character repeated (`aaaaaa`);
* the language of the message is **already the target language**, unless _Send even if the text seems already translated_ is on;
* the detection is **not reliable** enough, for example a very short message or a message with only emojis, unless _Send even if the text seems already translated_ is on (see [language detection](language-detection.md));
* the message is **shorter than the minimum size** of its channel, or its channel, one of its author's roles or its language is excluded in the [Exceptions](../website/dashboard/exceptions.md) (Premium);
* the message comes from **a bot**, on a server without Premium. On Premium, a translation rule translates it only if its _Translate bots_ option is on; a flag reaction does translate it;
* the translation is almost identical to the original text (a similarity of 60 % or more): the text is already in that language;
* the bot [lacks a permission](troubleshooting.md#permissions) in the channel.

### What is translated

| Content                                                                 | Free | Premium |
| ----------------------------------------------------------------------- | ---- | ------- |
| Message text                                                            | Yes  | Yes     |
| Pictures and files, copied with the translation (8 MB at most in total) | Yes  | Yes     |
| Text of embeds (title, description, fields, footer)                     | No   | Yes     |
| Buttons and select menus labels                                         | No   | Yes     |

The footer of an embed-style translation shows the source and target languages, for example `French (fr) -> English (en)`. Flag translations show the codes in capitals, `French (FR) -> English (EN)`.

## Limits

| Limit                                                       | Free                   | Premium                |
| ----------------------------------------------------------- | ---------------------- | ---------------------- |
| Translations of one message                                 | 3                      | 20                     |
| Translation rules per server                                | 30                     | 200                    |
| Languages in one rule (in the form)                         | 5                      | 20                     |
| Linked channels: links per server, channels per link        | 1, with 3 channels     | 5, with 5 channels     |
| Channels with a minimum message size                        | 20                     | 500                    |
| Channels with a flag reaction setting                       | 20                     | 500                    |

* **Translations of one message**: when one message must be translated into several languages, the bot stops at **3 translations on a free server and 20 on a premium server**. The translations beyond the limit are **not sent**. The **Translation rules** page then shows a notice with the affected channels. The bot also posts a warning in the channel, at most once a day per server; turn it off with the _Simultaneous Translation Warning_ option of the [Overview](../website/dashboard/overview.md).
* **Try it**: the tools of the Translation rules page show which translations a sentence would get, and which ones the limit cuts.
* **Premium**: see [Premium](../premium/premium.md) for all the limits.

## Languages

The source language is detected for you; you only choose the **target** language. In `/translate`, choose the language in the list that appears while you type, by its name or its code. `/languages` lists all the supported languages. See [Languages and flags](languages.md).

## Next steps

{% content-ref url="automatic.md" %}
[automatic.md](automatic.md)
{% endcontent-ref %}

{% content-ref url="flags.md" %}
[flags.md](flags.md)
{% endcontent-ref %}

{% content-ref url="commands.md" %}
[commands.md](commands.md)
{% endcontent-ref %}

{% content-ref url="how-it-works.md" %}
[how-it-works.md](how-it-works.md)
{% endcontent-ref %}

{% content-ref url="styles-and-options.md" %}
[styles-and-options.md](styles-and-options.md)
{% endcontent-ref %}
