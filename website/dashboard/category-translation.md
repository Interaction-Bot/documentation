---
description: Translate every channel of a category.
---

# Category Translation

## Localization

This page is in the navbar, in the category _**translation**_.

## What does category translation do?

When this setting is enabled for a category, every message sent in a channel of this category that is not in the target language is translated. It works like the [channel translation](channel-translation.md), but for all the channels of the category at once.

## Add a configuration

Click on _**Add a Configuration**_ and fill the popup:

* _**CATEGORY**_: the category to translate. Enable the automatic translation for it.
* _**LANGUAGE**_: the target language of the translation.

More options are available in _**OPTIONS**_:

* _**STYLE**_: embed, webhook or regular message.
* _**SENDING CHANNEL**_: the channel where the translation is sent.
* _**DELETE MESSAGE**_: delete the original message.
* _**DELETE TRANSLATION**_: delete the bot message after a delay.
* _**TRANSLATE BOT**_: translate messages sent by bots (**premium only**).
* _**ALWAYS SEND**_: send the translation even if the message is already in the target language.

{% hint style="info" %}
Channels in the [blacklist](blacklist.md) are ignored by role and category translation.
{% endhint %}

Don't forget to click on _**Save**_ to apply your configuration.
