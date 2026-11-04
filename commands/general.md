---
description: All other commands of Interaction Bot.
---

# General

| Command          | Description                                                                 |
| ---------------- | --------------------------------------------------------------------------- |
| `/about`         | Get information about the bot (versions, latency, cluster, servers, users). |
| `/dashboard`     | Get the link of the dashboard.                                              |
| `/documentation` | Get the documentation link.                                                 |
| `/help`          | Display the help page with all commands.                                    |
| `/invite`        | A card with five buttons: add the bot to a server, add it to your account (to install it as a [user app](user-app.md)), the support server, the dashboard and the vote. |
| `/ping`          | Get the ping of the bot.                                                    |
| `/support`       | Get the Discord link of the support server.                                 |
| `/reminder enable` | Enable or disable the reminder to vote for the bot on top.gg.             |

`/dashboard`, `/help`, `/invite` and `/support` also work as a [user app](user-app.md), without the bot in the server.

## Voting

Some voice commands ([`/connect`, `/tts say`](../audio/voice.md)) require that you voted for the bot on [top.gg](https://top.gg/bot/893494390142697493/vote) during the last 24 hours. You can vote every 12 hours, and `/reminder` can notify you when it is possible again.

## Premium

`/premium add` and `/premium remove` are described in the [premium usage](../premium/usage.md) page.

## Who sees the answer

The answers of the commands are shown to the whole channel, errors included. The commands that are private by nature answer only to you: `/privacy`, `/personal-language`, `/tts clone`, `/record list`, the temporary voice menus, and the right-click menus **Translate**, **Detect** and the one of voice messages. The answers to buttons and menus keep their own setting.
