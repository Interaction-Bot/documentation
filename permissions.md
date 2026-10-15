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
| `/tts start`, `/tts say`, `/connect`, TTS channels | Voice channel | View Channel, Connect, Speak                                 |
| Recording (`/record`)                     | Voice channel   | View Channel, Connect (the bot records, stage channels are not recorded) |
| Temporary voice channels (`/tempvoice`)   | Category        | Manage Channels, Move Members, Connect (checked by `/tempvoice setup`)  |
| Transcription (`/transcribe`)             | Voice channel   | View Channel, Connect (the bot listens)                                 |
| Transcription output                      | Text channel    | Send Messages, plus Embed Links (embed) or Manage Webhooks (webhook)    |
| FAQ replies (`/ask`, automatic)           | Channel         | View Channel, Read Message History, Send Messages, Embed Links (Send Messages in Threads in a thread) |

If the bot lacks *Manage Webhooks*, it falls back to a plain message. If it lacks the thread permissions, the translation is sent as a webhook message in the channel (see [Translation in threads](translation/threads.md#permissions)).

## Who can use the commands?

| Commands                                                                                                  | Who                                   |
| --------------------------------------------------------------------------------------------------------- | ------------------------------------- |
| `/translate`, `/detect`, `/languages`, Apps > Translate / Detect, `/help`, `/about`, `/ping`, `/invite`, `/support`, `/documentation`, `/dashboard`, `/reminder`, `/ask` | Everybody |
| `/tts start`, `/tts stop`, `/tts say`, `/tts voice`, `/connect`, `/disconnect`, `/transcribe start`, `/transcribe stop`, `/transcribe live`, `/record start`, `/record stop`, `/record list`, `/limits` | Everybody (voice features need a premium server or a recent [top.gg vote](https://top.gg/bot/893494390142697493/vote)). The server can limit `/tts start`, `/tts stop`, `/tts voice` and `/record start` to chosen roles and members, see [Text to speech settings](website/dashboard/tts-settings.md) and [Voice recording](website/dashboard/voice-recording.md). |
| `/tempvoice panel`, `/voice ...`, `/find`, `/join` | Everybody, with the rights of the channel owner (see [Temporary voice channels](commands/tempvoice.md)) |
| `/group`, `/faq`, `/flags`, `/tts-channel`, `/tts settings`, `/transcribe auto`, `/tempvoice setup`, `/tempvoice config`, `/check-permissions`, `/channel-translation`, `/role-translation`, `/category-translation`, `/flag-translation`, `/language-detection`, `/blacklist`, `/bot-language`, `/server-settings` | Members with **Manage Server** |
| `/premium add`, `/premium remove`                                                                          | The member who owns the premium (see [Usage](premium/usage.md)) |
| Dashboard                                                                                                  | Members with **Administrator**        |

Server administrators can change who sees a command in *Server Settings > Integrations > Interaction Bot*.

## Why does the bot need *Message Content*?

To translate a message, the bot has to read it. Discord requires bots to be approved for this ability, and Interaction Bot uses it only to translate, detect the language, answer FAQ questions and apply your configuration. The bot does not need the *Server Members* ability.
