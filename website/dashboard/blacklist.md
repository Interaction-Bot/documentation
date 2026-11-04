---
description: Exclude channels, languages and roles from the translation.
---

# Blacklist

{% hint style="info" %}
On the current dashboard this page is called **Exceptions**, in the **Translation** section, and it also holds the **minimum message size** (formerly *Language identification*). Excluding channels, roles and languages is a **Premium** option.
{% endhint %}

## Localization

This page is in the **Translation** section of the navigation bar, under **Exceptions**. Its first section is **Never translate**, with three lists: **Channels**, **Roles** and **Languages**.

<figure><img src="../../.gitbook/assets/dash-blacklist.png" alt="Blacklist page"><figcaption><p>Blacklist page</p></figcaption></figure>

{% hint style="warning" %}
Adding channels, roles or languages to the list is a **Premium** feature: a server without Premium cannot add new entries. Exclusions already in place stay active.
{% endhint %}

The page has one bar of changes at the bottom. It is shared with the [minimum message size](language-identification.md) section.

## Never translate

The section lists the channels, roles and languages whose messages are never translated. These exceptions apply to written messages, not to flags.

### Channels

Click _**Add a channel**_, then choose the channel in the popup, under **Which channel?**. Messages in this channel are never translated, whether by a rule, a linked channel or the server rule. You can select several channels at once.

Each excluded channel is shown as _Never translate {channel}_, with an _**Edit this channel**_ button.

A message posted in an excluded channel is **not translated at all**. Flag translations still work in this channel, because they are triggered by a reaction.

### Roles

Click _**Add a role**_, then choose the role under **Which role?**. Messages from members with this role are never translated, whatever the rule. Each role is shown as _Ignore messages from {role}_.

### Languages

Click _**Add a language**_, then choose the language under **Which language?**. Messages written in this language are never translated. Each language is shown as _Never translate messages in {language}_.

{% hint style="info" %}
Excluding channels, roles and languages is a Premium feature.
{% endhint %}

## Save

Click on _**Save**_ in the bar at the bottom of the page to apply your changes. _**Cancel**_ removes your unsaved changes. The bar says _You made changes, save them!_

If the bot refuses to save, the page shows _Saving failed. If your server is not Premium, excluding channels, roles and languages is reserved for Premium. Try again._

## Commands

The same list can be managed with the `/blacklist` command:

* `/blacklist add`: add a role, a channel or a language (Premium).
* `/blacklist remove`: remove a role, a channel or a language.
* `/blacklist list`: list the roles, channels and languages of the blacklist.
* `/blacklist manage`: open a panel to manage the blacklist.

By default, only members with the *Manage Server* permission can use these commands.

## Errors

* _Choose a channel first._, _Choose a role first._ or _Choose a language first._: nothing is selected in the popup.
* _This channel is already excluded. Edit it instead._ (and the same for a role or a language): the item is already in the list.

## Premium

| | Free | Premium |
| --- | --- | --- |
| Add entries to the blacklist | Not available | Available (up to 250 channels and 250 roles) |

## Tips

* Blacklist the channel where members talk in their own language, for example a *#francophone* channel, to avoid translating it.
* Blacklist a role used by bots, for example *@Bots*, if you do not want their messages to be translated.
* To stop translating a channel for a short time without losing the other settings, use [Channel Translation](channel-translation.md) and uncheck **Enabled** instead.
