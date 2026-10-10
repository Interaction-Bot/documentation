---
description: Link several channels, each with its own language.
---

# Translation groups

A **group** links several channels, each with its own language. A message written in one channel is automatically translated into the language of **all the other channels** of the group (one translation per language) and sent there. It is ideal for an international community: everyone writes in their own language in their own channel.

You can configure groups with commands or on the [dashboard](../website/dashboard/translation-groups.md). Commands require the *Manage Server* permission.

| Command                                         | Description                                                                 |
| ----------------------------------------------- | --------------------------------------------------------------------------- |
| `/group create <name>`                          | Create a group (name of 1 to 40 characters).                                |
| `/group delete <name>`                          | Delete a group.                                                             |
| `/group set-channel <name> <channel> <language>` | Add a channel to a group, or change its language.                          |
| `/group remove-channel <name> <channel>`        | Remove a channel from a group.                                              |
| `/group settings <name> [enabled] [style] [delete_original] [delete_translation] [translate_bots] [always_send] [delete_after]` | Change the settings of the group. |
| `/group list`                                   | List the groups of the server and their channels.                           |

**Settings**: `enabled` (pause a group without deleting it), `style` (webhook, message or embed), `delete_original`, `delete_translation`, `translate_bots` (premium), `always_send`, `delete_after` (duration in seconds, 5 to 86400, after which the translation is deleted).

**Limits** (see the dashboard page): free servers: 1 group of up to 3 channels. Premium: 5 groups of up to 5 channels.

{% hint style="info" %}
A channel can also be paused in the [channel translation](../website/dashboard/channel-translation.md) with the *Enabled* toggle, and each translation can be deleted after a chosen duration.
{% endhint %}
