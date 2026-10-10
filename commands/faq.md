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
