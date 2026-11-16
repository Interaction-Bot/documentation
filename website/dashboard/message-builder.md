---
description: "The message builder of the dashboard: templates to start from, the four forms of a message (card, embed, blocks, plain), several cards or embeds, every part of a message, images by link or drag and drop (also for the message itself), server emojis, JSON import and export (Discohook), the free layout with blocks."
---

# Message builder

The message builder is where you write the messages the bot sends: the control panel and the welcome message of [temp voice](temp-voice.md), the message and the replies of a [reaction roles](reaction-roles.md) panel, the warning of the [honeypot](honeypot.md), and the welcome, goodbye and private messages of the [Welcome](welcome.md) page. The Welcome page uses the same component; its only particularity is the _Welcome banner_, an image of the message set from the upload icon of an image (see [Welcome](welcome.md)). You write the message where it will appear, as Discord displays it. Nothing is a form: click a text and type.

## Start from a template

There is no switch of form to choose before you write: the message takes the form of what you build. To go faster, the _**Templates**_ list at the top starts the message for you, and everything stays editable afterwards. A template never erases the texts already written.

* **Cards**: _Card_ (one block, the title and the text), _Announcement_ (the banner on top, a footer and the time), _Rules_ (three fields to fill), _Welcome_ (author with icon, thumbnail and footer).
* **Embeds**: _Embed_ (the classic Discord embed with author and footer), _Columns_ (three fields side by side), _Several embeds_ (a main embed and two more in the same message).
* **Other**: _Plain message_ (only text).

The forms a message can take:

* **Card**: one block with the text, the images and the buttons inside it. A message can hold several cards.
* **Embed**: the classic Discord embed. Author with icon, title, text, fields side by side, thumbnail, image, footer with icon and time. The buttons are under the embed. It can hold up to **ten embeds**.
* **Plain message**: only text, without a frame. The buttons are under it.

_**Edit**_ and _**Preview**_ switch between writing and the exact rendering (Markdown rendered, variables replaced by an example). The preview follows Discord's own layout, checked by sending the same messages to a test server: fields in rows of three at most (a row of two splits in two), the empty line of a field without a title, the embed shrinking to its content, and the addresses of the message's pictures written at the end of the text of an embed or a plain message.

## The parts of a message (card and embed)

Only the title and the text are there at the start. Everything else is added with one of the **two Add buttons**, each a list that unfolds like the emoji picker, with an icon and a sentence for every entry. A part that is already there is not offered again.

* **Add to the embed** (or _Add to the card_), **inside** the embed, at the bottom: what belongs to the embed. Author, thumbnail, large image, a field, a free text, a **separator**, the footer, the time.
* **Add to the message**, **under** the message: what belongs to the message itself, outside the embed. The text of the message, an image of the message, another embed.

The **+** of a component's bar follows the same rule: on a part of the embed it adds to the embed, right under that part; on the text or an image of the message it adds to the message.

### The bar of a component

**Point at** a component (the author, the title and text, a field, the banner, the time, the buttons, the footer) and its bar appears just above it; **click or tap** it to **select** it and keep the bar (on a touch screen, a tap is the only way). The bar is an **overlay**: it never moves the message. It follows the component when you move it, until you select another one or press _Esc_. From left to right:

