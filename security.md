---
description: What the bot can see, what it keeps and for how long, who can read it, how the dashboard is protected, and your rights over your data.
---

# Security and privacy

This page is a summary. The full text is in the [Privacy Policy](https://interaction-bot.com/privacy) and the [Terms of Use](https://interaction-bot.com/tou), which prevail.

## What the bot can see

The bot asks Discord for the minimum it needs:

* **Servers, channels, roles and members**, to know where to translate, greet, give roles and follow invitations;
* **Messages and their content**, to translate them, detect their language and answer the FAQ;
* **Reactions**, for the [flag translation](translation/flags.md) and the [reaction roles](management/reaction-roles.md);
* **Voice states**, to join voice channels for [text to speech and transcription](audio/voice.md) and for [recording](audio/recording.md);
* **The audit log**, when the bot has the *View Audit Log* permission, to know who did an action (see the [event log](management/event-log.md)).

## What it keeps

The bot keeps **your configuration** (channels, roles, languages, rules, options, FAQ entries, the state of the features, the premium state) so that it can apply it. It stops keeping it when the bot leaves the server.

| What | How long |
| --- | --- |
| **Messages to translate** | Not kept. They are not stored in a database and do not appear in the logs. |
| **Context of the language detection**: the last messages of a member, to read a short message in the right language | In memory only, for 10 minutes. Never in a database or a file. A server can set how many messages are used. |
| **Recordings** of a voice channel (one track per speaker, encrypted) | 24 hours, or 7 days on a Premium server. |
| **Transcriptions of a recording** (encrypted) | With the recording they belong to. |
| **Cloned voices** and their voice sample | Until you delete them, and at most 30 days after the end of the Premium they need. |
| **Invitation journal** (who joined with which invitation) | The period chosen by the server (30, 90, 180 or 365 days), or until the server deletes it. |
| **Honeypot catches**, with the first 300 characters of the message as evidence | 30 days. |
| **Banner images** of the welcome messages | Until they are deleted, or the bot leaves the server. Up to 10 per server. |
| **Bot profile**: the nickname and the bio you chose, and their state | While the bot is on the server. |
| **Bot profile images** (avatar and banner) | **Never kept**: they go to Discord and are forgotten. |
| **Event log** | **Not kept**: the events are written to the channels you chose, and Discord keeps them there. |
| **AI assistant**: the conversation | Not kept once it ends. The log of the changes it made, and the request counters: 90 days. |
| **Your account**: Discord ID, username, avatar, and your preferences | Until you delete your account or your data. |
| **Action journal** of a server (who did what) | 90 days at most, shorter if the server chooses. |
| **Diagnostic logs** (when the server owner turns them on) | 7 days. |
| **Error logs** without personal data | 30 days. |
| **Purchases** (link with Stripe, subscriptions, invoices) | While a subscription runs. Billing records are kept as the law requires. |

Discord also keeps the messages that the event log writes to your channels: they are as safe as any message of your server.

## Who can read the data

* The data is only accessible to the administrators of Interaction Bot.
* Translation, language detection, text to speech, transcription and voice cloning run on **our own** models and servers. No third-party AI provider receives your messages or your voice.
* **The AI configuration assistant is the exception.** When you use it (on the dashboard or with `/ai setup`), the messages of the administrator who started the conversation, the earlier messages of that conversation, and the settings it reads or changes are sent to an AI model provider, OpenRouter, which forwards them to the host of the model. Nothing else you write on Discord is sent to it. See [AI setup](management/ai-setup.md#privacy).
* Recordings are encrypted. A recording can only be downloaded by the member who started it.
* The bot never sells your data and never uses it for advertising.

## The dashboard

* You log in with your **Discord account** (OAuth). The bot never sees your Discord password. The dashboard asks Discord for your identity and the list of your servers; the list is not stored.
* You can only configure the servers where you have the *Manage Server* or *Administrator* permission and where the bot is present. The bot checks it again at every save.
* The bot only posts in channels **of the server** that owns the configuration.
* The connections to the website use HTTPS. The website has no advertising or analytics cookie.

## Voice features

* The bot listens to a voice channel **only while a transcription or a recording is running**: started by a command, by the automatic mode you enabled, or from the Activity.
* A recording is announced: a message in the text channel, a spoken announcement, and the nickname of the bot (*Recording*) for as long as it records.
* Transcription time is limited per server and per day: 30 minutes on a free server, 3 hours on Premium, per UTC day (the counter restarts at midnight UTC). The bot leaves when no human remains.

## Premium and ages

* Discord requires its users to be at least 13 years old.
* Buying Premium and cloning a voice are reserved for people aged **18 or over**. You confirm it before you clone a voice.

## Your rights

Log in on the website and open **Account**, then **Privacy**:

* **Download my data**: a ZIP with your account data, your preferences, what the features keep about you, your own voice tracks and your lines in the transcriptions of recordings, your cloned voices, your purchases and your use of the AI assistant.
* **Delete my data**: removes your voice from the recordings, the recordings you started, your cloned voices and your preferences.
* **Delete my account**: all of the above, plus the link with your Patreon account and your Stripe purchase data. Cancel a running Stripe subscription first.

In Discord, the command `/privacy` explains what the bot keeps about you, with your opt-outs:

* **Stop recording me**: the bot no longer records your voice, and the live transcription ignores it.
* **Do not process my messages**: the bot no longer translates, reads aloud or analyses your new messages, and the AI assistant refuses to read them. The event log of a server is still written, because it is the record of that server.

For any other request, write to the address of the [Privacy Policy](https://interaction-bot.com/privacy). Your rights include access, copy, deletion, objection and restriction.

## Report a problem

If you found a security problem, please contact the [support](https://support.interaction-bot.com) privately and do not publish it.
