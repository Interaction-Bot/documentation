---
description: Questions and answers about the FAQ, /ask and the automatic replies, from A to Z.
---

# FAQ guides

This page answers the questions moderators and members ask most about the FAQ, `/ask` and the automatic replies. For the list of commands, see [FAQ and /ask](faq.md). For the settings, see the [FAQ dashboard page](../website/dashboard/faq.md).

## Setting up

### What is a FAQ group?

A group is a set of questions and answers (called **entries**) that the bot uses in some channels. A channel is linked to a group, and the bot only uses the group of the channel where a question is asked. A server can have several groups, for example one for the rules and one for technical support.

### How many groups, channels and questions can I have?

| | Free | Premium |
| - | ---- | ------- |
| Groups | 1 | 5 |
| Channels per group | 3 | 10 |
| Questions per group | 5 | 150 |

Limits are checked by the dashboard and by the bot when you save. See [Premium](../premium/premium.md) for the full list.

### How do I create a group?

Groups are created on the dashboard, or in Discord with the **Create a group** button of `/faq manage`. `/faq add` needs an existing group, and `/faq list` tells you to create one when there is none.

1. Open the [FAQ](../website/dashboard/faq.md) page and click **Create group**.
2. Give it a name (up to 40 characters, unique).
3. Choose the channels where the bot uses this group.
4. Add the questions and answers, then click **Save**.

### Can a channel belong to two groups?

No. A channel belongs to one group at most. To move a channel to another group, select it in the new group on the dashboard and save: the dashboard removes it from the old group in the same save.

### Can I use threads?

Yes. A thread uses the group of its parent channel, so questions asked in a thread are handled as if they were asked in the channel.

### Can I rename a group or delete one?

Yes, on the dashboard. Change the name and save. Deleting a group also deletes its channels and its questions, so keep a copy of the answers you need.

### Do my changes apply at once?

