---
description: How to buy a Premium offer and activate it on your server.
---

# Subscribe

{% hint style="info" %}
Premium is now bought on the [Premium page](../website/dashboard/premium.md) of the website, with Stripe. You pay for one plan (1, 3 or 10 servers), monthly. You can change plan from **My subscription** (the difference is prorated; going down is refused while more servers than the new plan allows have Premium) and manage payment and cancellation from the **Manage my subscription** button. Premium stays until the end of the paid period after a cancellation. A full refund or a lost dispute suspends Premium. The steps below describe the Patreon path, which still applies to existing Patreon subscriptions.
{% endhint %}

Buying Premium takes four steps: buy an offer on Patreon, link your Discord account to your Patreon account, wait for the bot to update, then activate Premium on your server.

## 1. Buy an offer on Patreon

1. Go to [Patreon](https://www.patreon.com/interactionbot).
2. Select your offer (1, 3 or 10 servers) and click on **Join**.

<figure><img src="../.gitbook/assets/patreon-join.png" alt="Patreon: choose a plan and click Join"><figcaption></figcaption></figure>

3. Enter the requested information and complete the purchase.

The offers of the dashboard are monthly. The yearly option is not available yet.

## 2. Link your Discord account to Patreon

Once the purchase is done, connect your Discord account on the [Patreon connections page](https://www.patreon.com/settings/apps).

The bot finds your offer through this link: it only reads the Discord account that is connected to your Patreon account.

## 3. Wait for the bot to update

The bot checks Patreon every **10 minutes**. If you linked your Discord account less than 10 minutes ago, wait a little. Then refresh the dashboard page.

## 4. Activate Premium on your server

Use one of these two ways:

* the **Premium** toggle of the [Premium page](../website/dashboard/premium.md) of the dashboard, then click on _**Save**_. You need the **Administrator** or **Manage Server** permission on this server;
* the `/premium add` command, typed in the server, see [Usage](usage.md). Your Discord account must be linked to Patreon.

If all your slots are used, the bot refuses: remove Premium from one of your servers first (the Premium toggle, or `/premium remove`), then activate it on the new server.

Premium is now active on the server: the server shows **PREMIUM: Yes** on the [Overview](../website/dashboard/overview.md) page of the dashboard.
