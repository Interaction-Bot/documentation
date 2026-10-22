---
description: Everything new in the server management update of October 2026 - welcome messages, invite tracker, honeypot, AI setup, voice messages and a new Temp voice page.
---

# October 2026 - server management

The third update of October 2026. It adds tools to welcome and protect your community, the AI setup, Discord voice messages, and a clearer [dashboard](../website/dashboard/README.md).

## New features

### Welcome and goodbye
* A **welcome message**, a **goodbye message** and a **private message** to the new member, with a card and a **banner** made of one of 8 designs, your own picture, or the visual editor (layers, avatars, shapes, texts with variables).
* **Roles given on arrival**, after the member accepts the rules of the server.
* Variables such as the member, the server, the rank of the member ("our 1,234th member"), the account age and the inviter. A preview and a **test button** show the result before it goes live.
* Free for every server. See [Welcome and goodbye](../management/welcome-and-goodbye.md) and the dashboard page [Welcome](../website/dashboard/welcome.md).

### Invite tracker
* Know **who invited each member**, with a ranking of the best inviters, a journal, fake account detection and corrections you can undo.
* `/invites [user]` and `/invite-leaderboard`. Invite labels can give a role. Variables `{inviter}`, `{invites}` and `{invite_label}` for the welcome message.
* Off by default, free for every server. See [Invite tracker](../management/invite-tracker.md) and the dashboard page [Invitations](../website/dashboard/invites.md).

### Honeypot
* **Trap channels** that catch spam bots and hacked accounts: kick and clean up, report, ban or timeout, with a pinned warning, a report in a log channel, a history with the message as evidence, and a protection that pauses the trap when real members fall into it.
* Free for every server. See [Honeypot](../management/honeypot.md) and the dashboard page [Honeypot](../website/dashboard/honeypot.md).

### AI setup
* `/ai setup` opens a conversation in a channel: say what you want, the AI proposes a plan and applies it after your confirmation. The same assistant is available on the dashboard. See [AI setup](../management/ai-setup.md).

### Voice messages
* Right click a Discord voice message > Apps > **Transcribe voice message**, with a **Translate to my language** button.
* On a Premium server, voice messages are translated by the translation of the server (channel, mirror, category, role, flag) and can be **dubbed** with text to speech.
* Optional automatic transcription under each voice message. See [Voice messages](../audio/voice-messages.md) and the dashboard page [Voice messages](../website/dashboard/voice-messages.md).

### A guided welcome message when the bot joins
* The message of the bot on a new server asks what you want to do first and turns into a short guide, with buttons that run the real commands. See [Getting started](../getting-started.md).

## Improvements

* **Temp voice page redesigned**: 4 tabs (Rooms, Control panel, Who can do what, Moderation), one card per Join to create channel, an editor with a preview, and the installation applied when you save. See [Temp voice](../website/dashboard/temp-voice.md).
* **Translation groups are now called Mirror Translation** in the dashboard and the bot (the commands `/group ...` do not change). **Speech to text** is now called **Transcription** on the dashboard.
* The **dashboard menu** is regrouped: Language identification, Blacklist and Flag shortcuts are under Translation, and Welcome, Invitations and Honeypot are under Management.
* The dashboard keeps your server list for 10 minutes and the bot **confirms every change** against your Discord permissions (Administrator or Manage Server).
* The voice recording is more robust against lost network packets, and a track now plays from the right position on its page.
* The bot now uses the **Server Members** ability, for the welcome messages and the invite tracker.
