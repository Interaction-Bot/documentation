---
description: The translation commands and menus - translate a message, detect a language, list the languages and choose your own language.
---

# Translation commands

The automatic translation of the messages of a server (channels, roles, categories, flags) is set up on the [dashboard](../website/dashboard/README.md), not with commands. This page lists the commands and menus that you use yourself. The complete list is on the [All commands](all-commands.md) page.

| Command or menu | What it does | Who sees the answer |
| --- | --- | --- |
| `/translate <message> [language]` 👤 | Translates a message into a language. | Everybody (posted in the channel) |
| **Apps > Translate** 👤 | Right click (long press on mobile) a message to translate it. | You only |
| `/detect <text>` 👤 | Tells the language of a text. | Everybody (posted in the channel) |
| **Apps > Detect** 👤 | Right click a message to tell its language. | You only |
| `/languages` 👤 | Lists the languages that the bot translates into. | Everybody (posted in the channel) |
| `/personal-language <language>` 👤 | Chooses the language of your own translations. | You only |

👤 means that the command also works as a [user app](user-app.md), without the bot in the server.

## /translate

`/translate` translates the text you give into the language you choose. The answer shows the message, with the language it was written in and the language it was translated into.

* `language` is optional. Without it, the bot uses **your language**: the one you chose with `/personal-language` (or on the [Account page](../website/dashboard/account.md)), or else the language of your Discord application.
* The language can be typed by its name or by its code, and the list is offered as you type. The languages are the 100 listed by [`/languages`](#languages).
* A member can use `/translate` once every 5 seconds.

## Apps > Translate

Right click (or long press on a phone) a message, then choose **Apps > Translate**. The translation is sent to you only, in your language (the same choice as `/translate`).

On a free account, this menu does not translate the messages of other bots: [Premium](../premium/premium.md) is needed for that. See [User app](user-app.md#premium).

## /detect and Apps > Detect

`/detect` tells the language of the text you give. **Apps > Detect** does the same for a message you right click, and the answer is only for you.

## /languages

`/languages` lists the 100 languages that the bot can translate into and their codes, with a flag when there is one. Use one of these codes or names with `/translate` and `/personal-language`.

## /personal-language

`/personal-language <language>` chooses the language of your translations: the one used by `/translate` when you do not choose one, and by **Apps > Translate**. The answer is private.

* Give a language name or a code, for example `French` or `fr`.
* Give `none` to go back to the language of your Discord application.
* The same setting is on the [Account page](../website/dashboard/account.md) of the dashboard.

## Automatic translation

The translation of the messages of a server is configured on the dashboard, in the **Translation** section:

* [Translation rules](../website/dashboard/translation-rules.md): the channels, roles and categories that are translated automatically, and into which language;
* [Flags](../website/dashboard/flag-translation.md): translation by a flag reaction, or flags added under the messages of a channel;
* [Exceptions](../website/dashboard/exceptions.md): the channels, roles and languages that are never translated, and the minimum size of a message.

To know how it works, see the [Translation](../translation/overview.md) section.
