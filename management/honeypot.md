---
description: "Honeypot: trap channels that catch spam bots and remove them, how it works, setup, sanctions, exceptions, reports, history, the false-alarm protection, permissions and limits."
---

# Honeypot

A honeypot is a **trap channel**: a channel that every member can see and write in, but that no real member has a reason to write in. Spam bots and hacked accounts post in every channel they can see. The first message they send in the trap is enough for the bot to **punish** them, for example by kicking them and deleting their recent messages.

* Settings on the website: [Honeypot](../website/dashboard/honeypot.md).
* Permissions the bot needs: [Permissions needed](#permissions-needed).
* Setup: [Set up in 2 minutes](#set-up-in-2-minutes).

## How it works

1. The bot posts a **warning** in the trap channel and **pins** it. It tells a real person not to write there.
2. A spam bot writes a message in the trap channel.
3. The bot applies the **sanction** of the server (see [Sanctions](#sanctions)). It deletes the message that triggered the trap. With the sanction _**Kick and clean up**_, it also deletes the messages the member posted in the last hours, in every channel where it can.
4. The catch is added to the **history** of the dashboard, with the message as evidence. If the server set a **log channel**, the catch is also posted there as a report.

Nothing happens on a server until its administrators turn the honeypot on. The bot only reads the messages it already receives.

## Set up in 2 minutes

1. **Invite the bot with the permissions of the feature.** The list is in [Permissions needed](#permissions-needed). The bot invitation link of the website includes them.
2. **Open the dashboard**, section _**Management**_ > _**Honeypot**_, tab _**Status**_.
3. **Create or choose a trap channel.**
   * Click _**Create #honeypot**_. The bot creates a `#honeypot` channel that everyone can see and write in, with threads closed.
   * Or choose an existing text channel in the list and click _**Add**_.

   Each addition is applied at once. The bot posts and pins the warning in the channel.
4. **Choose the sanction** in the tab _**Settings**_. The default is _**Kick and clean up**_. To test the trap first, choose _**Only report**_.
5. **Turn the honeypot on.** On the tab _**Status**_, switch the toggle on, then click _**Save**_ in the bar at the bottom of the page. A trap channel is needed first.
6. **Check the status.** When everything is ready, the status reads _The honeypot is watching_.

Optional: choose a **log channel** and a **role to mention** in the tab _**Settings**_ (section _**Reports**_), so that your team is told about each catch.

## Sanctions

The sanction is what the bot does to a member who writes in a trap channel.

| Sanction | What the bot does |
| --- | --- |
| _**Kick and clean up**_ (default) | Kicks the member and deletes their messages of the last hours in the channels where it can. A real person caught by mistake can join again. |
| _**Only report**_ | Does not kick, ban or time out. It only reports the catch. Ideal to test the trap first. |
| _**Ban**_ | Bans the member and deletes their messages of the last hours. For servers raided by bots that come back. |
| _**Timeout**_ | Mutes the member for the timeout length (default 24 hours) and lets the moderators decide. |

Notes:

* The message that triggered the trap is deleted in every case, including _**Only report**_.
* With _**Kick and clean up**_ and _**Timeout**_, the bot deletes the member's messages of the last hours (default 24 hours) in up to 80 text channels, with a budget of 25 seconds for the whole cleaning.
* If the member has a role higher than the bot's top role, the bot cannot punish them. The catch is recorded as failed, with the reason _the member has a role above the bot_.
* To set _**Kick and clean up**_, _**Ban**_ or _**Timeout**_, the person who saves the settings must have the matching Discord permission themselves: Kick Members, Ban Members or Timeout Members. Otherwise the dashboard refuses the save and says so.

## Exceptions

Some people are **never punished**, even if they write in a trap channel:

* the owner of the server;
* members with Administrator, Manage Server, Kick Members, Ban Members, Timeout Members or Manage Messages;
* bots;
* the **exempt roles** and **exempt members** that the server listed in the dashboard.

A moderator who posts in a trap is never treated as a spam bot. To test the trap, post with an account that has none of these permissions, or use _**Only report**_.

## Reports

When a log channel is set, each catch is posted there as an embed titled _Honeypot: member caught_. It shows the member, the date their account was created, the date they joined, the trap channel, the message, the sanction and the result.

If a **role to mention** is set, the role is mentioned in each report. Only that role is mentioned.

The bot also posts a notice in the log channel when a trap channel is deleted, and when the honeypot pauses itself (see below).

## Pinned warning

The warning is the message pinned in each trap channel. It has three modes, chosen in the tab _**Warning**_ of the dashboard:

* _**Standard**_ (default): the bot's own text, in the language of the server.
* _**Custom**_: your own title, text, footer and color.
* _**None**_: no warning is posted. Without a warning, a real person has nothing telling them not to write in the channel, so prefer a clear channel name.

The bot updates the warnings when you change the settings. A warning that cannot be posted or pinned is reported in the dashboard (see [Troubleshooting](#troubleshooting)).

## Protection against false alarms

A trap channel that the community really uses would punish real members. The honeypot protects against this:

* a member is considered **established** when they joined the server more than 30 days ago;
* if **3 established members** write in a trap channel within **10 minutes**, the honeypot **pauses itself**. It does not punish them, and the message that caused the pause is not deleted;
* the bot posts _Honeypot paused_ in the log channel, if one is set;
* the dashboard shows _The honeypot is paused_ on the tab _**Status**_.

To start it again, check the trap channel first, then click _**Start again**_ on the tab _**Status**_. The honeypot is then active again.

Other rules:

* a member caught a moment ago (60 seconds) is not punished a second time;
* only normal messages and replies count. Bots are ignored.

## Permissions needed

The bot needs these permissions on the server. The bot invitation link of the website includes them.

| Permission | Used for |
| --- | --- |
| View Channel, Send Messages, Embed Links (in the trap channel) | To post the warning. Without them the warning is missing. |
| Pin Messages | To pin the warning. This is a separate permission from Manage Messages. Without it the warning is posted but not pinned. |
| Manage Messages | To delete the message that triggered the trap, delete the old warning, and clean up the member's messages. |
| Read Message History (in the channels to clean) | To find the member's messages to delete. |
| Kick Members | For the sanction _**Kick and clean up**_. |
| Ban Members | For the sanction _**Ban**_. |
| Timeout Members | For the sanction _**Timeout**_. The Discord API calls it Moderate Members. |
| Manage Channels | Only for _**Create #honeypot**_. |

The bot's top role must be above the roles of the members it punishes.

## Limits

| Option | Limit |
| --- | --- |
| Trap channels | 5 per server |
| Exempt roles | 50 per server |
| Exempt members | 100 per server |
| History shown | The last 20 catches |
| History kept | 30 days. Older catches are erased every day. |
| Message kept as evidence | The first 300 characters |
| Messages deleted | 0 to 168 hours (default 24) |
| Timeout length | 1 to 672 hours (default 24) |

## Free or premium

The honeypot is **free for every server**. All the options above are available to all servers, and no premium plan or top.gg vote is needed.

## Troubleshooting

| Message in the dashboard | What to do |
| --- | --- |
| _The honeypot cannot work yet_ | A check failed. The list under the status shows which one, and how to fix it. |
| _The bot does not answer right now_ | The bot cannot be reached, so its permissions are not checked. Try again in a moment. |
| _This channel no longer exists_ | Remove the channel and add another one. |
| _Members cannot see this channel_ | Everyone must see the trap channel, or a bot that cannot see it will never fall in it. |
| _Members cannot write here_ | Everyone must be able to write in the trap channel, or nobody can fall in it. |
| _The bot cannot post in this channel_ | Give the bot View Channel, Send Messages and Embed Links in this channel. The warning is missing until then. |
| _The bot lacks the Pin Messages permission here_ | The warning is posted but not pinned. Give the bot Pin Messages. |
| _The honeypot is paused_ | Check the trap channel, then click _**Start again**_. |
| Catches show _Failed_ | Open the catch in the history. The reason is written under _Why it failed_. |
| No report arrives | Check that a log channel is set, and that the bot can send messages there. |

Errors when saving:

| Message | Meaning |
| --- | --- |
| _Add a trap channel before turning the honeypot on._ | The honeypot needs at least one trap channel. |
| _The log channel must be a text channel of this server._ | Choose a text channel. |
| _One of the roles no longer exists._ | Remove the role from the exceptions or the mention. |
| _Too many exempt roles or members for this server._ | Remove some entries. |
| _To use this action you need the matching Discord permission yourself._ | You do not have the permission of the sanction. Choose another sanction, or ask someone who has it. |

## Commands

The honeypot has no slash command. It is set up on the [dashboard](../website/dashboard/honeypot.md) only.
