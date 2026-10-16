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
| `/tts start` / `/tts stop`                                       | Read the chat aloud during a session / end the session.          | Allowed by the server (everybody by default) |
| `/tts say <query> [language]`                                    | Read one text aloud, once.                                       | Everybody     |
| `/tts voice [voice] [reset]`                                     | Choose the voice that reads your messages.                       | Allowed by the server |
| `/tts settings`                                                  | Settings of the text to speech, with buttons.                    | Manage Server |
| `/tts-channel set\|remove\|list\|manage`                         | Read the messages of a channel aloud.                            | Manage Server |
| `/transcribe start [channel] [language] [translate_to] [style]` / `stop` | Transcribe a voice channel.                              | Everybody     |
| `/transcribe live`                                               | Open the live transcription (Activity) of your voice channel.    | Everybody     |
| `/transcribe record start` / `stop`                              | Record the transcript (text only) of the running transcription.  | Allowed by the server |
| `/transcribe auto enable\|disable\|manage`                       | Transcribe automatically when someone joins a voice channel.     | Manage Server |

See [Voice](../audio/voice.md) and [Text to speech commands](tts.md).

## Recording

| Command                                     | Description                                                              | Who                |
| ------------------------------------------- | ------------------------------------------------------------------------ | ------------------ |
| `/record start [continuous]`                | Record the voice channel you are in, one track per speaker. `continuous` (premium) keeps it going when the channel is empty. | Allowed by the server |
| `/record stop`                              | Stop the recording of the server.                                        | The starter, or Manage Server / Move Members |
| `/record list`                              | Your recordings on this server, with their links.                        | Everybody          |

See [Recording commands](record.md).

## Temporary voice channels

| Command                                     | Description                                                              | Who                |
| ------------------------------------------- | ------------------------------------------------------------------------ | ------------------ |
| `/tempvoice setup`                          | Create the creator channel (category and room) and turn the feature on.  | Manage Server      |
| `/tempvoice config [vote_kick] [log] [role] [role_action]` | Vote kick share (10 to 100 %), moderation log, and roles allowed to create a room. | Manage Server |
| `/tempvoice panel`                          | Post the control panel in the chat of your channel.                      | The owner          |
| `/tempvoice interface [channel]`            | Post the control panel in a text channel (this one by default).          | Manage Server      |
| `/voice name <name>`                        | Rename your channel (64 characters at most).                             | The owner          |
| `/voice limit <limit>` / `/voice bitrate <kbps>` / `/voice region <region>` | User limit, audio quality, voice region.  | The owner          |
| `/voice privacy <mode>`                     | Public, Locked / Unlock, Hide / Unhide, Lock chat / Unlock chat.         | The owner          |
| `/voice status [text]` / `/voice thread`    | Status under the channel / chat thread on or off.                        | The owner          |
| `/voice waiting` / `/voice password [password]` | Waiting room on or off / password for `/join` (locked channels only). | The owner     |
| `/voice invite [message] [channel]`         | Post a public invitation with a link in a public text channel.           | The owner          |
| `/voice info`                               | Owner, privacy, password, chat, waiting room, trusted and blocked members. | Members of the channel |
| `/voice claim` / `/voice transfer <member>` / `/voice delete` | Take over a channel whose owner left / give it to a member / delete it. | Claim: anyone in the channel; others: the owner |
| `/voice reset`                              | Back to the defaults of the creator (removes trusted, blocked, password, waiting room). | The owner |
| `/voice user trust\|untrust\|block\|unblock <member> [member2] [member3]` | Trust, untrust, block or unblock up to 3 members. | The owner |
| `/voice user invite <member>`               | Send a member a private message with an invitation.                      | The owner          |
| `/voice user kick <member> [member2] [member3]` | Disconnect up to 3 members, or start a vote kick (for a non-owner).  | The owner, or any member for a vote |
| `/find <member>` / `/join <password>`       | Find the channel of a member / get into a locked channel with its password. | Everybody        |
| Apps > **Disconnect**, **Transfer Ownership**, **Send Invite** | Right click on a member.                              | The owner          |

See [Temporary voice channels](tempvoice.md) and [Temp voice](../website/dashboard/temp-voice.md).

## Limits

| Command      | Description                                                                 | Who        |
| ------------ | --------------------------------------------------------------------------- | ---------- |
| `/limits`    | Daily time of transcription, text to speech and recording: used, left, reset. | Everybody |

See [Daily limits](../audio/limits.md).

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
