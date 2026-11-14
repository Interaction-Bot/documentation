---
description: "Reaction roles page of the dashboard: the list of panels, the editor sections (Channel, Message, Reactions and roles, Reaction mode, Who can use it, Replies), saving and publishing."
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

A list at the top says what prevents publishing (no channel, a choice without role, an emoji used twice, a role the bot cannot give…).

Sections can be folded. **Channel**, **Message** and **Reactions and roles** are open; the others open on click.

### Channel

Pick the text channel of the message. For an emoji panel you can choose _**Existing message**_: paste the ID or the link of the message, and the bot only adds the reactions to it.

### Message

The message builder of the dashboard (the same as for [temp voice](temp-voice.md)): you write the message where it will appear.

* **Type**: _Card_ (one block, the choices inside the message), _Embed_ (the classic Discord embed: author with icon, fields side by side, footer icon, time) or _Plain message_ (only text).
* **Edit / Preview**: _Preview_ shows the message exactly as Discord displays it, with the Markdown rendered.
* **Add** adds what is missing: text above the message, author, thumbnail, image, field, footer, time. Each part is removed with its cross.
* Images: upload (cropped), an https address, or a variable (server icon, bot avatar).
* The color bar is on the right.

### Reactions and roles

Pick the kind (_Emoji_, _Buttons_, _Dropdown_). _Allow members to take several roles_ turns the "one role at a time" rule on or off. Each choice has an emoji, a label and the roles it gives; _More options_ opens the description (dropdown), the color of the button and the **duration** of the role. The arrows reorder the choices, the bin deletes one. The counter shows how many choices you can still add.

### Reaction mode

The mode (with an explanation and an example) and the maximum number of roles per member.

### Who can use it

_Allowed roles_ and _Denied roles_.

### Replies

_Private message_ or _Nothing_, and, under _Customize the texts_, your own texts for _role given_ and _role removed_.

## Messages of the page

* _The role X is above the role of the bot_: move the role of the bot higher in Server settings > Roles.
* _The role X has dangerous permissions_: a panel never gives such a role.
* _The bot cannot write in this channel_ (or see it, embed links, add reactions): fix the permissions of the channel.
* _The bot does not answer right now_: try again in a moment.
