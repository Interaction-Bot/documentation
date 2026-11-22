---
description: Every command of Interaction Bot on one page, in the sections of the /help card.
---

# All commands

This is the complete list of the slash commands of Interaction Bot, grouped in the same five sections as the `/help` card and the dashboard. Type `/help <command>` in Discord to read the details of one command.

`<arg>` is a required option, `[arg]` an optional one. The options are shown with their names as Discord shows them.

* **Vote**: the command needs a recent [top.gg](https://top.gg/bot/893494390142697493/vote) vote (of a member of the server, in the last 24 hours) or a server with [Premium](../premium/premium.md).
* **Premium**: the command, or one of its options, needs a server with [Premium](../premium/premium.md).
* **Manage Server**: only the members with the **Manage Server** permission see and use the command.
* 👤: the command also works as a [user app](user-app.md), on your account, without the bot in the server.

The bot has no configuration command: the settings are made on the [dashboard](../website/dashboard/README.md) or with the [AI setup](../management/ai-setup.md) (`/ai setup`). The commands that say "your channel" work on a temporary voice channel that you own.

## Overview and Premium

### Quick setup

| Command | Description | Who |
| --- | --- | --- |
| `/config` | How to set up the bot: the dashboard or the AI setup | Everybody |
| `/ai setup` | Start a conversation with the AI in this channel to configure the bot | Manage Server |
| `/dashboard` 👤 | Sends the link to the dashboard of the Interaction Bot. | Everybody |

### Premium

| Command | Description | Who |
| --- | --- | --- |
| `/premium add [guild-id]` | Add premium to a guild. | Everybody |
| `/premium remove [guild-id]` | Remove premium from a guild. | Everybody |
| `/limits` | Daily audio limits of this server (transcription, text to speech, recording) | Everybody |
| `/privacy` 👤 | What the bot keeps about you, and your opt-out | Everybody |
| `/reminder <enable>` 👤 | Remind to vote for the bot on top.gg. | Everybody |

## Translation

| Command | Description | Who |
| --- | --- | --- |
| `/translate <message> [language]` 👤 | Translate a message into a given language. | Everybody |
| `/detect <text>` 👤 | Detect the language of a given message. | Everybody |
| `/languages` 👤 | Displays all available languages. | Everybody |
| `/personal-language <language>` 👤 | Sets the language you translate into (Translate menu and /translate) | Everybody |

## Audio and AI

### Transcription

| Command | Description | Who |
| --- | --- | --- |
| `/transcribe live` | Open the live transcription (Activity) of your voice channel. | Vote, Premium |
| `/transcribe start [channel] [language] [translate-to] [style]` | Transcribe a voice channel. | Vote, Premium |
| `/transcribe stop` | Stop the transcription. | Everybody |

### Text to speech

| Command | Description | Who |
| --- | --- | --- |
| `/tts clone create <audio> <name>` | Create a voice from your recording (premium) | Premium |
| `/tts clone delete <voice>` | Delete one of your cloned voices | Everybody |
| `/tts clone list` | Show your cloned voices | Everybody |
| `/tts say <query> [language] [voice]` | Send a message in a voice channel. | Vote |
| `/tts start` | Join your voice channel and read the messages of this chat aloud | Vote |
| `/tts stop` | Leave the voice channel, end the session and cut the speech in progress | Everybody |
| `/tts voice [voice] [reset]` | Choose your voice (all voices are multilingual) | Everybody |
| `/connect [channel]` | Connects the bot to a voice channel. | Vote |
| `/disconnect` | Disconnects the bot from the voice channel. | Everybody |

### FAQ

| Command | Description | Who |
| --- | --- | --- |
| `/ask <question> [group]` | Ask a question: the answer comes from the FAQ of this server | Everybody |

### Voice recording

| Command | Description | Who |
| --- | --- | --- |
| `/record list` | Your recordings on this server, with their links | Everybody |
| `/record note <message>` | Add a timestamped note to the running recording | Everybody |
| `/record start [continuous]` | Record the voice channel you are in | Vote, Premium |
| `/record stop` | Stop the recording of this server | Everybody |
| `/record test` | Checks that a recording will work here, without starting one | Everybody |
| `/record transcribe [recording]` | Transcribe a recording of this server, in the background (free) | Everybody |
| `/record transcribe-cancel` | Cancel your running transcription on this server | Everybody |

### Temp voice

| Command | Description | Who |
| --- | --- | --- |
| `/tempvoice link list` | Lists the voice links of this server and their state | Manage Server |
| `/tempvoice link sync` | Checks again who is in the voice channels and fixes the roles | Manage Server |
| `/tempvoice panel` | Posts the control panel in the chat of your channel | Manage Server |
| `/tempvoice stats [days]` | Statistics of the temporary channels of this server | Manage Server |
| `/voice bitrate <kbps>` | Sets the audio quality in kbps (8 to 384, capped by the boost level) | Everybody |
| `/voice claim` | Takes over a channel whose owner left | Everybody |
| `/voice delete` | Deletes your temporary channel | Everybody |
| `/voice info` | Shows the owner, privacy and lists of your channel | Everybody |
| `/voice invite [message] [channel]` | Posts an invite to your channel in its chat | Everybody |
| `/voice limit <limit>` | Sets the user limit (0 = no limit) | Everybody |
| `/voice name <name>` | Renames your temporary channel | Everybody |
| `/voice password [password]` | Sets a password for /join (empty = remove it) | Everybody |
| `/voice privacy <mode>` | Locks, hides or locks the chat of your channel | Everybody |
| `/voice profile delete <name>` | Deletes one of your saved profiles | Everybody |
| `/voice profile list` | Lists your saved profiles | Everybody |
| `/voice profile load <name>` | Applies one of your saved profiles to your channel | Everybody |
| `/voice profile save <name>` | Saves the settings of your channel under a name | Everybody |
| `/voice purge` | Disconnects everybody except you, trusted members and moderators | Everybody |
| `/voice region <region>` | Sets the voice region of your channel | Everybody |
| `/voice request <channel>` | Asks the owner of a locked or hidden channel to let you in | Everybody |
| `/voice reset` | Back to the defaults: removes trusts, password and waiting room | Everybody |
| `/voice status [text]` | Sets the status shown under your channel (empty = clear) | Everybody |
| `/voice transfer <member>` | Gives your channel to a member in it | Everybody |
| `/voice user block <member> [member2] [member3]` | Keeps a member out of your channel | Everybody |
| `/voice user invite <member>` | Sends a member a DM with an invite to your channel (vote) | Everybody |
| `/voice user kick <member> [member2] [member3]` | Disconnects a member (owner), or starts a vote kick | Everybody |
| `/voice user trust <member> [member2] [member3]` | Lets a member in while the channel is locked or hidden | Everybody |
| `/voice user unblock <member> [member2] [member3]` | Removes the block of a member | Everybody |
| `/voice user untrust <member> [member2] [member3]` | Removes the trust of a member | Everybody |
| `/voice waiting` | Turns the waiting room on or off (the channel stays locked) | Everybody |
| `/find [member] [language]` | Finds the temporary channel where a member is | Everybody |
| `/join <password>` | Gets access to a temporary channel with its password | Everybody |

## Management

### Invitations

| Command | Description | Who |
| --- | --- | --- |
| `/invites [user]` | Shows how many people someone invited | Everybody |
| `/invite-leaderboard [period] [role]` | Shows who invited the most people | Everybody |
| `/invite-info codes [user]` | Lists the invites a member created | Everybody |
| `/invite-info who [user]` | Shows who invited a member and with which invite | Everybody |
| `/invite-admin add <user> <amount> [type] [reason]` | Adds invitations to a member (a correction kept in the list) | Manage Server |
| `/invite-admin delete-code <code>` | Deletes an invite of the server | Manage Server |
| `/invite-admin export <type>` | Sends the leaderboard, the list of arrivals or the journal as a CSV file | Manage Server |
| `/invite-admin list [user] [code] [label] [role]` | Lists the recorded arrivals, with the reason of each verdict | Manage Server |
| `/invite-admin purge [inactive_days] [never_used] [created_by] [channel] [max_uses] [preview]` | Deletes the invites that match the filters (a preview first) | Manage Server |
| `/invite-admin remove <user> <amount> [type] [reason]` | Removes invitations from a member (a correction kept in the list) | Manage Server |
| `/invite-admin reset <scope> [user]` | Starts the counters again (administrators only, with a confirmation) | Manage Server |
| `/invite-admin sync` | Takes the snapshot of the invites again (adds nothing to the counters) | Manage Server |

### Welcome & goodbye

| Command | Description | Who |
| --- | --- | --- |
| `/rules [language]` | Show the rules of the server, in your language | Everybody |

## Help and links

| Command | Description | Who |
| --- | --- | --- |
| `/help [command]` 👤 | Displays a help page with all commands. | Everybody |
| `/about` | Displays information about the bot. | Everybody |
| `/ping` 👤 | Indicates the ping of the bot. | Everybody |
| `/invite` 👤 | Sends the Interaction Bot invite. | Everybody |
| `/support` 👤 | Sends the invite to the support server. | Everybody |
| `/documentation` 👤 | Sends the bot's documentation. | Everybody |
| `/check-permissions` | Check why the bot does not translate: missing permissions in the configured channels | Manage Server |
