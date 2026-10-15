---
description: The daily time limits of the audio features (transcription, text to speech, recording), what counts, what happens at the limit, and the /limits command.
---

# Daily limits

The audio features have a **daily time limit per server**. The time is shared by all the channels and sessions of the server: two transcriptions in two voice channels use the same daily time.

## Limits

| Feature | Free server | Premium server | What is counted |
| --- | --- | --- | --- |
| Transcription ([Speech to text](voice.md)) | 30 minutes per day | 3 hours per day | The duration of the audio sent to the speech service. |
| Text to speech ([`/tts start`, `/tts say`](../commands/tts.md)) | 30 minutes per day | 3 hours per day | The duration of the speech generated. |
| Recording ([`/record`](../commands/record.md)) | 1 hour per day | 6 hours per day | The duration actually recorded. |

## When the day starts again

The day is a **UTC calendar day**: every server starts again at **midnight UTC**. The notices show the reset as a Discord countdown (*in 5 hours*, for example), so it is right whatever your time zone.

## Check the limits: `/limits`

`/limits` (ephemeral, only you see it) shows, for each feature:

* the time **used**, the **limit**, the time **left**, and when it **resets**;
* whether the server is **premium**.

## Notices

* **At 80 %** of the daily time, the bot posts a warning in the text channel: the share used, the time left and the reset time. It is sent **once per day** for each feature.
* **At 100 %**, the bot posts that the daily time is used up, with the reset time. It is also sent once per day.
* On a **free** server, these notices end with a link to [Premium](../premium/premium.md), which raises the limits.

## What happens at the limit

| Feature | At the limit |
| --- | --- |
| Transcription | The transcription stops and the bot leaves the voice channel. New transcriptions, including automatic ones, are refused until the reset. |
| Text to speech | The bot reads the clips already generated, then leaves the voice channel. `/tts say` and new sessions are refused until the reset. |
| Recording | The recording stops and is saved with what was recorded. A new recording is refused until the reset. |

## Limits and the rest of the bot

* The daily limits are the same for every server of the same offer: they are not configurable from the dashboard.
* Becoming premium or losing premium changes the limit at once. The usage of the day stays counted.
* The limits protect the service that the bot uses (the speech and voice services). They do not limit the rest of the bot: translation has [its own limits](../premium/premium.md).
