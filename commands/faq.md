---
description: Let your members get answers from a FAQ made by your moderators.
---

# FAQ and /ask

Moderators create a FAQ (questions and answers) for the server. Members use `/ask`, and the bot can also **answer automatically** to questions asked in the channels linked to a FAQ group, in any language.

| Command                         | Description                                                                                                               |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| `/ask <question> [group]`       | Ask a question: the answer comes from the FAQ of the server. By default the group linked to the current channel is used.  |
| `/faq add <group>`              | Add an entry (question and answer) to a group, with a form. Requires *Manage Server*.                                     |
| `/faq list`                     | List the entries of the FAQ groups.                                                                                       |
| `/faq remove <group> <entry>`   | Remove an entry.                                                                                                          |

Groups, linked channels and settings (for example the minimum confidence of automatic replies, between 80% and 95%) are managed on the dashboard, see [FAQ](../website/dashboard/faq.md).

**Good to know**

* A question is 200 characters at most, an answer 1800.
* Automatic replies ignore very short messages (fewer than 4 words) and only answer when the match is confident.
* Only the person who asked, or a moderator, can remove a wrong automatic answer with the "not helpful" button.
* **Limits**: free servers: 1 group, 5 entries per group, 3 channels per group. Premium: 5 groups, 150 entries per group, 10 channels per group.

## Step by step

1. **Create the FAQ** on the dashboard ([FAQ](../website/dashboard/faq.md)): create a group, add questions and answers, link the channels where it is used.
2. Or add entries from Discord: `/faq add group:<name>` opens a form (question and answer).
3. Members type `/ask question:<their question>`. The bot finds the best entry and answers **in the language of the question**.
4. For automatic replies, turn on *Auto reply* on the dashboard: the bot answers by itself in the linked channels when it is confident enough. Raise the minimum confidence (up to 95 %) if it answers too much, lower it (down to 80 %) if it never answers.

## Writing a good FAQ

* One question per entry, written the way a member would ask it ("How do I get the Member role?").
* Add several entries for the same answer if members ask in different ways.
* Keep answers short and complete (1800 characters max): the answer is sent exactly as written, then translated for the reader.
* Test with `/ask` before turning on *Auto reply*.

## Troubleshooting

| Symptom                                   | What to check |
| ----------------------------------------- | ------------- |
| `/ask` does not find the answer           | Add an entry with the wording of the question; check that the channel is linked to the group (or give the `group`). |
| No automatic reply                        | *Auto reply* is on, the message has at least 4 words, the channel belongs to the group, and the confidence is not set too high. |
| A wrong answer was given                  | Use the "not helpful" button (the asker or a moderator), then fix or add an entry. |
| Limit reached                             | Free: 1 group and 5 entries per group. Premium: 5 groups and 150 entries per group. |
