---
description: Reference of the temporary voice channels (TempVoice): setup, welcome message, control panel, /voice commands, invitations, waiting room, password, vote kick, log and the dashboard settings.
---

# Temporary voice channels

Temporary voice channels (TempVoice) give each member who joins a **creator channel** a voice channel of their own. The member becomes the **owner** of the new channel, controls it with a **control panel** and with the `/voice` commands, and the channel is deleted when everybody has left. The settings are on the dashboard page [Temp voice](../website/dashboard/temp-voice.md), and the server-wide ones can also be changed with `/tempvoice config`.

No top.gg vote is needed for any temporary voice channel action.

## Set up

| Command | Description | Who |
| --- | --- | --- |
| `/tempvoice setup` | Creates a category **TempVoice** and a creator channel **➕ Create your channel**, and turns the feature on. | Manage Server |
| `/tempvoice config [vote_kick] [log] [role] [role_action]` | Shows, or changes, the vote kick share (10 to 100 %, by steps of 5), the log channel, and the roles allowed to create a channel. `role_action` is *Add*, *Remove* or *Clear*, applied to `role`. | Manage Server |
| `/tempvoice panel` | Posts the control panel in the chat of your temporary channel. | The owner |
| `/tempvoice interface [channel]` | Posts the control panel in a text channel (this one by default). Its buttons act on the temporary channel of the member who presses them, so it can be posted anywhere the bot can write. | Manage Server |

* `/tempvoice setup` checks that the bot has **Connect**, **Manage Channels** and **Move Members**, and says which ones are missing.
* When the server does not let @everyone use *Use Voice Activity*, `/tempvoice setup` adds a warning: members get the push-to-talk pop-up in the voice channels. Give the permission to @everyone if you do not want it.
* You can have several creator channels: use the dashboard to add another one. Each one has its own settings.
* Without a creator channel nothing happens when someone joins. The feature is off until one exists.

## Life of a channel

1. A member joins a creator channel. The bot creates a channel named from the creator's **name template**, and moves the member into it. The member becomes the owner.
2. The owner's settings come back if they were saved before (see *Restore* below).
3. The **welcome message** is posted in the chat of the new channel, if the creator has one (see below).
4. When the channel is **empty**, it is deleted.
5. If the owner leaves while others remain, a member can take over with `/voice claim`. The channel's settings stay as they are.

**Failed creation**: when no channel can be made, the member gets a private message with the reason, at most once a minute:

* the server has a list of roles allowed to create a channel and the member has none of them;
* the server reached Discord's limit of 500 channels;
* Discord limits how many channels can be created: try again in a few minutes;
* Discord refused the channel: a server admin must check the permissions of the bot.

Discord's category limit is handled too: a category holds 50 channels, and when the creator's category is full, the channel goes into a fallback category. **Fallback categories** are a Premium feature (the dashboard lists them); without them, a new category named `X 2`, `X 3`... is made.

## Name templates

The name of a new channel comes from the **name template** of its creator (100 characters at most, once rendered). The default is `{OWNER_NICKNAME}'s Channel`. Placeholders:

| Placeholder | Becomes |
| --- | --- |
| `{OWNER_NAME}`, `{OWNER_USERNAME}` | The name of the owner. |
| `{OWNER_DISPLAY_NAME}`, `{OWNER_NICKNAME}` | The display name, or the nickname on this server. |
| `{OWNER_CREATED}`, `{OWNER_JOINED}` | The day the owner's account was created, or joined the server (day/month/year). |
| `{NUMBER}` | The smallest free number: 1, 2, 3... A deleted channel's number is reused. |
| `{NUMBER_ROMAN}`, `{NUMBER_ALPHA}`, `{NUMBER_DIGIT}`, `{NUMBER_EXPONENT}` | The same number in Roman numerals (I, II, III), letters (A, B... AA), three digits (001), or superscript (¹, ²). |
| `{RANDOM}` | A random word of the server's list, or a fallback icon. |
| `{PRIVACY}` | The privacy icon: locked, unlocked or hidden. Icons can be changed on the dashboard. |
| `{CUSTOM}` | The name the owner chose with `/voice name`, and the server's default text when there is none. |
| `{ACTIVITY}`, `{ACTIVITY_NAME}` | The activity of the members, or its name, or a fallback. |
| `{ROLE_HIGHEST}`, `{ROLE_HOIST}` | The highest role of the owner, or the highest role shown apart in the member list. |

The dashboard offers five **name templates** to start from: owner nickname; privacy and nickname; numbered; Roman number and highest role; random word.

Names are **censored** with the server's list of words (see the dashboard). A word is starred wherever it appears. `*word` covers every word that ends with it, `word*` every word that starts with it, `*word*` every word that contains it.

**Discord limits** are handled: a channel name can be changed only twice every 10 minutes, so renames are spaced by 5 minutes. A server holds 500 temporary channels at most.

## Welcome message

The creator can post a **welcome message** in the chat of each new channel. Its settings are on the dashboard:

