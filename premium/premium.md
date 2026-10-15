---
description: What Interaction Bot Premium brings to your servers, and how the slots work.
---

# Premium

Interaction Bot Premium adds features and higher limits to the bot on your servers. Premium offers are managed on Patreon. They give a number of **server slots**: **1**, **3** or **10** servers. Each server with Premium uses one slot.

The offers are available [here](https://www.patreon.com/interactionbot).

<figure><img src="../.gitbook/assets/dash-premium-public.png" alt="Premium page of the website"><figcaption><p>Premium page of the website</p></figcaption></figure>
<figure><img src="../.gitbook/assets/patreon-offers.png" alt="Patreon page"><figcaption><p>Patreon page</p></figcaption></figure>

## How the slots work

* Premium is set **per server**, not per member.
* A slot is used when a server gets Premium, with the `/premium add` command or with the **Premium** toggle of the [dashboard](../website/dashboard/premium.md). Turning Premium off, or running `/premium remove`, frees the slot.
* To give Premium to another server when all your slots are used, first remove it from a server.
* Premium is also used by the [user app](../commands/user-app.md): a member whose Discord account is linked to a Patreon offer gets it when using `/translate` and the Apps menus outside the servers where the bot is added.
* To buy, see [Subscribe](subscribe.md). To activate it, see [Usage](usage.md).

## What Premium brings

| Feature | Free | Premium |
| --- | --- | --- |
| Translation quality | Free tier of the translation service | Premium tier, routed to the best model |
| Channels, roles and categories translated | 20 of each | 500 of each |
| Translations of one message | Up to 3 | Up to 20 |
| Translation groups | 1 group of 3 channels | 5 groups of 5 channels |
| Messages of bots translated | No | Yes |
| Flag reactions on messages of bots | No | Yes |
| Embeds and buttons translated | No | Yes |
| Blacklist (channels, roles, languages) | No | Yes |
| Speech to text time (per server, per day from midnight UTC) | 30 minutes | 3 hours |
| Text to speech time (per server, per day from midnight UTC) | 30 minutes | 3 hours |
| Recording time (per server, per day from midnight UTC) | 1 hour | 6 hours |
| Recording kept after it ends | 7 days | 30 days |
| Continuous recording (keeps going when the channel is empty, 24 hours at most) | No | Yes |
| Speech to text without a top.gg vote | No | Yes |
| Speech to text configurations | 1 | Unlimited (3 per voice channel) |
| Speech to text translation | No | Yes |
| Text to speech without a top.gg vote | No | Yes |
| Text to speech channels | 5 | 25 |
| Text to speech translation of a TTS channel | No | Yes |
| FAQ | 1 group, 5 questions | 5 groups, 150 questions |
| Premium on several servers | - | With the 3 and 10 servers offers |

Without a top.gg vote, a free server can use speech to text, text to speech and recording when a member of the server has voted for the bot in the last 24 hours. The daily time of each feature is in [Daily limits](../audio/limits.md).

Example: with the role @french translated into English, Japanese, Brazilian and Spanish, a message of a member with this role produces 4 translations. The free version is limited to 3 translations per message, the Premium version to 20. The limit and the warning shown when it is exceeded are explained on the [Overview](../website/dashboard/overview.md) page.

Where to configure each feature: [Channel Translation](../website/dashboard/channel-translation.md), [Role Translation](../website/dashboard/role-translation.md), [Category Translation](../website/dashboard/category-translation.md), [Translation Groups](../website/dashboard/translation-groups.md), [Flag Translation](../website/dashboard/flag-translation.md), [Blacklist](../website/dashboard/blacklist.md), [Speech to text](../website/dashboard/speech-to-text.md), [Text to speech](../website/dashboard/tts-channels.md), [Text to speech settings](../website/dashboard/tts-settings.md), [Voice recording](../website/dashboard/voice-recording.md), [Temp voice](../website/dashboard/temp-voice.md) and [FAQ](../website/dashboard/faq.md).

**Refund policy:** In case of any problem, contact the support and we will handle refunds case by case, in a transparent way.
