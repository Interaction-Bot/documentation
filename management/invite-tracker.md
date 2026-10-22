---
description: "Invite tracker: which invite brought each new member, the totals and ranking per inviter, the journal, manual corrections, the commands /invites and /invite-leaderboard, and the privacy of the data."
---

# Invite tracker

The invite tracker tells you **who invited each new member**. For each arrival, the bot finds the invite that was used. The arrival is counted for the member who created that invite.

The tracker is **off** by default. Nothing is recorded for a server until an administrator turns it on.

* Settings, rules and ranking on the website: [Invitations (dashboard)](../website/dashboard/invites.md).
* Welcome messages that name the inviter: [Welcome and goodbye](welcome-and-goodbye.md).
* Permissions the bot needs: [Permissions needed](#permissions-needed).

## How it works

1. An administrator turns the tracker on in the dashboard, in _**Management**_ > _**Invitations**_.
2. The bot keeps in memory the number of uses of every invite of the server.
3. A member joins. The bot reads the invites again. The invite whose use count went up is the one the member used.
4. The bot records the arrival (member, invite, inviter, date) and adds one to the inviter's **joined** count.
5. When the member leaves, the bot adds one to the inviter's **left** count.

The bot never guesses. When no invite, or more than one invite, can explain the arrival, the journal shows **Invite not found**. No one gets the point. See [Why an arrival is not attributed](#why-an-arrival-is-not-attributed).

### How a total is computed

**Total = joined - left - fake + added**

| Count | Meaning |
| --- | --- |
| Joined | Arrivals of the members this inviter brought. |
| Left | Departures of those members. A departure of a fake account is not counted. |
| Fake | Arrivals of very recent accounts (see [Fake accounts](#fake-accounts)). |
| Added | The sum of the corrections made by hand, without the undone ones (see [Corrections](#corrections)). |

The total is what the ranking and `/invites` show.

### Returning members

A member who leaves and comes back is handled in one of two ways:

* **Default:** the first inviter keeps the point. The departure is cancelled, and the return is listed as **Came back to the server** in the journal. The total does not change.
* **Do not count returning members** turned on: the return counts as a fake account for the inviter. The point lost when the member left is not given back.

Only the returns that the bot has seen are recognized.

### Fake accounts

An account younger than the **Fake accounts: younger than** value (default 3 days) when it joins is a fake account. Its inviter gets the arrival and one fake count, so the total does not change. Setting the value to 0 turns this filter off. The maximum is 300 days.

### Inviters and roles that earn nothing

* An **inviter who earns nothing** is listed by hand. Their invitees are still written in the journal, but nobody gets the point for them.
* A **role that earns nothing** is set in the settings. Someone who has this role when a member joins earns nothing for that member. This check is not retroactive: the points earned before are kept.

The welcome messages are not affected by these rules.

## Set up in a few minutes

1. **Give the bot the Manage Server permission.** Without it, the bot cannot read the invites. See [Permissions needed](#permissions-needed).
2. **Open the dashboard**, _**Management**_ > _**Invitations**_ (see [Invitations (dashboard)](../website/dashboard/invites.md)).
3. **Turn the toggle on** on the _**Status**_ tab, then click _**Save**_ in the bar at the bottom of the page.
4. **Check the lights** on the _**Status**_ tab. When every check is green, the page says _Invite tracking is working_.
5. **Optional:** name your invites and give them a role in the _**Rules**_ tab, and add `{inviter}` to your welcome message.

Only the arrivals after the tracker is turned on are counted. Members who joined before are not in the totals.

## Commands

| Command | What it does |
| --- | --- |
| `/invites [user]` | Shows how many people a member invited: the total, and the joined, left, fake and added counts. The member is you by default. Only you see the answer. |
| `/invite-leaderboard` | Shows the top 10 inviters of the server. Members hidden from the leaderboard are left out. The answer is public, in the channel. |

Both commands need no permission to use. When the tracker is off, they answer that it is off on this server.

## Variables for the welcome message

These variables can be used in the texts of the Welcome page, see [Welcome and goodbye](welcome-and-goodbye.md).

| Variable | Shows |
| --- | --- |
| `{inviter}` | The inviter. In a text message, a mention. On the welcome card, the name. |
| `{inviter.name}` | The display name of the inviter. |
| `{invites}` | The current total of the inviter, with separators (for example 1,234). |
| `{invite_label}` | The label of the invite that was used (see [Invite labels](#invite-labels)). |

When the tracker is off, or does not know the arrival:

* `{inviter}` and `{inviter.name}` show `unknown`.
* `{invites}` shows `0`.
* `{invite_label}` shows the label of the invite if it has one, and `unknown` if not. A label can be shown even when the inviter is not known, for example for the custom link of the server.

## Invite labels

A label gives a name to one invite. It tells you where people come from, for example _Partners_ or _Summer event_.

* The invite can be a code or a link (`discord.gg/abc` or `abc`), or `vanity` for the custom link of the server.
* The label can have up to 60 characters.
* The label can give a **role**. Everyone who arrives with this invite gets the role when they join. The role comes on top of the automatic roles of the Welcome page.

The bot gives the role only when Discord allows it. If the bot lacks the Manage Roles permission, or the role is not below the bot's highest role, the member gets no role. The arrival is still recorded.

Labels are set in the _**Rules**_ tab of the dashboard, see [Invitations (dashboard)](../website/dashboard/invites.md#rules).

## Corrections

A correction changes the total of one member by hand. Use it for an event, or to fix a mistake.

* Add or remove up to 1000 invitations at a time. The amount cannot be 0.
* A reason of up to 200 characters is optional. It is shown in the list of corrections.
* A correction can be undone. The total then goes back to the value it had without this correction.

Corrections are set in the _**Corrections**_ tab of the dashboard. They are part of the total, and `/invites` shows them as _added by hand_.

## Privacy

Nothing is recorded while the tracker is off. When it is on, the tracker keeps the following data.

| Data | Kept until |
| --- | --- |
| **Journal**, one line for each arrival: member ID, inviter ID, invite code, kind of arrival (invite, custom link, not found, came back, or counted for nobody), date of arrival, date of departure, date the account was created, fake flag. | The retention you chose: 30, 90, 180 or 365 days. The old lines are erased once a day. |
| **Counts per inviter**: joined, left and fake. | A reset, see the dashboard page. |
| **Corrections**: member ID, amount, reason, date, and the ID of the dashboard user who made it. | A reset. An undone correction stays in the list, marked as undone, until a reset. |
| **Settings**: the options, the lists of members, the labels (invite code, label text, role ID). | Until they are changed. |

The use counts of the invites are kept in the bot's memory only. They are not saved. They are lost when the bot restarts.

**Members who refused the tracking** are counted for their inviter, but the journal does not show their name. The journal shows _A member who keeps their data private_ for them.

**Reset** erases all the counts and all the corrections of the server. The journal is not erased by a reset. It is erased when its retention ends. A reset cannot be undone.

## Limits

| Item | Limit |
| --- | --- |
| Retention of the journal | 30, 90 (default), 180 or 365 days |
| Age of the account for a fake account | 0 to 300 days (default 3) |
| Roles that earn nothing | 20 |
| Inviters who earn nothing | 100 |
| Members hidden from the leaderboard | 100 |
| Invite labels | 100 |
| Corrections at once | From -1000 to 1000, not 0 |
| Reason of a correction | 200 characters |
| Name of a label | 60 characters |
| `/invite-leaderboard` | Top 10 |
| Ranking and journal in the dashboard | 25 lines per page |
| Corrections in the dashboard | The last 50 corrections |

The tracker is free for every server. The limits above are the same for every server.

The tracker only sees what Discord tells it about the invites. It cannot see how a member joined when Discord does not link the arrival to an invite.

## Why an arrival is not attributed

The journal shows **Invite not found** when the bot cannot tell which invite was used. The bot does not guess in these cases:

* **Two or more invites** have a higher use count at the same time. The bot cannot tell which one was used.
* **No invite** has a higher use count. The member joined in a way that is not linked to an invite.
* **The first arrival after the bot starts**, or after the tracker settings are saved. The bot has no earlier count to compare with, so the arrival is not attributed.
* **The bot cannot read the invites.** It lacks the Manage Server permission, or Discord refuses to answer. The state of the tracker then shows a red light on the _**Status**_ tab.
* **The bot was offline** when the member joined or left. The bot does not see these events.

To fix a total that is wrong, use a correction. Labels and corrections are the way to keep the counts right.

## Troubleshooting

| What you see | What to do |
| --- | --- |
| _Invite tracking is on but cannot work yet_ on the _**Status**_ tab | Read the red lights. For the permission, give the bot **Manage Server**. For the member or invite events, contact support: these are set by Interaction Bot. |
| _The bot does not answer right now, so its state cannot be checked._ | The bot could not be reached. Try again later. |
| `/invites` says that the tracker is off | Turn the tracker on in the dashboard, then save. |
| Many arrivals show **Invite not found** | See [Why an arrival is not attributed](#why-an-arrival-is-not-attributed). |
| A total is wrong | Correct it in the _**Corrections**_ tab. |
| The welcome message shows `unknown` | The arrival is not attributed, or the tracker is off. |
| A member does not get the label role | The bot lacks Manage Roles, or the role is above the bot's highest role. Check the order of the roles. |
| `/invite-leaderboard` is empty | No inviter has a total above zero yet. Hidden members are not shown by this command. |

## Permissions needed

| Permission | Why the bot needs it |
| --- | --- |
| **Manage Server** | Reads the invites of the server. Without it, no arrival is attributed. |
| **Manage Roles** | Gives the role of an invite label. The Welcome page also uses it. |

The bot also needs to receive the invite events, which Interaction Bot enables. The **Server Members** intent is needed to see the arrivals and the departures of members. It is also set by Interaction Bot. The lights on the _**Status**_ tab show whether these events work.
