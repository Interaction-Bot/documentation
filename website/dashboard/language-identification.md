---
description: Choose, per channel, the minimum size of a message that the bot translates.
---

# Language identification

## Localization

This setting is on the **Exceptions** page of the **Translation** section of the navigation bar, in the card **Minimum message size**. The former **Language Identification** page redirects there.

<figure><img src="../../.gitbook/assets/dash-language-identification.png" alt="Language identification page"><figcaption><p>Language identification page</p></figcaption></figure>

## What does language identification do?

Before translating a message, the bot detects its language. A very short message (*ok*, *lol*, *yes*) often gets a wrong language, and its translation is then wrong or useless.

On this page, you choose for a channel the **minimum number of characters** that a message must have to be translated. A message shorter than this minimum is ignored in this channel: it is not translated by any rule (channel, role, category or group translation).

* Flag translations are not affected: a flag reaction still translates a short message.
* Without a configuration, a channel has no minimum.

## Running configurations

The list shows one sentence per channel that has a minimum, for example *In #general, messages shorter than 15 characters are not translated*.

In the **⋯** menu of each row:

* _**Edit**_: opens the configuration in the popup.
* _**Delete**_: removes the minimum of this channel (applied after you click on _**Save**_).

## Add a configuration

Click on _**Add a channel**_. On a server without Premium, when you already have 20 configurations, this button opens the Premium pop-up instead.

The popup has two fields:

* **Which channel?** (**Which channels?** when you add a configuration: you can tick several channels, and they all get the same minimum): *Messages in this channel that are shorter than the minimum are not translated.* Each channel can have only one configuration.
* **How many characters at least?**: *A message shorter than this number is not translated. It is a length threshold, not a language detection.* Type a number from **0** to **500**. A new configuration starts with **5**. Messages with fewer characters are ignored.

Click on _**Add the channel**_ in the popup (_**Validate**_ when you edit a configuration), then click on _**Save**_ in the bar at the bottom of the page.

### Example

In #general, many short messages are detected in the wrong language. Set **How many characters at least?** to `15` for #general: messages of fewer than 15 characters are no longer translated there, and longer messages are translated as before.

## Errors

Messages under the popup, which keep the _**Add the channel**_ button disabled:

* **Choose a channel first.**: no channel is selected.
* **Choose a number between 0 and 500.**: the number is empty or out of range.
* **This channel already has a minimum size. Edit it instead.**: the channel is already configured.
* **Maximum 20 channels without premium: N chosen**: the limit of a server without Premium would be exceeded.

When the save fails, the message *Saving failed. Your changes are still here: try again.* appears above the list. Nothing has been saved.

## Tips

* Start with a value between 10 and 20 in busy channels, and adjust it according to the translations you see.
* A value of `0` translates every message, as long as the other rules allow it.
* See also the [FAQ](../../faq.md) for the messages that are not translated.
