---
description: Your personal settings, independent of any server - vote reminder, user app, recordings and privacy.
---

# Account

The **Account** page (`interaction-bot.com/account`) is in the user menu of the website. Unlike the other pages, it is not linked to a server: its settings are **personal** and apply to your Discord account on every server.

## User informations

Your global name, your username and the number of **Premium offers** of your Patreon account.

## Vote reminder

The bot reminds you to vote for it on [top.gg](https://top.gg/bot/893494390142697493/vote), **once a day**, as long as you have not voted yet. Use the toggle to enable or disable the reminder. It is the same setting as the `/reminder` command.

## User app

Install the bot on your Discord account and choose how it answers you. See [User app](../../commands/user-app.md).

* **Add to my account**: opens Discord to install the bot on your account (no server needed).
* **Default language**: the language used by `/translate` and **Apps > Translate** when you do not pick one. Leave it empty to use the language of your Discord application.
* **Public replies**: when enabled, the answers of `/translate` and **Apps > Translate** are visible to everyone in the channel instead of only to you.

The settings are saved as soon as you change them. The message *Saved.* confirms it, and *The settings could not be saved.* tells you that something went wrong.

## My recordings

The **Open my recordings** button opens the [My recordings](../recordings.md) page: the voice channel recordings where you speak or that you started.

## Privacy

The **Privacy** card lets you control what the bot keeps about you. It shows how much is stored about you right now (recordings where you speak, recordings you started, notes, personal settings and cloned voices) and offers:

* **Don't process my messages (opt-out)**: the bot no longer translates, reads aloud or analyses your new messages, and refuses to translate them. Messages already processed are not deleted, and your own commands are not blocked. This change is applied when you save.
* **Do not record me (opt-out)**: from the next recording, the bot does not record your voice. What is already recorded does not change.
* **Download my data**: a ZIP file with what the bot holds about you, in open formats (JSON and FLAC): your Discord identifiers and settings, your Patreon identifier, the metadata of your cloned voices, your recordings and the notes you added.
* **Delete my data**: removes your voice from the recordings where you speak (their mix is rebuilt without you), deletes the recordings you started with their notes, the notes you wrote, and your personal settings and cloned voices. It cannot be undone. Your account and your subscription are not affected. Recordings still in progress are not touched: run it again when they have ended.
* **Delete my account**: deletes everything above and the link between your account and Patreon, then logs you out. Your Patreon subscription is **not** cancelled: cancel it on Patreon.

The same information is available in Discord with the `/privacy` command, see [Limits and privacy](../../audio/limits-and-privacy.md).
