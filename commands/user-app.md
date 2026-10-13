---
description: Install Interaction Bot on your Discord account to translate anywhere, even where the bot is not added.
---

# User app

Interaction Bot can be installed **on your own Discord account**, not only on a server. You then get a few commands and the **Apps** menus everywhere you use Discord: in servers **where the bot is not added**, in your direct messages with the bot, and in other direct messages and group chats.

{% hint style="info" %}
Nothing changes for servers that already have the bot: they keep all the features. The user app is an addition for the places where the bot cannot be added.
{% endhint %}

## Install it on your account

* From the **dashboard**: open the [Account page](../website/dashboard/account.md) and click **Add to my account** in the *User app* section.
* From Discord: run `/invite` and click the **Add to my account** button.
* Or use this link: [Add to my account](https://discord.com/oauth2/authorize?client_id=893494390142697493&integration_type=1&scope=applications.commands).

Discord asks you to confirm. The bot does not join any server: it only adds its commands to your account. You can remove it from your account at any time in the Discord settings of your apps.

## What you can use

These commands and menus work everywhere once the app is on your account:

| Command or menu | What it does |
| --- | --- |
| `/translate <message> [language]` | [Translate a text](../translation/commands.md#translate). |
| **Apps > Translate** | Right click (long press on mobile) a message to translate it. |
| `/detect <text>` | [Tell the language of a text](../translation/commands.md#detect). |
| **Apps > Detect** | Right click a message to tell its language. |
| `/languages` | List the supported languages. |
| `/help` | Help page. |
| `/invite` | Invitation links of the bot, with the **Add to my account** button. |
| `/dashboard` | Link of the dashboard. |
| `/support` | Link of the support server. |

Everything that needs the bot **inside the server** is not available as a user app: [translation groups](groups.md), [flag shortcuts](flags.md), [text to speech and speech to text](../audio/voice.md), the [FAQ](../qa/faq.md), `/premium`, `/check-permissions` and the automatic translation of channels, roles and categories. These need the bot to be added to the server by an administrator.

## Your settings

Two personal settings are on the [Account page](../website/dashboard/account.md) of the dashboard. They apply wherever you use the bot as a user app:

* **Default language**: the language used by `/translate` (when you do not choose one) and by **Apps > Translate**. By default, the language of your Discord application is used.
* **Public replies**: by default, the answers of `/translate` and **Apps > Translate** are **private** (only you see them). Turn this on to show them to everyone in the channel.

The answers of `/detect` and **Apps > Detect** are always private.

If the settings cannot be read, the defaults are used (your Discord language, private replies): the commands keep working.

## Premium

In a user app, the bot uses **Premium** when either:

* your Discord account is linked to a [Patreon offer](../premium/subscribe.md) (Premium of the member), or
* you are in a server where the bot is added and that server has [Premium](../premium/premium.md).

On a free account, the bot does not translate the messages of other bots (**Apps > Translate** on a bot message answers that Premium is needed).

## Limits and good to know

* `/translate` can be used once every **5 seconds** per member.
* The bot only sees what you give it: the text of the command, or the message you right click. It does not read the other messages of the channel and never answers on its own.

See also: [Translation commands](../translation/commands.md), [Account page](../website/dashboard/account.md).
