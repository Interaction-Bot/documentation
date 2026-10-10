---
description: The bot does not translate? Check these points.
---

# Troubleshooting translation

## Quick checklist

1. **Is the configuration saved?** On the dashboard, click _Save_ after any change. Check that the configuration is **enabled**.
2. **Does the bot have its permissions** in the source **and** the target channel? Run **`/check-permissions`**: it lists the missing permissions of every configured channel.
3. **Is the message long enough?** Very short messages are not translated (see [language detection](language-detection.md)).
4. **Is the message already in the target language?** Then nothing is sent (unless _Always send_ is on).
5. **Is the message only a link, or sent by a bot?** Links alone are ignored, bots need the premium option _Translate bot_.
6. **Did you reach the limit?** 3 translations per message on a free server (20 premium): extra ones are dropped and a warning is posted.
7. **Is the channel or role in the blacklist?** (premium)

## Permissions

The bot needs these permissions **in the channels it uses**:

| Where                     | Permissions                                                                 |
| ------------------------- | --------------------------------------------------------------------------- |
| Source channel            | View Channel, Read Message History                                          |
| Target channel, *embed* style   | View Channel, Send Messages, Embed Links, Attach Files                |
| Target channel, *webhook* style | View Channel, Send Messages, **Manage Webhooks**, Attach Files         |
| Target channel, *message* style | View Channel, Send Messages, Attach Files                              |
| *Delete message* option   | Manage Messages (in the source channel)                                     |
| Flag shortcuts            | Add Reactions                                                               |
| Voice features            | Connect, Speak                                                              |

{% hint style="info" %}
The simplest way is to give the bot a role with these permissions, and to check the **channel permission overrides** (a channel can refuse what the role allows).
{% endhint %}

## Typical problems

| Symptom                                                  | Cause and fix                                                                                         |
| -------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| Nothing happens in a channel                              | Missing permission or configuration not saved: run `/check-permissions`.                              |
| The translation is in the wrong language                  | The detection was wrong: raise the [minimum size](language-detection.md#minimum-message-size).        |
| Translations are posted as plain messages, not webhooks   | The bot lacks *Manage Webhooks*; it falls back to plain messages.                                      |
| "You have exceeded the limit of translation" warning      | More than 3 (or 20) translations for one message: reduce configurations or go premium. You can turn the warning off in the dashboard Overview. |
| Messages of a bot are not translated                      | Premium option _Translate bot_.                                                                       |
| The original message was not deleted                      | The bot lacks *Manage Messages*.                                                                       |
| A flag reaction does nothing                              | Flag translation is disabled in this channel on the dashboard, or the message is empty / written by a bot (premium only). |
| `/translate` says the language is not supported           | Pick the language from the autocomplete list.                                                         |

Still stuck? Join the [support server](https://support.interaction-bot.com).