* **Sending**: *Off* (nothing is posted), *With notification* (the owner is mentioned and notified, nobody else), or *Silent* (no notification at all). Silent is the default.
* **Message text**: up to 1900 characters, with the placeholders above, plus `{OWNER_MENTION}`, `{OWNER_ID}`, `{GUILD_ID}` and `{CHANNEL_ID}`, which are only filled in the welcome message (not in names).
* **Include the control panel**: the panel is posted in the same message as the text. If the text is empty, only the panel is posted.

## The control panel

The panel has **15 buttons**. Only the owner can press them, and each change applies at once. It shows the owner, the limit, the privacy, the region, the bitrate, the chat, the waiting room, the thread and the password of the channel.

| Button | What it does |
| --- | --- |
| Name | Renames the channel. |
| Limit | Sets the user limit: 0 means no limit, 99 at most. |
| Privacy | Locks, unlocks, hides or unhides the channel, and locks or unlocks the chat. See *Privacy*. |
| Waiting room | Turns the waiting room on or off. |
| Thread | Turns the chat thread on or off. |
| Trust / Untrust | Lets members in while the channel is locked or hidden. |
| Block / Unblock | Keeps members out. |
| Invite | Sends an invitation (see *Invitations*). |
| Kick | Disconnects a member, or starts a vote kick (see *Vote kick*). |
| Region | Sets the voice region. |
| Claim | Takes over a channel whose owner left. |
| Transfer | Gives the channel to a member who is in it. |
| Delete | Deletes the channel, after a confirmation. |

## The `/voice` commands

All of them act on **the channel you are in**. Most need you to be its owner.

| Command | Description |
| --- | --- |
| `/voice name <name>` | Renames the channel (1 to 64 characters, censored). The name is remembered for your next channel. |
| `/voice limit <limit>` | User limit (0 = none). It must stay in the range the server allows. |
| `/voice privacy <mode>` | **Public**, **Locked**, **Unlock**, **Hide**, **Unhide**, **Lock chat** or **Unlock chat**. See *Privacy*. |
| `/voice status [text]` | Status shown under the channel (500 characters at most). Empty clears it. |
| `/voice waiting` | Turns the waiting room on or off. |
| `/voice password [password]` | Sets a password for `/join` (8 characters at most). Empty removes it. |
| `/voice thread` | Turns the chat thread on or off. |
| `/voice invite [message] [channel]` | Posts a public invitation: a message and a link, in a public text channel (see *Invitations*). |
| `/voice region <region>` | Sets the voice region (*Automatic* or one of the 14 Discord regions). |
| `/voice bitrate <kbps>` | Audio quality from 8 to 384 kbps, capped by the boost level of the server. |
| `/voice info` | Shows the owner, the creation date, the privacy, the password, the chat, the waiting room, and the trusted and blocked members. Any member of the channel can use it. |
| `/voice claim` | Takes over a channel whose owner left. |
| `/voice transfer <member>` | Gives the channel to a member in it. A bot cannot be the owner. |
| `/voice delete` | Deletes the channel, after a confirmation. |
| `/voice reset` | Back to the defaults of the creator: name, limit, privacy, chat, bitrate and region. Removes the trusted and blocked members, the invitations, the password, the waiting room and the thread. |
| `/voice user trust <member> [member2] [member3]` | Lets up to 3 members in while the channel is locked or hidden. |
| `/voice user untrust <member> [member2] [member3]` | Removes the trust of up to 3 members. |
| `/voice user block <member> [member2] [member3]` | Keeps up to 3 members out, even when the channel is public. |
| `/voice user unblock <member> [member2] [member3]` | Removes the block of up to 3 members. |
| `/voice user invite <member>` | Sends the member a private message with an invitation (see *Invitations*). |
| `/voice user kick <member> [member2] [member3]` | The owner disconnects up to 3 members at once. Another member starts a vote kick. |

Other commands:

* `/find <member>`: tells in which temporary channel a member is, when you can see it.
* `/join <password>`: gets access to a locked channel that has this password.
* **Apps** (right click on a member): **Disconnect**, **Transfer Ownership**, **Send Invite**.

## Privacy

Privacy has **three separate settings**, which can be combined:

* **Locked**: only the trusted members, and the members allowed by the server, can join. The channel stays visible.
* **Hidden**: the channel is not visible to the others; only the trusted members see it and join it.
* **Chat locked**: the chat of the channel is closed to the others. It is a separate setting from the voice ones.

`/voice privacy` changes one of them at a time (**Lock** and **Unlock**, **Hide** and **Unhide**, **Lock chat** and **Unlock chat**). A channel with a **waiting room** stays locked: it cannot be unlocked or hidden while the waiting room is on, and the waiting room cannot be turned on while the channel is hidden.

## Waiting room

