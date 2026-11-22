---
description: Translate messages automatically with translation rules, by channel, two languages in one channel, linked channels, category, role or the whole server.
---

# Automatic translation

Automatic translation is set up once, on the **Translation rules** page of the [dashboard](../website/dashboard/translation-rules.md). Then the bot translates the messages **by itself**: nobody has to do anything. You can also ask the [AI assistant](../management/ai-setup.md) for a first setup, but on a server that uses translation rules the assistant reads the rules without changing them yet: the page is the place to change them.

The first time you open the Translation rules page, the former configurations of your server (channel, category, role and link configurations) are converted automatically, once. Nothing is lost.

## The six types of rules

| Type                                                  | What it does                                                                 | Typical use                                        |
| ----------------------------------------------------- | ---------------------------------------------------------------------------- | -------------------------------------------------- |
| [Channels](#channels)                                 | Every message of one channel is translated into its language(s)             | `#english` is translated into French in `#francais` |
| [Two languages in one channel](#two-languages-in-one-channel) | Messages in language A become B, and messages in B become A          | A bilingual channel                                |
| [Linked channels](#linked-channels)                   | Channels that translate into each other, each in its own language           | One channel per language, everybody reads theirs   |
| [Categories](#categories-and-the-whole-server)        | All the channels of a category                                              | Translate a whole section of the server            |
| [Whole server](#categories-and-the-whole-server)      | Every channel of the server                                                 | A server where everything must be readable in one language |
| [Roles](#roles)                                       | Messages written by the members who have a role, in any channel             | `@french` members are translated into English      |

## Which rule applies

When a member writes a message, the bot looks at the rules that match it, and applies the **most precise** place rule:

1. **Two languages in one channel**, then **channel**, then **category**, then **whole server**. Only the most precise level applies: a channel rule replaces the category and server rules of that channel.
2. **Roles** are always added to the place rule. They depend on the author, not on the place.
3. On a server that applies only the most precise rule, a channel that is part of **linked channels** keeps only its role rules: the link decides where its messages go.

{% hint style="info" %}
Servers whose former configurations used to add up keep this behaviour: their overlapping rules all apply. The Translation rules page then shows a warning, with the button **Keep only the most precise**, that pauses the less precise rules.
{% endhint %}

## Options of the rules

Every rule has the same options. They are in the popup of the rule, and the less used ones are in **More options**.

| Option                       | What it does                                                                                                                                  |
| ---------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| **Languages**                | The target language(s). Up to 5 languages per rule (20 with Premium). A message is still translated into 3 languages at most (20 with Premium). |
| **Send the translations to** | The channel where the translation is posted. _The same channel_ by default. Not used by linked channels, or by a rule of two languages.      |
| **Send style**               | *As the author* (name and avatar of the author, the default), *Bot message* (plain message), *Bot card* (embed with the languages), or, for a channel rule, *In a thread* (see [threads](threads.md)). |
| **Delete the original message** | The original message is deleted once a translation is sent. Needs the *Manage Messages* permission. Not available with the thread style.   |
| **Delete the translation after** | *Never*, *Automatic (reading time)* (0.13 second per character, 25 seconds at least), or *After N seconds* (from 5 seconds to 24 hours).     |
| **Translate bots**           | Also translate the messages of bots (Premium).                                                                                                 |
| **Send even if the text seems already translated** | Send the translation even when the message already seems to be in the target language, or when the detection is not sure. |
| **Enabled** (switch)         | Pause a rule without deleting it. A paused rule is shown as paused.                                                                            |

{% hint style="info" %}
**Which style?** *As the author* is the most natural to read: the translation looks as if the author wrote it. It needs the *Manage Webhooks* permission; without it the bot sends a plain bot message instead, so the translation is never lost. *Bot card* shows the languages in its footer. *Bot message* needs the fewest permissions.
{% endhint %}

The Translation rules page flags a rule that needs a permission the bot does not have, and lists the missing permissions.

## Channels

A channel rule says: "every message sent in **this channel** is translated into **this language**, and sent to **that channel** (or to the same channel)".

Example: `#announcements` is translated into French and sent to `#annonces`. The page shows the rule as a sentence, for example *Messages in #announcements are translated into French, in #annonces*.

## Two languages in one channel

A rule of two languages says: "messages in language **A** are translated into **B**, and messages in **B** are translated into **A**". It replaces two channel rules.

Example: `#general` in English and French. A French message is translated into English, an English message into French.

A message written in **another** language (neither A nor B) can be handled in three ways, chosen in the rule:

* *Translated into A*;
* *Translated into B* (the default);
* *Not translated*.

## Linked channels

Linked channels are several channels, **each with its own language**. A message written in one channel is translated into the language of **every other channel** of the link, one translation per language, and sent to those channels. You don't have to create every pair yourself.

Example: `#english` (English), `#francais` (French) and `#espanol` (Spanish) are linked. A message in `#francais` is translated into English and Spanish, and sent to `#english` and `#espanol`.

In **More options > Advanced**, the option **Translate in the original channel too** translates a message written in another language than the one of its channel into the language of that channel first, then sends it to the other channels as usual. It is used only when the language is detected with confidence.

Limits: a free server can have **one link of 3 channels**; a Premium server **5 links of 5 channels**.

## Categories and the whole server

A category rule works like a channel rule for **all the channels of a category**, including the ones created later. The channels that have their own rule keep it: a channel rule is more precise.

A whole-server rule translates **every channel** of the server into its language(s), except the channels that have a more precise rule.

## Roles

A role rule translates **everything the members who have this role write**, in any channel where the bot can read, into the chosen language. The translation is sent to the channel where the message was written, or to the channel you choose.

Example: members with the role `@french` write in French, and you want everybody to read English: a role rule `@french` -> English. If you add Japanese too, each message gets 2 translations.

Role rules never apply to webhook messages.

## Exceptions

The [Exceptions](../website/dashboard/exceptions.md) of the dashboard (Premium) come **before** the rules: a channel, a role or a language that is excluded is never translated, whatever rule would apply. The minimum message size of a channel works the same way. Exceptions do not apply to flag reactions.

## Bots, webhooks and edits

* The bot never translates **its own** messages, nor the webhook messages it sends.
* Messages of other bots are translated only on a Premium server, and only by the rules with the *Translate bots* option (role rules are not checked for bots).
* Editing a message **updates its translations** when the setting *Follow edited messages* of the [Overview](../website/dashboard/overview.md) is on (it is on by default). At most 5 new translations per message and per hour are made for an edit, and the bot keeps the link to a translation for 6 hours after its last update. The link is lost when the bot restarts, so an edit made just after a restart changes nothing.

## Limits

| Limit                                        | Free | Premium |
| -------------------------------------------- | ---- | ------- |
| Translation rules per server                 | 30   | 200     |
| Languages in one rule                        | 5    | 20      |
| Translations of one message                  | 3    | 20      |
| Linked channels (links per server x channels per link) | 1 x 3 | 5 x 5 |

See [Premium](../premium/premium.md) for the full list.

## Good practices

* Give the bot its permissions in **both** the source and the target channels (see [Troubleshooting](troubleshooting.md#permissions)). The [Check a channel](../website/dashboard/translation-rules.md#tools) tool of the Translation rules page, or `/check-permissions`, tells you what is missing.
* If a language is often detected wrongly, raise the [minimum message size](../website/dashboard/exceptions.md#minimum-message-size) of the channel, or see [language detection](language-detection.md).
* Use *Delete the translation after* in busy channels so the translations don't pile up.
* Use **Try a sentence** on the Translation rules page before you announce a new rule.
