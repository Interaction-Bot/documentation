---
description: Buy Premium and enable it on your server.
---

# Premium

## Localization

This page is the third item of the navigation bar, after **Overview** and **Journal**. Its title is **Premium**.

<figure><img src="../../.gitbook/assets/dash-premium-dashboard.png" alt="Premium page"><figcaption><p>Premium page</p></figcaption></figure>

Premium is set **per server**. Each offer gives a number of server slots (1, 3 or 10), and each premium server uses one slot. The offers and what they bring are described in [Premium](../../premium/premium.md).

## Subscribing with Stripe

The **Subscribe** button of the offer opens the Stripe payment page, in your language. After the payment you come back to this page and a **Thank you!** pop-up waits for your subscription to be active (up to about 10 seconds), with a **Choose my servers** button.

* The plans are monthly: **1 server 3.99 EUR**, **3 servers 9.99 EUR**, **10 servers 19.99 EUR**. You have one Stripe subscription at a time: 1, 3 or 10 servers. Subscriptions bought on Patreon add to it.
* **Change plan**: from **My subscription** of the [Account page](account.md), or on this page. The difference is prorated. Going down is refused while more servers than the new plan allows have Premium: turn Premium off on the extra servers first. Not possible while a cancellation or a payment is pending.
* **Manage my subscription** opens the Stripe portal (payment method, invoices, cancellation).
* After a cancellation, Premium stays until the end of the paid period. After a failed payment, Premium is kept for a few days.
* A full refund suspends Premium and removes it from your servers; a partial refund has no effect. A dispute suspends Premium until it is won.

The yearly option is shown but not available yet.

## Offers

The first part of the page shows the offers.

* The selector at the top has two options: **1 month** and **1 years** (**Soon**). Only the monthly offer can be used for now: the yearly option is shown but cannot be selected.
* The three cards show the offers: **1**, **3** or **10** servers.
* **Subscribe** opens the Stripe payment page for the plan. If you already have a subscription, the button becomes **Change plan**.
* The Patreon link appears only for an offer that Stripe does not offer.

## Compare plans

Under the offers, the **Compare plans** table shows what a free server and a premium server get. It is the same comparison as in [Premium](../../premium/premium.md).

## Existing Patreon subscriptions

This section is shown only while the site still offers Patreon subscriptions. It is a dropdown with the steps, and a _**Link Patreon**_ button that opens the Patreon connections page.

1. Buy an offer on Patreon (see [Subscribe](../../premium/subscribe.md)).
2. Link your Discord account to your Patreon account on the Patreon connections page. The bot reads your Discord account from your Patreon account.
3. Refresh the page. If you linked your account less than 10 minutes ago, wait: the bot checks Patreon every 10 minutes, so the premium is usually active after 10 minutes.

## Enable Premium on this server

Once your offer is active, go to the **Manage Premium** card, under the plans.

* **Premium** (switch): *Enable or disable your premium offers on this server.*
  * Turn it **on** to use one of your free slots for this server.
  * Turn it **off** to remove Premium from this server. The slot becomes free again and can be used on another server.

Click on _**Save**_ in the bar at the bottom of the page to apply the change.

In the same card, the **Refresh my Patreon status** button syncs your Patreon offer at once. It can be used again after 60 seconds.

<figure><img src="../../.gitbook/assets/image (54).png" alt=""><figcaption><p>Premium toggle</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

You can also activate Premium with the `/premium add` command, see [Usage](../../premium/usage.md).

## Errors

* **You don't have enough premiums available!** (pop-up): *Improve your premium offer or deactivate a premium on your servers.* All your slots are used, or your Discord account has no active Premium subscription (Stripe, or a Patreon offer linked to it). Turn Premium off on a server where you do not need it, or get a bigger offer.

{% hint style="info" %}
Turning Premium off removes the premium features of this server right away. Premium-only options that are already saved, such as *Translate Bot*, are switched off by the next Patreon check (within about 10 minutes).
{% endhint %}

## What happens when Premium ends?

**Patreon:** if your Patreon offer changes or ends, the premium of your servers is updated at the next Patreon check (every 10 minutes):

* If you have fewer slots than premium servers, Premium is removed from some of your servers until the number of premium servers matches your slots.
* If your Patreon membership no longer exists, Premium is removed from all your servers.

**Stripe:** when a subscription ends (cancelled at the end of the period, grace period over, full refund or dispute), its servers lose Premium within about 10 minutes, and the server gets a notice. The grace period after a failed payment is 3 days.

When a server loses Premium, the *Translate Bot* option is switched off in its channel and category translations.
