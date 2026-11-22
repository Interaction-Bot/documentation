---
description: Bot profile, a nickname, avatar, banner and bio for Interaction Bot on your server only (Premium) - what changes in Discord, what does not, the limits, and what happens after a new invitation.
---

# Bot profile

The bot profile changes how Interaction Bot looks **on your server only**: its nickname, its avatar, its banner and its "About me" text. Other servers are not affected.

It is not a custom bot. The name and the icon of the application stay **Interaction Bot** in the list of commands, in *Integrations* and in the audit log.

* Settings on the website: [Bot profile](../website/dashboard/bot-profile.md).
* Who can use it: the whole page is for **Premium** servers. You can see the page on any server, but changing it needs Premium. See [Premium](../website/dashboard/premium.md).
* Discord permission: only the nickname needs one, see [Permissions](#permissions).

## What you can change

| Field | Rule |
| --- | --- |
| **Nickname** | 1 to 32 characters, on one line. No `@`, no code block, no mention, no « everyone » or « here », no link and no server invitation. |
| **Avatar** | png, jpg, gif or webp, 8 MB at most. It is cut to a square and resized before it is sent to Discord. |
| **Banner** | png, jpg, gif or webp, 8 MB at most. It is cut to the shape of the profile card (17:6). Discord can ask for a boost level on the server to set a banner. |
| **Bio** | 190 characters at most, four lines at most. No mention and no invitation to a server. |

A name that looks like Discord or its staff (for example *Discord*, *Clyde*, *Staff*, *Official*) is accepted, but the page shows a warning: members could be misled.

## How a change reaches Discord

1. **You write.** The page shows a preview of how the bot will look in the member list and in a message, before anything is sent.
2. **You apply.** The text and the chosen images are sent to Discord in one request, with the **Apply to Discord** button of the save bar. The text alone can be saved as well.
3. **Discord answers.** The page says what was applied, or why it was not: a refused image, a nickname that Discord refuses, or a wait.

Limits:

* **5 changes an hour per server.** The page says how many are left. Discord also asks the bot to wait sometimes: the page then says when the next change is possible, and the saved text stays.
* **During a recording**, the nickname is left alone until the recording ends, because the bot uses its nickname to show that it records.

{% hint style="info" %}
The images are **never kept** by Interaction Bot. They go to Discord and are forgotten. The nickname, the bio and the state are kept, so the bot can apply them again.
{% endhint %}

## States

The page shows the state of the profile in this server:

| State | Meaning | What to do |
| --- | --- | --- |
| **The bot uses its default profile** | Nothing was changed. | Nothing. |
| **Saved, not applied yet** | The text is saved, Discord does not have it yet. | Click **Apply to Discord**. |
| **The profile is in force** | Discord has what you saved. | Nothing. |
| **The nickname was changed by hand in Discord** | Someone changed the nickname of the bot in Discord. The bot does not fight that change. | Click **Apply again** to bring the profile back. |
| **Discord reset the profile of the bot** | The bot left the server and was invited again. Discord reset its profile. | The nickname and the bio are applied again with **Apply again**. The avatar and the banner must be sent again. |
| **The last change failed** | Discord refused the change. | Check the fields marked in red, then try again. |

## Permissions

| Field | Discord permission |
| --- | --- |
| Nickname | **Change Nickname** on the bot role. Without it, the page shows *The bot cannot change its nickname here*, with a link that asks for the permission. |
| Avatar, banner, bio | None. |

## Reset

* **Reset** next to a field brings it back to the default of Discord.
* **Reset everything** brings back the nickname, the avatar, the banner and the bio. Click it twice to confirm.

A reset stays possible on a server that is no longer Premium.

## Switch off

The bot profile has a switch at the top of its page. When it is off, the page does not apply changes until it is on again. The profile that is already applied stays in Discord.

## Setup

1. Make sure the bot has the **Change Nickname** permission if you want a nickname.
2. Open **Bot profile** in the **Management** section of the dashboard.
3. Write the nickname and the bio, choose the images, and check the preview.
4. Click **Apply to Discord**.

The images are always chosen on the page.

## Privacy

* The text is kept per server, with the state.
* Each change adds a row to the dashboard journal: which fields were sent or reset. The text and the images are not in the journal.
* When the bot leaves a server, its profile rows are deleted with the rest of the server's data.

See [Security and privacy](../security.md).
