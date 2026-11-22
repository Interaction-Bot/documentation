---
description: Let your members get answers from a FAQ made by your moderators.
---

# FAQ and /ask

Moderators create a FAQ for the server on the [FAQ page of the dashboard](../website/dashboard/faq.md): questions and their answers, organized in **groups**. Members use `/ask` to search it. The bot can also **answer by itself** to questions asked in the channels linked to a group, in any language, when it is confident enough of the answer.

The answers are never generated: the bot only sends the answers your moderators wrote. If a question is asked in another language than the answer, the answer is translated, and Discord mentions, channel links and URLs are kept as they are.

| Command | Who | What it does |
| ------- | --- | ------------ |
| `/ask question:<text> [group]` | Everybody | Search the FAQ. The answer is shown only to the member who asked. |

There is no `/faq` command. Groups, questions, linked channels and the automatic replies are managed on the dashboard, see [FAQ](../website/dashboard/faq.md). For everything step by step, read [FAQ guides](faq-guides.md).

## /ask

Example: a member types `/ask question:How do I change my nickname?` in a channel linked to a group called `Support`.

* If the FAQ has a matching question, the member sees an embed titled **FAQ**, with the answer as its text. The footer says which question matched: `Matched question: How do I change my nickname on this server?`. If other close questions exist, a **See also** field lists up to two of them.
* If nothing matches well enough: `I did not find an answer in the FAQ. Try other words or ask the moderators.`

The answer is posted in the channel, so everybody there can read it.

Rules:

* The question can be up to 300 characters, in any language.
* `/ask` searches **one group only**. In a channel linked to a group, that group is used automatically. In any other channel, choose the group with the `group` option.
* A member can use `/ask` once every 10 seconds.
* In a channel that is not linked to any group: `This channel is not linked to a FAQ. Choose a group with the group option.`
* If the server has no FAQ yet: `This server has no FAQ yet. A moderator can create one on the dashboard.`
* Threads use the group of the channel they belong to.

## Automatic replies

When automatic replies are on for the group of a channel, the bot can answer a message by itself. The answer is a reply to the message, with:

* the question as its title,
* the answer as its text,
* in the footer, the group name and the confidence of the match, for example `Support · 91%`,
* a grey **Not helpful** button.

Example: a member writes in `#help` *"I cannot find the Developer role anywhere, how do I get it?"*. If the FAQ entry *"How do I get the Developer role?"* matches strongly enough, the bot replies under the message with that entry.

**The bot stays silent** (and does not answer) when:

* the message is from a bot or a webhook, starts with `/` or `!`, has fewer than 4 words, or contains only links, emojis or mentions;
* no entry reaches the group's minimum confidence (80% to 95%, 85% by default);
* two entries match almost equally well, so the bot cannot choose one;
* the bot cannot send messages or embeds in the channel, or the search is rate limited.

**Not helpful**: the member who asked, or a member with *Manage Messages*, can click the button. The reply is removed. Another member gets `⛔ Only the person who asked or a moderator can remove this answer.` The button works for 24 hours after the reply.

## Limits

These are the limits of the [dashboard](../website/dashboard/faq.md).

| | Free | Premium |
| - | ---- | ------- |
| Groups | 1 | 5 |
| Channels per group | 3 | 10 |
| Questions per group | 5 | 150 |
| Question length | 200 characters | 200 characters |
| Answer length | 1800 characters | 1800 characters |

A channel can belong to one group only.

## Messages of /ask

| Message shown | What to do |
| ------------- | ---------- |
| `This server has no FAQ yet. A moderator can create one on the dashboard.` | Ask a moderator to create a group on the dashboard. |
| `This channel is not linked to a FAQ. Choose a group with the group option.` | Use `/ask` with the `group` option, or ask a moderator to link the channel. |
| `FAQ group not found.` | The group was deleted or renamed. Pick a group from the suggestions. |
| `I did not find an answer in the FAQ. Try other words or ask the moderators.` | Try other words, or ask a moderator. |
| `The translation api seems to be inaccessible. Please try again later.` | The bot could not reach its analysis service. Try again later. |

{% hint style="info" %}
Automatic replies only use the entries of the group, and only when the question is close enough. If the bot never answers, read [FAQ guides](faq-guides.md#why-does-the-bot-never-answer-automatically).
{% endhint %}
