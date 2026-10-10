---
description: Every way to translate with Interaction Bot, and which one to choose.
---

# Translation overview

Interaction Bot translates Discord messages between **100 languages**. It can translate on demand (a command, a menu, a flag) or **automatically** (channels, roles, categories, groups). Everything is free to use; [premium](../premium/premium.md) raises the limits and unlocks a few options.

## Choose your method

| I want to...                                                              | Use                                                                                      | Needs the dashboard |
| ------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | ------------------- |
| Translate a text I type, only for me                                      | [`/translate`](commands.md)                                                              | No                  |
| Translate a message someone else wrote, only for me                       | [Apps > Translate](commands.md#apps-menus) (right click on the message)                  | No                  |
| Let members translate any message with one click                          | [Flag reactions](flags.md) (add a flag emoji), or [Flag shortcuts](flags.md#flag-shortcuts) | Optional            |
| Translate every message of a channel into another language               | [Channel translation](automatic.md#channel-translation)                                  | Yes                 |
| Translate everything a group of people (a role) writes                    | [Role translation](automatic.md#role-translation)                                        | Yes                 |
| Translate a whole category of channels                                    | [Category translation](automatic.md#category-translation)                                | Yes                 |
| Link several channels, one per language, so everybody reads their language | [Translation groups](../commands/groups.md)                                              | Optional            |
| Know the language of a text                                               | [`/detect`](commands.md), or Apps > Detect                                               | No                  |

## How the bot translates a message

1. A message is sent in a channel that has an automatic configuration (or someone adds a flag, or runs a command).
2. The bot **detects the language** of the message (see [language detection](language-detection.md)).
3. For each configuration that applies, it checks that the translation is useful (see the rules below).
4. It translates the text and sends the result with the style you chose: embed, webhook or plain message.

### When the bot does NOT translate

Automatic translation is skipped when:

* the message **only contains a link**, or a single character repeated (`aaaaaa`);
* the language of the message is **already the target language** (unless _Always send_ is on);
* the detection is **not reliable** enough, for example a very short message (unless _Always send_ is on). You can set a [minimum size](language-detection.md#minimum-message-size) per channel;
* the message was sent by **a bot** and _Translate bot_ is off (this option is [premium](../premium/premium.md));
* the channel, or one of the author's roles, is in the [blacklist](../website/dashboard/blacklist.md) (premium);
* the detected language is in the [language blacklist](../website/dashboard/blacklist.md) (premium);
* the translation would be identical to the original text;
* the bot [lacks a permission](troubleshooting.md#permissions) in the channel.

### What is translated

| Content                              | Free | Premium |
| ------------------------------------ | ---- | ------- |
| Message text                         | Yes  | Yes     |
| Attachments (re-sent, up to 1 MB)    | Yes  | Yes     |
| Text of embeds (title, description, fields, footer) | No | Yes |
| Buttons and select menus labels      | No   | Yes     |

The footer of an embed-style translation shows the source and target languages (for example `French (fr) -> English (en)`).

## Limits

* **Translations per message**: when one message must be translated into several languages (several configurations apply), the bot stops after **3 translations on a free server and 20 on a premium server**. When this happens the bot posts a warning that you can turn off in the [Overview](../website/dashboard/overview.md) of the dashboard (_Simultaneous Translation Warning_).
* **Configurations**: 20 channel, role and category configurations on a free server (500 on premium). See [Premium](../premium/premium.md) for all the limits.

## Languages

`/languages` lists all the supported languages. The bot accepts the language name or its code (`fr`, `ja`, `pt`...).

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
