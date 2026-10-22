---
description: Link several channels, each with its own language.
---

# Mirror Translation

<figure><img src="../../.gitbook/assets/dash-translation-groups.png" alt="Mirror Translation page"><figcaption><p>Mirror Translation page</p></figcaption></figure>

## Localization

Navbar > category _**Translation**_ > _**Mirror Translation**_.

The counter at the top right shows how many mirrors you use, for example `1/1` on a free server.

## How it works

Put several channels in a mirror and give each one its language. A message sent in one channel is translated into the language of **every other channel** of the mirror. No need to configure every source/target pair.

**Example.** A mirror called `Community` has three channels: `#general` in English, `#general-fr` in French and `#general-es` in Spanish. A message written in `#general-fr` is sent in `#general` in English and in `#general-es` in Spanish. It is not sent back to `#general-fr`.

The same mirrors can be managed with the [`/group` commands](../../commands/groups.md). The dashboard and the commands always show the same mirrors.

## Create a mirror

1. Click _**Add a mirror**_. A new mirror named `Group 1` (or the next free number) appears.
2. Change its settings (see the table below).
3. Click _**+ Add a channel**_ and choose a channel. The new row uses English by default: change the language if needed.
4. Repeat step 3 for each channel of the mirror.
5. Click _**Save**_ in the popup at the bottom of the page.

If you click _**Add a mirror**_ or _**+ Add a channel**_ when you are at your limit, the Premium popup opens instead.

## Settings of a mirror

| Field | What it does |
| ----- | ------------ |
| **Mirror name** | Up to 40 characters, unique in the server (upper and lower case are not distinguished). |
| **Sending style** | How translations are sent: **Webhook** (default), **Message** or **Embed**. See [Styles and options](../../translation/styles-and-options.md). |
| **Enabled** | Pause the whole mirror without deleting it. A paused mirror keeps its channels and languages. |
| **Channel** and **Language** | One row per channel. A channel can only appear once in a mirror, so the channels already used by another row are disabled in the list. |
| **Delete the original message** | Delete the original message once it has been translated. The bot needs the *Manage Messages* permission in the source channel. |
| **Delete translations after a while** | The translations are deleted after the duration you give in **Keep for (seconds)**, from 5 to 86400. Leave it empty (*auto*) to use the reading time of the text, with a minimum of 25 seconds. |
| **Translate bots** (Premium) | Also translate messages sent by bots. Locked on free servers. |
| **Always send** | Send the translations even when the message looks already translated, or is in the language of the channel. |

The **Delete mirror** button removes the mirror, with its channels. Nothing else is changed.

{% hint style="info" %}
A channel that is deleted from the server is removed from its mirror automatically.
{% endhint %}

## Saving

Changes are not saved until you click _**Save**_ in the popup at the bottom of the page. _**Cancel**_ goes back to the last saved configuration.

If the save is refused, the page shows: `Invalid configuration (duplicated name or channel, limit reached, ...)`. Check the names (no two mirrors with the same name), the channels (no channel twice in a mirror, only text channels of this server) and the limits. If the page shows `Could not save, try again`, the server did not answer: try again in a moment.

## Limits

| Free                        | Premium                      |
| --------------------------- | ---------------------------- |
| 1 mirror of up to 3 channels | 5 mirrors of up to 5 channels |

If Premium ends, the free limits apply again. The dashboard does not let you add mirrors or channels above them, and it refuses to save a configuration above them. Remove the extra mirrors or channels, then save.

## Troubleshooting

* **A mirror does nothing.** Check that the mirror is **enabled**, and that the bot has its permissions in the channels of the mirror. Run [`/check-permissions`](../../commands/flags.md#diagnostics-check-permissions) on your server to list the missing permissions.
* **A message is not translated into one language.** That language is the same as the message's language, or the message is too short or its language is uncertain. Turn on **Always send** to force the translation.
* **Translations are plain messages, not webhooks.** The bot lacks the *Manage Webhooks* permission.

For the full list of rules, see [Translation groups](../../commands/groups.md).
