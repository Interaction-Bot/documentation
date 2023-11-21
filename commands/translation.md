---
description: All commands about the translation
---

# Translation

Interaction bot provides many options to configure the translation. You can see in these pages which commands do what and how to use them.

There are several ways to translate a message:

* Command -> translate your message to given language (see `/translate`)
* Application - Translate -> translate the selected message (target language is based on your discord application language)\
  This translation is ephemeral, this means its only visible for you.\
  ![](<../.gitbook/assets/image (26).png>)
* Automatic -> automatic translation of the send messages (see [Broken link](broken-reference "mention"), [Broken link](broken-reference "mention") and [Broken link](broken-reference "mention"))

General commands for translate text:

| Commands                          | Description                                        |
| --------------------------------- | -------------------------------------------------- |
| `/translate <message> <language>` | Translate the message.                             |
| `/detect <message>`               | Detects the language of a message.                 |
| `/languages`                      | Display all supported language by Interaction Bot. |

Configuration commands of translation:

| Commands                                                                               | Description                                                                                                                                                                                         |
| -------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `/config get <option>`                                                                 | Displays the current translation configuration according to the option.                                                                                                                             |
| `/config detector <char>`                                                              | Sets the minimum number of characters before the message can be automatically translated.                                                                                                           |
| `/config flag_translation <enable> <#channel> <auto_delete> <mode> <apply_everywhere>` | <p>Configure flag translation for a specific channel.</p><p><code>&#x3C;mode></code> <br>    all -> translates on every reaction</p><p>    one -> will only translate if not translated yet<br></p> |

#### Common Parameter

|                              | Possible values                                                                                 | Usage                                                                                                                                                                                                                        |
| ---------------------------- | ----------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `<@role>`                    | Any role on the server. Mention role with @role-name                                            | The role that should automaticaly be translated. See [Broken link](broken-reference "mention") for more information                                                                                                          |
| `<#category>`                | Any category where the Bot has read and write permissions. Mention category with #category-name | The category where every channel underneath should be translated. See [Broken link](broken-reference "mention") for more information                                                                                         |
| `<#source_channel>`          | Any channel where the Bot has read permissions. Mention channel with #channel-name              | The Channel where the bot should translate from                                                                                                                                                                              |
| `<#target_channel>`          | Any channel where the Bot has write permissions. Mention channel with #channel-name             | The Channel where the bot should translate to (can be the same as `<#source_channel>`)                                                                                                                                       |
| `<language>`                 | Any available language. See `/languages`                                                        | The target language the bot should translate to                                                                                                                                                                              |
| `<enable>`                   | true \| false                                                                                   | activate (true) or deactive (false) the translation for the given combination of `<#source_channel>`, `<#target_channel>` and `<language>`                                                                                   |
| `<style>`                    | embed \| webhook \| message                                                                     | <p>Changes the styling of the translated message<br><img src="../.gitbook/assets/image (13).png" alt=""><br><img src="../.gitbook/assets/image (20).png" alt=""><br><img src="../.gitbook/assets/image (29).png" alt=""></p> |
| `<delete_original_message>`  | true \| false                                                                                   | deletes the original message to only keep the translation                                                                                                                                                                    |
| `<delete_translation>`       | true \| false                                                                                   | the translation will automaticaly be deleted after 30 seconds                                                                                                                                                                |
| `<translate_bot>`            | true \| false                                                                                   | allow the bot to translate other bots (**premium only**)                                                                                                                                                                     |
