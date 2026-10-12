---
description: The startup guide that explain how to use the bot for the first time.
---

# Getting started

## :white\_check\_mark: Invitation of the bot

First, invite the bot to your Discord server from the website [<mark style="color:blue;">www.interaction-bot.com</mark>](https://interaction-bot.com)

<figure><img src=".gitbook/assets/image (36).png" alt=""><figcaption><p>Click On the button "Add to dicord"</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (41).png" alt=""><figcaption><p>Select your server</p></figcaption></figure>

{% hint style="success" %}
#### After clicking on _Continue_ for the next steps, you have invited Interaction Bot, congratulations!
{% endhint %}

## :key: Give the bot its permissions

The bot works with the permissions it receives when you invite it. For translation it needs, in the channels it uses: **View Channel, Read Message History, Send Messages, Embed Links, Attach Files**, plus **Manage Webhooks** for the webhook style and **Manage Messages** to delete original messages. If something does not work, run `/check-permissions`: it tells you which permission is missing in which channel. Details: [Troubleshooting](translation/troubleshooting.md#permissions).

## :robot: Your first translation

Run `/help` to see all the commands.

<figure><img src=".gitbook/assets/discord-help.png" alt="/help command"><figcaption><p>/help command</p></figcaption></figure>

There are three quick ways to translate, without any configuration:

1. **A flag reaction**: send a message, then add a flag emoji below it.

<figure><img src=".gitbook/assets/discord-flag-reaction.png" alt="Flag reaction"><figcaption><p>Add a flag emoji below a message</p></figcaption></figure>

<figure><img src=".gitbook/assets/discord-flag-translation.png" alt="Translation by the bot"><figcaption><p>The bot answers with the translation</p></figcaption></figure>

2. **The command** <mark style="color:green;">`/translate message [language]`</mark>. The result is private.

<figure><img src=".gitbook/assets/discord-translate.png" alt="/translate command"><figcaption><p>/translate command</p></figcaption></figure>

3. **The Apps menu**: right click a message > *Apps* > *Translate*.

{% hint style="success" %}
**You can't add the bot to a server?** Install it on your own Discord account instead: `/translate`, **Apps > Translate** and **Apps > Detect** then work in any server and in DMs. See [User app](commands/user-app.md).
{% endhint %}

## :gear: Translate automatically

To translate messages **without anybody doing anything**, configure the bot on the [dashboard](website/dashboard/): log in with Discord, select your server and pick:

* [Translation Groups](website/dashboard/translation-groups.md): one channel per language, the easiest for an international community;
* [Channel translation](website/dashboard/channel-translation.md), [Role translation](website/dashboard/role-translation.md) or [Category translation](website/dashboard/category-translation.md).

Not sure which one? Read the [translation overview](translation/overview.md) and the [setup guides](translation/guides.md).

## :microphone: And more

* **Text to speech** and **speech to text** in voice channels: [Voice](commands/voice.md).
* A **FAQ** that answers your members' questions: [FAQ and /ask](commands/faq.md).
* **Premium** for higher limits and more options: [Premium](premium/premium.md).

{% hint style="info" %}
Need help? Join the [support server](https://support.interaction-bot.com) or read the [FAQ](faq.md).
{% endhint %}

Where to go next:

{% content-ref url="translation/overview.md" %}
[overview.md](translation/overview.md)
{% endcontent-ref %}

{% content-ref url="website/dashboard/" %}
[dashboard](website/dashboard/)
{% endcontent-ref %}

{% content-ref url="commands/general.md" %}
[general.md](commands/general.md)
{% endcontent-ref %}
