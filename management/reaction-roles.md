---
description: "Reaction roles: let members pick their own roles with emojis, buttons or a dropdown, how it works, the modes, the filters, temporary roles, the safety rules, permissions and limits."
---

# Reaction roles

A **reaction role** panel is a message of the bot with a list of choices. Each choice gives or removes one or more roles. Members pick their roles themselves, with **emojis**, **buttons** or a **dropdown**.

* Settings on the website: [Reaction roles](../website/dashboard/reaction-roles.md).
* Permissions the bot needs: [Permissions needed](#permissions-needed).
* Setup: [Set up in 3 minutes](#set-up-in-3-minutes).

## How it works

1. You build a panel in the dashboard: the channel, the message, the choices (each with an emoji, a label and the roles it gives) and the rules.
2. You press _**Publish**_. The bot writes the message in the channel (or, with emojis on an existing message, only adds the reactions).
3. A member uses a choice. The bot checks the rules, gives or removes the roles and answers in private.
4. You can edit the panel later and press _**Update the message**_: the message is edited in place, and the members keep the roles they already have.

A panel exists on Discord only after _**Publish**_. _**Save**_ keeps your changes without touching the message.

## Set up in 3 minutes

1. **Give the bot the permission _Manage Roles_** and put the role of the bot **above** the roles it gives (Server settings > Roles). The bot cannot give a role that is above its own.
2. Open the dashboard, section _**Management**_ > _**Reaction roles**_ and turn the page on.
3. Click _**New reaction role**_, pick a channel, write the message, add the choices.
4. Press _**Publish**_.

## The three kinds of choices

| Kind | What members see | Limit |
|---|---|---|
| **Emoji** | Reactions under the message. Also works on a message that already exists. | 20 per message (Discord's limit) |
| **Buttons** | Colored buttons (gray, blue, green, red), each with an emoji and a label. | 25 |
| **Dropdown** | A dropdown menu with a label, a description and an emoji for each choice. | 25 |

## Reaction modes

The mode says what happens when a member uses a choice.

| Mode | What it does | Good for |
|---|---|---|
| **Normal** | The first use gives the role, the next one takes it back. | Ping roles, games, optional channels. |
| **Add only** | The panel only gives the role. Using it again does not remove it. | Accepting the rules, getting access. |
| **Remove only** | The panel only removes the role, it never gives it. | Leaving a channel or a group. |
| **Final choice** | One choice, once: as long as the member has a role of the panel, they cannot change it. | Teams, houses. |
| **Reversed** (emoji only) | Adding the reaction removes the role, removing the reaction gives it back. | Hiding channels: reacting hides them. |

Two more settings apply to every mode:

* **Allow members to take several roles** (on by default). When it is off, a member keeps **one role of the panel at a time**: picking another choice replaces the previous one (with emojis, the previous reaction is removed too).
* **Roles per member**: the most choices of the panel a member can hold at once (0 = no limit).

## Who can use a panel

* **Allowed roles**: when you pick roles, only members who have **at least one** of them can use the panel.
* **Denied roles**: members who have **one** of these roles cannot use the panel.
* A panel can be turned off without deleting it: its buttons then answer _no longer available_ and change nothing.

## Temporary roles

Each choice can give its roles for **1 hour up to 30 days**. The bot takes the roles back by itself, even after a restart. A role given this way is taken back at the end of the time even if the member used the choice again.

## Answers to the member

* **Private message** (default): with buttons and dropdowns, an answer only the member sees; with emojis, a private message (nothing happens if the member closed their private messages).
* **Nothing**: the bot gives or removes the role without confirming. A refusal is always told.
* You can write your own texts for _role given_ and _role removed_. `{role}` stands for the roles concerned. Without your own text, the bot answers in the language of the server.

## Safety rules

* The bot only gives a role that is **below its own role**, that is not managed by an integration (bot, boosts…) and that is not `@everyone`.
* A role with **dangerous permissions** can never be given by a panel: Administrator, Manage Server, Manage Roles, Manage Channels, Manage Webhooks, Manage Messages, Manage Nicknames, Manage Expressions, Manage Events, Manage Threads, Kick Members, Ban Members, Timeout Members, Mention Everyone, View Audit Log, Mute Members, Deafen Members, Move Members (the same list as for the roles the bot gives on its own). The bot checks again at **every** use: a permission added to the role later blocks it. Removing a role is always allowed.
* A member can use a choice **once per second** at most.
* The dashboard tells you before you publish when a role or the channel does not work (role too high, dangerous role, missing permission).

## Permissions needed

| Permission | Why |
|---|---|
| Manage Roles | Give and remove the roles. |
| View Channel, Send Messages, Embed Links | Write the message of the panel. |
| Add Reactions, Read Message History | Emoji panels (the bot adds the reactions). |
| Manage Messages | Remove the reaction of a member after an _Add only_, _Remove only_ or _one role at a time_ choice (optional). |

## Limits

* 50 panels per server.
* 20 choices on an emoji panel, 25 on buttons or a dropdown.
* Up to 10 roles per choice, up to 25 roles in each filter.
* The reply texts hold 300 characters.
