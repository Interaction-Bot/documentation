---
description: Configure the translations in specific channel on your server.
---

# Channel Translation

## Localization

This page is the first section in the navbar in the category _**translation**_ at the left of the page.

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption><p>Channel translation page</p></figcaption></figure>

## What does channel translation do?

When this setting is enabled for a specific channel, any message in this channel that is not in the language defined by the configuration will be translated to the target language.

## Translate a new channel

To translate a new channel, you need to click on _**Add a Configuration**_ button.

<figure><img src="../../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

You see a popup that accepts different parameters

<figure><img src="../../.gitbook/assets/image (57).png" alt=""><figcaption><p>Channel translation popup</p></figcaption></figure>

* _**CHANNEL**_: the channel where messages that are not in the target language will be caught and translated.
* _**SENDING CHANNEL**_: the channel where the translation will be sent.
* _**LANGUAGE**_: the language where the message will be translated.

You can see more options by clicking on the _**OPTIONS**_.&#x20;

<figure><img src="../../.gitbook/assets/image (58).png" alt=""><figcaption><p>options dropdown</p></figcaption></figure>

These options accept different parameters

* _**STYLE:**_ the style of the message, if the translation will be sent in embed, in a webhook, or just like a regular message
* _**DELETE MESSAGE:**_ if the language of the message sent by the user is different than the _**Language**_ option, the message will be deleted.
* _**DELETE TRANSLATION:**_ the bot will delete his translation after a time that depends on the length of the translation (0.13 seconds per character).
* _**TRANSLATE BOT:**_ even if the message is sent by a bot, the bot will translate the message if the language doesn't correspond to the target language.
* _**ALWAYS SEND:**_ even if the message is in the same language as the LANGUAGE option, the bot will translate the message.

{% hint style="info" %}
These parameters can be left blank.
{% endhint %}

Once you have made your configuration, you must click on the _**Save**_ button on the popup. You will now see the new configuration that you have added, to post your configurations, follow[ this instruction](channel-translation.md#save-configurations).

## Save configurations

When you have configured all the channels that you want to be translated, don't forget to save your configuration!

<figure><img src="../../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>
