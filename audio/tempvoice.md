---
description: "Temporary voice channels (Join to create): how they work, the commands of the owner, the control panel, vote kick, waiting room, permissions and limits."
---

# Temporary voice channels

Temporary voice channels let each member of a server get **their own voice channel**, which they control, and which is **deleted automatically** when everyone has left.

* Set up on the website: [Temp voice](../website/dashboard/temp-voice.md).
* Permissions the bot needs: [Permissions needed](#permissions-needed).
* Troubleshooting: [Troubleshooting](#troubleshooting).

## How it works

1. An admin creates a **Join to create channel** (a voice channel that makes rooms). It is created on the [Temp voice](../website/dashboard/temp-voice.md) page, with **Add a room** then **Save**.
2. A member joins it. The bot creates a new voice channel for this member, moves the member into it, and makes the member its **owner**.
3. The owner controls the channel: name, user limit, privacy, members, and so on. The owner's commands are the `/voice` commands, the buttons of the control panel, and the context menus of a member.
4. When the **last human leaves**, the channel is deleted. A room left empty while the bot was offline is deleted when the bot starts again.

The name of each new room comes from the **name template** of its Join to create channel (for example *the nickname of the owner* or *a number*). The owner can then rename the room.

The feature is switched on from the dashboard. A server that has no Join to create channel has no room: nothing is made until one exists.

Temporary voice channels are **free**: no vote on [top.gg](https://top.gg/bot/893494390142697493/vote) and no premium server are needed. The only premium option is the **fallback categories** of the dashboard (see [Limits](#limits)).

## Who can do what

| Who | Can do |
| --- | --- |
| Members with **Manage Server** | Everything, in every room, whatever the function rules of the dashboard. |
| Owner of a temporary channel | The `/voice` commands and the control panel, as allowed by the [function rules](../website/dashboard/temp-voice.md#who-can-use-each-function) of the server. |
| Other members of a temporary channel | `/voice user kick` and the vote kick (see [Vote kick](#vote-kick)), `/voice info` and `/voice request` (when the rules allow it), `/voice claim` once the owner has left, `/find`, `/join`. |
| Members without an access role | Cannot create a room, when the server limits who can create one (see [Who can create a room](../website/dashboard/temp-voice.md#who-can-create-a-room)). |

The owner can also be given some server permissions while the owner controls the room, if the server chose it on the dashboard (**Permissions of the owner**). Those permissions are taken back when the ownership changes.

## Set up

1. **Invite the bot with the permissions of the feature.** The list is in [Permissions needed](#permissions-needed).
2. **Create the Join to create channel**, on the [Temp voice](../website/dashboard/temp-voice.md) page:
   * on a server with no room yet, **Add a room** then **Save** creates the category, the channel to join and the control panel;
   * you can also put the Join to create channel in a category of your choice, or add more of them later with **Add a room**.
3. **Try it.** Join the Join to create channel. You are moved to your own room, and the control panel can be posted in its chat (see [Control panel](#control-panel)).

Everything else (names, who can create a room, who can use each function, the log channel, the greeting) is set on the [dashboard](../website/dashboard/temp-voice.md).

## Commands

### `/tempvoice` (Manage Server)

| Command | Description |
| --- | --- |
| `/tempvoice panel` | Owner only: posts the control panel in the chat of your temporary channel. |
| `/tempvoice stats [days]` | Statistics of the temporary channels of the server, for 3 periods. |
| `/tempvoice link list` | Lists the voice links of the server and their state. A voice link gives a role and a text channel to the members who are in a voice channel. |
| `/tempvoice link sync` | Checks again who is in the voice channels, and fixes the roles. |

### `/voice` (the owner of the channel)

Each command of this table can also be run from the buttons of the control panel, unless said otherwise.

| Command | Description |
| --- | --- |
| `/voice name <name>` | Renames the channel (64 characters at most for your text; the channel name has 100 at most, Discord's limit). A rename is accepted once every **5 minutes**. |
| `/voice limit <0-99>` | Sets the user limit. `0` means no limit. |
| `/voice privacy <mode>` | Locks, unlocks, hides, unhides, locks or unlocks the chat of your channel. Lock and hide are independent: both can be on at once. |
| `/voice claim` | Takes over the channel when its owner has left (refused while the owner is still connected). Any member of the channel can run it. |
| `/voice transfer <member>` | Gives the channel to a member who is in it. A bot cannot be an owner. |
| `/voice delete` | Deletes the channel for everyone, after a confirmation button. |
| `/voice info` | Shows the owner, the creation date, whether there is a password, the locks, the chat lock, the waiting room, the limit, and the trusted and blocked members. The answer is posted in the channel. |
| `/voice status [text]` | Sets the status shown under the channel (500 characters at most). Empty clears it. |
| `/voice waiting` | Turns the waiting room on or off. The channel stays locked while it is on. |
| `/voice password [password]` | Sets a password for `/join` (8 characters at most). It needs a locked channel, and it must be unique on the server. Empty removes it. |
| `/voice invite [message] [channel]` | Posts the message and an invite link in a **public** text channel (see [Invitations](#invitations)). |
| `/voice region <region>` | Sets the voice region, or automatic. |
| `/voice bitrate <kbps>` | Sets the audio quality, from **8** to **384** kbps. |
| `/voice request <channel>` | Asks the owner of a locked or hidden channel to let you in. |
| `/voice purge` | Disconnects everybody except you, your trusted members and the moderators. |
| `/voice reset` | Back to the defaults of the Join to create channel: name, limit, privacy, chat, bitrate, region. Removes the trusted, blocked and invited members, the password, the waiting room and the thread. Forgets the saved settings of the owner. |
| `/voice profile save`, `load`, `delete`, `list` | Saves the settings of your channel under a name, and applies them to a later channel. |

### `/voice user` (members of the channel)

| Command | Description |
| --- | --- |
| `/voice user trust <member> [member2] [member3]` | Lets members in while the channel is locked or hidden. Up to 3 members at once. |
| `/voice user untrust <member> [member2] [member3]` | Removes the trust. Up to 3 members at once. |
| `/voice user block <member> [member2] [member3]` | Keeps members out of the channel. A member who is inside is disconnected. Moderators cannot be blocked. Up to 3 members at once. |
| `/voice user unblock <member> [member2] [member3]` | Removes the block. Up to 3 members at once. |
| `/voice user invite <member>` | Sends the member a private message with a one-use invite (see [Invitations](#invitations)). |
| `/voice user kick <member> [member2] [member3]` | The owner disconnects up to **3** members at once. Any other member of the channel starts a [vote kick](#vote-kick) against one member. |

### `/find` and `/join`

| Command | Description |
| --- | --- |
| `/find [member] [language]` | Tells you in which temporary channel a member is, or which channels have a language spoken in them, when you can see and join them. |
| `/join <password>` | Gives you access to the channel of this password, and moves you there when you are connected. Too many wrong tries block it for a while. |

### Context menus (right click on a member)

| Menu | Description |
| --- | --- |
| **Disconnect** | Disconnects the member from your channel (owner). |
| **Transfer Ownership** | Gives your channel to the member (owner). |
| **Send Invite** | Sends the member a private invitation (see [Invitations](#invitations)). |

## Control panel

The panel is a message with buttons, posted in the chat of a room (`/tempvoice panel`, by the owner, or when the room is created if the greeting includes it), or in any text channel of the server, from the dashboard (**Control panel in a channel**). A panel posted in a text channel acts on the temporary channel the member is connected to.

The main buttons are:

| Button | Action |
| --- | --- |
| Name | Renames the channel (a window asks for the name). |
| Limit | Sets the user limit (a window, from 0 to 99). |
| Privacy | A menu: lock, unlock, hide, unhide, lock or unlock the chat. |
| Waiting room | Turns the waiting room on or off. |
| Trust, Untrust | Trusts or untrusts members picked in a list. |
| Block, Unblock | Blocks or unblocks members picked in a list. |
| Invite | Sends a private invitation to a member. |
| Kick | The owner kicks up to 3 members; a member of the channel starts a vote kick. |
| Region | A menu of the voice regions, or automatic. |
| Claim | Takes over the channel when its owner has left. |
| Transfer | Gives the channel to a member who is in it. |
| Delete | Deletes the channel (with confirmation). |

The panel has a **More options** menu for the less used actions: **Status**, **Password**, **Bitrate**, **Public chat invite** (`/voice invite`), **Purge**, **Reset**, **Room info**. The menu also gets **Record** and **Text to speech** when those features are on the server.

Only the owner can use the buttons, except **Kick** (a member can start a vote kick) and **Claim** (any member, once the owner has left). Each function can be given to other roles or members on the dashboard, see [Who can use each function](../website/dashboard/temp-voice.md#who-can-use-each-function).

## Waiting room

A waiting room is a second voice channel attached to a locked channel.

* A member who is **not trusted** and joins a locked channel is moved to the waiting room. The owner receives a message in the waiting room with **Accept** and **Refuse** buttons.
* **Accept**: the member gets access to the channel as an invited member, and is moved in.
* **Refuse**: the member is disconnected. Only the owner can answer. An answer for a member who has already left says that the request has expired. A request expires after **5 minutes**.
* The waiting room cannot be turned on for a **hidden** channel. A waiting room keeps the channel locked: turn it off first to unlock or hide the channel.
* A trusted member is not sent to the waiting room.

## Vote kick

A vote kick removes a member from a channel when enough of the members agree.

* **Who starts it:** any member of the channel, when the **Vote kick** function of the server allows it (see [Who can use each function](../website/dashboard/temp-voice.md#who-can-use-each-function)). The owner also gets it when the owner's instant kick is not allowed. When both are open, the owner chooses between *Kick now* and *Start a vote*.
* **Conditions:** the channel must be **locked**, **hidden** or have a **user limit**. The target must be in the channel, must not be the owner, and must not be a **moderator** (a member with Kick Members, Ban Members or Timeout Members). There must be at least two other members besides the target, and a second vote cannot run in the same channel at once.
* **Votes:** the members of the channel who are not bots and are connected to it vote **Yes** or **No**, for **2 minutes**. The target cannot vote. The starter's vote is a yes.
* **Number of yes votes needed:** the vote share of the server (default **50 %**, set on the dashboard, from 10 % to 100 % by steps of 5) applied to the number of voters, rounded up, and at least one. For example, with 5 eligible voters and a share of 50 %, 3 yes votes are needed. If the starter's yes already reaches that number, the vote is decided at once.
* **Result:** the target is disconnected when the yes votes reach the number needed. The vote fails when the no votes make it impossible to reach that number. If nobody answers in 2 minutes, it expires.
* If the target becomes the owner during the vote (for example by a claim), the vote is cancelled.
* No top.gg vote is asked for a vote kick.

## Invitations

* **`/voice user invite`, Send Invite, and the Invite button:** the member receives a private message with a link that works **once**, for **1 hour**. Using the link gives the member access to the channel as a trusted (invited) member. The message has two buttons: *Stop receiving invitations* and *Receive invitations again*. A member who chose not to receive them gets nothing.
  * A member who is a bot, is blocked, or does not hold an access role of the server cannot be invited. A member who has not accepted the server rules yet cannot be invited either.
  * The owner waits **10 seconds** between two invitations.
  * If the member's private messages are closed, the bot tells the owner.
* **`/voice invite`:** posts a message and a **link that is reused for one hour**, in a **public** text channel. A public channel is one that everyone can see and write in, and where the owner can write too. The channel is the one given in the command, else the **public invitations channel** set on the dashboard, else the current channel. The owner waits **60 seconds** between two public invitations. The message has 250 characters at most, and mentions are never sent.

## Moderation log

When the server has a log channel (set on the [dashboard](../website/dashboard/temp-voice.md#moderation-and-log)), the bot writes a line for each creation, deletion, renaming, change of owner, kick and block, and each vote kick.

## Limits

| Item | Limit |
| --- | --- |
| Name of a channel | 100 characters (Discord's limit), template included. |
| Renames | One rename every **5 minutes** per channel. Other settings are not delayed. |
| User limit | 0 (no limit) to 99. |
| Bitrate | 8 to 384 kbps. |
| Status | 500 characters. |
| Password | 8 characters. A password is unique on the server. |
| Invitation message | 250 characters. |
| Trusted, blocked and invited lists | 25 members each. |
| Kick at once | 3 members (owner). |
| Vote kick | 2 minutes. The share is set from 10 % to 100 % by steps of 5 (default 50 %). |
| Roles that can create a room, or use a function | Up to 10 roles per function. |
| Server | 500 channels (Discord). When the server has 500 channels, nothing is created and the members are told. |
| Category | 50 channels (Discord). When the category is full, the **fallback categories** of the dashboard are used first (**Premium** servers only), else a new category is made, named after the creator's category with a number. |
| Greeting message | 1900 characters. |

## Permissions needed

These are the permissions read from the code. Grant them to the bot role, or to the channels where the feature works.

**Required** (without them the feature cannot run, and the dashboard says so):

| Permission | Used for |
| --- | --- |
| Manage Channels | Creates, renames, edits and deletes the temporary channels. |
| Move Members | Moves the members into their channel, and out of it when they are kicked or blocked. |
| Connect | Gives access to the channels (locks, waiting room). |
| Manage Roles | Sets the permissions of each channel (trusts, blocks, owner). Also gives the temporary voice role. |

**Recommended** (the feature works without them, but a part is lost):

| Permission | Lost without it |
| --- | --- |
| Send Messages | The control panel, the notices, the vote and the waiting room messages. |
| Embed Links | The embed messages. |
| Read Message History | The control panel reads its messages after a restart. |
| Create Invite | `/voice invite`, and the invitations of members. |
| Create Public Threads | The chat thread of a room. |
| Manage Threads | Deletes the thread when the chat thread is turned off or when the channel is deleted. |

The dashboard says when a permission is missing. The bot also needs its own permissions on the **category** and on the **Join to create channel**, where it creates the rooms: if Discord refuses the creation, the member gets a private message with the reason.

## Troubleshooting

| Message or problem | What to do |
| --- | --- |
| *Discord refused to create your temporary channel. Ask a server admin to check the bot's permissions.* | Check the Manage Channels permission of the bot, and the permissions of the category. |
| *No temporary channel can be created for now: Discord limits how many channels can be created. Try again in a few minutes.* | Discord's channel creation limit is reached. Try again in a few minutes. |
| *No temporary channel can be created: the server reached Discord's limit of 500 channels.* | Delete channels that are no longer used. |
| *You cannot create a temporary channel: you need one of the roles this server allows.* | Get one of the roles of [Who can create a room](../website/dashboard/temp-voice.md#who-can-create-a-room), or ask an admin. |
| *Join a temporary channel first.* | The command works only inside a temporary channel. |
| *Only the owner of this channel can do that.* | Ask the owner, or use `/voice claim` if the owner has left. |
| *The owner is still in the channel.* | `/voice claim` works only when the owner has left. |
| *Discord allows two renames per 10 minutes: try again in {seconds} s.* | Wait the number of seconds given, then rename again. |
| *This function is disabled on this server.* | An admin enables it on the dashboard. |
| *This function is reserved to: {roles}.* | Get one of the roles listed, or ask an admin. |
| *This channel has no owner: the server manages it, nobody can change it.* | The rooms are not managed by their owner on this server ("Rooms managed by their owner" is off on the dashboard). Ask an admin. |
| *A waiting room cannot be turned on while the channel is hidden.* | Unhide the channel first. |
| *Lock the channel first: a password only works on a locked channel.* | Lock the channel, then set the password. |
| *No temporary channel has this password.* | Check the password with the owner. Too many wrong tries block `/join` for a while. |
| *A vote kick is already running in this channel.* | Wait for the running vote to end. |
| *A member can be kicked only when the channel is locked, hidden or has a user limit.* | Lock or hide the channel, or set a user limit. |
| *Moderators cannot be kicked.* | Moderators are never kicked, neither by vote nor by the owner. |
| *This channel is not public (everyone must see and write in it), or you cannot write in it.* | Choose a public text channel for the invitation. |
| *Wait {seconds} s before inviting again.* | Wait the number of seconds given. |
| The channel was not deleted when everyone left | Check that the bot has Manage Channels, and look at the log channel. |
| The members of a channel are not moved | Check that the bot has Move Members. |

## Related

* [Temp voice (dashboard)](../website/dashboard/temp-voice.md): every setting of the website.
* [Permissions](../permissions.md): permissions of the bot, by feature.
* [Voice](voice.md): text to speech and speech to text.
