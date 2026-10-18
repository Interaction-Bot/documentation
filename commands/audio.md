---
description: Reference of the audio commands - text to speech, transcription, recording, temporary voice channels, limits and privacy.
---

# Audio commands

`<arg>` is required, `[arg]` is optional. The **Needs** column tells what a command needs: **Vote** = a recent [top.gg](https://top.gg/bot/893494390142697493/vote) vote or a premium server (the exact rule is in [Limits and privacy](../audio/limits-and-privacy.md) and [Voice](../audio/voice.md#access)); **Premium\*** = a premium server is needed for the command or for some of its options.

## Text to speech and voice connection

See [Voice (TTS and transcription)](../audio/voice.md) and [Voices and voice cloning](../audio/voices-and-cloning.md).

| Command | Description | Needs |
| --- | --- | --- |
| `/connect [channel]` | Connects the bot to a voice channel. | Vote |
| `/disconnect [channel]` | Disconnects the bot from the voice channel. | — |
| `/tts clone create <audio> <name>` | Create a voice from your recording (premium) | Premium* |
| `/tts clone delete <voice>` | Delete one of your cloned voices | — |
| `/tts clone list` | Show your cloned voices | — |
| `/tts say <query> [language] [voice]` | Send a message in a voice channel. | Vote |
| `/tts settings` | Text to speech settings, with buttons (Manage Server) | — |
| `/tts start` | Join your voice channel and read the messages of this chat aloud | Vote |
| `/tts stop` | Leave the voice channel, end the session and cut the speech in progress | — |
| `/tts voice [voice] [reset]` | Choose the voice that reads your messages | — |
| `/tts-channel list` | List the channels that are read aloud | — |
| `/tts-channel manage` | Manage the channels read aloud with buttons and menus | — |
| `/tts-channel remove <channel>` | Stop reading the messages of this channel | — |
| `/tts-channel set <channel> [language] [translate-to] [voice-channel]` | Read the messages of this channel aloud | Premium* |

## Speech to text

See [Voice](../audio/voice.md#transcription-speech-to-text) and [Live transcription (Activity)](../audio/live-transcription.md).

| Command | Description | Needs |
| --- | --- | --- |
| `/transcribe auto disable` | Disable automatic transcription. | — |
| `/transcribe auto enable [voice-channel] [text-channel] [language] [translate-to] [style]` | Enable automatic transcription. | — |
| `/transcribe auto manage` | Manage the automatic transcription with a panel | — |
| `/transcribe live` | Open the live transcription (Activity) of your voice channel. | Vote, Premium* |
| `/transcribe start [channel] [language] [translate-to] [style]` | Transcribe a voice channel. | Vote, Premium* |
| `/transcribe stop` | Stop the transcription. | — |

## Recording

See [Voice recording](../audio/recording.md). `/record stop` can be used by the member who started the recording, or by a member with *Manage Server* or *Move Members*. `/record auto` needs *Manage Server*.

| Command | Description | Needs |
| --- | --- | --- |
| `/record auto off` | Turn the automatic recording off | — |
| `/record auto on` | Turn the automatic recording on (premium) | — |
| `/record auto view` | Show the automatic recording settings | — |
| `/record list` | Your recordings on this server, with their links | — |
| `/record note <message>` | Add a timestamped note to the running recording | — |
| `/record start [continuous]` | Record the voice channel you are in | Vote, Premium* |
| `/record stop` | Stop the recording of this server | — |
| `/record test` | Checks that a recording will work here, without starting one | — |
| `/record transcribe [recording]` | Transcribe a recording of this server, in the background (free) | — |
| `/record transcribe-cancel` | Cancel your running transcription on this server | — |

## Temporary voice channels

See [Temporary voice channels](../audio/tempvoice.md).

| Command | Description | Needs |
| --- | --- | --- |
| `/find <member>` | Finds the temporary channel where a member is | — |
| `/join <password>` | Gets access to a temporary channel with its password | — |
| `/tempvoice config [vote_kick] [log] [role] [role_action] [name_moderation]` | Vote kick share, moderation log and roles allowed to create (Manage Server) | — |
| `/tempvoice interface [channel]` | Posts the control panel in a text channel (this one by default) | — |
| `/tempvoice panel` | Posts the control panel in the chat of your channel | — |
| `/tempvoice setup` | Creates the creator channel (join it to get your own channel) | — |
| `/voice bitrate <kbps>` | Sets the audio quality in kbps (8 to 384, capped by the boost level) | — |
| `/voice claim` | Takes over a channel whose owner left | — |
| `/voice delete` | Deletes your temporary channel | — |
| `/voice info` | Shows the owner, privacy and lists of your channel | — |
| `/voice invite [message] [channel]` | Posts an invite to your channel in its chat | — |
| `/voice limit <limit>` | Sets the user limit (0 = no limit) | — |
| `/voice name <name>` | Renames your temporary channel | — |
| `/voice password [password]` | Sets a password for /join (empty = remove it) | — |
| `/voice privacy <mode>` | Locks, hides or locks the chat of your channel | — |
| `/voice region <region>` | Sets the voice region of your channel | — |
| `/voice reset` | Back to the defaults: removes trusts, password and waiting room | — |
| `/voice status [text]` | Sets the status shown under your channel (empty = clear) | — |
| `/voice thread` | Turns the chat thread of your channel on or off | — |
| `/voice transfer <member>` | Gives your channel to a member in it | — |
| `/voice user block <member> [member2] [member3]` | Keeps a member out of your channel | — |
| `/voice user invite <member>` | Sends a member a DM with an invite to your channel (vote) | — |
| `/voice user kick <member> [member2] [member3]` | Disconnects a member (owner), or starts a vote kick | — |
| `/voice user trust <member> [member2] [member3]` | Lets a member in while the channel is locked or hidden | — |
| `/voice user unblock <member> [member2] [member3]` | Removes the block of a member | — |
| `/voice user untrust <member> [member2] [member3]` | Removes the trust of a member | — |
| `/voice waiting` | Turns the waiting room on or off (the channel stays locked) | — |

## Limits and privacy

See [Limits and privacy](../audio/limits-and-privacy.md).

| Command | Description | Needs |
| --- | --- | --- |
| `/limits` | Daily audio limits of this server (transcription, text to speech, recording) | — |
| `/privacy` | What the bot keeps about you, and your opt-out | — |
| `/reminder <enable>` | Remind to vote for the bot on top.gg. | — |
