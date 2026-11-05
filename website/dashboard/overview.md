---
description: >-
  The overview page shows information about your server and the bot, and lets you
  change the simultaneous translation warning and the follow of edited messages.
---

# Overview

## Localization

This page is the first item of the navigation bar. Its title is **Overview**.

<figure><img src="../../.gitbook/assets/dash-overview.png" alt="Overview page"><figcaption><p>Overview</p></figcaption></figure>

## Server

This section shows information about your Discord server. Nothing can be changed here.

* **MEMBERS**: the number of members of the server.
* **CHANNELS**: the number of channels of the server (text, voice and the other channels; categories are not counted).
* **ID**: the ID of your server. You need it to find the shard of your server on the [status page](../status.md), and to use the `guild-id` option of the [Premium commands](../../premium/usage.md).
* **CATEGORIES**: the number of categories of the server.
* **ROLES**: the number of roles of the server.

A **Premium** or **Free** badge at the top of the page tells whether the server has Premium. See [Premium](premium.md).

## Bot settings

This card holds the bot language, the announcements channel, the simultaneous translation warning and the follow of edited messages. The cluster and the shard of your server are shown on the [status page](../status.md#server-localization).

### Language

This setting sets the language of the bot messages on this server (help, errors, panels, confirmations), with the **LANGUAGE** list. **Automatic** (default) uses the language of the server on Discord; you can also choose one of the available languages. The same setting is available in Discord with [`/bot-language`](../../commands/configuration.md#language-of-the-bot).

### Announcements channel

The channel where the bot posts its own messages, such as its welcome message when it joins, the end of a Premium plan, and the messages of a recording started from the Activity. By default, it is the community updates channel of your server, else its system channel, else a private channel created by the bot.

### Edited messages

**Follow edited messages** (enabled by default): when someone edits a message that was translated, the translations are updated. The bot retranslates a message at most 5 times per hour, and only during 6 hours after the last translation of the message. The same setting is available in Discord with `/server-settings edits`.

### Warning

This section contains one toggle, **Simultaneous Translation Warning** (enabled by default).

When a single message is translated into more languages than the limit of your server, the bot posts a warning in the channel. The warning is shown at most once a day. The warning explains that the limit of your offer was exceeded, gives a link to the premium page, and tells how to disable it. The toggle only hides this warning: the limit itself still applies.

<details>

<summary>What is <em><strong>simultaneous translation</strong></em>?</summary>

When a message is posted in a channel that is translated automatically, the bot counts the translations that it makes for this message.

For example, if you post _Hello World_ in #Channel1 and the bot is configured to translate it into French, Japanese and German, the bot makes 3 translations for this message. That is the limit of a server without Premium: 3 translations per message. Premium servers can get up to 20 translations per message.

When the bot has to make more translations than the limit for one message, it shows the warning (if the toggle is enabled). To remove this warning, disable the toggle and save.

</details>

Don't forget to click on _**Save**_ after a change, see [Save your changes](README.md#save-your-changes).
