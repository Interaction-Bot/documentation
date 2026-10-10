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

## Example: an English / French / Spanish server

```
/group create name:general
/group set-channel name:general channel:#general-en language:English
/group set-channel name:general channel:#general-fr language:French
/group set-channel name:general channel:#general-es language:Spanish
/group settings name:general style:webhook
```

A message in `#general-fr` is translated **once per target language** and sent to `#general-en` and `#general-es`. Check the result with `/group list`.

## Good to know

* A channel can be in only one position of a group (it cannot be added twice).
* If two channels of a group share the same language, the message is translated once and sent to both.
* A message that is already in the language of the other channels is not translated (unless `always_send`).
* The messages of bots are ignored, except on premium servers with `translate_bots`.
* Pause a group with `enabled:false` to keep its configuration.
* A group counts in the 3 / 20 translations per message limit, together with the other rules ([how it works](../translation/how-it-works.md)).

## Groups or channel translation?

Use **groups** when each channel has its own language and they must stay synchronised. Use [channel translation](../website/dashboard/channel-translation.md) for a one way rule. See [Which method?](../translation/overview.md).

## Troubleshooting

| Symptom                              | What to check |
| ------------------------------------ | ------------- |
| Nothing is translated                | `/group list`: is the group enabled, do the channels have different languages, did you reach the limit (1 group of 3 channels on a free server)? |
| Translations appear as plain text    | The bot cannot create webhooks in the target channel (it falls back to a message). Give *Manage Webhooks*. |
| Can't create or edit a group         | The commands need the *Manage Server* permission. |
