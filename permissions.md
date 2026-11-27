---
description: Every permission the bot needs, per feature, the permissions of the invitation link, and who can use which command.
---

# Permissions

Interaction Bot works with the permissions you give it. This page lists what each feature needs, which permissions the invitation link asks for, and which members can run each command.

{% hint style="info" %}
Run **`/check-permissions`** (members with *Manage Server*) to see exactly which permission is missing in which configured channel. The dashboard also shows the missing permissions of each feature, with a link to ask for them again.
{% endhint %}

## Permissions of the bot

Give them to the bot role, then check the **permission overrides** of the channels: a channel can refuse what the role allows.

| Feature | Channel | Permissions needed |
| --- | --- | --- |
| Automatic translation (source) | Source | View Channel, Read Message History |
| Translation sent as **embed** | Target | View Channel, Send Messages, Embed Links, Attach Files |
| Translation sent as **webhook** | Target | View Channel, Send Messages, **Manage Webhooks**, Attach Files |
| Translation sent as **message** | Target | View Channel, Send Messages, Attach Files |
| Translation sent in a **thread** | Source | View Channel, Read Message History, **Create Public Threads**, **Send Messages in Threads** (plus Manage Webhooks for the webhook look, Manage Threads to reopen a locked thread) |
| *Delete message* option | Source | Manage Messages |
| Flag reaction translation | Message channel | View Channel, Read Message History, Send Messages (the bot replies) |
| Flag shortcuts (dashboard, page Flags) | Channel | View Channel, Add Reactions, Read Message History |
| Text to speech (`/tts`, rules of the dashboard) | Voice channel | View Channel, Connect, Speak, and Read Message History in the text channel read aloud |
| Transcription (`/transcribe`) | Voice channel | View Channel, Connect, Speak (the bot listens) |
| Transcription output | Text channel | Send Messages, plus Embed Links (embed) or Manage Webhooks (webhook) |
| Voice recording (`/record`) | Voice channel | View Channel, Connect (the bot records). See [Recording](audio/recording.md#permissions) |
| Temporary voice channels | Server | See [Permissions needed](audio/tempvoice.md#permissions-needed) |
| Welcome and goodbye messages | Welcome channel | View Channel, Send Messages, Embed Links, and Attach Files for banners; **Manage Roles** to give roles on arrival. See [Welcome and goodbye](management/welcome-and-goodbye.md#permissions-needed) |
| Invite tracker | Server | **Manage Server** (to read the invitations). See [Invite tracker](management/invite-tracker.md#permissions-needed) |
| Honeypot | Trap channel | View Channel, Send Messages, Embed Links, **Pin Messages**, **Manage Messages**, plus Kick, Ban or Timeout Members for the sanction. See [Honeypot](management/honeypot.md#permissions-needed) |
| Reaction roles | Panel channel | Send Messages, Embed Links, **Add Reactions**, Read Message History, **Manage Roles**, Manage Messages (to remove the reaction of a member). See [Reaction roles](management/reaction-roles.md) |
| Event log | Log channels | View Channel, Send Messages, Embed Links. **View Audit Log** (server) to know who did an event. See [Event log](management/event-log.md#permissions) |
| Bot profile | Server | **Change Nickname** for the nickname only. The avatar, the banner and the bio need no permission. See [Bot profile](management/bot-profile.md#permissions) |
| FAQ replies (`/ask`, automatic) | Channel | View Channel, Read Message History, Send Messages, Embed Links (Send Messages in Threads in a thread) |

If the bot lacks *Manage Webhooks*, it falls back to a plain message. If it lacks the thread permissions, the translation is sent as a webhook message in the channel (see [Translation in threads](translation/threads.md#permissions)).

The dashboard lists, for each feature, the permissions it is missing. Each entry comes with a link that asks the server to grant exactly what that feature needs.

## The invitation link

The link of the bot asks for the permissions of its features, so that a new server can use all of them from the first day.

* **New servers** get the base link of the website. It contains the permissions of the features above, plus, among others: **View Audit Log** (who did what), **Manage Nicknames**, **Manage Expressions** (emojis and stickers), **Manage Events** (scheduled events), **Send Voice Messages**, **Set Voice Channel Status** (status of a temporary voice channel), **Mute Members**, **Deafen Members**, **Priority Speaker** and **Use Soundboard** (the rights of the owner of a temporary voice channel).
* **Kick Members, Ban Members, Mention Everyone and Administrator are never in the base link.** The bot asks for them only for the feature that needs them, when you turn that feature on (for example the sanctions *Kick* and *Ban* of the honeypot, or the moderation actions). Without them, those actions say what is missing.
* **Servers that already have the bot** keep the permissions they granted. For a feature that needs more, the dashboard shows a link that asks only for what that feature needs.

{% hint style="info" %}
A feature that lacks one of its permissions says which one in its page of the dashboard. The other features keep working.
{% endhint %}

## Who can use the commands?

The list of the commands is in [All commands](commands/all-commands.md).

| Commands | Who |
| --- | --- |
| `/translate`, `/detect`, `/languages`, `/personal-language`, Apps > Translate / Detect, `/help`, `/config`, `/about`, `/ping`, `/invite`, `/support`, `/documentation`, `/dashboard`, `/reminder`, `/privacy`, `/rules`, `/ask` | Everybody |
| `/tts start`, `/tts say`, `/tts stop`, `/tts voice`, `/connect`, `/disconnect`, `/transcribe start`, `/transcribe stop`, `/transcribe live`, `/record start`, `/record stop` | Everybody. Voice features need a Premium server or a recent [top.gg vote](https://top.gg/bot/893494390142697493/vote) |
| `/tts clone create`, `/tts clone list`, `/tts clone delete` | Everybody with a Premium subscription, aged 18 or over (see [Voices and voice cloning](audio/voices-and-cloning.md)) |
| `/invites`, `/invite-leaderboard`, Apps > **Transcribe voice message** | Everybody |
| `/invite-info who`, `/invite-info codes` | Everybody, or only the members with **Manage Server**, as the server chose on the [Invitations](website/dashboard/invites.md) page |
| `/ai setup` | Members with **Manage Server** (or Administrator) |
| `/check-permissions`, `/invite-admin` (all its subcommands), `/tempvoice` (panel, stats, link list and link sync) | Members with **Manage Server** |
| `/voice …` (its settings) | The owner of a temporary voice channel, for their own channel. `/tempvoice join` and `/find` are for everybody |
| `/premium add` | A member who holds a Premium subscription (see [Usage](premium/usage.md)) |
| `/premium remove` | The member who holds the Premium of the server, or an administrator of that server |
| `/limits` | Everybody (daily audio limits of the server) |
| Dashboard | Members with **Manage Server** or **Administrator** |

Server administrators can change who sees a command in *Server Settings > Integrations > Interaction Bot*.

## Why does the bot need *Message Content*?

To translate a message, the bot has to read it. Discord requires bots to be approved for this ability, and Interaction Bot uses it only to translate, detect the language, answer FAQ questions and apply your configuration. The bot also uses the **Server Members** ability, to greet new members, to follow invitations (the [welcome messages](management/welcome-and-goodbye.md) and the [invite tracker](management/invite-tracker.md)), and to write the arrivals, departures, nicknames and roles of the members in the [event log](management/event-log.md). It uses it only for these features, and does not keep a list of your members.
