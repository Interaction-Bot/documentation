---
description: The styles of translation and every option of the translation rules and flags explained.
---

# Styles and options

The translation rules and the flag reactions share the same styles and options. This page explains them, with examples. The options are in the popup of each rule on the [Translation rules](../website/dashboard/translation-rules.md) page (**More options**), and on the [Flags](../website/dashboard/flag-translation.md) page.

## The styles

The *style* is how the translation looks in the channel.

| Style (name on the dashboard)           | What members see                                                                                                    | Needs on the bot         |
| --------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ------------------------ |
| **As the author** (*Webhook*)           | The translation as if the **author wrote it**: same name, same avatar, no "bot" label. It reads like a natural conversation. | Manage Webhooks          |
| **Bot message** (*Message*)             | A plain message sent by the bot, without any decoration.                                                            | Send Messages            |
| **Bot card** (*Embed*)                  | A card with the translation, and a footer such as *English (en) -> French (fr)*.                                    | Embed Links              |
| **In a thread** (*Thread*)              | The translations are in a **thread under the original message**, which stays in the channel. All the languages of a message are in the same thread. See [Translation in threads](threads.md). | Create Public Threads, Send Messages in Threads |

Flag reactions have one more style, **Private message**: the translation is sent to the member who added the flag, and nothing is posted in the channel.

{% hint style="success" %}
**As the author** is the best choice for a conversation between languages. **Bot card** is for an announcement channel where you want to see the languages. **Bot message** is the most discreet display.
{% endhint %}

If the bot cannot create the webhook (missing permission), it sends a plain bot message, so the translation is never lost. In the same way, if it cannot create the thread, the translation is sent as a webhook message in the channel.

The bot never pings anybody in a translation: `@everyone`, roles and members appear as text.

## Options of the translation rules

| Option                                  | Where            | What it does                                                                                                                  |
| --------------------------------------- | ---------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| **Channel, category, role, server**     | The rule         | What the rule applies to.                                                                                                     |
| **Languages**                           | The rule         | The target language(s). Every message that is not in this language is translated into it.                                    |
| **Send the translations to**            | Sending          | The channel where the translation is posted. *The same channel* by default. Not used by linked channels.                      |
| **Send style**                          | Sending          | As the author, bot message, bot card, or thread (channel rules only, see below).                                              |
| **Look in the thread**, **Archive the thread after**, **Show the language** | Advanced, with the thread style | How the translations look in the thread (as the author, bot message or bot card), the inactivity before the thread is archived (1 h, 24 h, 3 d or 7 d), and whether the language is written above each translation (on by default). |
| **Delete the original message**         | Deletion         | The original message is deleted when a translation is really sent. Needs *Manage Messages*. Not available with the thread style, which keeps the original message. |
| **Delete the translation after**        | Deletion         | *Never*, *Automatic (reading time)* (0.13 second per character, at least 25 seconds), or *After N seconds* (from 5 seconds to 24 hours). |
| **Translate bots**                      | Advanced         | Also translate the messages of bots. **Premium only.**                                                                        |
| **Send even if the text seems already translated** | Advanced | Send the translation even if the message already seems to be in the target language, or when the bot is not sure of the detected language. |
| **Translate in the original channel too** | Advanced, linked channels | A message written in another language than the one of its channel is first translated into the language of that channel. |
| **Enabled** (switch)                    | The rules page   | Pause a rule without deleting it.                                                                                             |

### "Delete the original message" in practice

The original message is deleted **only when a translation was really sent**. If the message is already in the target language, it stays. This avoids members losing their messages.

### "Send even if the text seems already translated" in practice

By default, the bot does not translate a message that is already in the target language. This is what you want almost always. Turn the option on when:

* your members write short messages and the detection is often unsure;
* you want a **tone or style check**: the bot translates even if the language is the same.

## Options of the flag reactions

| Option                                     | What it does                                                                                                                                                                    |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Style**                                  | *Embed* (default), *Webhook*, *Message*, *Thread* or *Private message* (see above).                                                                                             |
| **How often is it translated?**            | *Each time someone reacts* (default), or *Once per message*.                                                                                                                    |
| **Delete the translation automatically**   | The translation is deleted after the reading time (0.13 second per character, at least 25 seconds). A new configuration starts with it off.                                  |
| **Look in the thread**, **Archive the thread after**, **Show the language** | The same as for the translation rules, for the *Thread* style.                                                                                    |

## Permissions needed

Give the bot these permissions in the source channel **and** in the channel where the translations are sent:

| Permission                  | Used for                                                       |
| --------------------------- | -------------------------------------------------------------- |
| View Channel                | Reading the messages                                           |
| Read Message History        | Reading the message of a flag reaction                         |
| Send Messages               | Sending the translation (bot message)                          |
| Embed Links                 | Sending the translation (bot card)                             |
| Manage Webhooks             | Sending the translation as the author (otherwise a bot message) |
| Manage Messages             | Deleting the original message                                  |
| Add Reactions               | Automatically added flags                                      |
| Create Public Threads       | Creating the thread (thread style)                             |
| Send Messages in Threads    | Writing the translations in the thread (thread style)          |
| Manage Threads              | Reopening a **locked** archived thread (thread style, optional) |

`/check-permissions` lists the permissions that are missing, and the [Translation rules](../website/dashboard/translation-rules.md) page flags the rules that lack one.