When the waiting room is on, a member who joins the locked channel is moved to a **waiting room** voice channel instead. A request is posted there with an **Accept** and a **Refuse** button. Accepting lets the member in; refusing keeps them out. If the member has left the waiting room, the request expires. The waiting room channel is named with the server's **waiting room name** (the same placeholders as names, except `{CUSTOM}` and `{PRIVACY}`).

## Password

A password works on a **locked** channel only: lock the channel first (`/voice privacy Locked`), then set the password. A member runs `/join <password>` to get in. A password is at most 8 characters, and two channels of the same server cannot have the same password. Passwords are stored as salted hashes, not in clear.

## Invitations

* **Public invitation** (`/voice invite`, panel *Invite*): posts a message and a link in a **public** text channel. The channel is the one given in the command, else the **public invitations channel** of the dashboard, else the channel where you type the command. The message is 250 characters at most. The link lasts one hour and is reused meanwhile. You can send one every 60 seconds.
* **Invitation by private message** (`/voice user invite`, app *Send Invite*): sends the member a private message with a link, valid one hour and for one use. The member can reach the channel even when it is locked or hidden. There is a 10 second wait between two invitations of an owner.
* **Who is skipped**: an invitation is not sent to yourself, to a bot, to a blocked member, to a member who has not accepted the server rules yet, or to a member without one of the server's access roles.
* **Opting out**: the private message has a button to **stop receiving invitations** from TempVoice, and another one to receive them again. Opting out is a choice of the user, on every server.

## Vote kick

A member who is not the owner starts a **vote kick** against a member of the channel (`/voice user kick`, or *Kick* on the panel). The owner does not vote: the owner kicks instantly.

* The vote is posted in the chat where the command was typed. It lasts **2 minutes**. The members connected to the channel vote *Yes* or *No*; the starter votes *Yes*, and the member concerned does not vote.
* The member is disconnected when the number of *Yes* reaches the **share of votes** of the server: the share of the connected members, rounded up, and at least one yes vote. The share is set with `/tempvoice config vote_kick` or on the dashboard: 10 to 100 %, by steps of 5. The default is 50 %.
* A vote is refused when nobody else can vote, when another vote runs in the same channel, or when the target is the owner or a moderator.
* Moderators (members with *Ban Members*, *Kick Members* or *Timeout Members*) can never be kicked this way. The vote ends early when the target becomes the owner.

## Trust, block and lists

* A channel keeps up to **25 trusted** members and **25 blocked** members. The lists are limited per kind, and an entry can only be in one of them.
* A **blocked** member cannot be a moderator. A blocked member is disconnected and kept out, even from a public channel.
* `/voice info` shows the trusted and blocked members of the channel.

## Ownership

* **Claim** (`/voice claim`, button *Claim*): only when the owner has left the channel.
* **Transfer** (`/voice transfer`, app *Transfer Ownership*): to a member who is in the channel, not a bot. The new owner's saved settings come back (see *Restore* below).
* The owner's **permissions** are given while they control the channel and taken back when the ownership changes (see the dashboard, *Permissions of the owner*).

## Restore

When an owner comes back to a creator, the server can restore the settings they had in their previous channel. Each one can be turned on or off on the dashboard:

* **Name**: the name the owner chose with `/voice name`;
* **User limit**;
* **Trusted and blocked lists**;
* **Privacy**: locked, hidden, and chat locked.

When the owner has no saved settings, the defaults of the creator apply. `/voice reset` forgets the saved settings.

## Owner-less mode

A creator can run its rooms **without an owner**: nobody owns the room, nobody can command it, and there is no panel and no welcome message. Empty rooms are deleted. This is set on the dashboard (*Rooms managed by their owner*).

## Voice role

A creator can give a **temporary voice role** to members while they are in one of its rooms, and take it back when they leave. The role can be given to every member of the room, or to the owner only. The bot must be above the role.

## Age restriction

A creator can mark its rooms as **age-restricted**: the channel is flagged as age-restricted by Discord, and members must confirm that they are adults to read its messages. Discord no longer filters this chat for explicit content.

## Access and permissions

* **Who can create a channel**: everyone, or only members with one of the chosen roles (`/tempvoice config role`, or the dashboard). Members with *Manage Server* can always create one. Members without an access role see the rooms **hidden** or **locked**, depending on the setting on the dashboard.
* **Who can use each function**: for the owner of a room, function by function, on the dashboard: everyone, nobody, or chosen roles (up to 10 roles per function). Members with *Manage Server* can always use them.
* **Permissions given to the owner**: Manage Channels and Move Members by default. Other permissions can be added on the dashboard. *Manage Permissions* and *Manage Roles* need an explicit confirmation there.
* **Permissions of the rooms**: a new room can copy the role permissions of the creator channel, of its category, or none of them. Connect, View and Send Messages for everyone are never copied.

## Log

When a log channel is set (`/tempvoice config log` or the dashboard), the bot writes in it: creations, deletions, renamings, limits, privacy changes, claims, transfers, trusts and blocks, kicks, vote kicks, invitations, and changes of the waiting room, thread, password, region, bitrate, status and reset.
