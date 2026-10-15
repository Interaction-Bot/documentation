---
description: Reference of the temporary voice channels (TempVoice): setup, control panel, /voice commands, vote kick, moderation log and dashboard.
---

# Temporary voice channels

Temporary voice channels (TempVoice) give each member who wants one **a voice channel of their own**. The member who joins the creator channel becomes the **owner** of a new channel, and the channel is deleted when everybody has left. The owner controls it with a **control panel** of buttons and with the `/voice` commands.

Settings: [Temporary voice channels](../website/dashboard/temp-voice.md) on the dashboard, or `/tempvoice config`.

## Set up

| Command | Description | Who |
| --- | --- | --- |
| `/tempvoice setup` | Creates a category **TempVoice** and a creator channel **➕ Create your channel**, and turns the feature on. | Manage Server |
| `/tempvoice config [vote_kick] [log] [role] [role_action]` | Shows, or changes, the vote kick share, the log channel, and the roles allowed to create a channel. `role_action` is *Add*, *Remove* or *Clear*, applied to `role`. | Manage Server |
| `/tempvoice panel` | Posts the control panel in the chat of your channel. | The owner of the channel |

* `/tempvoice setup` checks that the bot has **Manage Channels**, **Move Members** and **Connect**, and says which ones are missing.
* You can have several creator channels: use the dashboard to add another one.
* Without a creator channel, nothing happens when someone joins. The feature is off until one exists.

## Life of a channel

1. A member joins a creator channel. The bot creates a channel named from the **room name** template (for example `{OWNER_NAME}'s channel`) and moves the member into it.
2. The member is the **owner**. The control panel is posted in the chat of the channel, unless the creator channel has the panel turned off.
3. When the channel is **empty**, it is deleted.
4. If the owner leaves while others remain, a member can take over with `/voice claim`.

**Placeholders** in the room name: `{OWNER_NAME}`, `{OWNER_USERNAME}`, `{OWNER_DISPLAY_NAME}`, `{OWNER_NICKNAME}`, `{NUMBER}`, `{NUMBER_ROMAN}`, `{NUMBER_ALPHA}`, `{NUMBER_DIGIT}`, `{RANDOM}`, `{PRIVACY}`, `{CUSTOM}`, `{ACTIVITY}`.

**Discord limits** are handled: a channel name can only be changed twice every 10 minutes, so renames are spaced by 5 minutes; a category holds 50 channels, and a new category is used when the creator's category is full; a server holds 500 temporary channels at most.

## The control panel

The panel has **15 buttons**. Only the owner can use them, and each change applies at once.

| Button | What it does |
| --- | --- |
| Name | Renames the channel (up to 100 characters). |
| Limit | Sets the user limit: 0 means no limit, 99 at most. |
| Privacy | **Public**, **Locked** (nobody new joins), **Hidden** (not visible in the channel list), or **Lock chat** (only the chat is locked). |
| Waiting room | Turns the waiting room on or off. New members wait until the owner lets them in; the channel stays locked. |
| Thread | Turns the chat thread of the channel on or off. |
| Trust / Untrust | Lets a member in while the channel is locked or hidden. Up to 25 trusted and blocked members per channel. |
| Block / Unblock | Keeps a member out of the channel. |
| Invite | Posts an invite to the channel. |
| Kick | Disconnects a member; a non-owner starts a vote kick instead. |
| Region | Sets the voice region (automatic by default). |
| Claim | Takes over a channel whose owner left. |
| Transfer | Gives the channel to a member who is in it. |
| Delete | Deletes the channel. |

The panel shows the owner, the limit, privacy, region, bitrate, chat, waiting room, thread and password of the channel.

## The `/voice` commands

All of them run for **the channel you are in**, and most need you to be its owner.

| Command | Description |
| --- | --- |
| `/voice name <name>` | Renames the channel. |
| `/voice limit <limit>` | User limit (0 = none). |
| `/voice privacy <mode>` | Public, Locked, Hidden or Lock chat. |
| `/voice status [text]` | Status shown under the channel (up to 500 characters). Empty clears it. |
| `/voice waiting` | Turns the waiting room on or off. |
| `/voice password [password]` | Sets a password for `/join` (up to 8 characters). Empty removes it. |
| `/voice thread` | Turns the chat thread on or off. |
| `/voice invite` | Posts an invite to the channel in its chat. |
| `/voice region <region>` | Sets the voice region. |
| `/voice bitrate <kbps>` | Audio quality from 8 to 384 kbps, capped by the boost level of the server. |
| `/voice info` | Shows the owner, the privacy and the lists of the channel. |
| `/voice claim` | Takes over a channel whose owner left. |
| `/voice transfer <member>` | Gives the channel to a member in it. |
| `/voice delete` | Deletes the channel. |
| `/voice reset` | Back to the defaults: removes the trusted and blocked members, the password and the waiting room. |
| `/voice user trust` / `untrust <member>` | Lets a member in, or removes that right. |
| `/voice user block` / `unblock <member>` | Keeps a member out, or removes the block. |
| `/voice user invite <member>` | Sends the member a private message with an invite (vote). |
| `/voice user kick <member> [member2] [member3]` | The owner disconnects up to 3 members at once. A non-owner starts a vote kick. |

Other commands:

* `/find <member>`: finds the temporary channel where a member is.
* `/join <password>`: gets access to a channel that has a password.
* **Apps** (right click on a member): **Disconnect**, **Transfer Ownership**, **Send Invite**.

## Vote kick

A member who is not the owner can start a **vote kick** against a member of the channel (`/voice user kick`, or *Kick* on the panel).

* The vote lasts **2 minutes**. Members connected to the channel vote *Yes* or *No*, and the starter votes *Yes*.
* The member is disconnected when the **share of votes** set by the server is reached. The default is **50 %** of the members of the channel. This share is set with `/tempvoice config vote_kick` or on the dashboard (1 to 100 %).
* Only one vote runs at a time in a channel. Moderators (members with *Ban Members*, *Kick Members* or *Timeout Members*) can never be kicked this way.

## Access and permissions

* **Who can create a channel**: everyone, or only members with one of the chosen roles (`/tempvoice config role`, or the dashboard). Members with *Manage Server* can always create one.
* **Who can use each function**: for the owner of a channel, function by function, on the dashboard: everyone, nobody, or the chosen roles. Members with *Manage Server* can always use them.
* **No top.gg vote is needed** for any temporary voice channel action. The only vote on this page is the **vote kick**, which is a vote of the members of the channel itself (see [Vote kick](#vote-kick)).

## Log

When a log channel is set (`/tempvoice config log` or the dashboard), the bot writes in it: creations, deletions, renamings, limits, privacy changes, claims, transfers, trusts and blocks, kicks, vote kicks, invites, and changes of the waiting room, thread, password, region, bitrate, status and reset.
