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
| *Delete message* option                   | Source          | Manage Messages                                                         |
| Flag reaction translation                 | Message channel | View Channel, Read Message History, Send Messages (the bot replies)     |
| Flag shortcuts (`/flags`)                 | Channel         | View Channel, Add Reactions, Read Message History                       |
| `/tts`, `/connect`, TTS channels          | Voice channel   | View Channel, Connect, Speak                                            |
| Transcription (`/transcribe`)             | Voice channel   | View Channel, Connect (the bot listens)                                 |
| Transcription output                      | Text channel    | Send Messages, plus Embed Links (embed) or Manage Webhooks (webhook)    |
| FAQ replies (`/ask`, automatic)           | Channel         | View Channel, Read Message History, Send Messages, Embed Links (Send Messages in Threads in a thread) |

If the bot lacks *Manage Webhooks*, it falls back to a plain message.

## Who can use the commands?

| Commands                                                                                                  | Who                                   |
| --------------------------------------------------------------------------------------------------------- | ------------------------------------- |
| `/translate`, `/detect`, `/languages`, Apps > Translate / Detect, `/help`, `/about`, `/ping`, `/invite`, `/support`, `/documentation`, `/dashboard`, `/reminder`, `/ask` | Everybody |
| `/tts`, `/tts-stop`, `/connect`, `/disconnect`, `/transcribe start`, `/transcribe stop`                    | Everybody (voice features need a premium server or a recent [top.gg vote](https://top.gg/bot/893494390142697493/vote)) |
| `/group`, `/faq`, `/flags`, `/tts-channel`, `/transcribe auto`, `/check-permissions`                       | Members with **Manage Server**        |
| `/premium add`, `/premium remove`                                                                          | The member who owns the premium (see [Usage](premium/usage.md)) |
| Dashboard                                                                                                  | Members with **Administrator**        |

Server administrators can change who sees a command in *Server Settings > Integrations > Interaction Bot*.

## Why does the bot need *Message Content*?

To translate a message, the bot has to read it. Discord requires bots to be approved for this ability, and Interaction Bot uses it only to translate, detect the language, answer FAQ questions and apply your configuration. The bot does not need the *Server Members* ability.
