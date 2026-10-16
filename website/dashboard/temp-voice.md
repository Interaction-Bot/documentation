---
description: Set up temporary voice channels on your server, and choose the defaults of each creator channel, the welcome message, who can use each function, the vote kick, and the moderation log.
---

# Temp voice

Navbar > category _**Audio & AI**_ > _**Temp voice**_.

Temporary voice channels give each member who joins a **Join to create** channel a voice channel of their own. The owner controls it with buttons and with the `/voice` commands. The full description is in [Temporary voice channels](../../commands/tempvoice.md).

## Turn it on

The feature is **off** until a _Join to create_ channel exists. Click _**Create the Join to create channel**_ and choose the category where the rooms are made (or the top of the server). The feature is then **on**: this is the same as the command `/tempvoice setup`.

* _**Add another Join to create channel**_ makes one more door, with its own settings.
* The _**Temporary voice channels are on**_ switch turns the feature off without deleting its channels.
* Deleting a _Join to create_ channel does **not** delete the rooms already open.

## Join to create channels

Each _Join to create_ channel makes the rooms of the members who join it. Its settings are the **defaults of its rooms**, which the owner can then change. Click _**Save this channel**_ to keep them.

### Name and size

| Setting | What it does |
| --- | --- |
| **Room name** | The name template of the room, 100 characters at most. The placeholders are listed on the page, and the page has five ready-made templates. |
| **Placeholder icons and words** | The icons of the privacy placeholder (locked, unlocked, hidden), the default text of `{CUSTOM}`, the text when the owner has no role, and the words used by `{RANDOM}`. |
| **User limit** | Number of members allowed in the room. `0` means no limit (99 at most). |
| **Minimum and maximum user limit** | The range the owner can choose from. `0` (no limit) only when the minimum is 0. |
| **Bitrate (kbps)** | Between 8 and 384. Empty uses the bitrate of the server. _Highest possible_ uses the highest bitrate the server allows. |
| **Position of the room** | _End of the category_, _Just below the Join to create channel_, or _Top of the category_. Discord can move it a little when many rooms are created at once. |
| **Category of the temporary rooms** | Where the new rooms are created. Empty: the category of the Join to create channel. |
| **Fallback categories** | Used when the category above is full (50 channels). Up to 10 categories. **Premium**. |
| **Privacy by default** | _Public_, _Locked_ or _Hidden_. |
| **Waiting room name** | The name of the waiting room, with the placeholders of the room name, except `{CUSTOM}` and `{PRIVACY}`. Empty: the default text of the bot. |
| **Permissions of the rooms** | Role permissions copied from the Join to create channel, from its category, or none. Connect, View and Send Messages for everyone are never copied. |

### Welcome message

| Setting | What it does |
| --- | --- |
| **Sending** | _Off_, _With notification_ (mentions the owner only), or _Silent_ (default). |
| **Message text** | Up to 1900 characters, with the placeholders of the room name, and `{OWNER_MENTION}`, `{OWNER_ID}`, `{GUILD_ID}` and `{CHANNEL_ID}`. |
| **Include the control panel** | Posts the control panel in the same message. |

### Owner

| Setting | What it does |
| --- | --- |
| **Rooms managed by their owner** | When off, nobody can customise or moderate the rooms: no owner, no panel, no commands. Empty rooms are deleted. |
| **Permissions of the owner** | Discord permissions given to the owner while they control the room, taken back when the ownership changes. *Manage Permissions* and *Manage Roles* need a confirmation. *Move Members* lets the owner move the moderators of the server, so the page warns about it. |
| **Restore the owner's settings** | For the next room of the same owner: name, user limit, trusted and blocked lists, privacy (locked, hidden). Turn off what must start again from the defaults of this channel. |
| **Temporary voice role** | Given while a member is in a room of this creator, then taken back. _Every member in a room_ or _The owner only_. The bot must be above this role. |
| **Age-restricted voice chat** | The rooms are flagged as age-restricted: members must confirm they are adults to read the messages. |

## Who can create a room

Only members with one of the chosen roles can join a _Join to create_ channel. Leave the list empty to let everyone create a room. Members with the *Manage Server* permission can always create one. When some roles are chosen, the rooms of the others are kept **hidden** or **locked**: choose which one under _Members without an access role_.

## Who can use each function

For the owner of a room, choose for each function who can use it:

* **Everyone**;
* **Nobody**;
* **Chosen roles** (up to 10 roles per function).

The functions are: rename, user limit, waiting room, chat, trust and untrust, block and unblock, invite, kick, vote kick, room info, region, bitrate, thread, password, status, claim ownership, transfer ownership, delete, reset settings, public invitations, lock and unlock, hide and unhide, and chat of the room.

Members with the *Manage Server* permission can always use them.

## Vote kick

The **share of votes** needed to kick a member out of a room, from 10 to 100 % by steps of 5 (50 % by default). At least two yes votes are always needed. A vote lasts 2 minutes. The owner kicks instantly; the other members vote. See [Vote kick](../../commands/tempvoice.md#vote-kick).

## Censored words

Words hidden in the names and the statuses of the rooms. A `*` is a wildcard: `word*` covers every word that starts with it, `*word` every word that ends with it, `*word*` every word that contains it. Up to 100 words, 32 characters each, without spaces.

## Log channel

Choose a text channel in which the bot writes what happens: creations and deletions of rooms, renamings, limits, privacy changes, claims and transfers, trusts and blocks, kicks, vote kicks, invitations, and changes of settings of a room. Choose _No log channel_ to stop it.

## Control panel in a channel

_Control panel in a channel_ posts the panel of the rooms in any text channel you choose. Its buttons act on the temporary room the member is in, so one panel is enough for a whole category. You can post it several times. The bot needs *View Channel*, *Send Messages* and *Embed Links* in that channel.

## Public invitations channel

The public text channel where the owner's `/voice invite` posts its message and link, when the command does not name a channel. It must be a public text channel.

{% hint style="info" %}
No top.gg vote is needed for temporary voice channels. The vote kick is a vote of the members of the room itself.
{% endhint %}
