---
description: "Reaction roles page of the dashboard: the list of panels, the editor (the message and its choices on the left, the settings tabs Choice, Rules and Replies on the right), saving and publishing."
---

# Reaction roles

The Reaction roles page builds the panels with which members pick their roles. How the feature works, the modes, the permissions and the safety rules are explained in [Reaction roles](../../management/reaction-roles.md).

Navbar > category _**Management**_ > _**Reaction roles**_.

## The list

Each panel is a row with its name, its channel, its kind (emoji, buttons, dropdown), its number of choices and its state:

* **Draft**: not published yet. Nothing exists on Discord.
* **Published**: the message is on Discord and up to date.
* **Changes not published**: you saved changes, the message does not have them yet.
* **Off**: the panel is turned off (its choices answer _no longer available_).

The switch of a row turns the panel on or off at once. _**Edit**_ opens the editor, the copy icon duplicates the panel (as a draft) and the bin deletes it after a confirmation (the message is removed, members keep their roles). The title bar switch turns the whole feature on or off.

## The editor

The header has the **back arrow**, the **name** of the panel (click to rename) and three buttons:

* _**Discard**_: goes back to the saved version.
* _**Save**_: keeps your changes without touching the message.
* _**Publish**_ (_**Update the message**_ once published): saves, then writes or edits the message. The button stays gray while something is missing; pressing it then shows what.

A list at the top says what prevents publishing (no channel, a choice without role, an emoji used twice, a role the bot cannot give…). After a refused _Publish_, the first choice to fix opens in the settings.

The editor has two columns (one under the other on a phone).

### The message (left)

A Discord channel with its message, as members will see it:

* **Channel**: the text channel of the message (top bar). For an emoji panel you can choose _**Existing message**_: paste the ID or the link of the message, and the bot only adds the reactions to it.
* **Role templates**: the _**Role templates**_ list next to the type of choices builds a **complete panel** in one click: _Colors_, _Continents_, _Zodiac signs_, _Platforms_, _RPG roles_, _Pronouns_, _League of Legends_ and _Notifications_. A template **replaces the content** of the panel (choices, name, title, text, color of the message) with a ready message: a title, a sentence and a **legend** that tells what each emoji gives (`🔴 | Red`). The **bot creates the missing roles** on your server (the colors template gives each role its color); a role that already has the same name is used as it is. If the bot cannot (it lacks _Manage Roles_, or the server is at Discord's limit of roles), the choices stay and you pick their roles yourself. Another template replaces the first one, and the arrows at the top of the message undo it.
* **Type of choices**: _Emoji_, _Buttons_ or _Dropdown_, with the counter of choices (how many you can still add).
* **The message** is the [message builder](message-builder.md) of the dashboard (the same as for [temp voice](temp-voice.md)): you write the message where it will appear. _Card_ (one block, the choices inside), _Embed_ (the classic Discord embed: author with icon, fields side by side, footer icon, time; up to ten embeds), _Blocks_ (a free layout: texts, image galleries, sections, separators, link buttons, and the place of the choices) or _Plain message_ (only text). Images are set by link or by drag and drop. _Preview_ shows the message exactly as Discord displays it, _Add_ adds what is missing (text above, author, thumbnail, image, field, footer, time), the color bar is on the right. The text of the title can be a link: the **title link** makes the title clickable in Discord.
* **The choices are edited in the message itself**: write the label inside a button (or in the open list), click _+_ to add a choice, the small cross on a choice removes it. A click on a choice selects it, and its settings open on the right. A red dot marks a choice to fix.

### The settings (right)

Three tabs:

* **Choice**: the selected choice. Its emoji, its label (buttons and dropdown), the roles it gives, the arrows to reorder and the bin to delete it. _More options_ opens the description (dropdown), the color of the button and the **duration** of the role.
* **Rules**: _Allow members to take several roles_ (off: one role of the panel at a time), the mode (with an explanation and an example), the maximum number of roles per member, and _Allowed roles_ / _Denied roles_ (who can use the panel).
* **Replies**: _Private message_ or _Nothing_, and your own texts for _role given_ and _role removed_.

## Messages of the page

* _The role X is above the role of the bot_: move the role of the bot higher in Server settings > Roles.
* _The role X has dangerous permissions_: a panel never gives such a role (the same list as for the roles the bot gives on its own: administrator, manage server, roles, channels, webhooks, messages, nicknames, expressions, events and threads, kick, ban, timeout, mention everyone, view audit log, mute, deafen and move members).
* _The bot cannot write in this channel_ (or see it, embed links, add reactions): fix the permissions of the channel.
* _The bot does not answer right now_: try again in a moment.
