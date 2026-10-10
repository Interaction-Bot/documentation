---
description: Configure the translation by flag emoji
---

# Flag translation

## Localization

This page is the third section in the navbar in the category _**translation**_ at the left of the page.

<figure><img src="../../.gitbook/assets/dash-flag-translation.png" alt=""><figcaption><p>Flag translation page</p></figcaption></figure>

## What does flag translation do?

Flag Translation lets members translate a Discord message by adding a flag emoji under it. The flag gives the target language (🇫🇷 French, 🇪🇸 Spanish, 🇯🇵 Japanese…, see [Languages and flags](../../translation/languages.md)). The bot answers with a reply under the message, so everybody can read the translation.

{% hint style="success" %}
Flag translation works **without any configuration**, in every channel. Use this page only to change the behaviour of a channel (disable it, choose *Once* or *Every time*, keep the translation).
{% endhint %}

## Configure flag translation for a channel

To configure a new channel, you need to click on _**Add a Configuration**_ button.

<figure><img src="../../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

You see a popup that accepts different parameters

<figure><img src="../../.gitbook/assets/dash-flag-translation-popup.png" alt=""><figcaption><p>Flag translation popup</p></figcaption></figure>

* _**Channel**_: The channel where the configuration will be applied.
* _**ACTIVATED**_: Enable or disable flag translation for this channel.

You can see more options by clicking on the _**OPTIONS**_.&#x20;

<figure><img src="../../.gitbook/assets/dash-flag-translation-options.png" alt=""><figcaption><p>options dropdown</p></figcaption></figure>

These options accept different parameters

* _**Activated**_ toggle: enable the flag translation in the channel.
* _**SENDING MODE:**_ The bot will translate messages differently depending on the selected mode. In "Every time" mode, the bot will send the translation each time a reaction is added to the message. In "Once" mode, the bot will only translate the message if it has never been translated previously by the translation flag and a reaction is added (the bot remembers the last 1,000 translated messages).
* _**AUTO DELETE:**_ If this option is enabled, the translation will be deleted after a delay that changes depending on the length of the message, otherwise the translation will never be deleted. The delay is about 0.13 seconds per character, with a minimum of 25 seconds.

{% hint style="info" %}
These parameters can be left blank.
{% endhint %}

Once you have made your configuration, you must click on the _**Save**_ button on the popup. You will now see the new configuration that you have added, to post your configurations, follow [this instruction](flag-translation.md#save-configurations).

## Save configurations

When you have made all your configuration, don't forget to save your configuration by clicking on _**Save**_!

<figure><img src="../../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Want the flags to appear automatically under every message? Use the [Flag shortcuts](flag-shortcuts.md).
{% endhint %}
