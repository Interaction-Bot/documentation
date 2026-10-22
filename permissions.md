---
description: Every permission the bot needs, per feature, and who can use which command.
---

# Permissions

Interaction Bot works with the permissions you give it. This page lists what each feature needs, and which members can run each command.

{% hint style="info" %}
Run **`/check-permissions`** (members with *Manage Server*) to see exactly which permission is missing in which configured channel.
{% endhint %}

## Permissions of the bot

Give them to the bot role, then check the **permission overrides** of the channels: a channel can refuse what the role allows.

| Feature                                   | Channel         | Permissions needed                                                      |
| ----------------------------------------- | --------------- | ----------------------------------------------------------------------- |
| Automatic translation (source)            | Source          | View Channel, Read Message History                                      |
| Translation sent as **embed**             | Target          | View Channel, Send Messages, Embed Links, Attach Files                  |
| Translation sent as **webhook**           | Target          | View Channel, Send Messages, **Manage Webhooks**, Attach Files          |
| Translation sent as **message**           | Target          | View Channel, Send Messages, Attach Files                               |
| Translation sent in a **thread**          | Source          | View Channel, Read Message History, **Create Public Threads**, **Send Messages in Threads** (plus Manage Webhooks for the webhook look, Manage Threads to reopen a locked thread) |
| *Delete message* option                   | Source          | Manage Messages                                                         |
| Flag reaction translation                 | Message channel | View Channel, Read Message History, Send Messages (the bot replies)     |
| Flag shortcuts (`/flags`)                 | Channel         | View Channel, Add Reactions, Read Message History                       |
| `/tts`, `/connect`, TTS channels          | Voice channel   | View Channel, Connect, Speak                                            |
| Transcription (`/transcribe`)             | Voice channel   | View Channel, Connect (the bot listens)                                 |
| Transcription output                      | Text channel    | Send Messages, plus Embed Links (embed) or Manage Webhooks (webhook)    |
| Voice recording (`/record`)               | Voice channel   | View Channel, Connect (the bot records), see [Recording](audio/recording.md#permissions) |
| Temporary voice channels                  | Server          | See [Permissions needed](audio/tempvoice.md#permissions-needed)         |
| Welcome and goodbye messages              | Welcome channel | View Channel, Send Messages, Embed Links, and Attach Files for banners; **Manage Roles** to give roles on arrival. See [Permissions](management/welcome-and-goodbye.md#permissions-needed) |
| Invite tracker                            | Server          | **Manage Server** (to read the invitations). See [Invite tracker](management/invite-tracker.md#permissions-needed) |
| Honeypot                                  | Trap channel    | View Channel, Send Messages, Embed Links, **Pin Messages**, **Manage Messages**, plus Kick, Ban or Timeout Members for the sanction. See [Honeypot](management/honeypot.md#permissions-needed) |
| FAQ replies (`/ask`, automatic)           | Channel         | View Channel, Read Message History, Send Messages, Embed Links (Send Messages in Threads in a thread) |

If the bot lacks *Manage Webhooks*, it falls back to a plain message. If it lacks the thread permissions, the translation is sent as a webhook message in the channel (see [Translation in threads](translation/threads.md#permissions)).

## Who can use the commands?

| Commands                                                                                                  | Who                                   |
| --------------------------------------------------------------------------------------------------------- | ------------------------------------- |
| `/translate`, `/detect`, `/languages`, Apps > Translate / Detect, `/help`, `/about`, `/ping`, `/invite`, `/support`, `/documentation`, `/dashboard`, `/reminder`, `/ask` | Everybody |
| `/tts`, `/tts-stop`, `/connect`, `/disconnect`, `/transcribe start`, `/transcribe stop`                    | Everybody (voice features need a premium server or a recent [top.gg vote](https://top.gg/bot/893494390142697493/vote)) |
| `/invites`, `/invite-leaderboard`, Apps > **Transcribe voice message** | Everybody |
| `/ai setup`, `/tempvoice setup`, `/tempvoice config` | Members with **Manage Server** |
| `/group`, `/faq`, `/flags`, `/tts-channel`, `/transcribe auto`, `/check-permissions`, `/channel-translation`, `/role-translation`, `/category-translation`, `/flag-translation`, `/language-detection`, `/blacklist`, `/bot-language`, `/server-settings` | Members with **Manage Server** |
| `/premium add`, `/premium remove`                                                                          | The member who owns the premium (see [Usage](premium/usage.md)) |
| Dashboard                                                                                                  | Members with **Administrator**        |

Server administrators can change who sees a command in *Server Settings > Integrations > Interaction Bot*.

## Why does the bot need *Message Content*?

To translate a message, the bot has to read it. Discord requires bots to be approved for this ability, and Interaction Bot uses it only to translate, detect the language, answer FAQ questions and apply your configuration. The bot also uses the **Server Members** ability, to greet new members and to follow invitations (the [welcome messages](management/welcome-and-goodbye.md) and the [invite tracker](management/invite-tracker.md)). It uses it only for these features, and does not keep a list of your members.
