---
description: The bot does not translate? Check these points, in this order.
---

# Troubleshooting translation

## Quick checklist

1. **Is the rule saved and enabled?** On the [Translation rules](../website/dashboard/translation-rules.md) page, a rule that is paused is shown as paused, and a change is kept only once you click **Save**.
2. **Does the bot have its permissions** in the source **and** the target channel? The **Check a channel** tool of the Translation rules page (*Why isn't it translating?*), or **`/check-permissions`**, lists the missing permissions.
3. **Is the message long enough?** A message shorter than the [minimum size](../website/dashboard/exceptions.md#minimum-message-size) of its channel is not translated, and very short messages are hard to detect (see [language detection](language-detection.md)).
4. **Is the message already in the target language?** Then nothing is sent, unless _Send even if the text seems already translated_ is on.
5. **Is the message only a link, or sent by a bot?** A message with only a link is ignored. Bots are ignored on a server without Premium; on Premium, a rule translates them only with its _Translate bots_ option.
6. **Did you reach the limit?** 3 translations per message on a free server (20 with Premium): the extra translations are not sent, and a warning is posted.
7. **Is the channel, a role of the author or the language excluded?** Check the [Exceptions](../website/dashboard/exceptions.md) page (Premium).

The **Try a sentence** tool of the Translation rules page shows which rules would translate a sentence in a channel, and why a rule would not.

## Permissions

The bot needs these permissions **in the channels it uses**:

| Where                                           | Permissions                                                                |
| ----------------------------------------------- | -------------------------------------------------------------------------- |
| Source channel                                  | View Channel, Read Message History                                         |
| Target channel, *bot message* style             | View Channel, Send Messages, Attach Files                                  |
| Target channel, *bot card* style                | View Channel, Send Messages, Embed Links, Attach Files                     |
| Target channel, *as the author* style           | View Channel, Send Messages, **Manage Webhooks**, Attach Files             |
| *Delete the original message* option            | Manage Messages (in the source channel)                                    |
| Automatically added flags                       | Add Reactions, Read Message History                                        |
| Thread style                                    | Create Public Threads, Send Messages in Threads                            |

{% hint style="info" %}
The simplest way is to give the bot a role with these permissions, and to check the **channel permission overrides**: a channel can refuse what the role allows. `/check-permissions` tells you exactly what is missing.
{% endhint %}

## Typical problems

| Symptom                                                          | Cause and fix                                                                                                                                                       |
| ---------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Nothing happens in a channel                                     | Missing permission, rule not saved or paused, or the channel is excluded: check the points above.                                                                    |
| The translation is in the wrong language                         | The detection was unsure: raise the [messages used to detect the language](language-detection.md#messages-used-to-detect-the-language) or the minimum size of the channel. |
| Translations are plain messages, not "as the author"              | The bot lacks *Manage Webhooks*. It falls back to a bot message.                                                                                                     |
| A warning "you have exceeded the limit of translation" is posted | More than 3 (or 20) translations for one message: reduce the rules of the channel, or go Premium. You can turn the warning off in the Overview of the dashboard.     |
| Messages of a bot are not translated                             | A server without Premium never translates bots. On Premium, turn on **Translate bots** in the rule.                                                                 |
| Pictures with no text are not translated                         | A message with no text has no language to detect. A rule skips it unless _Send even if the text seems already translated_ is on.                                    |
| The original message was not deleted                             | The bot lacks *Manage Messages*, or the rule uses the thread style (which keeps the original message).                                                              |
| A flag reaction does nothing                                     | Flag translation is switched off in this channel, the reaction was made by a bot, the message is empty, or the server is free and the message was written by a bot. |
| An edited message is not translated again                        | *Follow edited messages* is off on the [Overview](../website/dashboard/overview.md), or the message was already translated 5 times in the last hour, or the bot restarted since the translation. |
| `/translate` says the language is not supported                  | Pick the language from the list that appears while you type.                                                                                                         |

Still stuck? Join the [support server](https://support.interaction-bot.com).
