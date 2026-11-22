---
description: The voice commands of Interaction Bot - text to speech, transcription, recording, temporary voice channels, the FAQ command, limits and privacy.
---

# Audio commands

`<arg>` is a required option, `[arg]` an optional one. The **Needs** column tells what a command needs: **Vote** = a recent [top.gg](https://top.gg/bot/893494390142697493/vote) vote, of a member of the server, or a server with [Premium](../premium/premium.md); **Premium** = the command, or one of its options, needs a server with Premium.

The daily limits (text to speech, transcription and recording time) are explained in [Limits and privacy](../audio/limits-and-privacy.md). The settings of the voice features are on the dashboard, in the **Audio & AI** section: [Transcription](../website/dashboard/speech-to-text.md), [Text to speech](../website/dashboard/tts-channels.md), [FAQ](../website/dashboard/faq.md), [Voice recording](../website/dashboard/voice-recording.md) and [Temp voice](../website/dashboard/temp-voice.md).

## Text to speech and voice connection

See [Voice](../audio/voice.md) and [Voices and voice cloning](../audio/voices-and-cloning.md).

| Command | Description | Needs |
| --- | --- | --- |
| `/connect [channel]` | Connects the bot to a voice channel. | Vote |
| `/disconnect` | Disconnects the bot from the voice channel. | — |
| `/tts say <query> [language] [voice]` | Sends a message in your voice channel. The language is detected when you leave it empty. | Vote |
| `/tts start` | Joins your voice channel and reads the messages of this chat aloud. | Vote |
| `/tts stop` | Leaves the voice channel, ends the session and cuts the speech in progress. | — |
| `/tts voice [voice] [reset]` | Chooses your voice, for all your messages. Without a voice, it shows yours. `reset` gives you an automatic voice again. | — |
| `/tts clone create <audio> <name>` | Creates a voice from a recording of your voice. | Premium |
| `/tts clone list` | Shows your cloned voices. | — |
| `/tts clone delete <voice>` | Deletes one of your cloned voices. | — |

The text to speech rules (which channels are read aloud, and with which voice) are set on the dashboard, see [Text to speech](../website/dashboard/tts-channels.md).

Cloning a voice needs a recording of 3 to 30 seconds, and the consent of the owner of the voice, who must be 18 or over. A member can have up to 5 cloned voices. See [Voices and voice cloning](../audio/voices-and-cloning.md).

## Speech to text (transcription)

See [Voice](../audio/voice.md#transcription-speech-to-text) and [Live transcription (Activity)](../audio/live-transcription.md).

| Command | Description | Needs |
| --- | --- | --- |
| `/transcribe start [channel] [language] [translate-to] [style]` | Transcribes a voice channel: what is said is posted in a text channel. `style` is `Webhook` (the default, as the speaker), `Message` or `Embed`. | Vote, Premium |
| `/transcribe live` | Opens the live transcription (the [Activity](../audio/live-transcription.md)) of your voice channel. | Vote, Premium |
| `/transcribe stop` | Stops the transcription. | — |

With a server with Premium, the transcription needs no vote. The options `translate-to` (translation of what is said) and the Activity with live translation are for Premium servers.

## Recording

See [Voice recording](../audio/recording.md).

| Command | Description | Needs |
| --- | --- | --- |
| `/record start [continuous]` | Records the voice channel you are in. `continuous` keeps the recording when the channel is empty (up to 24 hours, Premium). | Vote, Premium |
| `/record stop` | Stops the recording of the server. | — |
| `/record note <message>` | Adds a timestamped note (200 characters at most) to the running recording. | — |
| `/record list` | Lists your recordings on this server, with their links. This answer is private. | — |
| `/record test` | Checks that a recording will work here, without starting one. | — |
| `/record transcribe [recording]` | Transcribes a recording of this server, in the background. Your latest recording is used when you do not choose one. | — |
| `/record transcribe-cancel` | Cancels your running transcription on this server. | — |

A recording is kept for 24 hours, or 7 days on a server with Premium. Transcribing a recording is free: 1 every 30 days without Premium, 1 every 24 hours with Premium.

## Temporary voice channels

See [Temporary voice channels](../audio/tempvoice.md).

| Command | Description | Needs |
| --- | --- | --- |
| `/find [member] [language]` | Finds the temporary channel where a member is. | — |
| `/join <password>` | Gets access to a temporary channel with its password. | — |
| `/tempvoice panel` | Posts the control panel in the chat of your channel. | Manage Server |
| `/tempvoice stats [days]` | Statistics of the temporary channels of the server, for 7, 30 or 90 days. | Manage Server |
| `/tempvoice link list` / `/tempvoice link sync` | Lists the voice links of the server, or checks again who is in the voice channels and fixes the roles. | Manage Server |
| `/voice info` | Shows the owner, the privacy and the lists of your channel. | — |
| `/voice name <name>` | Renames your temporary channel. | — |
| `/voice limit <limit>` | Sets the number of members (0 = no limit). | — |
| `/voice privacy <mode>` | Locks, hides or unlocks your channel, or locks or unlocks its chat. | — |
| `/voice password [password]` | Sets the password of `/join` (empty = removes it). | — |
| `/voice bitrate <kbps>` | Sets the audio quality, from 8 to 384 kbps (capped by the boost level of the server). | — |
| `/voice region <region>` | Sets the voice region of your channel. | — |
| `/voice status [text]` | Sets the status shown under your channel (empty = clears it). | — |
| `/voice invite [message] [channel]` | Posts an invitation to your channel in its chat. | — |
| `/voice request <channel>` | Asks the owner of a locked or hidden channel to let you in. | — |
| `/voice user trust` / `untrust` / `block` / `unblock` `<member>` | Lets a member in while the channel is locked, removes that, keeps a member out, or removes the block. Up to three members at a time. | — |
| `/voice user kick <member>` | Disconnects a member (owner), or starts a vote to kick. | — |
| `/voice user invite <member>` | Sends a member a private message with an invitation to your channel. | — |
| `/voice waiting` | Turns the waiting room on or off (the channel stays locked). | — |
| `/voice purge` | Disconnects everybody except you, the trusted members and the moderators. | — |
| `/voice transfer <member>` | Gives your channel to a member who is in it. | — |
| `/voice claim` | Takes over a channel whose owner left. | — |
| `/voice reset` | Back to the defaults: removes the trusts, the password and the waiting room. | — |
| `/voice delete` | Deletes your temporary channel. | — |
| `/voice profile save` / `load` / `list` / `delete` `<name>` | Saves the settings of your channel under a name, applies them to your channel, or lists and deletes your saved profiles. | — |

The commands that say *your channel* only work in a temporary channel that you own, or that you took over with `/voice claim`.

## FAQ

| Command | Description | Needs |
| --- | --- | --- |
| `/ask <question> [group]` | Asks a question: the answer comes from the FAQ of the server, in the language of the question. `group` chooses the FAQ group (by default, the group of the channel). | — |

The FAQ is written on the dashboard, see [FAQ](../website/dashboard/faq.md) and [FAQ and /ask](../qa/faq.md).

## Limits and privacy

See [Limits and privacy](../audio/limits-and-privacy.md).

| Command | Description | Needs |
| --- | --- | --- |
| `/limits` | Shows the daily audio limits of the server. | — |
| `/privacy` | Shows what the bot keeps about you, and your opt-out. | — |

The vote reminder (`/reminder`) and the other general commands are on the [General](general.md) page.
