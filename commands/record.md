---
description: Reference of the /record commands: record a voice channel with one track per speaker, encrypted, with a link and a retention period.
---

# Recording commands

`/record` records the audio of a voice channel: **one track per speaker**, aligned in time, plus a **mix** of the channel. The files are encrypted and kept for a limited time. The overview is in [Audio](../audio/overview.md), and the daily time in [Daily limits](../audio/limits.md).

| Command | Description | Who |
| --- | --- | --- |
| `/record start [continuous]` | Records the voice channel you are in. `continuous` keeps the recording going when the channel is empty (**premium**, 24 hours at most). | Members allowed by *Who can start a recording* (everyone by default) |
| `/record stop` | Ends the recording of the server and saves it. | The member who started it, or a member with *Manage Server* or *Move Members* |
| `/record list` | Lists your recordings on this server, with a button to open each one on the website. Only you see the answer. | Everybody |

## Start from the Activity

A recording can also be started from the **live transcription Activity** of your voice channel (see [Voice](../audio/voice.md#live-transcription-activity)), with the **Record the audio** button (*Enregistrer l'audio* in French). It records the same way as `/record start`: same permission, same access rule, same announcements, same link in private messages. On a premium server, the Activity also offers the **continuous** mode.

## Start a recording

* You must be in a **voice channel** (stage channels cannot be recorded), otherwise the bot answers *Join a voice channel first.*
* The bot joins your channel and announces the recording in the text channel of the command. Everyone who joins the channel afterwards is warned too (see below).
* While it records, the bot's nickname on the server is *Recording - Interaction Bot*. The previous nickname is restored at the end.
* Only **one recording per server** can run at a time (*A recording is already running on this server.*).
* A recording and a transcription cannot share the bot's voice connection on a server: while one runs, the other is refused with *The bot is busy on this server*.
* Access: the server is premium, **or** a member of the server has voted on [top.gg](https://top.gg/bot/893494390142697493/vote) in the last 24 hours (*Recording needs a vote on top.gg...*). When the vote is missing, the bot asks for it in the text channel, at most once a day.

## Consent: the members are told

* When a member **joins** the channel during a recording, the bot posts in the text channel: *Welcome {name}, I'm currently recording the audio of this voice channel. This announcement won't be in the recording.* The bot also says it out loud, when text to speech is available on the server.
* These announcements are **not part of the recording**: the bot does not record itself, and the announcement is played outside of the recording.
* Anyone who does not agree should leave the channel. The announcement at the start asks members to stay only if they agree.

## Stop a recording

* `/record stop` ends it. The recording also ends when:
  * **nobody is left** in the channel for **30 seconds**, for a standard recording;
  * the **24 hours** are reached, for a continuous recording;
  * the **daily recording time** of the server is used up. The message says when it starts again;
  * the bot is disconnected, or an error happens.
* A **continuous** recording (premium) keeps running when the channel is empty, so that people can join later. It stops at 24 hours at most.

## Recording files

* One **track per speaker**, and one **mix** of the channel. All the tracks start at the same time, so they can be put side by side.
* The files are **encrypted** on the server. Each recording has its own key.
* When the recording ends, the link is sent **in private messages** to the member who started it. If the member has private messages closed, the answer says that the link is in `/record list`. No public link is ever posted in a channel.
* The link opens the recording on the website. See [Voice recording](../website/dashboard/voice-recording.md) for the page and [Recordings](#recordings-on-the-website) below.

### If the bot restarts

If the bot stops during a recording (crash, restart, update), the recording is **saved with what was recorded up to that moment**. It gets the status *interrupted*, and the starter receives the link as for any other recording. The notice says that the bot restarted during the recording.

## Recordings on the website

* The page **My recordings** (`/recordings`) lists the recordings you started, with their duration, number of tracks, status and expiry date. You must log in with Discord. Other members never see your recordings.
* Each recording page shows its tracks, with a download button per track and for the **mix**, and a **Download all (ZIP)** button.
* A recording is listed with one of these statuses: *In progress*, *Finished*, *Interrupted*, *Failed* or *Expired*. An expired recording has its files deleted.

## Retention

| | Free server | Premium server |
| --- | --- | --- |
| Kept after the end of the recording | **7 days** | **30 days** |

After this time, the files are deleted and the recording shows as *Expired*.

## Daily time

Recording time is limited **per server and per day** (UTC midnight): **1 hour** on a free server, **6 hours** on a premium server. It counts the time actually recorded. The limits are shared with the other audio features, see [Daily limits](../audio/limits.md).

## Server settings

On the dashboard page [Voice recording](../website/dashboard/voice-recording.md) (Manage Server):

* turn recording **on or off** for the server. When off, `/record start` is refused with *Recording is disabled on this server.*;
* choose **who can start a recording**: everyone, or only the chosen roles and members. Administrators can always start one.
