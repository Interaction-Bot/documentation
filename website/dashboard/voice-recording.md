---
description: Turn voice recording on or off on your server, and choose who can start a recording with /record.
---

# Voice recording

Navbar > category _**Audio & AI**_ > _**Voice recording**_.

This page controls the [`/record`](../../commands/record.md) command: it records the audio of a voice channel, with **one track per speaker** and a **mix**. The page does not start recordings: members do, with `/record start`.

## Settings

* **Voice recording enabled**: when it is off, `/record start` is refused on this server with *Recording is disabled on this server.*
* **Who can start a recording**: everyone (default), or only the **chosen roles and members**. Members with the *Manage Server* permission can always start one.
  * **Allowed roles**: the members who have one of these roles can start a recording.
  * **Allowed members**: add a member by their Discord ID. To copy an ID, turn on developer mode in Discord, then right-click the member and choose *Copy ID*.

Click _**Save**_ to apply the changes. _**Cancel**_ restores the last saved settings.

## Everyone is warned

The page shows this rule to the administrator: when someone joins a channel that is being recorded, the bot posts a message in the text channel and announces the recording out loud. The bot does not record itself, and its announcements are never part of the recording.

## Who can see the recordings

Each member sees **only the recordings they started**, at [My recordings](https://interaction-bot.com/recordings) (log in with Discord). The page lists them with their duration, their tracks and their expiry date, and offers the download of each track, of the mix, or of all of them as a ZIP. Recordings are kept **7 days** on a free server and **30 days** on a premium server.

## Limits

Recording time is limited per server and per day: **1 hour** on a free server, **6 hours** on a premium server, from midnight UTC. See [Daily limits](../../audio/limits.md).

{% hint style="info" %}
A recording needs a vote on [top.gg](https://top.gg/bot/893494390142697493/vote) in the last 24 hours from a member of the server, or a premium server. The full rules are in [Recording commands](../../commands/record.md).
{% endhint %}
