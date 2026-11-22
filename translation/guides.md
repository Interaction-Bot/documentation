---
description: Ready-to-use setups for common situations, step by step on the dashboard or with the AI assistant.
---

# Setup guides

Step by step recipes. Each one uses the [dashboard](../website/dashboard/) (**Translation** section), and the [AI assistant](../management/ai-setup.md) when it can help.

{% hint style="info" %}
On a server that uses the translation rules, the AI assistant can **read** the rules but cannot change them yet: make the changes on the [Translation rules](../website/dashboard/translation-rules.md) page. Each guide below uses that page.
{% endhint %}

Before you start, check that the bot has its permissions in every channel involved. The [Check a channel](../website/dashboard/translation-rules.md#tools) tool of the Translation rules page, or `/check-permissions`, lists what is missing.

## 1. An international community: one channel per language

**Goal**: members write in their own language, in their own channel, and everybody reads all of them.

1. Create the channels `#english`, `#francais`, `#espanol`.
2. On the **Translation rules** page, click **Add a rule**, then choose **Linked channels**.
3. Choose the three channels, and the language of each one (English, French, Spanish). Save.
4. Check with the **Check a channel** tool that the bot can read and write in the three channels.

A message in any of the channels is translated into the languages of the two other channels, and sent there. A free server can have **one link of 3 channels**; a Premium server **5 links of 5 channels**.

## 2. Translate one channel into another

**Goal**: staff write in English in `#announcements`, and French members read `#annonces`.

1. On the **Translation rules** page, click **Add a rule**, then choose **Channels**.
2. Choose `#announcements`, the language **French**, and **Send the translations to** `#annonces`.
3. Keep the style **As the author** for a natural look. Save.

## 3. A bilingual channel

**Goal**: in `#general`, French messages are translated into English, and English messages into French.

1. Click **Add a rule**, then choose **Two languages in one channel**.
2. Choose `#general`, then the two languages (English and French).
3. Choose what happens to a message written in another language: translated into one of the two languages, or not translated. Save.

This replaces two channel rules.

## 4. Translate what some members write

**Goal**: Japanese speakers (role `@japanese`) write anywhere, and everybody reads English.

1. Click **Add a rule**, then choose **Roles**.
2. Choose the role `@japanese` and the language **English**.
3. Leave **Send the translations to** on *The channel where the message was written*, so the answer appears in the same channel. Save.

Add an [exception](../website/dashboard/exceptions.md) (Premium) for the channels where you don't want translations.

## 5. One-click translation for everybody

**Goal**: any member can translate any message of `#general`.

* Do nothing: members can already add any flag reaction under a message, see [Flag translation](flags.md).
* To show the flags under every new message, go to **Translation** > **Flags** > **Automatically added flags**, choose `#general`, and choose from 1 to 5 flags, for example 🇬🇧 🇫🇷 🇪🇸. The bot adds them under the new messages, and a member only clicks one.

## 6. Translate a whole section of the server

**Goal**: all the channels of the category "International" are translated into English.

1. Click **Add a rule**, then choose **Categories**.
2. Choose the category, and the language **English**. Save.

The channels of the category that have their own rule keep it: a channel rule is more precise than a category rule.

## 7. Translate every message of a server

**Goal**: everything written in the server is readable in English.

1. Click **Add a rule**, then choose **Whole server**.
2. Choose the language **English**. Save.

Use the exceptions to leave some channels alone, for example a channel that is already multilingual.

## 8. Exclude a channel, a role or a language

**Goal**: messages of `#bot-logs`, of the members with the role `@Bots`, or written in Latin are never translated (Premium).

1. Open **Translation** > **Exceptions**.
2. In **Never translate**, add the channel, the role or the language.

Exceptions apply before the rules. See [Exceptions](../website/dashboard/exceptions.md).

## 9. Read the messages of a channel aloud, or transcribe a voice channel

These are not translations, but they are often set up together. See [Voice](../audio/voice.md) and the dashboard pages [Text to speech](../website/dashboard/tts-channels.md) and [Speech to text](../website/dashboard/speech-to-text.md).

## 10. A FAQ that answers by itself

Create a group on the dashboard page [FAQ](../website/dashboard/faq.md), add questions and answers, choose the channels, and turn on automatic answers. See [FAQ and /ask](../qa/faq.md).