When you save on the dashboard, the bot is told to reload the FAQ of your server at once. If the bot cannot be reached at that moment, your changes are still saved, but they may take longer to apply. See [I changed the FAQ, but /ask still shows the old answer](#i-changed-the-faq-but-ask-still-shows-the-old-answer).

## Questions and answers

### How long can a question and an answer be?

A question can be up to **200 characters**, and an answer up to **1800 characters**. The dashboard and the `/faq add` form both enforce these limits.

### How do I write a good question?

The bot compares the **meaning** of a member's message with your questions, so you do not need to copy the exact words. Still, clear questions give better results:

* **Write one question per entry**, about one topic.
* **Write it the way members ask it**, as a full sentence: *How do I get the Developer role?* is better than *Developer role*.
* **Make the question self-contained**: avoid *as explained above* or *this*.
* **Keep it distinct**: two questions that say almost the same thing make both entries unusable for automatic replies (see [Why does the bot never answer automatically?](#why-does-the-bot-never-answer-automatically)).
* **Stay under 200 characters.** Very short questions such as *Roles?* are weak matches.

| Weak entry | Better entry |
| ---------- | ------------ |
| `Roles?` | `How do I get the Developer role?` |
| `How do I get the role?` and `How do I get the Developer role?` (two entries) | Keep only the more specific one, or make the two questions clearly different: `How do I get the Developer role?` and `How do I get the Beta tester role?` |
| `Rules` | `Where can I read the server rules?` |

### How do I write a good answer?

* Put the most useful information **first**: the answer is shown in an embed, and members often read only the start.
* Keep it **short and complete**: one answer should be enough without the other entries.
* Add **links** and **channel mentions**, such as `<#123456789012345678>` (the number is the channel ID). They are kept when the answer is translated.
* Do not rely on a language: write answers in the language of your server. Members who ask in another language still get the answer, translated.

### Are answers translated?

Yes, when needed. The answer is sent in the language of the question. When the language of your answer was not detected reliably when you wrote it, the bot sends it as you wrote it. If the translation fails, the bot also sends your original text.

Discord mentions, custom emojis, channel links and URLs are protected during the translation, so they stay correct.

### Why is my answer shown in another language?

Either the translation failed, or the language of the answer was not detected reliably when the entry was saved. Check that the answer is written in one clear language, and save it again.

### Can I edit an entry?

Yes, on the dashboard: change the question or the answer, then save. When you change a question, the bot recomputes the search data of that question automatically.

### Can members see all the questions?

Not with `/ask`: a member only sees the answer to the question they asked, and the questions that also match (under **See also**). The full list is for moderators: `/faq list` (*Manage Server* permission).

## /ask

### Who can use /ask?

Everybody. `/ask` is only visible to the member who uses it.

### How many answers can /ask show?

The best match is shown as the answer. Up to two other matching questions can be listed under **See also**. When the meaning-based search is available, only matches above the group's minimum confidence are shown.

### Why does /ask say that I did not find an answer?

The FAQ has no question close enough to your question, in the group that was searched. Try other words, check that the question is in the right group, or lower the minimum confidence on the dashboard (between 80% and 95%).

### Does /ask search all my groups?

No. `/ask` searches **one** group: the group of the channel where you type it, or the group you choose with the `group` option.

### Can I ask a question in any language?

Yes. Your question can be in any language, and the bot matches it with the questions of the group.

### Is there a limit on how often I can ask?

Yes: each member can use `/ask` once every 10 seconds. The question can be up to 300 characters.

### What happens if the meaning-based search is unavailable?

`/ask` falls back to keyword matching: it finds questions that share words with yours. Results are less precise than the meaning-based search. If the bot cannot analyze your question at all, `/ask` replies `The translation api seems to be inaccessible. Please try again later.`

## Automatic replies

### How do I turn on automatic replies?

On the dashboard, open the group and switch **Auto reply** on, then save. It is **off** by default. Automatic replies are set per group, and only work in the channels of that group.

### Which messages can get an automatic reply?

A message can get an automatic reply when it:

* is written by a member (not a bot, a webhook or a command starting with `/` or `!`),
* has at least **4 words** (links, custom emojis and mentions are not counted),
* is posted in a channel of a group that has auto reply on.

Messages that are only links, emojis or mentions are ignored.

### How does the bot decide to answer?

The bot compares the message with the questions of the group and gives each one a score. It answers only when:

1. the best score reaches the **minimum confidence** of the group, and
2. the best score is clearly above the second one (by at least 3 points), so that the answer is not a guess between two close questions.

If one of these is not true, the bot stays silent.

### What is the minimum confidence?

It is the score an entry must reach to be used, between **80%** and **95%** (84% by default). The percentage shown in the footer of an automatic reply is that score.

* **Higher** (for example 92%): fewer replies, but only for very close questions.
* **Lower** (for example 82%): more replies, with a higher risk of an answer that does not fit the question.

Start with the default value, and change it only after you read some automatic replies.

### What is the "two close answers" rule?

If two entries match almost equally well, the bot does not know which one is right, so it does not answer. Write distinct questions to avoid it (see [How do I write a good question?](#how-do-i-write-a-good-question)).

### Why does the bot never answer automatically?

Check these points, in order:

1. **Auto reply is off** for the group on the dashboard.
2. **The channel is not in the group**, or the channel belongs to another group.
3. **The messages are too short** (fewer than 4 words), or they start with `/` or `!`, or they are written by a bot.
4. **The minimum confidence is too high** for your questions. Try a lower value.
5. **Two entries are almost identical**, so the bot stays silent. Make them distinct.
6. **The bot lacks permissions** in the channel: it needs *Send Messages* and *Embed Links* (and *Send Messages in Threads* in threads). Run `/check-permissions`.
7. **Too many messages in a short time.** Automatic replies are rate limited per server and across the bot, and the bot skips them rather than answer late.
8. **The search service is unavailable.** Without it, only messages that repeat almost all the words of a question are answered.

### What is the "Not helpful" button?

Under an automatic reply, the **Not helpful** button removes the reply. It can be used by:

* the member who wrote the message that got the reply,
* a member with the *Manage Messages* permission (a moderator).

Any other member sees `⛔ Only the person who asked or a moderator can remove this answer.`. The button works for **24 hours** after the reply.

### Can a moderator remove a wrong answer?

Yes. Click **Not helpful** as a moderator, or change the entry on the dashboard (fix the answer, or delete the question). The change is used at once.

## Permissions and limits

### Which permissions does the bot need?

| Feature | Permissions |
| ------- | ----------- |
| `/ask` and `/faq` | None in the channel: the answers are sent privately to the member. |
| Automatic replies | *Send Messages* and *Embed Links* in the channel, plus *Send Messages in Threads* in threads. |

Run `/check-permissions` to see the missing permissions of every configured channel. See [Permissions](../permissions.md) for the full list.

### Who can manage the FAQ?

Members with *Manage Server* can use `/faq`, and the dashboard can be used by members with *Administrator*. Anybody can use `/ask`.

### How are the automatic replies limited?

To protect the bot and your server, the search for automatic replies is limited:

* per server: a short burst, then about one search every 5 seconds,
* for the whole bot: about 30 automatic replies per minute.

When a limit is reached, the bot stays silent for that message.

### What happens when Premium ends?

Nothing is deleted. The limits of the free plan apply again:

* **Groups**: only the oldest groups keep working. The newest groups are switched off, but kept. Switch one on again only when you have fewer groups than the free limit.
* **Channels**: only the first channels of each group (sorted by channel ID) are used. The others are ignored, but kept.
* **Questions**: only the first questions of each group (in the order they were added) are used. The others are kept, but not used.

The dashboard does not let you add groups, channels or questions beyond the free limits. Remove the extra ones before you add new ones.

### Is the FAQ shared between servers?

No. Each server has its own FAQ, groups and questions.

## Troubleshooting

### The bot answers with the wrong question.

Make your questions more distinct, and check that the wrong question is not in the same group as the right one. If the match is still weak, raise the minimum confidence of the group.

### /ask says that the channel is not linked to a FAQ.

The channel does not belong to any group. Add it to a group on the dashboard, or use `/ask` with the `group` option.

### I changed the FAQ, but /ask still shows the old answer.

Changes made on the dashboard are sent to the bot right away. If the bot could not be reached at that moment, the changes may take longer to apply. Save the configuration again on the dashboard, and if the old answer persists, contact the [support server](https://discord.gg/wjWjf6mCjf).

### /faq list shows `No entry yet.` for my group.

The group has no question. Add questions on the dashboard, or with `/faq add` (the form), then run `/faq list` again.

### The bot does not reply to a question in a group channel, but /ask finds it.

`/ask` and automatic replies do not use the same rules. `/ask` accepts shorter questions and does not need the channel permissions. Automatic replies need the checks listed in [Why does the bot never answer automatically?](#why-does-the-bot-never-answer-automatically).
