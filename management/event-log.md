---
description: Event log, the events of your server (edited and deleted messages, members, voice, channels, roles, moderation, invites, threads, emojis, webhooks) written to the channels you choose. Setup, categories, exclusions, permissions and limits.
---

# Event log

The event log writes what happens on your server to the text channels you choose: edited and deleted messages, members who join or leave, voice, channels, roles, moderation actions, invitations, threads, emojis and stickers, webhooks and integrations.

Nothing is stored by the bot: **the channel is the log**. Discord keeps the messages of the log channels, as it keeps any other message.

* Settings on the website: [Event log](../website/dashboard/event-log.md).
* Free for every server. None of its options is Premium.
* Off by default: nothing is written until you turn it on and choose a default log channel.

## Set it up

1. **Give the bot the permissions** it needs in the log channels: **View Channel**, **Send Messages** and **Embed Links**. See [Permissions](#permissions).
2. **Open the dashboard**, section **Management**, page **Event log**.
3. **Choose a default log channel.** Every category that has no channel of its own is written there.
4. **Turn on the categories you need.** Each category has its own switch and, if you want, its own channel.
5. **Turn on the event log** with the switch at the top of the page, then click **Save** in the bar at the bottom.

The page shows the state of the log in one line: *The event log is writing*, or what is missing (no default channel, a channel the bot cannot write in, or a pause).

## What is written

| Category | Events |
| --- | --- |
| **Messages** | Edited and deleted messages, bulk deletions, messages deleted by a moderator. |
| **Members** | Arrivals, departures, nicknames and roles. Needs the **Server Members** intent of the bot: the page says when it is not available. |
| **Voice** | Joining, leaving and moving between voice channels. |
| **Channels** | Creation, deletion and renaming. |
| **Roles** | Creation, deletion and renaming, and what the roles module did. |
| **Server** | Name and icon of the server, and its scheduled events. |
| **Invites** | Creation and deletion of invite links. |
| **Moderation** | Bans, unbans, kicks, timeouts, and the actions of AutoMod. |
| **Threads** | Creation, archiving and deletion of threads. |
| **Emojis and stickers** | Creation, renaming, changes and deletion. |
| **Integrations** | Webhooks, applications added to the server, and integrations. |

Each category has a list of its event types, with a channel of its own for each type if you need one. A type with no channel of its own is written in the channel of its category, then in the default channel.

## Who did it

Some events do not say who did them on Discord. For these, the bot reads the **audit log** of the server:

* kicks, timeouts, deletions by a moderator, AutoMod actions;
* emojis and stickers, webhooks, integrations and scheduled events;
* the changes of members (nickname, roles) when they come from the audit log.

For bans, channels, roles and the server, the event is written even without the author.

Without the **View Audit Log** permission, the page says so: the events that need the author are then written without it.

## Exclusions

Events that are not written, even when their category is on:

* **Ignored channels and categories**: up to 50. Everything inside a category is ignored when the category is.
* **Ignored roles**: up to 50. The events of the members who have one of these roles are not written.
* **Ignored members**: up to 50, by their Discord ID. Their events are not written, whether they are the subject of the event or its author.
* **Ignore bots**: on by default. The events of bots are not written.
* **Recent accounts**: an account younger than a number of days (1 to 90, 7 by default) is marked *recent account* when it joins.

## Limits

* **300 events in 10 minutes per server.** Past that, the next events are skipped, and the bot posts one warning in the log.
* **Several events can share one message**, to keep the channel readable.
* **If the bot cannot write in a log channel** (the channel was deleted, or the bot lacks a permission there), the event log stops for 10 minutes, and the page shows the channel to fix. It tries again by itself after that, or when you click **Check again**.

## Permissions

| Permission | Where | Why |
| --- | --- | --- |
| **View Channel**, **Send Messages**, **Embed Links** | Each log channel | To write the events. |
| **View Audit Log** | Server (the role of the bot) | To know who did an event. |
| **Server Members** intent | The bot | For the arrivals, departures, nicknames and roles of members. |

The events are written only in the channels of the server that owns the settings.

## Privacy

The bot does not keep the events. A message written to a log channel stays there, under the rules of Discord and of the server. The event log of a server is the record of that server: it is still written for members who opted out of message processing, which is stated in the [Privacy Policy](https://interaction-bot.com/privacy).

For what the bot keeps and your rights, read [Security and privacy](../security.md).
