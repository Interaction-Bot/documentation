---
description: Get more frequent question asked by user of Interaction Bot.
---

# FAQ

## Getting started

### How do I add the bot to my server?
Go to [interaction-bot.com](https://interaction-bot.com), click _Add to Discord_ and select your server. You need the *Manage Server* permission. See [Getting started](getting-started.md).

### How do I translate a message?
Add a flag emoji under it, right click > *Apps* > *Translate*, or use `/translate`. For automatic translation, configure the [dashboard](website/dashboard/). See the [translation overview](translation/overview.md).

### Can I use the bot on a server where it is not added?
Yes, install it on your Discord account (**Add to my account** on the [Account page](website/dashboard/account.md) or in `/invite`). `/translate` and the **Apps** menus then work in any server and in DMs. See [User app](commands/user-app.md).

### Which languages are supported?
100 languages. Run `/languages` to list them.

### Is the bot free?
Yes. [Premium](premium/premium.md) is optional and raises the limits (translations per message, number of configurations, voice sessions...).

## Translation

### Why is the translation of a message wrong?
The bot translates for free on tens of thousands of servers, with automatic translation models. The quality depends on the languages and on the message (slang, abbreviations and very short texts are harder). We keep improving the translation models, and premium servers get the best model with priority.

### Why is my message detected in the wrong language?
The bot must recognize 100 languages in any message. A message that is too short, or full of emojis and other elements, can be mistaken. Increase the minimum size in [Language identification](website/dashboard/language-identification.md), or blacklist a language that is too often confused with another one (premium). See [language detection](translation/language-detection.md).

### The bot does not translate in a channel
Run `/check-permissions`, and follow the [troubleshooting checklist](translation/troubleshooting.md).

### The bot translated a message several times / posted a warning about a limit
One message can receive up to 3 translations on a free server (20 on premium). If several configurations apply to the same message, the extra ones are dropped. Reduce overlapping configurations, or turn the warning off in the dashboard [Overview](website/dashboard/overview.md).

### Can the bot translate other bots?
Yes, on a premium server, with the option _Translate bot_.

### What happens to my data?
See the [Privacy Policy](https://interaction-bot.com/privacy) and the [Terms of Use](https://interaction-bot.com/tou).

### Who can use the dashboard?
Members with the *Administrator* permission of the server can configure the bot. If your server does not appear, check that you are logged in with the right Discord account and that the bot is on the server.

## Voice

### How do I make the bot read a message aloud?
Run `/tts say` with your text, or `/tts start` to have the messages of the chat read for as long as you want. `/tts say` needs a [top.gg vote](https://top.gg/bot/893494390142697493/vote) from you in the last 24 hours, even on a premium server. `/tts start` needs a premium server, or a vote from a member of the server. See [Text to speech commands](commands/tts.md).

### How long can a transcription last?
The limit is per server and per day: 30 minutes on a free server, 3 hours on premium. The time of all the transcriptions adds up, and the day restarts at midnight UTC. When the time is used up, the bot leaves the voice channel and says when it can transcribe again. See [Daily limits](audio/limits.md) and [Daily time and stop](audio/voice.md#daily-time-and-stop).

### Can I record a voice channel?
Yes, with `/record start`. The bot records one track per speaker, announces the recording to the members who join, and sends the link in private messages to the member who started it. Recordings are kept 7 days on a free server and 30 days on premium. See [Recording commands](commands/record.md).

### Where can I see how much time the server has left?
Run `/limits`. It shows the time used, the time left and the reset time for transcription, text to speech and recording. See [Daily limits](audio/limits.md).

## FAQ feature

### How do I make the bot answer questions on my server?
Create a group on the dashboard [FAQ](website/dashboard/faq.md), add questions and answers, and use `/ask` or turn on the automatic reply. See [FAQ and /ask](qa/faq.md).

## Premium

### How do I get premium?
See [Premium](premium/premium.md) and [Subscribe](premium/subscribe.md). Then run `/premium add` on your server.

### I subscribed but the server is not premium
Link your Patreon and Discord accounts, wait about 10 minutes, then run `/premium add` on the server. Contact the support if it still does not work.

## Still need help?

Join the [support server](https://support.interaction-bot.com).
