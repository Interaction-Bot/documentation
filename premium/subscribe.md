---
description: How to subscribe to a Premium offer with Stripe, change or cancel it, and activate it on your servers.
---

# Subscribe

{% hint style="info" %}
Premium is bought on the [Premium page](https://interaction-bot.com/premium) of the website, with Stripe, with your Discord account. The offers are monthly: **1 server €3.99**, **3 servers €9.99** or **10 servers €19.99** per month. You have one subscription at a time. Premium is reserved for people aged **18 or over**.
{% endhint %}

## Subscribe with Stripe

1. Log in to the [Premium page](https://interaction-bot.com/premium) of the website with your Discord account.
2. Choose your offer (1, 3 or 10 servers) and click **Subscribe**. Stripe opens the payment page, in your language.
3. Pay. When you come back to the website, a **Thank you!** window shows _Payment received. Activating your Premium…_ until your subscription is active, then **Choose my servers** takes you to the servers.

The payment is attached to the Discord account you are signed in with. It is activated on that account a few seconds after the payment: no Patreon link is needed.

Then turn Premium on for your servers, see [Activate Premium on your server](#activate-premium-on-your-server).

## My subscription

The **My subscription** block of the Premium page (and of the [Account page](../website/dashboard/account.md)) shows your offer, the number of servers that use Premium out of the number your offer allows, and when it renews or ends. From there you can:

* **Change plan**: choose another offer. The change applies at once. Stripe prorates it: you pay the difference for the rest of the month, or get a credit if you go down, then the new price at each renewal. There is still one subscription.
* **Manage my subscription**: opens the Stripe portal, to change the payment method, see the invoices, or cancel.

Going down is refused while more servers than the new offer allows have Premium: turn Premium off on the extra servers first. A plan cannot be changed while a cancellation is pending or a payment is due: resume the subscription, or settle the payment, with **Manage my subscription**, then change plan.

## Cancel, a failed payment, a refund

* **Cancelling** keeps Premium until the end of the period you have paid for. Premium then ends, and it is removed from your servers.
* **A failed payment** keeps Premium for a few days, while Stripe retries the payment. If the payment is not made in that time, Premium ends.
* **A full refund** suspends Premium and removes it from your servers. A partial refund has no effect.
* **A dispute** (a chargeback) suspends Premium until the dispute is won.

In case of any problem, contact the support.

## Activate Premium on your server

Use one of these two ways:

* the **Premium** switch of the [Premium page](../website/dashboard/premium.md) of the dashboard, then click on _**Save**_. You need the **Administrator** or the **Manage Server** permission on this server;
* the `/premium add` command, typed in the server, see [Usage](usage.md). Your Discord account must have an active subscription.

If all your slots are used, the bot refuses: turn Premium off on one of your servers first (the switch, or `/premium remove`), then activate it on the new server.

Premium is active on the server when the [Overview](../website/dashboard/overview.md) page of the dashboard shows the **Premium** badge, instead of **Free**.

## Existing Patreon subscriptions

Patreon is no longer used for new subscriptions. The steps below are for people who already have a Patreon offer. They still work.

1. Keep your offer on [Patreon](https://www.patreon.com/interactionbot). There is nothing to buy again.
2. Connect your Discord account on the [Patreon connections page](https://www.patreon.com/settings/apps). The bot only reads the Discord account that is connected to your Patreon account.
3. Wait for the bot to update. The website checks Patreon every **10 minutes**: if you linked your Discord account less than 10 minutes ago, wait a little, then refresh the dashboard page or click **Refresh my Patreon status** in the **Premium** page.

The offers on Patreon and on the Premium page are the same: 1, 3 or 10 servers. Activate them on your servers as above.
