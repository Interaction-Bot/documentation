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

The audio commands have their own page with every option: [Audio commands](audio.md).

| Command | Description | Who |
| --- | --- | --- |
| `/connect [channel]` / `/disconnect [channel]` | Move the bot to a voice channel or make it leave. | Everybody |
| `/tts say <query> [language] [voice]` | Read a text aloud in your voice channel. | Everybody |
| `/tts start` / `/tts stop` | Read the messages of this chat aloud / leave and cut the speech. | Everybody |
| `/tts voice [voice]` | Choose the voice that reads your messages. | Everybody |
| `/tts clone create\|list\|delete` | Your cloned voices (Premium). [Details](../audio/voices-and-cloning.md). | Everybody |
| `/tts settings` / `/tts-channel set\|remove\|list\|manage` | TTS settings and the channels read aloud. | Manage Server |
| `/transcribe start [channel] [language] [translate-to] [style]` / `stop` | Transcribe a voice channel. | Everybody |
| `/transcribe live` | Open the [live transcription Activity](../audio/live-transcription.md). | Everybody |
| `/transcribe auto enable\|disable\|manage` | Transcribe automatically when someone joins a voice channel. | Manage Server |
| `/record start\|stop\|test\|list\|note\|transcribe`, `/record auto on\|off\|view` | [Voice recording](../audio/recording.md). | Everybody (auto: Manage Server) |
| `/tempvoice setup\|config\|panel\|interface`, `/voice …`, `/join`, `/find` | [Temporary voice channels](../audio/tempvoice.md). | Setup: Manage Server |
| `/limits`, `/privacy` | [Daily audio limits and privacy](../audio/limits-and-privacy.md). | Everybody |

See [Voice](../audio/voice.md).

## Server management

| Command | Description | Who |
| --- | --- | --- |
| `/ai setup` | Start a conversation with an AI in this channel to configure the bot. [AI setup](../management/ai-setup.md). | Manage Server |
| `/invites [user]` | How many people a member invited. [Invite tracker](../management/invite-tracker.md). | Everybody |
| `/invite-leaderboard` | Who invited the most people. | Everybody |
| Apps > **Transcribe voice message** | Right click a voice message. [Voice messages](../audio/voice-messages.md). | Everybody |

The welcome messages and the honeypot have no command: they are set on the dashboard, see [Welcome and goodbye](../management/welcome-and-goodbye.md) and [Honeypot](../management/honeypot.md).

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
