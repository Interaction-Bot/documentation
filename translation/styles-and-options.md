---
description: The four styles of translation and every option of the dashboard explained.
---

# Styles and options

Channel, category and role translation and translation groups share the same options. This page explains them all, with examples. The options are in the **OPTIONS** dropdown of the popup of each configuration on the [dashboard](../website/dashboard/README.md).

## The four styles

The *style* is how the translation looks in the channel.

| Style       | What members see                                                                                   | Needs on the bot |
| ----------- | -------------------------------------------------------------------------------------------------- | ---------------- |
| **Embed**   | A card with the translation, the name and avatar of the author at the top, and a footer such as *English (en) -> French (fr).* | Embed Links |
| **Webhook** | The translation as if the **author wrote it**: same name, same avatar, no "bot" label. It reads like a natural conversation. | Manage Webhooks |
| **Message** | A plain message sent by the bot, without any decoration.                                           | Send Messages |
| **Thread**  | The translations are in a **thread under the original message**, which stays in the channel. All the languages of a message are in the same thread. See [Translation in threads](threads.md). | Create Public Threads, Send Messages in Threads |

{% hint style="success" %}
**Webhook** is the best choice for a conversation between languages, **Embed** for an announcement channel where you want to see the languages, and **Message** for the most discreet display.
{% endhint %}

If the bot cannot create the webhook (missing permission), it falls back to a plain message, so the translation is never lost. In the same way, if it cannot create the thread, the translation is sent as a webhook message in the channel.

{% hint style="info" %}
**Thread** is available for channel, category and role translations, from the dashboard or with the [configuration commands](../commands/configuration.md). It keeps the channel clean when you translate into several languages: [Translation in threads](threads.md).
{% endhint %}

The bot never mentions anybody in the translations: `@everyone`, roles and members appear as text without pinging.

## Options of the configurations

| Option                    | Where                          | What it does                                                                                           |
| ------------------------- | ------------------------------ | ------------------------------------------------------------------------------------------------------ |
| **Channel / Category / Role** | Channel, category, role      | What the rule applies to.                                                                              |
| **Sending channel**       | All                            | Where the translation is sent. Empty: the channel where the message was written (category and role). Required for a channel translation. It must be a channel of the same server. |
| **Language**              | All                            | The target language. Every message that is not in this language is translated into it.                  |
| **Style**                 | All (thread: channel, category, role) | Embed, webhook, message or thread (see above).                                                  |
| **Look in the thread**, **Archive the thread after**, **Show the language** | Style thread | Look of the translations in the thread (webhook, message, embed), inactivity before archiving (1 hour to 7 days) and language written above each translation. See [Translation in threads](threads.md#the-options-of-the-thread-style). |
| **Delete message**        | All (not with thread)          | The original message is deleted when it is translated. Only the translation stays. Needs *Manage Messages*. Not available with the thread style, which keeps the original message. |
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
| Create Public Threads     | Creating the thread (style thread)                |
| Send Messages in Threads  | Writing in the thread (style thread)              |
| Manage Threads            | Reopening a locked archived thread (style thread, optional) |

The command `/check-permissions` lists the permissions that are missing in a channel (see [Flags and diagnostics](../commands/flags.md)).
