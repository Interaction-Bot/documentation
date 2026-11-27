---
description: Get more frequent question asked by user of Interaction Bot.
---

# FAQ

## Getting started

### How do I add the bot to my server?
Go to [interaction-bot.com](https://interaction-bot.com), click _Add to Discord_ and select your server. You need the *Manage Server* permission. See [Getting started](getting-started.md).

### How do I set up the bot? Do I have to learn commands?
No. There is no configuration command. Use the **Quick setup** page of the dashboard (it sets the main modules in about a minute, see [Quick setup](management/quick-setup.md)), the [AI setup](management/ai-setup.md) (`/ai setup`: say what you want in one sentence), or the [dashboard](website/dashboard/README.md). Type `/config` to see the two ways again.

### How do I translate a message?
Add a flag emoji under it, right click > *Apps* > *Translate*, or use `/translate`. For automatic translation, set up a rule on the [dashboard](website/dashboard/README.md) or with the [AI setup](management/ai-setup.md). See the [translation overview](translation/overview.md).

### Can I use the bot on a server where it is not added?
Yes, install it on your Discord account (**Add to my account** on the [Account page](website/dashboard/account.md) or in `/invite`). `/translate` and the **Apps** menus then work in any server and in DMs. See [User app](commands/user-app.md).

### Which languages are supported?
100 languages. Run `/languages` to list them.

### Is the bot free?
Yes. The features are free, with limits: translation, the honeypot, the event log, the invite tracker, welcome messages, temporary voice channels and the AI setup. [Premium](premium/premium.md) is optional and raises the limits (rules, languages per rule, translations per message, voice without a vote, FAQ, AI requests...) and unlocks a few options, such as the bot profile.

## Translation

### Why is the translation of a message wrong?
The bot translates for free on tens of thousands of servers, with automatic translation models. The quality depends on the languages and on the message (slang, abbreviations and very short texts are harder). We keep improving the translation models, and premium servers get the best model with priority.

### Why is my message detected in the wrong language?
The bot must recognize 100 languages in any message. A message that is too short, or full of emojis and other elements, can be mistaken. The bot reads the last messages of the same author to decide. You can set the minimum size of the messages to translate in the [Exceptions](website/dashboard/exceptions.md) page, and the number of messages used for the detection in the [Overview](website/dashboard/overview.md). Blacklisting a language that is too often confused with another one is a Premium option, in the same page. See [language detection](translation/language-detection.md).

### The bot does not translate in a channel
Run `/check-permissions`, and follow the [troubleshooting checklist](translation/troubleshooting.md).

### The bot translated a message several times / posted a warning about a limit
One message can receive up to 3 translations on a free server (20 on premium). If several rules apply to the same message, the extra ones are dropped. Reduce overlapping rules, or read the [translation overview](translation/overview.md) to see which rule wins.

### Can the bot translate other bots?
Yes, on a Premium server, with the option for the messages of bots in the translation pages of the dashboard. Without Premium, the bot does not translate the messages of other bots.

### What happens to my data?
See the [Privacy Policy](https://interaction-bot.com/privacy) and the [Terms of Use](https://interaction-bot.com/tou), and [Security and privacy](security.md).

### Who can use the dashboard?
Members with the *Manage Server* or *Administrator* permission of the server can configure the bot. If your server does not appear, check that you are logged in with the right Discord account and that the bot is on the server.

## Voice

### How do I use `/tts say` or `/connect`?
On a Premium server these commands work without a vote. On other servers, they need a [top.gg vote](https://top.gg/bot/893494390142697493/vote) by any member of the server in the last 24 hours. No vote is needed during the first 24 hours after the bot is added to a server. See [Voice](audio/voice.md).

### How long can a transcription last?
The limit is per server: 30 minutes per day on a free server, 3 hours per day on Premium. The time of all the transcriptions adds up. The "day" is the UTC calendar day: the counter starts again at midnight UTC. When the time is used up, the bot leaves the voice channel and says when it can transcribe again. See [Daily time and stop](audio/voice.md#daily-time-and-stop).

## FAQ feature

### How do I make the bot answer questions on my server?
Create a group on the dashboard [FAQ](website/dashboard/faq.md), add questions and answers, and use `/ask` or turn on the automatic reply. A free server has 1 group with 5 answers and 3 channels; a Premium server has 5 groups, 150 answers and 10 channels. See [FAQ and /ask](qa/faq.md).

## Management

### Does the bot keep a log of what happens on my server?
Yes, if you turn it on: the [event log](management/event-log.md) writes the edited and deleted messages, the members who join or leave, the voice, the channels, the roles, the moderation actions and more to the channels you choose. It is free. The bot does not store these events: the channel is the log.

### Can the bot have its own nickname or avatar on my server only?
Yes, with the [bot profile](management/bot-profile.md). It is a Premium option. The name of the application stays *Interaction Bot* everywhere, and the other servers are not affected.

### Is the honeypot free?
Yes. See [Honeypot](management/honeypot.md).

### Are the invitation rankings free?
Yes, the invitation tracker and its rankings are free, and so are the pinned rankings. See [Invite tracker](management/invite-tracker.md).

## Premium

### How do I get premium?
See [Premium](premium/premium.md) and [Subscribe](premium/subscribe.md). Then run `/premium add` on your server.

### I subscribed but the server is not premium
Check that the subscription is active on the [Premium page](https://interaction-bot.com/premium) (**My subscription**). Then run `/premium add` on the server. For a Patreon offer, link your Discord account to Patreon and wait about 10 minutes. Contact the support if it still does not work.

## Still need help?

Join the [support server](https://support.interaction-bot.com).
