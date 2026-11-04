---
description: The Premium commands, their options and their messages.
---

# Usage

Two slash commands manage Premium. They can only be used in a server, not in private messages, and each user can run one of them every 5 seconds.

| Command | Description |
| --- | --- |
| `/premium add [guild-id]` | Adds Premium to a server, with one free slot of your offers. Without `guild-id`, it is the server where you type the command. |
| `/premium remove [guild-id]` | Removes Premium from a server. Without `guild-id`, it is the server where you type the command. |

The optional `guild-id` is the ID of a server where the bot is. You can find the ID of your server on the [Overview](../website/dashboard/overview.md) page of the dashboard.

## /premium add

Before it works, your Discord account must have an active Premium offer: a subscription bought on the website, or a Patreon offer linked to your account (see [Subscribe](subscribe.md)). The command then uses a free slot of that offer.

The bot answers with an embed. The possible messages are:

* **Premium has been added to the server!**: the server is now Premium.
* **This server is already premium.**: the server already has Premium.
* The message says that you are not connected, and links to the Premium page of the website: no active Premium offer is linked to your Discord account. If you have just linked a Patreon account, wait 10 minutes.
* **You don't have enough premium slots to add premium to this guild. Upgrade your offer here.**: all your slots are used. Remove Premium from another server, or upgrade your offer.
* **The guild ID is not valid.**: the `guild-id` is wrong, or the bot is not on this server.

## /premium remove

The command is allowed to the member who linked the Patreon offer that gives this server its Premium, and to the members with the **Administrator** permission of the server whose Premium is removed (the server given by `guild-id`, or the one where the command is typed).

The possible messages are:

* **Premium removed!**: Premium is removed from the server, and its slot is free again.
* **This server is not premium.**: there is nothing to remove.
* **This server's premium comes from a Discord subscription: cancel the subscription on Discord to end it.**: a Premium bought through Discord cannot be removed with this command.
* **You don't have permission to delete the premium on this server.**: you are neither the owner of this Premium nor an administrator.
* **The guild ID is not valid.**: the `guild-id` is wrong, or the bot is not on this server.

## Examples

* Activate Premium on the server where you are: `/premium add`
* Activate Premium on another server, with its ID: `/premium add guild-id:123456789012345678`
* Remove Premium from the server where you are: `/premium remove`

Note: you can also turn Premium on and off with the **Premium** toggle of the [dashboard](../website/dashboard/premium.md).