* the **emoji** and **variable** (**{ }**) buttons of the text you are writing (they are in this bar, never on top of the message). The variable button lists the variables the message accepts, each with its description, and the preview shows them replaced by an example. Reaction roles replies have their own: `{ROLE}`, `{USER}`, `{USER_NAME}` and `{SERVER}`; the Welcome page has `{user}`, `{server}`, `{member_count}`, `{inviter}`… (see [Welcome](welcome.md));
* **up** and **down arrows**: move the component (see [What you can place where](#what-you-can-place-where));
* **+**: add a component **right under this one**;
* on an image, no pencil: a **banner**, a **message image** or a **gallery image** you add is first a **plain blue picture** (the color of the bot, 1000 × 350), and a **thumbnail** a blue square (256 × 256): they show in the preview and the bot sends them, until you replace them. Every picture has an **upload icon** in its corner, as in MEE6: the icon opens the choice. A click on the frame itself, or on a picture already there, only selects it (so its bar shows on a touch screen too); the same icon sits over a picture to change it. The small round icons of the author and of the footer open on a click. **One choice window at a time**: opening one closes the other;
* the **cross**: remove the component (the component itself goes away, not only what it contained; a **thumbnail** or **image** leaves for good, and the _Add_ menu brings it back; the author, the title and text and the footer keep a dotted place);
* on a field, a **copy** button that duplicates it right under it.

Keyboard: **Alt + ↑ / ↓** moves the selected component without touching the text.

### What you can place where

Every component has arrows.

* In a **card** every part moves: author, title and text (with its thumbnail), each field or separator, the large image, the buttons or choices, the footer. The **text** and the **images of the message** are outside the card: above it, or **under it** (move them down past the card). The bot sends the message in this order.
* An **embed** has the order of Discord: the text of the message, its images, then the embed (author, title, text, fields, image, footer). Fields move among themselves. **Any other move** (the text under the embed, the image above the title…) switches the message to a **card**, where the order is free: a note says so, with **Undo**. Nothing is erased, but a card has no author icon, no footer icon and no fields side by side.
* The **large image** has a button in its bar that takes it **out of the embed** (it becomes an image of the message); an image of the message has a button that puts it **into the embed**.

### The parts

* **Text of the message**: outside the embed or the card, above it. In a card it can also go under it.
* **Author** (the header) and **footer**: always there while you write, as fields with their icon slot (empty, nothing is sent). In a **card** they are small texts without icon.
* **Title**: click the link icon next to it to make it clickable.
* **Thumbnail** (small image at the right) and **image** (large banner).
* **Fields**: a title and a text, up to 25. In an embed, the field's bar has a labelled _**Side by side**_ button (columns icon): on, the field shares its row with the next ones (up to three side by side); off, it takes the whole row. A card has no side-by-side fields.
* **Free text**: a field without a title. In a card it is a text you place anywhere; in an embed it sits among the fields.
* **Separator**: a thin line between two parts (the **eye** button of its bar shows or hides the line, leaving a simple space). In a card it is Discord's own separator, which spans the whole card; an embed has none, so the bot writes a **fixed line of 24 dashes**, preceded by an empty line like any field: it never spans the whole embed. For a full-width line, use a card.
* **Footer**: a text and an icon. **Time** shows the time the message was sent.
* **Empty places**: the places of the title and text, the author and the footer that are not filled yet appear as dotted places in the message; a click on one adds it right there. The **thumbnail** and the **image** are not there at the start: add them from the _Add_ menu. The cross of the header removes its title and text.
* **Message images**: see [Images of the message itself](#images-of-the-message-itself).
* **Color**: the bar at the left of the message (the round button at the right of it), or none.

Server emojis (`<:name:id>`, the ones you pick in the emoji list) are shown as images, as Discord displays them; what the bot sends is the written form. They are drawn where Discord draws them: in the text above the message, the title, the text and the **names and values of the fields**. Discord does not draw them in the **name of the author** nor in the **footer** (the code stays visible there, as it will be sent); a standard emoji (Unicode) works everywhere.

## Images: a link or drag and drop

Every image slot (author icon, thumbnail, image, footer icon, and every image of the blocks) takes an image **by link or by drag and drop**:

* **Drag and drop** a file from your computer on the slot, or click the slot and drop it in the zone. PNG, JPEG or WebP, 4 MB at most; each server keeps up to 10 uploaded images (20 MB in all).
* **A link**: click the slot, paste the address of the image (`https://…`) and apply. Dragging a link from a web page onto the slot works too.
* **A variable**: the avatar of the owner, the icon of the server or the avatar of the bot, replaced by the real image at each message. In the dashboard they are shown with real images: your own avatar for the member, and the icon of the server you are setting up.

## Every embed is an embed: move, duplicate, delete

Each embed (or card) of a message, **the first one included**, can be duplicated and deleted: its _duplicate_ and _delete_ buttons are **on its side**, under the color button, whether the message has one embed or several. A message with **one** embed shows no number. From **two** embeds on, each has its own line above it: its number and the _up_ and _down_ arrows. Moving the first one down swaps it with the next; deleting it makes the next one the first. Deleting the very last one leaves a **plain message** (the text above and the images of the message stay); the _Add_ menu of a plain message offers _Embed_ and _Card_ to bring one back.

The **time** (_Sent at_) has its own cross, apart from the footer. The cross of the **title and text** removes them from the message (an empty title would be the text of the bot, a removed one is nothing); a dotted _Title and text_ place brings them back.

## Undo and redo

The two arrows at the top of the message (or **Ctrl + Z**, **Ctrl + Shift + Z** outside a text field) undo and redo what you did, step by step: a removed component, a moved one, an applied template, an import, the text you typed. A pause of a moment ends a step.

## Images of the message itself

Besides the images of the embed (author icon, thumbnail, banner, footer icon), a message can carry **pictures of its own**, outside the embed, up to **ten**. Open _**Add to the message**_ (or the _+_ of the text) and choose _**Message image**_; each image has its own bar (up, down, +, remove) and takes an image by link, by drag and drop, or a variable (the avatar of the member, the icon of the server, the avatar of the bot). With an embed they are under the text and above the embed (the order of Discord); with a card they go above the card or under it.

An image you drop is **kept by Interaction Bot** for your server. It is deleted for you: as soon as the message no longer shows it, once the message is saved (and at once if you dropped it and removed it before saving), unless another message of the server still uses it. An image of the library that no message uses yet is never touched.

## Several embeds and several cards

In the _Embed_ form, _**Add an embed**_ adds a complete embed under the first one, up to **ten in all**. In the _Card_ form the same entry adds a card under the first one (up to ten cards; Discord counts 4,000 characters in all the cards). Each embed has every part above (author, title with link, text, fields, thumbnail, image, footer with icon, time, its own color). Each embed has its arrows above it (move up or down) and, on its side, its copy icon (duplicate) and its bin (delete). A counter shows the characters used: Discord accepts 6,000 characters in all the embeds of one message, the counter keeps a margin of 200 for the bot's own texts.

## JSON import and export

_**Import / export**_ (not in the _Blocks_ form) opens the message as JSON, the format of Discord messages used by Discohook, webhooks and the API:

* **Export** shows the JSON of the message as it is now, to copy.
* **Import** takes a message JSON **or a Discohook link** (`https://discohook.org/?data=…`). It replaces the message of the page: the form becomes _Embed_, the text above goes to the text of the message, the embeds are kept (ten at most). Images uploaded in the dashboard have no address, so they are not part of an export; on import only `https` addresses are kept, and the page tells how many parts were dropped.

## Blocks

A message built earlier with the former _Free layout_ keeps that form and is still edited block by block (a template brings it back to a card or an embed). New messages no longer need it: a card orders its parts freely.

* **Text**: Markdown, up to 4,000 characters in all the texts of the message.
* **Image gallery**: up to 10 images in all. A single image is a banner. Each image has a description (alternative text) and can be hidden as a spoiler. A click on a picture only selects it (an empty one opens the choice): its **upload icon** opens the choice of the image (drop, address or variable) and its bar has the **description**, the **spoiler** button, and, for a single image (a banner), the buttons of the block too (move, duplicate, remove), all in one bar. With several images each one has its own bar, and the block's bar is reached from the space around them.
* **Section**: one to three texts and, next to them, a thumbnail, a link button or nothing.
* **Separator**: a visible line or not, a small or a large space.
* **Link buttons**: up to five buttons in a row, each with an emoji, a text and an address.
* **Outside the card**: every block has a button in its bar that takes it **out of the card**. A block outside the card is a component of the message of its own (a banner, a text, a section…), so **the order of the blocks is the order of the message**: for example the banner, then a text, then the card with the rest. Blocks that follow each other inside share one card; a block outside between two of them splits the card in two. Converting an embed to the free layout keeps Discord's order (the text above and the pictures of the message become blocks outside the card, above it).
* **Message buttons**: where the buttons of the feature go (the buttons of the control panel, the choices of a reaction roles panel). One at most; without it the buttons are at the end of the message.

_**Add a block**_ adds a block at the end; each block has arrows (move), a copy icon and a cross. The round button at the right sets the color of the bar. The counter shows the components (30 at most), the characters (4,000) and the images (10) used; it turns red when Discord would refuse the message. A message has 25 blocks at most.

In the preview, pictures are drawn like Discord draws them: at most 400 px wide and 300 px tall, in their own proportions.

## Limits of Discord

A message has up to 10 embeds and 6,000 characters in all its embeds. A message in _Blocks_ form has up to 40 components (the buttons of the feature are counted by the bot), and cannot also contain embeds or text above. The builder applies these limits for you and tells which one a message goes over.
