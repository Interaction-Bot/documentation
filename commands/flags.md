---
description: Flag shortcuts and permission check.
---

# Flags and diagnostics

This page covers two commands: `/flags`, which adds flag reactions under every message of a channel, and `/check-permissions`, which tells you why the bot does not translate.

## Flag shortcuts

A **flag shortcut** makes translation one click away. The bot adds 1 to 5 flag reactions under every new message of a channel, and a member clicks a flag to get the message translated into that language.

| Command | Who | What it does |
| ------- | --- | ------------ |
| `/flags set channel:<channel> flags:<flags>` | *Manage Server* | Set the flags of a channel. It replaces the previous list. |
| `/flags clear channel:<channel>` | *Manage Server* | Stop adding flags in the channel. |

### /flags set

Example: `/flags set channel:#general flags:🇬🇧 🇫🇷 🇪🇸`

The bot replies:

```
✅ 🇬🇧 🇫🇷 🇪🇸 will be added under the messages of #general. Click a flag to translate the message.
```

From then on, each new message in `#general` gets the three flags. A member who clicks 🇫🇷 gets the message translated into French.

**How the flags are read**

* You can type the flag emojis, or their names such as `:flag_fr:`.
* Only the flags the bot can translate are kept. Other text is ignored. Duplicates are removed.
* Only the **first 5** valid flags are used. The others are ignored.
* The order you type is the order in which the bot adds the reactions.

Examples:

| You type | The bot keeps | Reply |
| -------- | ------------- | ----- |
| `🇬🇧 🇬🇧 🇯🇵 🇩🇪 🇮🇹 🇨🇳 🇷🇺` | 🇬🇧 🇯🇵 🇩🇪 🇮🇹 🇨🇳 (the duplicate 🇬🇧 is removed, and 🇷🇺 is dropped because only 5 are kept) | `✅ 🇬🇧 🇯🇵 🇩🇪 🇮🇹 🇨🇳 will be added under the messages of #general. …` |
| `🏴‍☠️` (the pirate flag) | nothing: this flag is not available as a shortcut | `⛔ I found no valid flag. Give up to 5 flag emojis, for example 🇬🇧 🇫🇷 🇪🇸.` |
| `:flag_fr: :flag_de:` | 🇫🇷 🇩🇪 | `✅ 🇫🇷 🇩🇪 will be added …` |

{% hint style="info" %}
The pirate flag 🏴‍☠️ works on a message as a [flag translation](../translation/flags.md) (English, then pirate speak), but it cannot be used as a shortcut.
{% endhint %}

**Permissions the bot needs in the channel**: *View Channel*, *Add Reactions* and *Read Message History*. If one is missing, the command replies `⛔ You do not have permission to execute this command.`. This text is the same for every command. It means the bot lacks a permission in that channel: give it the permission, then run the command again.

### /flags clear

Example: `/flags clear channel:#general`

The reply is `✅ No more flags under the messages of #general.` It also works when the channel had no flags.

### How the shortcuts behave

* Only **new** messages get the flags. Older messages are not changed.
* Messages written by **bots** get no flags, and neither do messages with no text, embed or attachment.
* The bot adds the flags one after the other. If Discord refuses one (missing permission, or the message was deleted), the bot stops for that message.
* A click on a flag is a normal [flag translation](../translation/flags.md). It follows the settings of the channel on the dashboard: if [Flag translation](../website/dashboard/flag-translation.md) is off in that channel, a click does nothing.
* The reactions added by the bot itself do not trigger a translation.

### Flags the bot supports

The list has 175 flags, one per language or country, such as 🇫🇷 French, 🇬🇧 English, 🇪🇸 Spanish, 🇩🇪 German and 🇯🇵 Japanese. Some regional flags are supported too:

* 🇮🇱 Hebrew, 🇧🇩 Bengali and 🇧🇼 Tswana (Botswana). Note that 🇹🇳 (Tunisia) is Arabic.
* 🏴 Welsh and 🏴 Scottish, which are sub-national flags.

The full list is on the [Languages and flags](../translation/languages.md) page.

## Diagnostics: /check-permissions

`/check-permissions` checks **every channel where a translation is configured**, and lists the permissions the bot lacks there. It is the first command to run when the bot does not translate.

Example: an admin runs `/check-permissions` on a server where a group sends translations as webhooks, but the bot lacks *Manage Webhooks* in the target channel `french`. The embed has one field, titled with the channel name, with this content:

```
group “Community” (webhook)
⚠️ Manage Webhooks
```

The embed title is **Missing permissions**, and its footer says: `1 problem(s). Give these permissions to the bot role (or the channel) and try again.`

**Who**: members with *Manage Server*. The command can be run once every 15 seconds per server.

**Replies**

| Reply | Meaning |
| ----- | ------- |
| `No translation is configured on this server yet. Use the dashboard to add one.` | There is nothing to check. |
| `✅ The bot has all the permissions it needs in the 3 configured channels. If it still does not translate, check that the message is long enough and not already in the target language.` | Every configured channel is fine. The number is the count of channels checked. |
| An embed titled **Missing permissions**, with one field per channel | Each field gives the channel, where it is used, and the missing permissions. Up to 20 channels are shown. |

**What the bot checks**

| Where the channel is used | Permissions needed |
| ------------------------- | ------------------ |
| Channel translation, source | View Channel, Read Message History |
| Channel translation, target | Depends on the style (see below) |
| Translation group | View Channel, Read Message History in each channel (source), and the style permissions of the group (target) |
| Role or category translation, target | Depends on the style (see below) |
| Flag translation | View Channel, Send Messages, Read Message History, Embed Links |
| TTS channel | View Channel, Read Message History |

**Permissions by style** (for the target channels)

| Style | Permissions |
| ----- | ----------- |
| `webhook` | View Channel, Send Messages, **Manage Webhooks**, Attach Files |
| `message` | View Channel, Send Messages, Attach Files |
| `embed` | View Channel, Send Messages, Embed Links, Attach Files |

A channel the bot cannot see at all is reported with *View Channel* as the missing permission. In that case the field shows the channel ID instead of its name.

Disabled channel translations, flag translations and groups are not checked. Permissions are checked in the channel itself, so **channel permission overrides** are taken into account: a channel can refuse what the bot role allows. See [Permissions](../permissions.md) for the complete list per feature.

## Symptom and check

| Symptom | Check |
| ------- | ----- |
| The bot does not translate anywhere | Run `/check-permissions`, then check that the configuration is saved and enabled. |
| The flags are not added under new messages | Run `/flags set` again, and check that the bot has *Add Reactions* in the channel. |
| The flags are added, but a click does nothing | Check that [Flag translation](../website/dashboard/flag-translation.md) is on in that channel. |
| Translations are plain messages, not webhooks | The bot lacks *Manage Webhooks*. |
| A group is not used | Check that the group is enabled and that the channels are in it (`/group list`). See [Translation groups](groups.md). |
| `⛔ You do not have permission to execute this command.` on `/flags` | The bot lacks *View Channel*, *Add Reactions* or *Read Message History* in that channel. |
