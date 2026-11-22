---
description: Install Interaction Bot on your Discord account to translate anywhere, even where the bot is not added.
---

# User app

Interaction Bot can be installed **on your own Discord account**, not only on a server. You then get a few commands and the **Apps** menus everywhere you use Discord: in servers **where the bot is not added**, in your direct messages with the bot, and in other direct messages and group chats.

{% hint style="info" %}
Nothing changes for servers that already have the bot: they keep all their features. The user app is an addition for the places where the bot cannot be added.
{% endhint %}

## Install it on your account

* From the **dashboard**: open the [Account page](../website/dashboard/account.md) and click **Add to my account** in the *User app* section.
* From Discord: run `/invite` and click the **Add to my account** button.
* Or use this link: [Add to my account](https://discord.com/oauth2/authorize?client_id=893494390142697493&integration_type=1&scope=applications.commands).

Discord asks you to confirm. The bot does not join any server: it only adds its commands to your account. You can remove it from your account at any time in the Discord settings of your apps.

## What you can use

These commands and menus work everywhere once the app is on your account:

| Command or menu | What it does | Who sees the answer |
| --- | --- | --- |
| `/translate <message> [language]` | [Translates a text](translation.md#translate). | Everybody (posted in the channel) |
| **Apps > Translate** | Right click (long press on mobile) a message to translate it. | You only |
| `/detect <text>` | [Tells the language of a text](translation.md#detect-and-apps--detect). | Everybody (posted in the channel) |
| **Apps > Detect** | Right click a message to tell its language. | You only |
| `/languages` | Lists the languages the bot translates into. | Everybody (posted in the channel) |
| `/personal-language <language>` | The language you translate into. | You only |
| `/help` | The help card of the bot. | Everybody |
| `/invite` | The invitation card of the bot, with the **Add to my account** button. | Everybody |
| `/dashboard` | The link to the dashboard. | Everybody |
| `/support` | The invitation to the support server. | Everybody |
| `/documentation` | The link to the documentation. | Everybody |
| `/ping` | The latency of the bot. | Everybody |
| `/reminder <enable>` | Turns on or off the reminder to vote for the bot on top.gg. | Everybody |
| `/privacy` | What the bot keeps about you, and your opt-out. | You only |

Everything that needs the bot **inside a server** is not available as a user app: the automatic translation of channels, roles and categories, the [flag translation](../translation/flags.md), the [voice commands](audio.md) (text to speech, transcription, recording, temporary voice channels), the [FAQ](../qa/faq.md), `/premium`, `/limits`, `/config` and `/check-permissions`. These need the bot to be added to the server by an administrator.

## Your settings

Your **language** is set on the [Account page](../website/dashboard/account.md) of the dashboard, in the *User app* section, or with `/personal-language`. It applies wherever you use the bot as a user app: it is the language used by `/translate` when you do not choose one, and by **Apps > Translate**. By default, the language of your Discord application is used. Use `none` with `/personal-language` to go back to it.

If the settings cannot be read, the default language is used (your Discord language): the commands keep working.

## Premium

The bot translates with **Premium** when either:

* you have an active Premium subscription, bought on the website (Stripe), through Discord, or through Patreon, linked to your Discord account (Premium of the member), or
* you are in a server where the bot is added and that server has [Premium](../premium/premium.md).

On an account without Premium, the bot does not translate the messages of other bots: **Apps > Translate** on a message of a bot answers that Premium is needed.

## Limits and good to know

* `/translate` can be used once every **5 seconds** per member.
* The bot only sees what you give it: the text of the command, or the message you right click. It does not read the other messages of the channel and never answers on its own.

See also: [Translation commands](translation.md), [Account page](../website/dashboard/account.md).
