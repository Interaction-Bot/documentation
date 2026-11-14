---
description: "The message builder of the dashboard: templates to start from, the four forms of a message (card, embed, blocks, plain), several cards or embeds, every part of a message, images by link or drag and drop (also for the message itself), server emojis, JSON import and export (Discohook), the free layout with blocks."
---

# Message builder

The message builder is where you write the messages the bot sends: the control panel and the welcome message of [temp voice](temp-voice.md), and the message of a [reaction roles](reaction-roles.md) panel. You write the message where it will appear, as Discord displays it. Nothing is a form: click a text and type.

## Start from a template

There is no switch of form to choose before you write: the message takes the form of what you build. To go faster, the _**Templates**_ list at the top starts the message for you, and everything stays editable afterwards. A template never erases the texts already written.

* **Cards**: _Card_ (one block, the title and the text), _Announcement_ (the banner on top, a footer and the time), _Rules_ (three fields to fill), _Welcome_ (author with icon, thumbnail and footer).
* **Embeds**: _Embed_ (the classic Discord embed with author and footer), _Columns_ (three fields side by side), _Several embeds_ (a main embed and two more in the same message).
* **Other**: _Plain message_ (only text) and _Free layout_ ([blocks](#blocks)).

The four forms a message can take:

* **Card**: one block with the text, the images and the buttons inside it. A message can hold several cards.
* **Embed**: the classic Discord embed. Author with icon, title, text, fields side by side, thumbnail, image, footer with icon and time. The buttons are under the embed. It can hold up to **ten embeds**.
* **Blocks**: a free layout, built block by block (see [Blocks](#blocks)).
* **Plain message**: only text, without a frame. The buttons are under it.

_**Edit**_ and _**Preview**_ switch between writing and the exact rendering (Markdown rendered, variables replaced by an example).

## The parts of a message (card and embed)

Only the title and the text are there at the start. Everything else is added with the **Add** menu, a list that unfolds like the emoji picker, with every part sorted by family (text, images, message frame, more), each with an icon and a sentence. A part that is already there is not offered again.

### The bar of a component

Click or point at any component (the author, the title and text, a field, the banner, the buttons, the footer) and **its own bar** appears in its corner. A click **selects** the component: it stays outlined and keeps its bar, even when you move it up or down (the bar follows it), until you click another one or press _Esc_. From left to right:

* the **emoji** and **variable** buttons of the text you are writing (they are in this bar, never on top of the message);
* **up** and **down arrows**: move the component;
* **+**: add a component **right under this one** (the same Add menu);
* the **cross**: remove the component.

The **Add** button under the message adds at the end.

### What you can place where

* In a **card** every part moves, the banner (large image) included: author, title and text (with its thumbnail), each field, the banner, the buttons or choices, the footer. The text above the message stays at the top. The bot sends the message in this order.
* In an **embed** the order is Discord's (author, title, text, fields, image, footer): only the fields have arrows. Fields side by side exist only here (the inline button of a field).
* For a free order of everything with columns left out, use the [blocks](#blocks) form.

### The parts

* **Text above the message**, outside the frame.
* **Author**: a name, an icon and a link.
* **Title**: click the link icon next to it to make it clickable.
* **Thumbnail** (small image at the right) and **image** (large banner).
* **Fields**: a title and a text, up to 25. In an embed a field can be _inline_ (up to three side by side).
* **Free text**: a field without a title. In a card it is a text you place anywhere; in an embed it sits among the fields.
* **Footer**: a text and an icon. **Time** shows the time the message was sent.
* **Empty places**: the places of the header (author and icon), the thumbnail, the banner and the footer that are not filled yet appear as dotted places in the message; a click on one adds it right there. The cross of the header removes its title and text.
* **Message images**: see [Images of the message itself](#images-of-the-message-itself).
* **Color**: the bar at the left of the message (the round button at the right of it), or none.
* **Free layout**: the last entry of the menu turns the message into [blocks](#blocks) (each part becomes a block). The original message is kept: pick _Card_ or _Embed_ again to get it back.

Server emojis (`<:name:id>`, the ones you pick in the emoji list) are shown as images, as Discord displays them; what the bot sends is the written form. They are drawn where Discord draws them: in the text above the message, the title, the text and the **names and values of the fields**. Discord does not draw them in the **name of the author** nor in the **footer** (the code stays visible there, as it will be sent); a standard emoji (Unicode) works everywhere.

## Images: a link or drag and drop

Every image slot (author icon, thumbnail, image, footer icon, and every image of the blocks) takes an image **by link or by drag and drop**:

* **Drag and drop** a file from your computer on the slot, or click the slot and drop it in the zone. PNG, JPEG or WebP, 4 MB at most; each server keeps up to 10 uploaded images (20 MB in all).
* **A link**: click the slot, paste the address of the image (`https://…`) and apply. Dragging a link from a web page onto the slot works too.
* **A variable**: the avatar of the owner, the icon of the server or the avatar of the bot, replaced by the real image at each message. In the dashboard they are shown with real images: your own avatar for the member, and the icon of the server you are setting up.

## Images of the message itself

Besides the images of the embed (author icon, thumbnail, banner, footer icon), the _Embed_ form and the _Plain message_ form can carry **pictures of the message itself**, shown under the text and above the embeds, up to **ten**. Open the _**Add**_ menu (or the _+_ of the text) and choose _**Message image**_; each image has its own bar (up, down, remove) and takes an image by link, by drag and drop, or a variable (the avatar of the member, the icon of the server, the avatar of the bot). A card or a free layout has no such images: Discord does not accept a text or a file next to those components, so use the banner or an image gallery instead.

An image you drop is **kept by Interaction Bot** for your server. It is deleted for you: as soon as the message no longer shows it, once the message is saved (and at once if you dropped it and removed it before saving), unless another message of the server still uses it. An image of the library that no message uses yet is never touched.

## Several embeds and several cards

In the _Embed_ form, _**Add an embed**_ adds a complete embed under the first one, up to **ten in all**. In the _Card_ form the same entry adds a card under the first one (up to ten cards; Discord counts 4,000 characters in all the cards). Each embed has every part above (author, title with link, text, fields, thumbnail, image, footer with icon, time, its own color). Point at an embed for its arrows (move up or down), its copy icon (duplicate) and its cross. A counter shows the characters used: Discord accepts 6,000 characters in all the embeds of one message, the counter keeps a margin of 200 for the bot's own texts.

## JSON import and export

_**Import / export**_ (not in the _Blocks_ form) opens the message as JSON, the format of Discord messages used by Discohook, webhooks and the API:

* **Export** shows the JSON of the message as it is now, to copy.
* **Import** takes a message JSON **or a Discohook link** (`https://discohook.org/?data=…`). It replaces the message of the page: the form becomes _Embed_, the text above goes to the text of the message, the embeds are kept (ten at most). Images uploaded in the dashboard have no address, so they are not part of an export; on import only `https` addresses are kept, and the page tells how many parts were dropped.

## Blocks

The _Blocks_ form is a free layout, built like the editors of the Discord components: a stack of blocks you order as you want.

* **Text**: Markdown, up to 4,000 characters in all the texts of the message.
* **Image gallery**: up to 10 images in all. A single image is a banner. Each image has a description (alternative text) and can be hidden as a spoiler.
* **Section**: one to three texts and, next to them, a thumbnail, a link button or nothing.
* **Separator**: a visible line or not, a small or a large space.
* **Link buttons**: up to five buttons in a row, each with an emoji, a text and an address.
* **Message buttons**: where the buttons of the feature go (the buttons of the control panel, the choices of a reaction roles panel). One at most; without it the buttons are at the end of the message.

_**Add a block**_ adds a block at the end; each block has arrows (move), a copy icon and a cross. _Whole message as spoiler_ hides all of it, and the round button at the right sets the color of the bar. The counter shows the components (30 at most), the characters (4,000) and the images (10) used; it turns red when Discord would refuse the message. A message has 25 blocks at most.

## Limits of Discord

A message has up to 10 embeds and 6,000 characters in all its embeds. A message in _Blocks_ form has up to 40 components (the buttons of the feature are counted by the bot), and cannot also contain embeds or text above. The builder applies these limits for you and tells which one a message goes over.
