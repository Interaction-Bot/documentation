---
description: >-
  The status page displays the current status of the bot for each cluster and
  some statistics about the bot.
---

# Status

## Localization

The status page is located on [this page,](https://interaction-bot.com/status) you can access it with the link below.

{% embed url="https://interaction-bot.com/status" %}

## Statistics

This section displays the number of servers the bot has, the number of shards used, and the sum of all users on all servers the bot is on.

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption><p>statistics of the bot</p></figcaption></figure>

## Cluster Status

The next section displays the status of each cluster, one cluster runs multiple servers so if one cluster is down, the bot will not work on servers localized on the cluster.&#x20;

A cluster can have three statuses:

* <mark style="color:green;">Operational:</mark> the cluster is operational for these servers, if your server is on this cluster, you don't have to expect any problems with the bot.e
* <mark style="color:yellow;">Partial Outage:</mark> the cluster has a big latency, or it doesn't load all servers.
* <mark style="color:red;">Major Outage:</mark> the cluster is down, all servers on this cluster can't use the bot.

You can check information about the cluster by overlaying your cursor on it, the color of the cluster indicates the status of the cluster.

<figure><img src="../.gitbook/assets/image (6).png" alt="" width="468"><figcaption><p>Cluster Status</p></figcaption></figure>

## Find the cluster of my server

You can find what cluster runs the bot on your server by entering your server ID on the section and clicking on _**Calculate**_.

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>
