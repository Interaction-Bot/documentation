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
