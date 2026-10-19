---
description: Welcome and goodbye messages, private message to new members, banners, automatic roles, variables, limits, permissions and troubleshooting.
---

# Welcome and goodbye

Interaction Bot can greet new members, say goodbye to members who leave, send a private message to new members and give them roles automatically. Everything is set on the [Welcome page](../website/dashboard/welcome.md) of the dashboard.

* Settings on the website: [Welcome](../website/dashboard/welcome.md).
* Permissions the bot needs: [Permissions needed](#permissions-needed).
* Invitations (who invited a new member): [Invite tracking](#invite-tracking).

## What the bot can do

| Feature | Where | What it does |
| --- | --- | --- |
| **Welcome message** | A text channel | Posts a message when a member joins. |
| **Goodbye message** | A text channel | Posts a message when a member leaves. |
| **Private message** | Direct message to the new member | Sends a message to the member who joins. Nothing happens if the member closed their private messages. |
| **Banner** | Inside the message or the private message | A picture with the avatar of the member, a title and a subtitle. |
| **Automatic roles** | The member | Gives roles to every new member, and separate roles to new bots. |

Each message can be a plain text, a card (embed), a banner, or both. The four tabs of the page are _**Welcome**_, _**Goodbye**_, _**Private message**_ and _**Roles**_.

## Set up in a few minutes

1. **Check the permissions.** The bot needs the permissions of the [Permissions needed](#permissions-needed) section in the channels where it posts. Run `/check-permissions` to see what is missing.
2. **Open the Welcome page.** In the sidebar, section _**Management**_, click _**Welcome**_.
3. **Use the quick start.** On a server where nothing is set yet, the page shows one question: the channel for welcome messages. Choose a channel and click _**Turn on welcome messages**_. The bot writes a message for the welcome, the goodbye and the private message. The goodbye and private message texts are filled in, but these two messages are not turned on.
4. **Check the message.** The _**Preview**_ on the right shows the message as Discord will display it. Use the variables to add details (see [Variables](#variables)).
5. **Save.** The bar at the bottom of the page says _You made changes, save them!_. Click _**Save**_.
6. **Test.** Click _**Send me a test**_. The bot posts a sample about you, with the saved settings. See [Test a message](#test-a-message).

The quick start is only shown when the server has no settings and no message is turned on. Everything can be changed afterwards.

## Variables

A message can contain variables. Each variable is replaced by the real value for each member. Write them between curly brackets, or click the buttons under the text box to insert them.

| Variable | Replaced by | In a goodbye message |
| --- | --- | --- |
| `{user}` | A mention of the member (the member is pinged). | The name of the member, not a mention. Nobody is pinged. |
| `{user.name}` | The username of the member. | Same. |
| `{user.display_name}` | The name shown for the member in the server (nickname, else display name). | Same. |
| `{user.id}` | The Discord id of the member. | Same. |
| `{server}` | The name of the server. | Same. |
| `{member_count}` | The number of members of the server, with separators (for example `1,234`). | Same. |
| `{member_count.ordinal}` | The rank of the member: `1st`, `2nd`, `3rd`, `4th`… | Same. |
| `{account_created}` | When the account of the member was created. In a message: a relative time, shown by Discord (for example "3 years ago"). In a banner: the date `YYYY-MM-DD`. | Same. |
| `{date}` | Today's date. In a message: the date shown by Discord, in the reader's language. In a banner: `YYYY-MM-DD`. | Same. |
| `{inviter}` | Who invited the member (a mention). | The name of the inviter, not a mention. |
| `{inviter.name}` | The name of the inviter. | Same. |
| `{invites}` | How many invitations of the inviter still count (see [Invite tracking](#invite-tracking)). | Same. |
| `{invite_label}` | The name given to the invite link used. If the link has no name, its code is shown. | Same. |

Notes:

* When invite tracking is off, or the bot does not know who invited the member, `{inviter}` and `{inviter.name}` show `unknown` (in the language of the server, for example `inconnu` in French), `{invites}` shows `0`, and `{invite_label}` shows `unknown` or the label that is known.
* The bot escapes the names written by members (name, display name). A name cannot ping anyone or change the layout of the message.
* The ordinal suffix follows the language of the server: `1st`, `2nd`… in English, `1er`, `2e` in French, `1º` in Spanish, Portuguese and Italian, `1.` in German, Polish, Turkish, Russian and Ukrainian. Other languages show the plain number.
* Unknown words between curly brackets are left as they are.

## Messages as a card

Turn on _**Show the message as a card**_ to show the text in a card: a title, a text, a colored edge and a picture, like a Discord embed. The card can also show:

* the **avatar** of the member as a small picture (_**Show the member's avatar**_, on by default);
* a **large picture** at the bottom, dropped in the card editor (a picture of your library, see [Your pictures](#your-pictures));
* a small **footer** text.

The card needs the *Embed Links* permission in the channel.

## Banners

A banner is a picture of 1000 × 350 pixels, drawn by the bot for each new member. It shows the avatar of the member, a title and a subtitle. Turn it on with _**Send a welcome banner**_ (or _**Send a goodbye banner**_, _**Send a banner with the private message**_).

Where the banner goes depends on the card:

* When the message is a card and _**Show the banner inside the card**_ is on (default), the banner is the picture of the card.
* Otherwise the banner is sent under the message, and the card can keep its own picture.

### Designs

Without a picture, the banner uses one of **8 designs**: _Aurora_ (default), _Sunset_, _Ocean_, _Forest_, _Midnight_, _Neon_, _Candy_ and _Slate_. A background can also be a solid color, or a picture of your own.

### Your pictures

Drop a picture in the _**Your picture**_ area, or click it to choose one. Accepted formats: **PNG, JPEG or WebP**, **4 MB** at most. The bot resizes and cleans the picture before it keeps it. A server can keep **10 pictures** and **20 MB** in total. Delete a picture with its trash button; a banner that used it goes back to the default design.

The recommended size is **1000 × 350 px** for a banner, and **1200 × 675 px** for the large picture of a card.

### Classic banner or custom layout

The **classic** banner shows the avatar, the _Banner title_ and the _Banner subtitle_. Leave them empty to use the default texts. Emoji are not drawn on a banner.

_**Design my own layout**_ opens the banner editor. A custom layout is a list of elements placed on the banner:

* **Text**: font (_Sans_, _Serif_, _Mono_), size, color, alignment, vertical position, bold and shadow. Variables can be used in the text. Serif and Mono only draw Latin letters; other scripts use the Sans font.
* **Avatar**: the picture of _The new member_, _Who invited them_ or _The server icon_, in a circle, a rounded square or a square. Without a picture, a colored disc with a letter is drawn.
* **Shape**: a rectangle or a circle, one or two colors, opacity, rounded corners and border.
* **Picture**: one of your pictures, cropped (_Fill the box_) or shown whole (_Show it all_).

A banner has at most **20 elements** and at most **4 pictures**. A text element keeps at most **200 characters**.

The editor starts from one of five templates: _Classic_, _Centered_, _Minimal_, _Framed_ or _Invited by_. The layers list changes the order of the elements (the first one is at the back). _**Discard**_ leaves the editor without saving; _**Done**_ keeps the layout, which is saved with the page.

The _**Real rendering**_ button asks the bot to draw the exact banner, about you. Use it to check the result before saving.

## Automatic roles

The _**Roles**_ tab gives roles to new members:

* **Roles for new members**: up to **10** roles, given when a member joins.
* **Roles for new bots**: up to **10** roles, given when a bot joins.
* **Wait until the member accepts the rules** (on by default): when the server uses membership screening (its rules), the roles of new members are given after the member accepts the rules, not before. When it is off, the roles are given when the member joins.

The bot gives a role only when all these are true:

* the role still exists and is not managed by an integration (for example the role of a bot or of an app);
* the role is below the highest role of the bot in the server settings;
* the role has no moderation or administration permission (for example *Manage Roles*, *Kick Members*, *Ban Members*, *Manage Messages* or *Administrator*).

The dashboard also refuses a role that you could not give yourself: you need *Manage Roles*, and the role must be below your highest role.

The order on arrival: the roles are given first, then the welcome message, then the private message.

## Test a message

_**Send me a test**_ (on each tab) makes the bot send the message as if you had just joined (or left). It uses the **saved** settings, so save first: the button stays disabled while there are unsaved changes.

* The welcome and goodbye messages are posted in the channel of the message. A test welcome or goodbye message is deleted after **2 minutes** at most.
* The private message is sent to you. The page then says _Check your private messages._

Errors shown by the test:

| Message on the page | Cause |
| --- | --- |
| _The bot cannot write in this channel. Give it the permission to send messages there._ | Missing *View Channel* or *Send Messages*. |
| _The bot cannot show cards in this channel. Give it the permission to embed links._ | Missing *Embed Links*. |
| _The bot cannot send pictures in this channel. Give it the permission to attach files._ | Missing *Attach Files*. |
| _Choose a channel and save first._ | No channel chosen, or the channel was not found. |
| _Turn this message on and save first._ | The message is off. |
| _Save the settings first._ | Nothing is saved yet. |
| _Your private messages are closed: the bot cannot write to you._ | Your private messages are closed for the server. |
| _The message is empty._ | No text, no card and no banner. |
| _The bot does not answer right now. Try again in a moment._ | The bot is not reachable. Try again. |

A test allows at most **6 tests per minute** for each person.

## Limits

| Item | Limit |
| --- | --- |
| Text of a message | 2000 characters |
| Title of a card | 256 characters |
| Text of a card | 4096 characters |
| Footer of a card | 2048 characters |
| Title and subtitle of a banner | 120 characters each |
| Text element of a custom banner | 200 characters |
| Elements in a custom banner | 20 |
| Pictures in a custom banner | 4 |
| Pictures kept by a server | 10 pictures, 20 MB in total |
| Picture sent from the page | PNG, JPEG or WebP, 4 MB |
| Automatic roles | 10 for new members, 10 for new bots |
| Deletion of a welcome message | Never, or after 10 seconds, 30 seconds, 1 minute, 5 minutes or 1 hour (dashboard choices) |
| Messages sent by the bot (welcome and goodbye) | 10 messages every 10 seconds for a server, see [Anti-raid](#anti-raid) |
| Tests | 6 per minute for each person |
| Real rendering of a banner | 30 per minute for each person |

## Anti-raid

When many members join in a short time (a raid), the bot limits the messages it posts:

* At most **10 welcome and goodbye messages every 10 seconds** for a server. The messages beyond this limit are not sent.
* At most **2 banners** are drawn at the same time, for all servers.

The limit applies to the welcome and goodbye channel messages. It does not apply to the private messages or to the roles.

The bot does not store the members. It uses the arrival and departure events on the spot, and keeps only the settings of the server.

## Permissions needed

| Where | Permission | Used for |
| --- | --- | --- |
| Welcome or goodbye channel | *View Channel* and *Send Messages* | Posting the message. |
| Welcome or goodbye channel | *Embed Links* | Messages shown as a card. |
| Welcome or goodbye channel | *Attach Files* | Banners and pictures. |
| Server | *Manage Roles* | Giving the automatic roles. The role must also be below the highest role of the bot. |
| Server | *Server Members* intent (see [Server Members intent](#server-members-intent)) | Knowing who joins and who leaves. |

The private message needs no permission in a channel: the bot writes to the member directly. The member must accept private messages from the server members.

The invitation link of the bot includes these permissions. If you invited the bot with a restricted link, add the missing ones in the server role of the bot.

## Server Members intent

Discord only tells a bot who joins or leaves a server when the bot has the privileged **Server Members** intent. If the Welcome page says _Not available on this bot yet_, the bot does not receive these events yet. The settings are saved and start to work as soon as the intent is on.

## Invite tracking

The Invites feature tells who invited each new member. When it is on, the variables `{inviter}`, `{inviter.name}`, `{invites}` and `{invite_label}` are filled. Without it, they show `unknown` and `0`.

Invite tracking is turned on in the Invitations page of the dashboard (section _**Management**_). It needs the Server Members intent, the Guild Invites intent and *Manage Server* for the bot. The `{invites}` value is the number of invitations of that inviter that still count.

## Free or premium

Welcome and goodbye messages, private messages, banners, pictures and automatic roles are **free** for every server. There is no premium option for this feature.

## Troubleshooting

| Problem | Cause | What to do |
| --- | --- | --- |
| No message when a member joins. | The welcome message is off, the channel is not chosen, or the bot cannot write in the channel. | Check the tab is on, the channel is saved, and run `/check-permissions`. Use the test. |
| The message is sent without the banner. | The bot cannot attach files in the channel, or the banner could not be drawn. | Give the bot *Attach Files*. Check the banner in the editor with _**Real rendering**_. |
| The card is not shown. | The bot cannot embed links in the channel. | Give the bot *Embed Links*. |
| The roles are not given. | The bot lacks *Manage Roles*, the role is above the bot's role, or the role has a moderation permission. | Put the role of the bot above the roles you chose, and give it *Manage Roles*. Check the warning on the Roles tab. |
| The roles are given after the rules, not at once. | _Wait until the member accepts the rules_ is on, and the server uses membership screening. | This is expected. Turn the option off to give the roles on arrival. |
| The private message is not received. | The member closed private messages from server members. | Nothing the bot can do. The bot does not retry. |
| The goodbye message does not appear. | The goodbye message is off, the channel is not saved, or the bot cannot write there. | Same checks as the welcome message. |
| The messages stop during a raid. | The limit of 10 messages every 10 seconds was reached. | This is expected. Only the messages beyond the limit are not sent. |
| `{inviter}` shows `unknown`. | Invite tracking is off, or the bot did not find the invite. | Turn on the Invitations feature (see [Invite tracking](#invite-tracking)). |
| A banner or card shows the default design or no picture. | The picture was deleted from the library. | Choose another picture or design, then save. |
| The page says _Not available on this bot yet_. | The bot does not have the Server Members intent. | See [Server Members intent](#server-members-intent). |

## Commands

This feature has no slash command. It is set on the dashboard only.

## Related pages

* [Welcome page of the dashboard](../website/dashboard/welcome.md): every tab and setting, with its default value.
* [Permissions](../permissions.md): the permissions of each feature.
* [Temp voice](../audio/tempvoice.md): another feature with a greeting message.
