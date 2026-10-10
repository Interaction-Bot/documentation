---
description: Flag shortcuts and permission check.
---

# Flags and diagnostics

## Flag shortcuts

| Command                         | Description                                                                                               |
| ------------------------------- | --------------------------------------------------------------------------------------------------------- |
| `/flags set <channel> <flags>`  | The bot adds 1 to 5 flag reactions under every message of the channel. Click a flag to translate the message. Example: `/flags set #general 🇬🇧 🇫🇷 🇪🇸`. |
| `/flags clear <channel>`        | Stop adding flags in the channel.                                                                          |

Flag translation itself (adding a flag reaction yourself) is described in [Flag translation](../website/dashboard/flag-translation.md). Supported flags include the Hebrew, Bengali, Tswana, Welsh and Scottish flags, and the pirate flag 🏴‍☠️ (translates to English, then in "pirate speak").

## /check-permissions

`/check-permissions` lists the permissions the bot is missing in each channel where a translation is configured. Use it when "the bot does not translate": it tells you exactly which permission to give to the bot role.

## Step by step

### Let members translate with one click

1. Run `/flags set channel:#general flags:🇬🇧 🇫🇷 🇪🇸` (1 to 5 flags), or use [Flag shortcuts](../website/dashboard/flag-shortcuts.md) on the dashboard.
2. The bot adds these flags under every new message of the channel.
3. A member clicks a flag: the bot replies with the translation in that language ([how it works](../translation/how-it-works.md)).
4. `/flags clear channel:#general` stops it.

The bot needs *Add Reactions* in the channel.

### Choose the flags

Pick the languages your community really speaks. Several flags can give the same language (🇬🇧, 🇺🇸 and 🇨🇦 give English), so one flag per language is enough. The complete list is in [Languages and flags](../translation/languages.md).

## `/check-permissions` step by step

1. Run `/check-permissions` (it needs the *Manage Server* permission).
2. The answer lists, for each channel with a configuration (translation, flags, TTS, FAQ…), the permissions the bot is missing.
3. Give these permissions to the bot role, or fix the permission overrides of the channel, then run the command again.

## Troubleshooting

| Symptom                                 | What to check |
| --------------------------------------- | ------------- |
| The flags do not appear                 | *Add Reactions* permission; the channel is in `/flags set`; Discord limits a message to 20 different reactions. |
| A flag reaction does nothing            | [Flag translation](../website/dashboard/flag-translation.md) is disabled in this channel, the message is empty, or it was written by a bot (premium only). |
| The translation disappears              | *Auto delete* is on: it deletes the translation after about 0.13 s per character (25 s minimum). |
