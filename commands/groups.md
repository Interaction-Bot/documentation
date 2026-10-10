---
description: Link several channels, each with its own language.
---

# Translation groups

A **group** links several channels, each with its own language. A message written in one channel is automatically translated into the language of **all the other channels** of the group, one translation per language, and sent there. It is ideal for an international community: everyone writes in their own language, in their own channel.

**Example.** A server has three channels for the same discussions: `#general` (English), `#general-fr` (French) and `#general-es` (Spanish), all in one group called `Community`.

* A member writes `Bonjour à tous, la réunion est reportée à demain.` in `#general-fr`.
* The bot sends an English translation in `#general` and a Spanish translation in `#general-es`.
* Nothing is sent back to `#general-fr`, because it is the channel the message came from.

You can configure groups with commands, or on the [dashboard](../website/dashboard/translation-groups.md). Commands require the *Manage Server* permission.

## Set up a group with commands

Run the commands in this order. Each example shows the reply you should see.

| Step | Command | Expected reply |
| ---- | ------- | -------------- |
| 1 | `/group create name:Community` | ``Group **Community** created. Add channels with `/group set-channel`.`` |
| 2 | `/group set-channel name:Community channel:#general language:English` | `#general is now in group **Community** and receives translations in **English**.` |
| 3 | `/group set-channel name:Community channel:#general-fr language:French` | `#general-fr is now in group **Community** and receives translations in **French**.` |
| 4 | `/group set-channel name:Community channel:#general-es language:Spanish` | `#general-es is now in group **Community** and receives translations in **Spanish**.` |
| 5 | `/group list` | An embed titled *Translation groups* with one field: `🟢 Community (webhook)`, listing the three channels and their languages. |

{% hint style="info" %}
The `language` option accepts a language name (`French`) or an ISO code (`fr`), in any case. Suggestions appear as you type. The `name` option suggests the existing groups of the server.
{% endhint %}

Running `/group set-channel` again with a channel that is already in the group only changes its language. The reply is the same as above.

## Commands

| Command | What it does |
| ------- | ------------ |
| `/group create <name>` | Create a group. The name is 1 to 40 characters, and it must be unique in the server. |
| `/group delete <name>` | Delete a group, with its channels. |
| `/group set-channel <name> <channel> <language>` | Add a channel to a group, or change the language of a channel already in it. |
| `/group remove-channel <name> <channel>` | Remove a channel from a group. The channel itself is not deleted. |
| `/group settings <name> [options]` | Change the settings of the group. Only the options you give are changed. |
| `/group list` | List the groups of the server, with their state (🟢 enabled, ⏸️ paused), style and channels. |

## Settings

Use `/group settings` with the group name and the options you want to change.

| Option | Effect | Example |
| ------ | ------ | ------- |
| `enabled` | `false` pauses the group without deleting it. The configuration is kept. | `/group settings name:Community enabled:false` |
| `style` | How translations are sent: `webhook` (default), `message` or `embed`. | `/group settings name:Community style:embed` |
| `delete_original` | Delete the original message once it has been translated. | `/group settings name:Community delete_original:true` |
| `delete_translation` | Delete the translations after a while. | `/group settings name:Community delete_translation:true` |
| `delete_after` | Seconds before each translation is deleted, from 5 to 86400. Setting it also turns on `delete_translation`. | `/group settings name:Community delete_after:3600` |
| `translate_bots` | Also translate messages sent by bots. Premium option. | `/group settings name:Community translate_bots:true` |
| `always_send` | Send the translations even when they look already translated (see the rules below). | `/group settings name:Community always_send:true` |

Every change gets the same reply: `Group settings updated.`

**Styles**

* `webhook`: the translation looks like the member who wrote the message (same name and avatar). It needs the *Manage Webhooks* permission. Without it, the bot sends a plain message.
* `message`: a plain message from the bot, with the text.
* `embed`: a card from the bot, with the text, the author's name and avatar, and the source and target languages in the footer.

**Errors you may see**

* `/group settings name:Community` with no option returns `Invalid settings.`
* A `delete_after` value outside 5 to 86400 is refused by Discord before the command runs.

## What gets translated

For each message posted in a channel of a group, the bot checks these rules before it translates:

* A message from a **bot** is ignored, unless `translate_bots` is on.
* A message whose language is **not detected reliably**, or that only repeats one character, is ignored, unless `always_send` is on.
* A target channel that already uses the **same language** as the message is skipped, unless `always_send` is on.
* A translation that is **almost identical** to the original text (similarity of 60% or more) is not sent, unless `always_send` is on.
* If the original message is deleted with `delete_original`, it is deleted only when at least one translation was sent.
* A channel deleted from the server is removed from its group automatically.

{% hint style="info" %}
One message can produce only a limited number of translations, all features included: 3 on a free server and 20 on a premium server. Read [Limits that protect your server](../translation/how-it-works.md#limits-that-protect-your-server) for details.
{% endhint %}

## Limits

These are the limits of the [dashboard](../website/dashboard/translation-groups.md).

| Free | Premium |
| ---- | ------- |
| 1 group of up to 3 channels | 5 groups of up to 5 channels |

## Errors and what to do

| Message shown | When it happens | What to do |
| ------------- | --------------- | ---------- |
| `The name must contain between 1 and 40 characters.` | The name is empty or too long. | Choose a shorter name. |
| `You reached the maximum number of groups for this server.` | Creating a group beyond the limit. | Delete a group, or go premium. |
| `A group with this name already exists.` | Two groups with the same name. | Choose another name. |
| `Group not found.` | The name does not match an existing group. | Names are matched exactly. Pick the group from the suggestions. |
| `This channel does not belong to this server.` | The channel is from another server. | Pick a channel of this server. |
| `This group reached its maximum number of channels.` | Adding a channel beyond the limit. | Remove a channel, or go premium. |
| `#channel is not in this group.` | `/group remove-channel` for a channel that is not in the group. | Check the channel with `/group list`. |
| `Invalid settings.` | No option given, or an invalid value. | Give at least one option, with a valid value. |
| ``There is no translation group yet. Create one with `/group create`.`` | `/group list` on a server without groups. | Create a group. |

## Common problems

* **Nothing is translated in a channel.** Check that the group is **enabled** (`/group list` shows 🟢). Then run `/check-permissions`: the bot needs *View Channel* and *Read Message History* in the source channel, and the permissions of its style in the target channels.
* **A message is not translated into one language.** That language is probably the same as the message's language, or the message is too short or uncertain.
* **Translations are plain messages, not webhooks.** The bot lacks *Manage Webhooks*.
* **Translations stop after a few messages.** The per-message limit was reached. See [Limits that protect your server](../translation/how-it-works.md#limits-that-protect-your-server).
* **The translations of a bot are missing.** Bot messages are translated only with `translate_bots` (premium).

{% hint style="info" %}
Groups and [channel translation](../website/dashboard/channel-translation.md) can be used together. A group does not replace the per-channel configuration. For the detailed list of permissions, see [Permissions](../permissions.md).
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
