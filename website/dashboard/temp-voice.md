---
description: "Configure the temporary voice channels (Join to create): the creator channels, the rooms, who can use what, votes, log, placeholders and the control panel."
---

# Temp voice

Configure the temporary voice channels of the server: the **Join to create** channels, the rooms they make, and the rules of the rooms. How the feature works for members is explained in [Temporary voice channels](../../audio/tempvoice.md).

Navbar > category _**Audio & AI**_ > _**Temp voice**_.

## Enable and set up

The switch at the top, _**Temporary voice channels are on**_, turns the feature on or off for the whole server. It stays off until a **Join to create channel** exists.

Under _**Set up**_:

* **Category of the Join to create channel**: where the new Join to create channel is created. Default: _No category (top of the server)_.
* _**Create the Join to create channel**_: creates it. You can add several (see _Join to create channels_ below).

The `/tempvoice setup` command does the same thing, and also creates a control panel channel. See [Temporary voice channels](../../audio/tempvoice.md#set-up-in-2-minutes).

{% hint style="info" %}
Turning the feature off stops the creation of new rooms. The rooms already open are not deleted.
{% endhint %}

## Join to create channels

Each Join to create channel has its own card. A member who joins it gets a room, and the settings of the card are the defaults of that room. The owner can then change them with the [commands](../../audio/tempvoice.md#commands) and the [control panel](../../audio/tempvoice.md#control-panel).

Click _**Save this channel**_ to save the card. _**Delete**_ removes the Join to create channel; the rooms already open are not deleted.

### Room settings

| Setting | Default | What it does |
| --- | --- | --- |
| Room name | `{OWNER_NICKNAME}'s Channel` | The name of the new room. Placeholders are listed in [Placeholders](#placeholders). |
| User limit | `0` | Number of members allowed in the room. `0` means no limit (99 at most). |
| Bitrate (kbps) | Server default (empty) | Audio quality, from 8 to 384 kbps. _Highest possible_ uses the highest value the boost level of the server allows. |
| Privacy by default | Public | _Public_, _Locked_ or _Hidden_ when the room is created. |
| Category of the temporary rooms | Same category as the Join to create channel | Where the new rooms are created. |
| Fallback categories (**Premium**) | None | Used when the category above is full (50 channels). Up to 10 categories. |
| Position of the room | End of the category | _End of the category_, _Just below the Join to create channel_ or _Top of the category_. |
| Public invitations channel | No channel | The public text channel where `/voice invite` posts its message and link. It must be a public channel. |
| Minimum user limit | `0` | The lowest limit the owner can choose. |
| Maximum user limit | `99` | The highest limit the owner can choose. `0` (no limit) is allowed only when the minimum is `0`. |
| Waiting room name | Empty (the default text of the bot) | Name of the waiting room. Same placeholders as the room name, except `{CUSTOM}` and `{PRIVACY}`. |
| Permissions of the owner | Manage Channels, Move Members | Permissions given to the owner while they control the room. The bot only gives the ones it has itself. |
| Permissions of the rooms | None | Copies the role permissions of the Join to create channel, of its category, or none. Connect, View and Send Messages for everyone are never copied. |
| Members without an access role | Hidden | Only applies when access roles are set (see below). _Hidden_: they do not see the rooms. _Locked_: they see them but cannot join. |
| Restore the owner's settings | All on | For the next room of the same owner: name, user limit, trusted and blocked lists, privacy. Turn off what must start again from the defaults. |
| Age-restricted voice chat | Off | Marks the rooms as age-restricted. |
| Rooms managed by their owner | On | When off, there is no owner: nobody can customise or moderate the rooms, there is no panel and no command. Empty rooms are deleted. |
| Temporary voice role | None | A role given while a member is in a room of this creator, then taken back. Use a dedicated role: the bot must be above it. |
| Who gets it | Every member in a room | _Every member in a room_ or _The owner only_. |
| Welcome message: sending | Silent | _Off_: no message. _With notification (mentions the owner)_: the owner is notified. _Silent_: no notification. |
| Welcome message: text | Empty | The message posted in the new room, 1900 characters at most. Empty: only the control panel, if it is ticked. |
| Welcome message: include the control panel | On | The control panel is part of the welcome message. |

{% hint style="warning" %}
The owner permissions _Manage Permissions_ and _Manage Roles_ let the owner change the permissions of the module. The page asks for a confirmation before saving them. _Move Members_ also lets the owner move, and so kick from the room, the moderators of the server.
{% endhint %}

### Restore the owner's settings

When an owner creates a new room, the settings the owner had in their previous room come back, depending on the switches of this card: the name, the user limit, the trusted and blocked lists, and the privacy (locked, hidden). The bitrate and the region are not remembered.

## Who can create a room

Under _**Who can create a room**_, choose the roles allowed to join a Join to create channel. Leave it empty to let everyone create a room.

A member without one of these roles gets a private message saying that they need one of the roles the server allows, and no room is created.

## Who can use each function

For the owner of a room, choose **who can use each function**. Each function has one of three rules:

| Rule | Meaning |
| --- | --- |
| Everyone | Default. Any owner can use the function. |
| Nobody | No owner can use the function. |
| Chosen roles | Only the members with one of the chosen roles. Up to 10 roles per function. |

Members with **Manage Server** can always use every function.

| Function | Controls |
| --- | --- |
| Rename | `/voice name`, Name button |
| User limit | `/voice limit`, Limit button |
| Lock and unlock | Locked privacy (`/voice privacy lock`, `unlock`) |
| Hide and unhide | Hidden privacy (`/voice privacy hide`, `unhide`) |
| Waiting room | `/voice waiting`, Waiting room button |
| Chat | Lock chat (`/voice privacy chat`, `unchat`) |
| Chat of the room | The chat of the voice channel for the chosen roles only (see note below) |
| Trust and untrust | `/voice user trust`, `untrust`, Trust and Untrust buttons |
| Block and unblock | `/voice user block`, `unblock`, Block and Unblock buttons |
| Invite | `/voice user invite`, Send Invite menu, Invite button |
| Send an invite to a public chat | `/voice invite` |
| Kick | `/voice user kick` (owner), Kick button |
| Vote kick | Starting a vote kick (`/voice user kick` by a member, Kick button) |
| Room info | `/voice info` |
| Region | `/voice region`, Region button |
| Bitrate | `/voice bitrate` |
| Thread | `/voice thread`, Chat thread button |
| Password | `/voice password` |
| Status | `/voice status` |
| Claim ownership | `/voice claim`, Claim button |
| Transfer ownership | `/voice transfer`, Transfer button and menu |
| Delete | `/voice delete`, Delete button |
| Reset settings | `/voice reset` |

When a member is refused a function, the bot says whether the function is disabled for everyone, or which roles may use it.

{% hint style="info" %}
_Chat of the room_ controls who can write in the chat of the voice channel. With _Nobody_ or chosen roles, @everyone is refused in the chat; with chosen roles, those roles can write. The exact effect of _Nobody_ on the owner is not confirmed (see the open questions of the documentation team).
{% endhint %}

## Vote kick

Under _**Vote kick**_, set the **share of votes** needed to remove a member: **50 %** by default. The share goes from **10 %** to **100 %**, by steps of **5 %**.

The number of yes votes needed is the share of the members who can vote, rounded up (at least one). See [Vote kick](../../audio/tempvoice.md#vote-kick) for the rules.

## Log channel

Under _**Log channel**_, choose the **text channel** where the events of the temporary rooms are written: creations, deletions, renamings, limits, privacy changes, kicks and blocks, votes, changes of owner. Default: _No log channel_.

## Name moderation and censored words

* **Name moderation** (default on): hides insults, links and mass mentions in the names and the statuses of the rooms. Links and mentions are always neutralised, even when it is off.
* **Censored words**: words hidden in the names, the statuses and the invitations of the creator's rooms. Type a word, then press Enter. A word has no spaces and 32 characters at most. A `*` is a wildcard: `word*` covers every word that starts with it, `*word` every word that ends with it, `*word*` every word that contains it. The list keeps 100 words at most. The censored words still apply when name moderation is off.

## Placeholders

The room name, the waiting room name and the welcome message use placeholders written between braces. Click a placeholder to insert it at the cursor.

| Placeholder | Value |
| --- | --- |
| `{OWNER_NAME}` | The name of the owner. |
| `{OWNER_DISPLAY_NAME}` | The display name of the owner. |
| `{OWNER_USERNAME}` | The username of the owner. |
| `{OWNER_NICKNAME}` | The nickname of the owner on this server. |
| `{OWNER_CREATED}` | The date the owner account was created (day/month/year). |
| `{OWNER_JOINED}` | The date the owner joined this server (day/month/year). |
| `{NUMBER}` | The smallest free number: 1, 2, 3... |
| `{NUMBER_ROMAN}` | The number in Roman numerals: I, II, III... |
| `{NUMBER_ALPHA}` | The number in letters: A, B... Z, AA... |
| `{NUMBER_DIGIT}` | The number with three digits: 001, 002... |
| `{NUMBER_EXPONENT}` | The number in superscript: ¹, ², ³... |
| `{RANDOM}` | A random word from the list of _Words for RANDOM_, or a fallback icon. |
| `{PRIVACY}` | The privacy icon: locked, unlocked or hidden. |
| `{CUSTOM}` | The name the owner chose with `/voice name`. |
| `{ACTIVITY}` | The activity of the members, or a fallback. |
| `{ACTIVITY_NAME}` | The name of the activity. |
| `{ROLE_HIGHEST}` | The highest role of the owner. |
| `{ROLE_HOIST}` | The highest role of the owner, shown apart in the member list. |

The welcome message also accepts `{OWNER_MENTION}`, `{OWNER_ID}`, `{GUILD_ID}` and `{CHANNEL_ID}`.

### Name templates

The page offers five templates: _Owner nickname_ (`{OWNER_NICKNAME}'s Channel`), _Privacy and nickname_ (`{PRIVACY} {OWNER_NICKNAME}`), _Numbered_ (`Voice {NUMBER}`), _Roman number and highest role_ (`{NUMBER_ROMAN} - {ROLE_HIGHEST}`) and _Random word_ (`{RANDOM} lounge`).

### Icons and words

Under _**Placeholder icons and words**_:

| Setting | Default |
| --- | --- |
| Privacy icon: locked | 🔒 |
| Privacy icon: unlocked | 🔓 |
| Privacy icon: hidden | 🕶️ |
| Default text of `{CUSTOM}` | Empty (the text of the bot) |
| Text when the owner has no role | Empty (the text of the bot) |
| Words for `{RANDOM}` | Empty (a fallback icon) |

Each icon takes 16 characters at most, and the default text of `{CUSTOM}` 64 characters at most.

## Control panel in a channel

Under _**Control panel in a channel**_, choose a **text channel** and click _**Post the panel**_. The control panel is posted there. Its buttons act on the temporary room the member is connected to. You can post it several times.

The bot needs the View Channel, Send Messages and Embed Links permissions in that channel.

## Limits

* Every setting of this page is free, except **fallback categories** (**Premium**).
* Temporary voice channels need no vote on top.gg.
* Discord limits a server to 500 channels, and a category to 50 channels: a full category is replaced by a new one. The full list of limits is in [Limits](../../audio/tempvoice.md#limits).

## Messages of the page

| Message | Meaning |
| --- | --- |
| _Create a Join to create channel before turning temporary voice channels on._ | The switch needs a Join to create channel. |
| _The bot cannot give this role: it is above its own role._ | Move the bot role above the role, in the server settings. |
| _One of the roles does not exist anymore. Remove it and save again._ | A role was deleted. Remove it from the list. |
| _This category does not exist anymore._ | The category was deleted. Choose another one. |
| _This channel is not a Join to create channel anymore. Reload the page._ | The channel was deleted. Reload the page. |
| _The room name is empty, too long, or uses an unknown placeholder._ | Fix the name, or use only the placeholders of the list above. |
| _The user limit must be a whole number between 0 and 99._ | Enter a valid number. |
| _The bitrate must be between 8 and 384 kbps, or empty._ | Enter a valid value. |
| _The limit range is invalid: the minimum must be at most the maximum, and the default limit must be inside it._ | Fix the minimum, the maximum or the default limit. |
| _The vote share must be a multiple of 5, between 10 and 100._ | Choose a value in the list. |
| _A function can be given to 10 roles at most._ | Remove roles from this function. |
| _Fallback categories are a Premium feature. Remove them to save._ | Remove the fallback categories, or get premium. |
| _The welcome message is too long (1900 characters at most) or uses an unknown placeholder._ | Shorten the message, or fix the placeholder. |
| _The public invitations channel must be a public text channel._ | Choose a public text channel, or _No channel_. |
| _The waiting room name uses an unknown variable or is too long._ | Fix the name. |
| _The bot cannot write in this channel. Give it the View Channel, Send Messages and Embed Links permissions._ | Give the permissions in that channel. |
| _The settings could not be saved._ | Try again. |

{% hint style="info" %}
The page only saves the configuration. The permissions the bot needs are listed in [Permissions needed](../../audio/tempvoice.md#permissions-needed), and the commands of the members are in [Commands](../../audio/tempvoice.md#commands).
{% endhint %}
