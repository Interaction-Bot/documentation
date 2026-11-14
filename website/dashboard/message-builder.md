---
description: "The message builder of the dashboard: the four forms of a message (card, embed, blocks, plain), up to ten embeds, every part of an embed, images by link or drag and drop, JSON import and export (Discohook), the free layout with blocks."
---

# Message builder

The message builder is where you write the messages the bot sends: the control panel and the welcome message of [temp voice](temp-voice.md), and the message of a [reaction roles](reaction-roles.md) panel. You write the message where it will appear, as Discord displays it. Nothing is a form: click a text and type.

## The four forms

The switch at the top chooses the form of the message:

* **Card**: one block with the text, the images and the buttons inside it.
* **Embed**: the classic Discord embed. Author with icon, title, text, fields side by side, thumbnail, image, footer with icon and time. The buttons are under the embed. It can hold up to **ten embeds**.
* **Blocks**: a free layout, built block by block (see [Blocks](#blocks)).
* **Plain message**: only text, without a frame. The buttons are under it.

_**Edit**_ and _**Preview**_ switch between writing and the exact rendering (Markdown rendered, variables replaced by an example).

## The parts of a message (card and embed)

Only the title and the text are there at the start. What is missing is added with the row of buttons under the switch (or the _**Add**_ menu) and removed with the small cross that appears when you point at a part:

* **Text above the message**, outside the frame.
* **Author**: a name, an icon and a link.
* **Title**: click the link icon next to it to make it clickable.
* **Thumbnail** (small image at the right) and **image** (large banner).
* **Fields**: a name and a value, up to 25. In an embed a field can be _inline_ (up to three side by side); the arrows reorder them.
* **Footer**: a text and an icon. **Time** shows the time the message was sent.
* **Color**: the bar at the left of the message (the round button at the right of it), or none.

## Images: a link or drag and drop

Every image slot (author icon, thumbnail, image, footer icon, and every image of the blocks) takes an image **by link or by drag and drop**:

* **Drag and drop** a file from your computer on the slot, or click the slot and drop it in the zone. PNG, JPEG or WebP, 4 MB at most; each server keeps up to 10 uploaded images (20 MB in all).
* **A link**: click the slot, paste the address of the image (`https://…`) and apply. Dragging a link from a web page onto the slot works too.
* **A variable**: the avatar of the owner, the icon of the server or the avatar of the bot, replaced by the real image at each message.

## Several embeds

In the _Embed_ form, _**Add an embed**_ adds a complete embed under the first one, up to **ten in all**. Each embed has every part above (author, title with link, text, fields, thumbnail, image, footer with icon, time, its own color). Point at an embed for its arrows (move up or down), its copy icon (duplicate) and its cross. A counter shows the characters used: Discord accepts 6,000 characters in all the embeds of one message, the counter keeps a margin of 200 for the bot's own texts.

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
