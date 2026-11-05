---
description: Translate a message by adding a flag reaction.
---

# Flag translation

The simplest way to translate: **add a flag emoji** under a message. The bot replies to the message with the translation in the language of the flag. Nothing to configure: it works on every channel by default.

<figure><img src="../.gitbook/assets/discord-flag-reaction.png" alt="Flag reaction"><figcaption><p>1. Add a flag emoji below a message</p></figcaption></figure>

<figure><img src="../.gitbook/assets/discord-flag-translation.png" alt="Translation by the bot"><figcaption><p>2. The bot answers with the translation</p></figcaption></figure>

## Which flags?

Around 175 flags are supported. Several flags can give the same language: for example 🇬🇧, 🇺🇸 and 🇨🇦 all give English. Examples: 🇫🇷 French, 🇪🇸 Spanish, 🇩🇪 German, 🇯🇵 Japanese... Some fun ones:

* 🏴‍☠️ the **pirate flag** translates the message into English, then into "pirate speak".
* the Hebrew 🇮🇱, Bengali 🇧🇩, Tswana 🇧🇼, Welsh 🏴 and Scottish 🏴 flags are supported.

Messages written by bots are translated only on a [premium](../premium/premium.md) server.

## Configure it per channel

On the dashboard, [Flag translation](../website/dashboard/flag-translation.md) (the **Flags** page, section **React with a flag**) lets you change the behavior of a channel:

| Option           | What it does                                                                                                                                                  |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Members can translate by reacting with a flag here**    | Turn the flag translation off for this channel.                                                                                                               |
| **How often is it translated?** | *Each time someone reacts*: every new flag reaction triggers a translation. *Once per message*: the message is translated once, further flags are ignored.                          |
| **Delete the translation automatically**  | The translation is deleted after a delay (reading time, 25 seconds minimum). If off, it stays forever. By default it is deleted automatically.              |
| **Style of the translation** | How the translation is sent: *Embed* (default), *Webhook*, *Message*, *Thread* (in a thread under the message) or *Private message* (sent to the member who added the flag). |

## Flag shortcuts

**Flag shortcuts** make the translation one click away: the bot itself **adds 1 to 5 flags** under every message of a channel, and members only click one.

* With a command: `/flags set #general 🇬🇧 🇫🇷 🇪🇸`, and `/flags clear #general` to stop.
* On the dashboard: [Flag shortcuts](../website/dashboard/flag-shortcuts.md), in the **Flags** page, section **Automatically added flags**.

The bot needs the *Add Reactions* permission in the channel.

## Flags or commands?

| Flag reaction                          | `/translate` or Apps > Translate                  |
| -------------------------------------- | ------------------------------------------------- |
| Visible by everybody in the channel    | `/translate`: everybody sees it. Apps > Translate: only you see it (ephemeral)               |
| Language chosen by the flag            | Language chosen with the command / your Discord language |
| Deleted automatically after a while    | Apps > Translate: disappears when you close it. `/translate`: stays in the channel                      |
