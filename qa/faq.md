---
description: Let your members get answers from a FAQ made by your moderators.
---

# FAQ and /ask

Moderators create a FAQ for the server: questions and their answers, organized in **groups**. Members use `/ask` to search it. The bot can also **answer by itself** to questions asked in the channels linked to a group, in any language, when it is confident enough of the answer.

The answers are never generated: the bot only sends the answers your moderators wrote. If a question is asked in another language than the answer, the answer is translated, and Discord mentions, channel links and URLs are kept as they are.

| Command | Who | What it does |
| ------- | --- | ------------ |
| `/ask question:<text> [group]` | Everybody | Search the FAQ. The answer is only visible to the member who asked. |
| `/faq add group:<group>` | *Manage Server* | Open a form to add a question and its answer to a group. |
| `/faq list [group]` | *Manage Server* | List the entries, with their numbers. |
| `/faq remove entry:<entry>` | *Manage Server* | Remove an entry. |
| `/faq manage` | *Manage Server* | Open a panel (buttons and menus) to manage the groups and the entries without typing options. See [Configuration commands](../commands/configuration.md#faq). |

Groups, linked channels and the automatic replies are managed on the dashboard, see [FAQ](../website/dashboard/faq.md). For everything step by step, from A to Z, read [FAQ guides](faq-guides.md).

## /ask

Example: a member types `/ask question:How do I change my nickname?` in a channel linked to a group called `Support`.

* If the FAQ has a matching question, the member sees an embed titled **FAQ**, with the answer as its text. The footer says which question matched: `Matched question: How do I change my nickname on this server?`. If other close questions exist, a **See also** field lists them.
* If nothing matches well enough: `I did not find an answer in the FAQ. Try other words or ask the moderators.`

Rules:

* The question can be up to 300 characters, in any language.
* `/ask` searches **one group only**. In a channel linked to a group, that group is used automatically. In any other channel, choose the group with the `group` option.
* A member can use `/ask` once every 10 seconds.
* In a channel that is not linked to any group: `This channel is not linked to a FAQ. Choose a group with the group option.`
* If the server has no FAQ yet: `This server has no FAQ yet. A moderator can create one on the dashboard.`
* Threads use the group of the channel they belong to.

## /faq add

Example: `/faq add group:Support`.

The bot opens a form titled **New FAQ entry** with two fields, **Question** (up to 200 characters) and **Answer** (up to 1800 characters). When you submit it, the bot replies:

```
✅ Entry added. The bot uses it for /ask and for the automatic replies of its group.
```

The new entry is used at once, by `/ask` and by the automatic replies.

## /faq list

Example: `/faq list` (or `/faq list group:Support` for one group).

The bot shows an embed titled **FAQ entries**. For each group, the field title gives the group name and its number of entries, and each line shows the entry number and its question:

```
Support (2)
`12` How do I change my nickname on this server?
`15` Where are the server rules?
```

The first 25 entries of each group are listed. If a group has no entry, it shows `No entry yet.` If the server has no group, it shows `This server has no FAQ group yet. Create one on the dashboard.`

## /faq remove

Example: `/faq remove entry:` then type `nickname`. The list suggests the matching questions, each with its group, for example `How do I change my nickname on this server? · Support`. Pick one.

The reply is `✅ Entry removed.`. If the entry no longer exists, it is `Entry not found.`

## Automatic replies

When automatic replies are on for the group of a channel, the bot can answer a message by itself. The answer is a reply to the message, with:

* the question as its title,
* the answer as its text,
* in the footer, the group name and the confidence of the match, for example `Support · 91%`,
* a grey **Not helpful** button.

Example: a member writes in `#help` *"I cannot find the Developer role anywhere, how do I get it?"*. If the FAQ entry *"How do I get the Developer role?"* matches strongly enough, the bot replies under the message with that entry.

**The bot stays silent** (and does not answer) when:

* the message is from a bot or a webhook, starts with `/` or `!`, has fewer than 4 words, or contains only links, emojis or mentions;
* no entry reaches the group's minimum confidence (80% to 95%, 84% by default);
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

## Errors and what to do

| Message shown | What to do |
| ------------- | ---------- |
| `FAQ group not found.` | The group does not exist anymore, or the name is wrong. Pick it from the suggestions. |
| `A FAQ group with this name already exists.` | Choose another name. |
| `This server reached the maximum number of FAQ groups of its plan.` | Delete a group, or go premium. |
| `This group reached the maximum number of entries of its plan.` | Remove an entry, or go premium. |
| `This group reached the maximum number of channels of its plan.` | Remove a channel from the group, or go premium. |
| `One of these channels already belongs to another FAQ group.` | A channel can belong to one group only. Remove it from the other group first. |
| `The question must contain between 1 and 200 characters.` | Shorten the question. |
| `The answer must contain between 1 and 1800 characters.` | Shorten the answer. |
| `Entry not found.` | The entry was already removed. Run `/faq list` again. |
| `The translation api seems to be inaccessible. Please try again later.` | The bot could not analyze the question (its language detection failed). Try again later. |

{% hint style="info" %}
Automatic replies only use the entries of the group, and only when the question is close enough. If the bot never answers, read [FAQ guides](faq-guides.md#why-does-the-bot-never-answer-automatically).
{% endhint %}
