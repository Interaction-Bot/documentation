---
description: Configure translation by the user's role on your server.
---

# Role Translation

## Localization

This page is the second section in the navbar in the category _**translation**_ at the left of the page.

<figure><img src="../../.gitbook/assets/image (62).png" alt=""><figcaption><p>Channel translation page</p></figcaption></figure>

## What does role translation do?

When this setting is enabled for a specific role, any message sent by a user or bot with this role that is not in the language defined by the configuration will be translated into the target language.

## Translate a new role

To translate a new role, you need to click on _**Add a Configuration**_ button.

<figure><img src="../../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

You see a popup that accepts different parameters

<figure><img src="../../.gitbook/assets/image (63).png" alt=""><figcaption><p>Channel translation popup</p></figcaption></figure>

* _**Role**_: This role allows you to translate any message sent by a user having it, as long as this message is not in the target language.
* _**LANGUAGE**_: the language where the message will be translated.

You can see more options by clicking on the _**OPTIONS**_.&#x20;

<figure><img src="../../.gitbook/assets/image (64).png" alt=""><figcaption><p>options dropdown</p></figcaption></figure>

These options accept different parameters

* _**STYLE:**_ the style of the message, if the translation will be sent in embed, in a webhook, or just like a regular message
* _**SENDING CHANNEL: t**_he channel where the translation will be sent, if not defined, the translation will be sent in the channel where the message has been posted.
* _**DELETE MESSAGE:**_ if the language of the message sent by the user is different than the _**Language**_ option, the message will be deleted.
* _**DELETE TRANSLATION:**_ the bot will delete his translation after a time that depends on the length of the translation (0.13 seconds per character).
* _**ALWAYS SEND:**_ even if the message is in the same language as the LANGUAGE option, the bot will translate the message.

{% hint style="info" %}
These parameters can be left blank.
{% endhint %}

Once you have made your configuration, you must click on the _**Save**_ button on the popup. You will now see the new configuration that you have added, to post your configurations, follow[ this instruction](role-translation.md#save-configurations).

## Save configurations

When you have made all your configuration, don't forget to save your configuration by clicking on _**Save**_!

<figure><img src="../../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>
