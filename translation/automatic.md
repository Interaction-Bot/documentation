---
description: Translate messages automatically by channel, role, category or group.
---

# Automatic translation

Automatic translation is configured on the [dashboard](../website/dashboard/) or with the [configuration commands](../commands/configuration.md) (`/channel-translation manage`, `/role-translation manage`, `/category-translation manage`, `/group manage`). Once saved, the bot translates the messages **by itself**, nobody has to do anything.

Four kinds of automatic translation exist. They can be combined: when several apply to the same message, the bot handles them in this order: **channel, group, category, role**.

| Kind                                  | Applies to                                       | Typical use                                      |
| ------------------------------------- | ------------------------------------------------ | ------------------------------------------------ |
| [Channel](#channel-translation)       | Every message of one channel                     | `#english` is translated into `#francais`        |
| [Group](#translation-groups)          | Every channel of a group, each with its language | One channel per language, everybody reads theirs |
| [Category](#category-translation)     | Every channel of a category                      | Translate a whole section of the server          |
| [Role](#role-translation)             | Every message written by members with a role    | `@french` members are translated into English    |

## Options shared by all of them

| Option                | What it does                                                                                                                                  |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| **Language**          | Target language of the translation.                                                                                                           |
| **Sending channel**   | Where the translation is posted. Empty = the channel of the original message (role and category).                                             |
| **Style**             | *Embed* (a card with the author, the translation and the languages), *Webhook* (sent under the author's name and avatar), *Message* (plain message), *Thread* (the translations in a thread under the message, see [Translation in threads](threads.md)). |
| **Delete message**    | The original message is deleted, only the translation stays.                                                                                  |
| **Delete translation**| The translation is deleted after a delay: the duration you set (5 seconds to 24 hours), or by default a reading time (0.13 s per character, 25 s minimum). |
| **Translate bot**     | Also translate messages of bots (**premium**).                                                                                                |
| **Always send**       | Translate even if the message already looks like the target language, or if the language is uncertain.                                       |
| **Enabled**           | Pause a configuration without deleting it (channels and groups).                                                                              |

{% hint style="info" %}
**Which style?** *Webhook* is the most natural to read: the translation looks like it was written by the author. It needs the *Manage Webhooks* permission; without it the bot falls back to a plain message. *Embed* shows the languages in its footer. *Message* needs the fewest permissions.
{% endhint %}

## Channel translation

A channel configuration says: "every message sent in **this channel** must be translated into **this language** and sent in **that channel**".

Example: `#english` -> `#francais` in French, and `#francais` -> `#english` in English. Two configurations make a two-way conversation. For more than two languages, use [groups](../commands/groups.md): they are simpler.

Dashboard page: [Channel translation](../website/dashboard/channel-translation.md).

## Role translation

A role configuration translates **everything the members who have this role write**, in any channel where the bot can read, into the chosen language.

Example: members with the role `@french` write in French, and you want everybody to read English: create a role configuration `@french` -> English. If you add Japanese too, each message gets 2 translations.

The [blacklist](../website/dashboard/blacklist.md) lets you exclude channels (role and category translation are not applied there).

Dashboard page: [Role translation](../website/dashboard/role-translation.md).

## Category translation

A category configuration works like a channel configuration for **all the channels of a category**, including the ones you create later. Free servers have 20 configurations, premium servers 500.

Dashboard page: [Category translation](../website/dashboard/category-translation.md).

## Translation groups

A group links several channels, each with **its own language**. A message written in one channel is translated into the language of **every other channel** of the group, one translation per language. You don't have to create every pair yourself.

Example: group "Community" with `#english` (English), `#francais` (French), `#espanol` (Spanish). A message in `#francais` is translated into English and Spanish and sent to the two other channels.

Details, commands and limits: [Translation groups](../commands/groups.md) and the dashboard page [Translation Groups](../website/dashboard/translation-groups.md).

## Bots, webhooks and edits

* The bot never translates **its own** messages, nor the webhook messages it sends.
* Messages of other bots are translated only if _Translate bot_ is on (premium).
* Role translation does not apply to webhook messages.
* Editing a message does not trigger a new translation.

## Good practices

* Give the bot its permissions in **both** the source and target channels (see [Troubleshooting](troubleshooting.md#permissions)). `/check-permissions` tells you exactly what is missing.
* If a language is often detected wrongly, increase the [minimum message size](language-detection.md#minimum-message-size) or [blacklist](../website/dashboard/blacklist.md) that language (premium).
* Use _Delete translation_ in busy channels so translations don't pile up.
