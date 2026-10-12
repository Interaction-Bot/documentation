---
description: Reference of the translation commands.
---

# Translation commands

| Command                            | Description                                                                                          |
| ---------------------------------- | ---------------------------------------------------------------------------------------------------- |
| `/translate <message> [language]`  | Translate a text. Without `language`, your default language ([Account page](../website/dashboard/account.md)) or your Discord language is used. The answer is private unless you enabled public replies. Works as a [user app](user-app.md).          |
| `/detect <text>`                   | Tell the language of a text.                                                                          |
| `/languages`                       | List the 100 supported languages.                                                                    |
| **Apps > Translate**               | Right click a message: private translation in your default or Discord language. Works as a [user app](user-app.md).                                 |
| **Apps > Detect**                  | Right click a message: language of the message.                                                      |
| `/group ...`                       | Translation groups, see [Translation groups](groups.md).                                              |
| `/flags set` / `/flags clear`      | Flag shortcuts under the messages of a channel, see [Flags](flags.md).                                |
| `/check-permissions`               | List the permissions the bot lacks in the configured channels.                                       |

{% hint style="info" %}
`/translate`, `/detect`, `/languages`, `/help`, `/invite`, `/dashboard`, `/support` and the **Translate** / **Detect** menus can be used without adding the bot to the server: see [User app](user-app.md).
{% endhint %}

{% hint style="info" %}
Everything about **how translation works** (automatic translation, flags, limits, detection, troubleshooting) is in the [Translation section](../translation/overview.md). Automatic translation by channel, role and category is configured on the [dashboard](../website/dashboard/).
{% endhint %}

{% content-ref url="../translation/overview.md" %}
[overview.md](../translation/overview.md)
{% endcontent-ref %}
