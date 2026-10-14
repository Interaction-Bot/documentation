---
description: Every command of Interaction Bot on one page.
---

# All commands

`<arg>` is required, `[arg]` is optional. Commands marked **Manage Server** are only visible to members with that permission. Commands marked 👤 can also be used as a [user app](user-app.md): installed on your Discord account, in servers where the bot is not added and in DMs.

## Translation

The configuration commands are described on one page: [Configuration commands](configuration.md).

| Command                                                  | Description                                                              | Who          |
| -------------------------------------------------------- | ------------------------------------------------------------------------ | ------------ |
| `/translate <message> [language]` 👤                      | Translate a text (private answer by default).                                     | Everybody    |
| `/detect <text>` 👤                                      | Tell the language of a text.                                              | Everybody    |
| `/languages` 👤                                          | List the 100 supported languages.                                         | Everybody    |
| Apps > **Translate** / **Detect** 👤                     | Right click a message.                                                    | Everybody    |
| `/channel-translation set\|remove\|list\|manage` | Automatic translation by channel, with the [Thread style](../translation/threads.md). [Details](configuration.md#channel-translation). | Manage Server |
| `/role-translation set\|remove\|list\|manage` | Automatic translation by role. [Details](configuration.md#role-translation). | Manage Server |
| `/category-translation set\|remove\|list\|manage` | Automatic translation by category. [Details](configuration.md#category-translation). | Manage Server |
| `/group create\|delete\|set-channel\|remove-channel\|settings\|list\|manage` | [Translation groups](groups.md).                                  | Manage Server |
| `/flag-translation set\|remove\|list\|manage` | Translation by flag reaction. [Details](configuration.md#flag-translation). | Manage Server |
| `/language-detection set\|reset\|list\|manage` | Minimum number of characters to translate, per channel. | Manage Server |
| `/blacklist add\|remove\|list\|manage` | Roles, channels and languages never translated (Premium). | Manage Server |
| `/flags set <channel> <flags>` / `/flags clear <channel>` | [Flag shortcuts](flags.md).                                              | Manage Server |
| `/check-permissions`                                     | List the permissions the bot lacks in the configured channels.            | Manage Server |

## Voice

| Command                                                          | Description                                                      | Who           |
| ---------------------------------------------------------------- | ---------------------------------------------------------------- | ------------- |
| `/connect [channel]` / `/disconnect [channel]`                   | Move the bot to a voice channel or make it leave.                | Everybody     |
| `/tts <query> [language]` / `/tts-stop`                          | Read a text aloud / stop the speech.                             | Everybody     |
| `/tts-channel set\|remove\|list`                                 | Read the messages of a channel aloud.                            | Manage Server |
| `/transcribe start [channel] [language] [translate_to] [style]` / `stop` | Transcribe a voice channel.                              | Everybody     |
| `/transcribe auto enable\|disable`                               | Transcribe automatically when someone joins a voice channel.     | Manage Server |

See [Voice](../audio/voice.md).

## FAQ

| Command                         | Description                                          | Who           |
| ------------------------------- | ---------------------------------------------------- | ------------- |
| `/ask <question> [group]`       | Ask the FAQ of the server.                           | Everybody     |
| `/faq add\|list\|remove\|manage` | Manage the groups and the entries of the FAQ.        | Manage Server |

See [FAQ and /ask](../qa/faq.md).

## General

| Command          | Description                                                      |
| ---------------- | ---------------------------------------------------------------- |
| `/help [command]` 👤| Help page with all the commands.                                  |
| `/about`         | Information about the bot.                                        |
| `/ping`          | Latency of the bot.                                               |
| `/invite` 👤        | Invitation link of the bot.                                       |
| `/support` 👤       | Link of the support server.                                       |
| `/documentation` | Link of this documentation.                                       |
| `/dashboard` 👤     | Link of the dashboard.                                            |
| `/reminder <enable>` | Be reminded when you can vote again on top.gg.                |
| `/bot-language [language]` | Language of the replies of the bot in the server (Manage Server). See [Configuration commands](configuration.md#language-of-the-bot). |
| `/server-settings [warning]` | Server settings of the dashboard overview (Manage Server). |

## Premium

| Command                       | Description                                  |
| ----------------------------- | -------------------------------------------- |
| `/premium add [guild_id]`     | Enable your premium on a server.             |
| `/premium remove [guild_id]`  | Remove your premium from a server.           |

See [Premium usage](../premium/usage.md).
