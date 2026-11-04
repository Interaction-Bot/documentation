---
description: Choose, per channel, the minimum size of a message that the bot translates.
---

# Language identification

## Localization

This page is in the **Translation** section of the navigation bar, under **Exceptions**. The section is called **Minimum message size** (formerly *Language identification*).

<figure><img src="../../.gitbook/assets/dash-language-identification.png" alt="Language identification page"><figcaption><p>Language identification page</p></figcaption></figure>

## What does language identification do?

Before translating a message, the bot detects its language. A very short message (*ok*, *lol*, *yes*) often gets a wrong language, and its translation is then wrong or useless.

On this page, you choose for a channel the **minimum number of characters** that a message must have to be translated. A message shorter than this minimum is ignored in this channel: it is not translated by any rule (channel, role, category or group translation).

* Flag translations are not affected: a flag reaction still translates a short message.
* Without a configuration, a channel has no minimum.

## Running configurations

The list shows one line for each channel that has a minimum, for example _In #general, messages shorter than 15 characters are not translated_. When no channel has a minimum, the list says _No channel has a minimum size. Add one to skip messages that are too short._

* _**Edit**_: opens the configuration in the popup. Clicking on the row does the same.
* _**Delete**_: removes the minimum of this channel (applied after you click on _**Save**_).

## Add a channel

Click on _**Add a channel**_. Without Premium, a server can have 20 channels at most.

The popup has two fields:

* **Which channel?**: the channel where the minimum applies. Messages in this channel that are shorter than the minimum are not translated. Each channel can have only one minimum size: a channel that already has one is refused, and you edit it instead.
* **How many characters at least?**: type a number from **0** to **500**. A new configuration starts with **5**. A message shorter than this number is not translated. It is a length threshold, not a language detection.

Click on _**Save**_ in the popup, then click on _**Save**_ in the bar at the bottom of the page.

### Example

In #general, many short messages are detected in the wrong language. Set **How many characters at least?** to `15` for #general: messages of fewer than 15 characters are no longer translated there, and longer messages are translated as before.

## Command

The same minimum can be set with the `/language-detection` command:

* `/language-detection set`: set the minimum of a channel, from 0 to 500 characters.
* `/language-detection reset`: remove the minimum of a channel.
* `/language-detection list`: list the channels that have a minimum.

By default, only members with the *Manage Server* permission can use these commands.

## Errors

* **Error - You have not completed all the required fields.** (pop-up): no channel is selected.
* **It seems something has gone wrong.** (pop-up, followed by the error): the save failed.
* The bar stays on the screen without any message when the bot refuses the save, for example when a channel no longer exists. Nothing has been saved.

## Tips

* Start with a value between 10 and 20 in busy channels, and adjust it according to the translations you see.
* A value of `0` translates every message, as long as the other rules allow it.
* See also the [FAQ](../../faq.md) for the messages that are not translated.
