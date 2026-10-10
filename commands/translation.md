---
description: Reference of the translation commands.
---

# Translation commands

| Command                            | Description                                                                                          |
| ---------------------------------- | ---------------------------------------------------------------------------------------------------- |
| `/translate <message> [language]`  | Translate a text. Without `language`, your Discord language is used. The answer is private.          |
| `/detect <text>`                   | Tell the language of a text.                                                                          |
| `/languages`                       | List the 100 supported languages.                                                                    |
| **Apps > Translate**               | Right click a message: private translation in your Discord language.                                 |
| **Apps > Detect**                  | Right click a message: language of the message.                                                      |
| `/group ...`                       | Translation groups, see [Translation groups](groups.md).                                              |
| `/flags set` / `/flags clear`      | Flag shortcuts under the messages of a channel, see [Flags](flags.md).                                |
| `/check-permissions`               | List the permissions the bot lacks in the configured channels.                                       |

{% hint style="info" %}
Everything about **how translation works** (automatic translation, flags, limits, detection, troubleshooting) is in the [Translation section](../translation/overview.md). Automatic translation by channel, role and category is configured on the [dashboard](../website/dashboard/).
{% endhint %}

{% content-ref url="../translation/overview.md" %}
[overview.md](../translation/overview.md)
{% endcontent-ref %}
