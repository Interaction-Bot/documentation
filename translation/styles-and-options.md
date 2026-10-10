---
description: The three styles of translation and every option of the dashboard explained.
---

# Styles and options

Channel, category and role translation and translation groups share the same options. This page explains them all, with examples. The options are in the **OPTIONS** dropdown of the popup of each configuration on the [dashboard](../website/dashboard/README.md).

## The three styles

The *style* is how the translation looks in the channel.

| Style       | What members see                                                                                   | Needs on the bot |
| ----------- | -------------------------------------------------------------------------------------------------- | ---------------- |
| **Embed**   | A card with the translation, the name and avatar of the author at the top, and a footer such as *English (en) -> French (fr).* | Embed Links |
| **Webhook** | The translation as if the **author wrote it**: same name, same avatar, no "bot" label. It reads like a natural conversation. | Manage Webhooks |
| **Message** | A plain message sent by the bot, without any decoration.                                           | Send Messages |

{% hint style="success" %}
**Webhook** is the best choice for a conversation between languages, **Embed** for an announcement channel where you want to see the languages, and **Message** for the most discreet display.
{% endhint %}

If the bot cannot create the webhook (missing permission), it falls back to a plain message, so the translation is never lost.

The bot never mentions anybody in the translations: `@everyone`, roles and members appear as text without pinging.

## Options of the configurations

| Option                    | Where                          | What it does                                                                                           |
| ------------------------- | ------------------------------ | ------------------------------------------------------------------------------------------------------ |
| **Channel / Category / Role** | Channel, category, role      | What the rule applies to.                                                                              |
| **Sending channel**       | All                            | Where the translation is sent. Empty: the channel where the message was written (category and role). Required for a channel translation. It must be a channel of the same server. |
| **Language**              | All                            | The target language. Every message that is not in this language is translated into it.                  |
| **Style**                 | All                            | Embed, webhook or message (see above).                                                                 |
| **Delete message**        | All                            | The original message is deleted when it is translated. Only the translation stays. Needs *Manage Messages*. |
| **Delete translation**    | All                            | The bot deletes its translation after a delay. By default the delay depends on the length of the text (0.13 s per character, at least 25 s). |
| **Keep it for (seconds)** | All                            | With *Delete translation*, choose the delay yourself, from 5 s to 24 h.                                |
| **Translate bot**         | Channel, category, role, group | Also translate the messages sent by bots. **Premium only.**                                            |
| **Always send**           | All                            | Send the translation even if the message already seems to be in the target language, or when the bot is not sure of the detected language. |
| **Enabled**               | All                            | Turn a configuration off without deleting it.                                                          |

### "Delete message" in practice

The original message is deleted **only when a translation was really sent**. If the message is already in the target language, it stays. This avoids members losing their messages.

### "Always send" in practice

By default the bot does not translate a message that is already in the target language. This is what you want 99 % of the time. Turn *Always send* on when:

* your members write short messages and the detection is often unsure;
* you want a **tone or style check**: the bot translates even if the language is the same.

## Permissions needed

Give the bot these permissions in the source channel **and** in the sending channel:

| Permission                | Used for                                          |
| ------------------------- | ------------------------------------------------- |
| View Channel              | Reading the messages                              |
| Send Messages             | Sending the translation (style message)           |
| Embed Links               | Sending the translation (style embed)             |
| Manage Webhooks           | Sending the translation (style webhook)           |
| Manage Messages           | Deleting the original message (*Delete message*)  |
| Read Message History      | Flag translation (reading the message)            |
| Add Reactions             | Flag shortcuts                                    |

The command `/check-permissions` lists the permissions that are missing in a channel (see [Flags and diagnostics](../commands/flags.md)).
