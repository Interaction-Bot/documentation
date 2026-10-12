---
description: Commands and menus to translate or detect a language on demand.
---

# Translation commands

These tools work **everywhere**, without any configuration. The result of `/translate` and **Apps > Translate** is **private** by default (only you see it); you can make it public in the [Account page](../website/dashboard/account.md). They also work in servers where the bot is not added, once the bot is [installed on your account](../commands/user-app.md).

## /translate

`/translate message [language]`

Translates the text you type.

* `message`: the text to translate.
* `language`: the target language. Pick it in the autocomplete list (name or code). If you don't set it, your **default language** from the [Account page](../website/dashboard/account.md) is used, or the language of **your Discord application** when none is set.

<figure><img src="../.gitbook/assets/discord-translate.png" alt="/translate command"><figcaption><p>/translate</p></figcaption></figure>

## Apps menus

Right click (long press on mobile) any message, then **Apps**:

* **Translate**: translates the message into your default language (see above). The result is only visible by you, unless you enabled public replies. Translating the message of another bot needs [Premium](../premium/premium.md).
* **Detect**: tells you in which language the message is written.

<figure><img src="../.gitbook/assets/discord-apps-menu.png" alt="Apps menu"><figcaption><p>Apps > Translate / Detect</p></figcaption></figure>

<figure><img src="../.gitbook/assets/discord-apps-translate.png" alt="Translate result"><figcaption><p>Result of Apps > Translate (private)</p></figcaption></figure>

## /detect

`/detect text`

Tells you the language a text is written in. The answer is private.

## /languages

Lists all the languages supported by the bot (100 languages) with their codes and flags.

## Related

* [Flag reactions](flags.md): translate for everybody with one emoji.
* [Automatic translation](automatic.md): translate by channel, role, category or group.
