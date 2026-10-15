---
description: Set up temporary voice channels on your server, and choose the defaults of the rooms, who can use each function, and the moderation log.
---

# Temp voice

Navbar > category _**Audio & AI**_ > _**Temp voice**_.

Temporary voice channels give each member who joins a **Join to create** channel a voice channel of their own. The owner controls it with buttons and with the `/voice` commands. The full description is in [Temporary voice channels](../../commands/tempvoice.md).

## Turn it on

The feature is **off** until a _Join to create_ channel exists. Click _**Create the Join to create channel**_ and choose the category where the rooms are made (or the top of the server). The feature is then **on**: this is the same as the command `/tempvoice setup`.

* _**Add another Join to create channel**_ makes one more door, with its own settings.
* The _**enabled**_ switch turns the feature off without deleting its channels.
* Deleting a _Join to create_ channel does **not** delete the rooms already open.

## Join to create channels

Each _Join to create_ channel makes the rooms of the members who join it. Its settings are the **defaults of its rooms**, which the owner can then change:

| Setting | What it does |
| --- | --- |
| **Room name** | The name of the room. Placeholders: `{OWNER_NAME}`, `{OWNER_DISPLAY_NAME}`, `{NUMBER}`, `{RANDOM}`, `{PRIVACY}`, `{CUSTOM}`, `{ACTIVITY}`, and others. |
| **User limit** | Number of members allowed in the room. `0` means no limit (99 at most). |
| **Bitrate (kbps)** | Between 8 and 384. Empty uses the bitrate of the server. |
| **Privacy by default** | _Public_, _Locked_ or _Hidden_. |
| **Control panel in the chat** | The owner finds the buttons of the room in its chat. |

Click _**Save this channel**_ to keep the settings of a Join to create channel, or _**Delete**_ to remove it.

## Who can create a room

Only members with one of the chosen roles can join a _Join to create_ channel. Leave the list empty to let everyone create a room. Members with the *Manage Server* permission can always create one.

## Who can use each function

For the owner of a room, choose for each function who can use it:

* **Everyone**;
* **Nobody**;
* **Chosen roles**.

The functions are: rename, user limit, privacy (lock and hide), waiting room, chat, trust and untrust, block and unblock, invite, kick, region, bitrate, thread, password, status, claim ownership, transfer ownership, delete, and reset settings.

Members with the *Manage Server* permission can always use them.

## Vote kick

The **share of votes** needed to kick a member out of a room, from 1 to 100 % (50 % by default). A vote lasts 2 minutes. See [Vote kick](../../commands/tempvoice.md#vote-kick).

## Log channel

Choose a text channel in which the bot writes what happens: creations and deletions of rooms, renamings, limits, privacy changes, claims and transfers, trusts and blocks, kicks, votes, invites, and changes of settings of a room. Choose _No log channel_ to stop it.

{% hint style="info" %}
No top.gg vote is needed for temporary voice channels. The vote kick is a vote of the members of the room itself.
{% endhint %}
